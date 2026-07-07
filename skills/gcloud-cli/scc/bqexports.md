# gcloud scc bqexports

manage Cloud SCC (Security Command Center) BigQuery exports

### `gcloud scc bqexports create`

Create a Security Command Center BigQuery export

Create a Security Command Center BigQuery export.

BigQuery exports that are created with Security Command Center API V2 and
later include a location attribute. If a location is not specified, the
default global location is used. For example, the following BigQuery export
name has location=global attribute:
organizations/123/locations/global/bigQueryExports/test-bq-export.

**Synopsis:**
```
gcloud scc bqexports create BIG_QUERY_EXPORT --dataset=DATASET
    [--description=DESCRIPTION] [--filter=FILTER]
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BIG_QUERY_EXPORT
   ID of the BigQuery export e.g. my-bq-export or the full resource name
   of the BigQuery export e.g.
   organizations/123/bigQueryExports/my-bq-export.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dataset` | DATASET |  | The dataset to write findings updates to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The text that will be used to describe a BigQuery export. |
| `--filter` | FILTER |  | The filter string which will applied to findings muted by a BigQuery export. |
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
To create a BigQuery export test-bq-export given organization 123 with a
dataset abc in project 234 and filter on category that equals to
XSS_SCRIPTING, run:

    $ gcloud scc bqexports create test-bq-export --organization=123 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\""

To create a BigQuery export test-bq-export given folder 456 with a dataset
abc in project 234 and filter on category that equals to XSS_SCRIPTING,
run:

    $ gcloud scc bqexports create test-bq-export --folder=456 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\""

To create a BigQuery export test-bq-export given project 789 with a dataset
abc in project 234 and filter on category that equals to XSS_SCRIPTING,
run:

    $ gcloud scc bqexports create test-bq-export --project=789 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\""

To create a BigQuery export test-bq-export given organization 123 and
location=global to send findings with category=XSS_SCRIPTING to the
BigQuery dataset abc in project 234, run:

    $ gcloud scc bqexports create test-bq-export --organization=123 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\"" --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/bqexports/create)

---
### `gcloud scc bqexports delete`

Delete a Security Command Center BigQuery export

Delete a Security Command Center BigQuery export.

BigQuery exports that are created with Security Command Center API V2 and
later include a location attribute. If the location attribute is included
in the resource name of a BigQuery export, you must specify it when
referencing the export. For example, the following BigQuery export name has
location=eu: organizations/123/locations/eu/bigQueryExports/test-bq-export.

**Synopsis:**
```
gcloud scc bqexports delete BIG_QUERY_EXPORT
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BIG_QUERY_EXPORT
   ID of the BigQuery export e.g. my-bq-export or the full resource name
   of the BigQuery export e.g.
   organizations/123/bigQueryExports/my-bq-export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
To delete a BigQuery export given organization 123 with id test-bq-export,
run:

    $ gcloud scc bqexports delete test-bq-export --organization=123

To delete a BigQuery export given folder 456 with id test-bq-export, run:

    $ gcloud scc bqexports delete test-bq-export --folder=456

To delete a BigQuery export given project 789 with id test-bq-export, run:

    $ gcloud scc bqexports delete test-bq-export --project=789

To delete the BigQuery export test-bq-export, with location=global, from
organization 123, run:

    $ gcloud scc bqexports delete test-bq-export --organization=123 \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/bqexports/delete)

---
### `gcloud scc bqexports get`

Get a Security Command Center BigQuery export

Get a Security Command Center BigQuery export.

BigQuery exports that are created with Security Command Center API V2 and
later include a location attribute. If the location attribute is included
in the resource name of a BigQuery export, you must specify it when
referencing the export. For example, the following BigQuery export name has
location=eu: organizations/123/locations/eu/bigQueryExports/test-bq-export.

**Synopsis:**
```
gcloud scc bqexports get BIG_QUERY_EXPORT
    [--location=LOCATION; default="global"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BIG_QUERY_EXPORT
   ID of the BigQuery export e.g. my-bq-export or the full resource name
   of the BigQuery export e.g.
   organizations/123/bigQueryExports/my-bq-export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
To get a BigQuery export under given organization 123 with id
test-bq-export, run:

    $ gcloud scc bqexports get test-bq-export --organization=123

To get a BigQuery export under given folder 456 with id test-bq-export,
run:

    $ gcloud scc bqexports get test-bq-export --folder=456

To get a BigQuery export under given project 789 with id test-bq-export,
run:

    $ gcloud scc bqexports get test-bq-export --project=789

To get a BigQuery export under given organization 123 with id
test-bq-export, and location=global run:

    $ gcloud scc bqexports get test-bq-export --organization=123 \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/bqexports/get)

---
### `gcloud scc bqexports list`

List Security Command Center BigQuery exports

List Security Command Center BigQuery exports.

    BigQuery exports that are created with Security Command Center API V2 and
    later include a `location` attribute. Include the `--location` flag to
    list BigQuery exports with `location` attribute other than `global`.

**Synopsis:**
```
gcloud scc bqexports list
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [--location=LOCATION; default="global"] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[Exactly one of these must be specified:]_ Folder where the BigQuery export resides. Formatted as folders/456 or just 456. |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ Organization where the BigQuery export resides. Formatted as organizations/123 or just 123. |
| `--project` | PROJECT |  | _[Exactly one of these must be specified:]_ Project (id or number) where the BigQuery export resides. Formatted as projects/789 or just 789. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |


**Examples:**
```bash
List BigQuery exports under organization 123:

    $ gcloud scc bqexports list --organization=123

List BigQuery exports under folder 456:

    $ gcloud scc bqexports list --folder=456

List BigQuery exports under project 789:

    $ gcloud scc bqexports list --project=789

List BigQuery exports under organization 123 and location global:

    $ gcloud scc bqexports list --organization=123 --location=global

List BigQuery exports under organization 123 and location=eu:

    $ gcloud scc bqexports list --organization=123 --location=eu
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/bqexports/list)

---
### `gcloud scc bqexports update`

Update a Security Command Center BigQuery export

Update a Security Command Center BigQuery export.

BigQuery exports that are created with Security Command Center API V2 and
later include a location attribute. If the location attribute is included
in the resource name of a BigQuery export, you must specify it when
referencing the export. For example, the following BigQuery export name has
location=eu: organizations/123/locations/eu/bigQueryExports/test-bq-export.

**Synopsis:**
```
gcloud scc bqexports update BIG_QUERY_EXPORT [--dataset=DATASET]
    [--description=DESCRIPTION] [--filter=FILTER]
    [--location=LOCATION; default="global"] [--update-mask=UPDATE_MASK]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BIG_QUERY_EXPORT
   ID of the BigQuery export e.g. my-bq-export or the full resource name
   of the BigQuery export e.g.
   organizations/123/bigQueryExports/my-bq-export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dataset` | DATASET |  | The dataset to write findings updates to. |
| `--description` | DESCRIPTION |  | The text that will be used to describe a BigQuery export. |
| `--filter` | FILTER |  | The filter string which will applied to findings muted by a BigQuery export. |
| `--location` | LOCATION | global | When data residency controls are enabled, this attribute specifies the location in which the resource is located and applicable. The location attribute can be provided as part of the fully specified resource name or with the --location argument on the command line. The default location is global. NOTE: If you override the endpoint to a regional endpoint (https://cloud.google.com/security-command-center/docs/reference/rest/index.html?rep_location=global#regional-service-endpoint) you must specify the correct data location (https://cloud.google.com/security-command-center/docs/data-residency-support#locations) using this flag. The default location on this command is unrelated to the default location that is specified when data residency controls are enabled for Security Command Center. NOTE: If no location is specified, the default location is global AND the request will be routed to the SCC V1 API. To use the SCC V2 API - please explicitly specify the flag. |
| `--update-mask` | UPDATE_MASK |  | Optional: If left unspecified (default), an update-mask is automatically created using the flags specified in the command and only those values are updated. |


**Examples:**
```bash
Update a BigQuery export with id test-bq-export under organization 123 with
a dataset abc in project 234 and a filter on category that equals to
XSS_SCRIPTING:

    $ gcloud scc bqexports update test-bq-export --organization=123 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\""

Update a BigQuery export with id test-bq-export under folder 456 with a
dataset abc in project 234 and a filter on category that equals to
XSS_SCRIPTING:

    $ gcloud scc bqexports update test-bq-export --folder=456 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\""

Update a BigQuery export with id test-bq-export under project 789 with a
dataset abc in project 234 and a filter on category that equals to
XSS_SCRIPTING:

    $ gcloud scc bqexports update test-bq-export --project=789 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\""

Update a BigQuery export test-bq-export in organization 123 and
location=global. This command updates the target dataset to
projects/234/datasets/abc, the export description to This is a test
BigQuery export and the export filter to XSS_SCRIPTING:

    $ gcloud scc bqexports update test-bq-export --organization=123 \
        --dataset=projects/234/datasets/abc \
        --description="This is a test BigQuery export" \
        --filter="category=\"XSS_SCRIPTING\"" --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/bqexports/update)

---