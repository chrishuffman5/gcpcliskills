# gcloud bms networks

manage networks in Bare Metal Solution

### `gcloud bms networks describe`

Describe a Bare Metal solution network

Describe a Bare Metal Solution network.

**Synopsis:**
```
gcloud bms networks describe (NETWORK : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - network. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Examples:**
```bash
To get a description of a network called my-network in project my-project
and region us-central1, run:

    $ gcloud bms networks describe my-network --project=my-project \
        --region=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/networks/describe)

---
### `gcloud bms networks list`

List Bare Metal Solution networks in a project

List Bare Metal Solution networks in a project.

**Synopsis:**
```
gcloud bms networks list [--region=REGION] [--filter=EXPRESSION]
    [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list networks in the region us-central1, run:

    $ gcloud bms networks list --region=us-central1

Or:

To list all networks in the project, run:

    $ gcloud bms networks list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/networks/list)

---
### `gcloud bms networks list-ip-reservations`

List IP range reservations for Bare Metal Solution networks in a project

List IP range reservations for Bare Metal Solution networks in a project.

**Synopsis:**
```
gcloud bms networks list-ip-reservations [--region=REGION]
    [--filter=EXPRESSION] [--limit=LIMIT] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | _[* set the property core/project.]_ ID of the region or fully qualified identifier for the region. To set the region attribute: + provide the argument --region on the command line. |


**Examples:**
```bash
To list IP range reservations for networks in the region us-central1, run:

    $ gcloud bms networks list-ip-reservations --region=us-central1

Or:

To list all IP range reservations in the project, run:

    $ gcloud bms networks list-ip-reservations
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/networks/list-ip-reservations)

---
### `gcloud bms networks rename`

Rename a Bare Metal Solution network

Rename a Bare Metal Solution network.

**Synopsis:**
```
gcloud bms networks rename (NETWORK : --region=REGION) --new-name=NEW_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - network. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--new-name` | NEW_NAME |  | New network name for renaming an already existing network. |


**Examples:**
```bash
To rename a network my-network to my-new-network-name in region
us-central1, run:

    $ gcloud bms networks rename my-network \
        --new-name=my-new-network-name --region=us-central1 \
        --project=bms-example-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/networks/rename)

---
### `gcloud bms networks update`

Update a Bare Metal Solution network

Update a Bare Metal Solution network.

This call returns immediately, but the update operation may take several
minutes to complete. To check if the operation is complete, use the
describe command for the network.

**Synopsis:**
```
gcloud bms networks update (NETWORK : --region=REGION) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--add-ip-range-reservation=[PROPERTY=VALUE,...]
      | --clear-ip-range-reservations
      | --remove-ip-range-reservation=[PROPERTY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network resource - network. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument network on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK
     ID of the network or fully qualified identifier for the network.

     To set the network attribute:
     + provide the argument network on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument network on the command line with a fully
       specified name;
     + provide the argument --region on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update an network called my-network in region us-central1 with a new
label key1=value1, run:

    $ gcloud bms networks update my-network --region=us-central1 \
        --update-labels=key1=value1

To clear all labels, run:

    $ gcloud bms networks update my-network --region=us-central1 \
        --clear-labels
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/networks/update)

---