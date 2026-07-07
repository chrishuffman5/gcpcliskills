# gcloud spanner samples

cloud Spanner sample apps

### `gcloud spanner samples backend`

Run the backend gRPC service for the given Cloud Spanner sample app

This command starts the backend gRPC service for the given sample
application. Before starting the service, create the database and load any
initial data with:

    $ gcloud spanner samples init APPNAME --instance-id=INSTANCE_ID

After starting the service, generate traffic with:

    $ gcloud spanner samples workload APPNAME

To run all three steps together, use:

    $ gcloud spanner samples run APPNAME --instance-id=INSTANCE_ID

**Synopsis:**
```
gcloud spanner samples backend APPNAME --instance-id=INSTANCE_ID
    [--database-id=DATABASE_ID] [--duration=DURATION; default="1h"]
    [--port=PORT] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
APPNAME
   The sample app name, e.g. "finance".
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-id` | INSTANCE_ID |  | The Cloud Spanner instance ID for the sample app. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-id` | DATABASE_ID |  | The Cloud Spanner database ID for the sample app. |
| `--duration` | DURATION | 1h | Duration of time allowed to run before stopping the service. |
| `--port` | PORT |  | Port on which to receive gRPC requests. |


**Examples:**
```bash
To run the backend gRPC service for the 'finance' sample app using instance
'my-instance', run:

    $ gcloud spanner samples backend finance --instance-id=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/samples/backend)

---
### `gcloud spanner samples init`

Initialize a Cloud Spanner sample app

This command creates a Cloud Spanner database in the given instance for the
sample app and loads any initial data required by the application.

**Synopsis:**
```
gcloud spanner samples init APPNAME --instance-id=INSTANCE_ID
    [--database-id=DATABASE_ID] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
APPNAME
   The sample app name, e.g. "finance", "finance-graph".
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-id` | INSTANCE_ID |  | The Cloud Spanner instance ID for the sample app. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-id` | DATABASE_ID |  | ID of the new Cloud Spanner database to create for the sample app. |


**Examples:**
```bash
To initialize the 'finance' sample app using instance 'my-instance', run:

    $ gcloud spanner samples init finance --instance-id=my-instance

To initialize the 'finance-graph' sample app using instance 'my-instance',
run:

    $ gcloud spanner samples init finance-graph --instance-id=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/samples/init)

---
### `gcloud spanner samples list`

List available sample applications

List available sample applications.

**Synopsis:**
```
gcloud spanner samples list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list available sample applications, run:

    $ gcloud spanner samples list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/samples/list)

---
### `gcloud spanner samples run`

Run the given Cloud Spanner sample app

Each Cloud Spanner sample application includes a backend gRPC service
backed by a Cloud Spanner database and a workload script that generates
service traffic. This command creates and initializes the Cloud Spanner
database and runs both the backend service and workload script.

These sample apps are open source and available at
https://github.com/GoogleCloudPlatform/cloud-spanner-samples.

To see a list of available sample apps, run:

    $ gcloud spanner samples list

**Synopsis:**
```
gcloud spanner samples run APPNAME --instance-id=INSTANCE_ID [--no-cleanup]
    [--database-id=DATABASE_ID] [--duration=DURATION; default="1h"]
    [--skip-init] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
APPNAME
   The sample app name, e.g. "finance".
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance-id` | INSTANCE_ID |  | The Cloud Spanner instance ID for the sample app. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--cleanup` |  |  | Delete the instance after running the sample app. Enabled by default, use --no-cleanup to disable. |
| `--database-id` | DATABASE_ID |  | ID of the new Cloud Spanner database to create for the sample app. |
| `--duration` | DURATION | 1h | Duration of time allowed to run the sample app before stopping the service. |
| `--skip-init` |  |  | Use an existing database instead of creating a new one. |


**Examples:**
```bash
To run the 'finance' sample app using instance 'my-instance', run:

    $ gcloud spanner samples run finance --instance-id=my-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/samples/run)

---
### `gcloud spanner samples workload`

Generate gRPC traffic for a given sample app's backend service

Before sending traffic to the backend service, create the database and
start the service with:

    $ gcloud spanner samples init APPNAME --instance-id=INSTANCE_ID
    $ gcloud spanner samples backend APPNAME --instance-id=INSTANCE_ID

To run all three steps together, use:

    $ gcloud spanner samples run APPNAME --instance-id=INSTANCE_ID

**Synopsis:**
```
gcloud spanner samples workload APPNAME [--duration=DURATION; default="1h"]
    [--port=PORT] [--target-qps=TARGET_QPS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
APPNAME
   The sample app name, e.g. "finance".
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--duration` | DURATION | 1h | Duration of time allowed to run before stopping the workload. |
| `--port` | PORT |  | Port of the running backend service. |
| `--target-qps` | TARGET_QPS |  | Target requests per second. |


**Examples:**
```bash
To generate traffic for the 'finance' sample app, run:

    $ gcloud spanner samples workload finance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/samples/workload)

---