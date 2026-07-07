# gcloud scc posture-operations

manage Cloud Security Command Center posture operations

### `gcloud scc posture-operations describe`

Describe a Cloud Security Command Center posture long running operation

Describe a Cloud Security Command Center (SCC) posture long running
operation.

**Synopsis:**
```
gcloud scc posture-operations describe OPERATION_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
OPERATION_NAME
   Relative resource name of the operation, of the format:
   organizations/<organizationID>/locations/<location>/operations/<operationID>.
```

**Examples:**
```bash
To return long running operation status for operation
(operation-1694515698847-605272e4bcd7c-f93dade6-067467ae) of parent
organizations/123/locations/global, run:

    $ gcloud scc posture-operations describe \
        organizations/123/locations/global/operations/\
    operation-1694515698847-605272e4bcd7c-f93dade6-067467ae
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/scc/posture-operations/describe)

---