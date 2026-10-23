# Project Sync

Consumer repository running scheduled GitHub Project board synchronization for `bcgov/projects/16` using [`bcgov/project-automator`](https://github.com/bcgov/project-automator).

## Overview

This repository decouples project board synchronization from the engine repository codebase, running hourly synchronization using the immutable release of `bcgov/project-automator`.

## Configuration

- **Rules**: Board columns, sprint assignments, monitored repositories, and exclusions are configured in [`rules.yml`](rules.yml).
- **Workflow**: Scheduled synchronization runs via [`.github/workflows/sync.yml`](.github/workflows/sync.yml) every hour (`7 * * * *`).

## Secrets

- `PROJECT_SYNC_TOKEN`: A GitHub Personal Access Token with read/write access to `bcgov/projects/16`, read access to all monitored repositories, and write access to issues and pull requests in monitored repositories for automatic assignment of authored items (optional; with a read-only token, automatic assignment is skipped while board synchronization still runs).
