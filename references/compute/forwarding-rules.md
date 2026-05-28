# gcloud compute forwarding-rules

read and manipulate traffic forwarding rules to network load balancers

### `gcloud compute forwarding-rules create`

Create a forwarding rule to direct network traffic to a load balancer

gcloud compute forwarding-rules create is used to create a forwarding rule.
A forwarding rule directs traffic that matches a destination IP address
(and possibly a TCP or UDP port) to a forwarding target (load balancer, VPN
gateway or VM instance).

Forwarding rules can be either global or regional, specified with the
--global or --region=REGION flags. For more information about the scope of
a forwarding rule, refer to
https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts.

Forwarding rules can be external, internal, internal managed, or internal
self-managed, specified with the
--load-balancing-scheme=[EXTERNAL|EXTERNAL_MANAGED|INTERNAL|INTERNAL_MANAGED|INTERNAL_SELF_MANAGED]
flag. External forwarding rules are accessible from the internet, while
internal forwarding rules are only accessible from within their VPC
networks. You can specify a reserved static external or internal IP address
with the --address=ADDRESS flag for the forwarding rule. Otherwise, if the
flag is unspecified, an ephemeral IP address is automatically assigned
(global IP addresses for global forwarding rules and regional IP addresses
for regional forwarding rules); an internal forwarding rule is
automatically assigned an ephemeral internal IP address from the subnet
specified with the --subnet flag. You must provide an IP address for an
internal self-managed forwarding rule.

Different types of load balancers work at different layers of the OSI
networking model (http://en.wikipedia.org/wiki/Network_layer). Layer 3/4
targets include target pools, target SSL proxies, target TCP proxies, and
backend services. Layer 7 targets include target HTTP proxies and target
HTTPS proxies. For more information, refer to
https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts.

When creating a forwarding rule, exactly one of --target-instance,
--target-pool, --target-http-proxy, --target-https-proxy,
--target-grpc-proxy, --target-ssl-proxy, --target-tcp-proxy,
--target-vpn-gateway, --backend-service or --target-google-apis-bundle must
be specified.

**Synopsis:**
```
gcloud compute forwarding-rules create NAME
    (--backend-service=BACKEND_SERVICE
      | --target-google-apis-bundle=TARGET_GOOGLE_APIS_BUNDLE
      | --target-grpc-proxy=TARGET_GRPC_PROXY
      | --target-http-proxy=TARGET_HTTP_PROXY
      | --target-https-proxy=TARGET_HTTPS_PROXY
      | --target-instance=TARGET_INSTANCE | --target-pool=TARGET_POOL
      | --target-service-attachment=TARGET_SERVICE_ATTACHMENT
      | --target-ssl-proxy=TARGET_SSL_PROXY
      | --target-tcp-proxy=TARGET_TCP_PROXY
      | --target-vpn-gateway=TARGET_VPN_GATEWAY) [--address=ADDRESS]
    [--allow-global-access] [--allow-psc-global-access]
    [--description=DESCRIPTION] [--disable-automate-dns-zone]
    [--ip-collection=IP_COLLECTION]
    [--ip-collection-region=IP_COLLECTION_REGION]
    [--ip-protocol=IP_PROTOCOL] [--ip-version=IP_VERSION]
    [--is-mirroring-collector]
    [--load-balancing-scheme=LOAD_BALANCING_SCHEME] [--network=NETWORK]
    [--network-tier=NETWORK_TIER]
    [--service-directory-registration=SERVICE_DIRECTORY_REGISTRATION]
    [--service-label=SERVICE_LABEL]
    [--source-ip-ranges=SOURCE_IP_RANGE,[...]] [--subnet=SUBNET]
    [--subnet-region=SUBNET_REGION]
    [--target-instance-zone=TARGET_INSTANCE_ZONE]
    [--target-pool-region=TARGET_POOL_REGION]
    [--target-service-attachment-region=TARGET_SERVICE_ATTACHMENT_REGION]
    [--target-vpn-gateway-region=TARGET_VPN_GATEWAY_REGION]
    [--address-region=ADDRESS_REGION | --global-address]
    [--backend-service-region=BACKEND_SERVICE_REGION
      | --global-backend-service] [--global | --region=REGION]
    [--global-target-http-proxy
      | --target-http-proxy-region=TARGET_HTTP_PROXY_REGION]
    [--global-target-https-proxy
      | --target-https-proxy-region=TARGET_HTTPS_PROXY_REGION]
    [--global-target-tcp-proxy
      | --target-tcp-proxy-region=TARGET_TCP_PROXY_REGION]
    [--port-range=[PORT | START_PORT-END_PORT] | --ports=ALL | [PORT
      | START_PORT-END_PORT],[...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the forwarding rule to create.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-service` | BACKEND_SERVICE |  | _[Exactly one of these must be specified:]_ Target backend service that receives the traffic. |
| `--target-google-apis-bundle` | TARGET_GOOGLE_APIS_BUNDLE |  | _[Exactly one of these must be specified:]_ Target bundle of Google APIs that will receive forwarded traffic via Private Service Connect. Acceptable values are all-apis, meaning all Google APIs, or vpc-sc, meaning just the APIs that support VPC Service Controls |
| `--target-grpc-proxy` | TARGET_GRPC_PROXY |  | _[Exactly one of these must be specified:]_ Target gRPC proxy that receives the traffic. |
| `--target-http-proxy` | TARGET_HTTP_PROXY |  | _[Exactly one of these must be specified:]_ Target HTTP proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-https-proxy` | TARGET_HTTPS_PROXY |  | _[Exactly one of these must be specified:]_ Target HTTPS proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-instance` | TARGET_INSTANCE |  | _[Exactly one of these must be specified:]_ Name of the target instance that receives the traffic. The target instance must be in a zone in the forwarding rule's region. Global forwarding rules cannot direct traffic to target instances. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--target-pool` | TARGET_POOL |  | _[Exactly one of these must be specified:]_ Target pool that receives the traffic. The target pool must be in the same region as the forwarding rule. Global forwarding rules cannot direct traffic to target pools. |
| `--target-service-attachment` | TARGET_SERVICE_ATTACHMENT |  | _[Exactly one of these must be specified:]_ Target service attachment that receives the traffic. The target service attachment must be in the same region as the forwarding rule. |
| `--target-ssl-proxy` | TARGET_SSL_PROXY |  | _[Exactly one of these must be specified:]_ Target SSL proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-tcp-proxy` | TARGET_TCP_PROXY |  | _[Exactly one of these must be specified:]_ Target TCP proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-vpn-gateway` | TARGET_VPN_GATEWAY |  | _[Exactly one of these must be specified:]_ Target VPN gateway (Cloud VPN Classic gateway) that receives forwarded traffic. Acceptable values for --ports flag are: 500, 4500. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--address` | ADDRESS |  | The IP address that the forwarding rule serves. When a client sends traffic to this IP address, the forwarding rule directs the traffic to the target that you specify in the forwarding rule. If you don't specify a reserved IP address, an ephemeral IP address is assigned. You can specify the IP address as a literal IP address or as a reference to an existing Address resource. The following examples are all valid: * 100.1.2.3 * 2600:1901::/96 * https://compute.googleapis.com/compute/v1/projects/project-1/regions/us-central1/addresses/address-1 * projects/project-1/regions/us-central1/addresses/address-1 * regions/us-central1/addresses/address-1 * global/addresses/address-1 * address-1 The load-balancing-scheme (EXTERNAL, EXTERNAL_MANAGED, INTERNAL, INTERNAL_SELF_MANAGED, INTERNAL_MANAGED) and the target of the forwarding rule determine the type of IP address that you can use. The address type must be external for load-balancing-scheme EXTERNAL or EXTERNAL_MANAGED. For other load-balancing-schemes, the address type must be internal. For detailed information, refer to https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#ip_address_specifications. |
| `--allow-global-access` |  |  | If True, then clients from all regions can access this internal forwarding rule. This can only be specified for forwarding rules with the LOAD_BALANCING_SCHEME set to INTERNAL or INTERNAL_MANAGED. For forwarding rules of type INTERNAL, the target must be either a backend service or a target instance. |
| `--allow-psc-global-access` |  |  | If specified, clients from all regions can access this Private Service Connect forwarding rule. This can only be specified if the forwarding rule's target is a service attachment (--target-service-attachment). |
| `--description` | DESCRIPTION |  | Optional textual description for the forwarding rule. |
| `--disable-automate-dns-zone` |  |  | If specified, then a DNS zone will not be auto-generated for this Private Service Connect forwarding rule. This can only be specified if the forwarding rule's target is a service attachment (--target-service-attachment=SERVICE_ATTACHMENT) or Google APIs bundle (--target-google-apis-bundle=API_BUNDLE) |
| `--ip-collection` | IP_COLLECTION |  | Resource reference to a public delegated prefix. The PublicDelegatedPrefix (PDP) must be a sub-prefix in EXTERNAL_IPV6_FORWARDING_RULE_CREATION mode. |
| `--ip-collection-region` | IP_COLLECTION_REGION |  | Region of the public delegated prefix to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. |
| `--ip-protocol` | one of: TCP, UDP, L3_DEFAULT |  | IP protocol that the rule will serve. The default is TCP. Note that if the load-balancing scheme is INTERNAL, the protocol must be one of: TCP, UDP, L3_DEFAULT. For a load-balancing scheme that is EXTERNAL, all IP_PROTOCOL options are valid. IP_PROTOCOL must be one of: AH, ESP, ICMP, SCTP, TCP, UDP, L3_DEFAULT. |
| `--ip-version` | one of: IPV4, IPV6 |  | Version of the IP address to be allocated or assigned. The default is IPv4. IP_VERSION must be one of: IPV4, IPV6. |
| `--is-mirroring-collector` |  |  | If set, this forwarding rule can be used as a collector for packet mirroring. This can only be specified for forwarding rules with the LOAD_BALANCING_SCHEME set to INTERNAL. |
| `--load-balancing-scheme` | one of: EXTERNAL Classic Application Load Balancers, global external proxy Network Load Balancers, external passthrough Network Load Balancers or protocol forwarding, used with one of --target-http-proxy, --target-https-proxy, --target-tcp-proxy, --target-ssl-proxy, --target-pool, --target-vpn-gateway, --target-instance |  | This defines the forwarding rule's load balancing scheme. Note that it defaults to EXTERNAL and is not applicable for Private Service Connect forwarding rules. LOAD_BALANCING_SCHEME must be one of: EXTERNAL Classic Application Load Balancers, global external proxy Network Load Balancers, external passthrough Network Load Balancers or protocol forwarding, used with one of --target-http-proxy, --target-https-proxy, --target-tcp-proxy, --target-ssl-proxy, --target-pool, --target-vpn-gateway, --target-instance. EXTERNAL_MANAGED Global and regional external Application Load Balancers, and regional external proxy Network Load Balancers, used with --target-http-proxy, --target-https-proxy, --target-tcp-proxy. INTERNAL Internal passthrough Network Load Balancers or protocol forwarding, used with --backend-service. INTERNAL_MANAGED Internal Application Load Balancers and internal proxy Network Load Balancers, used with --target-http-proxy, --target-https-proxy, --target-tcp-proxy. INTERNAL_SELF_MANAGED Traffic Director, used with --target-http-proxy, --target-https-proxy, --target-grpc-proxy, --target-tcp-proxy. |
| `--network` | NETWORK |  | (Only for --load-balancing-scheme=INTERNAL or --load-balancing-scheme=INTERNAL_SELF_MANAGED or --load-balancing-scheme=EXTERNAL_MANAGED (regional) or --load-balancing-scheme=INTERNAL_MANAGED) Network that this forwarding rule applies to. If this field is not specified, the default network is used. In the absence of the default network, this field must be specified. |
| `--network-tier` | one of: PREMIUM, STANDARD |  | Network tier to assign to the forwarding rules. NETWORK_TIER must be one of: PREMIUM, STANDARD. The default value is PREMIUM. |
| `--service-directory-registration` | SERVICE_DIRECTORY_REGISTRATION |  | The Service Directory service in which to register this forwarding rule as an endpoint. The Service Directory service must be in the same project and region as the forwarding rule you are creating. |
| `--service-label` | SERVICE_LABEL |  | (Only for Internal Load Balancing): https://cloud.google.com/load-balancing/docs/dns-names/ The DNS label to use as the prefix of the fully qualified domain name for this forwarding rule. The full name will be internally generated and output as dnsName. If this field is not specified, no DNS record will be generated and no DNS name will be output. You cannot use the --service-label flag if the forwarding rule references an internal IP address that has the --purpose=SHARED_LOADBALANCER_VIP flag set. |
| `--source-ip-ranges` | SOURCE_IP_RANGE,[...] |  | List of comma-separated IP addresses or IP ranges. If set, this forwarding rule only forwards traffic when the packet's source IP address matches one of the IP ranges set here. |
| `--subnet` | SUBNET |  | (Only for --load-balancing-scheme=INTERNAL and --load-balancing-scheme=INTERNAL_MANAGED) Subnetwork that this forwarding rule applies to. If the network is auto mode, this flag is optional. If the network is custom mode, this flag is required. |
| `--subnet-region` | SUBNET_REGION |  | Region of the subnetwork to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. |
| `--target-instance-zone` | TARGET_INSTANCE_ZONE |  | Zone of the target instance to operate on. Overrides the default compute/zone property value for this command invocation. |
| `--target-pool-region` | TARGET_POOL_REGION |  | Region of the target pool to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. |
| `--target-service-attachment-region` | TARGET_SERVICE_ATTACHMENT_REGION |  | Region of the target service attachment to operate on. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |
| `--target-vpn-gateway-region` | TARGET_VPN_GATEWAY_REGION |  | Region of the VPN gateway to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. |


**Examples:**
```bash
To create a global forwarding rule that will forward all traffic on port
8080 for IP address ADDRESS to a target http proxy PROXY, run:

    $ gcloud compute forwarding-rules create RULE_NAME --global \
        --target-http-proxy=PROXY --ports=8080 --address=ADDRESS

To create a regional forwarding rule for the subnet SUBNET_NAME on the
default network that will forward all traffic on ports 80-82 to a backend
service SERVICE_NAME, run:

    $ gcloud compute forwarding-rules create RULE_NAME \
        --load-balancing-scheme=INTERNAL \
        --backend-service=SERVICE_NAME --subnet=SUBNET_NAME \
        --network=default --region=REGION --ports=80-82
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/create)

---
### `gcloud compute forwarding-rules delete`

Delete forwarding rules

gcloud compute forwarding-rules delete deletes one or more Compute Engine
forwarding rules.

**Synopsis:**
```
gcloud compute forwarding-rules delete NAME [NAME ...]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the forwarding rules to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the forwarding rules are global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the forwarding rules to delete. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/delete)

---
### `gcloud compute forwarding-rules describe`

Display detailed information about a forwarding rule

gcloud compute forwarding-rules describe displays all data associated with
a forwarding rule in a project.

**Synopsis:**
```
gcloud compute forwarding-rules describe NAME [--global | --region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the forwarding rule to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--global` |  |  | _[At most one of these can be specified:]_ If set, the forwarding rule is global. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Region of the forwarding rule to describe. If not specified, you might be prompted to select a region (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/region property: $ gcloud config set compute/region REGION A list of regions can be fetched by running: $ gcloud compute regions list To unset the property, run: $ gcloud config unset compute/region Alternatively, the region can be stored in the environment variable CLOUDSDK_COMPUTE_REGION. |


**Examples:**
```bash
To get details about a global forwarding rule, run:

    $ gcloud compute forwarding-rules describe FORWARDING-RULE --global

To get details about a regional forwarding rule, run:

    $ gcloud compute forwarding-rules describe FORWARDING-RULE \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/describe)

---
### `gcloud compute forwarding-rules export`

Export a forwarding rule

Exports a forwarding rule's configuration to a file.

**Synopsis:**
```
gcloud compute forwarding-rules export NAME [--destination=DESTINATION]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the forwarding rule to export.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\ForwardingRule.yaml. |


**Examples:**
```bash
A forwarding rule can be exported by running:

    $ gcloud compute forwarding-rules export NAME \
        --destination=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/export)

---
### `gcloud compute forwarding-rules import`

Import a forwarding rule

Imports a forwarding rule's configuration from a file.

**Synopsis:**
```
gcloud compute forwarding-rules import NAME [--source=SOURCE]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the forwarding rule to import.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Path to a YAML file containing configuration export data. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT\lib\googlecloudsdk\schemas\compute\v1\ForwardingRule.yaml. Note: $CLOUDSDKROOT represents the Google Cloud CLI's installation directory. |


**Examples:**
```bash
Import a forwarding rule by running:

    $ gcloud compute forwarding-rules import NAME --source=<path-to-file>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/import)

---
### `gcloud compute forwarding-rules list`

List Google Compute Engine forwarding rules

gcloud compute forwarding-rules list displays all Google Compute Engine
forwarding rules in a project.

By default, global forwarding rules and forwarding rules from all regions
are listed. The results can be narrowed down by providing the --global or
--regions flag.

**Synopsis:**
```
gcloud compute forwarding-rules list [NAME ...]
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
To list all forwarding rules in a project in table form, run:

    $ gcloud compute forwarding-rules list

To list the URIs of all forwarding rules in a project, run:

    $ gcloud compute forwarding-rules list --uri

To list all global forwarding rules in a project, run:

    $ gcloud compute forwarding-rules list --global

To list all forwarding rules in the us-central1 and europe-west1 regions,
given they are regional resources, run:

    $ gcloud compute forwarding-rules list \
        --filter="region:( europe-west1 us-central1 )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/list)

---
### `gcloud compute forwarding-rules set-target`

Modify a forwarding rule to direct network traffic to a new target

gcloud compute forwarding-rules set-target is used to set a new target for
a forwarding rule. A forwarding rule directs traffic that matches a
destination IP address (and possibly a TCP or UDP port) to a forwarding
target (load balancer, VPN gateway or VM instance).

Forwarding rules can be either global or regional, specified with the
--global or --region=REGION flags. For more information about the scope of
a forwarding rule, refer to
https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts.

Forwarding rules can be external, internal, internal managed, or internal
self-managed, specified with the
--load-balancing-scheme=[EXTERNAL|EXTERNAL_MANAGED|INTERNAL|INTERNAL_MANAGED|INTERNAL_SELF_MANAGED]
flag. External forwarding rules are accessible from the internet, while
internal forwarding rules are only accessible from within their VPC
networks. You can specify a reserved static external or internal IP address
with the --address=ADDRESS flag for the forwarding rule. Otherwise, if the
flag is unspecified, an ephemeral IP address is automatically assigned
(global IP addresses for global forwarding rules and regional IP addresses
for regional forwarding rules); an internal forwarding rule is
automatically assigned an ephemeral internal IP address from the subnet
specified with the --subnet flag. You must provide an IP address for an
internal self-managed forwarding rule.

Different types of load balancers work at different layers of the OSI
networking model (http://en.wikipedia.org/wiki/Network_layer). Layer 3/4
targets include target pools, target SSL proxies, target TCP proxies, and
backend services. Layer 7 targets include target HTTP proxies and target
HTTPS proxies. For more information, refer to
https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts.

    When creating a forwarding rule, exactly one of  `_--target-instance_`,
    `_--target-pool_`, `_--target-http-proxy_`, `_--target-https-proxy_`,
    `_--target-grpc-proxy_`, `_--target-ssl-proxy_`,
    `_--target-tcp-proxy_` or `_--target-vpn-gateway_`
    must be specified.

**Synopsis:**
```
gcloud compute forwarding-rules set-target NAME
    (--backend-service=BACKEND_SERVICE
      | --target-grpc-proxy=TARGET_GRPC_PROXY
      | --target-http-proxy=TARGET_HTTP_PROXY
      | --target-https-proxy=TARGET_HTTPS_PROXY
      | --target-instance=TARGET_INSTANCE | --target-pool=TARGET_POOL
      | --target-ssl-proxy=TARGET_SSL_PROXY
      | --target-tcp-proxy=TARGET_TCP_PROXY
      | --target-vpn-gateway=TARGET_VPN_GATEWAY)
    [--load-balancing-scheme=LOAD_BALANCING_SCHEME; default="EXTERNAL"]
    [--network=NETWORK] [--subnet=SUBNET] [--subnet-region=SUBNET_REGION]
    [--target-instance-zone=TARGET_INSTANCE_ZONE]
    [--target-pool-region=TARGET_POOL_REGION]
    [--target-vpn-gateway-region=TARGET_VPN_GATEWAY_REGION]
    [--backend-service-region=BACKEND_SERVICE_REGION
      | --global-backend-service] [--global | --region=REGION]
    [--global-target-http-proxy
      | --target-http-proxy-region=TARGET_HTTP_PROXY_REGION]
    [--global-target-https-proxy
      | --target-https-proxy-region=TARGET_HTTPS_PROXY_REGION]
    [--global-target-tcp-proxy
      | --target-tcp-proxy-region=TARGET_TCP_PROXY_REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the forwarding rule to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--backend-service` | BACKEND_SERVICE |  | _[Exactly one of these must be specified:]_ Target backend service that receives the traffic. |
| `--target-grpc-proxy` | TARGET_GRPC_PROXY |  | _[Exactly one of these must be specified:]_ Target gRPC proxy that receives the traffic. |
| `--target-http-proxy` | TARGET_HTTP_PROXY |  | _[Exactly one of these must be specified:]_ Target HTTP proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-https-proxy` | TARGET_HTTPS_PROXY |  | _[Exactly one of these must be specified:]_ Target HTTPS proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-instance` | TARGET_INSTANCE |  | _[Exactly one of these must be specified:]_ Name of the target instance that receives the traffic. The target instance must be in a zone in the forwarding rule's region. Global forwarding rules cannot direct traffic to target instances. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |
| `--target-pool` | TARGET_POOL |  | _[Exactly one of these must be specified:]_ Target pool that receives the traffic. The target pool must be in the same region as the forwarding rule. Global forwarding rules cannot direct traffic to target pools. |
| `--target-ssl-proxy` | TARGET_SSL_PROXY |  | _[Exactly one of these must be specified:]_ Target SSL proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-tcp-proxy` | TARGET_TCP_PROXY |  | _[Exactly one of these must be specified:]_ Target TCP proxy that receives the traffic. For the acceptable ports, see Port specifications (https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts#port_specifications). |
| `--target-vpn-gateway` | TARGET_VPN_GATEWAY |  | _[Exactly one of these must be specified:]_ Target VPN gateway (Cloud VPN Classic gateway) that receives forwarded traffic. Acceptable values for --ports flag are: 500, 4500. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--load-balancing-scheme` | one of: EXTERNAL Classic Application Load Balancers, global external proxy Network Load Balancers, external passthrough Network Load Balancers or protocol forwarding, used with one of --target-http-proxy, --target-https-proxy, --target-tcp-proxy, --target-ssl-proxy, --target-pool, --target-vpn-gateway, --target-instance | EXTERNAL | (DEPRECATED) This defines the forwarding rule's load balancing scheme. The --load-balancing-scheme option is deprecated and will be removed in an upcoming release. If you're currently using this argument, you should remove it from your workflows. LOAD_BALANCING_SCHEME must be one of: EXTERNAL Classic Application Load Balancers, global external proxy Network Load Balancers, external passthrough Network Load Balancers or protocol forwarding, used with one of --target-http-proxy, --target-https-proxy, --target-tcp-proxy, --target-ssl-proxy, --target-pool, --target-vpn-gateway, --target-instance. EXTERNAL_MANAGED Global and regional external Application Load Balancers, and regional external proxy Network Load Balancers, used with --target-http-proxy, --target-https-proxy, --target-tcp-proxy. INTERNAL Internal passthrough Network Load Balancers or protocol forwarding, used with --backend-service. INTERNAL_MANAGED Internal Application Load Balancers and internal proxy Network Load Balancers, used with --target-http-proxy, --target-https-proxy, --target-tcp-proxy. INTERNAL_SELF_MANAGED Traffic Director, used with --target-http-proxy, --target-https-proxy, --target-grpc-proxy, --target-tcp-proxy. |
| `--network` | NETWORK |  | (DEPRECATED) Only for --load-balancing-scheme=INTERNAL or --load-balancing-scheme=INTERNAL_SELF_MANAGED or --load-balancing-scheme=EXTERNAL_MANAGED (regional) or --load-balancing-scheme=INTERNAL_MANAGED) Network that this forwarding rule applies to. If this field is not specified, the default network is used. In the absence of the default network, this field must be specified. The --network option is deprecated and will be removed in an upcoming release. If you're currently using this argument, you should remove it from your workflows. |
| `--subnet` | SUBNET |  | (DEPRECATED) Only for --load-balancing-scheme=INTERNAL and --load-balancing-scheme=INTERNAL_MANAGED) Subnetwork that this forwarding rule applies to. If the network is auto mode, this flag is optional. If the network is custom mode, this flag is required. The --subnet option is deprecated and will be removed in an upcoming release. If you're currently using this argument, you should remove it from your workflows. |
| `--subnet-region` | SUBNET_REGION |  | (DEPRECATED) Region of the subnetwork to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. The --subnet-region option is deprecated and will be removed in an upcoming release. If you're currently using this argument, you should remove it from your workflows. |
| `--target-instance-zone` | TARGET_INSTANCE_ZONE |  | Zone of the target instance to operate on. Overrides the default compute/zone property value for this command invocation. |
| `--target-pool-region` | TARGET_POOL_REGION |  | Region of the target pool to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. |
| `--target-vpn-gateway-region` | TARGET_VPN_GATEWAY_REGION |  | Region of the VPN gateway to operate on. If not specified, the region is set to the region of the forwarding rule. Overrides the default compute/region property value for this command invocation. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/set-target)

---
### `gcloud compute forwarding-rules update`

Update a Compute Engine forwarding rule

gcloud compute forwarding-rules update updates global access for a Compute
Engine forwarding rule.

**Synopsis:**
```
gcloud compute forwarding-rules update NAME [--allow-global-access]
    [--allow-psc-global-access]
    [--external-managed-backend-bucket-migration-testing-percentage=EXTERNAL_MANAGED_BACKEND_BUCKET_MIGRATION_TESTING_PERCENTAGE]
    [--load-balancing-scheme=LOAD_BALANCING_SCHEME]
    [--source-ip-ranges=SOURCE_IP_RANGE,[...]]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-external-managed-backend-bucket-migration-state
      | --external-managed-backend-bucket-migration-state=EXTERNAL_MANAGED_BACKEND_BUCKET_MIGRATION_STATE]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--global | --region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the forwarding rule to operate on.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-global-access` |  |  | If True, then clients from all regions can access this internal forwarding rule. This can only be specified for forwarding rules with the LOAD_BALANCING_SCHEME set to INTERNAL or INTERNAL_MANAGED. For forwarding rules of type INTERNAL, the target must be either a backend service or a target instance. |
| `--allow-psc-global-access` |  |  | If specified, clients from all regions can access this Private Service Connect forwarding rule. This can only be specified if the forwarding rule's target is a service attachment (--target-service-attachment). |
| `--external-managed-backend-bucket-migration-testing-percentage` | EXTERNAL_MANAGED_BACKEND_BUCKET_MIGRATION_TESTING_PERCENTAGE |  | Determines the fraction of requests that should be processed by the Global external Application Load Balancer. The value of this field must be in the range [0, 100]. |
| `--load-balancing-scheme` | one of: EXTERNAL, EXTERNAL_MANAGED |  | Only for the Global external Application Load Balancer migration. The value of this field must be EXTERNAL or EXTERNAL_MANAGED. LOAD_BALANCING_SCHEME must be one of: EXTERNAL, EXTERNAL_MANAGED. |
| `--source-ip-ranges` | SOURCE_IP_RANGE,[...] |  | List of comma-separated IP addresses or IP ranges. If set, this forwarding rule only forwards traffic when the packet's source IP address matches one of the IP ranges set here. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the forwarding rule to allow global access, run:

    $ gcloud compute forwarding-rules update example-fr \
        --allow-global-access --region=us-central1

To add/update labels k0 and k1 and remove labels with key k3, run:

    $ gcloud compute forwarding-rules update example-fr \
        --region=us-central1 --update-labels=k0=value1,k1=value2 \
        --remove-labels=k3

Labels can be used to identify the forwarding rule and to filter them as in

    $ gcloud compute forwarding-rules list --filter='labels.k1:value2'

To list existing labels, run:

    $ gcloud compute forwarding-rules describe example-fr \
        --format="default(labels)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/forwarding-rules/update)

---