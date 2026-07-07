# gcloud design-center spaces

manage space resources

### `gcloud design-center spaces create`

Create a space

Create a space.

**Synopsis:**
```
gcloud design-center spaces create (SPACE : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--enable-gcp-shared-templates] [--gcs-bucket=GCS_BUCKET]
    [--tags=[TAGS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - Identifier. The space name. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the space resource.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description for the space. |
| `--display-name` | DISPLAY_NAME |  | Display name for the space. |
| `--gcs-bucket` | GCS_BUCKET |  | _[Flag to enable Google opinionated shared templates.]_ An existing Google Cloud Storage bucket that you want to use instead of creating a new bucket during ADC setup. If not provided, a default bucket is created during setup. The bucket must exist in the same project as the space. If the bucket name does not exist in the same project as the space, the request fails with an INVALID_ARGUMENT error. If you do not have access to the bucket, the request fails with a PERMISSION_DENIED error. Format: {$bucket_name} For example, if the Cloud Storage bucket URI is gs:\/\/{$bucket_name}, the format is {$bucket_name}. |
| `--tags` | [TAGS,...] |  | _[Flag to enable Google opinionated shared templates.]_ Tags are key/values bound to space resource. Example: "123/environment": "production" "123/costCenter": "marketing". For more information on tag creation and management, see https://cloud.google.com/resource-manager/docs/tags/tags-overview. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --tags=string=string JSON Example: --tags='{"string": "string"}' File Example: --tags=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create the space my-space in project my-project and location
us-central1, run:

    $ gcloud design-center spaces create my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces create \
        projects/my-project/locations/us-central1/spaces/my-space

To create the space my-space in project my-project and location us-central1
with display name, description, and enable google templates, run:

    $ gcloud design-center spaces create my-space --project=my-project \
        --location=us-central1 --display-name=my-display-name \
        --description=my-description --enable-gcp-shared-templates
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/create)

---
### `gcloud design-center spaces delete`

Delete a space

Delete a space.

**Synopsis:**
```
gcloud design-center spaces delete (SPACE : --location=LOCATION) [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - The space name. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the space resource.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set to true, the space's children are also deleted. If false, the space is only deleted if it has no children. |


**Examples:**
```bash
To delete the space my-space in project my-project and location
us-central1, run:

    $ gcloud design-center spaces delete my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces delete \
        projects/my-project/locations/us-central1/spaces/my-space

If your space contains child resources such as application templates,
applications, catalogs, shared templates, force delete the space. To force
delete the space my-space in project my-project and location us-central1,
run:

    $ gcloud design-center spaces delete my-space --project=my-project \
        --location=us-central1 --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/delete)

---
### `gcloud design-center spaces describe`

Describe a space

Describe a space.

**Synopsis:**
```
gcloud design-center spaces describe (SPACE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - The space name. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the space resource.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the space my-space in project my-project and location
us-central1, run:

    $ gcloud design-center spaces describe my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces describe \
        projects/my-project/locations/us-central1/spaces/my-space
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/describe)

---
### `gcloud design-center spaces get-iam-policy`

Get the IAM policy for a Design Center space

Get the IAM policy for a Design Center space.

Returns an empty policy if the space does not have an existing IAM policy
set.

**Synopsis:**
```
gcloud design-center spaces get-iam-policy (SPACE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - The Space ID. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the space.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the space IAM policy for the Space my-space in project my-project in
location us-central1, run:

    $ gcloud design-center spaces get-iam-policy my-space \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/get-iam-policy)

---
### `gcloud design-center spaces list`

List spaces

List spaces.

**Synopsis:**
```
gcloud design-center spaces list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all spaces in project my-project and location us-central1, run:

    $ gcloud design-center spaces list --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces list \
        --location=projects/my-project/locations/us-central1

To filter and list spaces that contains my-space prefix in the display name
in project my-project and location us-central1, run:

    $ gcloud design-center spaces list --project=my-project \
        --location=us-central1 --filter="displayName:my-space*"

To list up to 10 spaces in project my-project and location us-central1,
run:

    $ gcloud design-center spaces list --project=my-project \
        --location=us-central1 --limit=10

To list up to 5 pages of spaces in project my-project and location
us-central1, run:

    $ gcloud design-center spaces list --project=my-project \
        --location=us-central1 --page-size=5

To list spaces sorted by display name in project my-project and location
us-central1, run:

    $ gcloud design-center spaces list --project=my-project \
        --location=us-central1 --sort-by=displayName
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/list)

---
### `gcloud design-center spaces set-iam-policy`

Set the IAM policy for a Design Center space as defined in a JSON/YAML file

Set the IAM policy for a Design Center space as defined in a JSON/YAML
file.

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud design-center spaces set-iam-policy (SPACE : --location=LOCATION)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - The Space ID. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the space.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To set the space IAM policy using a json file 'my_policy.json' for the
Space my-space in project my-project and location us-central1, run:

    $ gcloud design-center spaces set-iam-policy my-space \
        --location=us-central1 --project=my-project \
        /path/to/my_policy.json

To set the space IAM policy using a yaml file 'my_policy.yaml for the Space
my-space in project my-project and location us-central1, run:

    $ gcloud design-center spaces set-iam-policy my-space \
        --location=us-central1 --project=my-project \
        /path/to/my_policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/set-iam-policy)

---
### `gcloud design-center spaces test-iam-permissions`

Test IAM permissions for a Design Center space

Tests the IAM permissions that a caller has on a Design Center space.

Returns an empty set of permissions if the space does not exist.

Note: This operation is designed to be used for building permission-aware
UIs and command-line tools, not for authorization checking. This operation
may "fail open" without warning.

**Synopsis:**
```
gcloud design-center spaces test-iam-permissions
    (SPACE : --location=LOCATION) --permissions=[PERMISSION,...]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - The Space ID. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the space.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--permissions` | [PERMISSION,...] |  | The set of permissions to check for the resource. |


**Examples:**
```bash
To test if the caller has the designcenter.spaces.get and
designcenter.spaces.update permissions on the Space my-space in project
my-project and location us-central1, run:

    $ gcloud design-center spaces test-iam-permissions my-space \
        --location=us-central1 --project=my-project \
        --permissions=designcenter.spaces.get,designcenter.spaces.update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/test-iam-permissions)

---
### `gcloud design-center spaces update`

Update a space

Update a space.

**Synopsis:**
```
gcloud design-center spaces update (SPACE : --location=LOCATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--[no-]enable-gcp-shared-templates] [--gcs-bucket=GCS_BUCKET]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Space resource - Identifier. The space name. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument space on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SPACE
     ID of the space or fully qualified identifier for the space.

     To set the space attribute:
     + provide the argument space on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the space resource.

     To set the location attribute:
     + provide the argument space on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Description for the space. |
| `--display-name` | DISPLAY_NAME |  | Display name for the space. |
| `--gcs-bucket` | GCS_BUCKET |  | _[--no-enable-gcp-shared-templates to disable.]_ An existing Google Cloud Storage bucket that you want to use instead of creating a new bucket during ADC setup. If not provided, a default bucket is created during setup. The bucket must exist in the same project as the space. If the bucket name does not exist in the same project as the space, the request fails with an INVALID_ARGUMENT error. If you do not have access to the bucket, the request fails with a PERMISSION_DENIED error. Format: {$bucket_name} For example, if the Cloud Storage bucket URI is gs:\/\/{$bucket_name}, the format is {$bucket_name}. |


**Examples:**
```bash
To update the display name to My New Space Name in the space my-space in
project my-project and location us-central1, run:

    $ gcloud design-center spaces update my-space --project=my-project \
        --location=us-central1 --display-name="My New Space Name"

Or run:

    $ gcloud design-center spaces update \
        projects/my-project/locations/us-central1/spaces/my-space \
        --display-name="My New Space Name"

To disable google templates in the space my-space in project my-project and
location us-central1 , run:

    $ gcloud design-center spaces update my-space --project=my-project \
        --location=us-central1 --no-enable-gcp-shared-templates

To update the display name, description, and enable google templates in the
space my-space in project my-project and location us-central1, run:

    $ gcloud design-center spaces update my-space --project=my-project \
        --location=us-central1 --display-name="My Updated Space" \
        --description="Updated description" \
        --enable-gcp-shared-templates
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/update)

---

## `gcloud design-center spaces application-templates` — manage application template resources
### `gcloud design-center spaces application-templates commit`

Commit an application template

Commits an application template to create a new revision.

**Synopsis:**
```
gcloud design-center spaces application-templates commit
    (APPLICATION_TEMPLATE : --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApplicationTemplate resource - The name of the application template. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the applicationTemplate or fully qualified identifier for the
     applicationTemplate.

     To set the application_template attribute:
     + provide the argument application_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the applicationTemplate resource.

     To set the location attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the applicationTemplate resource.

     To set the space attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To commit the application template my-app-template in space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates commit \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates commit \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/commit)

---
### `gcloud design-center spaces application-templates create`

Create an application template

Create an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates create
    (APPLICATION_TEMPLATE : --location=LOCATION --space=SPACE)
    [--application-parameters=[key=KEY],[value=VALUE]]
    [--composition-type=COMPOSITION_TYPE] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME]
    [--root-input-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE]]
    [--root-output-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApplicationTemplate resource - Identifier. Application template name. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the applicationTemplate or fully qualified identifier for the
     applicationTemplate.

     To set the application_template attribute:
     + provide the argument application_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the applicationTemplate resource.

     To set the location attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the applicationTemplate resource.

     To set the space attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-parameters` | [key=KEY],[value=VALUE] |  | Parameters to apply to all components in an application. You can specify projectID and region. key The key of the parameter. value The value of the parameter. Shorthand Example: --application-parameters=key=string,value={...} --application-parameters=key=string,value={...} JSON Example: --application-parameters='[{"key": "string", "value": {...}}]' File Example: --application-parameters=path_to_file.(yaml\|json) |
| `--composition-type` | one of: composite ApplicationCompositionType is COMPOSITE |  | The composition type of the applicationTemplate: STANDARD OR COMPOSITE. This is a create time only param. In future, we may support conversion from STANDARD to COMPOSITE. COMPOSITION_TYPE must be one of: composite ApplicationCompositionType is COMPOSITE. The template is composed of STANDARD applicationTemplate(s) and might be having multiple root modules in terraform code. standard ApplicationCompositionType is STANDARD. The applicationTemplate or application is composed of components only of type service/workload/asset and has a single root module in terraform code. |
| `--description` | DESCRIPTION |  | Application template description. |
| `--display-name` | DISPLAY_NAME |  | Application template display name. |
| `--root-input-variables` | [componentUri=COMPONENTURI],[variable=VARIABLE] |  | Root level input variables of the application template. componentUri Component to which this variable belongs. variable Name of the variable. Shorthand Example: --root-input-variables=componentUri=string,variable=string --root-input-variables=componentUri=string,variable=string JSON Example: --root-input-variables='[{"componentUri": "string", "variable": "string"}]' File Example: --root-input-variables=path_to_file.(yaml\|json) |
| `--root-output-variables` | [componentUri=COMPONENTURI],[variable=VARIABLE] |  | Root level output variables of the application template. componentUri Component to which this variable belongs. variable Name of the variable. Shorthand Example: --root-output-variables=componentUri=string,variable=string --root-output-variables=componentUri=string,variable=string JSON Example: --root-output-variables='[{"componentUri": "string", "variable": "string"}]' File Example: --root-output-variables=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create the application template my-app-template in space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates create \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates create \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template

To create the application template my-app-template with a display name of
My App Template and description of My app template description, run:

    $ gcloud design-center spaces application-templates create \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 --display-name="My App Template" \
        --description="My app template description"

To create the application template my-app-template with application
parameters key-value pair of project_id:my-project and region:us-central1,
run the following shorthand example:

    $ gcloud design-center spaces application-templates create \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 \
        --application-parameters=key=project_id,value=my-project \
        --application-parameters=key=region,value=us-central1

Or run the following JSON example:

    $ gcloud design-center spaces application-templates create \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 \
        --application-parameters='[{"key": "project_id", "value":
     "my-project"}, {"key": "region", "value": "us-central1"}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces application-templates create \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 \
        --application-parameters=my-parameters.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/create)

---
### `gcloud design-center spaces application-templates delete`

Delete an application template

Delete an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates delete
    (APPLICATION_TEMPLATE : --location=LOCATION --space=SPACE) [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApplicationTemplate resource - The application template name. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the applicationTemplate or fully qualified identifier for the
     applicationTemplate.

     To set the application_template attribute:
     + provide the argument application_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the applicationTemplate resource.

     To set the location attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the applicationTemplate resource.

     To set the space attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set to true, the application template's children are also deleted. If false, the application template is only deleted if it has no children. |


**Examples:**
```bash
To delete the application template my-app-template in space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates delete \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template

If your application template contains child resources such as revisions,
components, force delete the application template. To force delete the
application template my-app-template in space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces application-templates delete \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/delete)

---
### `gcloud design-center spaces application-templates describe`

Describe an application template

Describe an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates describe
    (APPLICATION_TEMPLATE : --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApplicationTemplate resource - The application template name. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the applicationTemplate or fully qualified identifier for the
     applicationTemplate.

     To set the application_template attribute:
     + provide the argument application_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the applicationTemplate resource.

     To set the location attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the applicationTemplate resource.

     To set the space attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the application template my-app-template in space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates describe \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/describe)

---
### `gcloud design-center spaces application-templates generate`

Generate IaC for an application template

Generates Terraform files for an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates generate
    (APPLICATION_TEMPLATE : --space=SPACE) [--gcs-uri=GCS_URI]
    [--iac-format=IAC_FORMAT] [--location=LOCATION]
    [--artifact-location-gcs-uri=ARTIFACT_LOCATION_GCS_URI
      | [--developer-connect-export-config-dir=DEVELOPER_CONNECT_EXPORT_CONFIG_DIR (--developer-connect-export-config-repo-uri=DEVELOPER_CONNECT_EXPORT_CONFIG_REPO_URI : --connection=CONNECTION) : --developer-connect-export-config-branch=DEVELOPER_CONNECT_EXPORT_CONFIG_BRANCH]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApplicationTemplate resource - The name of the application template. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --location on the command line.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the applicationTemplate or fully qualified identifier for the
     applicationTemplate.

     To set the application_template attribute:
     + provide the argument application_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --space=SPACE
     The space id of the applicationTemplate resource.

     To set the space attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | The Cloud Storage URI to write the generated IaC to. DEPRECATED: Use the 'artifact_location' field instead. |
| `--iac-format` | one of: helm IaC format is HELM |  | The IaC format to generate. IAC_FORMAT must be one of: helm IaC format is HELM. terraform IaC format is Terraform. |
| `--location` | LOCATION |  | For resources [application_template, developer-connect-export-config-repo-uri], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |


**Examples:**
```bash
To generate IaC for the application template my-app-template in space
my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates generate \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates generate \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template

To generate IaC for the application template my-app-template in space
my-space, project my-project and location us-central1 and save to cloud
storage bucket my-bucket, run:

    $ gcloud design-center spaces application-templates generate \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 --gcs-uri=gs://my-bucket

To generate IaC for the application template my-app-template in Terraform
format in space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates generate \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 --iac-format=terraform
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/generate)

---
### `gcloud design-center spaces application-templates import`

Import to an application template

Imports to an existing application template from a given shared template or
application template revision.

**Synopsis:**
```
gcloud design-center spaces application-templates import
    [--application-template=APPLICATION_TEMPLATE]
    [--application-template-revision-uri=APPLICATION_TEMPLATE_REVISION_URI]
    [--location=LOCATION] [--space=SPACE]
    [--shared-template-revision-uri=SHARED_TEMPLATE_REVISION_URI
      : --shared-template=SHARED_TEMPLATE] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-template` | APPLICATION_TEMPLATE |  | For resources [application-template-revision-uri, application_template], provides fallback value for resource application-template attribute. When the resource's full URI path is not provided, application-template will fallback to this flag value. |
| `--location` | LOCATION |  | _[command line.]_ For resources [application-template-revision-uri, application_template, shared-template-revision-uri], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--space` | SPACE |  | _[command line.]_ For resources [application-template-revision-uri, application_template, shared-template-revision-uri], provides fallback value for resource space attribute. When the resource's full URI path is not provided, space will fallback to this flag value. |


**Examples:**
```bash
To import from a shared template revision to the application template
my-app-template in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates import \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1

To import from an application template revision to the application template
my-app-template in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates import \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --application-template-revision-uri=projects/my-project/\
    locations/us-central1/spaces/my-space/applicationTemplates/\
    another-app-template/revisions/rev2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/import)

---
### `gcloud design-center spaces application-templates import-iac`

Import Infrastructure as Code (IaC) for an Application Template

Import Infrastructure as Code (IaC) for a Design Center Application
Template.

**Synopsis:**
```
gcloud design-center spaces application-templates import-iac
    (APPLICATION_TEMPLATE : --location=LOCATION --space=SPACE)
    (--gcs-uri=GCS_URI | --iac-module-from-file=PATH_TO_FILE)
    [--allow-partial-import] [--validate-iac] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application template resource - The application template to import IaC
into IaC. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument APPLICATION_TEMPLATE on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the application_template or fully qualified identifier for the
     application_template.

     To set the application_template_id attribute:
     + provide the argument APPLICATION_TEMPLATE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the application_template.

     To set the location attribute:
     + provide the argument APPLICATION_TEMPLATE on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The ID of the space.

     To set the space attribute:
     + provide the argument APPLICATION_TEMPLATE on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | _[Exactly one of these must be specified:]_ The Cloud Storage URI of the Terraform code (e.g., gs://my-bucket/iac). |
| `--iac-module-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path to a local YAML or JSON file containing the IaC module definition. Use a full or relative path to a local file containing the value of iac_module. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-partial-import` |  |  | If set, partially import valid IaC changes and ignore invalid ones. |
| `--validate-iac` |  |  | Validate the IaC without performing the import. |


**Examples:**
```bash
To import IaC from a Google Cloud Storage URI into the application template
my-template in space dev-space and location us-central1, run:

    $ gcloud design-center spaces application-templates import-iac \
        my-template --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac

To import IaC from a local YAML file named iac_module.yaml into the
application template my-template in space dev-space and location
us-central1, run:

    $ gcloud design-center spaces application-templates import-iac \
        my-template --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml

To import IaC from a Google Cloud Storage URI and allow partial import of
valid edits into the application template my-template, run:

    $ gcloud design-center spaces application-templates import-iac \
        my-template --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac --allow-partial-import

To import IaC from a local YAML file and allow partial import of valid
edits into the application template my-template, run:

    $ gcloud design-center spaces application-templates import-iac \
        my-template --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml --allow-partial-import

To validate IaC from a Google Cloud Storage URI without importing into the
application template my-template, run:

    $ gcloud design-center spaces application-templates import-iac \
        my-template --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac --validate-iac

To validate IaC from a local YAML file without importing into the
application template my-template, run:

    $ gcloud design-center spaces application-templates import-iac \
        my-template --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml --validate-iac
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/import-iac)

---
### `gcloud design-center spaces application-templates list`

List application templates

List application templates in a given space.

**Synopsis:**
```
gcloud design-center spaces application-templates list
    (--space=SPACE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--space` | SPACE |  | _[This must be specified.]_ ID of the space or fully qualified identifier for the space. To set the space attribute: + provide the argument --space on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the space resource. To set the location attribute: + provide the argument --space on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all application templates in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces application-templates list \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates list \
        --space=projects/my-project/locations/us-central1/spaces/\
    my-space

To filter and list application templates with a display name of
my-app-template prefix in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates list \
        --space=my-space --project=my-project --location=us-central1 \
        --filter="displayName:my-app-template*"

To list up to 10 application templates in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates list \
        --space=my-space --project=my-project --location=us-central1 \
        --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/list)

---
### `gcloud design-center spaces application-templates update`

Update an application template

Update an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates update
    (APPLICATION_TEMPLATE : --location=LOCATION --space=SPACE)
    [--composition-type=COMPOSITION_TYPE] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME]
    [--application-parameters=[key=KEY],[value=VALUE]
      | --add-application-parameters=[key=KEY],[value=VALUE]
      --clear-application-parameters
      | --remove-application-parameters=[key=KEY],[value=VALUE]]
    [--root-input-variables=[componentUri=COMPONENTURI],[variable=VARIABLE]
      | --add-root-input-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE] --clear-root-input-variables
      | --remove-root-input-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE]]
    [--root-output-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE]
      | --add-root-output-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE] --clear-root-output-variables
      | --remove-root-output-variables=[componentUri=COMPONENTURI],
      [variable=VARIABLE]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ApplicationTemplate resource - Identifier. Application template name. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application_template on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION_TEMPLATE
     ID of the applicationTemplate or fully qualified identifier for the
     applicationTemplate.

     To set the application_template attribute:
     + provide the argument application_template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the applicationTemplate resource.

     To set the location attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the applicationTemplate resource.

     To set the space attribute:
     + provide the argument application_template on the command line
       with a fully specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--composition-type` | one of: composite ApplicationCompositionType is COMPOSITE |  | The composition type of the applicationTemplate: STANDARD OR COMPOSITE. This is a create time only param. In future, we may support conversion from STANDARD to COMPOSITE. COMPOSITION_TYPE must be one of: composite ApplicationCompositionType is COMPOSITE. The template is composed of STANDARD applicationTemplate(s) and might be having multiple root modules in terraform code. standard ApplicationCompositionType is STANDARD. The applicationTemplate or application is composed of components only of type service/workload/asset and has a single root module in terraform code. |
| `--description` | DESCRIPTION |  | Application template description. |
| `--display-name` | DISPLAY_NAME |  | Application template display name. |


**Examples:**
```bash
To update the display name to My New App Template Name for the application
template my-app-template in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates update \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 --display-name="My New App Template Name"

Or run:

    $ gcloud design-center spaces application-templates update \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template \
        --display-name="My New App Template Name"

To clear the application parameters for the application template
my-app-template in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates update \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 --clear-application-parameters

To add an application parameter key-value pair of project_id:new-project to
the application template my-app-template in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates update \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 \
        --add-application-parameters=key=project_id,value=new-project

To remove an application parameter key-value pair of project_id:new-project
from the application template my-app-template in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates update \
        my-app-template --space=my-space --project=my-project \
        --location=us-central1 \
        --remove-application-parameters=key=project_id,value=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/update)

---

## `gcloud design-center spaces application-templates components` — manage component resources
### `gcloud design-center spaces application-templates components create`

Create a component

Create a component in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components create
    (COMPONENT : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE)
    --shared-template-revision-uri=SHARED_TEMPLATE_REVISION_URI
    [--display-name=DISPLAY_NAME] [--parameters=[key=KEY],[value=VALUE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Component resource - Identifier. The component name. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument component on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  COMPONENT
     ID of the component or fully qualified identifier for the component.

     To set the component attribute:
     + provide the argument component on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the component resource.

     To set the application-template attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --location=LOCATION
     The location id of the component resource.

     To set the location attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the component resource.

     To set the space attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--shared-template-revision-uri` | SHARED_TEMPLATE_REVISION_URI |  | The shared template used to generate the component. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The component display name. |
| `--parameters` | [key=KEY],[value=VALUE] |  | The component parameters. key The key of the parameter. value The value of the parameter. Shorthand Example: --parameters=key=string,value={...} --parameters=key=string,value={...} JSON Example: --parameters='[{"key": "string", "value": {...}}]' File Example: --parameters=path_to_file.(yaml\|json) |


**Examples:**
```bash
To create the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1 using a shared template revision, run:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1

Or run:

    $ gcloud design-center spaces application-templates components \
        create \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1

To create the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1 using a google shared template google-shared-template and
revision rev1, run:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=google/google-shared-template/\
    revisions/rev1

To create the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1 using a google shared template google-shared-template with its
latest revision, run:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=google/google-shared-template

To create the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1 using a shared template my-shared-template and revision rev1
present in the same space, run:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=my-shared-template/revisions/rev1

To create the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1 using a shared template my-shared-template with its latest
revision present in the same space, run:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=my-shared-template

To create the component my-component with a display name My Component in
application template my-app-template, space my-space, project my-project
and location us-central1 using a shared template revision, run:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1 --display-name="My Component"

To create the component my-component with parameter key value pair of
region:us-central1 in application template my-app-template, space my-space,
project my-project and location us-central1, run the following shorthand
example:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1 --parameters=key=region,value=us-central1

Or run the following JSON example:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1 \
        --parameters='[{"key": "region", "value": "us-central1"}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces application-templates components \
        create my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --shared-template-revision-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/sharedTemplates/my-shared-template/\
    revisions/rev1 --parameters=my-parameters.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/create)

---
### `gcloud design-center spaces application-templates components delete`

Delete a component

Delete a component in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components delete
    (COMPONENT : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE) [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Component resource - The component name. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument component on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  COMPONENT
     ID of the component or fully qualified identifier for the component.

     To set the component attribute:
     + provide the argument component on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the component resource.

     To set the application-template attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --location=LOCATION
     The location id of the component resource.

     To set the location attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the component resource.

     To set the space attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If set to true, the component's children are also deleted. If false, the component is only deleted if it has no children. |


**Examples:**
```bash
To delete the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        delete my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates components \
        delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component

If your component contains child resources such as connections, force
delete the component. To force delete the component my-component in
application template my-app-template, space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        delete my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/delete)

---
### `gcloud design-center spaces application-templates components describe`

Describe a component

Describe a component in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components describe
    (COMPONENT : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Component resource - The component name. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument component on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  COMPONENT
     ID of the component or fully qualified identifier for the component.

     To set the component attribute:
     + provide the argument component on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the component resource.

     To set the application-template attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --location=LOCATION
     The location id of the component resource.

     To set the location attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the component resource.

     To set the space attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the component my-component in application template
my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        describe my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates components \
        describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/describe)

---
### `gcloud design-center spaces application-templates components list`

List components

List components in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components list
    (--application-template=APPLICATION_TEMPLATE
      : --location=LOCATION --space=SPACE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-template` | APPLICATION_TEMPLATE |  | _[This must be specified.]_ ID of the applicationTemplate or fully qualified identifier for the applicationTemplate. To set the application-template attribute: + provide the argument --application-template on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the applicationTemplate resource. To set the location attribute: + provide the argument --application-template on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--space` | SPACE |  | _[This must be specified.]_ The space id of the applicationTemplate resource. To set the space attribute: + provide the argument --application-template on the command line with a fully specified name; + provide the argument --space on the command line. |


**Examples:**
```bash
To list all components in application template my-app-template, space
my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        list --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates components \
        list \
        --application-template=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template

To filter and list components that contain a my-component prefix in the
display name in application template my-app-template, space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        list --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --filter="displayName:my-component*"

To list up to 10 components in application template my-app-template, space
my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        list --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 --limit=10

To list components sorted by display name in application template
my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        list --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --sort-by=displayName
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/list)

---
### `gcloud design-center spaces application-templates components update`

Update a component

Update a component in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components update
    (COMPONENT : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE) [--display-name=DISPLAY_NAME]
    [--parameters=[key=KEY],[value=VALUE]
      | --add-parameters=[key=KEY],[value=VALUE] --clear-parameters
      | --remove-parameters=[key=KEY],[value=VALUE]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Component resource - Identifier. The component name. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument component on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  COMPONENT
     ID of the component or fully qualified identifier for the component.

     To set the component attribute:
     + provide the argument component on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the component resource.

     To set the application-template attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --location=LOCATION
     The location id of the component resource.

     To set the location attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the component resource.

     To set the space attribute:
     + provide the argument component on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | The component display name. |


**Examples:**
```bash
To update the display name to My New Component Name in the component
my-component in application template my-app-template, space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --display-name="My New Component Name"

Or run:

    $ gcloud design-center spaces application-templates components \
        update \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component \
        --display-name="My New Component Name"

To update the parameters with new key-value pairs of project_id:new-project
and service_name:new-service for the component my-component in application
template my-app-template, space my-space, project my-project and location
us-central1, run the following shorthand example:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --parameters=key=project_id,value=new-project \
        --add-parameters=key=service_name,value=new-service

Or run the following JSON example:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --parameters='[{"key": "project_id", "value": "new-project"},
     {"key": "service_name", "value": "new-service"}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --parameters=my-parameters.yaml

To add new parameters key-value pair of project_id:new-project and
service_name:new-service to the component my-component in application
template my-app-template, space my-space, project my-project and location
us-central1, run the following shorthand example:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --add-parameters=key=project_id,value=new-project \
        --add-parameters=key=service_name,value=new-service

Or run the following JSON example:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --add-parameters='[{"key": "project_id", "value":
     "new-project"}, {"key": "service_name", "value": "new-service"}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --add-parameters=my-parameters.yaml

To clear all parameters from the component my-component in application
template my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --clear-parameters

To remove an existing parameter key-value pair of project_id:new-project
from the component my-component in application template my-app-template,
space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        update my-component --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1 \
        --remove-parameters=key=project_id,value=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/update)

---

## `gcloud design-center spaces application-templates components connections` — manage connection resources
### `gcloud design-center spaces application-templates components connections create`

Create a connection

Create a connection between components in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components connections
    create (CONNECTION : --component=COMPONENT)
    --destination-component-uri=DESTINATION_COMPONENT_URI
    [--application-template=APPLICATION_TEMPLATE]
    [--destination-component-parameters=[key=KEY],[value=VALUE]]
    [--location=LOCATION]
    [--source-component-parameters=[key=KEY],[value=VALUE]] [--space=SPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Identifier. The connection name. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

To set the space attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --space on the command line.

To set the application-template attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --application-template on the command line.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --component=COMPONENT
     The component id of the connection resource.

     To set the component attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --component on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-component-uri` | DESTINATION_COMPONENT_URI |  | _[This must be specified.]_ ID of the component or fully qualified identifier for the component. To set the component attribute: + provide the argument --destination-component-uri on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-template` | APPLICATION_TEMPLATE |  | For resources [connection, destination-component-uri], provides fallback value for resource application-template attribute. When the resource's full URI path is not provided, application-template will fallback to this flag value. |
| `--destination-component-parameters` | [key=KEY],[value=VALUE] |  | The parameters of the connection associated with the destination component. key The key of the parameter. value The value of the parameter. Shorthand Example: --destination-component-parameters=key=string,value={...} --destination-component-parameters=key=string,value={...} JSON Example: --destination-component-parameters='[{"key": "string", "value": {...}}]' File Example: --destination-component-parameters=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | For resources [connection, destination-component-uri], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--source-component-parameters` | [key=KEY],[value=VALUE] |  | The parameters of the connection associated with the source component. key The key of the parameter. value The value of the parameter. Shorthand Example: --source-component-parameters=key=string,value={...} --source-component-parameters=key=string,value={...} JSON Example: --source-component-parameters='[{"key": "string", "value": {...}}]' File Example: --source-component-parameters=path_to_file.(yaml\|json) |
| `--space` | SPACE |  | For resources [connection, destination-component-uri], provides fallback value for resource space attribute. When the resource's full URI path is not provided, space will fallback to this flag value. |


**Examples:**
```bash
To create the connection my-connection in component my-component of
application template my-app-template, space my-space, project my-project
and location us-central1 with a destination component other-component, run:

    $ gcloud design-center spaces application-templates components \
        connections create my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=other-component

Or run:

    $ gcloud design-center spaces application-templates components \
        connections create my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template/\
    components/other-component

Or run:

    $ gcloud design-center spaces application-templates components \
        connections create \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component/\
    connections/my-connection \
        --destination-component-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template/\
    components/other-component

To create the connection my-connection with a parameter key-value pair of
type:connection-type in component my-component of application template
my-app-template, space my-space, project my-project and location
us-central1 with a destination component other-component, run the following
shorthand example:

    $ gcloud design-center spaces application-templates components \
        connections create my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=other-component \
        --parameters=key=type,value=connection-type

Or run the following JSON example:

    $ gcloud design-center spaces application-templates components \
        connections create my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=other-component \
        --parameters='[{"key": "type", "value": "connection-type"}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces application-templates components \
        connections create my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=other-component \
        --parameters=my-parameters.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/connections/create)

---
### `gcloud design-center spaces application-templates components connections delete`

Delete a connection

Delete a connection between components in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components connections
    delete
    (CONNECTION : --application-template=APPLICATION_TEMPLATE
      --component=COMPONENT --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - The connection name. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the connection resource.

     To set the application-template attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --component=COMPONENT
     The component id of the connection resource.

     To set the component attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --component on the command line.

  --location=LOCATION
     The location id of the connection resource.

     To set the location attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the connection resource.

     To set the space attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To delete the connection my-connection in component my-component of
application template my-app-template, space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        connections delete my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates components \
        connections delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component/\
    connections/my-connection
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/connections/delete)

---
### `gcloud design-center spaces application-templates components connections describe`

Describe a connection

Describe a connection between components in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components connections
    describe
    (CONNECTION : --application-template=APPLICATION_TEMPLATE
      --component=COMPONENT --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Name of the resource The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the connection resource.

     To set the application-template attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --component=COMPONENT
     The component id of the connection resource.

     To set the component attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --component on the command line.

  --location=LOCATION
     The location id of the connection resource.

     To set the location attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the connection resource.

     To set the space attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the connection my-connection in component my-component of
application template my-app-template, space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        connections describe my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates components \
        connections describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component/\
    connections/my-connection
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/connections/describe)

---
### `gcloud design-center spaces application-templates components connections list`

List connections

List connections in a component of an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components connections
    list
    (--component=COMPONENT : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--component` | COMPONENT |  | _[This must be specified.]_ ID of the component or fully qualified identifier for the component. To set the component attribute: + provide the argument --component on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--application-template` | APPLICATION_TEMPLATE |  | _[This must be specified.]_ The applicationTemplate id of the component resource. To set the application-template attribute: + provide the argument --component on the command line with a fully specified name; + provide the argument --application-template on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the component resource. To set the location attribute: + provide the argument --component on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--space` | SPACE |  | _[This must be specified.]_ The space id of the component resource. To set the space attribute: + provide the argument --component on the command line with a fully specified name; + provide the argument --space on the command line. |


**Examples:**
```bash
To list all connections in component my-component of application template
my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        connections list --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates components \
        connections list \
        --component=projects/my-project/locations/us-central1/spaces/\
    my-space/applicationTemplates/my-app-template/components/\
    my-component
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/connections/list)

---
### `gcloud design-center spaces application-templates components connections update`

Update a connection

Update a connection between components in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates components connections
    update (CONNECTION : --component=COMPONENT)
    [--application-template=APPLICATION_TEMPLATE]
    [--destination-component-uri=DESTINATION_COMPONENT_URI]
    [--location=LOCATION] [--space=SPACE]
    [--destination-component-parameters=[key=KEY],[value=VALUE]
      | --add-destination-component-parameters=[key=KEY],[value=VALUE]
      --clear-destination-component-parameters
      | --remove-destination-component-parameters=[key=KEY],[value=VALUE]]
    [--source-component-parameters=[key=KEY],[value=VALUE]
      | --add-source-component-parameters=[key=KEY],[value=VALUE]
      --clear-source-component-parameters
      | --remove-source-component-parameters=[key=KEY],[value=VALUE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Identifier. The connection name. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

To set the space attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --space on the command line.

To set the application-template attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --application-template on the command line.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --component=COMPONENT
     The component id of the connection resource.

     To set the component attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --component on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-template` | APPLICATION_TEMPLATE |  | For resources [connection, destination-component-uri], provides fallback value for resource application-template attribute. When the resource's full URI path is not provided, application-template will fallback to this flag value. |
| `--location` | LOCATION |  | _[line.]_ For resources [connection, destination-component-uri], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--space` | SPACE |  | _[line.]_ For resources [connection, destination-component-uri], provides fallback value for resource space attribute. When the resource's full URI path is not provided, space will fallback to this flag value. |


**Examples:**
```bash
To update the destination component URI to
projects/my-project/locations/us-central1/spaces/my-space/applicationTemplates/my-app-template/components/other-new-component
in the connection my-connection in component my-component of application
template my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=other-new-component

Or run:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --destination-component-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template/\
    components/other-new-component

Or run:

    $ gcloud design-center spaces application-templates components \
        connections update \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/components/my-component/\
    connections/my-connection \
        --destination-component-uri=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template/\
    components/other-new-component

To add a new parameter key-value pair of new_parameter_key:new-parameter to
the connection my-connection in component my-component of application
template my-app-template, space my-space, project my-project and location
us-central1, run the following shorthand example:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection \
        --application-template=my-app-template \
        --component=my-component --space=my-space --project=my-project \
        --location=us-central1 \
        --add-parameters=key=project_id,value=new-project \
        --add-parameters=key=new_parameter_key,value=new-parameter

Or run the following JSON example:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection \
        --application-template=my-app-template \
        --component=my-component --space=my-space --project=my-project \
        --location=us-central1 \
        --add-parameters='[{"key": "project_id", "value":
     "new-project"}, {"key": "new_parameter_key", "value":
     "new-parameter"}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection \
        --application-template=my-app-template \
        --component=my-component --space=my-space --project=my-project \
        --location=us-central1 --add-parameters=my-parameters.yaml

To clear all parameters from the connection my-connection in component
my-component of application template my-app-template, space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 --clear-parameters

To remove an existing parameter key-value pair of type:connection-type from
the connection my-connection in component my-component of application
template my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates components \
        connections update my-connection --component=my-component \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 \
        --remove-parameters=key=type,value=connection-type
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/components/connections/update)

---

## `gcloud design-center spaces application-templates revisions` — manage application template revision resources
### `gcloud design-center spaces application-templates revisions delete`

Delete an application template revision

Delete an application template revision.

**Synopsis:**
```
gcloud design-center spaces application-templates revisions delete
    (REVISION : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - The application template revision name. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument revision on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the revision resource.

     To set the application-template attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --location=LOCATION
     The location id of the revision resource.

     To set the location attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the revision resource.

     To set the space attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To delete the application template revision my-revision in application
template my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates revisions \
        delete my-revision --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates revisions \
        delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/revisions/my-revision
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/revisions/delete)

---
### `gcloud design-center spaces application-templates revisions describe`

Describe an application template revision

Describe an application template revision.

**Synopsis:**
```
gcloud design-center spaces application-templates revisions describe
    (REVISION : --application-template=APPLICATION_TEMPLATE
      --location=LOCATION --space=SPACE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - The application template revision name. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument revision on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application-template=APPLICATION_TEMPLATE
     The applicationTemplate id of the revision resource.

     To set the application-template attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --application-template on the command line.

  --location=LOCATION
     The location id of the revision resource.

     To set the location attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the revision resource.

     To set the space attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the application template revision my-revision in application
template my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates revisions \
        describe my-revision --application-template=my-app-template \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates revisions \
        describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applicationTemplates/my-app-template/revisions/my-revision
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/revisions/describe)

---
### `gcloud design-center spaces application-templates revisions list`

List application template revisions

List application template revisions in an application template.

**Synopsis:**
```
gcloud design-center spaces application-templates revisions list
    (--application-template=APPLICATION_TEMPLATE
      : --location=LOCATION --space=SPACE) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-template` | APPLICATION_TEMPLATE |  | _[This must be specified.]_ ID of the applicationTemplate or fully qualified identifier for the applicationTemplate. To set the application-template attribute: + provide the argument --application-template on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the applicationTemplate resource. To set the location attribute: + provide the argument --application-template on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--space` | SPACE |  | _[This must be specified.]_ The space id of the applicationTemplate resource. To set the space attribute: + provide the argument --application-template on the command line with a fully specified name; + provide the argument --space on the command line. |


**Examples:**
```bash
To list all application template revisions in application template
my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates revisions list \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces application-templates revisions list \
        --application-template=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template

To list up to 10 application template revisions in application template
my-app-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces application-templates revisions list \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 --limit=10

To list application template revisions sorted by creation time in
application template my-app-template, space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces application-templates revisions list \
        --application-template=my-app-template --space=my-space \
        --project=my-project --location=us-central1 --sort-by=createTime
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/application-templates/revisions/list)

---

## `gcloud design-center spaces applications` — manage application resources
### `gcloud design-center spaces applications create`

Create an application

Create an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications create
    (APPLICATION : --location=LOCATION --space=SPACE)
    --scope-type=SCOPE_TYPE
    (--source-application-template-revision=SOURCE_APPLICATION_TEMPLATE_REVISION | --source-shared-template-revision-uri=SOURCE_SHARED_TEMPLATE_REVISION_URI)
    [--app-parameters=[key=KEY],[value=VALUE]]
    [--component-parameters=[component=COMPONENT],[parameters=PARAMETERS]]
    [--connection-configs=[connectionUri=CONNECTIONURI],
      [destinationComponentParameters=DESTINATIONCOMPONENTPARAMETERS],
      [sourceComponentParameters=SOURCECOMPONENTPARAMETERS]]
    [--deployment-project=DEPLOYMENT_PROJECT]
    [--deployment-region=DEPLOYMENT_REGION] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--import-existing-resources]
    [--service-account=SERVICE_ACCOUNT] [--type=TYPE]
    [--attributes-business-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --attributes-developer-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --attributes-operator-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      [--criticality-type=CRITICALITY_TYPE
      : --criticality-level=CRITICALITY_LEVEL
      --criticality-mission-critical] [--environment-type=ENVIRONMENT_TYPE
      : --environment=ENVIRONMENT]]
    [--gke-deployment-target-cluster-self-link=GKE_DEPLOYMENT_TARGET_CLUSTER_SELF_LINK --gke-deployment-target-kubernetes-service-account=GKE_DEPLOYMENT_TARGET_KUBERNETES_SERVICE_ACCOUNT --gke-deployment-target-namespace=GKE_DEPLOYMENT_TARGET_NAMESPACE : --gke-deployment-target-kubernetes-service-account-creation]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - Identifier. The name of the application. Format:
projects/{project}/locations/{location}/spaces/{space}/applications/{application}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the application resource.

     To set the space attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope-type` | one of: global Global type |  | _[This must be specified.]_ Scope Type. SCOPE_TYPE must be one of: global Global type. regional Regional type. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--app-parameters` | [key=KEY],[value=VALUE] |  | A list of parameters to attach to the deployment source object, which is a catalog entry or application template snapshot. key The key of the parameter. value The value of the parameter. Shorthand Example: --app-parameters=key=string,value={...} --app-parameters=key=string,value={...} JSON Example: --app-parameters='[{"key": "string", "value": {...}}]' File Example: --app-parameters=path_to_file.(yaml\|json) |
| `--component-parameters` | [component=COMPONENT],[parameters=PARAMETERS] |  | A list of component parameters to associate with the application. component The name of the component parameter. parameters A list of parameters associated with the component. key The key of the parameter. value The value of the parameter. Shorthand Example: --component-parameters=component=string,parameters=[{key=string,value={...}}] --component-parameters=component=string,parameters=[{key=string,value={...}}] JSON Example: --component-parameters='[{"component": "string", "parameters": [{"key": "string", "value": {...}}]}]' File Example: --component-parameters=path_to_file.(yaml\|json) |
| `--connection-configs` | [connectionUri=CONNECTIONURI],[destinationComponentParameters=DESTINATIONCOMPONENTPARAMETERS],[sourceComponentParameters=SOURCECOMPONENTPARAMETERS] |  | Connection configuration for the application. connectionUri The connection URI. destinationComponentParameters The parameters of the connection associated with the destination component. key The key of the parameter. value The value of the parameter. sourceComponentParameters The parameters of the connection associated with the source component. key The key of the parameter. value The value of the parameter. Shorthand Example: --connection-configs=connectionUri=string,destinationComponentParameters=[{key=string,value={...}}],sourceComponentParameters=[{key=string,value={...}}] --connection-configs=connectionUri=string,destinationComponentParameters=[{key=string,value={...}}],sourceComponentParameters=[{key=string,value={...}}] JSON Example: --connection-configs='[{"connectionUri": "string", "destinationComponentParameters": [{"key": "string", "value": {...}}], "sourceComponentParameters": [{"key": "string", "value": {...}}]}]' File Example: --connection-configs=path_to_file.(yaml\|json) |
| `--deployment-project` | DEPLOYMENT_PROJECT |  | Deployment project of the application. |
| `--deployment-region` | DEPLOYMENT_REGION |  | The region where the application is deployed. |
| `--description` | DESCRIPTION |  | Description of the application. |
| `--display-name` | DISPLAY_NAME |  | Display name of the application. |
| `--import-existing-resources` |  |  | Import existing resources into the application. |
| `--service-account` | SERVICE_ACCOUNT |  | Your own service account that you use to deploy an application. |
| `--type` | one of: helm-app Application type is helm application |  | The type of the application. TYPE must be one of: helm-app Application type is helm application. terraform-app Application type is terraform application. |


**Examples:**
```bash
To create the application my-application with a display name My
Application, description My application description, scope type global and
source application template revision
projects/my-project/locations/us-central1/spaces/my-space/applicationTemplates/my-app-template/revisions/rev1
in space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces applications create my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --display-name="My Application" \
        --description="My application description" --scope-type=global \
        --source-application-template-revision=projects/my-project/\
    locations/us-central1/spaces/my-space/applicationTemplates/\
    my-app-template/revisions/rev1

To create the application my-application with a deployment project
my-deployment-project, deployment region us-east1, scope type regional and
source application template revision
projects/my-project/locations/us-central1/spaces/my-space/applicationTemplates/my-app-template/revisions/rev1
in space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces applications create my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --deployment-project=my-deployment-project \
        --deployment-region=us-east1 --scope-type=regional \
        --source-application-template-revision=projects/my-project/\
    locations/us-central1/spaces/my-space/applicationTemplates/\
    my-app-template/revisions/rev1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/create)

---
### `gcloud design-center spaces applications delete`

Delete an application

Delete an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications delete
    (APPLICATION : --location=LOCATION --space=SPACE) [--async] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The application name. Format:
projects/$project/locations/$location/spaces/$space/applications/$application
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the application resource.

     To set the space attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, the application's children are also deleted. If false, the application is only deleted if it has no children. |


**Examples:**
```bash
To delete the application my-application in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces applications delete my-application \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces applications delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applications/my-application

If your application contains child resources, force delete the application.
To force delete the application my-application in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces applications delete my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --force
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/delete)

---
### `gcloud design-center spaces applications deploy`

Deploy an application

Deploy an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications deploy
    (APPLICATION : --location=LOCATION --space=SPACE) [--async]
    [--create-sa] [--replace] [--service-account=SERVICE_ACCOUNT]
    [--worker-pool=WORKER_POOL] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The application to deploy IaC. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument APPLICATION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument APPLICATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The ID of the space.

     To set the space attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--create-sa` |  |  | Create a new service account for the deployment. |
| `--replace` |  |  | Flag to update the existing deployment. If not set or false, deploy will fail if application state is in the DEPLOYED state. |
| `--service-account` | SERVICE_ACCOUNT |  | The service account to use for this deployment. * If provided, this service account will be used to execute the deployment process, taking precedence over any service_account specified on the Application resource. * The caller must have the "iam.serviceAccounts.actAs" permission on this service account. * If this field is omitted, the system will use the "service_account" defined within the Application resource. * If this field is omitted with --create-sa flag, the system will create a new and unique service_account and use it for the deployment. * We recommend that you provide a service account here or on the Application resource. If you don't provide a service account, the deployment will fail. * If the --create-sa flag is also provided, this value is the ID of a new service account to be created (e.g., my-new-sa). Format: projects/{PROJECT}/serviceAccounts/{EMAIL_ADDRESS} (when not using --create-sa) |
| `--worker-pool` | WORKER_POOL |  | The user-specified Worker Pool resource in which the Cloud Build job will execute. Format: projects/{project}/locations/{location}/workerPools/{workerPoolId} If this flag is omitted, the worker pool already defined on the application will be used. If no worker pool is defined on the application, the default Cloud Build worker pool is used. The worker pool must exist in the same region as the application. |


**Examples:**
```bash
To deploy the application my-application in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces applications deploy \
      projects/my-project/locations/us-central1/spaces/my-space/\
    applications/my-application

To deploy the application my-application in space my-space, project
my-project and location us-central1 and replace the existing deployment,
run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --replace

To deploy the application my-application in space my-space, project
my-project and location us-central1 using a worker pool
projects/my-project/locations/us-central1/workerPools/my-worker-pool, run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --worker-pool=projects/my-project/locations/us-central1/\
    workerPools/my-worker-pool

To deploy the application my-application and create a new service account
for the deployment, run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --create-sa

To deploy the application my-application and create a new service account
and create a specific service account for the deployment, run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --create-sa \
      --service-account=my-service-account@my-project.iam.gserviceacco\
    unt.com

To deploy the application my-application and use a specific service account
for the deployment, run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --service-account=projects/my-project/serviceAccounts/\
    my-service-account@my-project.iam.gserviceaccount.com

To deploy the application my-application in space my-space, project
my-project and location us-central1 asynchronously, run:

    $ gcloud design-center spaces applications deploy my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/deploy)

---
### `gcloud design-center spaces applications describe`

Describe an application

Describe an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications describe
    (APPLICATION : --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The application name. Format:
projects/$project/locations/$location/spaces/$space/applications/$application
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the application resource.

     To set the space attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the application my-application in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces applications describe my-application \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces applications describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applications/my-application
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/describe)

---
### `gcloud design-center spaces applications generate`

Generate IaC for an application

Generates Terraform files for an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications generate
    (APPLICATION : --space=SPACE) [--gcs-uri=GCS_URI]
    [--iac-format=IAC_FORMAT] [--location=LOCATION]
    [--artifact-location-gcs-uri=ARTIFACT_LOCATION_GCS_URI
      | [--developer-connect-export-config-dir=DEVELOPER_CONNECT_EXPORT_CONFIG_DIR (--developer-connect-export-config-repo-uri=DEVELOPER_CONNECT_EXPORT_CONFIG_REPO_URI : --connection=CONNECTION) : --developer-connect-export-config-branch=DEVELOPER_CONNECT_EXPORT_CONFIG_BRANCH]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The name of the application. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --space=SPACE
     The space id of the application resource.

     To set the space attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | The Cloud Storage URI to write the generated IaC to. DEPRECATED: Use the 'artifact_location' field instead. |
| `--iac-format` | one of: helm IaC format is HELM |  | The IaC format to generate. IAC_FORMAT must be one of: helm IaC format is HELM. terraform IaC format is Terraform. |
| `--location` | LOCATION |  | For resources [application, developer-connect-export-config-repo-uri], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |


**Examples:**
```bash
To generate IaC for the application my-application in space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces applications generate my-application \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces applications generate \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applications/my-application

To generate IaC for the application my-application in space my-space,
project my-project and location us-central1 and save to Cloud Storage
bucket my-bucket, run:

    $ gcloud design-center spaces applications generate my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --gcs-uri=gs://my-bucket

To generate IaC for the application my-application in Terraform format in
space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces applications generate my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --iac-format=terraform
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/generate)

---
### `gcloud design-center spaces applications import-iac`

Import Infrastructure as Code (IaC) for an Application

Import Infrastructure as Code (IaC) for a Design Center Application.

**Synopsis:**
```
gcloud design-center spaces applications import-iac
    (APPLICATION : --location=LOCATION --space=SPACE)
    (--gcs-uri=GCS_URI | --iac-module-from-file=PATH_TO_FILE)
    [--allow-partial-import] [--validate-iac] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The application to import IaC into IaC. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument APPLICATION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument APPLICATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The ID of the space.

     To set the space attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gcs-uri` | GCS_URI |  | _[Exactly one of these must be specified:]_ The Cloud Storage URI of the Terraform code (e.g., gs://my-bucket/iac). |
| `--iac-module-from-file` | PATH_TO_FILE |  | _[Exactly one of these must be specified:]_ Path to a local YAML or JSON file containing the IaC module definition. Use a full or relative path to a local file containing the value of iac_module. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allow-partial-import` |  |  | If set, partially import valid IaC changes and ignore invalid ones. |
| `--validate-iac` |  |  | Validate the IaC without performing the import. |


**Examples:**
```bash
To import IaC from a Google Cloud Storage URI into the application my-app
in space dev-space and location us-central1, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac

To import IaC from a local YAML file named iac_module.yaml into the
application my-app in space dev-space and location us-central1, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml

To import IaC from a Google Cloud Storage URI into the application my-app,
allowing partial imports of valid edits, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac --allow-partial-import

To import IaC from a local YAML file into the application my-app, allowing
partial imports of valid edits, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml --allow-partial-import

To validate IaC from a Google Cloud Storage URI for the application my-app
without importing, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac --validate-iac

To validate IaC from a local YAML file for the application my-app without
importing, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml --validate-iac

To validate IaC from a Google Cloud Storage URI for the application my-app
and indicate that a future import should allow partial success, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --gcs-uri=gs://my-bucket/iac --validate-iac \
        --allow-partial-import

To validate IaC from a local YAML file for the application my-app and
indicate that a future import should allow partial success, run:

    $ gcloud design-center spaces applications import-iac my-app \
        --location=us-central1 --space=dev-space \
        --iac-module-from-file=iac_module.yaml --validate-iac \
        --allow-partial-import
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/import-iac)

---
### `gcloud design-center spaces applications list`

List applications

List applications in a space.

**Synopsis:**
```
gcloud design-center spaces applications list
    (--space=SPACE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--space` | SPACE |  | _[This must be specified.]_ ID of the space or fully qualified identifier for the space. To set the space attribute: + provide the argument --space on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the space resource. To set the location attribute: + provide the argument --space on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all applications in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces applications list --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces applications list \
        --space=projects/my-project/locations/us-central1/spaces/\
    my-space

To filter and list applications that contain a my-application prefix in the
display name in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces applications list --space=my-space \
        --project=my-project --location=us-central1 \
        --filter="displayName:my-application*"

To list up to 10 applications in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces applications list --space=my-space \
        --project=my-project --location=us-central1 --limit=10

To list applications sorted by display name in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces applications list --space=my-space \
        --project=my-project --location=us-central1 \
        --sort-by=displayName
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/list)

---
### `gcloud design-center spaces applications preview`

Preview a Design Center application

Preview an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications preview
    (APPLICATION : --location=LOCATION --space=SPACE) [--async]
    [--create-sa] [--service-account=SERVICE_ACCOUNT]
    [--worker-pool=WORKER_POOL] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The application to preview IaC. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument APPLICATION on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument APPLICATION on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The ID of the space.

     To set the space attribute:
     + provide the argument APPLICATION on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--create-sa` |  |  | Create a new service account for the preview. |
| `--service-account` | SERVICE_ACCOUNT |  | The service account to use for this preview. * If provided, this service account will be used to execute the preview process, taking precedence over any service_account specified on the Application resource. * The caller must have the "iam.serviceAccounts.actAs" permission on this service account. * If this field is omitted, the system will use the "service_account" defined within the Application resource. * If this field is omitted with --create-sa flag, the system will create a new and unique service_account and use it for the preview. * We recommend that you provide a service account here or on the Application resource. If you don't provide a service account, the preview will fail. * If the --create-sa flag is also provided, this value is the ID of a new service account to be created (e.g., my-new-sa). Format: projects/{PROJECT}/serviceAccounts/{EMAIL_ADDRESS} (when not using --create-sa) |
| `--worker-pool` | WORKER_POOL |  | The user-specified Worker Pool resource in which the Cloud Build job will execute. Format: projects/{project}/locations/{location}/workerPools/{workerPoolId} If this flag is omitted, the worker pool already defined on the application will be used. If no worker pool is defined on the application, the default Cloud Build worker pool is used. The worker pool must exist in the same region as the application. |


**Examples:**
```bash
To preview the application my-application in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces applications preview my-application \
      --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces applications preview \
      projects/my-project/locations/us-central1/spaces/my-space/\
    applications/my-application

To preview the application my-application in space my-space, project
my-project and location us-central1 using a worker pool
projects/my-project/locations/us-central1/workerPools/my-worker-pool, run:

    $ gcloud design-center spaces applications preview my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --worker-pool=projects/my-project/locations/us-central1/\
    workerPools/my-worker-pool

To preview the application my-application and create a new service account
for the preview, run:

    $ gcloud design-center spaces applications preview my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --create-sa

To preview the application my-application and create a new provided service
account for the preview, run:

    $ gcloud design-center spaces applications preview my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --create-sa \
      --service-account=my-service-account@my-project.iam.gserviceacco\
    unt.com

To preview the application my-application and use a specific existing
service account for the preview, run:

    $ gcloud design-center spaces applications preview my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --service-account=projects/my-project/serviceAccounts/\
    my-service-account@my-project.iam.gserviceaccount.com

To preview the application my-application in space my-space, project
my-project and location us-central1 asynchronously, run:

    $ gcloud design-center spaces applications preview my-application \
      --space=my-space --project=my-project --location=us-central1 \
      --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/preview)

---
### `gcloud design-center spaces applications update`

Update an application

Update an application in a space.

**Synopsis:**
```
gcloud design-center spaces applications update
    (APPLICATION : --location=LOCATION --space=SPACE)
    [--deployment-project=DEPLOYMENT_PROJECT]
    [--deployment-region=DEPLOYMENT_REGION] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--[no-]import-existing-resources]
    [--service-account=SERVICE_ACCOUNT] [--type=TYPE]
    [--app-parameters=[key=KEY],[value=VALUE]
      | --add-app-parameters=[key=KEY],[value=VALUE] --clear-app-parameters
      | --remove-app-parameters=[key=KEY],[value=VALUE]]
    [--clear-attributes
      --attributes-business-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      | --add-attributes-business-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --clear-attributes-business-owners
      | --remove-attributes-business-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --attributes-developer-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      | --add-attributes-developer-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --clear-attributes-developer-owners
      | --remove-attributes-developer-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --attributes-operator-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      | --add-attributes-operator-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --clear-attributes-operator-owners
      | --remove-attributes-operator-owners=[channel=CHANNEL],
      [displayName=DISPLAYNAME],[email=EMAIL]
      --criticality-level=CRITICALITY_LEVEL
      --[no-]criticality-mission-critical
      --criticality-type=CRITICALITY_TYPE
      --environment=ENVIRONMENT --environment-type=ENVIRONMENT_TYPE]
    [--clear-deployment-target
      --gke-deployment-target-cluster-self-link=GKE_DEPLOYMENT_TARGET_CLUSTER_SELF_LINK --gke-deployment-target-kubernetes-service-account=GKE_DEPLOYMENT_TARGET_KUBERNETES_SERVICE_ACCOUNT --[no-]gke-deployment-target-kubernetes-service-account-creation --gke-deployment-target-namespace=GKE_DEPLOYMENT_TARGET_NAMESPACE]
    [--clear-scope --scope-type=SCOPE_TYPE]
    [--clear-source
      --source-application-template-revision=SOURCE_APPLICATION_TEMPLATE_REVISION | --source-shared-template-revision-uri=SOURCE_SHARED_TEMPLATE_REVISION_URI]
    [--component-parameters=[component=COMPONENT],[parameters=PARAMETERS]
      | --add-component-parameters=[component=COMPONENT],
      [parameters=PARAMETERS] --clear-component-parameters
      | --remove-component-parameters=[component=COMPONENT],
      [parameters=PARAMETERS]]
    [--connection-configs=[connectionUri=CONNECTIONURI],
      [destinationComponentParameters=DESTINATIONCOMPONENTPARAMETERS],
      [sourceComponentParameters=SOURCECOMPONENTPARAMETERS]
      | --add-connection-configs=[connectionUri=CONNECTIONURI],
      [destinationComponentParameters=DESTINATIONCOMPONENTPARAMETERS],
      [sourceComponentParameters=SOURCECOMPONENTPARAMETERS]
      --clear-connection-configs
      | --remove-connection-configs=[connectionUri=CONNECTIONURI],
      [destinationComponentParameters=DESTINATIONCOMPONENTPARAMETERS],
      [sourceComponentParameters=SOURCECOMPONENTPARAMETERS]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - Identifier. The name of the application. Format:
projects/{project}/locations/{location}/spaces/{space}/applications/{application}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument application on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  APPLICATION
     ID of the application or fully qualified identifier for the
     application.

     To set the application attribute:
     + provide the argument application on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the application resource.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the application resource.

     To set the space attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deployment-project` | DEPLOYMENT_PROJECT |  | Deployment project of the application. |
| `--deployment-region` | DEPLOYMENT_REGION |  | The region where the application is deployed. |
| `--description` | DESCRIPTION |  | Description of the application. |
| `--display-name` | DISPLAY_NAME |  | Display name of the application. |
| `--[no-]import-existing-resources` |  |  | Import existing resources into the application. Use --import-existing-resources to enable and --no-import-existing-resources to disable. |
| `--service-account` | SERVICE_ACCOUNT |  | Your own service account that you use to deploy an application. |
| `--type` | one of: helm-app Application type is helm application |  | The type of the application. TYPE must be one of: helm-app Application type is helm application. terraform-app Application type is terraform application. |


**Examples:**
```bash
To update the display name to My New Application Name for the application
my-application in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces applications update my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --display-name="My New Application Name"

Or run:

    $ gcloud design-center spaces applications update \
        projects/my-project/locations/us-central1/spaces/my-space/\
    applications/my-application --display-name="My New Application Name"

To update the source application template revision to
projects/my-project/locations/us-central1/spaces/my-space/applicationTemplates/my-app-template/revisions/rev2
for the application my-application in space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces applications update my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --source-application-template-revision=projects/my-project/\
    locations/us-central1/spaces/my-space/applicationTemplates/\
    my-app-template/revisions/rev2

To update the component parameters with new key-value pairs of
project_id:new-project and service_name:new-service for the component
projects/my-project/locations/us-central1/spaces/my-space/applicationTemplates/my-app-template/components/my-component
in application my-application, space my-space, project my-project and
location us-central1, run the following shorthand example:

    $ gcloud design-center spaces applications update my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --component-parameters=component=projects/my-project/locations/\
    us-central1/spaces/my-space/applicationTemplates/my-app-template/\
    components/my-component,parameters='[{"key": "project_id", "value":
     "new-project"}, {"key": "service_name", "value": "new-service"}]'

Or run the following JSON example:

    $ gcloud design-center spaces applications update my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --component-parameters='[{"component":
     "projects/my-project/locations/us-central1/spaces/my-space/applicat\
    ionTemplates/my-app-template/components/my-component",
     "parameters": [{"key": "project_id", "value": "new-project"},
     {"key": "service_name", "value": "new-service"}]}]'

Or create a YAML or JSON file with the parameters and run the following
file example:

    $ gcloud design-center spaces applications update my-application \
        --space=my-space --project=my-project --location=us-central1 \
        --component-parameters=component-parameters.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/applications/update)

---

## `gcloud design-center spaces catalogs` — manage catalog resources
### `gcloud design-center spaces catalogs create`

Create a catalog

Create a catalog in a space.

**Synopsis:**
```
gcloud design-center spaces catalogs create
    (CATALOG : --location=LOCATION --space=SPACE)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - Identifier. The catalog name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument catalog on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.

     To set the catalog attribute:
     + provide the argument catalog on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the catalog resource.

     To set the location attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the catalog resource.

     To set the space attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The catalog description. |
| `--display-name` | DISPLAY_NAME |  | The catalog display name. |


**Examples:**
```bash
To create the catalog my-catalog in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces catalogs create my-catalog \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs create \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog

To create the catalog my-catalog with a display name of My Catalog and
description of My catalog description in space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces catalogs create my-catalog \
        --space=my-space --project=my-project --location=us-central1 \
        --display-name="My Catalog" \
        --description="My catalog description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/create)

---
### `gcloud design-center spaces catalogs delete`

Delete a catalog

Delete a catalog in a space.

**Synopsis:**
```
gcloud design-center spaces catalogs delete
    (CATALOG : --location=LOCATION --space=SPACE) [--async] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The catalog name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument catalog on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.

     To set the catalog attribute:
     + provide the argument catalog on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the catalog resource.

     To set the location attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the catalog resource.

     To set the space attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, the catalog's children are also deleted. If false, the catalog is only deleted if it has no children. |


**Examples:**
```bash
To delete the catalog my-catalog in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces catalogs delete my-catalog \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog

If your catalog contains child resources such as catalog templates, shares,
force delete the catalog. To force delete the catalog my-catalog in space
my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs delete my-catalog \
        --space=my-space --project=my-project --location=us-central1 \
        --force

To delete the catalog my-catalog in space my-space, project my-project and
location us-central1 asynchronously, run:

    $ gcloud design-center spaces catalogs delete my-catalog \
        --space=my-space --project=my-project --location=us-central1 \
        --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/delete)

---
### `gcloud design-center spaces catalogs describe`

Describe a catalog

Describe a catalog in a space.

**Synopsis:**
```
gcloud design-center spaces catalogs describe
    (CATALOG : --location=LOCATION --space=SPACE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - The catalog name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument catalog on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.

     To set the catalog attribute:
     + provide the argument catalog on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the catalog resource.

     To set the location attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the catalog resource.

     To set the space attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the catalog my-catalog in space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces catalogs describe my-catalog \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/describe)

---
### `gcloud design-center spaces catalogs list`

List catalogs

List catalogs in a space.

**Synopsis:**
```
gcloud design-center spaces catalogs list
    (--space=SPACE : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--space` | SPACE |  | _[This must be specified.]_ ID of the space or fully qualified identifier for the space. To set the space attribute: + provide the argument --space on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the space resource. To set the location attribute: + provide the argument --space on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all catalogs in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces catalogs list --space=my-space \
        --project=my-project --location=us-central1

To filter and list catalogs that contain a my-catalog prefix in the display
name in space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs list --space=my-space \
        --project=my-project --location=us-central1 \
        --filter="displayName:my-catalog*"

To list catalogs sorted by display name in space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs list --space=my-space \
        --project=my-project --location=us-central1 \
        --sort-by=displayName
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/list)

---
### `gcloud design-center spaces catalogs update`

Update a catalog

Update a catalog in a space.

**Synopsis:**
```
gcloud design-center spaces catalogs update
    (CATALOG : --location=LOCATION --space=SPACE)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Catalog resource - Identifier. The catalog name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument catalog on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CATALOG
     ID of the catalog or fully qualified identifier for the catalog.

     To set the catalog attribute:
     + provide the argument catalog on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the catalog resource.

     To set the location attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the catalog resource.

     To set the space attribute:
     + provide the argument catalog on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The catalog description. |
| `--display-name` | DISPLAY_NAME |  | The catalog display name. |


**Examples:**
```bash
To update the display name to My New Catalog Name for the catalog
my-catalog in space my-space, project my-project and location us-central1,
run:

    $ gcloud design-center spaces catalogs update my-catalog \
        --space=my-space --project=my-project --location=us-central1 \
        --display-name="My New Catalog Name"

Or run:

    $ gcloud design-center spaces catalogs update \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog --display-name="My New Catalog Name"

To update the description to My new description for the catalog my-catalog
in space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs update my-catalog \
        --space=my-space --project=my-project --location=us-central1 \
        --description="My new description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/update)

---

## `gcloud design-center spaces catalogs shares` — manage share resources
### `gcloud design-center spaces catalogs shares create`

Create a share

Create a share in a catalog.

**Synopsis:**
```
gcloud design-center spaces catalogs shares create
    (SHARE : --catalog=CATALOG --space=SPACE)
    --destination-space=DESTINATION_SPACE [--async] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Share resource - Identifier. The share name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/shares/$share
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument share on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument share on the command line with a fully specified
   name;
 * provide the argument --location on the command line.

This must be specified.

  SHARE
     ID of the share or fully qualified identifier for the share.

     To set the share attribute:
     + provide the argument share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the share resource.

     To set the catalog attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --space=SPACE
     The space id of the share resource.

     To set the space attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-space` | DESTINATION_SPACE |  | _[This must be specified.]_ ID of the space or fully qualified identifier for the space. To set the space attribute: + provide the argument --destination-space on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--location` | LOCATION |  | For resources [share, destination-space], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |


**Examples:**
```bash
To create a share my-share in catalog my-catalog to destination space
my-destination-space, in space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces catalogs shares create my-share \
        --catalog=my-catalog --space=my-space --project=my-project \
        --location=us-central1 --destination-space=my-destination-space

Or run:

    $ gcloud design-center spaces catalogs shares create \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/shares/my-share \
        --destination-space=my-destination-space

To create the share my-share in catalog my-catalog to destination space
projects/my-descendant-project/locations/us-central1/spaces/my-destination-space
present in a descendant management project my-descendant-project, in the
space my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs shares create my-share \
        --catalog=my-catalog --space=my-space --project=my-project \
        --location=us-central1 \
        --destination-space=projects/my-descendant-project/locations/\
    us-central1/spaces/my-destination-space
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/shares/create)

---
### `gcloud design-center spaces catalogs shares delete`

Delete a share

Delete a share in a catalog.

**Synopsis:**
```
gcloud design-center spaces catalogs shares delete
    (SHARE : --catalog=CATALOG --location=LOCATION --space=SPACE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Share resource - The share name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/shares/$share
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument share on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SHARE
     ID of the share or fully qualified identifier for the share.

     To set the share attribute:
     + provide the argument share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the share resource.

     To set the catalog attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the share resource.

     To set the location attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the share resource.

     To set the space attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the share my-share in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs shares delete my-share \
        --catalog=my-catalog --space=my-space --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs shares delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/shares/my-share

To delete the share my-share in catalog my-catalog, space my-space, project
my-project and location us-central1 asynchronously, run:

    $ gcloud design-center spaces catalogs shares delete my-share \
        --catalog=my-catalog --space=my-space --location=us-central1 \
        --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/shares/delete)

---
### `gcloud design-center spaces catalogs shares describe`

Describe a share

Describe a share in a catalog.

**Synopsis:**
```
gcloud design-center spaces catalogs shares describe
    (SHARE : --catalog=CATALOG --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Share resource - The share name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/shares/$share
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument share on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SHARE
     ID of the share or fully qualified identifier for the share.

     To set the share attribute:
     + provide the argument share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the share resource.

     To set the catalog attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the share resource.

     To set the location attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the share resource.

     To set the space attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the share my-share in catalog my-catalog, space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs shares describe my-share \
        --catalog=my-catalog --space=my-space --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs shares describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/shares/my-share
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/shares/describe)

---
### `gcloud design-center spaces catalogs shares list`

List shares

List shares in a catalog.

**Synopsis:**
```
gcloud design-center spaces catalogs shares list
    (--catalog=CATALOG : --location=LOCATION --space=SPACE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--catalog` | CATALOG |  | _[This must be specified.]_ ID of the catalog or fully qualified identifier for the catalog. To set the catalog attribute: + provide the argument --catalog on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the catalog resource. To set the location attribute: + provide the argument --catalog on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--space` | SPACE |  | _[This must be specified.]_ The space id of the catalog resource. To set the space attribute: + provide the argument --catalog on the command line with a fully specified name; + provide the argument --space on the command line. |


**Examples:**
```bash
To list all shares in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs shares list \
        --catalog=my-catalog --space=my-space --location=us-central1

To list up to 10 shares in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs shares list \
        --catalog=my-catalog --space=my-space --location=us-central1 \
        --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/shares/list)

---
### `gcloud design-center spaces catalogs shares sync`

Sync a share

Sync a share in a catalog.

**Synopsis:**
```
gcloud design-center spaces catalogs shares sync
    (SHARE : --catalog=CATALOG --location=LOCATION --space=SPACE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Share resource - The share name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/shares/$share
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument share on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SHARE
     ID of the share or fully qualified identifier for the share.

     To set the share attribute:
     + provide the argument share on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the share resource.

     To set the catalog attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the share resource.

     To set the location attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the share resource.

     To set the space attribute:
     + provide the argument share on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To sync the share my-share in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs shares sync my-share \
        --catalog=my-catalog --space=my-space --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs shares sync \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/shares/my-share

To sync the share my-share in catalog my-catalog, space my-space, project
my-project and location us-central1 asynchronously, run:

    $ gcloud design-center spaces catalogs shares sync \
        --catalog=my-catalog --space=my-space --location=us-central1 \
        --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/shares/sync)

---

## `gcloud design-center spaces catalogs templates` — manage catalog template resources
### `gcloud design-center spaces catalogs templates create`

Create a catalog template

Create a catalog template.

**Synopsis:**
```
gcloud design-center spaces catalogs templates create
    (TEMPLATE : --catalog=CATALOG --location=LOCATION --space=SPACE)
    --template-category=TEMPLATE_CATEGORY [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--type=TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Identifier. The catalog template name in following
format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/templates/$template
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the template resource.

     To set the catalog attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the template resource.

     To set the space attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--template-category` | one of: application-template ADC application template |  | The category of the ADC template. TEMPLATE_CATEGORY must be one of: application-template ADC application template. component-template ADC component template. composite-solution-template Imported as a single, complex unit without disassembling into components. instance-template ADC application instance. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The catalog template description. |
| `--display-name` | DISPLAY_NAME |  | The display name of a catalog template. |
| `--type` | one of: application An application template is a composition of workload/service/asset templates |  | The Application Design Center assembly template type. TYPE must be one of: application An application template is a composition of workload/service/asset templates. asset An asset template can be used to provision resources that are not services or workloads. composite-application-template A composite application template. helm-application A helm chart based template. helm-chart A helm chart based template. jss-solution A Jumpstart Solution template. service A service template is an App Hub service. service-data-source A service data source template. standard-application-template A standard application template. workload A workload template is an App Hub workload. |


**Examples:**
```bash
To create the catalog template my-template with template category
application-template in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates create \
        my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1 \
        --template-category=application-template

Or run:

    $ gcloud design-center spaces catalogs templates create \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/templates/my-template \
        --template-category=application-template

To create the catalog template my-template with a display name of My
Template, description of My template description and template category of
application-template in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates create \
        my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1 \
        --display-name="My Template" \
        --description="My template description" \
        --template-category=application-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/create)

---
### `gcloud design-center spaces catalogs templates delete`

Delete a catalog template

Delete a catalog template.

**Synopsis:**
```
gcloud design-center spaces catalogs templates delete
    (TEMPLATE : --catalog=CATALOG --location=LOCATION --space=SPACE)
    [--async] [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The catalog template name. Format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/templates/$template
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the template resource.

     To set the catalog attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the template resource.

     To set the space attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--force` |  |  | If set to true, the catalog template's children are also deleted. If false, the catalog template is only deleted if it has no children. |


**Examples:**
```bash
To delete the catalog template my-template in catalog my-catalog, space
my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates delete \
        my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs templates delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/templates/my-template

If your catalog template contains child resources such as catalog template
revisions, force delete the catalog template. To force delete the catalog
template my-template in catalog my-catalog, space my-space, project
my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates delete \
        my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1 --force

To delete the catalog template my-template in catalog my-catalog, space
my-space, project my-project and location us-central1 asynchronously, run:

    $ gcloud design-center spaces catalogs templates delete \
        my-template --catalog=my-catalog --space=my-space \
        --location=us-central1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/delete)

---
### `gcloud design-center spaces catalogs templates describe`

Describe a catalog template

Describe a catalog template.

**Synopsis:**
```
gcloud design-center spaces catalogs templates describe
    (TEMPLATE : --catalog=CATALOG --location=LOCATION --space=SPACE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - The catalog template name in the following format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/templates/$template
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the template resource.

     To set the catalog attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the template resource.

     To set the space attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Examples:**
```bash
To describe the catalog template my-template in catalog my-catalog, space
my-space, project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates describe \
        my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs templates describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/templates/my-template
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/describe)

---
### `gcloud design-center spaces catalogs templates list`

List catalog templates

List catalog templates in a given catalog.

**Synopsis:**
```
gcloud design-center spaces catalogs templates list
    (--catalog=CATALOG : --location=LOCATION --space=SPACE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--catalog` | CATALOG |  | _[This must be specified.]_ ID of the catalog or fully qualified identifier for the catalog. To set the catalog attribute: + provide the argument --catalog on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the catalog resource. To set the location attribute: + provide the argument --catalog on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--space` | SPACE |  | _[This must be specified.]_ The space id of the catalog resource. To set the space attribute: + provide the argument --catalog on the command line with a fully specified name; + provide the argument --space on the command line. |


**Examples:**
```bash
To list all catalog templates in catalog my-catalog, space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates list \
        --catalog=my-catalog --space=my-space --project=my-project \
        --location=us-central1

To filter and list catalog templates that contain a my-template prefix in
the display name in catalog my-catalog, space my-space, project my-project
and location us-central1, run:

    $ gcloud design-center spaces catalogs templates list \
        --catalog=my-catalog --space=my-space --project=my-project \
        --location=us-central1 --filter="displayName:my-template*"

To list up to 10 catalog templates in catalog my-catalog, space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces catalogs templates list \
        --catalog=my-catalog --space=my-space --project=my-project \
        --location=us-central1 --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/list)

---
### `gcloud design-center spaces catalogs templates update`

Update a catalog template

Update a catalog template.

**Synopsis:**
```
gcloud design-center spaces catalogs templates update
    (TEMPLATE : --catalog=CATALOG --location=LOCATION --space=SPACE)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--template-category=TEMPLATE_CATEGORY] [--type=TYPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Template resource - Identifier. The catalog template name in following
format:
projects/$project/locations/$location/spaces/$space/catalogs/$catalog/templates/$template
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument template on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  TEMPLATE
     ID of the template or fully qualified identifier for the template.

     To set the template attribute:
     + provide the argument template on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the template resource.

     To set the catalog attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the template resource.

     To set the location attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the template resource.

     To set the space attribute:
     + provide the argument template on the command line with a fully
       specified name;
     + provide the argument --space on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | The catalog template description. |
| `--display-name` | DISPLAY_NAME |  | The display name of a catalog template. |
| `--template-category` | one of: application-template ADC application template |  | The category of the ADC template. TEMPLATE_CATEGORY must be one of: application-template ADC application template. component-template ADC component template. composite-solution-template Imported as a single, complex unit without disassembling into components. instance-template ADC application instance. |
| `--type` | one of: application An application template is a composition of workload/service/asset templates |  | The Application Design Center assembly template type. TYPE must be one of: application An application template is a composition of workload/service/asset templates. asset An asset template can be used to provision resources that are not services or workloads. composite-application-template A composite application template. helm-application A helm chart based template. helm-chart A helm chart based template. jss-solution A Jumpstart Solution template. service A service template is an App Hub service. service-data-source A service data source template. standard-application-template A standard application template. workload A workload template is an App Hub workload. |


**Examples:**
```bash
To update the display name to My New Template Name for the catalog template
my-template in catalog my-catalog, space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces catalogs templates update \
        my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1 \
        --display-name="My New Template Name"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/update)

---

## `gcloud design-center spaces catalogs templates revisions` — manage catalog template revision resources
### `gcloud design-center spaces catalogs templates revisions create`

Create a new catalog template revision

Create a new catalog template revision.

**Synopsis:**
```
gcloud design-center spaces catalogs templates revisions create
    (REVISION : --catalog=CATALOG
      --location=LOCATION --space=SPACE --template=TEMPLATE)
    (--application-template-revision-source=APPLICATION_TEMPLATE_REVISION_SOURCE | --gcs-source-uri=GCS_SOURCE_URI | --developer-connect-repo=DEVELOPER_CONNECT_REPO --developer-connect-repo-dir=DEVELOPER_CONNECT_REPO_DIR --developer-connect-repo-ref=DEVELOPER_CONNECT_REPO_REF | [--git-source-ref-tag=GIT_SOURCE_REF_TAG --git-source-repo=GIT_SOURCE_REPO : --git-source-dir=GIT_SOURCE_DIR] | [--oci-repo-uri=OCI_REPO_URI : --oci-repo-version=OCI_REPO_VERSION])
    [--async] [--description=DESCRIPTION] [--metadata=METADATA]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - The revision to create. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument revision on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The ID of the catalog.

     To set the catalog attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The Cloud location for the revision.

     To set the location attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The ID of the space.

     To set the space attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --space on the command line.

  --template=TEMPLATE
     The ID of the template.

     To set the template attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --template on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application-template-revision-source` | APPLICATION_TEMPLATE_REVISION_SOURCE |  | _[Exactly one of these must be specified:]_ Application template revision to use as source. Example: projects/my-project/locations/us-central1/spaces/my-space/catalogs/my-catalog/templates/my-template/revisions/r1 |
| `--gcs-source-uri` | GCS_SOURCE_URI |  | _[Exactly one of these must be specified:]_ Google Cloud Storage URI for source. Example: gs://my-bucket/my-template. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | A description for the revision. |
| `--metadata` | METADATA |  | Path to a local YAML file containing the template metadata. Example: "path/to/metadata.yaml". |


**Examples:**
```bash
To create a new catalog template revision named my-revision for the
template my-template, within the catalog my-catalog and space my-space, in
location us-central1 and project my-project, using a Developer Connect
repository as the source, run:

    $ gcloud design-center spaces catalogs templates revisions create \
         my-revision --project=my-project --location=us-central1 \
         --space=my-space --catalog=my-catalog --template=my-template \
         --description="My test revision description" \
         --developer-connect-repo=projects/my-project/locations/\
     us-central1/connections/my-connection/gitRepositoryLinks/my-repo \
         --developer-connect-repo-ref=refs/tags/v1.0.0 \
         --developer-connect-repo-dir=modules/my-product

    Or run using the full resource name:

    $ gcloud design-center spaces catalogs templates revisions create \
       projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/templates/my-template/revisions/my-revision \
        --description="My test revision description" \
        --developer-connect-repo=projects/my-project/locations/\
    us-central1/connections/my-connection/gitRepositoryLinks/my-repo \
        --developer-connect-repo-ref=refs/tags/v1.0.0 \
        --developer-connect-repo-dir=modules/my-product

    To create a revision using a metadata file from a local path, run:

    $ gcloud design-center spaces catalogs templates revisions create \
       my-revision --project=my-project --location=us-central1 \
       --space=my-space --catalog=my-catalog --template=my-template \
       --developer-connect-repo=projects/my-project/locations/\
    us-central1/connections/my-connection/gitRepositoryLinks/my-repo \
        --developer-connect-repo-ref=refs/tags/v1.0.0 \
        --developer-connect-repo-dir=modules/my-product \
        --metadata=/path/to/metadata.yaml

    To create a revision using a Git repository as the source, run:

    $ gcloud design-center spaces catalogs templates revisions create \
       my-revision --project=my-project --location=us-central1 \
       --space=my-space --catalog=my-catalog --template=my-template \
       --git-source-repo=GoogleCloudPlatform/\
    terraform-google-cloud-run --git-source-ref-tag=v1.0.0 \
        --git-source-dir=modules/my-product

    To create a revision using a Google Cloud Storage URI as the source, run:

    $ gcloud design-center spaces catalogs templates revisions create \
       my-revision --project=my-project --location=us-central1 \
       --space=my-space --catalog=my-catalog --template=my-template \
       --gcs-source-uri=gs://my-bucket/my-template

    To create a revision using an OCI repository as the source, run:

    $ gcloud design-center spaces catalogs templates revisions create \
       my-revision --project=my-project --location=us-central1 \
       --space=my-space --catalog=my-catalog --template=my-template \
       --oci-repo-uri=oci://us-west1-docker.pkg.dev/my-project/\
    my-repo/my-chart --oci-repo-version=1.0.0

    To create a revision using an Application Template Revision as the source, run:

    $ gcloud design-center spaces catalogs templates revisions create \
       my-revision --project=my-project --location=us-central1 \
       --space=my-space --catalog=my-catalog --template=my-template \
       --application-template-revision-source=projects/my-project/\
    locations/us-central1/spaces/my-space/applicationTemplates/\
    my-app-template/revisions/a1

    To create a revision using Git source and a metadata file from a local path, run:

    $ gcloud design-center spaces catalogs templates revisions create \
       my-revision --project=my-project --location=us-central1 \
       --space=my-space --catalog=my-catalog --template=my-template \
       --git-source-repo=GoogleCloudPlatform/\
    terraform-google-cloud-run --git-source-ref-tag=v1.0.0 \
        --git-source-dir=modules/my-product \
        --metadata=/path/to/metadata.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/revisions/create)

---
### `gcloud design-center spaces catalogs templates revisions delete`

Delete a catalog template revision

Delete a catalog template revision.

**Synopsis:**
```
gcloud design-center spaces catalogs templates revisions delete
    (REVISION : --catalog=CATALOG
      --location=LOCATION --space=SPACE --template=TEMPLATE) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - The template revision name. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument revision on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the revision resource.

     To set the catalog attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the revision resource.

     To set the location attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the revision resource.

     To set the space attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --space on the command line.

  --template=TEMPLATE
     The template id of the revision resource.

     To set the template attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --template on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the catalog template revision my-revision in template
my-template, catalog my-catalog, space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces catalogs templates revisions delete \
        my-revision --template=my-template --catalog=my-catalog \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs templates revisions delete \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/templates/my-template/revisions/my-revision

To delete the catalog template revision my-revision in template
my-template, catalog my-catalog, space my-space, project my-project and
location us-central1 asynchronously, run:

    $ gcloud design-center spaces catalogs templates revisions delete \
        my-revision --template=my-template --catalog=my-catalog \
        --space=my-space --location=us-central1 --async
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/revisions/delete)

---
### `gcloud design-center spaces catalogs templates revisions describe`

Describe a catalog template revision

Describe a catalog template revision.

**Synopsis:**
```
gcloud design-center spaces catalogs templates revisions describe
    (REVISION : --catalog=CATALOG
      --location=LOCATION --space=SPACE --template=TEMPLATE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - The catalog template revisions name. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument revision on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  REVISION
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument revision on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --catalog=CATALOG
     The catalog id of the revision resource.

     To set the catalog attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --catalog on the command line.

  --location=LOCATION
     The location id of the revision resource.

     To set the location attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --space=SPACE
     The space id of the revision resource.

     To set the space attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --space on the command line.

  --template=TEMPLATE
     The template id of the revision resource.

     To set the template attribute:
     + provide the argument revision on the command line with a fully
       specified name;
     + provide the argument --template on the command line.
```

**Examples:**
```bash
To describe the catalog template revision my-revision in template
my-template, catalog my-catalog, space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces catalogs templates revisions \
        describe my-revision --template=my-template \
        --catalog=my-catalog --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces catalogs templates revisions \
        describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    catalogs/my-catalog/templates/my-template/revisions/my-revision
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/revisions/describe)

---
### `gcloud design-center spaces catalogs templates revisions list`

List catalog template revisions

List catalog template revisions in a given template.

**Synopsis:**
```
gcloud design-center spaces catalogs templates revisions list
    (--template=TEMPLATE
      : --catalog=CATALOG --location=LOCATION --space=SPACE)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--template` | TEMPLATE |  | _[This must be specified.]_ ID of the template or fully qualified identifier for the template. To set the template attribute: + provide the argument --template on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--catalog` | CATALOG |  | _[This must be specified.]_ The catalog id of the template resource. To set the catalog attribute: + provide the argument --template on the command line with a fully specified name; + provide the argument --catalog on the command line. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the template resource. To set the location attribute: + provide the argument --template on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--space` | SPACE |  | _[This must be specified.]_ The space id of the template resource. To set the space attribute: + provide the argument --template on the command line with a fully specified name; + provide the argument --space on the command line. |


**Examples:**
```bash
To list all catalog template revisions in template my-template, catalog
my-catalog, space my-space, project my-project and location us-central1,
run:

    $ gcloud design-center spaces catalogs templates revisions list \
        --template=my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1

To list up to 10 catalog template revisions in template my-template,
catalog my-catalog, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces catalogs templates revisions list \
        --template=my-template --catalog=my-catalog --space=my-space \
        --project=my-project --location=us-central1 --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/catalogs/templates/revisions/list)

---

## `gcloud design-center spaces shared-templates` — manage shared template resources
### `gcloud design-center spaces shared-templates describe`

Describe a shared template

Describe a shared template.

**Synopsis:**
```
gcloud design-center spaces shared-templates describe SHARED_TEMPLATE
    [--location=LOCATION]
    [--google-catalog | --project=PROJECT --space=SPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SHARED_TEMPLATE
   ID of the sharedTemplate or fully qualified identifier for the
   sharedTemplate. Format:
   projects/$project/locations/$location/spaces/$space/sharedTemplates/$sharedTemplate
   To set the shared_template attribute:
   * provide the fully qualified identifier shared_template on the
     command line;
   * provide the argument shared_template which represents the shared
     template id and the other arguments --location, --project, --space or
     --google-catalog on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location id of the sharedTemplate resource. To set the location attribute: * provide the argument shared_template on the command line with a fully specified name; * provide the argument --location on the command line. |


**Examples:**
```bash
To describe the shared template my-shared-template in space my-space,
project my-project and location us-central1, run:

    $ gcloud design-center spaces shared-templates describe \
        my-shared-template --space=my-space --project=my-project \
        --location=us-central1

Or run:

    $ gcloud design-center spaces shared-templates describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    sharedTemplates/my-shared-template

To describe a shared template google-template from the Google Catalog and
location us-central1, run:

    $ gcloud design-center spaces shared-templates describe \
        google-template --google-catalog --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/shared-templates/describe)

---
### `gcloud design-center spaces shared-templates list`

List shared templates

List shared templates in a given space.

**Synopsis:**
```
gcloud design-center spaces shared-templates list
    (--google-catalog | [--space=SPACE : --project=PROJECT])
    [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--google-catalog` |  |  | _[Exactly one of these must be specified:]_ If provided, lists all shared template from the Google Catalog. This sets the project to "gcpdesigncenter" and space to "googlespace". |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location id of the space resource. To set the location attribute: * provide the argument --space on the command line with a fully specified name; * provide the argument --location on the command line. |


**Examples:**
```bash
To list all shared templates in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces shared-templates list \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces shared-templates list \
        --space=projects/my-project/locations/us-central1/spaces/\
    my-space

To list all shared templates from the Google Catalog in location
us-central1, run:

    $ gcloud design-center spaces shared-templates list \
        --google-catalog --location=us-central1

To filter and list shared templates that contain a my-shared-template
prefix in the display name in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces shared-templates list \
        --space=my-space --project=my-project --location=us-central1 \
        --filter="displayName:my-shared-template*"

To list up to 10 shared templates in space my-space, project my-project and
location us-central1, run:

    $ gcloud design-center spaces shared-templates list \
        --space=my-space --project=my-project --location=us-central1 \
        --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/shared-templates/list)

---

## `gcloud design-center spaces shared-templates revisions` — manage shared template revision resources
### `gcloud design-center spaces shared-templates revisions describe`

Describe a shared template revision

Describe a shared template revision.

**Synopsis:**
```
gcloud design-center spaces shared-templates revisions describe REVISION
    [--location=LOCATION] [--shared-template=SHARED_TEMPLATE]
    [--google-catalog | --project=PROJECT --space=SPACE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
REVISION
   ID of the revision or fully qualified identifier for the
   sharedTemplateRevision. Format:
   projects/$project/locations/$location/spaces/$space/sharedTemplates/$sharedTemplate/revisions/$revision
   To set the revision attribute:
   * provide the fully qualified identifier revision on the command
     line;
   * provide the argument revision which represents the revision id and
     the other arguments --shared-template, --location, --project, --space
     or --google-catalog on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location id of the revision resource. To set the location attribute: * provide the argument revision on the command line with a fully specified name; * provide the argument --location on the command line. |
| `--shared-template` | SHARED_TEMPLATE |  | The sharedTemplate id of the revision resource. To set the shared-template attribute: * provide the argument revision on the command line with a fully specified name; * provide the argument --shared-template on the command line. |


**Examples:**
```bash
To describe the shared template revision my-revision in shared template
my-shared-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces shared-templates revisions describe \
        my-revision --shared-template=my-shared-template \
        --space=my-space --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces shared-templates revisions describe \
        projects/my-project/locations/us-central1/spaces/my-space/\
    sharedTemplates/my-shared-template/revisions/my-revision

To describe a shared template revision my-revision in shared template
google-template from the Google Catalog and location us-central1, run:

    $ gcloud design-center spaces shared-templates revisions describe \
        my-revision --shared-template=google-template --google-catalog \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/shared-templates/revisions/describe)

---
### `gcloud design-center spaces shared-templates revisions list`

List shared template revisions

List shared template revisions in a given shared template.

**Synopsis:**
```
gcloud design-center spaces shared-templates revisions list
    --shared-template=SHARED_TEMPLATE [--location=LOCATION]
    [--google-catalog | --project=PROJECT --space=SPACE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--shared-template` | SHARED_TEMPLATE |  | ID of the sharedTemplate or fully qualified identifier for the sharedTemplate. To set the shared-template attribute: * provide the argument --shared-template on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | The location id of the sharedTemplate resource. To set the location attribute: * provide the argument --shared-template on the command line with a fully specified name; * provide the argument --location on the command line. |


**Examples:**
```bash
To list all shared template revisions in shared template
my-shared-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces shared-templates revisions list \
        --shared-template=my-shared-template --space=my-space \
        --project=my-project --location=us-central1

Or run:

    $ gcloud design-center spaces shared-templates revisions list \
        --shared-template=projects/my-project/locations/us-central1/\
    spaces/my-space/sharedTemplates/my-shared-template

To list all shared template revisions for shared template google-template
from the Google Catalog in location us-central1, run:

    $ gcloud design-center spaces shared-templates revisions list \
        --shared-template=google-template --google-catalog \
        --location=us-central1

To list up to 10 shared template revisions in shared template
my-shared-template, space my-space, project my-project and location
us-central1, run:

    $ gcloud design-center spaces shared-templates revisions list \
        --shared-template=my-shared-template --space=my-space \
        --project=my-project --location=us-central1 --limit=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/design-center/spaces/shared-templates/revisions/list)

---