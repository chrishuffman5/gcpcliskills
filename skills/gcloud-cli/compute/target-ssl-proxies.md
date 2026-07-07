# gcloud compute target-ssl-proxies

list, create, and delete target SSL proxies

### `gcloud compute target-ssl-proxies create`

Create a target SSL proxy

gcloud compute target-ssl-proxies create is used to create target SSL
proxies. A target SSL proxy is referenced by one or more forwarding rules
which define which packets the proxy is responsible for routing. The target
SSL proxy points to a backend service which handle the actual requests. The
target SSL proxy also points to at most 15 SSL certificates used for
server-side authentication or one certificate map. The target SSL proxy can
be associated with at most one SSL policy.

**Synopsis:**
```
gcloud compute target-ssl-proxies create NAME
    --backend-service=BACKEND_SERVICE
    (--certificate-map=CERTIFICATE_MAP
      --ssl-certificates=SSL_CERTIFICATE,[...]) [--description=DESCRIPTION]
    [--proxy-header=PROXY_HEADER; default="NONE"] [--ssl-policy=SSL_POLICY]
    [--global-ssl-policy | --ssl-policy-region=SSL_POLICY_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target SSL proxy to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-service` | BACKEND_SERVICE |  | A backend service that will be used for connections to the target SSL proxy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the target SSL proxy. |
| `--proxy-header` | one of: NONE No proxy header is added | NONE | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Enables PROXY protocol (version 1) for passing client connection information. |
| `--ssl-policy` | SSL_POLICY |  | A reference to an SSL policy resource that defines the server-side support for SSL features and affects the connections between clients and load balancers that are using the SSL proxy. The SSL policy must exist and cannot be deleted while referenced by a target SSL proxy. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-ssl-proxies/create)

---
### `gcloud compute target-ssl-proxies delete`

Delete target SSL proxies

gcloud compute target-ssl-proxies delete deletes one or more target SSL
proxies.

**Synopsis:**
```
gcloud compute target-ssl-proxies delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target SSL proxies to delete.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-ssl-proxies/delete)

---
### `gcloud compute target-ssl-proxies describe`

Display detailed information about a target SSL proxy

gcloud compute target-ssl-proxies describe displays all data associated
with a target SSL proxy in a project.

**Synopsis:**
```
gcloud compute target-ssl-proxies describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target SSL proxy to describe.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-ssl-proxies/describe)

---
### `gcloud compute target-ssl-proxies list`

List Google Compute Engine target SSL proxies

gcloud compute target-ssl-proxies list displays all Google Compute Engine
target SSL proxies in a project.

**Synopsis:**
```
gcloud compute target-ssl-proxies list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all target SSL proxies in a project in table form, run:

    $ gcloud compute target-ssl-proxies list

To list the URIs of all target SSL proxies in a project, run:

    $ gcloud compute target-ssl-proxies list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-ssl-proxies/list)

---
### `gcloud compute target-ssl-proxies update`

Update a target SSL proxy

gcloud compute target-ssl-proxies update is used to replace the SSL
certificate, backend service, proxy header or SSL policy of existing target
SSL proxies. A target SSL proxy is referenced by one or more forwarding
rules which define which packets the proxy is responsible for routing. The
target SSL proxy in turn points to a backend service which will handle the
requests. The target SSL proxy also points to at most 15 SSL certificates
used for server-side authentication or one certificate map. The target SSL
proxy can be associated with at most one SSL policy.

**Synopsis:**
```
gcloud compute target-ssl-proxies update NAME
    [--backend-service=BACKEND_SERVICE] [--proxy-header=PROXY_HEADER]
    [--clear-ssl-policy | --ssl-policy=SSL_POLICY --global-ssl-policy
      | --ssl-policy-region=SSL_POLICY_REGION]
    [--ssl-certificates=SSL_CERTIFICATE,[...] | --clear-ssl-certificates
      | --certificate-map=CERTIFICATE_MAP | --clear-certificate-map]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target SSL proxy to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-service` | BACKEND_SERVICE |  | A backend service that will be used for connections to the target SSL proxy. |
| `--proxy-header` | one of: NONE No proxy header is added |  | The type of proxy protocol header to be sent to the backend. PROXY_HEADER must be one of: NONE No proxy header is added. PROXY_V1 Enables PROXY protocol (version 1) for passing client connection information. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-ssl-proxies/update)

---