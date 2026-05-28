# gcloud iam simulator

understand how an IAM policy change could impact access before deploying the change

### `gcloud iam simulator replay-recent-access`

Determine affected recent access attempts before IAM policy change deployment

Replay the most recent 1,000 access logs from the past 90 days using the
simulated policy. For each log entry, the replay determines if setting the
provided policy on the given resource would result in a change in the
access state, e.g. a previously granted access becoming denied. Any
differences found are returned.

**Synopsis:**
```
gcloud iam simulator replay-recent-access RESOURCE POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE
   Full resource name to simulate the IAM policy for.

   See:
   https://cloud.google.com/apis/design/resource_names#full_resource_name.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy. See the
   Policy reference
   (https://cloud.google.com/iam/reference/rest/v1/Policy) for details.
```

**Examples:**
```bash
To simulate a permission change of a member on a resource, run:

    $ gcloud iam simulator replay-recent-access projects/project-id \
        path/to/policy_file.json

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/simulator/replay-recent-access)

---