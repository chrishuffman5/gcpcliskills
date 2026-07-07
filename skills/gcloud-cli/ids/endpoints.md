# gcloud ids endpoints

create and manage Cloud IDS Endpoints

### `gcloud ids endpoints create`

Create a Cloud IDS endpoint

Create an endpoint for the specified VPC network. Successful creation of an
endpoint results in an endpoint in READY state. Check the progress of
endpoint creation by using gcloud alpha ids endpoints list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud ids endpoints create (ENDPOINT : --zone=ZONE) --network=NETWORK
    --severity=SEVERITY [--async] [--description=DESCRIPTION]
    [--enable-traffic-logs] [--labels=[KEY=VALUE,...]]
    [--max-wait=MAX_WAIT; default="60m"]
    [--threat-exceptions=[exc1,exc2,...,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - endpoint. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the endpoint.

     To set the zone attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | Name of the VPC network to monitor |
| `--severity` | one of: INFORMATIONAL, LOW, MEDIUM, HIGH, CRITICAL |  | Minimum severity of threats to report on. SEVERITY must be one of: INFORMATIONAL, LOW, MEDIUM, HIGH, CRITICAL. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Description of the endpoint. |
| `--enable-traffic-logs` |  |  | Whether to enable traffic logs on the endpoint. Enabling traffic logs can generate a large number of logs which can increase costs in Cloud Logging. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--threat-exceptions` | [exc1,exc2,...,...] |  | List of threat IDs to be excepted from alerting. Passing empty list clears the exceptions. |


**Examples:**
```bash
To create an endpoint called my-endpoint for VPC network my-net, in zone
us-central1-a, alerting on LOW threats or higher, run:

    $ gcloud ids endpoints create my-endpoint --network=my-net \
        --zone=us-central1-a --project=my-project --severity=LOW

To create an endpoint called my-endpoint for VPC network my-net, in zone
us-central1-a, alerting on LOW threats or higher, excluding threat IDs 1000
and 2000, run:

    $ gcloud ids endpoints create my-endpoint --network=my-net \
        --zone=us-central1-a --project=my-project --severity=LOW \
        --threat-exceptions=1000,2000
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ids/endpoints/create)

---
### `gcloud ids endpoints delete`

Delete a Cloud IDS endpoint

Delete a Cloud IDS endpoint.

**Synopsis:**
```
gcloud ids endpoints delete (ENDPOINT : --zone=ZONE) [--async]
    [--max-wait=MAX_WAIT; default="60m"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - endpoint. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the endpoint.

     To set the zone attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |


**Examples:**
```bash
To delete an endpoint called my-ep in project my-project and zone
us-central1-a, run:

    $ gcloud ids endpoints delete my-ep --project=my-project \
        --zone=us-central1-a

OR

    $ gcloud ids endpoints delete \
        projects/myproject/locations/us-central1-a/endpoints/my-ep
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ids/endpoints/delete)

---
### `gcloud ids endpoints describe`

Describe a Cloud IDS endpoint

Describe a Cloud IDS endpoint.

**Synopsis:**
```
gcloud ids endpoints describe (ENDPOINT : --zone=ZONE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - endpoint. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the endpoint.

     To set the zone attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Examples:**
```bash
To get a description of a endpoint called my-ep in project my-project and
zone us-central1-a, run:

    $ gcloud ids endpoints describe my-ep --project=my-project \
        --zone=us-central1-a

OR

    $ gcloud ids endpoints describe \
        projects/myproject/locations/us-central1-a/endpoints/my-ep
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ids/endpoints/describe)

---
### `gcloud ids endpoints list`

List Cloud IDS endpoints

List Cloud IDS endpoints in a project.

**Synopsis:**
```
gcloud ids endpoints list [--project=PROJECT_ID] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
    $ gcloud ids endpoints list --project=my-project

The project is automatically read from the core/project property if it is
defined.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ids/endpoints/list)

---
### `gcloud ids endpoints update`

Update an existing Cloud IDS endpoint

Update the endpoint for the specified VPC network. Check the progress of
endpoint update by using gcloud alpha ids endpoints list.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud ids endpoints update (ENDPOINT : --zone=ZONE) [--async]
    [--max-wait=MAX_WAIT; default="60m"]
    [--threat-exceptions=[exc1,exc2,...,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Endpoint resource - endpoint. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument endpoint on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ENDPOINT
     ID of the endpoint or fully qualified identifier for the endpoint.

     To set the endpoint attribute:
     + provide the argument endpoint on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     Zone of the endpoint.

     To set the zone attribute:
     + provide the argument endpoint on the command line with a fully
       specified name;
     + provide the argument --zone on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--max-wait` | MAX_WAIT | 60m | Time to synchronously wait for the operation to complete, after which the operation continues asynchronously. Ignored if --no-async isn't specified. See $ gcloud topic datetimes for information on time formats. |
| `--threat-exceptions` | [exc1,exc2,...,...] |  | List of threat IDs to be excepted from alerting. Passing empty list clears the exceptions. |


**Examples:**
```bash
To update an endpoint called my-endpoint, excluding threat IDs 1000 and
2000, run:

    $ gcloud ids endpoints update my-endpoint \
        --threat-exceptions=1000,2000

To update an endpoint called my-endpoint, clearing the excluded threat
list, run:

    $ gcloud ids endpoints update my-endpoint --threat-exceptions=
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ids/endpoints/update)

---