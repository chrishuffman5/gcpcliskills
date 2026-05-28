# gcloud network-security authz-policies

manage Network Security AuthzPolicy resources

### `gcloud network-security authz-policies delete`

Delete an AuthzPolicy resource

Delete the specified AuthzPolicy resource.

**Synopsis:**
```
gcloud network-security authz-policies delete
    (AUTHZ_POLICY : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AuthzPolicy resource - The ID of the deleted AuthzPolicy resource. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authz_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHZ_POLICY
     ID of the AuthzPolicy or fully qualified identifier for the
     AuthzPolicy.

     To set the authz_policy attribute:
     + provide the argument authz_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument authz_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an AuthzPolicy resource named my-authz-policy in us-central1,
run:

    $ gcloud network-security authz-policies delete my-authz-policy \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authz-policies/delete)

---
### `gcloud network-security authz-policies describe`

Describe an AuthzPolicy resource

Show details about an AuthzPolicy resource.

**Synopsis:**
```
gcloud network-security authz-policies describe
    (AUTHZ_POLICY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AuthzPolicy resource - The ID of the AuthzPolicy resource. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument authz_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHZ_POLICY
     ID of the AuthzPolicy or fully qualified identifier for the
     AuthzPolicy.

     To set the authz_policy attribute:
     + provide the argument authz_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument authz_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To show details about the AuthzPolicy resource named my-authz-policy
located in us-central1.

    $ gcloud network-security authz-policies describe my-authz-policy \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authz-policies/describe)

---
### `gcloud network-security authz-policies import`

Import an AuthzPolicy resource

Import an AuthzPolicy resource defined in a YAML file.

**Synopsis:**
```
gcloud network-security authz-policies import
    (AUTHZ_POLICY : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AuthzPolicy resource - The ID of the new or updated AuthzPolicy resource.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument authz_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHZ_POLICY
     ID of the AuthzPolicy or fully qualified identifier for the
     AuthzPolicy.

     To set the authz_policy attribute:
     + provide the argument authz_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument authz_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import an AuthzPolicy resource named my-authz-poilcy from a YAML file in
us-central1, run:

    $ gcloud network-security authz-policies import my-authz-policy \
      --source=my-authz-policy.yaml --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authz-policies/import)

---
### `gcloud network-security authz-policies list`

List AuthzPolicy resources

List all AuthzPolicy resources in the specified location of the current
project.

**Synopsis:**
```
gcloud network-security authz-policies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all AuthzPolicy resources in the current project located in
us-central1 region run:

    $ gcloud network-security authz-policies list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authz-policies/list)

---