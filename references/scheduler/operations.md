# gcloud scheduler operations

get information about Cloud Scheduler operations

### `gcloud scheduler operations describe`

Show the latest status of an operation

Show the latest status of an operation.

**Synopsis:**
```
gcloud scheduler operations describe --name=NAME [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | NAME |  | The full name of the Cloud Scheduler operation to describe. Format: projects/{project}/locations/{location}/operations/{operation} |


**Examples:**
```bash
To describe the latest status of an operation:

    $ gcloud scheduler operations describe \
      projects/my-project/locations/us-central1/operations/\
    my-operation
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scheduler/operations/describe)

---