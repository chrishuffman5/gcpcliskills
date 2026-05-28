# gcloud firestore fields

manage field metadata for Cloud Firestore


## `gcloud firestore fields ttls` — manage Time-to-live metadata for Cloud Firestore
### `gcloud firestore fields ttls list`

List all fields used as a Time To Live expiration setting

List fields that give an expiration timestamp for documents in a collection
group or kind.

**Synopsis:**
```
gcloud firestore fields ttls list
    [--collection-group=COLLECTION_GROUP --database=DATABASE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collection-group` | COLLECTION_GROUP |  | _[* set the property core/project.]_ ID of the collection group or fully qualified identifier for the collection group. To set the collection-group attribute: + provide the argument --collection-group on the command line; + provide the argument [--collection-group] on the command line. |
| `--database` | DATABASE |  | _[* set the property core/project.]_ Database of the collection group. To set the database attribute: + provide the argument --collection-group on the command line with a fully specified name; + provide the argument [--collection-group] on the command line with a fully specified name; + provide the argument --database on the command line; + the default value of argument [--database] is (default). |


**Examples:**
```bash
The following command lists all TTL fields for the whole database:

    $ gcloud firestore fields ttls list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/fields/ttls/list)

---
### `gcloud firestore fields ttls update`

Update the TTL configuration of the given field

Update the TTL configuration of the given field.

This enables or disables using a field as the TTL field for its collection
group or kind. Note that only one field can be the TTL field for a
collection group.

**Synopsis:**
```
gcloud firestore fields ttls update
    (FIELD : --collection-group=COLLECTION_GROUP --database=DATABASE)
    (--disable-ttl | --enable-ttl) [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Field resource - Field to update. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument field on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIELD
     ID of the field or fully qualified identifier for the field.

     To set the field attribute:
     + provide the argument field on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --collection-group=COLLECTION_GROUP
     Collection group of the field.

     To set the collection-group attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --collection-group on the command line.

  --database=DATABASE
     Database of the field.

     To set the database attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + provide the argument --database on the command line;
     + the default value of argument [--database] is (default).
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disable-ttl` |  |  | _[Exactly one of these must be specified:]_ Set to make this field no longer the TTL for its collection group. |
| `--enable-ttl` |  |  | _[Exactly one of these must be specified:]_ Set to enable this field as the TTL for its collection group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command sets the expiry field of the Events collection group
(kind) to be the TTL field:

    $ gcloud firestore fields ttls update expiry \
        --collection-group=Events --enable-ttl

The following command disables the expiry field so it is no longer the TTL
for the Events collection group (kind):

    $ gcloud firestore fields ttls update expiry \
        --collection-group=Events --disable-ttl
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/fields/ttls/update)

---