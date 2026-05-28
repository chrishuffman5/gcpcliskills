# gcloud storage objects

manage Cloud Storage objects

### `gcloud storage objects compose`

Concatenate a sequence of objects into a new composite object

gcloud storage objects compose creates a new object whose content is the
concatenation of a given sequence of source objects in the same bucket. For
more information, please see: composite objects documentation
(https://cloud.google.com/storage/docs/composite-objects).

There is a limit (currently 32) to the number of components that can be
composed in a single operation.

**Synopsis:**
```
gcloud storage objects compose SOURCE [SOURCE ...] DESTINATION
    [--additional-headers=HEADER=VALUE]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION]
    [--retain-until=DATETIME --retention-mode=RETENTION_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SOURCE [SOURCE ...]
   The list of source objects that will be concatenated into a single
   object.

DESTINATION
   The destination object.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |


**Examples:**
```bash
The following command creates a new object target.txt by concatenating
a.txt and b.txt:

    $ gcloud storage objects compose gs://bucket/a.txt \
        gs://bucket/b.txt gs://bucket/target.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/objects/compose)

---
### `gcloud storage objects describe`

Describe a Cloud Storage object

Describe a Cloud Storage object.

**Synopsis:**
```
gcloud storage objects describe URL [--additional-headers=HEADER=VALUE]
    [--fetch-encrypted-object-hashes] [--raw] [--soft-deleted]
    [--decryption-keys=[DECRYPTION_KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   Specifies URL of object to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--fetch-encrypted-object-hashes` |  |  | If the initial GET request returns an object encrypted with a customer-supplied encryption key, the hash fields will be null. If the matching decryption key is present on the system, this flag retries the GET request with the key. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |
| `--soft-deleted` |  |  | Displays soft-deleted resources only. For objects, it will exclude live and noncurrent ones. |


**Examples:**
```bash
Describe a Google Cloud Storage object with the url
"gs://bucket/my-object":

    $ gcloud storage objects describe gs://bucket/my-object

Describe object with JSON formatting, only returning the "name" key:

    $ gcloud storage objects describe gs://bucket/my-object \
        --format="json(name)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/objects/describe)

---
### `gcloud storage objects list`

Lists Cloud Storage objects

List Cloud Storage objects.

Bucket URLs like gs://bucket match all the objects inside a bucket, but
gs://b* fails because it matches a list of buckets.

**Synopsis:**
```
gcloud storage objects list URLS [URLS ...]
    [--additional-headers=HEADER=VALUE] [--exhaustive]
    [--fetch-encrypted-object-hashes] [--next-page-token=NEXT_PAGE_TOKEN]
    [--raw] [--soft-deleted] [--stat]
    [--decryption-keys=[DECRYPTION_KEY,...]] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   Specifies URL of objects to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--exhaustive` |  |  | For features like soft delete, the API may return an empty list. If present, continue querying. This may incur costs from repeated LIST calls and may not return any additional objects. |
| `--fetch-encrypted-object-hashes` |  |  | API requests to the LIST endpoint do not fetch the hashes for encrypted objects by default. If this flag is set, a GET request is sent for each encrypted object in order to fetch hashes. This can significantly increase the cost of the command. |
| `--next-page-token` | NEXT_PAGE_TOKEN |  | Page token for resuming LIST calls. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |
| `--soft-deleted` |  |  | Displays soft-deleted resources only. For objects, it will exclude live and noncurrent ones. |
| `--stat` |  |  | Emulates gsutil stat-style behavior. Does not show past object versions and changes output format. |


**Examples:**
```bash
List all objects in bucket my-bucket within current directory level:

    $ gcloud storage objects list gs://my-bucket

List all objects across nested directories using wildcards
(https://cloud.google.com/storage/docs/wildcards):

    $ gcloud storage objects list gs://my-bucket/**

List all objects in bucket beginning with ``o'', including objects across
nested directories:

    $ gcloud storage objects list gs://my-bucket/**/o*

List all objects within current directory of bucket with JSON formatting,
only returning the value of the name metadata field:

    $ gcloud storage objects list gs://my-bucket --format="json(name)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/objects/list)

---
### `gcloud storage objects update`

Update Cloud Storage objects

Update Cloud Storage objects.

**Synopsis:**
```
gcloud storage objects update [URL ...] [--additional-headers=HEADER=VALUE]
    [--all-versions] [--continue-on-error, -c] [--[no-]event-based-hold]
    [--read-paths-from-stdin, -I] [--recursive, -R, -r]
    [--storage-class=STORAGE_CLASS, -s STORAGE_CLASS]
    [--[no-]temporary-hold]
    [--acl-file=ACL_FILE --add-acl-grant=[ACL_GRANT,...]
      --canned-acl=PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL, -a
      PREDEFINED_ACL
      --[no-]preserve-acl, -p --remove-acl-grant=REMOVE_ACL_GRANT]
    [--clear-encryption-key --decryption-keys=[DECRYPTION_KEY,...]
      --encryption-key=ENCRYPTION_KEY]
    [--cache-control=CACHE_CONTROL --clear-cache-control
      --clear-content-disposition --clear-content-encoding
      --clear-content-language --clear-content-type --clear-custom-time
      --content-disposition=CONTENT_DISPOSITION
      --content-encoding=CONTENT_ENCODING
      --content-language=CONTENT_LANGUAGE --content-type=CONTENT_TYPE
      --custom-time=CUSTOM_TIME --clear-custom-metadata
      | --custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]
      | --remove-custom-metadata=[METADATA_KEYS,...]
      --update-custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION]
    [--clear-retention --override-unlocked-retention
      --retain-until=DATETIME --retention-mode=RETENTION_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URL ...]
   Specifies URLs of objects to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--all-versions` |  |  | Perform the operation on all object versions. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--[no-]event-based-hold` |  |  | Enables or disables an event-based hold on objects. Use --event-based-hold to enable and --no-event-based-hold to disable. |
| `--read-paths-from-stdin, -I` |  |  | Read the list of objects to update from stdin. No need to enter a source argument if this flag is present. Example: "storage objects update -I --content-type=new-type" |
| `--recursive, -R, -r` |  |  | Recursively update objects under any buckets or directories that match the URL expression. |
| `--storage-class` | STORAGE_CLASS, -s STORAGE_CLASS |  | Specify the storage class of the object. Using this flag triggers a rewrite of underlying object data. |
| `--[no-]temporary-hold` |  |  | Enables or disables a temporary hold on objects. Use --temporary-hold to enable and --no-temporary-hold to disable. |
| `--acl-file` | ACL_FILE |  | Path to a local JSON or YAML formatted file containing a valid policy. See the ObjectAccessControls resource (https://cloud.google.com/storage/docs/json_api/v1/objectAccessControls) for a representation of JSON formatted files. The output of gcloud storage [buckets\|objects] describe --format="multi(acl:format=json)" is a valid file and can be edited for more fine-grained control. |
| `--add-acl-grant` | [ACL_GRANT,...] |  | Key-value pairs mirroring the JSON accepted by your cloud provider. For example, for Cloud Storage,--add-acl-grant=entity=user-tim@gmail.com,role=OWNER |
| `--canned-acl` | PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL, -a PREDEFINED_ACL |  | Applies predefined, or "canned," ACLs to a resource. See docs for a list of predefined ACL constants: https://cloud.google.com/storage/docs/access-control/lists#predefined-acl |
| `--[no-]preserve-acl, -p` |  |  | Preserves ACLs when copying in the cloud. This option is Cloud Storage-only, and you need OWNER access to all copied objects. If all objects in the destination bucket should have the same ACL, you can also set a default object ACL on that bucket instead of using this flag. Preserving ACLs is the default behavior for updating existing objects. Use --preserve-acl to enable and --no-preserve-acl to disable. |
| `--remove-acl-grant` | REMOVE_ACL_GRANT |  | Key-value pairs mirroring the JSON accepted by your cloud provider. For example, for Cloud Storage, --remove-acl-grant=ENTITY, where ENTITY has a valid ACL entity format, such as user-tim@gmail.com, group-admins, allUsers, etc. |


**Examples:**
```bash
Update a Google Cloud Storage object's custom-metadata:

    $ gcloud storage objects update gs://bucket/my-object \
        --custom-metadata=key1=value1,key2=value2

You can use wildcards (https://cloud.google.com/storage/docs/wildcards) to
update multiple objects in a single command. For instance to update all
objects to have a custom-metadata key:

    $ gcloud storage objects update gs://bucket/** \
        --custom-metadata=key1=value1,key2=value2

Rewrite all JPEG images to the NEARLINE storage class, including objects
across nested directories:

    $ gcloud storage objects update gs://bucket/**/*.jpg \
        --storage-class=NEARLINE

You can also provide a precondition on an object's metageneration in order
to avoid potential race conditions:

    $ gcloud storage objects update gs://bucket/*.jpg \
        --storage-class=NEARLINE --if-metageneration-match=123456789
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/objects/update)

---