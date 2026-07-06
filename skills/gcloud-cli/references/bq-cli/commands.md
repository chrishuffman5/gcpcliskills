# bq — commands

The standalone BigQuery CLI (invoked as plain `bq`, not `gcloud bq`). Format: `bq [--global_flags] <command> [--command_flags] [args]`. Flags below are command-specific; global flags (`--project_id`, `--location`, `--format`, `--quiet`, `--synchronous_mode`, ...) are covered in [`overview.md`](overview.md). Boolean flags accept `--flag`/`--flag=true`/`--flag=false`/`--noflag`. Flags marked *(Experimental)*, *(Preview)*, or *(Deprecated)* in the tool's own help are labeled as such — prefer the unlabeled GA surface.

### `bq add-iam-policy-binding`

Add a binding to a BigQuery resource's policy in IAM.

Retrieves the IAM policy for a table or view and adds one binding (member + role) to it in a single step — the one-shot alternative to `get-iam-policy` → edit → `set-iam-policy`. Does not support datasets; to change dataset access use `bq update --dataset` with an access spec or the console.

**Synopsis:**
```
bq add-iam-policy-binding --member=MEMBER_TYPE:MEMBER --role=ROLE
    [-t | --connection | --reservation | --routine] IDENTIFIER
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | MEMBER | | Member part of the binding: `user:<email>`, `group:<email>`, `serviceAccount:<email>`, `domain:<domain>`, `allAuthenticatedUsers`, or `allUsers`. |
| `--role` | ROLE | | Role part of the binding: a predefined role (`roles/bigquery.dataViewer`), a project custom role (`projects/my-project/roles/MyCustomRole`), or an org custom role (`organizations/111111111111/roles/MyCustomRole`). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-t`, `--table` | boolean | `false` | Treat the identifier as a table. |
| `--connection` | boolean | `false` | Treat the identifier as a connection. |
| `-d`, `--dataset` | boolean | `false` | Treat the identifier as a dataset (not fully supported per the official reference). |
| `--reservation` | boolean | `false` | Treat the identifier as a reservation. |
| `--routine` | boolean | `false` | Treat the identifier as a routine. |

**Examples:**
```bash
bq add-iam-policy-binding \
    --member='user:myaccount@gmail.com' \
    --role='roles/bigquery.dataViewer' \
    mydataset.mytable

bq add-iam-policy-binding \
    --member='serviceAccount:my.service.account@my-domain.com' \
    --role='roles/bigquery.dataEditor' \
    project1:dataset1.table1

bq add-iam-policy-binding \
    --member='allAuthenticatedUsers' \
    --role='roles/bigquery.dataViewer' \
    --project_id=proj -t ds.table1
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_add-iam-policy-binding)

---
### `bq cancel`

Request a cancel and wait for the job to be cancelled.

Requests cancellation, then waits until the job is done if the global sync flag is set (default), or returns immediately with `--nosync`. Not all job types support cancel (an error is returned if not), and even where supported success is not guaranteed — the job may already be done or past the cancellable stage. The global `--location` flag is required for this command.

**Synopsis:**
```
bq [--nosync] cancel JOB_ID
```

No command-specific flags. `JOB_ID` is the job to cancel.

**Examples:**
```bash
bq cancel bqjob_r1234_5678          # request cancel, wait until the job is done
bq --nosync cancel bqjob_r1234_5678 # request cancel, return immediately
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_cancel)

---
### `bq cp`

Copy one table to another.

Also creates table snapshots (`--snapshot`) and table clones (`--clone`). Multiple comma-separated source tables can be copied/appended to a single destination. Prompts before overwriting an existing destination unless `-f`.

**Synopsis:**
```
bq cp [FLAGS] SOURCE_TABLE[,SOURCE_TABLE...] DESTINATION_TABLE
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-a`, `--append_table` | boolean | `false` | Append to an existing table. |
| `--clone` | boolean | `false` | Create a clone of the source table. |
| `--destination_kms_key` | KEY | | Cloud KMS key for encryption of the destination table data. |
| `--expiration` | integer (seconds) | | Expiration time, in seconds from now, of the destination table. |
| `-f`, `--force` | boolean | `false` | Overwrite an existing destination without prompting. |
| `-n`, `--no_clobber` | boolean | `false` | Do not overwrite an existing table. |
| `-r`, `--restore` | boolean | `false` | *(Deprecated — use `--clone`.)* Restore a table snapshot to a live table. |
| `-s`, `--snapshot` | boolean | `false` | Create a table snapshot of the source table. |

**Examples:**
```bash
bq cp dataset.old_table dataset2.new_table
bq cp --destination_kms_key=kms_key dataset.old_table dataset2.new_table
bq cp -a dataset.src dataset.dest                        # append
bq cp --snapshot --expiration=86400 ds.table ds.snap     # snapshot, 24h TTL
bq cp --clone ds.table ds.table_clone                    # writable clone
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_cp)

---
### `bq extract`

Export (extract) a table or model to Cloud Storage.

Runs an extract job from a source table (or, with `-m`, a BigQuery ML model) to one or more comma-separated `gs://` URIs. Use a `*` wildcard in the URI to shard large exports across multiple files.

**Synopsis:**
```
bq extract [FLAGS] SOURCE_TABLE DESTINATION_URIS
bq extract -m [FLAGS] SOURCE_MODEL DESTINATION_URI
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--compression` | `GZIP`\|`DEFLATE`\|`SNAPPY`\|`ZSTD`\|`NONE` | `NONE` | Compression type for exported files. Not applicable to models. |
| `--destination_format` | `CSV`\|`NEWLINE_DELIMITED_JSON`\|`AVRO`\|`PARQUET`\|`ML_TF_SAVED_MODEL`\|`ML_XGBOOST_BOOSTER` | `CSV` (tables), `ML_TF_SAVED_MODEL` (models) | Exported file format. The ML_* formats apply to models. Tables with nested/repeated fields cannot be exported as CSV. |
| `-F`, `--field_delimiter` | CHAR | `,` | Column delimiter in the output file; `\t` and `tab` accepted for tab. Not applicable to models. |
| `-m`, `--model` | boolean | `false` | Extract a model instead of a table. |
| `--print_header` | boolean | `true` | Print header rows for formats that have headers. Not applicable to models. |
| `--trial_id` | integer | default trial | 1-based ID of the trial to export from a hyperparameter-tuning model. |
| `--use_avro_logical_types` | boolean | | For AVRO output, extract applicable column types (e.g. TIMESTAMP) to their AVRO logical types (timestamp-micros) instead of raw types (long). Not applicable to models. |
| `--add_serving_default_signature` | boolean | | Add a `serving_default` signature when exporting BigQuery ML TensorFlow models. |
| `--reservation_id` | RESERVATION | | Reservation to run the job in: `project_id:reservation_id`, `project_id:location.reservation_id`, or `reservation_id`. |

**Examples:**
```bash
bq extract mydataset.mytable gs://mybucket/table.csv
bq extract --destination_format=NEWLINE_DELIMITED_JSON --compression=GZIP \
    mydataset.mytable 'gs://mybucket/export/table_*.json.gz'
bq extract -m mydataset.mymodel gs://mybucket/model
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_extract)

---
### `bq get-iam-policy`

Get the IAM policy for a resource.

Prints the IAM policy of a dataset, table, view, routine, connection, or reservation to stdout as JSON. Use the resource-type boolean flag when the identifier is ambiguous.

**Synopsis:**
```
bq get-iam-policy [-t | -d | --connection | --reservation | --routine] IDENTIFIER
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-t`, `--table` | boolean | `false` | Identifier is a table. |
| `-d`, `--dataset` | boolean | `false` | Identifier is a dataset. |
| `--connection` | boolean | `false` | Identifier is a connection. |
| `--reservation` | boolean | `false` | Identifier is a reservation. |
| `--routine` | boolean | `false` | Identifier is a routine. |

**Examples:**
```bash
bq get-iam-policy ds.table1
bq get-iam-policy --project_id=proj -t ds.table1
bq get-iam-policy proj:ds.table1
bq get-iam-policy --reservation proj:US.reservation1
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_get-iam-policy)

---
### `bq head`

Display rows in a table.

Prints table rows (or, with `-j`, the results of a query job) without running a query — no bytes billed.

**Synopsis:**
```
bq head [FLAGS] [DATASET.]TABLE
bq head -j [FLAGS] JOB_ID
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-j`, `--job` | boolean | `false` | Read the results of a query job. |
| `-t`, `--table` | boolean | `false` | Read rows from a table. |
| `-n`, `--max_rows` | integer | `100` | Number of rows to print. |
| `-s`, `--start_row` | integer | `0` | Number of rows to skip before printing. |
| `-c`, `--selected_fields` | FIELD,... | all fields | Subset of (possibly nested) fields to return, e.g. `-c a,b`. |

**Examples:**
```bash
bq head dataset.table
bq head -j job_id
bq head -n 10 dataset.table
bq head -s 5 -n 10 -c 'name,value' dataset.table
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_head)

---
### `bq help`

Display help within the tool.

`bq help` lists all commands with examples; `bq help COMMAND` prints a command's description and its command-specific flags; `bq --help` prints the global flags.

**Synopsis:**
```
bq help [COMMAND]
```

**Examples:**
```bash
bq help          # all commands
bq help mk       # one command's flags
bq --help        # global flags
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_help)

---
### `bq info`

Return the execution information of bq.

Prints environment details for the running tool (paths, versions). No command-specific flags. Not listed on the web reference; documented via `bq help`.

**Synopsis:**
```
bq info
```

**Examples:**
```bash
bq info
```

---
### `bq init`

Authenticate and create a default `.bigqueryrc` file.

Interactive bootstrap for credentials and the config file. The official reference recommends **not** using `bq init` to create `.bigqueryrc` — write the file with an editor instead (see [`overview.md`](overview.md)). Not listed on the web reference command list; documented via `bq help`.

**Synopsis:**
```
bq init [--delete_credentials]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--delete_credentials` | boolean | `false` | Delete the credentials file associated with this `.bigqueryrc`. |

**Examples:**
```bash
bq init
bq init --delete_credentials
```

---
### `bq insert`

Insert rows into a table via streaming.

Streams records formatted as newline-delimited JSON from a file (or stdin if no file is given) into the table using the streaming API. Insert errors are printed to stdout. Intended for testing — for production streaming use the Storage Write API or `tabledata.insertAll`.

**Synopsis:**
```
bq insert [FLAGS] [DATASET.]TABLE [FILE]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-i`, `--ignore_unknown_values` | boolean | | Ignore any values in a row that are not present in the schema. |
| `-s`, `--skip_invalid_rows` | boolean | | Attempt to insert all valid rows, even if invalid rows are present. |
| `--insert_id` | PREFIX | | Deduplication prefix: appended with the row number to form each row's `insertId`, so repeat executions do not add unintended data. |
| `-x`, `--template_suffix` | SUFFIX | | Treat the destination table as a base template and insert into `{destination}{templateSuffix}`; BigQuery creates the instance table from the template's schema. |

**Examples:**
```bash
bq insert dataset.table /tmp/mydata.json
echo '{"a":1, "b":2}' | bq insert dataset.table
bq insert -x=_suffix dataset.table /tmp/mydata.json   # template tables
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_insert)

---
### `bq load`

Load data into a table.

Runs a load job from a local file or a comma-separated list of `gs://` URIs into `DESTINATION_TABLE` (created if missing, appended to if it exists). The optional `SCHEMA` argument is either a JSON schema file or an inline text schema (`name[:type],...`, type defaults to `STRING`); omit it when the table already has a schema or when using `--autodetect`. To load into a temporary table, give a bare table name plus `--session_id`.

**Synopsis:**
```
bq load [FLAGS] DESTINATION_TABLE SOURCE [SCHEMA]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source_format` | `CSV`\|`NEWLINE_DELIMITED_JSON`\|`DATASTORE_BACKUP`\|`AVRO`\|`PARQUET`\|`ORC`\|`THRIFT` | `CSV` | Format of the source data. |
| `--autodetect` | boolean | | Auto-detect schema and options for non-self-describing formats (CSV, JSON). |
| `--schema` | file or `name[:type],...` | | Schema as a flag instead of the positional argument. |
| `--replace` | boolean | `false` | Erase existing data (and schema) before loading. |
| `--replace_data` | boolean | `false` | Erase existing contents only; keep table metadata such as schema. |
| `--schema_update_option` | `ALLOW_FIELD_ADDITION`\|`ALLOW_FIELD_RELAXATION` | | When appending or replacing a partition, update the destination schema from the new data (repeatable). |
| `--skip_leading_rows` | integer | | Number of rows at the beginning of the source file to skip (CSV headers). |
| `-F`, `--field_delimiter` | CHAR | | CSV column delimiter; `\t` and `tab` accepted for tab. |
| `-E`, `--encoding` | `UTF-8`\|`ISO-8859-1`\|`UTF-16BE`\|`UTF-16LE`\|`UTF-32BE`\|`UTF-32LE` | | Character encoding of the input file. |
| `--quote` | CHAR | `"` | Quote character enclosing CSV records; empty string means no quoting. |
| `--allow_jagged_rows` | boolean | | Allow missing trailing optional columns in CSV data. |
| `--allow_quoted_newlines` | boolean | | Allow quoted newlines in CSV data. |
| `--preserve_ascii_control_characters` | boolean | | Preserve embedded ASCII control characters in CSV data. |
| `--ignore_unknown_values` | boolean | | Allow and ignore extra, unrecognized values in CSV or JSON data. |
| `--max_bad_records` | integer | `0` | Max bad records tolerated before the job fails (CSV and NEWLINE_DELIMITED_JSON only). |
| `--null_marker` | STRING | | Custom string representing NULL in CSV data. |
| `--null_markers` | STRING,... | | List of custom strings representing NULL in CSV data. |
| `--source_column_match` | `POSITION`\|`NAME` | | How loaded columns match the schema: by position, or by header-row name. |
| `--column_name_character_map` | `STRICT`\|`V1`\|`V2` | | Character map for column names: STRICT (latest map, reject invalid), V1 (alphanumeric + underscore, normalize invalid), V2 (flexible names, normalize invalid). |
| `--date_format` / `--datetime_format` / `--time_format` / `--timestamp_format` | format string | | Format elements defining how DATE / DATETIME / TIME / TIMESTAMP values are formatted in the input (e.g. `MM/DD/YYYY HH24:MI:SS.FF3`). |
| `--time_zone` | TZ name | | Default time zone applied when parsing timestamps with no zone (e.g. `America/Los_Angeles`). |
| `--timestamp_target_precision` | `[6]`\|`[12]`\|`[6, 12]` | `[6]` | Target TIMESTAMP precision(s) for autodetected CSV columns; higher-precision input is truncated. |
| `--numeric_type_conversion_mode` | `ROUND` | fail | Round numeric values whose fractional precision exceeds scale 9 instead of failing the job. |
| `--decimal_target_types` | `NUMERIC`\|`BIGNUMERIC`\|`STRING` | | Preference-ordered list of types that source decimal values may convert to (repeatable). |
| `--time_partitioning_type` | `DAY`\|`HOUR`\|`MONTH`\|`YEAR` | `DAY` | Enable time-based partitioning and set the granularity. |
| `--time_partitioning_field` | FIELD | ingestion time | Partition on this field instead of load time. |
| `--time_partitioning_expiration` | integer (seconds) | | Keep partition storage for this long past the partition time. |
| `--range_partitioning` | `field,start,end,interval` | | Integer-range partitioning on a top-level non-repeated INT64 field. |
| `--require_partition_filter` | boolean | | Require a partition filter for queries over this table. |
| `--clustering_fields` | FIELD,... | | Comma-separated columns to cluster the table on; empty value removes clustering. |
| `--destination_kms_key` | KEY | | Cloud KMS key for encryption of the destination table data. |
| `--session_id` | SESSION | | Session ID when loading into a temporary table. |
| `--use_avro_logical_types` | boolean | | For AVRO sources, interpret logical types (e.g. TIMESTAMP) instead of raw types (e.g. INTEGER). |
| `--parquet_enable_list_inference` | boolean | | Use Parquet-specific schema inference for the LIST logical type (element node collapsed to a repeated field). |
| `--parquet_enum_as_string` | boolean | | Infer Parquet ENUM as STRING instead of BYTES. |
| `--parquet_map_target_type` | `ARRAY_OF_STRUCT` | | Represent Parquet maps as a repeated struct with key and value fields. |
| `--reference_file_schema_uri` | URI | | Reference file providing the reader schema (AVRO, PARQUET, ORC). |
| `--hive_partitioning_mode` | `AUTO`\|`STRINGS` | | Enable hive partitioning: AUTO infers key types, STRINGS treats all keys as STRING. |
| `--hive_partitioning_source_uri_prefix` | URI prefix | | Prefix after which hive partition encoding begins (for `gs://bucket/path/key1=value/file`, use `gs://bucket/path`). |
| `--file_set_spec_type` | `FILE_SYSTEM_MATCH`\|`NEW_LINE_DELIMITED_MANIFEST` | `FILE_SYSTEM_MATCH` | How to discover files from source URIs: expand by listing the object store, or treat URIs as newline-delimited manifest files. |
| `--projection_fields` | FIELD,... | | For DATASTORE_BACKUP, which entity properties to load (case sensitive, top-level). |
| `--json_extension` | `GEOJSON` | | *(Experimental)* Load input as newline-delimited GeoJSON (requires NEWLINE_DELIMITED_JSON source format). |
| `--copy_files_only` | boolean | | *(Experimental)* Only copy files to a BigLake managed table without reading/rewriting content. |
| `--boundary_bytes_base64` / `--thrift_framing` / `--thrift_deserialization` / `--thrift_schema_idl_root_dir` / `--thrift_schema_idl_uri` / `--thrift_schema_struct` | various | | THRIFT source-format options: boundary bytes, framing (`NOT_FRAMED`\|`FRAMED_WITH_BIG_ENDIAN`\|`FRAMED_WITH_LITTLE_ENDIAN`), protocol (`T_BINARY_PROTOCOL`), and IDL locations defining the schema struct. |
| `--reservation_id` | RESERVATION | | Reservation to run the job in: `project_id:reservation_id`, `project_id:location.reservation_id`, or `reservation_id`. |

**Examples:**
```bash
bq load ds.new_tbl ./info.csv ./info_schema.json
bq load ds.new_tbl gs://mybucket/info.csv ./info_schema.json
bq load ds.small gs://mybucket/small.csv name:integer,value:string
bq load --source_format=NEWLINE_DELIMITED_JSON --autodetect ds.tbl ./data.json
bq load --replace --skip_leading_rows=1 ds.tbl gs://mybucket/data.csv
bq load temp_tbl --session_id=my_session ./info.csv ./info_schema.json
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_load)

---
### `bq ls`

List the objects contained in the named collection.

Lists objects in the named project or dataset (a trailing `:` or `.` marks the identifier as a project or dataset). With `-j` lists jobs in the project; with `-p` lists projects; other flags switch to models, routines, row access policies, transfer configs/runs/logs, reservations, capacity commitments, and connections.

**Synopsis:**
```
bq ls [FLAGS] [IDENTIFIER]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-n`, `--max_results` | integer | | Maximum number of results to list. |
| `-a`, `--all` | boolean | | Show all results: jobs from all users; hidden datasets. (Redundant for transfer configs/runs.) |
| `-d`, `--datasets` | boolean | `false` | Show datasets described by this identifier. |
| `-j`, `--jobs` | boolean | `false` | Show jobs described by this identifier. |
| `-p`, `--projects` | boolean | `false` | Show all projects. |
| `-m`, `--models` | boolean | `false` | Show all models. |
| `--routines` | boolean | `false` | Show all routines in the dataset. |
| `--row_access_policies` | boolean | `false` | Show all row access policies on the table. |
| `--filter` | EXPRESSION | | Filter results. Datasets: space-separated `labels.key:value` terms (must match all). Transfer configs: `dataSourceIds:value(s)`. Transfer runs and jobs: `states:VALUE(s)`. |
| `-k`, `--page_token` | TOKEN | | Start listing from this page token. |
| `--print_last_token` | boolean | `false` | Also print the next page token for the jobs list. |
| `--print_unreachable` | boolean | `false` | Also print unreachable locations for dataset and jobs lists. |
| `--min_creation_time` / `--max_creation_time` | integer (ms) | | Only jobs created after / before this timestamp (milliseconds since epoch). |
| `--parent_job_id` | JOB_ID | | Only jobs that are children of this parent job; if omitted, only top-level jobs. |
| `--transfer_config` | boolean | `false` | Show transfer configurations (requires `--transfer_location`). |
| `--transfer_location` | LOCATION | | Location for the transfer-config list (e.g. `us`, `eu`). |
| `--transfer_run` | boolean | `false` | List transfer runs for a config resource name. |
| `--run_attempt` | `LATEST`\|`RUN_ATTEMPT_UNSPECIFIED` | `LATEST` | Which transfer-run attempts to pull. |
| `--transfer_log` | boolean | `false` | List messages under the specified transfer run. |
| `--message_type` | `messageTypes:INFO\|WARNING\|ERROR` | | Which transfer-log message severities to list. |
| `--reservation` | boolean | | List all reservations for the given project and location. |
| `--reservation_assignment` | boolean | | List reservation assignments for the project/location. |
| `--reservation_group` | boolean | | List reservation groups for the project/location. |
| `--reservation_group_name` | NAME | | Filter reservations by reservation group (with `--reservation`). |
| `--capacity_commitment` | boolean | | List capacity commitments (slots) for the project and location. |
| `--connection` | boolean | | List all connections for the project/location. |
| `--migration_workflow` | boolean | `false` | List migration workflows for the project and location. |

**Examples:**
```bash
bq ls                          # datasets in the default project
bq ls mydataset                # tables in a dataset
bq ls -j proj                  # jobs in a project
bq ls -j --filter='states:RUNNING,PENDING' proj
bq ls -p -n 1000               # projects
bq ls -a                       # include hidden datasets
bq ls -m mydataset             # models
bq ls --routines mydataset
bq ls --filter='labels.color:red labels.size:*'
bq ls --transfer_config --transfer_location=us --filter='dataSourceIds:play,adwords'
bq ls --reservation --project_id=proj --location=us
bq ls --connection --project_id=proj --location=us
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_ls)

---
### `bq mk`

Create a dataset, table, view, or transfer configuration with this name.

One creation entry point for most BigQuery resources; the boolean type flag (`-d`, `-t`, `--view`, `--materialized_view`, `--transfer_config`, `--reservation`, `--connection`, `--row_access_policy`, ...) selects what gets created. Table schemas use the same inline text (`name[:type],...`) or JSON-file format as `bq load`.

**Synopsis:**
```
bq mk [FLAGS] IDENTIFIER [SCHEMA]
```

**Optional flags — resource type selectors:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-d`, `--dataset` | boolean | `false` | Create a dataset. |
| `-t`, `--table` | boolean | `false` | Create a table. |
| `--view` | SQL | | Create a view with this GoogleSQL/legacy-SQL query. |
| `--materialized_view` | SQL | | *(Experimental per help; GA feature)* Create a materialized view from this GoogleSQL query. |
| `--transfer_config` | boolean | | Create a Data Transfer Service config. |
| `--transfer_run` | boolean | `false` | Create transfer runs for a time range or specific run time. |
| `--reservation` | boolean | | Create a reservation. |
| `--reservation_assignment` | boolean | | Create a reservation assignment. |
| `--reservation_group` | boolean | | Create a reservation group. |
| `--capacity_commitment` | boolean | | Create a capacity commitment (ID assigned automatically). |
| `--connection` | boolean | | Create a connection. |
| `--row_access_policy` | boolean | | Create a row access policy on a table. |
| `--migration_workflow` | boolean | | Create a migration workflow from `--config_file`. |

**Optional flags — common / dataset / table:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-f`, `--force` | boolean | `false` | Succeed (and ignore the error) if the object already exists. |
| `--description` | TEXT | | Description of the dataset, table, or connection. |
| `--label` | `key:value` | | Label to set on the table or dataset (repeatable). |
| `--add_tags` | `ns/key:value,...` | | Tags to attach to the dataset or table (namespaced key:value pairs). |
| `--expiration` | integer (seconds) | | Expiration time of the table, in seconds from now. |
| `--schema` | file or `name[:type],...` | | Table schema as a flag instead of the positional argument. |
| `--data_location` | LOCATION | | Geographic location of the dataset (e.g. `EU`, `us-central1`). |
| `--default_table_expiration` | integer (seconds) | | Default lifetime for newly created tables in the dataset. |
| `--default_partition_expiration` | integer (seconds) | | Default partition expiration for partitioned tables in the dataset (overrides `default_table_expiration` for them). |
| `--default_kms_key` | KEY | | Default KMS key for new objects created in the dataset. |
| `--max_time_travel_hours` | integer (48–168) | `168` | Time-travel window for the dataset in hours (2–7 days). |
| `--storage_billing_model` | `LOGICAL`\|`PHYSICAL` | | Storage billing model of the dataset. |
| `--source_dataset` | DATASET | | Create a Linked Dataset pointing at this source dataset (requires allowlisting). |
| `--external_source` | `aws-glue://ARN` | | External source backing the dataset (AWS Glue databases only), with `--connection_id`. |
| `--external_catalog_dataset_options` / `--external_catalog_table_options` | JSON or file | | Open-source-catalog metadata for the dataset / table (inline JSON or path to a JSON file). |
| `--time_partitioning_type` | `DAY`\|`HOUR`\|`MONTH`\|`YEAR` | `DAY` | Enable time-based partitioning and set the granularity. |
| `--time_partitioning_field` | FIELD | ingestion time | Partition on this field instead of load time. |
| `--time_partitioning_expiration` | integer (seconds) | | Keep partition storage for this long past the partition time. |
| `--range_partitioning` | `field,start,end,interval` | | Integer-range partitioning on a top-level non-repeated INT64 field. |
| `--require_partition_filter` | boolean | | Require a partition filter for queries over the table. |
| `--clustering_fields` | FIELD,... | | Columns to cluster the table on. |
| `--destination_kms_key` | KEY | | Cloud KMS key for encryption of table data. |
| `--external_table_definition` | `TABLE::DEF` file or `schema@format=uri@connection` | | Create an external table from a definition file (see `bq mkdef`) or inline spec; `schema@`, `format=`, and `connection` parts optional, format defaults to CSV. |
| `--connection_id` | CONNECTION | | Connection for reading external storage: `project.location.connection` or full resource path. |
| `--metadata_cache_mode` | `AUTOMATIC`\|`MANUAL` | | Metadata caching for an external table with a connection. |
| `--max_staleness` | INTERVAL | none | Max staleness allowed when querying a materialized view or external table (e.g. 1 hour: `0-0 0 1:0:0`). |
| `--object_metadata` | `SIMPLE` | | Create an Object Table (directory listing of the URIs in the external definition). |
| `--file_format` | `PARQUET` | | File format of BigLake table data (with `--storage_uri`). |
| `--table_format` | `ICEBERG` | | Metadata snapshot format of a BigLake table. |
| `--storage_uri` | `gs://bucket/path/` | | Fully qualified external folder prefix for BigLake table data (no `*` wildcard). |
| `--file_set_spec_type` | `FILE_SYSTEM_MATCH`\|`NEW_LINE_DELIMITED_MANIFEST` | `FILE_SYSTEM_MATCH` | How to discover files from source URIs. |
| `--reference_file_schema_uri` | URI | | Reference file with the table schema (AVRO, PARQUET, ORC). |
| `--use_avro_logical_types` | boolean | `true` | For AVRO, interpret logical types instead of raw types. |
| `--parquet_enable_list_inference` | boolean | `false` | Parquet LIST logical-type inference. |
| `--parquet_enum_as_string` | boolean | `false` | Infer Parquet ENUM as STRING instead of BYTES. |
| `--parquet_map_target_type` | `ARRAY_OF_STRUCT` | | Represent Parquet maps as repeated key/value structs. |
| `--preserve_ascii_control_characters` | boolean | `false` | Preserve ASCII control characters in CSV external tables. |
| `--null_marker` / `--null_markers` | STRING(s) | | Custom NULL representations in CSV external-table data. |
| `--source_column_match` | `POSITION`\|`NAME` | | Column-to-schema matching strategy for CSV external tables. |
| `--date_format` / `--datetime_format` / `--time_format` / `--timestamp_format` | format string | | Input format elements for DATE / DATETIME / TIME / TIMESTAMP values. |
| `--time_zone` | TZ name | | Default time zone for timestamps with no zone. |
| `--timestamp_target_precision` | `[6]`\|`[12]`\|`[6, 12]` | `[6]` | Target TIMESTAMP precision(s) for autodetection (CSV). |
| `--view_udf_resource` | URI or path | | Code file loaded and evaluated as a UDF resource used by the view (repeatable). |
| `--use_legacy_sql` | boolean | server default | Dialect of the `--view` query; if unset, determined by dialect prefixes, else legacy SQL. Use `--use_legacy_sql=false` for GoogleSQL views. |
| `--source` | file | | Path to a file with the JSON payload for the creation request. |

**Optional flags — transfer configs and runs:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data_source` | SOURCE | | Data source of the transfer config (e.g. `scheduled_query`, `google_cloud_storage`). |
| `--target_dataset` | DATASET | | Target dataset for the transfer config. |
| `--display_name` | NAME | | Display name of the transfer config or connection. |
| `-p`, `--params` | JSON | | Parameters for the transfer config, e.g. `--params='{"param":"value"}'`. |
| `--schedule` | schedule string | source default | Transfer schedule, e.g. `every 24 hours`, `1st,3rd monday of month 15:30`. |
| `--schedule_start_time` / `--schedule_end_time` | RFC3339 UTC | | Window in which transfer runs are scheduled. |
| `--no_auto_scheduling` | boolean | `false` | Disable automatic scheduling of transfer runs. |
| `--event_driven_schedule` | JSON | | Event-driven schedule, e.g. `{"pubsub_subscription": "projects/p/subscriptions/s"}`; mutually exclusive with `--schedule`/`--no_auto_scheduling`/start/end times. |
| `--refresh_window_days` | integer | `0` | Refresh window days for the transfer config. |
| `--service_account_name` | EMAIL | | Service account used as the transfer-config credential. |
| `--notification_pubsub_topic` | TOPIC | | Pub/Sub topic notified after a transfer run completes or fails. |
| `--managed_table_type` | `NATIVE`\|`BIGLAKE` | | Destination table type for the transfer config. |
| `--start_time` / `--end_time` | RFC3339 UTC | | Range of transfer runs to create (with `--transfer_run`). |
| `--run_time` | RFC3339 UTC | | Specific time for a single transfer run (with `--transfer_run`). |

**Optional flags — reservations, commitments, connections, row access policies:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--slots` | integer | `0` | Baseline slots for the reservation (or split size for commitments). |
| `--edition` | `STANDARD`\|`ENTERPRISE`\|`ENTERPRISE_PLUS` | | Edition of the reservation or capacity commitment (STANDARD not valid for commitments). |
| `--autoscale_max_slots` | integer | | Slots to scale when needed; enables autoscaling. |
| `--ignore_idle_slots` / `--use_idle_slots` | boolean | use idle | Whether queries in the reservation may use idle slots from other reservations (`--use_idle_slots=true` default; `--ignore_idle_slots` is the inverse). |
| `--target_job_concurrency` | integer | auto (`0`) | Soft cap on concurrent jobs in the reservation. (`--concurrency`/`--max_concurrency` are deprecated synonyms.) |
| `--scheduling_policy_concurrency` / `--scheduling_policy_max_slots` | integer | | Per-project caps on concurrency / slot-consumption rate within the reservation. |
| `--max_slots` + `--scaling_mode` | integer + `AUTOSCALE_ONLY`\|`IDLE_SLOTS_ONLY`\|`ALL_SLOTS` | | *(Preview)* Overall max slots with a scaling mode; mutually exclusive with `--autoscale_max_slots`. |
| `--multi_region_auxiliary` | boolean | `false` | Place the commitment/reservation in the org's auxiliary DR region (US/EU, allowlisted). |
| `--reservation_group_name` | NAME | | Reservation group to create the reservation in. |
| `--plan` | `FLEX`\|`MONTHLY`\|`ANNUAL`\|`THREE_YEAR` | | Commitment plan for the capacity commitment. |
| `--renewal_plan` | `NONE`\|`FLEX`\|`MONTHLY`\|`ANNUAL`\|`THREE_YEAR` | | Plan the commitment converts to after the committed period (NONE only with `--edition`; FLEX/MONTHLY not with `--edition`). |
| `--job_type` | `QUERY`\|`PIPELINE`\|`ML_EXTERNAL`\|`BACKGROUND`\|`SPARK`\|`CONTINUOUS`\|... | | Job type the reservation assignment applies to. |
| `--assignee_type` | `PROJECT`\|`FOLDER`\|`ORGANIZATION` | | Assignee type for the reservation assignment. |
| `--assignee_id` | ID | | Project/folder/organization ID assigned to the reservation. |
| `--reservation_id` | `project:location.reservation` | | Reservation the assignment is created for. |
| `--priority` | `HIGH`\|`INTERACTIVE`\|`BATCH` | | Default job priority of the reservation assignment (HIGH is allowlisted). |
| `--connection_type` | `CLOUD_SQL`\|`AWS`\|`Azure`\|`SQL_DATA_SOURCE`\|`CLOUD_SPANNER`\|`CLOUD_RESOURCE`\|`SPARK` | | Type of the connection. |
| `--properties` | JSON | | Connection properties. |
| `--connection_credential` | JSON | | Connection credential, e.g. `{"username":"u","password":"p"}`. |
| `--connector_configuration` | JSON | | Connector configuration for connector-based connections. |
| `--kms_key_name` | KEY | | Cloud KMS key used for connection encryption. |
| `--policy_id` | ID | | Row access policy ID to create (with `--row_access_policy`). |
| `--target_table` | TABLE | | Table the row access policy applies to. |
| `--grantees` | `user:...,group:...` | | Initial iam_member grantees of the row access policy. |
| `--filter_predicate` | SQL bool expr | | Row filter of the row access policy, e.g. `Region="US"`. |
| `--config_file` | file | | JSON definition of the migration workflow to create. |

**Examples:**
```bash
bq mk new_dataset
bq mk new_dataset.new_table
bq mk -t new_dataset.newtable name:integer,value:string
bq mk -d --data_location=EU new_dataset
bq mk --view='select 1 as num' new_dataset.newview
bq mk --materialized_view='select sum(x) as sum_x from dataset.table' new_dataset.newview
bq mk --transfer_config --target_dataset=dataset --display_name=name \
    -p='{"param":"value"}' --data_source=source
bq mk --transfer_run --start_time=2019-01-20T06:50:00Z --end_time=2019-01-21T06:50:00Z \
    projects/p/locations/l/transferConfigs/c
bq mk --reservation --project_id=project --location=us --slots=100 reservation_name
bq mk --reservation_assignment --reservation_id=project:us.dev \
    --job_type=QUERY --assignee_type=PROJECT --assignee_id=myproject
bq mk --connection --connection_type='CLOUD_SQL' \
    --properties='{"instanceId":"instance","database":"db","type":"MYSQL"}' \
    --connection_credential='{"username":"u","password":"p"}' \
    --project_id=proj --location=us --display_name=name new_connection
bq mk --row_access_policy --policy_id=new_policy \
    --target_table='existing_dataset.existing_table' \
    --grantees='user:user1@google.com' --filter_predicate='Region="US"'
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_mk)

---
### `bq mkdef`

Emit a JSON definition for an external table, such as GCS.

Prints an external-table definition with the most commonly used option values to stdout. Redirect it to a file and pass it to the `--external_table_definition` flag of `bq mk` or `bq query`; edit the JSON to override option values. `SOURCE_URIS` is a comma-separated list of URIs; `SCHEMA` is an inline text schema or a JSON schema file (omit with `--autodetect`).

**Synopsis:**
```
bq mkdef [FLAGS] SOURCE_URIS [SCHEMA]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source_format` | `CSV`\|`GOOGLE_SHEETS`\|`NEWLINE_DELIMITED_JSON`\|`DATASTORE_BACKUP`\|`DELTA_LAKE`\|`ORC`\|`PARQUET`\|`ICEBERG`\|`AVRO` | `CSV` | Format of the source data. |
| `--autodetect` | boolean | | Autodetect schema and format options. |
| `--connection_id` | CONNECTION | | Connection for reading external storage (Azure Blob, GCS, S3): `project.location.connection` or full resource path. |
| `-E`, `--encoding` | `UTF-8`\|`ISO-8859-1`\|`UTF-16BE`\|`UTF-16LE`\|`UTF-32BE`\|`UTF-32LE` | | Character encoding of the input files. |
| `-i`, `--ignore_unknown_values` | boolean | | Ignore values in a row that are not present in the schema. |
| `--metadata_cache_mode` | `AUTOMATIC`\|`MANUAL` | | Metadata caching for an external table with a connection. |
| `--object_metadata` | `SIMPLE` | | Emit an Object Table definition. |
| `--hive_partitioning_mode` | `AUTO`\|`STRINGS` | | Enable hive partitioning: infer key types, or treat all keys as STRING. |
| `--hive_partitioning_source_uri_prefix` | URI prefix | | Prefix after which hive partition encoding begins. |
| `--require_hive_partition_filter` | boolean | | Require a hive partition key in query predicates. |
| `--file_set_spec_type` | `FILE_SYSTEM_MATCH`\|`NEW_LINE_DELIMITED_MANIFEST` | `FILE_SYSTEM_MATCH` | How to discover files from source URIs. |
| `--reference_file_schema_uri` | URI | | Reference file with the expected table schema (AVRO, PARQUET, ORC). |
| `--use_avro_logical_types` | boolean | `true` | For AVRO, interpret logical types instead of raw types. |
| `--parquet_enable_list_inference` | boolean | `false` | Parquet LIST logical-type inference. |
| `--parquet_enum_as_string` | boolean | `false` | Infer Parquet ENUM as STRING instead of BYTES. |
| `--parquet_map_target_type` | `ARRAY_OF_STRUCT` | | Represent Parquet maps as repeated key/value structs. |
| `--preserve_ascii_control_characters` | boolean | `false` | Preserve ASCII control characters in CSV data. |
| `--null_marker` / `--null_markers` | STRING(s) | | Custom NULL representations in CSV data. |
| `--source_column_match` | `POSITION`\|`NAME` | | Column-to-schema matching strategy for CSV data. |
| `--date_format` / `--datetime_format` / `--time_format` / `--timestamp_format` | format string | | Input format elements for DATE / DATETIME / TIME / TIMESTAMP values. |
| `--time_zone` | TZ name | | Default time zone for timestamps with no zone. |
| `--timestamp_target_precision` | `[6]`\|`[12]`\|`[6, 12]` | `[6]` | Target TIMESTAMP precision(s) for autodetection (CSV). |

**Examples:**
```bash
bq mkdef 'gs://bucket/file.csv' field1:integer,field2:string
bq mkdef --source_format=PARQUET --autodetect 'gs://bucket/data/*.parquet' > tabledef.json
bq mk --external_table_definition=tabledef.json mydataset.exttable
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_mkdef)

---
### `bq partition`

Copy date/time-sharded source tables into a partitioned table.

Copies tables named `<source_table_prefix><time_unit_suffix>` into a destination partitioned table, with each source table's suffix becoming the partition ID. The suffix is `YYYYmmdd` by default, `YYYY` with `--time_partitioning_type=YEAR`, `YYYYmm` with MONTH, `YYYYmmddHH` with HOUR. If the destination does not exist, it is created with the schema of the last matching source table.

**Synopsis:**
```
bq partition [FLAGS] SOURCE_TABLE_PREFIX DESTINATION_PARTITIONED_TABLE
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-n`, `--no_clobber` | boolean | `false` | Do not overwrite an existing partition. |
| `--time_partitioning_type` | `DAY`\|`HOUR`\|`MONTH`\|`YEAR` | `DAY` | Partitioning granularity (also selects the expected suffix format). |
| `--time_partitioning_expiration` | integer (seconds) | | Keep partition storage for this long past the partition time. |

**Examples:**
```bash
bq partition dataset1.sharded_ dataset2.partitioned_table
bq partition --time_partitioning_type=MONTH ds.monthly_ ds.partitioned
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_partition)

---
### `bq query`

Execute a query.

Runs a query job from SQL given on the command line or on stdin, prints the results, and (optionally) writes them to a destination table. **Dialect gotcha:** without `--nouse_legacy_sql` / `--use_legacy_sql=false` (or a `#standardSQL` prefix in the query), the query runs as **legacy SQL**. To cancel a running query job, use `bq cancel JOB_ID`.

**Synopsis:**
```
bq query [FLAGS] [SQL_QUERY]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--nouse_legacy_sql` / `--use_legacy_sql=false` | boolean | legacy SQL | Run the query as GoogleSQL. If unset, the dialect comes from query prefixes, else legacy SQL. |
| `--dry_run` | boolean | | Validate the query without running it and report the bytes that would be processed. |
| `--parameter` | file or `name:type:value` | | Query parameter (repeatable), or a file with a JSON list of parameters. Empty name = positional; omitted type = STRING (`name::value`); value `NULL` = null. |
| `--destination_table` | TABLE | temp table | Write results to this table. |
| `--destination_schema` | file or `name[:type],...` | | Schema for the destination table. |
| `--append_table` | boolean | `false` | Append results to the destination table. |
| `--replace` | boolean | `false` | Erase existing contents (and metadata) of the destination table before writing. |
| `--replace_data` | boolean | `false` | Erase existing contents only; keep schema and other metadata. |
| `--schema_update_option` | `ALLOW_FIELD_ADDITION`\|`ALLOW_FIELD_RELAXATION` | | When appending or replacing a partition, update the destination schema from the results (repeatable). |
| `--destination_kms_key` | KEY | | Cloud KMS key for encryption of the destination table data. |
| `-n`, `--max_rows` | integer | `100` | Rows to return in the result. |
| `-s`, `--start_row` | integer | `0` | First row to return. |
| `--use_cache` | boolean | | Use the query cache for previously cached queries. |
| `--require_cache` | boolean | | Only run the query if it is already cached. |
| `--batch` | boolean | | Run in batch mode (ignored if `--priority` is given). |
| `--priority` | `HIGH`\|`INTERACTIVE`\|`BATCH` | via `--batch` | Query priority (HIGH only for allowlisted reservations). |
| `--maximum_bytes_billed` | integer | | Upper limit of bytes billed; the query fails beyond it. |
| `--maximum_billing_tier` | integer | | Upper limit of billing tier (legacy SQL). |
| `--job_timeout_ms` | integer | | Maximum time to run the entire script. |
| `--label` | `key:value` | | Label on the query job (repeatable). |
| `--time_partitioning_type` / `--time_partitioning_field` / `--time_partitioning_expiration` | see `bq load` | | Time partitioning for the destination table. |
| `--range_partitioning` | `field,start,end,interval` | | Integer-range partitioning for the destination table. |
| `--clustering_fields` | FIELD,... | | Clustering columns for the destination table. |
| `--require_partition_filter` | boolean | | Require a partition filter for queries over the destination table. |
| `--external_table_definition` | `NAME::DEF` | | Define a temporary external table usable in the query: `table::path_to_def_file` or `table::schema@format=uri@connection` (repeatable). |
| `--udf_resource` | URI or path | | Code file loaded as a legacy-SQL UDF resource (repeatable). |
| `--create_session` | boolean | | Create a new session and run the query in it. |
| `--session_id` | SESSION | | Run the query in an existing session. |
| `--connection_property` | `key=value` | | Connection properties (repeatable), e.g. `session_id=...`. |
| `--continuous` | boolean | `false` | Run as a continuous query. |
| `--job_creation_mode` | `job_creation_required`\|`job_creation_optional` | | `JOB_CREATION_OPTIONAL` may speed up the query by letting the engine bypass job creation. |
| `--max_child_jobs` | integer | `1000` | Max child jobs to fetch results from after a script; beyond it only the final result is shown. |
| `--max_statement_results` | integer | `100` | Max script statements to display results for. |
| `--script_statement_timeout_ms` / `--script_statement_byte_budget` | integer | | Per-statement time / billed-bytes limits in a script. |
| `--schedule` | schedule string | | Create a scheduled query with this schedule (e.g. `every 24 hours`). |
| `--display_name` | NAME | | Display name of the created scheduled-query config. |
| `--target_dataset` | DATASET | | Target dataset for the scheduled query. |
| `--no_auto_scheduling` | boolean | `false` | Create the scheduled-query config with automatic scheduling disabled. |
| `--allow_large_results` | boolean | | Enable larger destination-table sizes for legacy SQL queries. |
| `--flatten_results` | boolean | flatten | Flatten nested/repeated fields in results (legacy SQL). |
| `--min_completion_ratio` | number 0–1.0 | server (`1.0`) | *(Experimental)* Minimum fraction of data that must be scanned before the query returns. |
| `--rpc` | boolean | `false` | Use the rpc-style `jobs.query` API instead of `jobs.insert`. |
| `--request_id` | ID | | Request ID for `jobs.query` (only with `--rpc`). |
| `--reservation_id` | RESERVATION | | Reservation to run the job in: `project_id:reservation_id`, `project_id:location.reservation_id`, or `reservation_id`. |

**Examples:**
```bash
bq query --nouse_legacy_sql \
    'SELECT COUNT(*) FROM `bigquery-public-data.samples.shakespeare`'

echo 'SELECT 1' | bq query --nouse_legacy_sql

# Dry run: estimate cost
bq query --nouse_legacy_sql --dry_run 'SELECT * FROM `proj.ds.t`'

# Parameterized
bq query --nouse_legacy_sql --parameter='corpus::hamlet' \
    'SELECT word FROM `bigquery-public-data.samples.shakespeare` WHERE corpus = @corpus'

# Write results to a table, appending
bq query --nouse_legacy_sql --destination_table=ds.results --append_table 'SELECT ...'

# Batch priority with a cost cap
bq query --nouse_legacy_sql --batch --maximum_bytes_billed=10000000 'SELECT ...'
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_query)

---
### `bq remove-iam-policy-binding`

Remove a binding from a BigQuery resource's policy in IAM.

Retrieves the IAM policy for a table or view and removes one binding (member + role) from it in a single step. Does not support datasets.

**Synopsis:**
```
bq remove-iam-policy-binding --member=MEMBER_TYPE:MEMBER --role=ROLE
    [-t | --connection | --reservation | --routine] IDENTIFIER
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | MEMBER | | Member part of the binding: `user:<email>`, `group:<email>`, `serviceAccount:<email>`, `domain:<domain>`, `allAuthenticatedUsers`, or `allUsers`. |
| `--role` | ROLE | | Role part of the binding: predefined or custom role (see `bq add-iam-policy-binding`). |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-t`, `--table` | boolean | `false` | Treat the identifier as a table. |
| `--connection` | boolean | `false` | Treat the identifier as a connection. |
| `-d`, `--dataset` | boolean | `false` | Treat the identifier as a dataset (not fully supported per the official reference). |
| `--reservation` | boolean | `false` | Treat the identifier as a reservation. |
| `--routine` | boolean | `false` | Treat the identifier as a routine. |

**Examples:**
```bash
bq remove-iam-policy-binding \
    --member='user:myaccount@gmail.com' \
    --role='roles/bigquery.dataViewer' \
    mydataset.mytable

bq remove-iam-policy-binding \
    --member='allAuthenticatedUsers' \
    --role='roles/bigquery.dataViewer' \
    --project_id=proj -t ds.table1
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_remove-iam-policy-binding)

---
### `bq rm`

Delete the resource described by the identifier.

Always requires an identifier (unlike `show` and `ls`) and prompts for confirmation unless `-f`. The boolean type flags disambiguate what the identifier refers to; `-r` removes a dataset together with all its tables.

**Synopsis:**
```
bq rm [FLAGS] IDENTIFIER
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-f`, `--force` | boolean | | Delete without prompting for confirmation. |
| `-r`, `--recursive` | boolean | `false` | Remove a dataset and any tables it contains. |
| `-d`, `--dataset` | boolean | `false` | Identifier is a dataset. |
| `-t`, `--table` | boolean | `false` | Identifier is a table. |
| `-j`, `--job` | boolean | `false` | Identifier is a job. |
| `-m`, `--model` | boolean | `false` | Identifier is a model. |
| `--routine` | boolean | `false` | Identifier is a routine. |
| `--transfer_config` | boolean | `false` | Identifier is a transfer configuration resource name. |
| `--connection` | boolean | `false` | Identifier is a connection. |
| `--reservation` | boolean | `false` | Identifier is a reservation. |
| `--reservation_assignment` | boolean | `false` | Identifier is a reservation assignment. |
| `--reservation_group` | boolean | `false` | Identifier is a reservation group. |
| `--capacity_commitment` | boolean | `false` | Identifier is a capacity commitment. |
| `--migration_workflow` | boolean | `false` | Identifier is a migration workflow. |

**Examples:**
```bash
bq rm ds.table
bq rm -m ds.model
bq rm --routine ds.routine
bq rm -r -f old_dataset                        # dataset + tables, no prompt
bq rm --transfer_config projects/p/locations/l/transferConfigs/c
bq rm --connection --project_id=proj --location=us con
bq rm --reservation --project_id=proj --location=us reservation_name
bq rm --capacity_commitment proj:US.capacity_commitment_id
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_rm)

---
### `bq set-iam-policy`

Set the IAM policy for a resource.

Replaces the IAM policy of a dataset, table, view, routine, connection, or reservation with the JSON policy in `FILENAME`, then prints the new policy. If the policy file contains an `etag`, it must match the current policy's etag (get it with `bq get-iam-policy`) — this prevents clobbering concurrent updates.

**Synopsis:**
```
bq set-iam-policy [-t | -d | --connection | --reservation | --routine] IDENTIFIER FILENAME
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-t`, `--table` | boolean | `false` | Identifier is a table. |
| `-d`, `--dataset` | boolean | `false` | Identifier is a dataset. |
| `--connection` | boolean | `false` | Identifier is a connection. |
| `--reservation` | boolean | `false` | Identifier is a reservation. |
| `--routine` | boolean | `false` | Identifier is a routine. |

**Examples:**
```bash
bq set-iam-policy ds.table1 /tmp/policy.json
bq set-iam-policy --project_id=proj -t ds.table1 /tmp/policy.json
bq set-iam-policy --reservation proj:US.reservation1 /tmp/policy.json
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_set-iam-policy)

---
### `bq shell`

Start an interactive bq session.

REPL where you enter commands without the leading `bq` (e.g. `ls`, `query 'SELECT 1'`). Exit with `exit` or Ctrl+D. Not listed on the web reference command list; documented via `bq help`.

**Synopsis:**
```
bq shell [--prompt=PROMPT]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--prompt` | STRING | project id | Prompt to use for the BigQuery shell. |

**Examples:**
```bash
bq shell
```

---
### `bq show`

Show all information about an object.

Prints details of a dataset, table, view, materialized view, model, routine, job, transfer config/run, reservation, capacity commitment, connection, or row access policy. `--schema` limits table output to just the schema; combine with `--format=prettyjson` for machine-readable metadata. The global `--location` flag is required when showing jobs with `-j`.

**Synopsis:**
```
bq show [FLAGS] [IDENTIFIER]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--schema` | boolean | `false` | Show only the table schema instead of general table details. |
| `-j`, `--job` | boolean | `false` | Interpret the identifier as a job ID. |
| `-d`, `--dataset` | boolean | `false` | Show a dataset. |
| `--dataset_view` | `METADATA`\|`ACL`\|`FULL` | `FULL` | Which dataset information to return. |
| `--view` | boolean | `false` | Show view-specific details. |
| `--materialized_view` | boolean | `false` | Show materialized-view-specific details. |
| `--table_replica` | boolean | `false` | Show table-replica-specific details. |
| `-m`, `--model` | boolean | `false` | Show details of a model. |
| `--routine` | boolean | `false` | Show details of a routine. |
| `--transfer_config` | boolean | `false` | Show a transfer configuration resource name. |
| `--transfer_run` | boolean | `false` | Show a transfer run. |
| `--connection` | boolean | `false` | Show a connection. |
| `--reservation` | boolean | `false` | Show a reservation. |
| `--reservation_assignment` | boolean | | Look up reservation assignments for a project/folder/organization (explicit, else inherited); use with `--job_type`, `--assignee_type`, `--assignee_id`. |
| `--reservation_group` | boolean | | Show a reservation group. |
| `--capacity_commitment` | boolean | | Show a capacity commitment. |
| `--job_type` | `QUERY`\|`PIPELINE`\|`ML_EXTERNAL`\|`BACKGROUND`\|`SPARK`\|`CONTINUOUS`\|... | | Job type to search reservation assignments for. |
| `--assignee_type` | `PROJECT`\|`FOLDER`\|`ORGANIZATION` | | Assignee type for the reservation-assignment lookup. |
| `--assignee_id` | ID | | Assignee ID for the reservation-assignment lookup. |
| `--encryption_service_account` | boolean | `false` | Show (creating if needed) the BigQuery encryption service account for the project. |
| `--migration_workflow` | boolean | | Show a migration workflow. |

**Examples:**
```bash
bq show mydataset
bq show mydataset.mytable
bq show --schema --format=prettyjson mydataset.mytable
bq show --view mydataset.myview
bq show -j --location=US job_id
bq show -m ds.model
bq show --routine ds.routine
bq show --transfer_config projects/p/locations/l/transferConfigs/c
bq show --encryption_service_account
bq show --reservation --location=US --project_id=project reservation_name
bq show --connection --project_id=project --location=us connection
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_show)

---
### `bq truncate`

Truncate a table/dataset/project back to a particular timestamp.

Point-in-time rollback used with cross-region dataset replication: rewinds tables to `--timestamp` (or the recommended timestamp with `--dry_run`). Without `--overwrite`, output tables get the timestamp appended to their names instead of being replaced. Not listed on the web reference command list; documented via `bq help`.

**Synopsis:**
```
bq truncate [FLAGS] PROJECT_ID:DATASET[.TABLE]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-t`, `--timestamp` | integer (ms since epoch) | recommended | Timestamp to truncate table(s) to. |
| `--dry_run` | boolean | | No-op that prints the plan and the recommended timestamp without modifying anything. |
| `--overwrite` | boolean | `false` | Overwrite existing tables instead of writing timestamp-suffixed copies. |
| `-s`, `--skip_fully_replicated_tables` | boolean | `true` | Skip tables that are fully replicated and need no truncation (faster, but tables may end up at different points in time). |

**Examples:**
```bash
bq truncate project_id:dataset
bq truncate --overwrite project_id:dataset --timestamp 123456789
bq truncate --skip_fully_replicated_tables=false project_id:dataset
```

---
### `bq undelete`

Undelete a dataset.

Restores the dataset described by the identifier, optionally at a specific deletion timestamp (milliseconds since epoch); by default restores the most recently deleted version. Always requires an identifier and prompts for confirmation. Not listed on the web reference command list; documented via `bq help`.

**Synopsis:**
```
bq undelete [--timestamp=MILLISECONDS] DATASET
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--timestamp` | integer (ms since epoch) | most recent deletion | Timestamp version of the dataset to restore. |

**Examples:**
```bash
bq undelete dataset
bq undelete --timestamp 1714720875568 dataset
```

---
### `bq update`

Update a dataset, table, view, model, or transfer configuration with this name.

The mutating counterpart of `bq mk` — the same resource-type boolean flags select what to update. For tables, passing a schema (positional or `--schema`) replaces the schema; `--view`/`--materialized_view` update the defining SQL; label/tag flags add and remove metadata; reservation/commitment/connection/row-access-policy flags mirror `bq mk` semantics unless noted.

**Synopsis:**
```
bq update [FLAGS] IDENTIFIER [SCHEMA]
```

**Optional flags — resource type selectors:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `-d`, `--dataset` | boolean | `false` | Update a dataset. |
| `-t`, `--table` | boolean | `false` | Update a table. |
| `-m`, `--model` | boolean | `false` | Update a model. |
| `--view` | SQL | | Update the view's SQL query. |
| `--materialized_view` | SQL | | Update the materialized view's SQL query. |
| `--transfer_config` | boolean | `false` | Update a transfer configuration resource name. |
| `--reservation` | boolean | | Update a reservation. |
| `--reservation_assignment` | boolean | | Move a reservation assignment to `--destination_reservation_id`. |
| `--capacity_commitment` | boolean | | Update (or `--split`/`--merge`) a capacity commitment. |
| `--connection` | boolean | | Update a connection. |
| `--row_access_policy` | boolean | | Update a row access policy. |

**Optional flags — datasets, tables, views:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | TEXT | | Description of the dataset, table, view, or connection. |
| `--expiration` | integer (seconds) | | Expiration of the table/view, in seconds from now; `0` removes the expiration. |
| `--default_table_expiration` | integer (seconds) | | Dataset default table lifetime; `0` removes it. |
| `--default_partition_expiration` | integer (seconds) | | Dataset default partition expiration; `0` removes it. |
| `--default_kms_key` | KEY | | Dataset default KMS key for new objects. |
| `--max_time_travel_hours` | integer (48–168) | `168` | Dataset time-travel window in hours. |
| `--storage_billing_model` | `LOGICAL`\|`PHYSICAL` | | Dataset storage billing model. |
| `--update_mode` | `update_metadata`\|`update_acl`\|`update_full` | `UPDATE_FULL` | Which dataset fields to update. |
| `--set_label` | `key:value` | | Label to set on the dataset/table (repeatable). |
| `--clear_label` | KEY | | Label key to remove (repeatable). |
| `--add_tags` / `--remove_tags` | `ns/key[:value],...` | | Attach / detach namespaced tags on the dataset or table. |
| `--clear_all_tags` | boolean | `false` | Clear all tags attached to the dataset or table. |
| `--schema` | file or `name[:type],...` | | New table schema (also accepted positionally). |
| `--autodetect_schema` | boolean | `false` | Autodetect the schema instead of leaving it unchanged. |
| `--time_partitioning_type` / `--time_partitioning_field` / `--time_partitioning_expiration` | see `bq mk` | | Time-partitioning settings; negative expiration means no expiration. |
| `--range_partitioning` | `field,start,end,interval` | | Integer-range partitioning. |
| `--require_partition_filter` | boolean | | Require a partition filter for queries over the table. |
| `--clustering_fields` | FIELD,... | | Clustering columns; empty value removes clustering. |
| `--destination_kms_key` | KEY | | Cloud KMS key for the table data. |
| `--external_table_definition` | file or `schema@format=uri@connection` | | Update an external table from a definition file or inline spec. |
| `--metadata_cache_mode` | `AUTOMATIC`\|`MANUAL` | | Metadata caching (requires `--external_table_definition`). |
| `--max_staleness` | INTERVAL | none | Max staleness for a materialized view or external table (requires `--external_table_definition` for external tables). |
| `--object_metadata` | `SIMPLE` | | Object Table metadata type. |
| `--external_catalog_dataset_options` / `--external_catalog_table_options` | JSON or file | | Open-source-catalog metadata for the dataset / table. |
| `--enable_refresh` | boolean | `true` | Automatic refresh of a materialized view when the base table changes. |
| `--refresh_interval_ms` | integer | `1800000` | Minimum interval between automatic materialized-view refreshes. |
| `--view_udf_resource` | URI or path | | UDF resource used by the view (repeatable). |
| `--use_legacy_sql` | boolean | server default | Dialect of the `--view` query; use `--use_legacy_sql=false` for GoogleSQL. |
| `--vertex_ai_model_id` | ID | | Vertex AI model ID to register a BigQuery ML model under. |
| `--etag` | ETAG | | Only update if the etag matches. |
| `--source` | file | | Path to a file with the JSON payload for the update. |

**Optional flags — transfer configs:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display_name` | NAME | | Updated display name of the transfer config or connection. |
| `--target_dataset` | DATASET | | Updated dataset ID of the transfer config. |
| `-p`, `--params` | JSON | | Updated parameters, e.g. `--params='{"param":"value"}'`. |
| `--schedule` | schedule string | | Updated transfer schedule. |
| `--schedule_start_time` / `--schedule_end_time` | RFC3339 UTC | | Updated scheduling window. |
| `--no_auto_scheduling` | boolean | `false` | Disable automatic scheduling of transfer runs. |
| `--event_driven_schedule` | JSON | | Event-driven schedule; mutually exclusive with `--schedule`/`--no_auto_scheduling`/start/end times. |
| `--refresh_window_days` | integer | | Updated refresh window days. |
| `--update_credentials` | boolean | `false` | Update the transfer configuration credentials. |
| `--service_account_name` | EMAIL | | Service account used as the transfer-config credential. |
| `--notification_pubsub_topic` | TOPIC | | Pub/Sub topic notified after a transfer run completes or fails. |

**Optional flags — reservations, commitments, connections, row access policies:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--slots` | integer | | Baseline slots of the reservation (or `--split` part size). |
| `--autoscale_max_slots` | integer | | Autoscale slot ceiling. |
| `--ignore_idle_slots` / `--use_idle_slots` | boolean | use idle | Whether queries in the reservation may use idle slots from other reservations. |
| `--target_job_concurrency` | integer | auto (`0`) | Soft cap on concurrent jobs. (`--concurrency`/`--max_concurrency` deprecated synonyms.) |
| `--scheduling_policy_concurrency` / `--scheduling_policy_max_slots` | integer | | Per-project caps within the reservation. |
| `--max_slots` + `--scaling_mode` | integer + `SCALING_MODE_UNSPECIFIED`\|`AUTOSCALE_ONLY`\|`IDLE_SLOTS_ONLY`\|`ALL_SLOTS` | | *(Preview)* Overall max slots with scaling mode; mutually exclusive with `--autoscale_max_slots`. |
| `--reservation_group_name` | NAME | | Move the reservation into this reservation group. |
| `--bi_reservation_size` | bytes or `NG` | | BI Engine reservation size (min 1 GB; `0` removes it). (`--reservation_size` deprecated.) |
| `--destination_reservation_id` | RESERVATION | | Target reservation for `--reservation_assignment` moves. |
| `--priority` | `HIGH`\|`INTERACTIVE`\|`BATCH`\|`''` | | Reservation-assignment default job priority; empty string unsets it. |
| `--plan` | `MONTHLY`\|`ANNUAL`\|`THREE_YEAR` | | Commitment plan; can only move to a longer committed period. |
| `--renewal_plan` | `NONE`\|`FLEX`\|`MONTHLY`\|`ANNUAL`\|`THREE_YEAR` | | Plan after the committed period ends (NONE only with `--edition`; FLEX/MONTHLY not with `--edition`). |
| `--split` | boolean | | Split a capacity commitment in two; sizes set by `--slots`. |
| `--merge` | boolean | | Merge two or more comma-separated capacity commitments into one. |
| `--connection_type` | `CLOUD_SQL`\|`AWS`\|`Azure`\|`SQL_DATA_SOURCE`\|`CLOUD_SPANNER`\|`CLOUD_RESOURCE`\|`SPARK` | | Connection type. |
| `--properties` / `--connection_credential` / `--connector_configuration` | JSON | | Connection properties / credential / connector configuration. |
| `--kms_key_name` | KEY | | Cloud KMS key used for connection encryption. |
| `--policy_id` / `--target_table` / `--grantees` / `--filter_predicate` | see `bq mk` | | Row access policy identity, table, grantees, and row filter. |

**Examples:**
```bash
bq update --description "Dataset description" existing_dataset
bq update --description "My table" existing_dataset.existing_table
bq update -t existing_dataset.existing_table name:integer,value:string
bq update --set_label=env:prod --clear_label=tmp existing_dataset
bq update --view='select 1 as num' existing_dataset.existing_view
bq update --expiration 0 existing_dataset.existing_table        # remove expiry
bq update --transfer_config --display_name=name -p='{"param":"value"}' \
    projects/p/locations/l/transferConfigs/c
bq update --reservation --location=US --project_id=my-project \
    --bi_reservation_size=2G
bq update --capacity_commitment --location=US --project_id=my-project \
    --plan=MONTHLY --renewal_plan=FLEX commitment_id
bq update --reservation_assignment \
    --destination_reservation_id=proj:US.new_reservation \
    proj:US.old_reservation.assignment_id
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_update)

---
### `bq version`

Return the version of bq.

No command-specific flags.

**Synopsis:**
```
bq version
```

**Examples:**
```bash
bq version    # e.g. "This is BigQuery CLI 2.1.27"
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_version)

---
### `bq wait`

Wait some number of seconds for a job to finish.

Polls `JOB_ID` until the job is DONE or `SECS` seconds have elapsed; waits forever if `SECS` is omitted. With no `JOB_ID` and exactly one running job, polls that job. `SECS` of `0` polls once and returns immediately. With `--fail_on_error` (the default) the exit code reflects job success — the standard way to join on a `--nosync` job in scripts.

**Synopsis:**
```
bq wait [FLAGS] [JOB_ID] [SECS]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fail_on_error` | boolean | `true` | After waiting, exit nonzero if the job is still running or ended in failure. |
| `--wait_for_status` | STATUS | `DONE` | Wait for the job to reach this status (e.g. `RUNNING`, `DONE`). |

**Examples:**
```bash
bq wait                          # waits forever for the one running job
bq wait job_id                   # waits forever
bq wait job_id 100               # waits up to 100 seconds
bq wait job_id 0                 # polls once, returns immediately
bq wait --fail_on_error job_id   # exit code reflects job success
bq wait --wait_for_status=RUNNING job_id
```

[Official reference](https://docs.cloud.google.com/bigquery/docs/reference/bq-cli-reference#bq_wait)

---
