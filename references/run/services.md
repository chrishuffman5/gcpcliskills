# gcloud run services

view and manage your Cloud Run services

### `gcloud run services add-iam-policy-binding`

Add IAM policy binding to a Cloud Run service

Add an IAM policy binding to the IAM policy of a Cloud Run service. One
binding consists of a member, and a role.

**Synopsis:**
```
gcloud run services add-iam-policy-binding SERVICE --member=PRINCIPAL
    --role=ROLE [--region=REGION]
    [--condition=[KEY=VALUE,...] | --condition-from-file=PATH_TO_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The service for which to add IAM policy binding to.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/run.invoker' for the
user 'test-user@gmail.com' with service 'my-service' and region
'us-central1', run:

    $ gcloud run services add-iam-policy-binding my-service \
        --region='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/run.invoker'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/add-iam-policy-binding)

---
### `gcloud run services delete`

Delete a service

Delete a service.

**Synopsis:**
```
gcloud run services delete (SERVICE : --namespace=NAMESPACE) [--[no-]async]
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service to delete. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument SERVICE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     service.

     To set the namespace attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]async` |  |  | Return immediately, without waiting for the operation in progress to complete. Defaults to --no-async. Use --async to enable and --no-async to disable. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To delete a service:

    $ gcloud run services delete <service-name>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/delete)

---
### `gcloud run services describe`

Obtain details about a given service

Obtain details about a given service.

**Synopsis:**
```
gcloud run services describe (SERVICE : --namespace=NAMESPACE)
    [--region=REGION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service to describe. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument SERVICE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     service.

     To set the namespace attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To obtain details about a given service:

    $ gcloud run services describe <service-name>

To get those details in the YAML format:

    $ gcloud run services describe <service-name> --format=yaml

To get them in YAML format suited to export (omitting metadata specific to
this deployment and status info):

    $ gcloud run services describe <service-name> --format=export
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/describe)

---
### `gcloud run services get-iam-policy`

Get the IAM policy for a Cloud Run service

This command gets the IAM policy for a service. If formatted as JSON, the
output can be edited and used as a policy file for set-iam-policy. The
output includes an "etag" field identifying the version emitted and
allowing detection of concurrent policy updates; see $ gcloud alpha run
registries set-iam-policy for additional details.

**Synopsis:**
```
gcloud run services get-iam-policy SERVICE [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The service for which to display the IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To print the IAM policy for a given service, run:

    $ gcloud run services get-iam-policy --region=us-central1 my-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/get-iam-policy)

---
### `gcloud run services list`

List available services

List available services.

**Synopsis:**
```
gcloud run services list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To list available services:

    $ gcloud run services list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/list)

---
### `gcloud run services proxy`

Proxy a service to localhost authenticating as the active account or with the specified token

Runs a server on localhost that proxies requests to the specified Cloud Run
Service with credentials attached.

You can use this to test services protected with IAM authentication.

The Cloud Run service must be reachable from the machine running this
command. For example, if the Cloud Run Service is configured to only allow
internal ingress, this command will not work from outside the service's VPC
network.

**Synopsis:**
```
gcloud run services proxy (SERVICE : --namespace=NAMESPACE) [--port=PORT]
    [--region=REGION] [--tag=TAG] [--token=TOKEN] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service to proxy locally. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument SERVICE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     service.

     To set the namespace attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--port` | PORT |  | Local port number to expose the proxied service. If not specified, it will be set to 8080. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--tag` | TAG |  | Traffic tag of the service to expose via the proxy. If not specified, the default service URL will be proxied which may serve different revisions based on traffic-splits. Custom tags can be used to proxy specific revisions. Please see https://cloud.google.com/run/docs/rollouts-rollbacks-traffic-migration#tags. |
| `--token` | TOKEN |  | The specific identity token to add to all requests of the proxied service. If not specified, the identity token of the currently active authenticated account will be used (e.g. gcloud auth print-identity-token). |


**Examples:**
```bash
To proxy the service 'my-service' at localhost port 8080:

    $ gcloud run services proxy my-service --port=8080

To proxy the existing traffic tag 'my-tag' on the service 'my-service:

    $ gcloud run services proxy my-service --tag=my-tag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/proxy)

---
### `gcloud run services remove-iam-policy-binding`

Remove IAM policy binding of a Cloud Run service

Remove an IAM policy binding from the IAM policy of a service. One binding
consists of a member, and a role.

**Synopsis:**
```
gcloud run services remove-iam-policy-binding SERVICE --member=PRINCIPAL
    --role=ROLE [--region=REGION]
    [--all | --condition=[KEY=VALUE,...]
      | --condition-from-file=PATH_TO_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The service for which to remove the IAM policy binding.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/run.invoker' for the
user 'test-user@gmail.com' with service 'my-service' and region
'us-central1', run:

    $ gcloud run services remove-iam-policy-binding my-service \
        --region='us-central1' --member='user:test-user@gmail.com' \
        --role='roles/run.invoker'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/remove-iam-policy-binding)

---
### `gcloud run services replace`

Create or replace a service from a YAML service specification

Creates or replaces a service from a YAML service specification.

**Synopsis:**
```
gcloud run services replace FILE [--async] [--dry-run] [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
FILE
   The absolute path to the YAML file with a Knative service definition
   for the service to update or deploy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--dry-run` |  |  | If set to true, only validates the configuration. The configuration will not be applied. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To replace the specification for a service defined in myservice.yaml

    $ gcloud run services replace myservice.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/replace)

---
### `gcloud run services set-iam-policy`

Set the IAM policy for a service

This command replaces the existing IAM policy for a service, given a
service and a file encoded in JSON or YAML that contains the IAM policy. If
the given policy file specifies an "etag" value, then the replacement will
succeed only if the policy already in place matches that etag. (An etag
obtain via get-iam-policy will prevent the replacement if the policy for
the service has been subsequently updated.) A policy file that does not
contain an etag value will replace any existing policy for the service.

**Synopsis:**
```
gcloud run services set-iam-policy SERVICE POLICY_FILE [--region=REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The service for which to set the IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the region attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --region on the command line;
 * set the property run/region;
 * specify from a list of available regions in a prompt.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
The following command will read an IAM policy defined in a JSON file
'policy.json' and set it for a service with identifier 'my-service'

    $ gcloud run services set-iam-policy --region=us-central1 \
        my-service policy.json

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/set-iam-policy)

---
### `gcloud run services update`

Update Cloud Run environment variables and other configuration settings

Update Cloud Run environment variables and other configuration settings.

**Synopsis:**
```
gcloud run services update [[SERVICE] --namespace=NAMESPACE] [--async]
    [--breakglass=JUSTIFICATION] [--clear-vpc-connector]
    [--concurrency=CONCURRENCY] [--container=CONTAINER] [--[no-]cpu-boost]
    [--[no-]cpu-throttling] [--[no-]default-url]
    [--[no-]deploy-health-check]
    [--execution-environment=EXECUTION_ENVIRONMENT] [--gpu-type=GPU_TYPE]
    [--[no-]gpu-zonal-redundancy] [--ingress=INGRESS; default="all"]
    [--[no-]invoker-iam-check] [--max=MAX] [--max-instances=MAX_INSTANCES]
    [--min=MIN] [--min-instances=MIN_INSTANCES] [--region=REGION]
    [--remove-containers=[CONTAINER,...]]
    [--revision-suffix=REVISION_SUFFIX] [--scaling=SCALING]
    [--service-account=SERVICE_ACCOUNT] [--[no-]session-affinity]
    [--tag=TAG] [--timeout=TIMEOUT] [--no-traffic]
    [--vpc-connector=VPC_CONNECTOR] [--vpc-egress=VPC_EGRESS]
    [--add-cloudsql-instances=[CLOUDSQL-INSTANCES,...]
      | --clear-cloudsql-instances
      | --remove-cloudsql-instances=[CLOUDSQL-INSTANCES,...]
      | --set-cloudsql-instances=[CLOUDSQL-INSTANCES,...]]
    [--add-custom-audiences=[CUSTOM-AUDIENCES,...]
      | --clear-custom-audiences
      | --remove-custom-audiences=[CUSTOM-AUDIENCES,...]
      | --set-custom-audiences=[CUSTOM-AUDIENCES,...]]
    [--add-volume=[KEY=VALUE,...]
      --clear-volumes --remove-volume=[VOLUME,...]]
    [--add-volume-mount=[volume=NAME,mount-path=MOUNT_PATH,...]
      --args=[ARG,...] --clear-volume-mounts --command=[COMMAND,...]
      --cpu=CPU --depends-on=[CONTAINER,...] --gpu=GPU --image=IMAGE
      --liveness-probe=[KEY=VALUE,...] --memory=MEMORY --port=PORT
      --remove-volume-mount=[MOUNT_PATH,...]
      --startup-probe=[KEY=VALUE,...] --[no-]use-http2 --clear-env-vars
      | --env-vars-file=FILE_PATH | --set-env-vars=[KEY=VALUE,...]
      | --remove-env-vars=[KEY,...]
      --update-env-vars=[KEY=VALUE,...] --clear-secrets
      | --set-secrets=[KEY=VALUE,...]
      | --remove-secrets=[KEY,...] --update-secrets=[KEY=VALUE,...]]
    [--binary-authorization=POLICY | --clear-binary-authorization]
    [--clear-encryption-key-shutdown-hours
      | --encryption-key-shutdown-hours=ENCRYPTION_KEY_SHUTDOWN_HOURS]
    [--clear-key | --key=KEY]
    [--clear-labels | --remove-labels=[KEY,...] --labels=[KEY=VALUE,...]
      | --update-labels=[KEY=VALUE,...]]
    [--clear-network
      | --network=NETWORK --subnet=SUBNET --clear-network-tags
      | --network-tags=[TAG,...]]
    [--clear-post-key-revocation-action-type
      | --post-key-revocation-action-type=POST_KEY_REVOCATION_ACTION_TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service to update the configuration of. The arguments
in this group can be used to specify the attributes of this resource.

  [SERVICE]
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument SERVICE on the command line;
     + specify the service name from an interactive prompt.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     service.

     To set the namespace attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + specify the service name from an interactive prompt with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--breakglass` | JUSTIFICATION |  | Justification to bypass Binary Authorization policy constraints and allow the operation. See https://cloud.google.com/binary-authorization/docs/using-breakglass for more information. Next update or deploy command will automatically clear existing breakglass justification. |
| `--clear-vpc-connector` |  |  | Remove the VPC connector for this resource. |
| `--concurrency` | CONCURRENCY |  | Set the maximum number of concurrent requests allowed per container instance. Leave concurrency unspecified or provide the special value 'default' to receive the server default value. |
| `--container` | CONTAINER |  | Specifies a container by name. Flags following --container will apply to the specified container. Flags that are not container-specific must be specified before --container. |
| `--[no-]cpu-boost` |  |  | Whether to allocate extra CPU to containers on startup to reduce the perceived latency of a cold start request. Enabled by default when unspecified on new services. Use --cpu-boost to enable and --no-cpu-boost to disable. |
| `--[no-]cpu-throttling` |  |  | Whether to throttle the CPU when the container is not actively serving requests. Use --cpu-throttling to enable and --no-cpu-throttling to disable. |
| `--[no-]default-url` |  |  | Toggles the default url for a run service. This is enabled by default if not specified. Use --default-url to enable and --no-default-url to disable. |
| `--[no-]deploy-health-check` |  |  | Schedules a single instance of the Revision and waits for it to pass its startup probe for the deployment to succeed. If disabled, the startup probe runs only when the revision is first started via invocation or by setting min-instances. This check is enabled by default when unspecified. Use --deploy-health-check to enable and --no-deploy-health-check to disable. |
| `--execution-environment` | one of: gen1 Run the application in a first generation execution environment |  | Selects the execution environment where the application will run. EXECUTION_ENVIRONMENT must be one of: gen1 Run the application in a first generation execution environment. gen2 Run the application in a second generation execution environment. |
| `--gpu-type` | GPU_TYPE |  | The GPU type to use. |
| `--[no-]gpu-zonal-redundancy` |  |  | Set GPU zonal redundancy. Use --gpu-zonal-redundancy to enable and --no-gpu-zonal-redundancy to disable. |
| `--ingress` | one of: all Inbound requests from all sources are allowed | all | Set the ingress traffic sources allowed to call the service. For Cloud Run the --[no-]allow-unauthenticated flag separately controls the identities allowed to call the service. INGRESS must be one of: all Inbound requests from all sources are allowed. internal For Cloud Run, only inbound requests from VPC networks in the same project or VPC Service Controls perimeter, as well as Pub/Sub subscriptions and Eventarc events in the same project or VPC Service Controls perimeter are allowed. All other requests are rejected. See https://cloud.google.com/run/docs/securing/ingress for full details on the definition of internal traffic for Cloud Run. internal-and-cloud-load-balancing Only inbound requests from Google Cloud Load Balancing or a traffic source allowed by the internal option are allowed. |
| `--[no-]invoker-iam-check` |  |  | Optionally disable invoker IAM checks. This feature is available by invitation only. More info at https://cloud.google.com/run/docs/securing/managing-access#invoker_check. Use --invoker-iam-check to enable and --no-invoker-iam-check to disable. |
| `--max` | MAX |  | The maximum number of container instances to run for this Service. This instance limit will be divided among all Revisions receiving a percentage of traffic and can be modified without deploying a new Revision. |
| `--max-instances` | MAX_INSTANCES |  | The maximum number of container instances for this Revision to run or 'default' to remove. This setting is immutably set on each new Revision and modifying its value will deploy another Revision. |
| `--min` | MIN |  | The minimum number of container instances to run for this Service or 'default' to remove. These instances will be divided among all Revisions receiving a percentage of traffic and can be modified without deploying a new Revision. |
| `--min-instances` | MIN_INSTANCES |  | The minimum number of container instances to run for this Revision or 'default' to remove. This setting is immutably set on each new Revision and modifying its value will deploy a another Revision. Consider using --min to set the minimum number of instances across all revisions of the Service which may be modified dynamically. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--remove-containers` | [CONTAINER,...] |  | List of containers to remove. |
| `--revision-suffix` | REVISION_SUFFIX |  | Specify the suffix of the revision name. Revision names always start with the service name automatically. For example, specifying [--revision-suffix=v1] for a service named 'helloworld', would lead to a revision named 'helloworld-v1'. Set empty string to clear the suffix and resume server-assigned naming. |
| `--scaling` | SCALING |  | The scaling mode to use for this service. Flag value could be either "auto" for automatic scaling, or a positive integer to configure manual scaling with the given integer as a fixed instance count. |
| `--service-account` | SERVICE_ACCOUNT |  | the email address of an IAM service account associated with the revision of the service. The service account represents the identity of the running revision, and determines what permissions the revision has. |
| `--[no-]session-affinity` |  |  | Whether to enable session affinity for connections to the service. Use --session-affinity to enable and --no-session-affinity to disable. |
| `--tag` | TAG |  | Traffic tag to assign to the newly created revision. |
| `--timeout` | TIMEOUT |  | Set the maximum request execution time (timeout). It is specified as a duration; for example, "10m5s" is ten minutes, and five seconds. If you don't specify a unit, seconds is assumed. For example, "10" is 10 seconds. |
| `--no-traffic` |  |  | True to avoid sending traffic to the revision being deployed. Setting this flag assigns any traffic assigned to the LATEST revision to the specific revision bound to LATEST before the deployment. The effect is that the revision being deployed will not receive traffic. After a deployment with this flag the LATEST revision will not receive traffic on future deployments. To restore sending traffic to the LATEST revision by default, run the gcloud run services update-traffic command with --to-latest. |
| `--vpc-connector` | VPC_CONNECTOR |  | Set a VPC connector for this resource. |
| `--vpc-egress` | one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector |  | Specify which of the outbound traffic to send through Direct VPC egress or the VPC connector for this resource. This resource must have Direct VPC egress enabled or a VPC connector to set this flag. VPC_EGRESS must be one of: all (DEPRECATED) Sends all outbound traffic through Direct VPC egress or the VPC connector. Provides the same functionality as 'all-traffic'. Prefer to use 'all-traffic' instead. all-traffic Sends all outbound traffic through Direct VPC egress or the VPC connector. private-ranges-only Default option. Sends outbound traffic to private IP addresses (RFC 1918 and Private Google Access IPs) through Direct VPC egress or the VPC connector. Traffic to other Cloud Run services might require additional configuration. See https://cloud.google.com/run/docs/securing/private-networking#send_requests_to_other_services_and_services for more information. |
| `--add-volume` | [KEY=VALUE,...] |  | _[values.]_ Adds a volume to the Cloud Run resource. To add more than one volume, specify this flag multiple times. Volumes must have a name and type key. Only certain values are supported for type. Depending on the provided type, other keys will be required. The following types are supported with the specified additional keys: cloud-storage: A volume representing a Cloud Storage bucket. This volume type is mounted using Cloud Storage FUSE. See https://cloud.google.com/storage/docs/gcs-fuse for the details and limitations of this filesystem. Additional keys: * bucket: (required) the name of the bucket to use as the source of this volume * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. * mount-options: (optional) A list of flags to pass to GCSFuse. Flags should be specified without leading dashes and separated by semicolons. in-memory: An ephemeral volume that stores data in the instance's memory. With this type of volume, data is not shared between instances and all data will be lost when the instance it is on is terminated. Additional keys: * size-limit: (optional) A quantity representing the maximum amount of memory allocated to this volume, such as "512Mi" or "3G". Data stored in an in-memory volume consumes the memory allocation of the container that wrote the data. If size-limit is not specified, the maximum size will be half the total memory limit of all containers. nfs: Represents a volume backed by an NFS server. Additional keys: * location: (required) The location of the NFS Server, in the form SERVER:/PATH * readonly: (optional) A boolean. If true, this volume will be read-only from all mounts. |
| `--clear-volumes` |  |  | _[values.]_ Remove all existing volumes from the Cloud Run resource, including volumes mounted as secrets |
| `--remove-volume` | [VOLUME,...] |  | _[values.]_ Removes volumes from the Cloud Run resource. |


**Examples:**
```bash
To update one or more env vars:

    $ gcloud run services update myservice \
      --update-env-vars=KEY1=VALUE1,KEY2=VALUE2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/update)

---
### `gcloud run services update-traffic`

Adjust the traffic assignments for a Cloud Run service

Adjust the traffic assignments for a Cloud Run service.

**Synopsis:**
```
gcloud run services update-traffic [[SERVICE] --namespace=NAMESPACE]
    [--async] [--region=REGION]
    [--clear-tags | --set-tags=[TAG=REVISION,...]
      | --remove-tags=[TAG,...] --update-tags=[TAG=REVISION,...]]
    [--to-latest | --to-revisions=[REVISION-NAME=PERCENTAGE,...]
      | --to-tags=[TAG=PERCENTAGE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - Service to update the configuration of. The arguments
in this group can be used to specify the attributes of this resource.

  [SERVICE]
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument SERVICE on the command line;
     + specify the service name from an interactive prompt.

  --namespace=NAMESPACE
     Specific to Cloud Run for Anthos: Kubernetes namespace for the
     service.

     To set the namespace attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + specify the service name from an interactive prompt with a fully
       specified name;
     + provide the argument --namespace on the command line;
     + set the property run/namespace;
     + For Cloud Run on Kubernetes Engine, defaults to "default".
       Otherwise, defaults to project ID.;
     + provide the argument project on the command line;
     + set the property core/project.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |
| `--set-tags` | candidate=LATEST,current=myservice-v1 assigns the tag |  | _[revision names or "LATEST" for the latest ready revision. For example,]_ |


**Examples:**
```bash
To assign 10% of traffic to revision myservice-s5sxn and 90% of traffic to
revision myservice-cp9kw run:

    $ gcloud run services update-traffic myservice \
      --to-revisions=myservice-s5sxn=10,myservice-cp9kw=90

To increase the traffic to revision myservice-s5sxn to 20% and by reducing
the traffic to revision myservice-cp9kw to 80% run:

    $ gcloud run services update-traffic myservice \
      --to-revisions=myservice-s5sxn=20

To rollback to revision myservice-cp9kw run:

    $ gcloud run services update-traffic myservice \
      --to-revisions=myservice-cp9kw=100

To assign 100% of traffic to the current or future LATEST revision run:

    $ gcloud run services update-traffic myservice --to-latest

You can also refer to the current or future LATEST revision in
--to-revisions by the string "LATEST". For example, to set 10% of traffic
to always float to the latest revision:

    $ gcloud run services update-traffic myservice \
      --to-revisions=LATEST=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/update-traffic)

---

## `gcloud run services logs` — read logs for Cloud Run services
### `gcloud run services logs read`

Read logs for a Cloud Run service

gcloud run services logs read reads log entries. Log entries matching
--log-filter are returned according to the specified --order. If the log
entries come from multiple logs, then entries from different logs might be
intermingled in the results.

**Synopsis:**
```
gcloud run services logs read SERVICE [--freshness=FRESHNESS; default="1d"]
    [--log-filter=LOG_FILTER] [--order=ORDER; default="desc"]
    [--region=REGION] [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SERVICE
   Name for a Cloud Run service.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--freshness` | FRESHNESS | 1d | Return entries that are not older than this value. Works only with DESC ordering and filters without a timestamp. See $ gcloud topic datetimes for information on duration formats. |
| `--log-filter` | LOG_FILTER |  | Filter expression that specifies the log entries to return. Detailed information about filters can be found at: https://cloud.google.com/logging/docs/view/logging-query-language |
| `--order` | one of: desc, asc | desc | Ordering of returned log entries based on timestamp field. ORDER must be one of: desc, asc. |
| `--region` | REGION |  | Region in which the resource can be found. Alternatively, set the property [run/region]. |


**Examples:**
```bash
To read log entries from for a Cloud Run Service, run:

    $ gcloud run services logs read my-service

To read log entries with severity ERROR or higher, run:

    $ gcloud run services logs read my-service \
        --log-filter="severity>=ERROR"

To read log entries written in a specific time window, run:

    $ gcloud run services logs read my-service \
        --log-filter='timestamp<="2015-05-31T23:59:59Z" AND
     timestamp>="2015-05-31T00:00:00Z"'

To read up to 10 log entries in your service payloads that include the word
SearchText and format the output in JSON format, run:

    $ gcloud run services logs read my-service \
        --log-filter="textPayload:SearchText" --limit=10 --format=json

Detailed information about filters can be found at:
https://cloud.google.com/logging/docs/view/advanced_filters
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/services/logs/read)

---