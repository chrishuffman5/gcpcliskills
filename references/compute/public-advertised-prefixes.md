# gcloud compute public-advertised-prefixes

manage public advertised prefix resources

### `gcloud compute public-advertised-prefixes create`

Creates a Compute Engine public advertised prefix

**Synopsis:**
```
gcloud compute public-advertised-prefixes create NAME --range=RANGE
    [--description=DESCRIPTION] [--dns-verification-ip=DNS_VERIFICATION_IP]
    [--ipv6-access-type=IPV6_ACCESS_TYPE] [--pdp-scope=PDP_SCOPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public advertised prefix to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--range` | RANGE |  | IP range allocated to this public advertised prefix, in CIDR format. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description of this public advertised prefix. |
| `--dns-verification-ip` | DNS_VERIFICATION_IP |  | IP address to use for verification. It must be within the IP range specified in --range. |
| `--ipv6-access-type` | one of: internal, external |  | Specifies the IPv6 access type of the public advertised prefix. IPV6_ACCESS_TYPE must be one of: internal, external. |
| `--pdp-scope` | one of: GLOBAL, REGIONAL |  | Specifies how child public delegated prefix will be scoped. PDP_SCOPE must be one of: GLOBAL, REGIONAL. |


**Examples:**
```bash
To create a public advertised prefix:

    $ gcloud compute public-advertised-prefixes create \
        my-public-advertised-prefix --range=120.120.10.0/24 \
        --dns-verification-ip=120.120.10.15

To create a v2 public advertised prefix:

    $ gcloud compute public-advertised-prefixes create \
        my-v2-public-advertised-prefix --range=120.120.10.0/24 \
        --dns-verification-ip=120.120.10.15 --pdp-scope=REGIONAL
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-advertised-prefixes/create)

---
### `gcloud compute public-advertised-prefixes delete`

Deletes a Compute Engine public advertised prefix

**Synopsis:**
```
gcloud compute public-advertised-prefixes delete NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public advertised prefix to operate on.
```

**Examples:**
```bash
To delete a public advertised prefix:

    $ gcloud compute public-advertised-prefixes delete \
        my-public-advertised-prefix
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-advertised-prefixes/delete)

---
### `gcloud compute public-advertised-prefixes describe`

Describes a Compute Engine public advertised prefix

**Synopsis:**
```
gcloud compute public-advertised-prefixes describe NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public advertised prefix to operate on.
```

**Examples:**
```bash
To describe a public advertised prefix:

    $ gcloud compute public-advertised-prefixes describe my-pap
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-advertised-prefixes/describe)

---
### `gcloud compute public-advertised-prefixes list`

List Google Compute Engine public advertised prefixes

gcloud compute public-advertised-prefixes list displays all Google Compute
Engine public advertised prefixes in a project.

**Synopsis:**
```
gcloud compute public-advertised-prefixes list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all public advertised prefixes in a project in table form, run:

    $ gcloud compute public-advertised-prefixes list

To list the URIs of all public advertised prefixes in a project, run:

    $ gcloud compute public-advertised-prefixes list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-advertised-prefixes/list)

---
### `gcloud compute public-advertised-prefixes update`

Updates a Compute Engine public advertised prefix

**Synopsis:**
```
gcloud compute public-advertised-prefixes update NAME
    (--announce-prefix | --status=STATUS | --withdraw-prefix)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the public advertised prefix to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--announce-prefix` |  |  | _[Exactly one of these must be specified:]_ Specify if the prefix will be announced. Default is false. |
| `--status` | STATUS |  | _[Exactly one of these must be specified:]_ The status of public advertised prefix. STATUS must be (only one value is supported): ptr-configured. |
| `--withdraw-prefix` |  |  | _[Exactly one of these must be specified:]_ Specify if the prefix will be withdrawn. Default is false. |


**Examples:**
```bash
To update a public advertised prefix:

    $ gcloud compute public-advertised-prefixes update my-pap \
        --status=ptr-configured

To announce a public advertised prefix:

    $ gcloud compute public-advertised-prefixes update my-pap \
        --announce-prefix

To withdraw a public advertised prefix:

    $ gcloud compute public-advertised-prefixes update my-pap \
        --withdraw-prefix
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/public-advertised-prefixes/update)

---