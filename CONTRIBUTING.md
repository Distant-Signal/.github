# Contributing to Distant Signal

Thanks for your interest. Distant Signal is a personal UK rail companion,
maintained by one person. Bug reports, suggestions and pull requests are all
welcome. For anything larger than a small fix, please open an issue first so
we can agree on the approach before you spend time on it.

Each repository's README and `CLAUDE.md` list its exact build, lint and test
commands. This guide covers what applies everywhere.

## Issues

All issues live in the main repository,
[Distant-Signal](https://github.com/FasterSpeeding/Distant-Signal/issues),
whatever area they concern. Pick the issue form that fits. Security
problems are the exception: report them privately, as described in
[SECURITY.md](SECURITY.md).

## Pull requests

- Keep each pull request to one change, and say what it does and why in a
  sentence or two.
- Make sure CI passes. Run the formatters, linters and tests for the parts
  you touched before you push.
- Tests cover the change.
- API changes get an entry in `docs/api-changelog.md`, newest first,
  written for a client of the API.
- Visible changes include screenshots at 390 px and 1366 px wide, in light
  and dark (four in all). Every new page has a title and a meta description,
  and every icon-only button has an `aria-label`.

## Commits

- Every commit is authored `FasterSpeeding <lucy@cursed.solutions>`. Commit
  identity is checked in CI, so set it before committing:

  ```sh
  git config user.name FasterSpeeding
  git config user.email lucy@cursed.solutions
  ```

  If you are an outside contributor, open your pull request as usual; the
  maintainer will sort out authorship when it merges.
- Commit messages carry no AI attribution: no `Co-Authored-By` trailers
  naming an AI assistant and no "Generated with" footers. The same goes for
  pull request descriptions.
- Maintainer commits end with a `Task: DS-123` trailer naming the work card.
  Outside contributors can leave it out.

## Conventions

### Writing

User-facing copy uses sentence case. Failures read "Couldn't <verb>
<noun>.". No em dashes, ellipses or arrows, and no internal vocabulary
(such as "ingest", "TOC", "CRS" or "sign in"). The style guide in the main
repository (`docs/style-guide.md`) has the rest, and `scripts/check-copy.py`
enforces the banned words.

Never name or cite third-party train-tracking websites, in code, docs,
commits, issues or pull requests.

### Rust

- Line data comes only from the TOML line catalogue (`lines/*.toml`).
- Unit tests go in an inline `mod tests`. Tests that need Postgres or Redis
  are marked `#[ignore]`, and CI runs them separately.
- Use runtime `sqlx::query`, not the `query!` macros.
- Keep `cargo fmt`, `cargo clippy -- -D warnings` and `cargo deny` clean.

### Database migrations

Migrations (sqlx) are forward-only, and a merged migration is never edited:
sqlx checksums it. In short:

- a new migration's timestamp must be newer than every migration on `main`;
- statements that take locks set `SET LOCAL lock_timeout` first;
- indexes on existing tables are created `CONCURRENTLY`, in a file whose
  first line is `-- no-transaction`;
- constraints are added `NOT VALID` and validated in a later migration;
- destructive changes (drops, renames, type changes, `SET NOT NULL`) carry a
  `-- contract:` header and ship a release after the code stopped using
  what they remove.

A new table also needs its grants in the database grants file. CI checks
all of this.

### Frontend

The frontend is Next.js with Mantine. No inline `style` props, which ESLint
enforces. Icons are hand-inlined SVG. Visual regression baselines are only
valid when generated inside the pinned Playwright container
(`scripts/visual-tests.py`); never regenerate them anywhere else, and review
every changed image.

### Scripts

Tooling scripts are typed, standard-library Python, checked with ruff and
mypy and run with [uv](https://docs.astral.sh/uv/) (`uv.lock`,
`uv sync --locked`, `uv run`). Use bash only for trivial one-liners. No pip
or `requirements.txt` files.

## Licence

Distant Signal is licensed under the GNU Affero General Public License,
version 3 or later (AGPL-3.0-or-later). By contributing, you agree that
your contribution is licensed under the same terms.
