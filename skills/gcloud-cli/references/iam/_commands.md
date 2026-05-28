# gcloud iam (top-level commands)

### `gcloud iam list-grantable-roles`

List IAM grantable roles for a resource

This command displays the list of grantable roles for a resource. The
resource can be referenced either via the full resource name or via a URI.
User can then add IAM policy bindings to grant the roles.

**Synopsis:**
```
gcloud iam list-grantable-roles RESOURCE [--filter=EXPRESSION]
    [--page-size=PAGE_SIZE; default=300] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE
   The full resource name or URI to get the list of roles for.

   See "Resource Names"
   (https://cloud.google.com/apis/design/resource_names) for details. To
   get a URI from most list commands in gcloud, pass the --uri flag. For
   example:

       $ gcloud compute instances list --project prj --uri \
       https://compute.googleapis.com/compute/v1/projects/prj/zones/us-east1-c/instances/i1 \
       https://compute.googleapis.com/compute/v1/projects/prj/zones/us-east1-d/instances/i2
```

**Examples:**
```bash
List grantable roles for a project:

    $ gcloud iam list-grantable-roles \
        //cloudresourcemanager.googleapis.com/projects/PROJECT_ID

List grantable roles for a resource identified via full resource name:

    $ gcloud iam list-grantable-roles \
        //compute.googleapis.com/projects/example-project/zones/\
    us-central1-f/instances/example-instance

List grantable roles for a resource identified via URI:

    $ gcloud iam list-grantable-roles \
        https://www.googleapis.com/compute/v1/projects/example-project/\
    zones/us-central1-f/instances/example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/list-grantable-roles)

---
### `gcloud iam list-testable-permissions`

List IAM testable permissions for a resource

Testable permissions mean the permissions that user can add or remove in a
role at a given resource. The resource can be referenced either via the
full resource name or via a URI.

**Synopsis:**
```
gcloud iam list-testable-permissions RESOURCE [--filter=EXPRESSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE
   The full resource name or URI to get the testable permissions for.

   See "Resource Names"
   (https://cloud.google.com/apis/design/resource_names) for details. To
   get a URI from most list commands in gcloud, pass the --uri flag. For
   example:

       $ gcloud compute instances list --project prj --uri \
       https://compute.googleapis.com/compute/v1/projects/prj/zones/us-east1-c/instances/i1 \
       https://compute.googleapis.com/compute/v1/projects/prj/zones/us-east1-d/instances/i2
```

**Examples:**
```bash
List testable permissions for a resource identified via full resource name:

    $ gcloud iam list-testable-permissions \
        //cloudresourcemanager.googleapis.com/organizations/1234567

List testable permissions for a resource identified via URI:

    $ gcloud iam list-testable-permissions \
        https://www.googleapis.com/compute/v1/projects/example-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/list-testable-permissions)

---