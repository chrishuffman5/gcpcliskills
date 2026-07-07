# gcloud run (top-level commands)

### `gcloud run deploy`

Create or update a Cloud Run service

Creates or updates a Cloud Run service.

**Synopsis:**
```
gcloud run deploy [[SERVICE] --namespace=NAMESPACE]
    [--[no-]allow-unauthenticated] [--async] [--breakglass=JUSTIFICATION]
    [--clear-vpc-connector] [--concurrency=CONCURRENCY]
    [--container=CONTAINER] [--[no-]cpu-boost] [--[no-]cpu-throttling]
    [--[no-]default-url] [--[no-]deploy-health-check]
    [--description=DESCRIPTION]
    [--execution-environment=EXECUTION_ENVIRONMENT] [--gpu-type=GPU_TYPE]
    [--[no-]gpu-zonal-redundancy] [--ingress=INGRESS; default="all"]
    [--[no-]invoker-iam-check] [--max=MAX] [--max-instances=MAX_INSTANCES]
    [--min=MIN] [--min-instances=MIN_INSTANCES] [--region=REGION]
    [--regions=REGIONS] [--remove-containers=[CONTAINER,...]]
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
      --args=[ARG,...] --[no-]automatic-updates --clear-volume-mounts
      --cpu=CPU --depends-on=[CONTAINER,...] --gpu=GPU
      --liveness-probe=[KEY=VALUE,...] --memory=MEMORY --port=PORT
      --remove-volume-mount=[MOUNT_PATH,...]
      --startup-probe=[KEY=VALUE,...]
      --[no-]use-http2 --base-image=BASE_IMAGE
      | --clear-base-image --build-env-vars-file=FILE_PATH
      | --clear-build-env-vars | --set-build-env-vars=[KEY=VALUE,...]
      | --remove-build-env-vars=[KEY,...]
      --update-build-env-vars=[KEY=VALUE,...]
      --build-service-account=BUILD_SERVICE_ACCOUNT
      | --clear-build-service-account --build-worker-pool=BUILD_WORKER_POOL
      | --clear-build-worker-pool --clear-env-vars
      | --env-vars-file=FILE_PATH | --set-env-vars=[KEY=VALUE,...]
      | --remove-env-vars=[KEY,...]
      --update-env-vars=[KEY=VALUE,...] --clear-secrets
      | --set-secrets=[KEY=VALUE,...] | --remove-secrets=[KEY,...]
      --update-secrets=[KEY=VALUE,...] --command=[COMMAND,...]
      | --function=FUNCTION --image=IMAGE --source=SOURCE]
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
Service resource - Service to deploy to. The arguments in this group can
be used to specify the attributes of this resource.

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
| `--[no-]allow-unauthenticated` |  |  | Whether to enable allowing unauthenticated access to the service. This may take a few moments to take effect. Use --allow-unauthenticated to enable and --no-allow-unauthenticated to disable. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--breakglass` | JUSTIFICATION |  | Justification to bypass Binary Authorization policy constraints and allow the operation. See https://cloud.google.com/binary-authorization/docs/using-breakglass for more information. Next update or deploy command will automatically clear existing breakglass justification. |
| `--clear-vpc-connector` |  |  | Remove the VPC connector for this resource. |
| `--concurrency` | CONCURRENCY |  | Set the maximum number of concurrent requests allowed per container instance. Leave concurrency unspecified or provide the special value 'default' to receive the server default value. |
| `--container` | CONTAINER |  | Specifies a container by name. Flags following --container will apply to the specified container. Flags that are not container-specific must be specified before --container. |
| `--[no-]cpu-boost` |  |  | Whether to allocate extra CPU to containers on startup to reduce the perceived latency of a cold start request. Enabled by default when unspecified on new services. Use --cpu-boost to enable and --no-cpu-boost to disable. |
| `--[no-]cpu-throttling` |  |  | Whether to throttle the CPU when the container is not actively serving requests. Use --cpu-throttling to enable and --no-cpu-throttling to disable. |
| `--[no-]default-url` |  |  | Toggles the default url for a run service. This is enabled by default if not specified. Use --default-url to enable and --no-default-url to disable. |
| `--[no-]deploy-health-check` |  |  | Schedules a single instance of the Revision and waits for it to pass its startup probe for the deployment to succeed. If disabled, the startup probe runs only when the revision is first started via invocation or by setting min-instances. This check is enabled by default when unspecified. Use --deploy-health-check to enable and --no-deploy-health-check to disable. |
| `--description` | DESCRIPTION |  | Provides an optional, human-readable description of the service. |
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
| `--regions` | REGIONS |  | Comma-separated list of regions in which the multi-region Service can be found. |
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
To deploy a container to the service my-backend on Cloud Run:

    $ gcloud run deploy my-backend \
      --image=us-docker.pkg.dev/project/image

You may also omit the service name. Then a prompt will be displayed with a
suggested default value:

    $ gcloud run deploy --image=us-docker.pkg.dev/project/image

To deploy to Cloud Run on Kubernetes Engine, you need to specify a cluster:

    $ gcloud run deploy --image=us-docker.pkg.dev/project/image \
      --cluster=my-cluster
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/run/deploy)

---