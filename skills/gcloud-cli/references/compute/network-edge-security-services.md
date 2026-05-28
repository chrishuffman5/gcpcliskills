# gcloud compute network-edge-security-services

read and manipulate network edge security services

### `gcloud compute network-edge-security-services create`

Create a Compute Engine network edge security service

gcloud compute network-edge-security-services create is used to create
network edge security services.

**Synopsis:**
```
gcloud compute network-edge-security-services create NAME
    [--description=DESCRIPTION] [--region=REGION]
    [--security-policy=SECURITY_POLICY]
    [--security-policy-region=SECURITY_POLICY_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network edge security service to create.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the network edge security service. |
| `--region` | REGION |  | Region of the network edge security service to create. Overrides the default compute/region property value for this command invocation. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that will be set for this network edge security service. To remove the policy from this network edge security service set the policy to an empty string. |
| `--security-policy-region` | SECURITY_POLICY_REGION |  | Region of the security policy to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To create a network edge security service with the name 'my-service' in
region 'us-central1', run:

    $ gcloud compute network-edge-security-services create my-service \
        --region=us-central1

To create a network edge security service with the name 'my-service' with
security policy 'my-policy' attached in region 'us-central1', run:

    $ gcloud compute network-edge-security-services create my-service \
        --security-policy=my-policy --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-edge-security-services/create)

---
### `gcloud compute network-edge-security-services delete`

Delete network edge security services

gcloud compute network-edge-security-services delete deletes Compute Engine
network edge security services.

**Synopsis:**
```
gcloud compute network-edge-security-services delete NAME [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network edge security service to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the network edge security service to delete. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To delete a network edge security service with the name 'my-service' in
region 'us-central1', run:

    $ gcloud compute network-edge-security-services delete my-service \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-edge-security-services/delete)

---
### `gcloud compute network-edge-security-services describe`

Describe a Compute Engine network edge security service

gcloud compute network-edge-security-services describe displays all data
associated with a Compute Engine network edge security service in a
project.

**Synopsis:**
```
gcloud compute network-edge-security-services describe NAME
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network edge security service to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region of the network edge security service to describe. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To describe a network edge security service with the name 'my-service' in
region 'us-central1', run:

    $ gcloud compute network-edge-security-services describe \
        my-service --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-edge-security-services/describe)

---
### `gcloud compute network-edge-security-services list`

List Google Compute Engine network edge security services

gcloud compute network-edge-security-services list displays all Google
Compute Engine network edge security services in a project.

By default, network edge security services from all regions are listed. The
results can be narrowed down using a filter: --filter="region:( REGION ...
)".

**Synopsis:**
```
gcloud compute network-edge-security-services list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all network edge security services in a project in table form, run:

    $ gcloud compute network-edge-security-services list

To list the URIs of all network edge security services in a project, run:

    $ gcloud compute network-edge-security-services list --uri

To list all network edge security services in the us-central1 and
europe-west1 regions, run:

    $ gcloud compute network-edge-security-services list \
        --filter="region:( us-central1 europe-west1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-edge-security-services/list)

---
### `gcloud compute network-edge-security-services update`

Update a network edge security service

gcloud compute network-edge-security-services update is used to update
network edge security services.

**Synopsis:**
```
gcloud compute network-edge-security-services update NAME
    [--description=DESCRIPTION] [--region=REGION]
    [--security-policy=SECURITY_POLICY]
    [--security-policy-region=SECURITY_POLICY_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the network edge security service to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the network edge security service. |
| `--region` | REGION |  | Region of the network edge security service to update. Overrides the default compute/region property value for this command invocation. |
| `--security-policy` | SECURITY_POLICY |  | The security policy that will be set for this network edge security service. To remove the policy from this network edge security service set the policy to an empty string. |
| `--security-policy-region` | SECURITY_POLICY_REGION |  | Region of the security policy to operate on. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To attach a new security policy 'my-policy' to a network edge security
service with the name 'my-service' in region 'us-central1', run:

    $ gcloud compute network-edge-security-services update my-service \
        --security-policy=my-policy --region=us-central1

To remove the security policy attached to a network edge security service
with the name 'my-service' in region 'us-central1', run:

    $ gcloud compute network-edge-security-services update my-service \
        --security-policy="" --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-edge-security-services/update)

---