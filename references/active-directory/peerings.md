# gcloud active-directory peerings

managed Microsoft AD peerings

### `gcloud active-directory peerings create`

Create a Managed Microsoft Active Directory domain peering

Create a new Managed Microsoft AD domain peering with the given name using
Google Cloud's Managed Service for Microsoft Active Directory.

This command can fail for the following reasons:
  o A domain peering with the same name already exists.
  o The active account does not have permission to create AD domains
    peerings.
  o There is an overlap between the provided CIDR range and authorized
    network's CIDR.

**Synopsis:**
```
gcloud active-directory peerings create PEERING
    --authorized-network=AUTHORIZED_NETWORK --domain=DOMAIN [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Peering resource - Name of the managed Managed Microsoft AD domain peering
you want to create. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PEERING
     ID of the peering or fully qualified identifier for the peering.

     To set the peering attribute:
     + provide the argument peering on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--authorized-network` | AUTHORIZED_NETWORK |  | Name of the Network that is authorized to communicate with Managed Microsoft AD domain. This is usually the full path name of the network in the peer project. |
| `--domain` | DOMAIN |  | Name of the managed Managed Microsoft AD domain you want to peer to. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command creates an AD domain peering with the name
my-peering, network my-network and domain
projects/domain-project/locations/global/domains/domain.com

    $ gcloud active-directory peerings create my-peering \
        --domain=projects/domain-project/locations/global/domains/\
    domain.com \
        --authorized-network=projects/network-project/global/networks/\
    my-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/peerings/create)

---
### `gcloud active-directory peerings delete`

Delete a Managed Microsoft Active Directory domain peering

Delete a Managed Microsoft Active Directory (AD) domain peering.

This command can fail for the following reasons:
  o The active account does not have permission to access the given AD
    domain.
  o The domain peering is no longer existed.

**Synopsis:**
```
gcloud active-directory peerings delete PEERING [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Peering resource - Name of the managed Managed Microsoft AD domain peering
you want to delete. This represents a Cloud resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PEERING
     ID of the peering or fully qualified identifier for the peering.

     To set the peering attribute:
     + provide the argument peering on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command deletes an AD domain peering with the name
my-peering.

    $ gcloud active-directory peerings delete my-peering
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/peerings/delete)

---
### `gcloud active-directory peerings describe`

Describe a Managed Microsoft Active Directory domain peering

Show metadata for a Managed Microsoft AD domain peering.

Displays all metadata associated with a Active Directory domain peering
given a valid domain peering name.

This command can fail for the following reasons:
  o The specified domain peering does not exist.
  o The active account does not have permission to access the given
    domain.

**Synopsis:**
```
gcloud active-directory peerings describe PEERING [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Peering resource - Name of the Managed Microsoft AD domain peering you
want to describe. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PEERING
     ID of the peering or fully qualified identifier for the peering.

     To set the peering attribute:
     + provide the argument peering on the command line.
```

**Examples:**
```bash
The following command gets metadata for an AD domain peering with the name
my-peering.

    $ gcloud active-directory peerings describe my-peering
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/peerings/describe)

---
### `gcloud active-directory peerings list`

List all Managed Microsoft Active Directory domain peerings

List all Managed Microsoft AD domain peerings in the given project.

Displays associated Active Directory domain peerings.

This command can fail for the following reasons:
  o The active account does not have permission to access the given
    domain.

**Synopsis:**
```
gcloud active-directory peerings list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists five AD domain peerings in the project.

    $ gcloud active-directory peerings list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/peerings/list)

---
### `gcloud active-directory peerings update`

Update a Managed Microsoft Active Directory domain peering

Update a Managed Microsoft Active Directory (AD) domain peering.

This command can fail for the following reasons:
  o The active account does not have permission to access the given AD
    domain.

**Synopsis:**
```
gcloud active-directory peerings update PEERING [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Peering resource - Name of the managed Managed Microsoft AD domain you
want to delete. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument peering on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PEERING
     ID of the peering or fully qualified identifier for the peering.

     To set the peering attribute:
     + provide the argument peering on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
The following command updates an AD domain peering my-peering with the
label l1 and l2

    $ gcloud active-directory peerings update my-peering \
        --update-labels=l1=1,l2=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/active-directory/peerings/update)

---