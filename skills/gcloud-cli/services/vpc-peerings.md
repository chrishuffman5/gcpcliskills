# gcloud services vpc-peerings

VPC Peerings to various services

### `gcloud services vpc-peerings connect`

Connect to a service via VPC peering for a project network

This command connects a private service connection to a service via a VPC
network.

**Synopsis:**
```
gcloud services vpc-peerings connect --network=NETWORK --ranges=RANGES
    [--async]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project to be peered with the service |
| `--ranges` | RANGES |  | The names of IP CIDR ranges for service to use. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The service to connect to |


**Examples:**
```bash
To connect a network called my-network on the current project to a service
called your-service with IP CIDR ranges google-range-1,google-range-2 for
the service to use, run:

    $ gcloud services vpc-peerings connect --network=my-network \
        --service=your-service --ranges=google-range-1,google-range-2

To run the same command asynchronously (non-blocking), run:

    $ gcloud services vpc-peerings connect --network=my-network \
        --service=your-service --ranges=google-range-1,google-range-2 \
        --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/connect)

---
### `gcloud services vpc-peerings delete`

Delete a private service connection to a service for a project network

This command deletes a private service connection to a service via a VPC
network.

**Synopsis:**
```
gcloud services vpc-peerings delete --network=NETWORK [--async]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project which is peered with the service |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The service to connect to |


**Examples:**
```bash
To delete an existing connection for a network called my-network on the
current project to a service called your-service run:

    $ gcloud services vpc-peerings delete --network=my-network \
        --service=your-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud services vpc-peerings delete --network=my-network \
        --service=your-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/delete)

---
### `gcloud services vpc-peerings disable-vpc-service-controls`

Disable VPC Service Controls for the peering connection

This command disables VPC Service Controls for the peering connection.

The local default route (destination 0.0.0.0/0, next hop default internet
gateway) is recreated in the service producer VPC network. After the route
is recreated, the service producer VPC network cannot import a custom
default route from the peering connection to the customer VPC network.

**Synopsis:**
```
gcloud services vpc-peerings disable-vpc-service-controls --network=NETWORK
    [--async]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project that is peered with the service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The service to enable VPC service controls for. |


**Examples:**
```bash
To disable VPC Service Controls for a connection peering a network called
my-network on the current project to a service called your-service, run:

    $ gcloud services vpc-peerings disable-vpc-service-controls \
        --network=my-network --service=your-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud services vpc-peerings disable-vpc-service-controls \
        --network=my-network --service=your-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/disable-vpc-service-controls)

---
### `gcloud services vpc-peerings enable-vpc-service-controls`

Enable VPC Service Controls for the peering connection

This command configures IPv4 routes and DNS zones applicable to a service
producer VPC network (for example, servicenetworking). The route and DNS
configuration match those recommended for using the
restricted.googleapis.com VIP:

When enabled, Google Cloud makes the following route configuration changes
in the service producer VPC network: Google Cloud removes the IPv4 default
route (destination 0.0.0.0/0, next hop default internet gateway). Google
Cloud then creates an IPv4 route for destination 199.36.153.4/30 using the
default internet gateway next hop.

When enabled, Google Cloud also creates Cloud DNS managed private zones and
authorizes those zones for the service producer VPC network. The zones
include googleapis.com, pkg.dev, gcr.io, and other necessary domains or
host names for Google APIs and services that are compatible with VPC
Service Controls. Record data in the zones resolves all host names to
199.36.153.4, 199.36.153.5, 199.36.153.6, and 199.36.153.7.

When disabled, Google Cloud makes the following route configuration changes
in the service producer VPC network: Google Cloud restores a default route
(destination 0.0.0.0/0, next hop default internet gateway). Google Cloud
also deletes the Cloud DNS managed private zones that provided the host
name overrides.

While enabled, the service producer VPC network can still import static and
dynamic routes from the peered customer network if you enable custom route
export. These custom routes can include a default route. For this reason,
this command is not to be used solely as a means for preventing access to
the internet.

**Synopsis:**
```
gcloud services vpc-peerings enable-vpc-service-controls --network=NETWORK
    [--async]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project that is peered with the service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The service to enable VPC service controls for. |


**Examples:**
```bash
To enable VPC Service Controls for a connection peering a network called
my-network on the current project to a service called your-service, run:

    $ gcloud services vpc-peerings enable-vpc-service-controls \
        --network=my-network --service=your-service

To run the same command asynchronously (non-blocking), run:

    $ gcloud services vpc-peerings enable-vpc-service-controls \
        --network=my-network --service=your-service --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/enable-vpc-service-controls)

---
### `gcloud services vpc-peerings get-vpc-service-controls`

Get VPC state of Service Controls for the peering connection

This command provides the state of the VPC Service Controls for a
connection. The state can be enabled or disabled.

When enabled, Google Cloud makes the following route configuration changes
in the service producer VPC network: Google Cloud removes the IPv4 default
route (destination 0.0.0.0/0, next hop default internet gateway), Google
Cloud then creates an IPv4 route for destination 199.36.153.4/30 using the
default internet gateway next hop.

When enabled, Google Cloud also creates Cloud DNS managed private zones and
authorizes those zones for the service producer VPC network. The zones
include googleapis.com, gcr.io, pkg.dev, notebooks.cloud.google.com,
kernels.googleusercontent.com, backupdr.cloud.google.com, and
backupdr.googleusercontent.com as necessary domains or host names for
Google APIs and services that are compatible with VPC Service Controls.
Record data in the zones resolves all host names to 199.36.153.4,
199.36.153.5, 199.36.153.6, and 199.36.153.7.

When disabled, Google Cloud makes the following route configuration changes
in the service producer VPC network: Google Cloud restores a default route
(destination 0.0.0.0/0, next hop default internet gateway), Google Cloud
also deletes the Cloud DNS managed private zones that provided the host
name overrides.

While enabled, the service producer VPC network can still import static and
dynamic routes from the peered customer network if you enable custom route
export. These custom routes can include a default route. For this reason,
this command is not to be used solely as a means for preventing access to
the internet.

**Synopsis:**
```
gcloud services vpc-peerings get-vpc-service-controls --network=NETWORK
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project that is peered with the service. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE | servicenetworking.googleapis.com | The service to get VPC service controls for. |


**Examples:**
```bash
To get the status of the VPC Service Controls for a connection peering a
network called my-network on the current project to a service called
your-service, run:

    $ gcloud services vpc-peerings get-vpc-service-controls \
        --network=my-network --service=your-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/get-vpc-service-controls)

---
### `gcloud services vpc-peerings list`

List connections to a service via VPC peering for a project network

This command lists connections of a network to a service via VPC peering
for a project.

**Synopsis:**
```
gcloud services vpc-peerings list --network=NETWORK [--service=SERVICE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project to list connections with the service |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service` | SERVICE |  | The service to list connections |


**Examples:**
```bash
To list connections of a network called my-network to a service called
your-service, run:

    $ gcloud services vpc-peerings list --network=my-network \
        --service=your-service

To list connections of a network against all services, run:

    $ gcloud services vpc-peerings list --network=my-network
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/list)

---
### `gcloud services vpc-peerings update`

Update a private service connection to a service for a project network

This command updates a private service connection to a service via a VPC
network.

**Synopsis:**
```
gcloud services vpc-peerings update --network=NETWORK [--async] [--force]
    [--ranges=RANGES]
    [--service=SERVICE; default="servicenetworking.googleapis.com"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--network` | NETWORK |  | The network in the current project to be peered with the service |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If specified, the update call will proceed even if the update can be destructive. |
| `--ranges` | RANGES |  | The names of IP CIDR ranges for service to use. |
| `--service` | SERVICE | servicenetworking.googleapis.com | The service to connect to |


**Examples:**
```bash
To update connection for a network called my-network on the current project
to a service called your-service with IP CIDR ranges
google-range-1,google-range-2 for the service to use, run:

    $ gcloud services vpc-peerings update --network=my-network \
        --service=your-service --ranges=google-range-1,google-range-2

To run the same command asynchronously (non-blocking), run:

    $ gcloud services vpc-peerings update --network=my-network \
        --service=your-service --ranges=google-range-1,google-range-2 \
        --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/update)

---

## `gcloud services vpc-peerings operations` — manage VPC Peering operations
### `gcloud services vpc-peerings operations describe`

Describes an operation resource for a given operation name

This command will return information about an operation given the name of
that operation.

**Synopsis:**
```
gcloud services vpc-peerings operations describe --name=OPERATION_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | OPERATION_NAME |  | The name of operation to describe |


**Examples:**
```bash
To describe an operation resource named operations/abc, run:

    $ gcloud services vpc-peerings operations describe \
        --name=operations/abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/operations/describe)

---
### `gcloud services vpc-peerings operations wait`

Waits for an operation to complete for a given operation name

This command will block until an operation has been marked as complete.

**Synopsis:**
```
gcloud services vpc-peerings operations wait --name=OPERATION_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--name` | OPERATION_NAME |  | The name of operation to wait |


**Examples:**
```bash
To wait on an operation named operations/abc to complete, run:

    $ gcloud services vpc-peerings operations wait --name=operations/abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/vpc-peerings/operations/wait)

---