# gcloud certificate-manager maps

manage Certificate Manager certificate maps

### `gcloud certificate-manager maps create`

Create a certificate map

This command creates a certificate map.

**Synopsis:**
```
gcloud certificate-manager maps create (MAP : --location=LOCATION)
    [--description=DESCRIPTION] [--async] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map resource - The certificate map to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument map on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MAP
     ID of the certificate map or fully qualified identifier for the
     certificate map.

     To set the map attribute:
     + provide the argument map on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map.

     To set the location attribute:
     + provide the argument map on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To create a certificate map with name simple-map, run:

    $ gcloud certificate-manager maps create simple-map
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/create)

---
### `gcloud certificate-manager maps delete`

Delete a certificate map

Delete a certificate map resource.

**Synopsis:**
```
gcloud certificate-manager maps delete (MAP : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map resource - The certificate map to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument map on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MAP
     ID of the certificate map or fully qualified identifier for the
     certificate map.

     To set the map attribute:
     + provide the argument map on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map.

     To set the location attribute:
     + provide the argument map on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the certificate map with name simple-map, run:

    $ gcloud certificate-manager maps delete simple-map
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/delete)

---
### `gcloud certificate-manager maps describe`

Describe an existing certificate map

This command fetches and prints information about an existing certificate
map.

**Synopsis:**
```
gcloud certificate-manager maps describe (MAP : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map resource - The certificate map to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument map on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MAP
     ID of the certificate map or fully qualified identifier for the
     certificate map.

     To set the map attribute:
     + provide the argument map on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map.

     To set the location attribute:
     + provide the argument map on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To describe a certificate map with name simple-map, run:

    $ gcloud certificate-manager maps describe simple-map
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/describe)

---
### `gcloud certificate-manager maps list`

List certificate maps

List Certificate Manager maps in the project.

**Synopsis:**
```
gcloud certificate-manager maps list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + default value of location is [global]. |


**Examples:**
```bash
To list all certificate maps in the project, run:

    $ gcloud certificate-manager maps list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/list)

---
### `gcloud certificate-manager maps update`

Update a certificate map

This command updates existing certificate map.

**Synopsis:**
```
gcloud certificate-manager maps update (MAP : --location=LOCATION)
    [--description=DESCRIPTION] [--async] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map resource - The certificate map to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument map on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MAP
     ID of the certificate map or fully qualified identifier for the
     certificate map.

     To set the map attribute:
     + provide the argument map on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map.

     To set the location attribute:
     + provide the argument map on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].
```

**Examples:**
```bash
To update a certificate map with name simple-map, run:

    $ gcloud certificate-manager maps update simple-map \
        --description="desc" --update-labels="key=value"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/update)

---

## `gcloud certificate-manager maps entries` — manage Certificate Manager certificate map entries
### `gcloud certificate-manager maps entries create`

Create a certificate map entry

This command creates a certificate map entry.

**Synopsis:**
```
gcloud certificate-manager maps entries create
    (ENTRY : --location=LOCATION --map=MAP)
    (--hostname=HOSTNAME | --set-primary) [--description=DESCRIPTION]
    [--async] [--certificates=[CERTIFICATES,...]]
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map entry resource - The certificate map entry to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the certificate map entry or fully qualified identifier for the
     certificate map entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].

  --map=MAP
     The certificate map for the certificate map entry.

     To set the map attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --map on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hostname` | HOSTNAME |  | _[Exactly one of these must be specified:]_ A domain name (FQDN), which controls when list of certificates specified in the resource will be taken under consideration for certificate selection. |
| `--set-primary` |  |  | _[Exactly one of these must be specified:]_ The certificate will be used as the default cert if no other certificate in the map matches on SNI. |


**Examples:**
```bash
To create a certificate map entry with name simple-entry, run:

    $ gcloud certificate-manager maps entries create simple-entry \
        --map=simple-map --certificates=simple-cert
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/entries/create)

---
### `gcloud certificate-manager maps entries delete`

Delete a certificate map entry

Delete a certificate map entry resource.

**Synopsis:**
```
gcloud certificate-manager maps entries delete
    (ENTRY : --location=LOCATION --map=MAP) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map entry resource - The certificate map entry to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the certificate map entry or fully qualified identifier for the
     certificate map entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].

  --map=MAP
     The certificate map for the certificate map entry.

     To set the map attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --map on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the certificate map entry with name simple-entry, run:

    $ gcloud certificate-manager maps entries delete simple-entry \
        --map=simple-map
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/entries/delete)

---
### `gcloud certificate-manager maps entries describe`

Describe an existing certificate map entry

This command fetches and prints information about an existing certificate
map entry.

**Synopsis:**
```
gcloud certificate-manager maps entries describe
    (ENTRY : --location=LOCATION --map=MAP) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map entry resource - The certificate map entry to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the certificate map entry or fully qualified identifier for the
     certificate map entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].

  --map=MAP
     The certificate map for the certificate map entry.

     To set the map attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --map on the command line.
```

**Examples:**
```bash
To describe a certificate map entry with name simple-entry, run:

    $ gcloud certificate-manager maps entries describe simple-entry \
        --map=simple-map
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/entries/describe)

---
### `gcloud certificate-manager maps entries list`

List certificate map entries

List Certificate Manager certificate map entries in the certificate map.

**Synopsis:**
```
gcloud certificate-manager maps entries list
    (--map=MAP : --location=LOCATION) [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--map` | MAP |  | _[This must be specified.]_ ID of the certificate map or fully qualified identifier for the certificate map. To set the map attribute: + provide the argument --map on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Cloud location for the certificate map. To set the location attribute: + provide the argument --map on the command line with a fully specified name; + provide the argument --location on the command line; + default value of location is [global]. |


**Examples:**
```bash
To list all certificate map entries in the certificate map, run:

    $ gcloud certificate-manager maps entries list --map=simple-map
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/entries/list)

---
### `gcloud certificate-manager maps entries update`

Update a certificate map entry

This command updates existing certificate map entry.

**Synopsis:**
```
gcloud certificate-manager maps entries update
    (ENTRY : --location=LOCATION --map=MAP) [--description=DESCRIPTION]
    [--async] [--certificates=[CERTIFICATES,...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Certificate map entry resource - The certificate map entry to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument entry on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENTRY
     ID of the certificate map entry or fully qualified identifier for the
     certificate map entry.

     To set the entry attribute:
     + provide the argument entry on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the certificate map entry.

     To set the location attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + default value of location is [global].

  --map=MAP
     The certificate map for the certificate map entry.

     To set the map attribute:
     + provide the argument entry on the command line with a fully
       specified name;
     + provide the argument --map on the command line.
```

**Examples:**
```bash
To update a certificate map entry with name simple-entry, run:

    $ gcloud certificate-manager maps entries update simple-entry \
        --map="simple-map" --description="desc" \
        --update-labels="key=value" --certificates="simple-cert"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/certificate-manager/maps/entries/update)

---