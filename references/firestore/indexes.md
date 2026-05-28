# gcloud firestore indexes

manage indexes for Cloud Firestore


## `gcloud firestore indexes composite` — manage composite indexes for Cloud Firestore
### `gcloud firestore indexes composite create`

Create a new composite index

Create a new composite index.

**Synopsis:**
```
gcloud firestore indexes composite create
    --field-config=[array-config=ARRAY-CONFIG],
      [field-path=FIELD-PATH],[order=ORDER],[vector-config=VECTOR-CONFIG]
    (--collection-group=COLLECTION_GROUP : --database=DATABASE)
    [--api-scope=API_SCOPE; default="any-api"] [--async]
    [--density=DENSITY] [--multikey]
    [--query-scope=QUERY_SCOPE; default="collection"] [--unique]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--field-config` | [array-config=ARRAY-CONFIG],[field-path=FIELD-PATH],[order=ORDER],[vector-config=VECTOR-CONFIG] |  | Required, Configuration for an index field. array-config Specifies the configuration for an array field. The only valid option is 'contains'. Exactly one of 'order', 'array-config', or 'vector-config' must be specified. field-path Specifies the field path (e.g. 'address.city'). This is required. order Specifies the order. Valid options are 'ascending', 'descending'. Exactly one of 'order', 'array-config', or 'vector-config' must be specified. vector-config Specifies the configuration for a vector field. Exactly one of 'order', 'array-config', or 'vector-config' must be specified. dimension Sets dimension value. flat Sets flat value. Shorthand Example: --field-config=array-config=string,field-path=string,order=string,vector-config={dimension=int,flat} --field-config=array-config=string,field-path=string,order=string,vector-config={dimension=int,flat} JSON Example: --field-config='[{"array-config": "string", "field-path": "string", "order": "string", "vector-config": {"dimension": int, "flat": {}}}]' File Example: --field-config=path_to_file.(yaml\|json) |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api-scope` | one of: any-api, datastore-mode-api, mongodb-compatible-api | any-api | Api scope the index applies to. API_SCOPE must be one of: any-api, datastore-mode-api, mongodb-compatible-api. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--density` | one of: dense, density-unspecified, sparse-all, sparse-any |  | Density of the index. DENSITY must be one of: dense, density-unspecified, sparse-all, sparse-any. |
| `--multikey` |  |  | Optional. Whether the index is multikey. By default, the index is not multikey. For non-multikey indexes, none of the paths in the index definition reach or traverse an array, except via an explicit array index. For multikey indexes, at most one of the paths in the index definition reach or traverse an array, except via an explicit array index. Violations will result in errors. Note this field only applies to index with MONGODB_COMPATIBLE_API ApiScope. |
| `--query-scope` | one of: collection, collection-group, collection-recursive | collection | Query scope the index applies to. QUERY_SCOPE must be one of: collection, collection-group, collection-recursive. |
| `--unique` |  |  | Optional. Whether it is an unique index. Unique index ensures all values for the indexed field(s) are unique across documents. |


**Examples:**
```bash
The following command creates a composite index with fields user_id (in
descending order) followed by timestamp (in descending order) in the Events
collection group.

    $ gcloud firestore indexes composite create \
        --collection-group=Events \
        --field-config=field-path=user-id,order=descending \
        --field-config=field-path=timestamp,order=descending

    $ gcloud firestore indexes composite create --database=(default) \
        --collection-group=Events \
        --field-config=field-path=user-id,order=descending \
        --field-config=field-path=timestamp,order=descending
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/composite/create)

---
### `gcloud firestore indexes composite delete`

Delete the given composite index

Delete the given composite index.

**Synopsis:**
```
gcloud firestore indexes composite delete (INDEX : --database=DATABASE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Composite index resource - Index to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the collection-group attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument [--collection-group] on the command line.

This must be specified.

  INDEX
     ID of the composite index or fully qualified identifier for the
     composite index.

     To set the index attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --database=DATABASE
     Database of the composite index.

     To set the database attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --database on the command line;
     + the default value of argument [--database] is (default).
```

**Examples:**
```bash
The following command deletes the composite index with ID 3421ef:

    $ gcloud firestore indexes composite delete 3421ef

    $ gcloud firestore indexes composite delete 3421ef \
        --database=(default)
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/composite/delete)

---
### `gcloud firestore indexes composite describe`

Describe the given composite index

Describe the given composite index.

**Synopsis:**
```
gcloud firestore indexes composite describe (INDEX : --database=DATABASE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Composite index resource - Index to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the collection-group attribute:
 * provide the argument index on the command line with a fully specified
   name;
 * provide the argument [--collection-group] on the command line.

This must be specified.

  INDEX
     ID of the composite index or fully qualified identifier for the
     composite index.

     To set the index attribute:
     + provide the argument index on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --database=DATABASE
     Database of the composite index.

     To set the database attribute:
     + provide the argument index on the command line with a fully
       specified name;
     + provide the argument --database on the command line;
     + the default value of argument [--database] is (default).
```

**Examples:**
```bash
The following command describes the composite index with ID 3421ef:

    $ gcloud firestore indexes composite describe 3421ef

    $ gcloud firestore indexes composite describe 3421ef \
        --database=(default)
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/composite/describe)

---
### `gcloud firestore indexes composite list`

List composite indexes

List composite indexes.

**Synopsis:**
```
gcloud firestore indexes composite list [--database=DATABASE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | _[* provide the argument [--collection-group] on the command line.]_ Database of the collection group. To set the database attribute: + provide the argument [--collection-group] on the command line with a fully specified name; + provide the argument --database on the command line; + the default value of argument [--database] is (default). |


**Examples:**
```bash
The following command lists all composite indexes in the database:

    $ gcloud firestore indexes composite list

    $ gcloud firestore indexes composite list --database=(default)

The following command lists composite indexes in the Events collection
group:

    $ gcloud firestore indexes composite list \
        --filter=COLLECTION_GROUP:Events
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/composite/list)

---

## `gcloud firestore indexes fields` — manage single-field indexes for Cloud Firestore
### `gcloud firestore indexes fields describe`

Describe the index configuration of the given field

Describe the index configuration of the given field.

**Synopsis:**
```
gcloud firestore indexes fields describe
    [[FIELD] --collection-group=COLLECTION_GROUP --database=DATABASE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Field resource - Field to describe.

This can be omitted to describe the database-wide default index settings.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument field on the command line with a fully specified
   name;
 * with a fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

  [FIELD]
     ID of the field or fully qualified identifier for the field.

     To set the field attribute:
     + provide the argument field on the command line;
     + .

  --collection-group=COLLECTION_GROUP
     Collection group of the field.

     To set the collection-group attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + with a fully specified name;
     + provide the argument --collection-group on the command line;
     + .

  --database=DATABASE
     Database of the field.

     To set the database attribute:
     + provide the argument field on the command line with a fully
       specified name;
     + with a fully specified name;
     + provide the argument --database on the command line;
     + the default value of argument [--database] is (default).
```

**Examples:**
```bash
The following command describes the database-wide default index settings:

    $ gcloud firestore indexes fields describe

    $ gcloud firestore indexes fields describe --database=(default)

The following command describes the index configuration of the timestamp
field in the Events collection group.

    $ gcloud firestore indexes fields describe timestamp \
        --collection-group=Events
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/fields/describe)

---
### `gcloud firestore indexes fields list`

List fields with non-default index settings

List fields that have had their index configurations exempted from the
automatic settings. This includes the field describing the database-wide
default index settings, unless otherwise filtered out.

**Synopsis:**
```
gcloud firestore indexes fields list
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
The following command lists all fields with custom index settings:

    $ gcloud firestore indexes fields list

    $ gcloud firestore indexes fields list --database=(default)

The following command lists fields with custom index settings in the Events
collection group:

    $ gcloud firestore indexes fields list --collection-group=Events

The following command lists the indexes of all fields with custom index
settings:

    $ gcloud firestore indexes fields list \
        --format="table[box](name,indexConfig.indexes:format='table[titl\
    e=INDEXES,box](fields.order.flatten(),fields.arrayConfig.flatten(),q\
    ueryScope,state)')"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/fields/list)

---
### `gcloud firestore indexes fields update`

Update the index configuration of the given field

Update the index configuration of the given field.

This creates an exemption for the field in question, allowing one to modify
the field's index settings and override the defaults.

**Synopsis:**
```
gcloud firestore indexes fields update
    (FIELD : --collection-group=COLLECTION_GROUP --database=DATABASE)
    (--clear-exemption | --disable-indexes | --index=[KEY=VALUE,...])
    [--async] [GCLOUD_WIDE_FLAG ...]
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
| `--clear-exemption` |  |  | _[Exactly one of these must be specified:]_ If provided, the field's current index configuration will be reverted to inherit from its ancestor index configurations. |
| `--disable-indexes` |  |  | _[Exactly one of these must be specified:]_ If provided, the field will no longer be indexed at all. |
| `--index` | [KEY=VALUE,...] |  | _[Exactly one of these must be specified:]_ An index for the field. This flag can be repeated to provide multiple indexes. Any existing indexes will be overwritten with the ones provided. Any omitted indexes will be deleted if they currently exist. The following keys are allowed: order Specifies the order. Valid options are: 'ascending', 'descending'. Exactly one of 'order' or 'array-config' must be specified. array-config Specifies the configuration for an array field. The only valid option is 'contains'. Exactly one of 'order' or 'array-config' must be specified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
The following command creates an exemption for the timestamp field in the
Events collection group, in which all indexes are disabled:

    $ gcloud firestore indexes fields update timestamp \
        --collection-group=Events --disable-indexes

    $ gcloud firestore indexes fields update timestamp \
        --database=(default) --collection-group=Events --disable-indexes

The following command creates an exemption for the timestamp field in the
Events collection group, in which the list of indexes is explicitly set to
[ASCENDING, DESCENDING]:

    $ gcloud firestore indexes fields update timestamp \
        --collection-group=Events --index=order=ASCENDING \
        --index=order=DESCENDING

The following command clears the exemption on the timestamp field in the
Events collection group, so that the field will return to inheriting its
index settings from its ancestors:

    $ gcloud firestore indexes fields update timestamp \
        --collection-group=Events --clear-exemption
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/indexes/fields/update)

---