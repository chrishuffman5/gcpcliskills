# gcloud emulators spanner

manage your local Spanner emulator

### `gcloud emulators spanner env-init`

Print the commands required to export Spanner emulator's env variables

Print the commands required to export Spanner emulator's env variables.

**Synopsis:**
```
gcloud emulators spanner env-init [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To print the env variables exports for a Spanner emulator, run:

    $ gcloud emulators spanner env-init
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/emulators/spanner/env-init)

---
### `gcloud emulators spanner notices`

Print third-party notices for the local Cloud Spanner emulator

Print third-party notices for the local Cloud Spanner emulator.

**Synopsis:**
```
gcloud emulators spanner notices [--use-docker] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--use-docker` |  |  | Use the Cloud Spanner emulator docker image even if the platform has a native binary available in the gcloud CLI. Currently we only provide a native binary for Linux. For other systems, you must install Docker for your platform before starting the emulator. |


**Examples:**
```bash
To print third-party notices for the local Cloud Spanner emulator, run:

    $ gcloud emulators spanner notices
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/emulators/spanner/notices)

---
### `gcloud emulators spanner start`

Start a local Cloud Spanner emulator

This command starts a local Cloud Spanner emulator.

**Synopsis:**
```
gcloud emulators spanner start
    [--enable-fault-injection=ENABLE_FAULT_INJECTION]
    [--host-port=HOST_PORT] [--rest-port=REST_PORT]
    [--use-docker=USE_DOCKER] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-fault-injection` | ENABLE_FAULT_INJECTION |  | If true, the emulator will randomly inject faults into transactions. This facilitates application abort-retry testing. |
| `--host-port` | HOST_PORT |  | The host:port to which the emulator should be bound. The default value is localhost:9010. Note that this port serves gRPC requests. To override the default port serving REST requests, use --rest-port. If using Docker to run the emulator, the host must be specified as an ipaddress. |
| `--rest-port` | REST_PORT |  | The port at which REST requests are served. gcloud uses REST to communicate with the emulator. The default value is 9020. |
| `--use-docker` | USE_DOCKER |  | Use the Cloud Spanner emulator docker image even if the platform has a native binary available in the gcloud CLI. Currently we only provide a native binary for Linux. For other systems, you must install Docker for your platform before starting the emulator. |


**Examples:**
```bash
To start a local Cloud Spanner emulator, run:

    $ gcloud emulators spanner start
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/emulators/spanner/start)

---