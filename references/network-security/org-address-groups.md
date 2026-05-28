# gcloud network-security org-address-groups

manage Network Security AddressGroups

### `gcloud network-security org-address-groups add-items`

Add items to an address group of organization

Add items to an existing address group of organization.

**Synopsis:**
```
gcloud network-security org-address-groups add-items
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--items=[ITEMS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--items` | [ITEMS,...] |  | Items to be added to the address group. |


**Examples:**
```bash
Add an item to an address group named my-address-group of organization
1234.

    $ gcloud network-security org-address-groups add-items \
        my-address-group --items=192.168.1.1 --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/add-items)

---
### `gcloud network-security org-address-groups clone-items`

Clone items from source address group of organization

Clone items from source address group of organization.

**Synopsis:**
```
gcloud network-security org-address-groups clone-items
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Source address group to be cloned from. |


**Examples:**
```bash
Clone items from source address group named other-address-group of
organization 1234.

    $ gcloud network-security org-address-groups clone-items \
        my-address-group --organization=1234 \
        --source=other-address-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/clone-items)

---
### `gcloud network-security org-address-groups create`

Create an address group

Create a new address group with the given name.

**Synopsis:**
```
gcloud network-security org-address-groups create
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    --capacity=CAPACITY --type=TYPE [--async] [--description=DESCRIPTION]
    [--items=[ITEMS,...]] [--labels=[KEY=VALUE,...]]
    [--purpose=[PURPOSE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be created. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
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

    $ gcloud network-security org-address-groups create \
        my-address-group --type=IPV4 --capacity=100 \
        --description="optional description" --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/create)

---
### `gcloud network-security org-address-groups delete`

Delete address group

Delete the specified address group.

**Synopsis:**
```
gcloud network-security org-address-groups delete
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group you want to delete. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an address group called 'my-address-group', run:

    $ gcloud network-security org-address-groups delete \
        my-address-group --location=global --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/delete)

---
### `gcloud network-security org-address-groups describe`

Describe an address group

Show details of an address group.

**Synopsis:**
```
gcloud network-security org-address-groups describe
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be described. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
Show details about an address group named my-address-group.

    $ gcloud network-security org-address-groups describe \
        my-address-group --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/describe)

---
### `gcloud network-security org-address-groups list`

List address groups

List all address groups in the specified location of an organization.

**Synopsis:**
```
gcloud network-security org-address-groups list
    (--location=LOCATION : --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ Organization number. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list address groups in an organization, run:

    $ gcloud network-security org-address-groups list \
        --location=global --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/list)

---
### `gcloud network-security org-address-groups list-references`

Lists References of an Organization Address Group

Lists References of an Organization Address Group.

**Synopsis:**
```
gcloud network-security org-address-groups list-references
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - address group group help. The arguments in this
group can be used to specify the attributes of this resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument ADDRESS_GROUP on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To list References of address group named my-address-group.

    $ gcloud network-security org-address-groups list-references \
        my-address-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/list-references)

---
### `gcloud network-security org-address-groups remove-items`

Remove items from an address group of organization

Remove items from an existing address group of organization.

**Synopsis:**
```
gcloud network-security org-address-groups remove-items
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--items=[ITEMS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--items` | [ITEMS,...] |  | Items to be removed from the address group. |


**Examples:**
```bash
Remove an item from an address group named my-address-group of organization
1234.

    $ gcloud network-security org-address-groups remove-items \
        my-address-group --items=192.168.1.1 --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/remove-items)

---
### `gcloud network-security org-address-groups update`

Update an address group

Update the details of an address group.

**Synopsis:**
```
gcloud network-security org-address-groups update
    (ADDRESS_GROUP : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--description=DESCRIPTION] [--items=[ITEMS,...]]
    [--purpose=[PURPOSE,...]] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Address group resource - Name of the address group to be updated. The
arguments in this group can be used to specify the attributes of this
resource.

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

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument address_group on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
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

    $ gcloud network-security org-address-groups update \
        my-address-group --description="New description" \
        --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/org-address-groups/update)

---