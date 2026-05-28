# gcloud monitoring policies

manage Cloud Monitoring alerting policies

### `gcloud monitoring policies create`

Create a new alerting policy

Creates a new alerting policy. An alert policy can be specified as a
JSON/YAML value passed in as a string through the --policy flag or as a
file through the --policy-from-file flag. A basic policy can also be
specified through command line flags. If a policy is specified through
--policy or --policy-from-file, and additional flags are supplied, the
flags will override the policy's settings and a specified condition will be
appended to the list of conditions.

For information about the JSON/YAML format of an alerting policy:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.alertPolicies

**Synopsis:**
```
gcloud monitoring policies create
    [--notification-channels=[NOTIFICATION_CHANNELS,...]]
    [--aggregation=AGGREGATION
      --condition-display-name=CONDITION_DISPLAY_NAME
      --condition-filter=CONDITION_FILTER
      --duration=DURATION --if=IF_VALUE --trigger-count=TRIGGER_COUNT
      | --trigger-percent=TRIGGER_PERCENT]
    [--combiner=COMBINER --display-name=DISPLAY_NAME --no-enabled
      --user-labels=[KEY=VALUE,...]
      --documentation-format=DOCUMENTATION_FORMAT;
      default="text/markdown" --documentation=DOCUMENTATION
      | --documentation-from-file=PATH_TO_FILE]
    [--policy=POLICY | --policy-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--notification-channels` | [NOTIFICATION_CHANNELS,...] |  | _[* set the property core/project.]_ IDs of the Notification Channels or fully qualified identifiers for the Notification Channels. To set the notification_channels attribute: + provide the argument --notification-channels on the command line. |
| `--aggregation` | AGGREGATION |  | _[any conditions are already specified, this condition will be appended.]_ Specifies an Aggregation message as a JSON/YAML value to be applied to the condition. For more information about the format: https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.alertPolicies |
| `--condition-display-name` | CONDITION_DISPLAY_NAME |  | _[any conditions are already specified, this condition will be appended.]_ The display name for the condition. |
| `--condition-filter` | CONDITION_FILTER |  | _[any conditions are already specified, this condition will be appended.]_ Specifies the "filter" in a metric absence or metric threshold condition. |
| `--duration` | DURATION |  | _[any conditions are already specified, this condition will be appended.]_ The duration (e.g. "60s", "2min", etc.) that the condition must hold in order to trigger as true. |
| `--if` | IF_VALUE |  | _[any conditions are already specified, this condition will be appended.]_ One of "absent", "< THRESHOLD", "> THRESHOLD" where "THRESHOLD" is an integer or float. |
| `--combiner` | one of: AND An incident is created only if all conditions are met simultaneously |  | _[in the --policy or --policy-from-file flags if specified.]_ The combiner for the Alert Policy. COMBINER must be one of: AND An incident is created only if all conditions are met simultaneously. This combiner is satisfied if all conditions are met, even if they are met on completely different resources. AND_WITH_MATCHING_RESOURCE Combine conditions using logical AND operator, but unlike the regular AND option, an incident is created only if all conditions are met simultaneously on at least one resource. COMBINE_UNSPECIFIED An unspecified combiner OR An incident is created if any of the listed conditions is met. |
| `--display-name` | DISPLAY_NAME |  | _[in the --policy or --policy-from-file flags if specified.]_ The display name for the Alert Policy. |
| `--enabled` |  |  | _[in the --policy or --policy-from-file flags if specified.]_ If the policy is enabled. Enabled by default, use --no-enabled to disable. |
| `--user-labels` | [KEY=VALUE,...] |  | _[in the --policy or --policy-from-file flags if specified.]_ List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. If the policy was given as a JSON/YAML object from a string or file, this flag will replace the labels value in the given policy. |
| `--policy` | POLICY |  | _[At most one of these can be specified:]_ The policy as a string. In either JSON or YAML format. |
| `--policy-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ The path to a JSON or YAML file containing the policy. Use a full or relative path to a local file containing the value of policy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/create)

---
### `gcloud monitoring policies delete`

Delete a Cloud Monitoring alerting policy

Delete a Monitoring alerting policy.

**Synopsis:**
```
gcloud monitoring policies delete POLICY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The alerting policy to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/delete)

---
### `gcloud monitoring policies describe`

Describe an alerting policy

Describe an alerting policy.

**Synopsis:**
```
gcloud monitoring policies describe POLICY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The alerting policy to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  POLICY
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/describe)

---
### `gcloud monitoring policies list`

List alerting policies

List alerting policies.

**Synopsis:**
```
gcloud monitoring policies list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To order your results first by the team key in user_labels and then the
policy's display name:

    $ gcloud monitoring policies list \
        --sort-by user_label.team,display_name

To order your results in reverse order, you can add either '~' or '-' in
front of the field name:

    $ gcloud monitoring policies list --sort-by "-display_name"

To return results with non-empty display names or descriptions:

    $ gcloud monitoring policies list \
        --filter "(NOT display_name.empty OR NOT description.empty)"

To return results whose descriptions contain the word 'cloud':

    $ gcloud monitoring policies list --filter "description:(cloud)"

Please find all supported fields at
https://cloud.google.com/monitoring/api/v3/sorting-and-filtering#alertpolicy.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/list)

---
### `gcloud monitoring policies migrate`

Migrate a Prometheus configuration file to Cloud Monitoring

Creates new alerting policies and/or notification channels based on
provided Prometheus files. The rules YAML file, which holds the alert
rules, must be specified as a file through the
--policies-from-prometheus-alert-rules-yaml flag.

**Synopsis:**
```
gcloud monitoring policies migrate
    [--channels-from-prometheus-alertmanager-yaml=PROMETHEUS_ALERT_MANAGER_FILE_PATH --policies-from-prometheus-alert-rules-yaml=[PROMETHEUS_ALERT_RULE_FILE_PATHS,
      ...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--channels-from-prometheus-alertmanager-yaml` | PROMETHEUS_ALERT_MANAGER_FILE_PATH |  | Prometheus alert manager YAML file to be converted to Cloud Monitoring notification channels. Specifying this flag with the --policies-from-prometheus-alert-rules-yaml flag puts the newly created notification channels into the translated Alert Policies' definition. Use a full or relative path to a local file containing the value of channels_from_prometheus_alertmanager_yaml. |
| `--policies-from-prometheus-alert-rules-yaml` | [PROMETHEUS_ALERT_RULE_FILE_PATHS,...] |  | One or more Prometheus alert rule YAML files (separated by commas if multiple) to be converted to Cloud Alerting Policies. Example: --policies-from-prometheus-alert-rules-yaml=rules_1.yaml,rules_2.yaml |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/migrate)

---
### `gcloud monitoring policies update`

Updates an alerting policy

Updates an alerting policy.

If --policy or --policy-from-file are specified:

  o If --fields is specified, the only the specified fields will be
    updated.
  o Else, the policy will be replaced with the provided policy. The
    policy can be modified further using the flags from the Policy Settings
    group below.

Otherwise, the policy will be updated with the values specified in the
flags from the Policy Settings group.

For information about the JSON/YAML format of an alerting policy:
https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.alertPolicies

**Synopsis:**
```
gcloud monitoring policies update ALERT_POLICY
    [--fields=[field,...] | --combiner=COMBINER --display-name=DISPLAY_NAME
      --[no-]enabled
      --add-notification-channels=[NOTIFICATION-CHANNELS,...]
      | --clear-notification-channels
      | --remove-notification-channels=[NOTIFICATION-CHANNELS,...]
      | --set-notification-channels=[NOTIFICATION-CHANNELS,...]
      --documentation-format=DOCUMENTATION_FORMAT
      --documentation=DOCUMENTATION
      | --documentation-from-file=PATH_TO_FILE
      --update-user-labels=[KEY=VALUE,...] --clear-user-labels
      | --remove-user-labels=[KEY,...]]
    [--policy=POLICY | --policy-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Alert Policy resource - Name of the Alert Policy to be updated. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument alert_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ALERT_POLICY
     ID of the Alert Policy or fully qualified identifier for the Alert
     Policy.

     To set the policy attribute:
     + provide the argument alert_policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fields` | one of: disabled, notificationChannels |  | _[At most one of these can be specified:]_ The list of fields to update. Must specify --policy or --policy-from-file if using this flag. field must be one of: disabled, notificationChannels. |
| `--policy` | POLICY |  | _[At most one of these can be specified:]_ The policy as a string. In either JSON or YAML format. |
| `--policy-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ The path to a JSON or YAML file containing the policy. Use a full or relative path to a local file containing the value of policy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/update)

---

## `gcloud monitoring policies conditions` — manage Cloud Monitoring alerting policy conditions
### `gcloud monitoring policies conditions create`

Create a condition in an alerting policy

Create a condition in an alerting policy.

**Synopsis:**
```
gcloud monitoring policies conditions create ALERT_POLICY
    [--aggregation=AGGREGATION
      --condition-display-name=CONDITION_DISPLAY_NAME
      --condition-filter=CONDITION_FILTER
      --duration=DURATION --if=IF_VALUE --trigger-count=TRIGGER_COUNT
      | --trigger-percent=TRIGGER_PERCENT]
    [--condition=CONDITION | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Alert Policy resource - Name of the Alert Policy to add a condition to.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument alert_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ALERT_POLICY
     ID of the Alert Policy or fully qualified identifier for the Alert
     Policy.

     To set the policy attribute:
     + provide the argument alert_policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aggregation` | AGGREGATION |  | _[any conditions are already specified, this condition will be appended.]_ Specifies an Aggregation message as a JSON/YAML value to be applied to the condition. For more information about the format: https://cloud.google.com/monitoring/api/ref_v3/rest/v3/projects.alertPolicies |
| `--condition-display-name` | CONDITION_DISPLAY_NAME |  | _[any conditions are already specified, this condition will be appended.]_ The display name for the condition. |
| `--condition-filter` | CONDITION_FILTER |  | _[any conditions are already specified, this condition will be appended.]_ Specifies the "filter" in a metric absence or metric threshold condition. |
| `--duration` | DURATION |  | _[any conditions are already specified, this condition will be appended.]_ The duration (e.g. "60s", "2min", etc.) that the condition must hold in order to trigger as true. |
| `--if` | IF_VALUE |  | _[any conditions are already specified, this condition will be appended.]_ One of "absent", "< THRESHOLD", "> THRESHOLD" where "THRESHOLD" is an integer or float. |
| `--condition` | CONDITION |  | _[At most one of these can be specified:]_ The condition as a string. In either JSON or YAML format. |
| `--condition-from-file` | PATH_TO_FILE |  | _[At most one of these can be specified:]_ The path to a JSON or YAML file containing the condition. Use a full or relative path to a local file containing the value of condition. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/conditions/create)

---
### `gcloud monitoring policies conditions delete`

Delete a condition in an alerting policy

Delete a condition in an alerting policy. If the specified condition does
not exist, this command will fail with an error. This will not delete the
policy if no conditions exist.

**Synopsis:**
```
gcloud monitoring policies conditions delete (CONDITION : --policy=POLICY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Condition resource - The name of the Condition to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument condition on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONDITION
     ID of the condition or fully qualified identifier for the condition.

     To set the condition attribute:
     + provide the argument condition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     Name of the alerting policy.

     To set the policy attribute:
     + provide the argument condition on the command line with a fully
       specified name;
     + provide the argument --policy on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/conditions/delete)

---
### `gcloud monitoring policies conditions describe`

Describe a condition in a Cloud Monitoring alerting policy

Describe a condition in a Cloud Monitoring alerting policy.

**Synopsis:**
```
gcloud monitoring policies conditions describe
    (CONDITION : --policy=POLICY) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Condition resource - The name of the Condition to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument condition on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONDITION
     ID of the condition or fully qualified identifier for the condition.

     To set the condition attribute:
     + provide the argument condition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     Name of the alerting policy.

     To set the policy attribute:
     + provide the argument condition on the command line with a fully
       specified name;
     + provide the argument --policy on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/conditions/describe)

---
### `gcloud monitoring policies conditions update`

Update a condition in an alerting policy

Update a condition in an alerting policy.

**Synopsis:**
```
gcloud monitoring policies conditions update (CONDITION : --policy=POLICY)
    [--display-name=DISPLAY_NAME] [--if=IF_VALUE]
    [--trigger-count=TRIGGER_COUNT | --trigger-percent=TRIGGER_PERCENT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Condition resource - The name of the Condition to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument condition on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONDITION
     ID of the condition or fully qualified identifier for the condition.

     To set the condition attribute:
     + provide the argument condition on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     Name of the alerting policy.

     To set the policy attribute:
     + provide the argument condition on the command line with a fully
       specified name;
     + provide the argument --policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The display name for the Condition. |
| `--if` | IF_VALUE |  | One of "absent", "< THRESHOLD", "> THRESHOLD" where "THRESHOLD" is an integer or float. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/monitoring/policies/conditions/update)

---