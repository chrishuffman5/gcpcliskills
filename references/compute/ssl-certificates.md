# gcloud compute ssl-certificates

list, create, and delete Compute Engine SSL certificate resources

### `gcloud compute ssl-certificates create`

Create a Compute Engine SSL certificate

gcloud compute ssl-certificates create creates SSL certificate resources,
which you can use in a target HTTPS or target SSL proxy. An SSL certificate
resource consists of a certificate and private key. The private key is
encrypted before it is stored.

You can create either a managed or a self-managed SslCertificate resource.
A managed SslCertificate is provisioned and renewed for you. A self-managed
certificate is created by passing the certificate obtained from Certificate
Authority through --certificate and --private-key flags.

**Synopsis:**
```
gcloud compute ssl-certificates create NAME
    (--domains=DOMAIN,[DOMAIN,...]
      | --certificate=LOCAL_FILE_PATH --private-key=LOCAL_FILE_PATH)
    [--description=DESCRIPTION] [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the SSL certificate to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--domains` | DOMAIN,[DOMAIN,...] |  | _[Exactly one of these must be specified:]_ List of domains to create a managed certificate for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the SSL certificate. |


**Examples:**
```bash
To create a self-managed certificate resource 'my-cert' from a certificate
placed under path 'foo/cert' and a private key placed under path 'foo/pk',
run:

    $ gcloud compute ssl-certificates create my-cert \
      --certificate=foo/cert --private-key=foo/pk
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/ssl-certificates/create)

---
### `gcloud compute ssl-certificates delete`

Delete Compute Engine SSL certificates

gcloud compute ssl-certificates delete deletes one or more Compute Engine
SSL certificate resources. SSL certificates can only be deleted when no
other resources (for example, target HTTPS proxies) refer to them.

**Synopsis:**
```
gcloud compute ssl-certificates delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the SSL certificates to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the SSL certificates are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the SSL certificates to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To delete a certificate resource 'my-cert', run:

    $ gcloud compute ssl-certificates delete my-cert

To delete certificate resources 'my-cert1', 'my-cert2' and 'my-cert3', run:

    $ gcloud compute ssl-certificates delete my-cert1 my-cert2 my-cert3
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/ssl-certificates/delete)

---
### `gcloud compute ssl-certificates describe`

Describe a Compute Engine SSL certificate

gcloud compute ssl-certificates describe displays all data (except private
keys) associated with Compute Engine SSL certificate resources in a
project.

**Synopsis:**
```
gcloud compute ssl-certificates describe NAME [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the SSL certificate to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ (Default) If set, the SSL certificate is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the SSL certificate to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To display a description of a certificate 'my-cert', run:

    $ gcloud compute ssl-certificates describe my-cert
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/ssl-certificates/describe)

---
### `gcloud compute ssl-certificates list`

List Google Compute Engine SSL certificates

gcloud compute ssl-certificates list displays all Google Compute Engine SSL
certificates in a project.

By default, global SSL certificates and SSL certificates from all regions
are listed. The results can be narrowed down by providing the --global or
--regions flag.

**Synopsis:**
```
gcloud compute ssl-certificates list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--global | --regions=[REGION,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |


**Examples:**
```bash
To list all SSL certificates in a project in table form, run:

    $ gcloud compute ssl-certificates list

To list the URIs of all SSL certificates in a project, run:

    $ gcloud compute ssl-certificates list --uri

To list all global SSL certificates in a project, run:

    $ gcloud compute ssl-certificates list --global

To list all SSL certificates in the us-central1 and europe-west1 regions,
given they are regional resources, run:

    $ gcloud compute ssl-certificates list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/ssl-certificates/list)

---