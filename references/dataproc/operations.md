# gcloud dataproc operations

view and manage Dataproc operations

### `gcloud dataproc operations cancel`

Cancel an active operation

Cancel an active operation.

**Synopsis:**
```
gcloud dataproc operations cancel (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to cancel. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the operation. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To cancel an operation, run:

    $ gcloud dataproc operations cancel operation_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/operations/cancel)

---
### `gcloud dataproc operations delete`

Delete the record of an inactive operation

Delete the record of an inactive operation.

**Synopsis:**
```
gcloud dataproc operations delete (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the operation. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To delete the record of an operation, run:

    $ gcloud dataproc operations delete operation_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/operations/delete)

---
### `gcloud dataproc operations describe`

View the details of an operation

View the details of an operation.

**Synopsis:**
```
gcloud dataproc operations describe (OPERATION : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the operation. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
To view the details of an operation, run:

    $ gcloud dataproc operations describe operation_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/operations/describe)

---
### `gcloud dataproc operations get-iam-policy`

Get IAM policy for an operation

Gets the IAM policy for an operation, given an operation ID.

**Synopsis:**
```
gcloud dataproc operations get-iam-policy (OPERATION : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to retrieve the policy for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the operation. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property dataproc/region.
```

**Examples:**
```bash
The following command prints the IAM policy for an operation with the ID
example-operation:

    $ gcloud dataproc operations get-iam-policy example-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/operations/get-iam-policy)

---
### `gcloud dataproc operations list`

View the list of all operations

View a list of operations in a project. An optional filter can be used to
constrain the operations returned. Filters are case-sensitive and have the
following syntax:

    field = value [AND [field = value]] ...

where field is either of status.state or labels.[KEY], where [KEY] is a
label key. value can be * to match all values. status.state is one of:
PENDING, ACTIVE, DONE. Only the logical AND operator is supported;
space-separated items are treated as having an implicit AND operator.

**Synopsis:**
```
gcloud dataproc operations list [--cluster=CLUSTER] [--region=REGION]
    [--state-filter=STATE_FILTER] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE; default=100] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cluster` | CLUSTER |  | Restrict to the operations of this Dataproc cluster. This flag is ignored when --filter is specified. The equivalent term in a --filter expression is: clusterName = myclustername |
| `--region` | REGION |  | Dataproc region to use. Each Dataproc region constitutes an independent resource namespace constrained to deploying instances into Compute Engine zones inside the region. Overrides the default dataproc/region property value for this command invocation. |
| `--state-filter` | one of: active, inactive |  | Filter by cluster state. This flag is ignored when --filter is specified. The equivalent term in a --filter expression is: status.state = ACTIVE. STATE_FILTER must be one of: active, inactive. |


**Examples:**
```bash
To see the list of all operations in Dataproc's 'us-central1' region, run:

    $ gcloud dataproc operations list --region='us-central1'

To see the list of all create cluster operations in Dataproc's 'global'
region, run:

    $ gcloud dataproc operations list --region='global' \
        --filter='operationType = CREATE'

To see the list of all active operations in a cluster named 'mycluster'
located in Dataproc's 'global' region, run:

    $ gcloud dataproc operations list --region='global' \
        --filter='status.state = RUNNING AND
      clusterName = mycluster'

To see a list of all pending operations with the label env=staging on
cluster mycluster located in Dataproc's 'us-central1' region, run:

    $ gcloud dataproc operations list --region='us-central1' \
        --filter='status.state = PENDING
      AND labels.env = staging AND clusterName = mycluster'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/operations/list)

---
### `gcloud dataproc operations set-iam-policy`

Set IAM policy for an operation

Sets the IAM policy for an operation, given an operation ID and the policy.

**Synopsis:**
```
gcloud dataproc operations set-iam-policy (OPERATION : --region=REGION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to set the policy on. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Dataproc region for the operation. Each Dataproc region constitutes
     an independent resource namespace constrained to deploying instances
     into Compute Engine zones inside the region. Overrides the default
     dataproc/region property value for this command invocation.

     To set the region attribute:
     + provide the argument operation on the command line with a fully
       specified name;
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
The following command will read an IAM policy from 'policy.json' and set it
for an operation with 'example-operation' as the identifier:

    $ gcloud dataproc operations set-iam-policy example-operation \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dataproc/operations/set-iam-policy)

---