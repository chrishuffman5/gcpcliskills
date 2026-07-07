# gcloud compute target-instances

read and manipulate Compute Engine virtual target instances

### `gcloud compute target-instances create`

Create a target instance for handling traffic from a forwarding rule

gcloud compute target-instances create is used to create a target instance
for handling traffic from one or more forwarding rules. Target instances
are ideal for traffic that should be managed by a single source. For more
information on target instances, see
https://cloud.google.com/compute/docs/protocol-forwarding/#targetinstances

**Synopsis:**
```
gcloud compute target-instances create NAME --instance=INSTANCE
    [--description=DESCRIPTION] [--instance-zone=INSTANCE_ZONE]
    [--network=NETWORK] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target instance to operate on.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | The name of the virtual machine instance that will handle the traffic. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An optional, textual description of the target instance. |
| `--instance-zone` | INSTANCE_ZONE |  | Zone of the instance to operate on. If not specified, it will be set to the same as zone. Overrides the default compute/zone property value for this command invocation. |
| `--network` | NETWORK |  | Network that this target instance applies to. This is only necessary if the corresponding instance has multiple network interfaces. If not specified, the default network interface will be used. |
| `--zone` | ZONE |  | Zone of the target instance to operate on. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-instances/create)

---
### `gcloud compute target-instances delete`

Delete target instances

gcloud compute target-instances delete deletes one or more Compute Engine
target instances. Target instances can be deleted only if they are not
being used by any other resources like forwarding rules.

**Synopsis:**
```
gcloud compute target-instances delete NAME [NAME ...] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME [NAME ...]
   Names of the target instances to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the target instances to delete. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-instances/delete)

---
### `gcloud compute target-instances describe`

Describe a target instance

gcloud compute target-instances describe displays all data associated with
a Compute Engine target instance in a project.

**Synopsis:**
```
gcloud compute target-instances describe NAME [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target instance to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | Zone of the target instance to describe. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-instances/describe)

---
### `gcloud compute target-instances list`

List Google Compute Engine target instances

gcloud compute target-instances list displays all Google Compute Engine
target instances in a project.

By default, target instances from all zones are listed. The results can be
narrowed down using a filter: --filter="zone:( ZONE ... )".

**Synopsis:**
```
gcloud compute target-instances list [NAME ...]
    [--regexp=REGEXP, -r REGEXP] [--zones=ZONE,[ZONE,...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[NAME ...]
   (DEPRECATED) If provided, show details for the specified names and/or
   URIs of resources.

   Argument NAME is deprecated. Use --filter="name=( 'NAME' ... )"
   instead.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--regexp` | REGEXP, -r REGEXP |  | (DEPRECATED) Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. Flag --regexp is deprecated. Use --filter="name~'REGEXP'" instead. |
| `--zones` | ZONE,[ZONE,...] |  | If provided, only resources from the given zones are queried. |


**Examples:**
```bash
To list all target instances in a project in table form, run:

    $ gcloud compute target-instances list

To list the URIs of all target instances in a project, run:

    $ gcloud compute target-instances list --uri

To list all target instances in the us-central1-b and europe-west1-d zones,
run:

    $ gcloud compute target-instances list \
        --filter="zone:( us-central1-b europe-west1-d )"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-instances/list)

---
### `gcloud compute target-instances update`

Update a Compute Engine target instance

gcloud compute target-instances update updates a Compute Engine target
instance.

**Synopsis:**
```
gcloud compute target-instances update NAME
    [--security-policy=SECURITY_POLICY]
    [--security-policy-region=SECURITY_POLICY_REGION] [--zone=ZONE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Name of the target instance to update.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--security-policy` | SECURITY_POLICY |  | The security policy that will be set for this target instance. To remove the policy from this target instance set the policy to an empty string. |
| `--security-policy-region` | SECURITY_POLICY_REGION |  | Region of the security policy to operate on. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE |  | Zone of the target instance to update. If not specified and the compute/zone property isn't set, you might be prompted to select a zone (interactive mode only). To avoid prompting when this flag is omitted, you can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To update the security policy run this:

    $ gcloud compute target-instances update TARGET_INSTANCE \
        --security-policy='my-policy'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/target-instances/update)

---