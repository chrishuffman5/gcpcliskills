# gcloud network-security authorization-policies

manage Network Security AuthorizationPolicies

### `gcloud network-security authorization-policies delete`

Delete authorization policy

Delete the specified authorization policy.

**Synopsis:**
```
gcloud network-security authorization-policies delete
    (AUTHORIZATION_POLICY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorization policy resource - Name of the authorization policy you want
to delete. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument authorization_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZATION_POLICY
     ID of the authorization policy or fully qualified identifier for the
     authorization policy.

     To set the authorization_policy attribute:
     + provide the argument authorization_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument authorization_policy on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an authorization policy called 'my-authz-policy', run:

    $ gcloud network-security authorization-policies delete \
        my-authz-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authorization-policies/delete)

---
### `gcloud network-security authorization-policies export`

Export authorization policy

Export an authorization policy.

**Synopsis:**
```
gcloud network-security authorization-policies export
    (AUTHORIZATION_POLICY : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorization policy resource - Name of the authorization policy to
export. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument authorization_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZATION_POLICY
     ID of the authorization policy or fully qualified identifier for the
     authorization policy.

     To set the authorization_policy attribute:
     + provide the argument authorization_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument authorization_policy on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export an authorization policy, run:

    $ gcloud network-security authorization-policies export \
        my-authz-policy --destination=my-authz-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authorization-policies/export)

---
### `gcloud network-security authorization-policies import`

Import authorization policy

Import an authorization policy.

**Synopsis:**
```
gcloud network-security authorization-policies import
    (AUTHORIZATION_POLICY : --location=LOCATION) [--async]
    [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorization policy resource - Name of the authorization policy to
import. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument authorization_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  AUTHORIZATION_POLICY
     ID of the authorization policy or fully qualified identifier for the
     authorization policy.

     To set the authorization_policy attribute:
     + provide the argument authorization_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument authorization_policy on the command line
       with a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import an authorization policy from a YAML file, run:

    $ gcloud network-security authorization-policies import \
        my-authz-policy --source=my-authz-policy.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authorization-policies/import)

---
### `gcloud network-security authorization-policies list`

List authorization policies

List all authorization policies in the specified location of the current
project.

**Synopsis:**
```
gcloud network-security authorization-policies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list authorization policies in the current project, run:

    $ gcloud network-security authorization-policies list \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/authorization-policies/list)

---