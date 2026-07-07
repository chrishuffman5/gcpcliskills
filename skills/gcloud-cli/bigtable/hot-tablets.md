# gcloud bigtable hot-tablets

manage Cloud Bigtable hot tablets

### `gcloud bigtable hot-tablets list`

List hot tablets in a Cloud Bigtable cluster

List hot tablets in a Cloud Bigtable cluster.

**Synopsis:**
```
gcloud bigtable hot-tablets list (CLUSTER : --instance=INSTANCE)
    [--end-time=END_TIME] [--start-time=START_TIME] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Cluster resource - The cluster to list hot tablets for. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument cluster on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CLUSTER
     ID of the cluster or fully qualified identifier for the cluster.

     To set the cluster attribute:
     + provide the argument cluster on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the cluster.

     To set the instance attribute:
     + provide the argument cluster on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--end-time` | END_TIME |  | End time of the time range to search for hot tablets. See $ gcloud topic datetimes for information on time formats. |
| `--start-time` | START_TIME |  | Start time of the time range to search for hot tablets. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
Search for hot tablets in the past 24 hours:

    $ gcloud bigtable hot-tablets list my-cluster-id \
        --instance=my-instance-id

Search for hot tablets with start and end times by minute:

    $ gcloud bigtable hot-tablets list my-cluster-id \
        --instance=my-instance-id --start-time="2018-08-12 03:30:00" \
        --end-time="2018-08-13 17:00:00"

Search for hot tablets with start and end times by day:

    $ gcloud bigtable hot-tablets list my-cluster-id \
        --instance=my-instance-id --start-time=2018-01-01 \
        --end-time=2018-01-05
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/hot-tablets/list)

---