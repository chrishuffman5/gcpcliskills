# gcloud access-context-manager cloud-bindings

manage Access Context Manager cloud access bindings

### `gcloud access-context-manager cloud-bindings create`

Create cloud access bindings for a specific group

Create a new cloud access binding. The access level and/or session settings
will be globally bound with the group.

To apply access level and/or session settings to a specific application,
specify the restricted application in the 'binding-file'. In such case, the
access level and/or session settings specified in the yaml file will be
bound with the group and the restricted applications.

**Synopsis:**
```
gcloud access-context-manager cloud-bindings create --group-key=GROUP_KEY
    [--binding-file=YAML_FILE] [--dry-run-level=[DRY_RUN_LEVEL,...]]
    [--level=[LEVEL,...]] [--organization=ORGANIZATION]
    [--session-length=SESSION_LENGTH]
    [--session-reauth-method=SESSION_REAUTH_METHOD; default="login"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-key` | GROUP_KEY |  | Google Group ID whose members are subject to the restrictions of this binding. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--binding-file` | YAML_FILE |  | Path to the file that contains a Google Cloud Platform user access binding. This file contains a YAML-compliant object representing a GcpUserAccessBinding (as described in the API reference) containing ScopedAccessSettings only. No other binding fields are allowed. |
| `--dry-run-level` | [DRY_RUN_LEVEL,...] |  | The dry run access level that binds to the given group. The dry run access level will be evaluated but won't be enforced. Denial on dry run access level will be logged. The input must be the full identifier of an access level, such as accessPolicies/123/accessLevels/new-def. |
| `--level` | [LEVEL,...] |  | The access level that binds to the given group. The input must be the full identifier of an access level, such as accessPolicies/123/accessLevels/abc. |
| `--organization` | ORGANIZATION |  | Parent organization for this binding. |
| `--session-length` | SESSION_LENGTH |  | The maximum lifetime of a user session provided as an ISO 8601 duration string. Must be at least one hour or zero seconds, and no more than twenty-four hours. Granularity is limited to seconds. When --session-length=0 then users in the group attached to this binding will have infinite session length, effectively disabling the session settings. A session begins when a user signs in successfully. If a user signs out before the end of the session lifetime, a new login creates a new session with a fresh lifetime. When a session expires, the user is asked to re-authenticate in accordance with session-method. Setting --session-reauth-method when --session-length is empty raises an error. |
| `--session-reauth-method` | one of: login The user must complete a regular login | login | Specifies the type of re-authentication challenge given to the user when their session expires. Defaults to --session-reauth-method=login if unspecified and --session-length is set. Cannot be used when --session-length is empty or 0. SESSION_REAUTH_METHOD must be one of: login The user must complete a regular login. password The user will only be required to enter their password. security-key The user must re-autheticate using their security key. Before enabling this session reauth method, ensure a security key is properly configured for the user. For help configuring your security key, see https://support.google.com/a/answer/2537800?hl=en#zippy=%2Cview-add-or-remove-security-keys |


**Examples:**
```bash
To create a new cloud access binding, run:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key \
        --level=accessPolicies/123/accessLevels/abc

To create a new cloud access binding for particular applications using a
yaml file, run:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key --organization='1234567890' \
        --binding-file='binding.yaml'

To create a new global cloud access binding, and for particular
applications using a yaml file, run:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key \
        --level=accessPolicies/123/accessLevels/abc \
        --organization='1234567890' --binding-file='binding.yaml'

To create a new cloud access binding for the dry run access level, run:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key \
        --level=accessPolicies/123/accessLevels/abc \
        --dry-run-level=accessPolicies/123/accessLevels/def

To create a new cloud access binding with global session settings, specify
your session length using an ISO duration string and the session-length
flag. For example:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key --organization='1234567890' \
        --session-length=2h

To set a particular session reauth method for these session settings, run:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key --organization='1234567890' \
        --session-length=2h --session-reauth-method=LOGIN

To create session settings for a particular application, supply a YAML file
and run:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key --organization='1234567890' \
        --binding-file='binding.yaml'

Global and per-app session settings can be set on the same group, along
with access levels. For example:

    $ gcloud access-context-manager cloud-bindings create \
        --group-key=my-group-key --organization='1234567890' \
        --session-length=2h --session-reauth-method=LOGIN \
        --level=accessPolicies/123/accessLevels/abc \
        --dry-run-level=accessPolicies/123/accessLevels/def \
        --binding-file='binding.yaml'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/cloud-bindings/create)

---
### `gcloud access-context-manager cloud-bindings delete`

Delete a cloud access binding

Delete an existing cloud access binding.

**Synopsis:**
```
gcloud access-context-manager cloud-bindings delete
    (--binding=BINDING : --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--binding` | BINDING |  | _[This must be specified.]_ ID of the cloud-access-binding or fully qualified identifier for the cloud-access-binding. To set the binding attribute: + provide the argument --binding on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The ID of the organization. To set the organization attribute: + provide the argument --binding on the command line with a fully specified name; + provide the argument --organization on the command line; + set the property access_context_manager/organization. |


**Examples:**
```bash
To delete an existing cloud access binding, run:

    $ gcloud access-context-manager cloud-bindings delete \
        --binding=binding-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/cloud-bindings/delete)

---
### `gcloud access-context-manager cloud-bindings describe`

Show details about a cloud access binding

Show details about an existing cloud access binding.

**Synopsis:**
```
gcloud access-context-manager cloud-bindings describe
    (--binding=BINDING : --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--binding` | BINDING |  | _[This must be specified.]_ ID of the cloud-access-binding or fully qualified identifier for the cloud-access-binding. To set the binding attribute: + provide the argument --binding on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The ID of the organization. To set the organization attribute: + provide the argument --binding on the command line with a fully specified name; + provide the argument --organization on the command line; + set the property access_context_manager/organization. |


**Examples:**
```bash
To get details about an existing cloud access binding, run:

    $ gcloud access-context-manager cloud-bindings describe \
        --binding=binding-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/cloud-bindings/describe)

---
### `gcloud access-context-manager cloud-bindings list`

List cloud access bindings under an organization

List cloud access bindings.

**Synopsis:**
```
gcloud access-context-manager cloud-bindings list
    [--organization=ORGANIZATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[to list. This represents a Cloud resource.]_ ID of the organization or fully qualified identifier for the organization. To set the organization attribute: + provide the argument --organization on the command line; + set the property access_context_manager/organization. |


**Examples:**
```bash
To list cloud access bindings, run:

    $ gcloud access-context-manager cloud-bindings list

This command prints a list of Google Cloud user access bindings,
gcpUserAccessBindings, in YAML format. By default, the binding is printed
in the following format:

    ---
    accessLevels:
    - accessPolicies/9522/accessLevels/device_trusted
    dryRunAccessLevels:
    - accessPolicies/9522/accessLevels/specific_location
    groupKey: a3dad
    name: organizations/256/gcpUserAccessBindings/b3-BhcX_Ud5N
    sessionSettings:
      sessionLength: 57600s
      sessionLengthEnabled: true
      sessionReauthMethod: LOGIN

Or

    ---
    accessLevels:
    - accessPolicies/9522/accessLevels/device_trusted
    dryRunAccessLevels:
    - accessPolicies/9522/accessLevels/specific_location
    groupKey: a3dad
    name: organizations/256/gcpUserAccessBindings/b3-BhcX_Ud5N
    scopedAccessSettings:
    - activeSettings:
        accessLevels:
        - accessPolicies/9522/accessLevels/device_trusted
      dryRunSettings:
        accessLevels:
        - accessPolicies/9522/accessLevels/specific_location
      scope:
        clientScope:
          restrictedClientApplication:
            clientId: 123.apps.googleusercontent.com
    - activeSettings:
        accessLevels:
        - accessPolicies/9522/accessLevels/device_trusted
      dryRunSettings:
        accessLevels:
        - accessPolicies/9522/accessLevels/specific_location
      scope:
        clientScope:
          restrictedClientApplication:
            name: Cloud Console
    - activeSettings:
        sessionSettings:
          sessionLength: 57600s
          sessionLengthEnabled: true
          sessionReauthMethod: LOGIN
      scope:
        clientScope:
          restrictedClientApplication:
            clientId: 123.apps.googleusercontent.com
    sessionSettings:
      sessionLength: 57600s
      sessionLengthEnabled: true
      sessionReauthMethod: LOGIN
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/cloud-bindings/list)

---
### `gcloud access-context-manager cloud-bindings update`

Update a existing cloud access binding under an organization

Update an existing cloud access binding. You can update the level, dry run
level, session settings, and scoped access settings. They cannot all be
empty.

**Synopsis:**
```
gcloud access-context-manager cloud-bindings update
    (--binding=BINDING : --organization=ORGANIZATION) [--append]
    [--binding-file=YAML_FILE] [--dry-run-level=[DRY_RUN_LEVEL,...]]
    [--level=[LEVEL,...]] [--session-length=SESSION_LENGTH]
    [--session-reauth-method=SESSION_REAUTH_METHOD; default="login"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--binding` | BINDING |  | _[This must be specified.]_ ID of the cloud-access-binding or fully qualified identifier for the cloud-access-binding. To set the binding attribute: + provide the argument --binding on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The ID of the organization. To set the organization attribute: + provide the argument --binding on the command line with a fully specified name; + provide the argument --organization on the command line; + set the property access_context_manager/organization. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--append` |  |  | When true, append the ScopedAccessSettings in --binding-file to the existing ScopedAccessSettings on the binding. When false, the existing binding's ScopedAccessSettings will be overwritten. Defaults to false. You may only append ScopedAccessSettings that exclusively hold session settings (i.e no access levels). |
| `--binding-file` | YAML_FILE |  | Path to the file that contains a Google Cloud Platform user access binding. This file contains a YAML-compliant object representing a GcpUserAccessBinding (as described in the API reference) containing ScopedAccessSettings only. No other binding fields are allowed. The file content replaces the corresponding fields in the existing binding. Unless --append is specified. See --append help text for more details. |
| `--dry-run-level` | [DRY_RUN_LEVEL,...] |  | The dry run access level that replaces the existing dry run level for the given binding. The input must be the full identifier of an access level, such as accessPolicies/123/accessLevels/new-def. |
| `--level` | [LEVEL,...] |  | The access level that replaces the existing level for the given binding. The input must be the full identifier of an access level, such as accessPolicies/123/accessLevels/new-abc. |
| `--session-length` | SESSION_LENGTH |  | The maximum lifetime of a user session provided as an ISO 8601 duration string. Must be at least one hour or zero, and no more than twenty-four hours. Granularity is limited to seconds. When --session-length=0 users in the group attached to this binding will have infinite session length, effectively disabling the session settings. A session begins after a user signs in successfully. If a user signs out before the end of the session lifetime, a new login creates a new session with a fresh lifetime. When a session expires, the user is asked to reauthenticate in accordance with session-reauth-method. Setting --session-reauth-method when --session-length is empty raises an error. Cannot set --session-length on restricted client applications; please use scoped access settings. |
| `--session-reauth-method` | one of: login The user will be prompted to perform regular login | login | Specifies the security check a user must undergo when their session expires. Defaults to --session-reauth-method=LOGIN if unspecified and --session-length is set. Cannot be used when --session-length is empty or 0. SESSION_REAUTH_METHOD must be one of: login The user will be prompted to perform regular login. Users who are enrolled in two-step verification and haven't chosen to "Remember this computer" will be prompted for their second factor. password The user will only be required to enter their password. security-key The user will be prompted to autheticate using their security key. If no security key has been configured, the LOGIN method is used. |


**Examples:**
```bash
To update an existing cloud access binding, run:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id \
        --level=accessPolicies/123/accessLevels/new-abc

To remove level and add dry run level, run:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id --level= \
        --dry-run-level=accessPolicies/123/accessLevels/new-def

To replace scoped access settings with a new list, run:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id --binding-file='binding.yaml'

To append scoped access settings to the existing list, run:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id --binding-file='binding.yaml' --append

Note this is only possible for scoped access settings that exclusively hold
session settings (i.e. no access levels).

To update session settings, run:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id --session-length=2h

To update the session reauth method you must also specify --session-length
(this can be the existing value if you only want to modify the reauth
method), run:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id --session-length=2h \
        --session-reauth-method=login

To disable session settings, set --session-length=0, for example:

    $ gcloud access-context-manager cloud-bindings update \
        --binding=my-binding-id --session-length=0
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/cloud-bindings/update)

---