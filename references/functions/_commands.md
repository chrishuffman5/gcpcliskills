# gcloud functions (top-level commands)

### `gcloud functions add-iam-policy-binding`

Adds an IAM policy binding for a Google Cloud Function

Adds an IAM policy binding for a Google Cloud Function.

**Synopsis:**
```
gcloud functions add-iam-policy-binding (NAME : --region=REGION)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to add IAM policy binding for.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add the iam policy binding for FUNCTION-1 to role ROLE-1 for member
MEMBER-1 run:

    $ gcloud functions add-iam-policy-binding FUNCTION-1 \
        --member=MEMBER-1 --role=ROLE-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/add-iam-policy-binding)

---
### `gcloud functions add-invoker-policy-binding`

Adds an invoker binding to the IAM policy of a Google Cloud Function

Adds an invoker role IAM policy binding that allows the specified member to
invoke the specified function.

For Cloud Functions (1st gen), this adds the Cloud Functions Invoker
binding to the IAM policy of the specified function.

For Cloud Functions (2nd gen), this adds the Cloud Run Invoker binding to
the IAM policy of the specified function's underlying Cloud Run service.

**Synopsis:**
```
gcloud functions add-invoker-policy-binding (NAME : --region=REGION)
    --member=PRINCIPAL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to add the invoker binding to.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add to the IAM policy. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |


**Examples:**
```bash
To add the invoker role policy binding for FUNCTION-1 for member MEMBER-1
run:

    $ gcloud functions add-invoker-policy-binding FUNCTION-1 \
        --member=MEMBER-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/add-invoker-policy-binding)

---
### `gcloud functions call`

Triggers execution of a Google Cloud Function

Triggers execution of a Google Cloud Function.

**Synopsis:**
```
gcloud functions call (NAME : --region=REGION)
    [--cloud-event=CLOUD_EVENT | --data=DATA] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to execute. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cloud-event` | CLOUD_EVENT |  | _[At most one of these can be specified:]_ JSON encoded string with a CloudEvent in structured content mode. Mutually exclusive with --data flag. Use for Cloud Functions 2nd Gen CloudEvent functions. The CloudEvent object will be sent to your function as a binary content mode message with the top-level 'data' field set as the HTTP body and all other JSON fields sent as HTTP headers. |
| `--data` | DATA |  | _[At most one of these can be specified:]_ JSON string with data that will be passed to the function. |


**Examples:**
```bash
To call a function, giving it 'Hello World!' in the message field of its
event argument (depending on your environment you might need to escape
characters in --data flag value differently), run:

    $ gcloud functions call helloWorld \
      --data='{"message": "Hello World!"}'

Note that this method has a limited quota which cannot be increased. It is
intended for testing and debugging and should not be used in production.

Calls to HTTP-triggered functions are sent as HTTP POST requests. To use
other HTTP methods, use a dedicated HTTP request tool such as cURL or wget.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/call)

---
### `gcloud functions delete`

Delete a Google Cloud Function

Delete a Google Cloud Function.

**Synopsis:**
```
gcloud functions delete (NAME : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/delete)

---
### `gcloud functions deploy`

Create or update a Google Cloud Function

Create or update a Google Cloud Function.

**Synopsis:**
```
gcloud functions deploy (NAME : --region=REGION)
    [--[no-]allow-unauthenticated] [--concurrency=CONCURRENCY]
    [--docker-registry=DOCKER_REGISTRY] [--egress-settings=EGRESS_SETTINGS]
    [--entry-point=ENTRY_POINT] [--gen2] [--ignore-file=IGNORE_FILE]
    [--ingress-settings=INGRESS_SETTINGS] [--retry]
    [--run-service-account=RUN_SERVICE_ACCOUNT] [--runtime=RUNTIME]
    [--runtime-update-policy=RUNTIME_UPDATE_POLICY]
    [--security-level=SECURITY_LEVEL; default="secure-always"]
    [--serve-all-traffic-latest-revision]
    [--service-account=SERVICE_ACCOUNT] [--source=SOURCE]
    [--stage-bucket=STAGE_BUCKET] [--timeout=TIMEOUT]
    [--trigger-location=TRIGGER_LOCATION]
    [--trigger-service-account=TRIGGER_SERVICE_ACCOUNT]
    [--update-labels=[KEY=VALUE,...]]
    [--binary-authorization=BINARY_AUTHORIZATION
      | --clear-binary-authorization]
    [--build-env-vars-file=FILE_PATH | --clear-build-env-vars
      | --set-build-env-vars=[KEY=VALUE,...]
      | --remove-build-env-vars=[KEY,...]
      --update-build-env-vars=[KEY=VALUE,...]]
    [--build-service-account=BUILD_SERVICE_ACCOUNT
      | --clear-build-service-account]
    [--build-worker-pool=BUILD_WORKER_POOL | --clear-build-worker-pool]
    [--clear-docker-repository | --docker-repository=DOCKER_REPOSITORY]
    [--clear-env-vars | --env-vars-file=FILE_PATH
      | --set-env-vars=[KEY=VALUE,...]
      | --remove-env-vars=[KEY,...] --update-env-vars=[KEY=VALUE,...]]
    [--clear-kms-key | --kms-key=KMS_KEY]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-max-instances | --max-instances=MAX_INSTANCES]
    [--clear-min-instances | --min-instances=MIN_INSTANCES]
    [--clear-secrets
      | --set-secrets=[SECRET_ENV_VAR=SECRET_VALUE_REF,
      /secret_path=SECRET_VALUE_REF,
      /mount_path:/secret_file_path=SECRET_VALUE_REF,...]
      | --remove-secrets=[SECRET_ENV_VAR,
      /secret_path,/mount_path:/secret_file_path,...]
      --update-secrets=[SECRET_ENV_VAR=SECRET_VALUE_REF,
      /secret_path=SECRET_VALUE_REF,
      /mount_path:/secret_file_path=SECRET_VALUE_REF,...]]
    [--clear-vpc-connector | --vpc-connector=VPC_CONNECTOR]
    [--memory=MEMORY : --cpu=CPU]
    [--trigger-bucket=TRIGGER_BUCKET | --trigger-http
      | --trigger-topic=TRIGGER_TOPIC
      | --trigger-event=EVENT_TYPE --trigger-resource=RESOURCE
      | --trigger-event-filters=[ATTRIBUTE=VALUE,...]
      --trigger-event-filters-path-pattern=[ATTRIBUTE=PATH_PATTERN,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to deploy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]allow-unauthenticated` |  |  | If set, makes this a public function. This will allow all callers, without checking authentication. Use --allow-unauthenticated to enable and --no-allow-unauthenticated to disable. |
| `--concurrency` | CONCURRENCY |  | Set the maximum number of concurrent requests allowed per container instance. Leave concurrency unspecified to receive the server default value. |
| `--docker-registry` | one of: artifact-registry, container-registry |  | (DEPRECATED) Docker Registry to use for storing the function's Docker images. The option artifact-registry is used by default. With the general transition from Container Registry to Artifact Registry, the option to specify docker registry is deprecated. All container image storage and management will automatically transition to Artifact Registry. For more information, see https://cloud.google.com/artifact-registry/docs/transition/transition-from-gcr DOCKER_REGISTRY must be one of: artifact-registry, container-registry. |
| `--egress-settings` | one of: private-ranges-only, all |  | Egress settings controls what traffic is diverted through the VPC Access Connector resource. By default private-ranges-only will be used. EGRESS_SETTINGS must be one of: private-ranges-only, all. |
| `--entry-point` | ENTRY_POINT |  | Name of a Google Cloud Function (as defined in source code) that will be executed. Defaults to the resource name suffix (ID of the function), if not specified. |
| `--gen2` |  |  | If enabled, this command will use Cloud Functions (Second generation). If disabled with --no-gen2, Cloud Functions (First generation) will be used. If not specified, the value of this flag will be taken from the functions/gen2 configuration property. If the functions/gen2 configuration property is not set, defaults to looking up the given function and using its generation. |
| `--ignore-file` | IGNORE_FILE |  | Override the .gcloudignore file in the source directory and use the specified file instead. By default, the source directory is your current directory. Note that it could be changed by the --source flag, in which case your .gcloudignore file will be searched in the overridden directory. For example, --ignore-file=.mygcloudignore combined with --source=./mydir would point to ./mydir/.mygcloudignore |
| `--ingress-settings` | one of: all, internal-only, internal-and-gclb |  | Ingress settings controls what traffic can reach the function. By default all will be used. INGRESS_SETTINGS must be one of: all, internal-only, internal-and-gclb. |
| `--retry` |  |  | If specified, then the function will be retried in case of a failure. |
| `--run-service-account` | RUN_SERVICE_ACCOUNT |  | The email address of the IAM service account associated with the Cloud Run service for the function. The service account represents the identity of the running function, and determines what permissions the function has. If not provided, the function will use the project's default service account for Compute Engine. |
| `--runtime` | RUNTIME |  | Runtime in which to run the function. Required when deploying a new function; optional when updating an existing function. For a list of available runtimes, run gcloud functions runtimes list. |
| `--runtime-update-policy` | one of: automatic, on-deploy |  | Runtime update policy for the function being deployed. The option automatic is used by default. RUNTIME_UPDATE_POLICY must be one of: automatic, on-deploy. |
| `--security-level` | one of: secure-always, secure-optional | secure-always | Security level controls whether a function's URL supports HTTPS only or both HTTP and HTTPS. By default, secure-always will be used, meaning only HTTPS is supported. SECURITY_LEVEL must be one of: secure-always, secure-optional. |
| `--serve-all-traffic-latest-revision` |  |  | If specified, latest function revision will be served all traffic. |
| `--service-account` | SERVICE_ACCOUNT |  | The email address of the IAM service account associated with the function at runtime. The service account represents the identity of the running function, and determines what permissions the function has. If not provided, the function will use the project's default service account for Compute Engine. |
| `--source` | SOURCE |  | Location of source code to deploy. Location of the source can be one of the following three options: * Source code in Google Cloud Storage (must be a .zip archive), * Reference to source repository or, * Local filesystem path (root directory of function source). Note that, depending on your runtime type, Cloud Functions will look for files with specific names for deployable functions. For Node.js, these filenames are index.js or function.js. For Python, this is main.py. If you do not specify the --source flag: * The current directory will be used for new function deployments. * If the function was previously deployed using a local filesystem path, then the function's source code will be updated using the current directory. * If the function was previously deployed using a Google Cloud Storage location or a source repository, then the function's source code will not be updated. The value of the flag will be interpreted as a Cloud Storage location, if it starts with gs://. The value will be interpreted as a reference to a source repository, if it starts with https://. Otherwise, it will be interpreted as the local filesystem path. When deploying source from the local filesystem, this command skips files specified in the .gcloudignore file (see gcloud topic gcloudignore for more information). If the .gcloudignore file doesn't exist, the command will try to create it. The minimal source repository URL is: https://source.developers.google.com/projects/${PROJECT}/repos/${REPO} By using the URL above, sources from the root directory of the repository on the revision tagged master will be used. If you want to deploy from a revision different from master, append one of the following three sources to the URL: * /revisions/${REVISION}, * /moveable-aliases/${MOVEABLE_ALIAS}, * /fixed-aliases/${FIXED_ALIAS}. If you'd like to deploy sources from a directory different from the root, you must specify a revision, a moveable alias, or a fixed alias, as above, and append /paths/${PATH_TO_SOURCES_DIRECTORY} to the URL. Overall, the URL should match the following regular expression: ^https://source\.developers\.google\.com/projects/ (?<accountId>[^/]+)/repos/(?<repoName>[^/]+) (((/revisions/(?<commit>[^/]+))\|(/moveable-aliases/(?<branch>[^/]+))\| (/fixed-aliases/(?<tag>[^/]+)))(/paths/(?<path>.*))?)?$ An example of a validly formatted source repository URL is: https://source.developers.google.com/projects/123456789/repos/testrepo/ moveable-aliases/alternate-branch/paths/path-to=source |
| `--stage-bucket` | STAGE_BUCKET |  | When deploying a function from a local directory, this flag's value is the name of the Google Cloud Storage bucket in which source code will be stored. Note that if you set the --stage-bucket flag when deploying a function, you will need to specify --source or --stage-bucket in subsequent deployments to update your source code. To use this flag successfully, the account in use must have permissions to write to this bucket. For help granting access, refer to this guide: https://cloud.google.com/storage/docs/access-control/ |
| `--timeout` | TIMEOUT |  | The function execution timeout, e.g. 30s for 30 seconds. Defaults to original value for existing function or 60 seconds for new functions. For GCF 1st gen functions, cannot be more than 540s. For GCF 2nd gen functions, cannot be more than 3600s. See $ gcloud topic datetimes for information on duration formats. |
| `--trigger-location` | TRIGGER_LOCATION |  | The location of the trigger, which must be a region or multi-region where the relevant events originate. |
| `--trigger-service-account` | TRIGGER_SERVICE_ACCOUNT |  | The email address of the IAM service account associated with the Eventarc trigger for the function. This is used for authenticated invocation. If not provided, the function will use the project's default service account for Compute Engine. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Label keys starting with deployment are reserved for use by deployment tools and cannot be specified manually. |
| `--memory` | MEMORY |  | _[- provide the argument --vpc-connector on the command line.]_ Limit on the amount of memory the function can use. Allowed values for v1 are: 128MB, 256MB, 512MB, 1024MB, 2048MB, 4096MB, and 8192MB. Allowed values for GCF 2nd gen are in the format: <number><unit> with allowed units of "k", "M", "G", "Ki", "Mi", "Gi". Ending 'b' or 'B' is allowed, but both are interpreted as bytes as opposed to bits. Examples: 1000000K, 1000000Ki, 256Mb, 512M, 1024Mi, 2G, 4Gi. By default, a new function is limited to 256MB of memory. When deploying an update to an existing function, the function keeps its old memory limit unless you specify this flag. |
| `--cpu` | CPU |  | _[- provide the argument --vpc-connector on the command line.]_ The number of available CPUs to set. Only valid when --memory=MEMORY is specified. Examples: .5, 2, 2.0, 2000m. By default, a new function's available CPUs is determined based on its memory value. When deploying an update that includes memory changes to an existing function, the function's available CPUs will be recalculated based on the new memory unless this flag is specified. When deploying an update that does not include memory changes to an existing function, the function's "available CPUs" setting will keep its old value unless you use this flag to change the setting. |


**Examples:**
```bash
To deploy a function that is triggered by write events on the document
/messages/{pushId}, run:

    $ gcloud functions deploy my_function --runtime=python37 \
        --trigger-event=providers/cloud.firestore/eventTypes/\
    document.write \
        --trigger-resource=projects/project_id/databases/(default)/\
    documents/messages/{pushId}

See https://cloud.google.com/functions/docs/calling for more details of
using other types of resource as triggers.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/deploy)

---
### `gcloud functions describe`

Display details of a Google Cloud Function

Display details of a Google Cloud Function.

**Synopsis:**
```
gcloud functions describe (NAME : --region=REGION) [--v2]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--v2` |  |  | If specified, this command will use Cloud Functions v2 APIs and return the result in the v2 format (See https://cloud.google.com/functions/docs/reference/rest/v2/projects.locations.functions#Function). If not specified, 1st gen and 2nd gen functions will use v1 and v2 APIs respectively and return the result in the corresponding format (For v1 format, see https://cloud.google.com/functions/docs/reference/rest/v1/projects.locations.functions#resource:-cloudfunction). This command conflicts with --no-gen2. If specified with this combination, v2 APIs will be used. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/describe)

---
### `gcloud functions detach`

Detach a Cloud Functions v2 function from its existing environment and make it a native Cloud Run function

Detach a Cloud Functions v2 function from its existing environment and make
it a native Cloud Run function.

**Synopsis:**
```
gcloud functions detach (NAME : --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The name of the Cloud Functions v2 function to detach.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/detach)

---
### `gcloud functions get-iam-policy`

Get IAM policy for a Google Cloud Function

Get IAM policy for a Google Cloud Function.

**Synopsis:**
```
gcloud functions get-iam-policy (NAME : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to get IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Examples:**
```bash
To get the iam policy for FUNCTION-1 run:

    $ gcloud functions get-iam-policy FUNCTION-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/get-iam-policy)

---
### `gcloud functions list`

List Google Cloud Functions

List Google Cloud Functions.

**Synopsis:**
```
gcloud functions list [--regions=REGION,[REGION,...]; default="-"] [--v2]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regions` | REGION,[REGION,...] | - | Regions containing functions to list. By default, functions from the region configured in [functions/region] property are listed. |
| `--v2` |  |  | If specified, this command will use Cloud Functions v2 APIs and return the result in the v2 format (See https://cloud.google.com/functions/docs/reference/rest/v2/projects.locations.functions#Function). If not specified, 1st gen and 2nd gen functions will use v1 and v2 APIs respectively and return the result in the corresponding format (For v1 format, see https://cloud.google.com/functions/docs/reference/rest/v1/projects.locations.functions#resource:-cloudfunction). This command conflicts with --no-gen2. If specified with this combination, v2 APIs will be used. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/list)

---
### `gcloud functions remove-iam-policy-binding`

Removes an IAM policy binding from a Google Cloud Function

Removes an IAM policy binding from a Google Cloud Function.

**Synopsis:**
```
gcloud functions remove-iam-policy-binding (NAME : --region=REGION)
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to remove IAM policy binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove the iam policy binding for FUNCTION-1 from role ROLE-1 for member
MEMBER-1 run:

    $ gcloud functions remove-iam-policy-binding FUNCTION-1 \
        --member=MEMBER-1 --role=ROLE-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/remove-iam-policy-binding)

---
### `gcloud functions remove-invoker-policy-binding`

Removes an invoker binding from the IAM policy of a Google Cloud Function

Removes the invoker role IAM policy binding that allows the specified
member to invoke the specified function.

For Cloud Functions (1st gen), this removes the Cloud Functions Invoker
binding from the IAM policy of the specified function.

For Cloud Functions (2nd gen), this removes the Cloud Run Invoker binding
from the IAM policy of the specified function's underlying Cloud Run
service.

**Synopsis:**
```
gcloud functions remove-invoker-policy-binding (NAME : --region=REGION)
    --member=PRINCIPAL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to remove the invoker binding
from. The arguments in this group can be used to specify the attributes of
this resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove from the IAM policy. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |


**Examples:**
```bash
To remove the invoker role policy binding for FUNCTION-1 for member
MEMBER-1 run:

    $ gcloud functions remove-invoker-policy-binding FUNCTION-1 \
        --member=MEMBER-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/remove-invoker-policy-binding)

---
### `gcloud functions set-iam-policy`

Sets IAM policy for a Google Cloud Function

Sets IAM policy for a Google Cloud Function.

**Synopsis:**
```
gcloud functions set-iam-policy (NAME : --region=REGION) POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Function resource - The Cloud Function name to get IAM policy for. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the function or fully qualified identifier for the function.

     To set the function attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     The Cloud region for the function. Overrides the default
     functions/region property value for this command invocation.

     To set the region attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property functions/region.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.
```

**Examples:**
```bash
To set the iam policy for FUNCTION-1 to the policy defined in POLICY-FILE-1
run:

    $ gcloud functions set-iam-policy FUNCTION-1 POLICY-FILE-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/set-iam-policy)

---