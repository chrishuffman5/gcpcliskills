# gcloud network-services service-lb-policies

manage Network Services ServiceLbPolicies

### `gcloud network-services service-lb-policies create`

Create a service LB policy

Create a new service LB policy with the given name.

**Synopsis:**
```
gcloud network-services service-lb-policies create
    (SERVICE_LB_POLICY : --location=LOCATION) [--async]
    [--auto-capacity-drain] [--description=DESCRIPTION]
    [--failover-health-threshold=FAILOVER_HEALTH_THRESHOLD]
    [--isolation-config-granularity=ISOLATION_CONFIG_GRANULARITY;
      default="unspecified"]
    [--isolation-config-mode=ISOLATION_CONFIG_MODE; default="unspecified"]
    [--load-balancing-algorithm=LOAD_BALANCING_ALGORITHM;
      default="waterfall-by-region"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service lb policy resource - Name of the service LB policy to be created.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_lb_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_LB_POLICY
     ID of the service lb policy or fully qualified identifier for the
     service lb policy.

     To set the service_lb_policy attribute:
     + provide the argument service_lb_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_lb_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-capacity-drain` |  |  | If specified, an unhealthy MIG/NEG will be removed from Global load balancing and traffic routing for the service. A MIG/NEG is considered to be unhealthy if less than 25% of the instance/endpoints in the MIG/NEG are healthy. autoCapacityDrain will never drain more than 50% of the configured MIGs/NEGs of a Backend Service. |
| `--description` | DESCRIPTION |  | The description for the service LB policy. |
| `--failover-health-threshold` | FAILOVER_HEALTH_THRESHOLD |  | The percentage threshold that a load balancer will begin to send traffic to failover backends. If the percentage of endpoints in a MIG/NEG is smaller than this value, traffic would be sent to failover backends if possible. This field should be set to a value between 1 and 99. The default value is 50 for Proxyless service mesh, and 70 for others. |
| `--isolation-config-granularity` | one of: region Traffic for this service will be isolated at the nearest cloud region | unspecified | The granularity of the isolation. ISOLATION_CONFIG_GRANULARITY must be one of: region Traffic for this service will be isolated at the nearest cloud region. unspecified No isolation is configured for the backend service. Traffic can overflow based on the load balancing algorithm. |
| `--isolation-config-mode` | one of: nearest Traffic will be sent to the nearest location | unspecified | The granularity of the isolation. ISOLATION_CONFIG_MODE must be one of: nearest Traffic will be sent to the nearest location. strict Traffic will fail if no serving backends are available in the same region as the load balancer. unspecified No isolation mode is configured for the backend service. |
| `--load-balancing-algorithm` | one of: spray-to-region Spread the traffic from each client to all the MIGs/NEGs in a region | waterfall-by-region | The global load balancing algorithm to be used. LOAD_BALANCING_ALGORITHM must be one of: spray-to-region Spread the traffic from each client to all the MIGs/NEGs in a region. spray-to-world Balance traffic across all backends across the world proportionally based on capacity. waterfall-by-region Direct traffic to the nearest region with endpoints and capacity before spilling over to other regions. waterfall-by-zone Attempt to keep traffic in a single zone closest to the client, before spilling over to other zones. |


**Examples:**
```bash
Create a service LB policy with the name 'my-service-lb-policy', load
balancing algorithm 'waterfall-by-region', and location 'global'.

    $ gcloud network-services service-lb-policies create \
        my-service-lb-policy \
        --load-balancing-algorithm=waterfall-by-region \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/create)

---
### `gcloud network-services service-lb-policies delete`

Delete service LB policy

Delete the specified service LB policy.

**Synopsis:**
```
gcloud network-services service-lb-policies delete
    (SERVICE_LB_POLICY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service lb policy resource - Name of the service LB policy you want to
delete. The arguments in this group can be used to specify the attributes
of this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument service_lb_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_LB_POLICY
     ID of the service lb policy or fully qualified identifier for the
     service lb policy.

     To set the service_lb_policy attribute:
     + provide the argument service_lb_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_lb_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a service LB policy named my-service-lb-policy, run:

    $ gcloud network-services service-lb-policies delete \
        my-service-lb-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/delete)

---
### `gcloud network-services service-lb-policies describe`

Describe a service LB policy

Show details of a service LB policy.

**Synopsis:**
```
gcloud network-services service-lb-policies describe
    (SERVICE_LB_POLICY : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service lb policy resource - Name of the service LB policy to be
described. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service_lb_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_LB_POLICY
     ID of the service lb policy or fully qualified identifier for the
     service lb policy.

     To set the service_lb_policy attribute:
     + provide the argument service_lb_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_lb_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a service LB policy named 'my-service-lb-policy'.

    $ gcloud network-services service-lb-policies describe \
        my-service-lb-policy --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/describe)

---
### `gcloud network-services service-lb-policies export`

Export service LB policy

Export a service LB policy.

**Synopsis:**
```
gcloud network-services service-lb-policies export
    (SERVICE_LB_POLICY : --location=LOCATION) [--destination=DESTINATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service lb policy resource - Name of the service LB policy to export. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_lb_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_LB_POLICY
     ID of the service lb policy or fully qualified identifier for the
     service lb policy.

     To set the service_lb_policy attribute:
     + provide the argument service_lb_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_lb_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a service LB policy named my-service-lb-policy to a YAML file,
run:

    $ gcloud network-services service-lb-policies export \
        my-service-lb-policy --destination=my-service-lb-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/export)

---
### `gcloud network-services service-lb-policies import`

Import service LB policy

Import a service LB policy.

**Synopsis:**
```
gcloud network-services service-lb-policies import
    (SERVICE_LB_POLICY : --location=LOCATION) [--async] [--source=SOURCE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service lb policy resource - Name of the service LB policy to import. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_lb_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_LB_POLICY
     ID of the service lb policy or fully qualified identifier for the
     service lb policy.

     To set the service_lb_policy attribute:
     + provide the argument service_lb_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_lb_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a service LB policy named my-service-lb-policy from a YAML file,
run:

    $ gcloud network-services service-lb-policies import \
        my-service-lb-policy --source=my-service-lb-policy.yaml \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/import)

---
### `gcloud network-services service-lb-policies list`

List ServiceLbPolicies

List all ServiceLbPolicies in the specified location of the current
project.

**Synopsis:**
```
gcloud network-services service-lb-policies list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list service lb policies in the current project, run:

    $ gcloud network-services service-lb-policies list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/list)

---
### `gcloud network-services service-lb-policies update`

Update a service LB policy

Update the detail of a service LB Policy.

**Synopsis:**
```
gcloud network-services service-lb-policies update
    (SERVICE_LB_POLICY : --location=LOCATION) [--async]
    [--auto-capacity-drain] [--description=DESCRIPTION]
    [--failover-health-threshold=FAILOVER_HEALTH_THRESHOLD]
    [--isolation-config-granularity=ISOLATION_CONFIG_GRANULARITY;
      default="unspecified"]
    [--isolation-config-mode=ISOLATION_CONFIG_MODE; default="unspecified"]
    [--load-balancing-algorithm=LOAD_BALANCING_ALGORITHM;
      default="waterfall-by-region"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service lb policy resource - Name of the service LB policy to be updated.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument service_lb_policy on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE_LB_POLICY
     ID of the service lb policy or fully qualified identifier for the
     service lb policy.

     To set the service_lb_policy attribute:
     + provide the argument service_lb_policy on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument service_lb_policy on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--auto-capacity-drain` |  |  | If specified, an unhealthy MIG/NEG will be removed from Global load balancing and traffic routing for the service. A MIG/NEG is considered to be unhealthy if less than 25% of the instance/endpoints in the MIG/NEG are healthy. autoCapacityDrain will never drain more than 50% of the configured MIGs/NEGs of a Backend Service. |
| `--description` | DESCRIPTION |  | The description for the service LB policy. |
| `--failover-health-threshold` | FAILOVER_HEALTH_THRESHOLD |  | The percentage threshold that a load balancer will begin to send traffic to failover backends. If the percentage of endpoints in a MIG/NEG is smaller than this value, traffic would be sent to failover backends if possible. This field should be set to a value between 1 and 99. The default value is 50 for Proxyless service mesh, and 70 for others. |
| `--isolation-config-granularity` | one of: region Traffic for this service will be isolated at the nearest cloud region | unspecified | The granularity of the isolation. ISOLATION_CONFIG_GRANULARITY must be one of: region Traffic for this service will be isolated at the nearest cloud region. unspecified No isolation is configured for the backend service. Traffic can overflow based on the load balancing algorithm. |
| `--isolation-config-mode` | one of: nearest Traffic will be sent to the nearest location | unspecified | The granularity of the isolation. ISOLATION_CONFIG_MODE must be one of: nearest Traffic will be sent to the nearest location. strict Traffic will fail if no serving backends are available in the same region as the load balancer. unspecified No isolation mode is configured for the backend service. |
| `--load-balancing-algorithm` | one of: spray-to-region Spread the traffic from each client to all the MIGs/NEGs in a region | waterfall-by-region | The global load balancing algorithm to be used. LOAD_BALANCING_ALGORITHM must be one of: spray-to-region Spread the traffic from each client to all the MIGs/NEGs in a region. spray-to-world Balance traffic across all backends across the world proportionally based on capacity. waterfall-by-region Direct traffic to the nearest region with endpoints and capacity before spilling over to other regions. waterfall-by-zone Attempt to keep traffic in a single zone closest to the client, before spilling over to other zones. |


**Examples:**
```bash
Update load-balancing-algorithm of a service LB policy named
my-service-lb-policy:

    $ gcloud network-services service-lb-policies update \
        my-service-lb-policy \
        --load-balancing-algorithm=waterfall-by-zone
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/service-lb-policies/update)

---