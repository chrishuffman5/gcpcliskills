# gcloud bigtable app-profiles

manage Cloud Bigtable app profiles

### `gcloud bigtable app-profiles create`

Create a new Bigtable app profile

Create a new Bigtable app profile.

**Synopsis:**
```
gcloud bigtable app-profiles create (APP_PROFILE : --instance=INSTANCE)
    ([--route-any : --restrict-to=[RESTRICT_TO,...] --row-affinity]
      | [--route-to=ROUTE_TO : --transactional-writes])
    [--description=DESCRIPTION] [--force]
    [--data-boost
      --data-boost-compute-billing-owner=DATA_BOOST_COMPUTE_BILLING_OWNER
      | [--priority=PRIORITY : --standard]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
App profile resource - The app profile to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument app_profile on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APP_PROFILE
     ID of the app profile or fully qualified identifier for the app
     profile.

     To set the name attribute:
     + provide the argument app_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the app profile.

     To set the instance attribute:
     + provide the argument app_profile on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--route-any` |  |  | _[Multi Cluster Routing Policy]_ Use Multi Cluster Routing policy. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--restrict-to` | [RESTRICT_TO,...] |  | _[Multi Cluster Routing Policy]_ Cluster IDs to route to using the Multi Cluster Routing Policy. If unset, all clusters in the instance are eligible. |
| `--row-affinity` |  |  | _[Multi Cluster Routing Policy]_ Use row-affinity routing for this app profile. |
| `--route-to` | ROUTE_TO |  | _[Single Cluster Routing Policy]_ Cluster ID to route to using Single Cluster Routing policy. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--transactional-writes` |  |  | _[Single Cluster Routing Policy]_ Allow transactional writes with a Single Cluster Routing policy. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Friendly name of the app profile. |
| `--force` |  |  | Ignore warnings and force create. |


**Examples:**
```bash
To create an app profile with a multi-cluster routing policy, run:

    $ gcloud bigtable app-profiles create my-app-profile-id \
        --instance=my-instance-id --route-any

To create an app profile with a single-cluster routing policy which routes
all requests to my-cluster-id, run:

    $ gcloud bigtable app-profiles create \
        my-single-cluster-app-profile --instance=my-instance-id \
        --route-to=my-cluster-id

To create an app profile with a friendly description, run:

    $ gcloud bigtable app-profiles create my-app-profile-id \
        --instance=my-instance-id --route-any \
        --description="Routes requests for my use case"

To create an app profile with a request priority of PRIORITY_MEDIUM, run:

    $ gcloud bigtable app-profiles create my-app-profile-id \
        --instance=my-instance-id --route-any --priority=PRIORITY_MEDIUM

To create an app profile with row-affinity routing enabled, run:

    $ gcloud bigtable app-profiles create my-app-profile-id \
        --instance=my-instance-id --route-any --row-affinity

To create an app profile with Data Boost enabled which bills usage to the
host project, run:

    $ gcloud bigtable app-profiles create my-app-profile-id \
        --instance=my-instance-id --data-boost \
        --data-boost-compute-billing-owner=HOST_PAYS
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/app-profiles/create)

---
### `gcloud bigtable app-profiles delete`

Delete a Bigtable app profile

Delete a Bigtable app profile.

**Synopsis:**
```
gcloud bigtable app-profiles delete (APP_PROFILE : --instance=INSTANCE)
    [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
App profile resource - The app profile to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument app_profile on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APP_PROFILE
     ID of the app profile or fully qualified identifier for the app
     profile.

     To set the name attribute:
     + provide the argument app_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the app profile.

     To set the instance attribute:
     + provide the argument app_profile on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Ignore warnings and force delete. |


**Examples:**
```bash
To delete an app profile, run:

    $ gcloud bigtable app-profiles delete my-app-profile-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/app-profiles/delete)

---
### `gcloud bigtable app-profiles describe`

Describe an existing Bigtable app profile

Describe an existing Bigtable app profile.

**Synopsis:**
```
gcloud bigtable app-profiles describe (APP_PROFILE : --instance=INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
App profile resource - The app profile to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument app_profile on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APP_PROFILE
     ID of the app profile or fully qualified identifier for the app
     profile.

     To set the name attribute:
     + provide the argument app_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the app profile.

     To set the instance attribute:
     + provide the argument app_profile on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To view an app profile's description, run:

    $ gcloud bigtable app-profiles describe my-app-profile-id \
        --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/app-profiles/describe)

---
### `gcloud bigtable app-profiles list`

List Bigtable app profiles

List Bigtable app profiles.

**Synopsis:**
```
gcloud bigtable app-profiles list --instance=INSTANCE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[This must be specified.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line. |


**Examples:**
```bash
To list all app profiles for an instance, run:

    $ gcloud bigtable app-profiles list --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/app-profiles/list)

---
### `gcloud bigtable app-profiles update`

Update a Bigtable app profile

Update a Bigtable app profile.

**Synopsis:**
```
gcloud bigtable app-profiles update (APP_PROFILE : --instance=INSTANCE)
    [--async] [--description=DESCRIPTION] [--force]
    [--data-boost
      --data-boost-compute-billing-owner=DATA_BOOST_COMPUTE_BILLING_OWNER
      | [--priority=PRIORITY : --standard]]
    [[--route-any : --restrict-to=[RESTRICT_TO,...] --row-affinity]
      | [--route-to=ROUTE_TO : --transactional-writes]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
App profile resource - The app profile to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument app_profile on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APP_PROFILE
     ID of the app profile or fully qualified identifier for the app
     profile.

     To set the name attribute:
     + provide the argument app_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the app profile.

     To set the instance attribute:
     + provide the argument app_profile on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Friendly name of the app profile. |
| `--force` |  |  | Ignore warnings and force update. |


**Examples:**
```bash
To update an app profile to use a multi-cluster routing policy, run:

    $ gcloud bigtable app-profiles update my-app-profile-id \
        --instance=my-instance-id --route-any

To update an app profile to use a single-cluster routing policy that routes
all requests to my-cluster-id and allows transactional writes, run:

    $ gcloud bigtable app-profiles update my-app-profile-id \
        --instance=my-instance-id --route-to=my-cluster-id \
        --transactional-writes

To update the description for an app profile, run:

    $ gcloud bigtable app-profiles update my-app-profile-id \
        --instance=my-instance-id --description="New description"

To update the request priority for an app profile to PRIORITY_LOW, run:

    $ gcloud bigtable app-profiles update my-app-profile-id \
        --instance=my-instance-id --priority=PRIORITY_LOW

To update an app profile to enable row-affinity routing, run:

    $ gcloud bigtable app-profiles update my-app-profile-id \
        --instance=my-instance-id --route-any --row-affinity

To update an app profile to enable Data Boost which bills usage to the host
project, run:

    $ gcloud bigtable app-profiles update my-app-profile-id \
        --instance=my-instance-id --data-boost \
        --data-boost-compute-billing-owner=HOST_PAYS
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/app-profiles/update)

---