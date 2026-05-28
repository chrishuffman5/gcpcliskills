# gcloud logging metrics

manages logs-based metrics

### `gcloud logging metrics create`

Create a logs-based metric

Create a logs-based metric to count the number of log entries that match a
filter expression. Logs-based metrics can also be used to extract values
from logs and create a distribution of the values.

**Synopsis:**
```
gcloud logging metrics create METRIC_NAME
    (--config-from-file=PATH_TO_FILE
      | [--description=DESCRIPTION --log-filter=LOG_FILTER
      : --bucket-name=BUCKET_NAME]) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
METRIC_NAME
   The name of the new metric.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ A path to a YAML or JSON file specifying the logs-based metric to create. Use a full or relative path to a local file containing the value of config. |


**Examples:**
```bash
To create a metric that counts the number of log entries with a severity
level higher than WARNING, run:

    $ gcloud logging metrics create high_severity_count \
        --description="Number of high severity log entries" \
        --log-filter="severity > WARNING"

Detailed information about filters can be found at:
https://cloud.google.com/logging/docs/view/logging-query-language

To create a metric that uses advanced features like distribution or
user-defined labels, run:

    $ gcloud logging metrics create my_metric \
        --config-from-file=$PATH_TO_FILE

The config file can be in YAML or JSON format. Detailed information about
how to configure metrics can be found at:
https://cloud.google.com/logging/docs/reference/v2/rest/v2/projects.metrics#LogMetric.

To create a bucket log-based metric, run:

    $ gcloud logging metrics create my_bucket_metric \
        --description="DESCRIPTION" --log-filter="LOG_FILTER" \
        --bucket-name="BUCKET_NAME"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/metrics/create)

---
### `gcloud logging metrics delete`

Delete a logs-based metric

Delete a logs-based metric called high_severity_count.

**Synopsis:**
```
gcloud logging metrics delete METRIC_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
METRIC_NAME
   The name of the metric to delete.
```

**Examples:**
```bash
To delete a metric called high_severity_count, run:

    $ gcloud logging metrics delete high_severity_count
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/metrics/delete)

---
### `gcloud logging metrics describe`

Display the definition of a logs-based metric

Show the definition of a logs-based metric.

**Synopsis:**
```
gcloud logging metrics describe METRIC_NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
METRIC_NAME
   The name of the metric.
```

**Examples:**
```bash
To show the definition of a metric called high_severity_count, run:

    $ gcloud logging metrics describe high_severity_count
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/metrics/describe)

---
### `gcloud logging metrics list`

Display all logs-based metrics

List all logs-based metrics.

**Synopsis:**
```
gcloud logging metrics list [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list the top 10 logs-based metrics, run:

    $ gcloud logging metrics list --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/metrics/list)

---
### `gcloud logging metrics update`

Update the definition of a logs-based metric

Update the description or the filter expression of an existing logs-based
metric.

**Synopsis:**
```
gcloud logging metrics update METRIC_NAME
    (--config-from-file=PATH_TO_FILE | --bucket-name=BUCKET_NAME
      --description=DESCRIPTION --log-filter=LOG_FILTER)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
METRIC_NAME
   The name of the log-based metric to update.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ A path to a YAML file specifying the updates to be made to the logs-based metric. Use a full or relative path to a local file containing the value of config. |


**Examples:**
```bash
To update the description of a metric called high_severity_count, run:

    $ gcloud logging metrics update high_severity_count \
        --description="Count of high-severity log entries."

To update the filter expression of the metric, run:

    $ gcloud logging metrics update high_severity_count \
        --log-filter="severity >= WARNING"

Detailed information about filters can be found at:
https://cloud.google.com/logging/docs/view/logging-query-language

For advanced features such as user-defined labels and distribution metrics,
update using a config file:

    $ gcloud logging metrics update high_severity_count \
        --config-from-file=$PATH_TO_FILE

The config file should be in YAML format. Detailed information about how to
configure metrics can be found at:
https://cloud.google.com/logging/docs/reference/v2/rest/v2/projects.metrics#LogMetric.
Any top-level fields in the LogMetric definition that aren't specified in
the config file will not be updated in the metric.

To update the bucket associated with a bucket log-based metric, run:

    $ gcloud logging metrics update my-bucket-metric \
        --bucket-name="NEW_BUCKET_NAME"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/logging/metrics/update)

---