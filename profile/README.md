# Distant Signal

A personal UK rail companion: line status, train and journey tracking, trip
planning and Delay Repay support. It is free software, licensed
AGPL-3.0-or-later.

Use it at **[ds.cursed.solutions](https://ds.cursed.solutions/)**.

## Repositories

| Repository | Role |
|---|---|
| [Distant-Signal](https://github.com/FasterSpeeding/Distant-Signal) | The whole project today: the Rust services, the Next.js frontend, the Helm chart and the line catalogue. It moves into this organisation as `distant-signal`, which keeps the frontend and becomes the front page. |
| [.github](https://github.com/Distant-Signal/.github) | This profile and the default security policy, contributing guide and issue forms. |

The services will later move into their own repositories (`ds-core`,
`ds-api`, `ds-ingest`, `ds-pollers`, `ds-workers`, `ds-deploy` and `ci`).
They will be listed here as they are created.

Start with the [main repository's README](https://github.com/FasterSpeeding/Distant-Signal#readme).
