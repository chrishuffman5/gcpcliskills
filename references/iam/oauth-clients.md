# gcloud iam oauth-clients

create and manage OAuth clients

### `gcloud iam oauth-clients create`

Create an OAuth client

Create a new OAuth client.

**Synopsis:**
```
gcloud iam oauth-clients create (OAUTH_CLIENT : --location=LOCATION)
    --allowed-grant-types=[ALLOWED_GRANT_TYPES,...]
    --allowed-redirect-uris=[ALLOWED_REDIRECT_URIS,...]
    --allowed-scopes=[ALLOWED_SCOPES,...] --client-type=CLIENT_TYPE
    [--description=DESCRIPTION] [--disabled] [--display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client resource - The OAuth client to create. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument oauth_client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OAUTH_CLIENT
     ID of the oauth client or fully qualified identifier for the oauth
     client.

     To set the oauth_client attribute:
     + provide the argument oauth_client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument oauth_client on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-grant-types` | [ALLOWED_GRANT_TYPES,...] |  | A list of OAuth grant types that are allowed for the OAuth client. The following grant types are currently supported: * authorization-code-grant * refresh-token-grant |
| `--allowed-redirect-uris` | [ALLOWED_REDIRECT_URIS,...] |  | A list of redirect uris that is allowed for redirecting when the authorization is completed. |
| `--allowed-scopes` | [ALLOWED_SCOPES,...] |  | A list of scopes that the OAuth client is allowed to request during OAuth flows. The following scopes are currently supported: * https://www.googleapis.com/auth/cloud-platform: View, edit, configure, and delete your Google Cloud data, and view the email address for your Google Account. * openid: Associate you with your personal info on Google Cloud. * email: The OAuth client can read a federated identity's email address. * groups: The OAuth client can read a federated identity's groups. |
| `--client-type` | one of: confidential-client, public-client |  | The type of OAuth client. CLIENT_TYPE must be one of: confidential-client, public-client. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | A description of the OAuth client. Cannot exceed 256 characters. |
| `--disabled` |  |  | Disables the OAuth client. You cannot use a disabled OAuth client for login. Include --no-disabled to enable a disabled OAuth client. |
| `--display-name` | DISPLAY_NAME |  | A display name for the OAuth client. Cannot exceed 32 characters. |


**Examples:**
```bash
The following command creates a disabled OAuth client with ID
my-oauth-client in the default project:

    $ gcloud iam oauth-clients create my-oauth-client \
        --location="global" --client-type="confidential-client" \
        --display-name="My oauth client" \
        --description="My oauth client description" --disabled \
        --allowed-grant-types="authorization-code-grant,refresh-token-gr\
    ant" \
        --allowed-scopes="https://www.googleapis.com/auth/cloud-platform\
    ,openid" --allowed-redirect-uris="https://example.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/create)

---
### `gcloud iam oauth-clients delete`

Delete an OAuth client

Delete an OAuth client.

**Synopsis:**
```
gcloud iam oauth-clients delete (OAUTH_CLIENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client resource - The OAuth client to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument oauth_client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OAUTH_CLIENT
     ID of the oauth client or fully qualified identifier for the oauth
     client.

     To set the oauth_client attribute:
     + provide the argument oauth_client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument oauth_client on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command deletes the OAuth client with the ID my-oauth-client
in the default project:

    $ gcloud iam oauth-clients delete my-oauth-client --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/delete)

---
### `gcloud iam oauth-clients describe`

Describe an OAuth client

Describe an OAuth client.

**Synopsis:**
```
gcloud iam oauth-clients describe (OAUTH_CLIENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client resource - The OAuth client you want to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument oauth_client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OAUTH_CLIENT
     ID of the oauth client or fully qualified identifier for the oauth
     client.

     To set the oauth_client attribute:
     + provide the argument oauth_client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument oauth_client on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command describes the OAuth client with the ID
my-oauth-client in the default project:

    $ gcloud iam oauth-clients describe my-oauth-client \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/describe)

---
### `gcloud iam oauth-clients list`

List OAuth clients

List OAuth clients.

**Synopsis:**
```
gcloud iam oauth-clients list --location=LOCATION [--show-deleted]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Whether to return soft-deleted OAuth clients. |


**Examples:**
```bash
The following command lists all OAuth clients in the default project,
including the soft-deleted ones:

    $ gcloud iam oauth-clients list --location="global" --show-deleted
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/list)

---
### `gcloud iam oauth-clients undelete`

Undelete an OAuth client

Undelete an OAuth client.

**Synopsis:**
```
gcloud iam oauth-clients undelete (OAUTH_CLIENT : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client resource - The OAuth client to undelete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument oauth_client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OAUTH_CLIENT
     ID of the oauth client or fully qualified identifier for the oauth
     client.

     To set the oauth_client attribute:
     + provide the argument oauth_client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument oauth_client on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
The following command undeletes the OAuth client with the ID
my-oauth-client in the default project:

    $ gcloud iam oauth-clients undelete my-oauth-client \
        --location="global"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/undelete)

---
### `gcloud iam oauth-clients update`

Update an OAuth client

Update an OAuth Client.

**Synopsis:**
```
gcloud iam oauth-clients update (OAUTH_CLIENT : --location=LOCATION)
    [--allowed-grant-types=[ALLOWED_GRANT_TYPES,...]]
    [--allowed-redirect-uris=[ALLOWED_REDIRECT_URIS,...]]
    [--allowed-scopes=[ALLOWED_SCOPES,...]] [--description=DESCRIPTION]
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client resource - The OAuth client to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument oauth_client on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OAUTH_CLIENT
     ID of the oauth client or fully qualified identifier for the oauth
     client.

     To set the oauth_client attribute:
     + provide the argument oauth_client on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument oauth_client on the command line with a
       fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--allowed-grant-types` | [ALLOWED_GRANT_TYPES,...] |  | A list of OAuth grant types that are allowed for the OAuth client. The following grant types are currently supported: * authorization-code-grant * refresh-token-grant |
| `--allowed-redirect-uris` | [ALLOWED_REDIRECT_URIS,...] |  | A list of redirect uris that is allowed for redirecting when the authorization is completed. |
| `--allowed-scopes` | [ALLOWED_SCOPES,...] |  | A list of scopes that the OAuth client is allowed to request during OAuth flows. The following scopes are currently supported: * https://www.googleapis.com/auth/cloud-platform: View, edit, configure, and delete your Google Cloud data, and view the email address for your Google Account. * openid: Associate you with your personal info on Google Cloud. * email: The OAuth client can read a federated identity's email address. * groups: The OAuth client can read a federated identity's groups. |
| `--description` | DESCRIPTION |  | A description of the OAuth client. Cannot exceed 256 characters. |
| `--disabled` |  |  | Disables the OAuth client. You cannot use a disabled OAuth client for login. Include --no-disabled to enable a disabled OAuth client. |
| `--display-name` | DISPLAY_NAME |  | A display name for the OAuth client. Cannot exceed 32 characters. |


**Examples:**
```bash
The following command updates the OAuth client with ID my-oauth-client in
the default project:

    $ gcloud iam oauth-clients update my-oauth-client \
        --location="global" --display-name="My oauth client" \
        --description="My oauth client description" --disabled \
        --allowed-grant-types="authorization-code-grant,refresh-token-gr\
    ant" \
        --allowed-scopes="https://www.googleapis.com/auth/cloud-platform\
    ,openid" --allowed-redirect-uris="http://localhost/"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/update)

---

## `gcloud iam oauth-clients credentials` — create and manage OAuth client credentials
### `gcloud iam oauth-clients credentials create`

Create an OAuth client credential

Create a new OAuth client credential.

**Synopsis:**
```
gcloud iam oauth-clients credentials create
    (CREDENTIAL : --location=LOCATION --oauth-client=OAUTH_CLIENT)
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client credential resource - The OAuth client credential to create.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument credential on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CREDENTIAL
     ID of the oauth client credential or fully qualified identifier for
     the oauth client credential.

     To set the credential attribute:
     + provide the argument credential on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --oauth-client=OAUTH_CLIENT
     ID to use for the OAuth client, which becomes the final component of
     the resource name. This value should be 4-32 characters, and may
     contain the characters [a-z0-9-]. The prefix gcp- is reserved for use
     by Google, and may not be specified.

     To set the oauth-client attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --oauth-client on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disabled` |  |  | Disables the OAuth client credential. You cannot use a disabled OAuth client credential for OAuth. Include --no-disabled to enable a disabled OAuth client credential. |
| `--display-name` | DISPLAY_NAME |  | A display name for the OAuth client credential. Cannot exceed 32 characters. |


**Examples:**
```bash
To create a disabled OAuth client credential with ID
my-oauth-client-credential in the default project, run:

    $ gcloud iam oauth-clients credentials create \
        my-oauth-client-credential --location="global" \
        --oauth-client="my-oauth-client" \
        --display-name="My OAuth client credential" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/credentials/create)

---
### `gcloud iam oauth-clients credentials delete`

Delete an OAuth client credential

Delete an OAuth client credential.

**Synopsis:**
```
gcloud iam oauth-clients credentials delete
    (CREDENTIAL : --location=LOCATION --oauth-client=OAUTH_CLIENT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client credential resource - The OAuth client credential to delete.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument credential on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CREDENTIAL
     ID of the oauth client credential or fully qualified identifier for
     the oauth client credential.

     To set the credential attribute:
     + provide the argument credential on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --oauth-client=OAUTH_CLIENT
     ID to use for the OAuth client, which becomes the final component of
     the resource name. This value should be 4-32 characters, and may
     contain the characters [a-z0-9-]. The prefix gcp- is reserved for use
     by Google, and may not be specified.

     To set the oauth-client attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --oauth-client on the command line.
```

**Examples:**
```bash
To delete the OAuth client credential with ID my-oauth-client-credential in
the default project, run:

    $ gcloud iam oauth-clients credentials delete \
        my-oauth-client-credential --location="global" \
        --oauth-client="my-oauth-client"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/credentials/delete)

---
### `gcloud iam oauth-clients credentials describe`

Describe an OAuth client credential

Describe an OAuth client credential.

**Synopsis:**
```
gcloud iam oauth-clients credentials describe
    (CREDENTIAL : --location=LOCATION --oauth-client=OAUTH_CLIENT)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client credential resource - The OAuth client credential you want to
describe. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument credential on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CREDENTIAL
     ID of the oauth client credential or fully qualified identifier for
     the oauth client credential.

     To set the credential attribute:
     + provide the argument credential on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --oauth-client=OAUTH_CLIENT
     ID to use for the OAuth client, which becomes the final component of
     the resource name. This value should be 4-32 characters, and may
     contain the characters [a-z0-9-]. The prefix gcp- is reserved for use
     by Google, and may not be specified.

     To set the oauth-client attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --oauth-client on the command line.
```

**Examples:**
```bash
To describe the OAuth client credential with ID my-oauth-client-credential
in the default project, run:

    $ gcloud iam oauth-clients credentials describe \
        my-oauth-client-credential --location="global" \
        --oauth-client="my-oauth-client"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/credentials/describe)

---
### `gcloud iam oauth-clients credentials list`

List OAuth client credentials

List OAuth client credentials.

**Synopsis:**
```
gcloud iam oauth-clients credentials list
    (--oauth-client=OAUTH_CLIENT : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--oauth-client` | OAUTH_CLIENT |  | _[This must be specified.]_ ID of the oauth client or fully qualified identifier for the oauth client. To set the oauth-client attribute: + provide the argument --oauth-client on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location name. To set the location attribute: + provide the argument --oauth-client on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all OAuth client credentials in the default project, run:

    $ gcloud iam oauth-clients credentials list --location="global" \
        --oauth-client="my-oauth-client"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/credentials/list)

---
### `gcloud iam oauth-clients credentials update`

Update an OAuth client credential

Update an OAuth client credential.

**Synopsis:**
```
gcloud iam oauth-clients credentials update
    (CREDENTIAL : --location=LOCATION --oauth-client=OAUTH_CLIENT)
    [--disabled] [--display-name=DISPLAY_NAME] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Oauth client credential resource - The OAuth client credential to update.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument credential on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  CREDENTIAL
     ID of the oauth client credential or fully qualified identifier for
     the oauth client credential.

     To set the credential attribute:
     + provide the argument credential on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --location on the command line.

  --oauth-client=OAUTH_CLIENT
     ID to use for the OAuth client, which becomes the final component of
     the resource name. This value should be 4-32 characters, and may
     contain the characters [a-z0-9-]. The prefix gcp- is reserved for use
     by Google, and may not be specified.

     To set the oauth-client attribute:
     + provide the argument credential on the command line with a fully
       specified name;
     + provide the argument --oauth-client on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disabled` |  |  | Disables the OAuth client credential. You cannot use a disabled OAuth client credential for OAuth. Include --no-disabled to enable a disabled OAuth client credential. |
| `--display-name` | DISPLAY_NAME |  | A display name for the OAuth client credential. Cannot exceed 32 characters. |


**Examples:**
```bash
To update the OAuth client credential with ID my-oauth-client-credential in
the default project, run:

    $ gcloud iam oauth-clients credentials update \
        my-oauth-client-credential --location="global" \
        --oauth-client="my-oauth-client" \
        --display-name="My OAuth client credential" --disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/oauth-clients/credentials/update)

---