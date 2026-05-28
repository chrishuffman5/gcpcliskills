# gcloud access-context-manager perimeters

manage Access Context Manager service perimeters

### `gcloud access-context-manager perimeters create`

Create a new service perimeter

Create a new service perimeter in a given access policy.

**Synopsis:**
```
gcloud access-context-manager perimeters create
    (PERIMETER : --policy=POLICY) --title=TITLE
    [--access-levels=[LEVEL,...]] [--async] [--description=DESCRIPTION]
    [--egress-policies=YAML_FILE] [--ingress-policies=YAML_FILE]
    [--perimeter-type=PERIMETER_TYPE; default="regular"]
    [--resources=[RESOURCES,...]] [--restricted-services=[SERVICE,...]]
    [--enable-vpc-accessible-services
      --vpc-allowed-services=[VPC_SERVICE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to create. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--title` | TITLE |  | Short human-readable title for the service perimeter. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-levels` | [LEVEL,...] |  | Comma-separated list of IDs for access levels (in the same policy) that an intra-perimeter request must satisfy to be allowed. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Long-form description of service perimeter. |
| `--egress-policies` | YAML_FILE |  | Path to a file containing a list of Engress Policies. This file contains a list of YAML-compliant objects representing Engress Policies described in the API reference. For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For more information about non-alpha versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |
| `--ingress-policies` | YAML_FILE |  | Path to a file containing a list of Ingress Policies. This file contains a list of YAML-compliant objects representing Ingress Policies described in the API reference. For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For more information about non-alpha versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |
| `--perimeter-type` | one of: bridge Allows resources in different regular service perimeters to import and export data between each other | regular | Type of the perimeter. PERIMETER_TYPE must be one of: bridge Allows resources in different regular service perimeters to import and export data between each other. A project may belong to multiple bridge service perimeters (only if it also belongs to a regular service perimeter). Both restricted and unrestricted service lists, as well as access level lists, must be empty. regular Allows resources within this service perimeter to import and export data amongst themselves. A project may belong to at most one regular service perimeter. |
| `--resources` | [RESOURCES,...] |  | Comma-separated list of resources (currently only projects, in the form projects/<projectnumber>) in this perimeter. |
| `--restricted-services` | [SERVICE,...] |  | Comma-separated list of services to which the perimeter boundary does apply (for example, storage.googleapis.com). |
| `--enable-vpc-accessible-services` |  |  | Whether to restrict API calls within the perimeter to those in the vpc-allowed-services list. |
| `--vpc-allowed-services` | [VPC_SERVICE,...] |  | Comma-separated list of APIs accessible from within the Service Perimeter. In order to include all restricted services, use reference "RESTRICTED-SERVICES". Requires vpc-accessible-services be enabled. |


**Examples:**
```bash
To create a new basic Service Perimeter:

    $ gcloud access-context-manager perimeters create \
        --title=my_perimeter_title --resources=projects/12345 \
        --restricted-services="storage.googleapis.com" --policy=9876543
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/create)

---
### `gcloud access-context-manager perimeters delete`

Delete a service perimeter

Delete a service perimeter in a given access policy.

**Synopsis:**
```
gcloud access-context-manager perimeters delete
    (PERIMETER : --policy=POLICY) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter you want to delete. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/delete)

---
### `gcloud access-context-manager perimeters describe`

Show details about a service perimeter

Show details about an service perimeter in a given access policy.

**Synopsis:**
```
gcloud access-context-manager perimeters describe
    (PERIMETER : --policy=POLICY) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter you want to show details about.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/describe)

---
### `gcloud access-context-manager perimeters list`

List service perimeters

List all service access zones in an access policy object.

**Synopsis:**
```
gcloud access-context-manager perimeters list [--policy=POLICY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy` | POLICY |  | _[perimeters for. This represents a Cloud resource.]_ ID of the policy or fully qualified identifier for the policy. To set the policy attribute: + provide the argument --policy on the command line; + set the property access_context_manager/policy; + automatically, if the current account belongs to an organization with exactly one access policy.. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/list)

---
### `gcloud access-context-manager perimeters replace-all`

Replace all existing service perimeters

Replace all existing service perimeter in specified access policy with
service perimeters specified in a file.

**Synopsis:**
```
gcloud access-context-manager perimeters replace-all [POLICY]
    --source-file=SOURCE_FILE [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy that contains the perimeters you want
to replace. This represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-file` | SOURCE_FILE |  | Path to a file containing a list of service perimeters. An service perimeter file is a YAML-formatted list of service perimeters, which are YAML objects representing a Condition as described in the API reference. For example: - name: my_perimeter title: My Perimeter description: Perimeter for foo. perimeterType: PERIMETER_TYPE_REGULAR status: resources: - projects/0123456789 accessLevels: - accessPolicies/my_policy/accessLevels/my_level restrictedServices: - storage.googleapis.com For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For other versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | An etag which specifies the version of the Access Policy. Only etags that represent the latest version of the Access Policy will be accepted. |


**Examples:**
```bash
To replace all perimeters within a policy, using etag:

    $ gcloud access-context-manager perimeters replace-all \
        my-policy-number \
        --source-file=path-to-file-containing-all-replacement-service-pe\
    rimeters.yaml --etag=optional-latest-etag-of-policy

To replace all perimeters within a policy, without using etag:

    $ gcloud access-context-manager perimeters replace-all \
        my-policy-number \
        --source-file=path-to-file-containing-all-replacement-service-pe\
    rimeters.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/replace-all)

---
### `gcloud access-context-manager perimeters update`

Update the enforced configuration for an existing Service Perimeter

This command updates the enforced configuration (status) of a Service
Perimeter.

**Synopsis:**
```
gcloud access-context-manager perimeters update
    (PERIMETER : --policy=POLICY) [--description=DESCRIPTION] [--etag=etag]
    [--title=TITLE] [--type=TYPE]
    [--add-access-levels=[LEVEL,...] | --clear-access-levels
      | --remove-access-levels=[LEVEL,...]
      | --set-access-levels=[LEVEL,...]]
    [--add-resources=[RESOURCES,...] | --clear-resources
      | --remove-resources=[RESOURCES,...]
      | --set-resources=[RESOURCES,...]]
    [--add-restricted-services=[SERVICE,...] | --clear-restricted-services
      | --remove-restricted-services=[SERVICE,...]
      | --set-restricted-services=[SERVICE,...]]
    [--clear-egress-policies | --set-egress-policies=YAML_FILE]
    [--clear-ingress-policies | --set-ingress-policies=YAML_FILE]
    [--enable-vpc-accessible-services
      --add-vpc-allowed-services=[VPC_SERVICE,...]
      | --clear-vpc-allowed-services
      | --remove-vpc-allowed-services=[VPC_SERVICE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to update. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Long-form description of service perimeter. |
| `--etag` | etag |  | The etag for the version of the Access Policy that this operation is to be performed on. If, at the time of the operation, the etag for the Access Policy stored in Access Context Manager is different from the specified etag, then the commit operation will not be performed and the call will fail. If etag is not provided, the operation will be performed as if a valid etag is provided. |
| `--title` | TITLE |  | Short human-readable title of the service perimeter. |
| `--type` | one of: bridge, regular |  | Type of the perimeter. A regular perimeter allows resources within this service perimeter to import and export data amongst themselves. A project may belong to at most one regular service perimeter. A bridge perimeter allows resources in different regular service perimeters to import and export data between each other. A project may belong to multiple bridge service perimeters (only if it also belongs to a regular service perimeter). Both restricted and unrestricted service lists, as well as access level lists, must be empty. TYPE must be one of: bridge, regular. |
| `--enable-vpc-accessible-services` |  |  | _[https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters]_ When specified restrict API calls within the Service Perimeter to the set of vpc allowed services. To disable use '--no-enable-vpc-accessible-services'. |


**Examples:**
```bash
To update the enforced configuration for a Service Perimeter:

    $ gcloud access-context-manager perimeters update my-perimeter \
        --add-resources="projects/123,projects/456" \
        --remove-restricted-services="storage.googleapis.com" \
        --add-access-levels="accessPolicies/123/accessLevels/a_level" \
        --enable-vpc-accessible-services --clear-vpc-allowed-services
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/update)

---

## `gcloud access-context-manager perimeters dry-run` — enable management of dry-run mode configuration for Service Perimeters
### `gcloud access-context-manager perimeters dry-run create`

Create a dry-run mode configuration for a new or existing Service Perimeter

When a Service Perimeter with the specified name does not exist, a new
Service Perimeter will be created. In this case, the newly created Service
Perimeter will not have any enforcement mode configuration, and, therefore,
all policy violations will be logged.

When a perimeter with the specified name does exist, a dry-run mode
configuration will be created for it. The behavior of the enforcement mode
configuration, if present, will not be impacted in this case. Requests that
violate the existing enforcement mode configuration of the Service
Perimeter will continue being denied. Requests that only violate the policy
in the dry-run mode configuration will be logged but will not be denied.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run create
    (PERIMETER : --policy=POLICY)
    (--access-levels=[access_levels,...] --egress-policies=YAML_FILE
      --ingress-policies=YAML_FILE --resources=[resources,...]
      --restricted-services=[restricted_services,...]
      --enable-vpc-accessible-services
      --vpc-allowed-services=[vpc_allowed_services,...]
      | [--perimeter-title=PERIMETER_TITLE --perimeter-type=PERIMETER_TYPE
      : --perimeter-access-levels=[access_levels,...]
      --perimeter-description=PERIMETER_DESCRIPTION
      --perimeter-egress-policies=YAML_FILE
      --perimeter-ingress-policies=YAML_FILE
      --perimeter-resources=[resources,...]
      --perimeter-restricted-services=[restricted_services,...]
      --perimeter-enable-vpc-accessible-services
      --perimeter-vpc-allowed-services=[vpc_allowed_services,...]])
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to update. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--access-levels` | [access_levels,...] |  | _[Perimeter.]_ Comma-separated list of IDs for access levels (in the same policy) that an intra-perimeter request must satisfy to be allowed. |
| `--egress-policies` | YAML_FILE |  | _[Perimeter.]_ Path to a file containing a list of Egress Policies. This file contains a list of YAML-compliant objects representing Egress Policies described in the API reference. For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For more information about non-alpha versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |
| `--ingress-policies` | YAML_FILE |  | _[Perimeter.]_ Path to a file containing a list of Ingress Policies. This file contains a list of YAML-compliant objects representing Ingress Policies described in the API reference. For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For more information about non-alpha versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |
| `--resources` | [resources,...] |  | _[Perimeter.]_ Comma-separated list of resources (currently only projects, in the form projects/<projectnumber>) in this perimeter. |
| `--restricted-services` | [restricted_services,...] |  | _[Perimeter.]_ Comma-separated list of services to which the perimeter boundary does apply (for example, storage.googleapis.com). |
| `--enable-vpc-accessible-services` |  |  | _[Perimeter.]_ Whether to restrict API calls within the perimeter to those in the vpc-allowed-services list. |
| `--vpc-allowed-services` | [vpc_allowed_services,...] |  | _[Perimeter.]_ Comma-separated list of APIs accessible from within the Service Perimeter. In order to include all restricted services, use reference "RESTRICTED-SERVICES". Requires vpc-accessible-services be enabled. |
| `--perimeter-title` | PERIMETER_TITLE |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Short human-readable title for the Service Perimeter. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--perimeter-type` | PERIMETER_TYPE |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Type of the perimeter. A *regular* perimeter allows resources within this service perimeter to import and export data amongst themselves. A project may belong to at most one regular service perimeter. A *bridge* perimeter allows resources in different regular service perimeters to import and export data between each other. A project may belong to multiple bridge service perimeters (only if it also belongs to a regular service perimeter). Both restricted and unrestricted service lists, as well as access level lists, must be empty. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--perimeter-access-levels` | [access_levels,...] |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Comma-separated list of IDs for access levels (in the same policy) that an intra-perimeter request must satisfy to be allowed. |
| `--perimeter-description` | PERIMETER_DESCRIPTION |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Long-form description of Service Perimeter. |
| `--perimeter-egress-policies` | YAML_FILE |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Path to a file containing a list of Egress Policies. This file contains a list of YAML-compliant objects representing Egress Policies described in the API reference. For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For more information about non-alpha versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |
| `--perimeter-ingress-policies` | YAML_FILE |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Path to a file containing a list of Ingress Policies. This file contains a list of YAML-compliant objects representing Ingress Policies described in the API reference. For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.servicePerimeters For more information about non-alpha versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.servicePerimeters |
| `--perimeter-resources` | [resources,...] |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Comma-separated list of resources (currently only projects, in the form projects/<projectnumber>) in this perimeter. |
| `--perimeter-restricted-services` | [restricted_services,...] |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Comma-separated list of services to which the perimeter boundary does apply (for example, storage.googleapis.com). |
| `--perimeter-enable-vpc-accessible-services` |  |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Whether to restrict API calls within the perimeter to those in the vpc-allowed-services list. |
| `--perimeter-vpc-allowed-services` | [vpc_allowed_services,...] |  | _[Arguments for creating a dry-run spec for a new Service Perimeter.]_ Comma-separated list of APIs accessible from within the Service Perimeter. In order to include all restricted services, use reference "RESTRICTED-SERVICES". Requires vpc-accessible-services be enabled. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To create a dry-run configuration for an existing Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run create \
        my-perimeter --resources="projects/0123456789" \
        --access-levels="accessPolicies/a_policy/accessLevels/a_level" \
        --restricted-services="storage.googleapis.com"

To create a dry-run configuration for a new Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run create \
        my-perimeter --perimeter-title="My New Perimeter" \
        --perimeter-description="Perimeter description" \
        --perimeter-type="regular" \
        --perimeter-resources="projects/0123456789" \
        --perimeter-access-levels="accessPolicies/a_policy/accessLevels/\
    a_level" --perimeter-restricted-services="storage.googleapis.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/create)

---
### `gcloud access-context-manager perimeters dry-run delete`

Mark the Service Perimeter as deleted in the dry-run mode

When this command completed successfully, the affected Service Perimeter
will be considered to have been deleted in the dry-run mode, but the
enforcement mode configuration will be left untouched.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run delete
    (PERIMETER : --policy=POLICY) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to delete. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To mark the Service Perimeter as deleted in the dry-run mode:

    $ gcloud access-context-manager perimeters dry-run delete \
        my-perimeter
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/delete)

---
### `gcloud access-context-manager perimeters dry-run describe`

Display the dry-run mode configuration for a Service Perimeter

The dry-run mode configuration is presented as a diff against the
enforcement mode configuration. '+' indicates additions in spec,'-'
indicates removals from status and entries without either of those indicate
that they are the same across the dry-run and the enforcement mode
configurations. When a particular field is completely empty, it will not be
displayed.

Note: When this command is executed on a Service Perimeter with no explicit
dry-run mode configuration, the effective dry-run mode configuration is
inherited from the enforcement mode configuration, and thus, the
enforcement mode configuration is displayed in such cases.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run describe
    (PERIMETER : --policy=POLICY) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to describe. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Examples:**
```bash
To display the dry-run mode configuration for a Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run describe \
        my-perimeter

Sample output:

    ===
      name: my_perimeter
      title: My Perimeter
      type: PERIMETER_TYPE_REGULAR
      resources:
    +   projects/123
    -   projects/456
        projects/789
      restrictedServices:
    +   bigquery.googleapis.com
    -   storage.googleapis.com
        bigtable.googleapis.com
      vpcAccessibleServices:
    +   allowedServices:
    +     bigquery.googleapis.com
    -     storage.googleapis.com
    +   enableRestriction: true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/describe)

---
### `gcloud access-context-manager perimeters dry-run drop`

Reset the dry-run mode configuration of a Service Perimeter

Removes the explicit dry-run mode configuration for a Service Perimeter.
After this operation, the effective dry-run mode configuration is
implicitly inherited from the enforcement mode configuration. No audit logs
will be generated in this state.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run drop
    (PERIMETER : --policy=POLICY) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to reset. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To reset the dry-run mode configuration for a Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run drop my-perimeter
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/drop)

---
### `gcloud access-context-manager perimeters dry-run enforce`

Enforces a Service Perimeter's dry-run configuration

Copies a Service Perimeter's dry-run mode configuration to its enforcement
mode configuration and unsets the explicit dry-run spec. After this
operation succeeds, the Service Perimeter will not have an explicit dry-run
mode configuration, and, instead, the previous dry-run mode configuration
will become the enforcement mode configuration. The operation will not be
performed if there is no explicit dry-run mode configuration or if the
dry-run mode configuration is incompatible with the overall enforcement
mode VPC Service Controls policy.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run enforce
    (PERIMETER : --policy=POLICY) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to reset. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To enforce the dry-run mode configuration for a Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run enforce \
        my-perimeter
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/enforce)

---
### `gcloud access-context-manager perimeters dry-run enforce-all`

Enforces the dry-run mode configuration for all Service Perimeters

An enforce operation on a Service Perimeter involves copying its dry-run
mode configuration (spec) to that Service Perimeter's enforcement mode
configration (status). This command performs this operation for all Service
Perimeters in the user's Access Policy.

Note: Only Service Perimeters with an explicit dry-run mode configuration
are affected by this operation. The overall operation succeeds once the
dry-run configurations of all such Service Perimeters have been enforced.
If the operation fails for any given Service Perimeter, it will cause the
entire operation to be aborted.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run enforce-all [--etag=etag]
    [--policy=policy] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | etag |  | The etag for the version of the Access Policy that this operation is to be performed on. If, at the time of the operation, the etag for the Access Policy stored in Access Context Manager is different from the specified etag, then the commit operation will not be performed and the call will fail. If etag is not provided, the operation will be performed as if a valid etag is provided. |
| `--policy` | policy |  | The parent Access Policy which owns all Service Perimeters in scope for the commit operation. |


**Examples:**
```bash
To enforce the dry-run mode configurations for all Service Perimeter in an
Access Policy, run the following command:

    $ gcloud access-context-manager perimeters dry-run enforce-all
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/enforce-all)

---
### `gcloud access-context-manager perimeters dry-run list`

List the effective dry-run configuration across all Service Perimeters

By default, only the Service Perimeter name, title, type and the dry-run
mode configuration (as spec) is displayed.

Note: For Service Perimeters without an explicit dry-run mode
configuration, the enforcement mode configuration is used as the dry-run
mode configuration, resulting in no audit logs being generated.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run list [--policy=policy]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy` | policy |  | Policy resource - The access policy you want to list the effective dry-run configuration for. This represents a Cloud resource. |


**Examples:**
```bash
To list the dry-run mode configuration across all Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run list

Output:

    name: perimeter_1*
    spec:
      resources:
      - projects/123
      - projects/456
      restrictedServices:
      - storage.googleapis.com
    title: Perimeter 1
    ---
    name: perimeter_2
    spec:
      resources:
      - projects/789
      restrictedServices:
      - bigquery.googleapis.com
      vpcAccessibleServices:
        allowedServices:
        - bigquery.googleapis.com
        enableRestriction: true
    title: Perimeter 2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/list)

---
### `gcloud access-context-manager perimeters dry-run update`

Update the dry-run mode configuration for a Service Perimeter

This command updates the dry-run mode configuration (spec) for a Service
Perimeter.

For Service Perimeters with an explicitly defined dry-run mode
configuration (i.e. an explicit spec), this operation updates that
configuration directly, ignoring enforcement mode configuration.

Service Perimeters that do not have explict dry-run mode configuration will
inherit the enforcement mode configuration in the dry-run mode. Therefore,
this command effectively clones the enforcement mode configuration, then
applies the update on that configuration, and uses that as the explicit
dry-run mode configuration.

**Synopsis:**
```
gcloud access-context-manager perimeters dry-run update
    (PERIMETER : --policy=POLICY) [--async] [--etag=etag]
    [--add-access-levels=[ACCESS-LEVELS,...] | --clear-access-levels
      | --remove-access-levels=[ACCESS-LEVELS,...]]
    [--add-resources=[RESOURCES,...] | --clear-resources
      | --remove-resources=[RESOURCES,...]]
    [--add-restricted-services=[RESTRICTED-SERVICES,...]
      | --clear-restricted-services
      | --remove-restricted-services=[RESTRICTED-SERVICES,...]]
    [--clear-egress-policies | --set-egress-policies=YAML_FILE]
    [--clear-ingress-policies | --set-ingress-policies=YAML_FILE]
    [--enable-vpc-accessible-services
      --add-vpc-allowed-services=[VPC-ALLOWED-SERVICES,...]
      | --clear-vpc-allowed-services
      | --remove-vpc-allowed-services=[VPC-ALLOWED-SERVICES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Perimeter resource - The service perimeter to update. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  PERIMETER
     ID of the perimeter or fully qualified identifier for the perimeter.

     To set the perimeter attribute:
     + provide the argument perimeter on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument perimeter on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | etag |  | The etag for the version of the Access Policy that this operation is to be performed on. If, at the time of the operation, the etag for the Access Policy stored in Access Context Manager is different from the specified etag, then the commit operation will not be performed and the call will fail. If etag is not provided, the operation will be performed as if a valid etag is provided. |


**Examples:**
```bash
To update the dry-run mode configuration for a Service Perimeter:

    $ gcloud access-context-manager perimeters dry-run update \
        my-perimeter --add-resources="projects/123,projects/456" \
        --remove-restricted-services="storage.googleapis.com" \
        --add-access-levels="accessPolicies/123/accessLevels/a_level" \
        --enable-vpc-accessible-services --clear-vpc-allowed-services
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/perimeters/dry-run/update)

---