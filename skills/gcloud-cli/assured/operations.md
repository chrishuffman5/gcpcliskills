# gcloud assured operations

read and manipulate Assured Workloads operation resources

### `gcloud assured operations describe`

Describe Assured Workloads operations

Obtain details about a given Assured Workloads operation.

**Synopsis:**
```
gcloud assured operations describe
    (OPERATION : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The Assured Workloads operation resource to describe.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     The parent organization for the operation.

     To set the organization attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To describe an Assured Workloads operation in the us-central1 region,
belonging to an organization with ID 123, with workload ID 456, run:

    $ gcloud assured operations describe \
        organizations/123/locations/us-central1/operations/456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/operations/describe)

---
### `gcloud assured operations list`

List all Assured Workloads operations that belong to a given parent organization

List all Assured Workloads operations that belong to a given parent
organization.

**Synopsis:**
```
gcloud assured operations list --location=LOCATION
    --organization=ORGANIZATION [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location of the Assured Workloads operations. For a current list of supported LOCATION values, see Assured Workloads locations (https://cloud.google.com/assured-workloads/docs/locations). |
| `--organization` | ORGANIZATION |  | The parent organization of the Assured Workloads operations, provided as an organization ID. |


**Examples:**
```bash
The following example command lists all Assured Workloads operations with
these properties:

  o belonging to an organization with ID 123
  o located in the us-central1 region
  o return no more than 30 results
  o requesting 10 results at a time from the backend

    $ gcloud assured operations list \
        organizations/123/locations/us-central1 --limit=30 \
        --page-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/assured/operations/list)

---