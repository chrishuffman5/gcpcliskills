# gcloud dataproc autoscaling-policies

create and manage Dataproc autoscaling policies

### `gcloud dataproc autoscaling-policies delete`

Delete an autoscaling policy

**Synopsis:**
```
gcloud dataproc autoscaling-policies delete
    (AUTOSCALING_POLICY : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Autoscaling policy resource - The autoscaling policy to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autoscaling_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOSCALING_POLICY
     ID of the autoscaling policy or fully qualified identifier for the
     autoscaling policy.

     To set the autoscaling_policy attribute:
     + provide the argument autoscaling_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the autoscaling policy. Each Dataproc region
     constitutes an independent resource namespace constrained to
     deploying instances into Compute Engine zones inside the region.
     Overrides the default dataproc/region property value for this command
     invocation.

     To set the region attribute:
     + provide the argument autoscaling_policy on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command deletes the autoscaling policy
example-autoscaling-policy:

    $ gcloud dataproc autoscaling-policies delete \
        example-autoscaling-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/delete)

---
### `gcloud dataproc autoscaling-policies describe`

Describe an autoscaling policy

**Synopsis:**
```
gcloud dataproc autoscaling-policies describe
    (AUTOSCALING_POLICY : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Autoscaling policy resource - The autoscaling policy to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autoscaling_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOSCALING_POLICY
     ID of the autoscaling policy or fully qualified identifier for the
     autoscaling policy.

     To set the autoscaling_policy attribute:
     + provide the argument autoscaling_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the autoscaling policy. Each Dataproc region
     constitutes an independent resource namespace constrained to
     deploying instances into Compute Engine zones inside the region.
     Overrides the default dataproc/region property value for this command
     invocation.

     To set the region attribute:
     + provide the argument autoscaling_policy on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command prints out the autoscaling policy
example-autoscaling-policy:

    $ gcloud dataproc autoscaling-policies describe \
        example-autoscaling-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/describe)

---
### `gcloud dataproc autoscaling-policies export`

Export an autoscaling policy

Exporting an autoscaling policy is similar to describing one, except that
export omits output only fields, such as the policy id and resource name.
This is to allow piping the output of export directly into import, which
requires that output only fields are omitted.

**Synopsis:**
```
gcloud dataproc autoscaling-policies export
    (AUTOSCALING_POLICY : --region=REGION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Autoscaling policy resource - The autoscaling policy to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autoscaling_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOSCALING_POLICY
     ID of the autoscaling policy or fully qualified identifier for the
     autoscaling policy.

     To set the autoscaling_policy attribute:
     + provide the argument autoscaling_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the autoscaling policy. Each Dataproc region
     constitutes an independent resource namespace constrained to
     deploying instances into Compute Engine zones inside the region.
     Overrides the default dataproc/region property value for this command
     invocation.

     To set the region attribute:
     + provide the argument autoscaling_policy on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. |


**Examples:**
```bash
The following command saves the contents of autoscaling policy
example-autoscaling-policy to a file so that it can be imported later:

    $ gcloud dataproc autoscaling-policies export \
        example-autoscaling-policy --destination=saved-policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/export)

---
### `gcloud dataproc autoscaling-policies get-iam-policy`

Get IAM policy for an autoscaling policy

Gets the IAM policy for an autoscaling policy, given an autoscaling policy
ID.

**Synopsis:**
```
gcloud dataproc autoscaling-policies get-iam-policy
    (AUTOSCALING_POLICY : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Autoscaling policy resource - The autoscaling policy to retrieve the IAM
policy for. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument autoscaling_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOSCALING_POLICY
     ID of the autoscaling policy or fully qualified identifier for the
     autoscaling policy.

     To set the autoscaling_policy attribute:
     + provide the argument autoscaling_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the autoscaling policy. Each Dataproc region
     constitutes an independent resource namespace constrained to
     deploying instances into Compute Engine zones inside the region.
     Overrides the default dataproc/region property value for this command
     invocation.

     To set the region attribute:
     + provide the argument autoscaling_policy on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command prints the IAM policy for an autoscaling policy with
the ID example-autoscaling-policy:

    $ gcloud dataproc autoscaling-policies get-iam-policy \
        example-autoscaling-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/get-iam-policy)

---
### `gcloud dataproc autoscaling-policies import`

Import an autoscaling policy

If the specified autoscaling policy already exists, it will be overwritten.
Otherwise, a new autoscaling policy will be created. To edit an existing
autoscaling policy, you can export the autoscaling policy to a file, edit
its configuration, and then import the new configuration.

This command does not allow output only fields, such as policy id and
resource name. It populates the id field based on the resource name
specified as the first command line argument.

**Synopsis:**
```
gcloud dataproc autoscaling-policies import
    (AUTOSCALING_POLICY : --region=REGION) [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Autoscaling policy resource - The autoscaling policy to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument autoscaling_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOSCALING_POLICY
     ID of the autoscaling policy or fully qualified identifier for the
     autoscaling policy.

     To set the autoscaling_policy attribute:
     + provide the argument autoscaling_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the autoscaling policy. Each Dataproc region
     constitutes an independent resource namespace constrained to
     deploying instances into Compute Engine zones inside the region.
     Overrides the default dataproc/region property value for this command
     invocation.

     To set the region attribute:
     + provide the argument autoscaling_policy on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. |


**Examples:**
```bash
The following command creates or updates the contents of autoscaling policy
example-autoscaling-policy based on a yaml file:

    $ gcloud dataproc autoscaling-policies import \
        example-autoscaling-policy --source=saved-policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/import)

---
### `gcloud dataproc autoscaling-policies list`

List autoscaling policies

**Synopsis:**
```
gcloud dataproc autoscaling-policies list [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |


**Examples:**
```bash
The following command lists all autoscaling policies in Dataproc's
'us-central1' region:

    $ gcloud dataproc autoscaling-policies list --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/list)

---
### `gcloud dataproc autoscaling-policies set-iam-policy`

Set IAM policy for an autoscaling policy

Sets the IAM policy for an autoscaling policy, given an autoscaling policy
ID and the IAM policy.

**Synopsis:**
```
gcloud dataproc autoscaling-policies set-iam-policy
    (AUTOSCALING_POLICY : --region=REGION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Autoscaling policy resource - The autoscaling policy to retrieve the IAM
policy for. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument autoscaling_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTOSCALING_POLICY
     ID of the autoscaling policy or fully qualified identifier for the
     autoscaling policy.

     To set the autoscaling_policy attribute:
     + provide the argument autoscaling_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the autoscaling policy. Each Dataproc region
     constitutes an independent resource namespace constrained to
     deploying instances into Compute Engine zones inside the region.
     Overrides the default dataproc/region property value for this command
     invocation.

     To set the region attribute:
     + provide the argument autoscaling_policy on the command line with
       a fully specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for an autoscaling-policy with identifier
'example-autoscaling-policy'

    $ gcloud dataproc autoscaling-policies set-iam-policy \
      autoscaling-policies set-iam-policy example-autoscaling-policy \
      policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/autoscaling-policies/set-iam-policy)

---