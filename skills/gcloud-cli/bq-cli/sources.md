# bq — sources

Official source URLs backing this reference for the standalone `bq` BigQuery command-line tool (GA surface).

## Official documentation

- https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference — bq command-line tool reference: syntax, boolean-flag forms, resource naming, global flags, deprecated flags, per-command flags and examples, `.bigqueryrc` defaults, CLI help, and troubleshooting. (Also reachable via https://cloud.google.com/bigquery/docs/reference/bq-cli-reference.)
- https://docs.cloud.google.com/bigquery/docs/quickstarts/load-data-bq — "Use the bq tool" quickstart (load and query data). The former usage-guide URL https://cloud.google.com/bigquery/docs/bq-command-line-tool now redirects here.
- https://cloud.google.com/bigquery/docs/schemas#specifying_a_json_schema_file — JSON schema file format used by `load`, `mk`, `mkdef`, and `update`.
- https://cloud.google.com/bigquery/docs — BigQuery product documentation home.

## Local tool verification

Flags, defaults, enum values, and command descriptions were verified against the local help output of **bq version 2.1.27** (Google Cloud SDK 552.0.0): `bq help`, `bq help <command>` for each of the 26 commands, and `bq --helpshort` for global flags. Five commands (`info`, `init`, `shell`, `truncate`, `undelete`) appear in the tool's own help but not on the web reference's command list; they are marked as such in `commands.md`.
