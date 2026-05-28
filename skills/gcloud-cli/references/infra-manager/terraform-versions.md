# gcloud infra-manager terraform-versions

manage Terraform version resources

### `gcloud infra-manager terraform-versions describe`

Describe Terraform versions

Describe a Terraform version

**Synopsis:**
```
gcloud infra-manager terraform-versions describe
    (TERRAFORM_VERSION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
TerraformVersion resource - The Terraform version to describe The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument terraform_version on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TERRAFORM_VERSION
     ID of the terraformVersion or fully qualified identifier for the
     terraformVersion.

     To set the terraform_version attribute:
     + provide the argument terraform_version on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     locations TBD

     To set the location attribute:
     + provide the argument terraform_version on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property infra-manager/location.
```

**Examples:**
```bash
To describe a Terraform version 1.5.7 in project p1 at location
us-central1, run:

    $ gcloud infra-manager terraform-versions describe \
        projects/p1/locations/us-central1/terraformVersions/1.5.7
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/terraform-versions/describe)

---
### `gcloud infra-manager terraform-versions list`

List Terraform versions

**Synopsis:**
```
gcloud infra-manager terraform-versions list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property infra-manager/location. |


**Examples:**
```bash
To list all Terraform versions at location us-central1, run:

    $ gcloud infra-manager terraform-versions list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/infra-manager/terraform-versions/list)

---