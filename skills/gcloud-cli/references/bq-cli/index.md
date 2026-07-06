# bq — command index

Standalone BigQuery CLI (invoked as plain `bq`, not `gcloud bq`) — 26 commands.

- `bq add-iam-policy-binding` — add a binding to a BigQuery resource's policy in IAM
- `bq cancel` — request a cancel and wait for the job to be cancelled
- `bq cp` — copy one table to another (also snapshots and clones)
- `bq extract` — export a table or model to Cloud Storage
- `bq get-iam-policy` — get the IAM policy for a resource
- `bq head` — display rows in a table
- `bq help` — list all commands, or show help for one command
- `bq info` — return the execution information of bq
- `bq init` — authenticate and create a default `.bigqueryrc` file
- `bq insert` — insert rows into a table via streaming (newline-delimited JSON)
- `bq load` — load data into a table
- `bq ls` — list the objects contained in the named collection
- `bq mk` — create a dataset, table, view, or transfer configuration
- `bq mkdef` — emit a JSON definition for an external table
- `bq partition` — copy date/time-sharded source tables into a partitioned table
- `bq query` — execute a query
- `bq remove-iam-policy-binding` — remove a binding from a BigQuery resource's policy in IAM
- `bq rm` — delete the resource described by the identifier
- `bq set-iam-policy` — set the IAM policy for a resource
- `bq shell` — start an interactive bq session
- `bq show` — show all information about an object
- `bq truncate` — truncate table/dataset/project back to a particular timestamp
- `bq undelete` — undelete a dataset
- `bq update` — update a dataset, table, view, or transfer configuration
- `bq version` — return the version of bq
- `bq wait` — wait some number of seconds for a job to finish
