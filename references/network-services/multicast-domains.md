# gcloud network-services multicast-domains

manage Network Services MulticastDomains

### `gcloud network-services multicast-domains create`

Create a multicast domain

Create a multicast domain in the specified location of the current project.

**Synopsis:**
```
gcloud network-services multicast-domains create
    (MULTICAST_DOMAIN : --location=LOCATION) --admin-network=ADMIN_NETWORK
    (--connection-type=CONNECTION_TYPE;
      default="CONNECTION_TYPE_UNSPECIFIED" --ncc-hub=NCC_HUB) [--async]
    [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [--multicast-domain-group=MULTICAST_DOMAIN_GROUP]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain resource - Name of the multicast domain to be created.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN
     ID of the multicast domain or fully qualified identifier for the
     multicast domain.

     To set the multicast_domain attribute:
     + provide the argument multicast_domain on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--admin-network` | ADMIN_NETWORK |  | The URI of the admin network to be used. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast domain. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--multicast-domain-group` | MULTICAST_DOMAIN_GROUP |  | The URI of the multicast domain group to be used. |


**Examples:**
```bash
Create a multicast domain with the name 'my-multicast-domain',
admin-network 'path_to_admin_network', connection-type 'SAME_VPC', and
location 'global'.

    $ gcloud network-services multicast-domains create \
        my-multicast-domain --admin-network=path_to_admin_network \
        --connection-type=SAME_VPC --location=global

Create a multicast domain with the name 'my-multicast-domain',
admin-network 'path_to_admin_network', connection-type 'NCC', ncc-hub
'path_to_ncc_hub', and location 'global'.

    $ gcloud network-services multicast-domains create \
        my-multicast-domain --admin-network=path_to_admin_network \
        --connection-type=NCC --ncc-hub=path_to_ncc_hub \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domains/create)

---
### `gcloud network-services multicast-domains delete`

Delete a multicast domain

Delete a multicast domain in the specified location of the current project.

**Synopsis:**
```
gcloud network-services multicast-domains delete
    (MULTICAST_DOMAIN : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain resource - The multicast domain to delete. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument multicast_domain on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN
     ID of the multicast domain or fully qualified identifier for the
     multicast domain.

     To set the multicast_domain attribute:
     + provide the argument multicast_domain on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a multicast domain in the current project, run:

    $ gcloud network-services multicast-domains delete \
        my-multicast-domain --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domains/delete)

---
### `gcloud network-services multicast-domains describe`

Describe a multicast domain

Show details of a multicast domain in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-domains describe
    (MULTICAST_DOMAIN : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain resource - The multicast domain to display. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument multicast_domain on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN
     ID of the multicast domain or fully qualified identifier for the
     multicast domain.

     To set the multicast_domain attribute:
     + provide the argument multicast_domain on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe details of a multicast domain in the current project, run:

    $ gcloud network-services multicast-domains describe \
        my-multicast-domain --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domains/describe)

---
### `gcloud network-services multicast-domains list`

List multicast domains

List all multicast domains in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services multicast-domains list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list multicast domains in the current project, run:

    $ gcloud network-services multicast-domains list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domains/list)

---
### `gcloud network-services multicast-domains update`

Update a multicast domain

Update a multicast domain in the specified location of the current project.

**Synopsis:**
```
gcloud network-services multicast-domains update
    (MULTICAST_DOMAIN : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Multicast domain resource - Name of the multicast domain to be updated.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument multicast_domain on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MULTICAST_DOMAIN
     ID of the multicast domain or fully qualified identifier for the
     multicast domain.

     To set the multicast_domain attribute:
     + provide the argument multicast_domain on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument multicast_domain on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | The description for the multicast domain. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update a multicast domain with the name my-multicast-domain and location
zone.

    $ gcloud network-services multicast-domains update \
        my-multicast-domain --description="new description" \
        --location=zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/multicast-domains/update)

---