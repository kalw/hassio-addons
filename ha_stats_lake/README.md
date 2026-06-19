# ![Project Stage][project-stage-shield] Home Assistant Add-on: HA Stats Lake

[![GitHub Release][releases-shield]][releases]
![Project Stage][project-stage-shield]
[![License][license-shield]](LICENSE.md)

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

[![Github Actions][github-actions-shield]][github-actions]
[![GitHub Activity][commits-shield]][commits]
[![GitHub Last Commit][last-commit-shield]][commits]

Long-term storage for Home Assistant sensor data via DuckLake on S3-compatible storage.

## About

Samples a configured list of entities every 30 minutes to flat per-entity
monthly CSV files, then nightly:

- consolidates new rows into a [DuckLake](https://ducklake.select/) (Parquet)
  on any **S3-compatible store** (Cloudflare R2, AWS S3, MinIO, …)
- syncs raw CSVs to any [rclone](https://rclone.org/) remote as a cold backup
  (OneDrive, Google Drive, SFTP, …)

Visualization on demand via `duckdb -ui` pointed at your S3 store — no
dashboard server to maintain.

[:books: Read the full add-on documentation][docs]


[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[github-actions-shield]: https://github.com/kalw/ha-stats-lake/workflows/CI/badge.svg
[github-actions]: https://github.com/kalw/ha-stats-lake/actions
[commits]: https://github.com/kalw/ha-stats-lake/commits/main
[commits-shield]: https://img.shields.io/github/commit-activity/y/kalw/ha-stats-lake.svg
[releases-shield]: https://img.shields.io/github/release/kalw/ha-stats-lake.svg
[releases]: https://github.com/kalw/ha-stats-lake/releases
[last-commit-shield]: https://img.shields.io/github/last-commit/kalw/ha-stats-lake.svg
[license-shield]: https://img.shields.io/github/license/kalw/ha-stats-lake.svg
[docs]: https://github.com/kalw/ha-stats-lake/blob/main/ha_stats/DOCS.md

[project-stage-shield]: https://img.shields.io/badge/project%20stage-experimental-yellow.svg
