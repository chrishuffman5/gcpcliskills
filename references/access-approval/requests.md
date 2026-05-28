# gcloud access-approval requests

manage Access Approval requests

### `gcloud access-approval requests approve`

Approve an Access Approval request

Approve an Access Approval request. This will raise an error if the request
does not exist or is not in a pending state.

**Synopsis:**
```
gcloud access-approval requests approve NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Access Approval request to invalidate
```

**Examples:**
```bash
To approve an approval request using its name (e.g.
projects/12345/approvalRequests/abc123), run:

    $ gcloud access-approval requests approve \
        projects/12345/approvalRequests/abc123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/requests/approve)

---
### `gcloud access-approval requests dismiss`

Dismiss an Access Approval request

Dismiss an Access Approval request. Note: this does not deny access to the
resource if another request has been made and approved for the same
resource. This will raise an error if the request does not exist.

**Synopsis:**
```
gcloud access-approval requests dismiss NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Access Approval request to invalidate
```

**Examples:**
```bash
To dismiss an approval request using its name (e.g.
projects/12345/approvalRequests/abc123), run:

    $ gcloud access-approval requests dismiss \
        projects/12345/approvalRequests/abc123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/requests/dismiss)

---
### `gcloud access-approval requests get`

Get an Access Approval request

Get an Access Approval Request. Raise error if the request does not exist.

**Synopsis:**
```
gcloud access-approval requests get NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Access Approval request to invalidate
```

**Examples:**
```bash
To get an approval request using its name (e.g.
projects/my-project-123/approvalRequests/abc123), run:

    $ gcloud access-approval requests get \
        projects/my-project-123/approvalRequests/abc123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/requests/get)

---
### `gcloud access-approval requests invalidate`

Invalidate an Access Approval request

Invalidate an Access Approval request. This will raise an error if the
request does not exist or is not in an approved state.

**Synopsis:**
```
gcloud access-approval requests invalidate NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the Access Approval request to invalidate
```

**Examples:**
```bash
To invalidate an approval request using its name (e.g.
projects/12345/approvalRequests/abc123), run:

    $ gcloud access-approval requests invalidate \
        projects/12345/approvalRequests/abc123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/requests/invalidate)

---
### `gcloud access-approval requests list`

List Access Approval requests

List Access Approval requests by parent (project/folder/organization).

**Synopsis:**
```
gcloud access-approval requests list [--state=STATE; default="pending"]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--state` | STATE | pending | filter for request state |


**Examples:**
```bash
To list all approval requests owned by project my-project-123, run:

    $ gcloud access-approval requests list --project=my-project-123 \
        --state=all

To list pending approval requests owned by organization 999, run:

    $ gcloud access-approval requests list --organization=999

or

    $ gcloud access-approval requests list --organization=999 \
        --state=pending

Note that the user needs to have permission accessapproval.requests.list on
the project/folder/organization
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-approval/requests/list)

---