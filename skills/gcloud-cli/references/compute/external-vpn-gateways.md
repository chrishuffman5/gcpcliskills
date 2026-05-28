# gcloud compute external-vpn-gateways

list, create, delete and update External VPN Gateways

### `gcloud compute external-vpn-gateways create`

Create a new Compute Engine external VPN gateway

gcloud compute external-vpn-gateways create creates a new external VPN
gateway.

External VPN gateway is the on-premises VPN gateway or another cloud
provider's VPN gateway that connects to your Google Cloud VPN gateway. To
create a highly available VPN from Google Cloud to your on-premises side or
another Cloud provider's VPN gateway, you must create an external VPN
gateway resource in Google Cloud, which provides the information to Google
Cloud about your external VPN gateway.

**Synopsis:**
```
gcloud compute external-vpn-gateways create NAME
    --interfaces=[ID=IP_ADDRESS,...] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the external VPN gateway to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--interfaces` | [ID=IP_ADDRESS,...] |  | Map of interfaces from interface ID to interface IP address for the External VPN Gateway. There can be one, two, or four interfaces in the map. For example, to create an external VPN gateway with one interface: $ gcloud compute external-vpn-gateways create MY-EXTERNAL-GATEWAY \ --interfaces 0=192.0.2.0 To create an external VPN gateway with two interfaces: $ gcloud compute external-vpn-gateways create MY-EXTERNAL-GATEWAY \ --interfaces 0=192.0.2.0,1=192.0.2.1 To create an external VPN gateway with four interfaces: $ gcloud compute external-vpn-gateways create MY-EXTERNAL-GATEWAY \ --interfaces 0=192.0.2.0,1=192.0.2.1,2=192.0.2.3,3=192.0.2.4 To create an external VPN gateway with IPv6 addresses on four interfaces: $ gcloud compute external-vpn-gateways create MY-EXTERNAL-GATEWAY \ --interfaces \ 0=2001:db8::1,1=2001:db8::2,2=2001:db8::3,3=2001:db8::4 Note that the redundancy type of the gateway will be automatically inferred based on the number of interfaces provided: 1 interface: `SINGLE_IP_INTERNALLY_REDUNDANT` 2 interfaces: `TWO_IPS_REDUNDANCY` 4 interfaces: `FOUR_IPS_REDUNDANCY` |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Textual description of the External VPN Gateway. |


**Examples:**
```bash
To create an external VPN gateway, run:

    $ gcloud compute external-vpn-gateways create my-external-gateway \
      --interfaces=0=8.9.9.9
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/external-vpn-gateways/create)

---
### `gcloud compute external-vpn-gateways delete`

Delete a Compute Engine external VPN gateway

gcloud compute external-vpn-gateways delete is used to delete all data
associated with a Compute Engine external VPN gateway in a project.

An external VPN gateway provides the information to Google Cloud about your
on-premises side or another Cloud provider's VPN gateway.

**Synopsis:**
```
gcloud compute external-vpn-gateways delete NAME [NAME ...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the external VPN gateways to delete.
```

**Examples:**
```bash
To delete an external VPN gateway, run:

    $ gcloud compute external-vpn-gateways delete my-external-gateway
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/external-vpn-gateways/delete)

---
### `gcloud compute external-vpn-gateways describe`

Describe a Compute Engine external VPN gateway

gcloud compute external-vpn-gateways describe is used to display all data
associated with a Compute Engine external VPN gateway in a project.

An external VPN gateway provides the information to Google Cloud about your
on-premises side or another Cloud provider's VPN gateway.

**Synopsis:**
```
gcloud compute external-vpn-gateways describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the external VPN gateway to describe.
```

**Examples:**
```bash
To describe an external VPN gateway, run:

    $ gcloud compute external-vpn-gateways describe my-external-gateway
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/external-vpn-gateways/describe)

---
### `gcloud compute external-vpn-gateways list`

List Google Compute Engine external VPN gateways

gcloud compute external-vpn-gateways list displays all Google Compute
Engine external VPN gateways in a project.

**Synopsis:**
```
gcloud compute external-vpn-gateways list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all external VPN gateways in a project in table form, run:

    $ gcloud compute external-vpn-gateways list

To list the URIs of all external VPN gateways in a project, run:

    $ gcloud compute external-vpn-gateways list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/external-vpn-gateways/list)

---
### `gcloud compute external-vpn-gateways update`

Update a Compute Engine external VPN gateway

gcloud compute external-vpn-gateways update updates labels for a Compute
Engine external VPN gateway. For example:

    $ gcloud compute external-vpn-gateways update example-gateway \
      --update-labels=k0=value1,k1=value2 --remove-labels=k3

will add/update labels k0 and k1 and remove labels with key k3.

Labels can be used to identify the External VPN gateway and to filter them
as in

    $ gcloud compute external-vpn-gateways list \
        --filter='labels.k1:value2'

To list existing labels

    $ gcloud compute external-vpn-gateways describe example-gateway \
        --format="default(labels)"

**Synopsis:**
```
gcloud compute external-vpn-gateways update NAME
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the external VPN gateway to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update labels for an external VPN gateway, run:

    $ gcloud compute external-vpn-gateways update my-external-gateway \
      --update-labels=k0=value1,k1=value2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/external-vpn-gateways/update)

---