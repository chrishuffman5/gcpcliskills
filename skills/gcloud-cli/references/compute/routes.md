# gcloud compute routes

read and manipulate routes

### `gcloud compute routes create`

Create a new route

gcloud compute routes create is used to create routes. A route is a rule
that specifies how certain packets should be handled by the virtual
network. Routes are associated with virtual machine instances by tag, and
the set of routes for a particular VM is called its routing table. For each
packet leaving a virtual machine, the system searches that machine's
routing table for a single best matching route.

Routes match packets by destination IP address, preferring smaller or more
specific ranges over larger ones (see --destination-range). If there is a
tie, the system selects the route with the smallest priority value. The
packet is then forwarded as specified by --next-hop-address,
--next-hop-instance, --next-hop-vpn-tunnel, or --next-hop-gateway of the
winning route. Packets that do not match any route in the sending virtual
machine routing table will be dropped.

Exactly one of --next-hop-address, --next-hop-gateway,
--next-hop-vpn-tunnel, or --next-hop-instance must be provided with this
command.

**Synopsis:**
```
gcloud compute routes create NAME --destination-range=DESTINATION_RANGE
    (--next-hop-address=NEXT_HOP_ADDRESS
      | --next-hop-gateway=NEXT_HOP_GATEWAY | --next-hop-ilb=NEXT_HOP_ILB
      | --next-hop-instance=NEXT_HOP_INSTANCE
      | --next-hop-vpn-tunnel=NEXT_HOP_VPN_TUNNEL)
    [--description=DESCRIPTION] [--network=NETWORK; default="default"]
    [--next-hop-ilb-region=NEXT_HOP_ILB_REGION]
    [--next-hop-instance-zone=NEXT_HOP_INSTANCE_ZONE]
    [--next-hop-vpn-tunnel-region=NEXT_HOP_VPN_TUNNEL_REGION]
    [--priority=PRIORITY; default=1000]
    [--resource-manager-tags=[KEY=VALUE,...]] [--tags=TAG,[TAG,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the route to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-range` | DESTINATION_RANGE |  | The destination range of outgoing packets that the route will apply to. To match all traffic, use ``0.0.0.0/0''. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description for the route. |
| `--network` | NETWORK | default | Specifies the network to which the route will be applied. |
| `--next-hop-ilb-region` | NEXT_HOP_ILB_REGION |  | The region of the next hop forwarding rule. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--next-hop-instance-zone` | NEXT_HOP_INSTANCE_ZONE |  | The zone of the next hop instance. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--next-hop-vpn-tunnel-region` | NEXT_HOP_VPN_TUNNEL_REGION |  | The region of the next hop vpn tunnel. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--priority` | PRIORITY | 1000 | Specifies the priority of this route relative to other routes with the same specificity. The lower the value, the higher the priority. |
| `--resource-manager-tags` | [KEY=VALUE,...] |  | A comma-separated list of Resource Manager tags to apply to the route. |
| `--tags` | TAG,[TAG,...] |  | Identifies the set of instances that this route will apply to. If no tags are provided, the route will apply to all instances in the network. |


**Examples:**
```bash
To create a route with the name 'route-name' with destination range
'0.0.0.0/0' and with next hop gateway 'default-internet-gateway', run:

    $ gcloud compute routes create route-name \
        --destination-range=0.0.0.0/0 \
        --next-hop-gateway=default-internet-gateway
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routes/create)

---
### `gcloud compute routes delete`

Delete routes

gcloud compute routes delete deletes one or more Compute Engine routes.

**Synopsis:**
```
gcloud compute routes delete NAME [NAME ...] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the routes to delete.
```

**Examples:**
```bash
To delete a route with the name 'route-name', run:

    $ gcloud compute routes delete route-name

To delete two routes with the names 'route-name1' and 'route-name2', run:

    $ gcloud compute routes delete route-name1 route-name2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routes/delete)

---
### `gcloud compute routes describe`

Describe a route

gcloud compute routes describe displays all data associated with a Compute
Engine route in a project.

**Synopsis:**
```
gcloud compute routes describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the route to describe.
```

**Examples:**
```bash
To describe a route with the name 'route-name', run:

    $ gcloud compute routes describe route-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routes/describe)

---
### `gcloud compute routes list`

List non-dynamic Google Compute Engine routes

gcloud compute routes list displays all custom static, subnet, and peering
routes in VPC networks in a project.

To list custom dynamic routes learned by Cloud Routers, query the status of
the Cloud Router that learned the route using gcloud compute routers
get-status. For more details, refer to
https://cloud.google.com/vpc/docs/using-routes#listingroutes.

**Synopsis:**
```
gcloud compute routes list [NAME ...] [--regexp=REGEXP, -r REGEXP]
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
To list all non-dynamic routes in a project in table form, run:

    $ gcloud compute routes list

To list the URIs of all non-dynamic routes in a project, run:

    $ gcloud compute routes list --uri
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/routes/list)

---