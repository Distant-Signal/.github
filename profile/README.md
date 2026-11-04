# Distant Signal

A personal UK rail companion: line status, train and journey tracking, trip
planning and Delay Repay support. It is free software, licensed
AGPL-3.0-or-later.

Use it at **[ds.cursed.solutions](https://ds.cursed.solutions/)**.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Distant-Signal/.github/main/profile/images/home-dark-1366.webp">
  <img src="https://raw.githubusercontent.com/Distant-Signal/.github/main/profile/images/home-light-1366.webp" alt="Distant Signal's home page: upcoming journeys, pinned lines and their status" width="640">
</picture>

## Repositories

The code is split across several repositories. All issues, whatever they
concern, are filed in `distant-signal`.

| Repository | Role |
|---|---|
| [distant-signal](https://github.com/Distant-Signal/distant-signal) | The frontend, the project's front page, the docs and the dev stack. All issues live here. |
| [ds-core](https://github.com/Distant-Signal/ds-core) | The shared crates, the database schema and migrations, grants, the stream envelope and the line catalogue. |
| [ds-api](https://github.com/Distant-Signal/ds-api) | The api, the trip planner and the timetable services, with the generated API types and changelog. |
| [ds-ingest](https://github.com/Distant-Signal/ds-ingest) | The ingest writer, the Kafka relays and the train movement consumers. |
| [ds-pollers](https://github.com/Distant-Signal/ds-pollers) | The pollers that fetch the upstream feeds. |
| [ds-workers](https://github.com/Distant-Signal/ds-workers) | The aggregator, enricher and notifier. |
| [ds-deploy](https://github.com/Distant-Signal/ds-deploy) | The Helm charts and the deploy tooling. |
| [ci](https://github.com/Distant-Signal/ci) | Shared workflows, actions and the Renovate preset. |
| [.github](https://github.com/Distant-Signal/.github) | This profile and the default security policy, contributing guide and issue forms. |
| DS-MCP (hosted elsewhere) | An MCP server for Distant Signal. It consumes the public API. |

Start with the [main repository's README](https://github.com/Distant-Signal/distant-signal#readme).
