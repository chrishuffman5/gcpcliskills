# gcloud monitoring snoozes

manage Cloud Monitoring snoozes

### `gcloud monitoring snoozes cancel`

Cancels a snooze

Cancel a snooze.

If the start time is in the future, then this command is equivalent to:

  o update --start-time="+PT1S" --end-time="+PT1S

Otherwise, if the start time is past and the ending time is in the future,
then this command is equivalent to:

  o update --end-time="+PT1S

For information about the JSON/YAML format of a snooze:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.snoozes

**Synopsis:**
```
gcloud monitoring snoozes cancel SNOOZE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snooze resource - Name of the Snooze to be canceled. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument snooze on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNOOZE
     ID of the Snooze or fully qualified identifier for the Snooze.

     To set the snooze attribute:
     + provide the argument snooze on the command line.
```

**Examples:**
```bash
To cancel a snooze, run:

    $ gcloud monitoring snoozes cancel MY-SNOOZE

To cancel a snooze contained within a specific project, run:

    $ gcloud monitoring snoozes cancel MY-SNOOZE --project=MY-PROJECT

To cancel a snooze with a fully qualified snooze ID, run:

    $ gcloud monitoring snoozes cancel \
        projects/MY-PROJECT/snoozes/MY-SNOOZE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/snoozes/cancel)

---
### `gcloud monitoring snoozes create`

Create a new snooze

Creates a new snooze. A snooze can be specified as a JSON/YAML value passed
in as a file through the --snooze-from-file flag. A snooze can also be
specified through command line flags. If a snooze is specified through
--snooze-from-file, and additional flags are supplied, the flags will
override the snooze's settings.

For information about the JSON/YAML format of a snooze:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.snoozes

**Synopsis:**
```
gcloud monitoring snoozes create [--snooze-from-file=PATH_TO_FILE]
    [--criteria-filter=CRITERIA_FILTER
      --criteria-policies=CRITERIA_POLICIES,[...]
      --display-name=DISPLAY_NAME
      --end-time=END_TIME --start-time=START_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snooze-from-file` | PATH_TO_FILE |  | The path to a JSON or YAML file containing the snooze. Use a full or relative path to a local file containing the value of snooze. |


**Examples:**
```bash
To create a snooze with command-line options, run:

    $ gcloud monitoring snoozes create \
        --criteria-policies=LIST_OF_POLICIES --criteria-filter=FILTER \
        --display-name=DISPLAY_NAME --start-time=START_TIME \
        --end-time=END_TIME

To create a snooze with a file, run:

    $ gcloud monitoring snoozes create --snooze-from-file=MY-FILE

Sample contents of MY-FILE:

    criteria:
      policies:
      - projects/MY-PROJECT/alertPolicies/MY-POLICY
      filter: 'resource.labels.zone="us-central1-a" AND resource.labels.instance_id="1234567890"'
    interval:
      startTime: '2024-03-01T08:00:00Z'
      endTime: '2024-03-08T04:59:59.500Z'
    displayName: New Snooze
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/snoozes/create)

---
### `gcloud monitoring snoozes describe`

Describe a snooze

Describe a snooze.

**Synopsis:**
```
gcloud monitoring snoozes describe SNOOZE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snooze resource - Name of the Snooze to be described. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument snooze on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNOOZE
     ID of the Snooze or fully qualified identifier for the Snooze.

     To set the snooze attribute:
     + provide the argument snooze on the command line.
```

**Examples:**
```bash
To describe a snooze, run:

    $ gcloud monitoring snoozes describe MY-SNOOZE

To describe a snooze in JSON, run:

    $ gcloud monitoring snoozes describe MY-SNOOZE --format=json

To describe a snooze contained within a specific project, run:

    $ gcloud monitoring snoozes describe MY-SNOOZE --project=MY-PROJECT

To describe a snooze with a fully qualified snooze ID, run:

    $ gcloud monitoring snoozes describe \
        projects/MY-PROJECT/snoozes/MY-SNOOZE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/snoozes/describe)

---
### `gcloud monitoring snoozes list`

List snoozes

List snoozes.

**Synopsis:**
```
gcloud monitoring snoozes list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To order your results first by the snooze's display name and then the end
time:

    $ gcloud monitoring snoozes list \
        --sort-by=display_name,interval.end_time

To order your results in reverse order, you can add '~' in front of the
field name:

    $ gcloud monitoring snoozes list --sort-by="~display_name"

To return results with expired snoozes only:

    $ gcloud monitoring snoozes list --filter="interval.end_time<+PT1S"

To return results whose display name contain the word 'cloud':

    $ gcloud monitoring snoozes list --filter="display_name:(cloud)"

More information can be found at
https://cloud.google.com/sdk/gcloud/reference/topic/filters
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/snoozes/list)

---
### `gcloud monitoring snoozes update`

Updates a snooze

Update a snooze.

If --snooze-from-file is specified, then the update rules depend on the
value of the (optional) --fields flag:

  o If --fields is specified, then only the specified fields of the
    snooze are updated.
  o Else, all fields of the snooze are replaced. The updated snooze can
    be modified further using the flags from the Snooze Settings group
    below.

Otherwise, the snooze will be updated with the values specified in the
flags from the Snooze Settings group.

For information about the JSON/YAML format of a snooze:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.snoozes

**Synopsis:**
```
gcloud monitoring snoozes update SNOOZE [--snooze-from-file=PATH_TO_FILE]
    [--fields=[field,...] | --display-name=DISPLAY_NAME
      --end-time=END_TIME --start-time=START_TIME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Snooze resource - Name of the Snooze to be updated. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument snooze on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SNOOZE
     ID of the Snooze or fully qualified identifier for the Snooze.

     To set the snooze attribute:
     + provide the argument snooze on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--snooze-from-file` | PATH_TO_FILE |  | The path to a JSON or YAML file containing the snooze. Use a full or relative path to a local file containing the value of snooze. |


**Examples:**
```bash
To update a snooze time interval with command-line options, run:

    $ gcloud monitoring snoozes update MY-SNOOZE \
        --start-time=START_TIME --end-time=END_TIME

To update a snooze display name with a file, run:

    $ gcloud monitoring snoozes update --snooze-from-file=MY-FILE \
        --fields=display_name

Sample contents of MY-FILE:

    criteria:
      policies:
      - projects/MY-PROJECT/alertPolicies/MY-POLICY
    interval:
      startTime: '2024-03-01T08:00:00Z'
      endTime: '2024-03-08T04:59:59.500Z'
    displayName: New Snooze with New Display Name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/snoozes/update)

---