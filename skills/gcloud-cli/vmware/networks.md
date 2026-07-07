# gcloud vmware networks

manage VMware Engine networks in Google Cloud VMware Engine

### `gcloud vmware networks create`

Create a Google Cloud VMware Engine network

Create a VMware Engine network. VMware Engine network creation is
considered finished when the VMware Engine network is in ACTIVE state.
Check the progress of a VMware Engine network creation using gcloud vmware
networks list.

**Synopsis:**
```
gcloud vmware networks create (VMWARE_ENGINE_NETWORK : --location=LOCATION)
    --type=TYPE [--async] [--description=DESCRIPTION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine network resource - vmware_engine_network. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument vmware_engine_network on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VMWARE_ENGINE_NETWORK
     ID of the VMware Engine network or fully qualified identifier for the
     VMware Engine network.

     To set the vmware-engine-network attribute:
     + provide the argument vmware_engine_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument vmware_engine_network on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default) or a region.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--type` | one of: LEGACY Network type used by private clouds created in projects without a network of type STANDARD |  | Type of the VMware Engine network. TYPE must be one of: LEGACY Network type used by private clouds created in projects without a network of type STANDARD. This network type is only used for new PCs in existing projects that continue to use LEGACY network. A VMware Engine network of type LEGACY is a regional resource. STANDARD Standard network type used for private cloud connectivity. A VMware Engine network of type STANDARD is a global resource. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the VMware Engine network. |


**Examples:**
```bash
To create a VMware Engine network of type STANDARD, run:

    $ gcloud vmware networks create my-network --type=STANDARD \
        --location=global --project=my-project

Or:

    $ gcloud vmware networks create my-network --type=STANDARD

In the second example, the project is taken from gcloud properties
core/project and the location is taken as global.

To create a VMware Engine network of type LEGACY in the us-west2 region,
run:

    $ gcloud vmware networks create my-network --type=LEGACY \
        --location=us-west2 --project=my-project

Or:

    $ gcloud vmware networks create my-network --type=LEGACY \
        --location=us-west2

In the last example, the project is taken from gcloud properties
core/project. For VMware Engine networks of type LEGACY, you must always
specify a region as the location.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/networks/create)

---
### `gcloud vmware networks delete`

Delete a Google Cloud VMware Engine network

Delete a VMware Engine network.

**Synopsis:**
```
gcloud vmware networks delete (VMWARE_ENGINE_NETWORK : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine network resource - vmware_engine_network. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument vmware_engine_network on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VMWARE_ENGINE_NETWORK
     ID of the VMware Engine network or fully qualified identifier for the
     VMware Engine network.

     To set the vmware-engine-network attribute:
     + provide the argument vmware_engine_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument vmware_engine_network on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default) or a region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |


**Examples:**
```bash
To delete a network called my-network of type STANDARD in project
my-project and region global, run:

    $ gcloud vmware networks delete my-network --location=global \
        --project=my-project

Or:

    $ gcloud vmware networks delete my-network

In the second example, the project is taken from gcloud properties
core/project and the location is taken as global.

To delete a network called my-network of type LEAGACY in project my-project
and region us-west2, run:

    $ gcloud vmware networks delete my-network --location=us-west2 \
        --project=my-project

Or:

    $ gcloud vmware networks delete my-network --location=us-west2

In the last example, the project is taken from gcloud properties
core/project. For VMware Engine networks of type LEGACY, you must always
specify a region as the location.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/networks/delete)

---
### `gcloud vmware networks describe`

Describe a Google Cloud VMware Engine network

Describe a VMware Engine network.

**Synopsis:**
```
gcloud vmware networks describe
    (VMWARE_ENGINE_NETWORK : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine network resource - vmware_engine_network. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument vmware_engine_network on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VMWARE_ENGINE_NETWORK
     ID of the VMware Engine network or fully qualified identifier for the
     VMware Engine network.

     To set the vmware-engine-network attribute:
     + provide the argument vmware_engine_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument vmware_engine_network on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default) or a region.
```

**Examples:**
```bash
To get a description of a network called my-network of type STANDARD in
project my-project and region global, run:

    $ gcloud vmware networks describe my-network --location=global \
        --project=my-project

Or:

    $ gcloud vmware networks describe my-network

In the second example, the project is taken from gcloud properties
core/project and the location is taken as global.

To get a description of a network called my-network of type LEGACY in
project my-project and region us-west2, run:

    $ gcloud vmware networks describe my-network --location=us-west2 \
        --project=my-project

Or:

    $ gcloud vmware networks describe my-network --location=us-west2

In the last example, the project is taken from gcloud properties
core/project. For VMware Engine networks of type LEGACY, you must always
specify a region as the location.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/networks/describe)

---
### `gcloud vmware networks list`

List Google Cloud VMware Engine networks

List VMware Engine networks.

**Synopsis:**
```
gcloud vmware networks list [--location=LOCATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set location as 'global' (default) or a region. |


**Examples:**
```bash
To list VMware Engine networks of type STANDARD in your project, run:

    $ gcloud vmware networks list --location=global --project=my-project

Or:

    $ gcloud vmware networks list

In the second example, the project is taken from gcloud properties
core/project and the location is taken as global.

To list VMware Engine networks of type LEGACY in the location us-west2 in
your project, run:

    $ gcloud vmware networks list --location=us-west2 \
        --project=my-project

Or:

    $ gcloud vmware networks list --location=us-west2

In the last example, the project is taken from gcloud properties
core/project. For VMware Engine networks of type LEGACY, you must always
specify a region as the location.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/networks/list)

---
### `gcloud vmware networks update`

Update a Google Cloud VMware Engine network

Update a VMware Engine network.

**Synopsis:**
```
gcloud vmware networks update (VMWARE_ENGINE_NETWORK : --location=LOCATION)
    [--async] [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VMware Engine network resource - vmware_engine_network. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument vmware_engine_network on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  VMWARE_ENGINE_NETWORK
     ID of the VMware Engine network or fully qualified identifier for the
     VMware Engine network.

     To set the vmware-engine-network attribute:
     + provide the argument vmware_engine_network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The resource name of the location.

     To set the location attribute:
     + provide the argument vmware_engine_network on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + set location as 'global' (default) or a region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is True. Enabled by default, use --no-async to disable. |
| `--description` | DESCRIPTION |  | Text describing the VMware Engine network |


**Examples:**
```bash
To update a network named my-network of type STANDARD by changing its
description to Example description, run:

    $ gcloud vmware networks update my-network --location=global \
        --project=my-project --description='Example description'

Or:

    $ gcloud vmware networks update my-network \
        --description='Example description'

In the second example, the project is taken from gcloud properties
core/project and the location is taken as global.

To update a network named my-network of type LEGACY by changing its
description to Example description, run:

    $ gcloud vmware networks update my-network --location=us-west2 \
        --project=my-project --description='Example description'

Or:

    $ gcloud vmware networks update my-network --location=us-west2 \
        --description='Example description'

In the last example, the project is taken from gcloud properties
core/project. For VMware Engine networks of type LEGACY, you must always
specify a region as the location.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/vmware/networks/update)

---