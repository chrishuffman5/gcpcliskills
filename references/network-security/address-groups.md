# gcloud network-security address-groups

manage Network Security AddressGroups

### `gcloud network-security address-groups add-items`

Add items to an address group

Add items to an existing address group.

**Synopsis:**
```
gcloud network-security address-groups add-items
    (ADDRESS_GROUP : --location=LOCATION) [--async] [--items=[ITEMS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--items` | [ITEMS,...] |  | Items to be added to the address group. |


**Examples:**
```bash
Add an item to an address group named my-address-group.

    $ gcloud network-security address-groups add-items \
        my-address-group --items=192.168.1.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/add-items)

---
### `gcloud network-security address-groups clone-items`

Clone items from source address group

Clone items from source address group.

**Synopsis:**
```
gcloud network-security address-groups clone-items
    (ADDRESS_GROUP : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Source address group to be cloned from. |


**Examples:**
```bash
Clone items from source address group named other-address-group.

    $ gcloud network-security address-groups clone-items \
        my-address-group \
        --source=projects/other/locations/global/other-address-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/clone-items)

---
### `gcloud network-security address-groups create`

Create an address group

Create a new address group with the given name.

**Synopsis:**
```
gcloud network-security address-groups create
    (ADDRESS_GROUP : --location=LOCATION) --capacity=CAPACITY --type=TYPE
    [--async] [--description=DESCRIPTION] [--items=[ITEMS,...]]
    [--labels=[KEY=VALUE,...]] [--purpose=[PURPOSE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be created. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--capacity` | CAPACITY |  | Capacity of the address group. |
| `--type` | one of: ipv4, ipv6 |  | Type of the address group. TYPE must be one of: ipv4, ipv6. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the address group. |
| `--items` | [ITEMS,...] |  | Items of the address group. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |
| `--purpose` | one of: cloud-armor, default |  | List of Address Group purposes. PURPOSE must be one of: cloud-armor, default. |


**Examples:**
```bash
Create an address group with the name my-address-group, type IPV4, capacity
100 and the description optional description.

    $ gcloud network-security address-groups create my-address-group \
        --type=IPV4 --capacity=100 --description="optional description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/create)

---
### `gcloud network-security address-groups delete`

Delete address group

Delete the specified address group.

**Synopsis:**
```
gcloud network-security address-groups delete
    (ADDRESS_GROUP : --location=LOCATION) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group you want to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an address group called 'my-address-group', run:

    $ gcloud network-security address-groups delete my-address-group \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/delete)

---
### `gcloud network-security address-groups describe`

Describe an address group

Show details of an address group.

**Synopsis:**
```
gcloud network-security address-groups describe
    (ADDRESS_GROUP : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be described. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about an address group named my-address-group.

    $ gcloud network-security address-groups describe my-address-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/describe)

---
### `gcloud network-security address-groups list`

List address groups

List all address groups in the specified location of the current project.

**Synopsis:**
```
gcloud network-security address-groups list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list address groups in the current project, run:

    $ gcloud network-security address-groups list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/list)

---
### `gcloud network-security address-groups list-references`

Lists References of an Address Group

Lists References of an Address Group.

**Synopsis:**
```
gcloud network-security address-groups list-references
    (ADDRESS_GROUP : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - address group group help. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument ADDRESS_GROUP on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument ADDRESS_GROUP on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument ADDRESS_GROUP on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To list References of address group named my-address-group.

    $ gcloud network-security address-groups list-references \
        my-address-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/list-references)

---
### `gcloud network-security address-groups remove-items`

Remove items from an address group

Remove items from an existing address group.

**Synopsis:**
```
gcloud network-security address-groups remove-items
    (ADDRESS_GROUP : --location=LOCATION) [--async] [--items=[ITEMS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--items` | [ITEMS,...] |  | Items to be removed from the address group. |


**Examples:**
```bash
Remove an item from an address group named my-address-group.

    $ gcloud network-security address-groups remove-items \
        my-address-group --items=192.168.1.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/remove-items)

---
### `gcloud network-security address-groups update`

Update an address group

Update the details of an address group.

**Synopsis:**
```
gcloud network-security address-groups update
    (ADDRESS_GROUP : --location=LOCATION) [--async]
    [--description=DESCRIPTION] [--items=[ITEMS,...]]
    [--purpose=[PURPOSE,...]] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument address_group on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDRESS_GROUP
     ID of the address group or fully qualified identifier for the address
     group.

     To set the address_group attribute:
     + provide the argument address_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the address group. |
| `--items` | [ITEMS,...] |  | Items of the address group. |
| `--purpose` | one of: cloud-armor, default |  | List of Address Group purposes. PURPOSE must be one of: cloud-armor, default. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
Update description of an address group named my-address-group.

    $ gcloud network-security address-groups update my-address-group \
        --description="New description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/address-groups/update)

---