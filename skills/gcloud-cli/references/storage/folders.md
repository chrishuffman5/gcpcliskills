# gcloud storage folders

manage Cloud Storage folders

### `gcloud storage folders create`

Create folders for hierarchical namespace bucket

Create folders.

**Synopsis:**
```
gcloud storage folders create URL [URL ...]
    [--additional-headers=HEADER=VALUE] [--recursive]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs of the folders to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--recursive` |  |  | Recursively create all folders in a given path if they do not alraedy exist. |


**Examples:**
```bash
The following command creates a folder called folder/ in a bucket named
my-bucket:

    $ gcloud storage folders create gs://my-bucket/folder/

The following command creates all folders in the path A/B/C/D in a bucket
named my-bucket:

    $ gcloud storage folders create \
        --recursive gs://my-bucket/folder/A/B/C/D
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/folders/create)

---
### `gcloud storage folders delete`

Delete folders

Delete folders.

**Synopsis:**
```
gcloud storage folders delete URLS [URLS ...]
    [--additional-headers=HEADER=VALUE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   The URLs of the folders to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |


**Examples:**
```bash
The following command deletes a folder named folder in a hierarchical
namesapce bucket called my-bucket:

    $ gcloud storage folders delete gs://my-bucket/folder/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/folders/delete)

---
### `gcloud storage folders describe`

Describe hierarchical namesapace bucket folders

Describe hierarchical namespace bucket folders.

**Synopsis:**
```
gcloud storage folders describe URL [--additional-headers=HEADER=VALUE]
    [--raw] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   The URL of the folder to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
The following command shows information about a folder named folder in an
hierarchical namespace bucket called my-bucket:

    $ gcloud storage folders describe gs://my-bucket/folder/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/folders/describe)

---
### `gcloud storage folders list`

List folders

List folders.

**Synopsis:**
```
gcloud storage folders list URL [URL ...]
    [--additional-headers=HEADER=VALUE] [--raw] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs of the resources to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--raw` |  |  | Shows metadata in the format returned by the API instead of standardizing it. |


**Examples:**
```bash
The following command lists all folders in a hierarchical namespace bucket:

    $ gcloud storage folders list gs://my-bucket/

The following command lists all folders under a parent folder:

    $ gcloud storage folders list gs://my-bucket/parent-folder/

You can use wildcards (https://cloud.google.com/storage/docs/wildcards) to
match multiple paths (including multiple buckets). Bucket wildcards are
expanded to match only buckets contained in your current project. The
following command matches folders that are stored in buckets in your
project that begin with my-b:

    $ gcloud storage folders list gs://my-b*/

Following is another example where we are listing all folders that begin
with ``B'' under a given bucket:

    $ gcloud storage folders list gs://my-bucket/B*
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/folders/list)

---