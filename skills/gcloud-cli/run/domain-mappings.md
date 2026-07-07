# gcloud run domain-mappings

view and manage your Cloud Run for Anthos domain mappings

### `gcloud run domain-mappings create`

Create domain mappings for Cloud Run for Anthos

Create domain mappings for Cloud Run for Anthos.

For domain mapping support with fully managed Cloud Run, use gcloud beta
run domain-mappings create.

**Synopsis:**
```
gcloud run domain-mappings create --service=SERVICE
    (--domain=DOMAIN : --namespace=NAMESPACE) [--force-override]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | Create domain mapping for the given service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force-override` |  |  | Map this domain even if it is already mapped to another service. |


**Examples:**
```bash
To create a Cloud Run domain mapping, run:

    $ gcloud run domain-mappings create --service=myapp \
      --domain=www.example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/domain-mappings/create)

---
### `gcloud run domain-mappings delete`

Delete domain mappings for Cloud Run for Anthos

Delete domain mappings for Cloud Run for Anthos.

For domain mapping support with fully managed Cloud Run, use gcloud beta
run domain-mappings delete.

**Synopsis:**
```
gcloud run domain-mappings delete (--domain=DOMAIN : --namespace=NAMESPACE)
    [--[no-]async] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--domain` | DOMAIN |  | _[This must be specified.]_ ID of the DomainMapping or fully qualified identifier for the DomainMapping. To set the domain attribute: + provide the argument --domain on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--namespace` | NAMESPACE |  | _[This must be specified.]_ Specific to Cloud Run for Anthos: Kubernetes namespace for the DomainMapping. To set the namespace attribute: + provide the argument --domain on the command line with a fully specified name; + provide the argument --namespace on the command line; + set the property run/namespace; + For Cloud Run on Kubernetes Engine, defaults to "default". Otherwise, defaults to project ID.; + provide the argument project on the command line; + set the property core/project. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]async` |  |  | Return immediately, without waiting for the operation in progress to complete. Defaults to --no-async. Use --async to enable and --no-async to disable. |


**Examples:**
```bash
To delete a Cloud Run domain mapping, run:

    $ gcloud run domain-mappings delete --domain=www.example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/domain-mappings/delete)

---
### `gcloud run domain-mappings describe`

Describe domain mappings for Cloud Run for Anthos

Describe domain mappings for Cloud Run for Anthos.

For domain mapping support with fully managed Cloud Run, use gcloud beta
run domain-mappings describe.

**Synopsis:**
```
gcloud run domain-mappings describe
    (--domain=DOMAIN : --namespace=NAMESPACE) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--domain` | DOMAIN |  | _[This must be specified.]_ ID of the DomainMapping or fully qualified identifier for the DomainMapping. To set the domain attribute: + provide the argument --domain on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--namespace` | NAMESPACE |  | _[This must be specified.]_ Specific to Cloud Run for Anthos: Kubernetes namespace for the DomainMapping. To set the namespace attribute: + provide the argument --domain on the command line with a fully specified name; + provide the argument --namespace on the command line; + set the property run/namespace; + For Cloud Run on Kubernetes Engine, defaults to "default". Otherwise, defaults to project ID.; + provide the argument project on the command line; + set the property core/project. |


**Examples:**
```bash
To describe a Cloud Run domain mapping, run:

    $ gcloud run domain-mappings describe --domain=www.example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/domain-mappings/describe)

---
### `gcloud run domain-mappings list`

Lists domain mappings for Cloud Run for Anthos

Lists domain mappings for Cloud Run for Anthos.

For domain mapping support with fully managed Cloud Run, use gcloud beta
run domain-mappings list.

**Synopsis:**
```
gcloud run domain-mappings list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all Cloud Run domain mappings, run:

    $ gcloud run domain-mappings list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/domain-mappings/list)

---