# gcloud audit-manager enrollments

command group for Audit Manager Enrollments

### `gcloud audit-manager enrollments add`

Enroll a new scope

Enroll a new scope.

**Synopsis:**
```
gcloud audit-manager enrollments add --eligible-gcs-buckets=BUCKET
    URI,[BUCKET URI,...]
    (--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--eligible-gcs-buckets` | BUCKET URI,[BUCKET URI,...] |  | Eligible cloud storage buckets where report and evidence can be uploaded. |


**Examples:**
```bash
To enroll a project with ID 123 with gs://test-bucket-1 and
gs://my-bucket-2 as eligible storage buckets, run:

    $ gcloud audit-manager enrollments add --project=123 \
        --eligible-gcs-buckets="gs://test-bucket-1,gs://my-bucket-2"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/audit-manager/enrollments/add)

---