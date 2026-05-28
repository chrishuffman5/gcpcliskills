# gcloud apphub applications

manage App Hub Applications

### `gcloud apphub applications add-iam-policy-binding`

Add IAM policy binding to an Apphub application

Add IAM policy binding to an Apphub application.

**Synopsis:**
```
gcloud apphub applications add-iam-policy-binding
    (APPLICATION : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of roles/apphub.viewer for the
user test-user@gmail.com to Application my-app in location us-east1, run:

    $ gcloud apphub applications add-iam-policy-binding my-app \
        --location=us-east1 --role=roles/apphub.viewer \
        --member=user:test-user@gmail.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/add-iam-policy-binding)

---
### `gcloud apphub applications create`

Create an Apphub application

Create an Apphub application.

**Synopsis:**
```
gcloud apphub applications create (APPLICATION : --location=LOCATION)
    --scope-type=SCOPE_TYPE [--async]
    [--business-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--criticality-type=CRITICALITY_TYPE] [--description=DESCRIPTION]
    [--developer-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--display-name=DISPLAY_NAME] [--environment-type=ENVIRONMENT_TYPE]
    [--operator-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope-type` | SCOPE_TYPE |  | Scope of the Application. SCOPE_TYPE must be one of: GLOBAL Represents a global application REGIONAL Represents a regional application |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--business-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Business owners of the application |
| `--criticality-type` | CRITICALITY_TYPE |  | Criticality Type of the application. CRITICALITY_TYPE must be one of: HIGH High impact LOW Low impact MEDIUM Medium impact MISSION_CRITICAL Mission critical service, application or workload TYPE_UNSPECIFIED Unspecified criticality type |
| `--description` | DESCRIPTION |  | Description of the Application |
| `--developer-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Developer owners of the application |
| `--display-name` | DISPLAY_NAME |  | Human-friendly display name |
| `--environment-type` | ENVIRONMENT_TYPE |  | Environment Type of the application. ENVIRONMENT_TYPE must be one of: DEVELOPMENT Development environment PRODUCTION Production environment STAGING Staging environment TEST Test environment TYPE_UNSPECIFIED Unspecified environment type |
| `--operator-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Operator owners of the application |


**Examples:**
```bash
To create the Application my-app with scope type REGIONAL in location
us-east1, run:

    $ gcloud apphub applications create my-app --location=us-east1 \
        --scope-type=REGIONAL
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/create)

---
### `gcloud apphub applications delete`

Delete an Apphub application

Delete an Apphub application.

**Synopsis:**
```
gcloud apphub applications delete (APPLICATION : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the Application my-app in location us-east1, run:

    $ gcloud apphub applications delete my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/delete)

---
### `gcloud apphub applications describe`

Describe an Apphub application

Describe an Apphub application.

**Synopsis:**
```
gcloud apphub applications describe (APPLICATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the Application my-app in location us-east1, run:

    $ gcloud apphub applications describe my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/describe)

---
### `gcloud apphub applications get-iam-policy`

Get the IAM policy for an Apphub application

Returns an empty policy if the application does not have an existing IAM
policy set.

**Synopsis:**
```
gcloud apphub applications get-iam-policy
    (APPLICATION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the application IAM policy for the Application my-app in in location
us-east1, run:

    $ gcloud apphub applications get-iam-policy my-app \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/get-iam-policy)

---
### `gcloud apphub applications list`

List Apphub applications

List Apphub applications.

**Synopsis:**
```
gcloud apphub applications list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all applications in locations us-east1, run:

    $ gcloud apphub applications list --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/list)

---
### `gcloud apphub applications remove-iam-policy-binding`

Remove IAM policy binding from an Apphub application

Remove IAM policy binding from an Apphub application.

**Synopsis:**
```
gcloud apphub applications remove-iam-policy-binding
    (APPLICATION : --location=LOCATION) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of roles/apphub.viewer for the
user test-user@gmail.com from Application my-app in location us-east1, run:

    $ gcloud apphub applications remove-iam-policy-binding my-app \
        --location=us-east1 --role=roles/apphub.viewer \
        --member=user:test-user@gmail.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/remove-iam-policy-binding)

---
### `gcloud apphub applications set-iam-policy`

Set the IAM policy for an Apphub application as defined in a JSON/YAML file

See https://cloud.google.com/iam/docs/managing-policies for details of the
policy file format and contents.

**Synopsis:**
```
gcloud apphub applications set-iam-policy
    (APPLICATION : --location=LOCATION) POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
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
To set the application IAM policy using a json file 'my_policy.json' for
the Application my-app in location us-east1, run:

    $ gcloud apphub applications set-iam-policy my-app \
        --location=us-east1 /path/to/my_policy.json

To set the application IAM policy using a yaml file 'my_policy.yaml for the
Application my-app in location us-east1, run:

    $ gcloud apphub applications set-iam-policy my-app \
        --location=us-east1 /path/to/my_policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/set-iam-policy)

---
### `gcloud apphub applications update`

Update an Apphub application

Update an Apphub application.

**Synopsis:**
```
gcloud apphub applications update (APPLICATION : --location=LOCATION)
    [--async] [--business-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--criticality-type=CRITICALITY_TYPE] [--description=DESCRIPTION]
    [--developer-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--display-name=DISPLAY_NAME] [--environment-type=ENVIRONMENT_TYPE]
    [--operator-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Application resource - The Application ID. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

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
     The Cloud location for the application.

     To set the location attribute:
     + provide the argument application on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--business-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Business owners of the application |
| `--criticality-type` | CRITICALITY_TYPE |  | Criticality Type of the application. CRITICALITY_TYPE must be one of: HIGH High impact LOW Low impact MEDIUM Medium impact MISSION_CRITICAL Mission critical service, application or workload TYPE_UNSPECIFIED Unspecified criticality type |
| `--description` | DESCRIPTION |  | Description of the Application |
| `--developer-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Developer owners of the application |
| `--display-name` | DISPLAY_NAME |  | Human-friendly display name |
| `--environment-type` | ENVIRONMENT_TYPE |  | Environment Type of the application. ENVIRONMENT_TYPE must be one of: DEVELOPMENT Development environment PRODUCTION Production environment STAGING Staging environment TEST Test environment TYPE_UNSPECIFIED Unspecified environment type |
| `--operator-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Operator owners of the application |


**Examples:**
```bash
To update the Application my-app with a new environment prod in location
us-east1, run:

    $ gcloud apphub applications update my-app --location=us-east1 \
        --environment-type=TEST
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/update)

---

## `gcloud apphub applications services` — manage App Hub Application Services
### `gcloud apphub applications services create`

Create an Apphub application service

Create an Apphub application service.

**Synopsis:**
```
gcloud apphub applications services create
    (SERVICE : --application=APPLICATION --location=LOCATION)
    --discovered-service=DISCOVERED_SERVICE [--async]
    [--business-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--criticality-type=CRITICALITY_TYPE] [--description=DESCRIPTION]
    [--developer-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--display-name=DISPLAY_NAME] [--environment-type=ENVIRONMENT_TYPE]
    [--operator-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service resource. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument SERVICE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument SERVICE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the service.

     To set the location attribute:
     + provide the argument SERVICE on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--discovered-service` | DISCOVERED_SERVICE |  | _[This must be specified.]_ ID of the discoveredService or fully qualified identifier for the discoveredService. To set the discovered_service attribute: + provide the argument --discovered-service on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--business-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Business owners of the service |
| `--criticality-type` | CRITICALITY_TYPE |  | Criticality Type of the service. CRITICALITY_TYPE must be one of: HIGH High impact LOW Low impact MEDIUM Medium impact MISSION_CRITICAL Mission critical service, application or workload TYPE_UNSPECIFIED Unspecified criticality type |
| `--description` | DESCRIPTION |  | Description of the service |
| `--developer-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Developer owners of the service |
| `--display-name` | DISPLAY_NAME |  | Human-friendly display name |
| `--environment-type` | ENVIRONMENT_TYPE |  | Environment Type of the service. ENVIRONMENT_TYPE must be one of: DEVELOPMENT Development environment PRODUCTION Production environment STAGING Staging environment TEST Test environment TYPE_UNSPECIFIED Unspecified environment type |
| `--operator-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Operator owners of the service |


**Examples:**
```bash
To create the Service my-service with discovered service
my-discovered-service in the Application my-app in location us-east1, run:

    $ gcloud apphub applications services create my-service \
        --application=my-app --location=us-east1 \
        --discovered-service=my-discovered-service
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/services/create)

---
### `gcloud apphub applications services delete`

Delete an Apphub application service

Delete an Apphub application service.

**Synopsis:**
```
gcloud apphub applications services delete
    (SERVICE : --application=APPLICATION --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service ID. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the Service my-service from the Application my-app in location
us-east1, run:

    $ gcloud apphub applications services delete my-service \
        --application=my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/services/delete)

---
### `gcloud apphub applications services describe`

Describe an Apphub application service

Describe an Apphub application service.

**Synopsis:**
```
gcloud apphub applications services describe
    (SERVICE : --application=APPLICATION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service ID. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the Service my-service in the Application my-app in location
us-east1, run:

    $ gcloud apphub applications services describe my-service \
        --application=my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/services/describe)

---
### `gcloud apphub applications services list`

List Apphub application services

List Apphub application services.

**Synopsis:**
```
gcloud apphub applications services list
    (--application=APPLICATION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application` | APPLICATION |  | _[This must be specified.]_ ID of the application or fully qualified identifier for the application. To set the application attribute: + provide the argument --application on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Cloud location for the application. To set the location attribute: + provide the argument --application on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all Services in the Application my-app in location us-east1, run:

    $ gcloud apphub applications services list --application=my-app \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/services/list)

---
### `gcloud apphub applications services update`

Update an Apphub application service

Update an Apphub application service.

**Synopsis:**
```
gcloud apphub applications services update
    (SERVICE : --application=APPLICATION --location=LOCATION) [--async]
    [--business-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--criticality-type=CRITICALITY_TYPE] [--description=DESCRIPTION]
    [--developer-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--display-name=DISPLAY_NAME] [--environment-type=ENVIRONMENT_TYPE]
    [--operator-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Service resource - The Service ID. The arguments in this group can be used
to specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument service on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SERVICE
     ID of the service or fully qualified identifier for the service.

     To set the service attribute:
     + provide the argument service on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the service.

     To set the location attribute:
     + provide the argument service on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--business-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Business owners of the service |
| `--criticality-type` | CRITICALITY_TYPE |  | Criticality Type of the service. CRITICALITY_TYPE must be one of: HIGH High impact LOW Low impact MEDIUM Medium impact MISSION_CRITICAL Mission critical service, application or workload TYPE_UNSPECIFIED Unspecified criticality type |
| `--description` | DESCRIPTION |  | Description of the service |
| `--developer-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Developer owners of the service |
| `--display-name` | DISPLAY_NAME |  | Human-friendly display name |
| `--environment-type` | ENVIRONMENT_TYPE |  | Environment Type of the service. ENVIRONMENT_TYPE must be one of: DEVELOPMENT Development environment PRODUCTION Production environment STAGING Staging environment TEST Test environment TYPE_UNSPECIFIED Unspecified environment type |
| `--operator-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Operator owners of the service |


**Examples:**
```bash
To update the Service my-service with a new environment prod in the
Application my-app in location us-east1, run:

    $ gcloud apphub applications services update my-service \
        --environment-type=TEST --application=my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/services/update)

---

## `gcloud apphub applications workloads` — manage App Hub Application Workloads
### `gcloud apphub applications workloads create`

Create an Apphub application workload

Create an Apphub application workload.

**Synopsis:**
```
gcloud apphub applications workloads create
    (WORKLOAD : --application=APPLICATION --location=LOCATION)
    --discovered-workload=DISCOVERED_WORKLOAD [--async]
    [--business-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--criticality-type=CRITICALITY_TYPE] [--description=DESCRIPTION]
    [--developer-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--display-name=DISPLAY_NAME] [--environment-type=ENVIRONMENT_TYPE]
    [--operator-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Workload resource. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument WORKLOAD on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument WORKLOAD on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument WORKLOAD on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the workload.

     To set the location attribute:
     + provide the argument WORKLOAD on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--discovered-workload` | DISCOVERED_WORKLOAD |  | _[This must be specified.]_ ID of the discoveredWorkload or fully qualified identifier for the discoveredWorkload. To set the discovered_workload attribute: + provide the argument --discovered-workload on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--business-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Business owners of the workload |
| `--criticality-type` | CRITICALITY_TYPE |  | Criticality Type of the workload. CRITICALITY_TYPE must be one of: HIGH High impact LOW Low impact MEDIUM Medium impact MISSION_CRITICAL Mission critical service, application or workload TYPE_UNSPECIFIED Unspecified criticality type |
| `--description` | DESCRIPTION |  | Description of the Workload |
| `--developer-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Developer owners of the workload |
| `--display-name` | DISPLAY_NAME |  | Human-friendly display name |
| `--environment-type` | ENVIRONMENT_TYPE |  | Environment Type of the workload. ENVIRONMENT_TYPE must be one of: DEVELOPMENT Development environment PRODUCTION Production environment STAGING Staging environment TEST Test environment TYPE_UNSPECIFIED Unspecified environment type |
| `--operator-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Operator owners of the workload |


**Examples:**
```bash
To create the Workload my-workload with discovered workload
my-discovered-workload in the Application my-app in location us-east1, run:

    $ gcloud apphub applications workloads create my-workload \
        --application=my-app --location=us-east1 \
        --discovered-workload=my-discovered-workload
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/workloads/create)

---
### `gcloud apphub applications workloads delete`

Delete an Apphub application workload

Delete an Apphub application workload.

**Synopsis:**
```
gcloud apphub applications workloads delete
    (WORKLOAD : --application=APPLICATION --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Workload ID. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete the Workload my-workload from the Application my-app in location
us-east1, run:

    $ gcloud apphub applications workloads delete my-workload \
        --application=my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/workloads/delete)

---
### `gcloud apphub applications workloads describe`

Describe an Apphub application workload

Describe an Apphub application workload.

**Synopsis:**
```
gcloud apphub applications workloads describe
    (WORKLOAD : --application=APPLICATION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Workload ID. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the Workload my-workload in the Application my-app in location
us-east1, run:

    $ gcloud apphub applications workloads describe my-workload \
        --application=my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/workloads/describe)

---
### `gcloud apphub applications workloads list`

List Apphub application workloads

List Apphub application workloads.

**Synopsis:**
```
gcloud apphub applications workloads list
    (--application=APPLICATION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--application` | APPLICATION |  | _[This must be specified.]_ ID of the application or fully qualified identifier for the application. To set the application attribute: + provide the argument --application on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The Cloud location for the application. To set the location attribute: + provide the argument --application on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all Workloads in the Application my-app in location us-east1, run:

    $ gcloud apphub applications workloads list --application=my-app \
        --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/workloads/list)

---
### `gcloud apphub applications workloads update`

Update an Apphub application workload

Update an Apphub application workload.

**Synopsis:**
```
gcloud apphub applications workloads update
    (WORKLOAD : --application=APPLICATION --location=LOCATION) [--async]
    [--business-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--criticality-type=CRITICALITY_TYPE] [--description=DESCRIPTION]
    [--developer-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [--display-name=DISPLAY_NAME] [--environment-type=ENVIRONMENT_TYPE]
    [--operator-owners=[display-name=DISPLAY-NAME],[email=EMAIL]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Workload resource - The Workload ID. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument workload on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  WORKLOAD
     ID of the workload or fully qualified identifier for the workload.

     To set the workload attribute:
     + provide the argument workload on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --application=APPLICATION
     Name for the application

     To set the application attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --application on the command line.

  --location=LOCATION
     The Cloud location for the workload.

     To set the location attribute:
     + provide the argument workload on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--business-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Business owners of the workload |
| `--criticality-type` | CRITICALITY_TYPE |  | Criticality Type of the workload. CRITICALITY_TYPE must be one of: HIGH High impact LOW Low impact MEDIUM Medium impact MISSION_CRITICAL Mission critical service, application or workload TYPE_UNSPECIFIED Unspecified criticality type |
| `--description` | DESCRIPTION |  | Description of the Workload |
| `--developer-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Developer owners of the workload |
| `--display-name` | DISPLAY_NAME |  | Human-friendly display name |
| `--environment-type` | ENVIRONMENT_TYPE |  | Environment Type of the workload. ENVIRONMENT_TYPE must be one of: DEVELOPMENT Development environment PRODUCTION Production environment STAGING Staging environment TEST Test environment TYPE_UNSPECIFIED Unspecified environment type |
| `--operator-owners` | [display-name=DISPLAY-NAME],[email=EMAIL] |  | Operator owners of the workload |


**Examples:**
```bash
To update the Workload my-workload with a new environment prod in the
Application my-app in location us-east1, run:

    $ gcloud apphub applications workloads update my-workload \
        --environment-type=TEST --application=my-app --location=us-east1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apphub/applications/workloads/update)

---