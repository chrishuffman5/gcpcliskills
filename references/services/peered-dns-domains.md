# gcloud services peered-dns-domains

peered DNS domains for various private service connections

### `gcloud services peered-dns-domains create`

Create a peered DNS domain for a private service connection

This command creates a peered DNS domain for a private service connection
which sends requests for records in a given namespace originating in the
service producer VPC network to the consumer VPC network to be resolved.

**Synopsis:**
```
gcloud services peered-dns-domains create NAME --dns-suffix=DNS_SUFFIX
    --network=NETWORK [--async]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the peered DNS domain to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dns-suffix` | DNS_SUFFIX |  | The DNS domain name suffix of the peered DNS domain. |
| `--network` | NETWORK |  | The network in the consumer project peered with the service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The name of the service to create a peered DNS domain for. |


**Examples:**
```bash
To create a peered DNS domain called example-com which forwards DNS
requests for the domain suffix example.com. for a private service
connection between service peering-service and the consumer network
my-network in the current project, run:

    $ gcloud services peered-dns-domains create example-com \
        --network=my-network --service=peering-service \
        --dns-suffix=example.com.

To run the same command asynchronously (non-blocking), run:

    $ gcloud services peered-dns-domains create example-com \
        --network=my-network --service=peering-service \
        --dns-suffix=example.com. --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/peered-dns-domains/create)

---
### `gcloud services peered-dns-domains delete`

Delete a peered DNS domain for a private service connection

This command deletes a peered DNS domain from a private service connection.

**Synopsis:**
```
gcloud services peered-dns-domains delete NAME --network=NETWORK [--async]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The name of the peered DNS domain to delete.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the consumer project peered with the service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The name of the service to delete a peered DNS domain for. |


**Examples:**
```bash
To delete a peered DNS domain called example-com from a private service
connection between service peering-service and the consumer network
my-network in the current project, run:

    $ gcloud services peered-dns-domains delete example-com \
        --network=my-network --service=peering-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud services peered-dns-domains delete example-com \
        --network=my-network --service=peering-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/peered-dns-domains/delete)

---
### `gcloud services peered-dns-domains list`

List the peered DNS domains for a private service connection

This command lists the peered DNS domains for a private service connection.

**Synopsis:**
```
gcloud services peered-dns-domains list --network=NETWORK
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | Network in the consumer project peered with the service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE | servicenetworking.googleapis.com | Name of the service to list the peered DNS domains for. |


**Examples:**
```bash
To list the peered DNS domains for a private service connection between
service peering-service and the consumer network my-network in the current
project, run:

    $ gcloud services peered-dns-domains list --network=my-network \
        --service=peering-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/peered-dns-domains/list)

---