# gcloud auth (top-level commands)

### `gcloud auth activate-service-account`

Authorize access to Google Cloud with a service account

To allow gcloud (and other tools in Google Cloud CLI) to use service
account credentials to make requests, use this command to import these
credentials from a file that contains a private authorization key, and
activate them for use in gcloud. gcloud auth activate-service-account
serves the same function as gcloud auth login but uses a service account
rather than Google user credentials.

For more information on authorization and credential types, see:
https://cloud.google.com/sdk/docs/authorizing.

Key File

To obtain the key file for this command, use either the Google Cloud
Console (https://console.cloud.google.com) or gcloud iam service-accounts
keys create. The key file can be .json (preferred) or .p12 (legacy) format.
In the case of legacy .p12 files, a separate password might be required and
is displayed in the Console when you create the key.

Credentials

Credentials will also be activated (similar to running gcloud config set
account [ACCOUNT_NAME]).

If a project is specified using the --project flag, the project is set in
active configuration, which is the same as running gcloud config set
project [PROJECT_NAME]. Any previously active credentials, will be retained
(though no longer default) and can be displayed by running gcloud auth
list.

If you want to delete previous credentials, see gcloud auth revoke.

Note: Service accounts use client quotas for tracking usage.

**Synopsis:**
```
gcloud auth activate-service-account [ACCOUNT] --key-file=KEY_FILE
    [--password-file=PASSWORD_FILE | --prompt-for-password]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ACCOUNT]
   E-mail address of the service account.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-file` | KEY_FILE |  | Path to the private key file. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--password-file` | PASSWORD_FILE |  | _[At most one of these can be specified:]_ Path to a file containing the password for the service account private key (only for a .p12 file). |
| `--prompt-for-password` |  |  | _[At most one of these can be specified:]_ Prompt for the password for the service account private key (only for a .p12 file). |


**Examples:**
```bash
To authorize gcloud to access Google Cloud using an existing service
account while also specifying a project, run:

    $ gcloud auth activate-service-account SERVICE_ACCOUNT@DOMAIN.COM \
    --key-file=/path/key.json --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/activate-service-account)

---
### `gcloud auth configure-docker`

Register gcloud as a Docker credential helper

gcloud auth configure-docker adds the Docker credHelper entry to Docker's
configuration file, or creates the file if it doesn't exist. This will
register gcloud as the credential helper for all Google-supported Docker
registries. If the Docker configuration already contains a credHelper
entry, it will be overwritten.

Note: docker and gcloud need to be on the same system PATH to work
correctly.

Note: This command will not work for docker installed via Snap, as the
docker snap package does not currently provide an interface for credential
helpers.

For more details on Docker registries, see
https://docs.docker.com/registry/.

For more details on how to authenticate to Google Container Registry using
this command, see
https://cloud.google.com/container-registry/docs/advanced-authentication#gcloud-helper.

For more details on Google Container Registry's standalone credential
helpers, see https://github.com/GoogleCloudPlatform/docker-credential-gcr.

For more details on Docker credential helpers, see
https://docs.docker.com/engine/reference/commandline/login/#credential-helpers.

**Synopsis:**
```
gcloud auth configure-docker [REGISTRIES] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[REGISTRIES]
   The comma-separated list of registries to configure the credential
   helper for. Container Registry is a service for storing private
   container images. For available registries, see
   https://cloud.google.com/container-registry/docs/pushing-and-pulling#add-registry.
```

**Examples:**
```bash
To configure docker authentication after logging into gcloud, run:

    $ gcloud auth configure-docker

To configure docker authentication with Container Registry, e.g., gcr.io,
run:

    $ gcloud auth configure-docker gcr.io
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/configure-docker)

---
### `gcloud auth list`

Lists credentialed accounts

Lists accounts whose credentials have been obtained using gcloud init,
gcloud auth login and gcloud auth activate-service-account, and shows which
account is active. The active account is used by gcloud and other Google
Cloud CLI tools to access Google Cloud Platform. While there is no limit on
the number of accounts with stored credentials, there is only one active
account.

**Synopsis:**
```
gcloud auth list [--filter-account=FILTER_ACCOUNT] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter-account` | FILTER_ACCOUNT |  | List only credentials for one account. Use --filter="account~PATTERN" to select accounts that match PATTERN. |


**Examples:**
```bash
To set an existing account to be the current active account, run:

    $ gcloud config set core/account your-email-account@gmail.com

If you don't have an existing account, create one using:

    $ gcloud init

To list the active account name:

    $ gcloud auth list --filter=status:ACTIVE --format="value(account)"

To list the inactive account names with prefix test:

    $ gcloud auth list --filter="-status:ACTIVE account:test*" \
        --format="value(account)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/list)

---
### `gcloud auth login`

Authorize gcloud to access the Cloud Platform with Google user credentials

Obtains access credentials for your user account via a web-based
authorization flow. When this command completes successfully, it sets the
active account in the current configuration to the account specified. If no
configuration exists, it creates a configuration named default.

If valid credentials for an account are already available from a prior
authorization, the account is set to active without rerunning the flow.

Use gcloud auth list to view credentialed accounts.

If you'd rather authorize without a web browser but still interact with the
command line, use the --no-browser flag. To authorize without a web browser
and non-interactively, create a service account with the appropriate scopes
using the Google Cloud Console (https://console.cloud.google.com) and use
gcloud auth activate-service-account with the corresponding JSON key file.

In addition to Google user credentials, authorization using workload
identity federation, workforce identity federation, or service account keys
is also supported.

For authorization with external accounts or service accounts, the
--cred-file flag must be specified with the path to the workload identity
credential configuration file or service account key file (JSON).

Login with workload and workforce identity federation is also supported in
both gsutil and bq. This command is the recommended way of using external
accounts.

For more information on workload identity federation, see:
https://cloud.google.com/iam/docs/workload-identity-federation.

For more information on workforce identity federation, see:
https://cloud.google.com/iam/docs/workforce-identity-federation.

For more information on authorization and credential types, see:
https://cloud.google.com/sdk/docs/authorizing.

**Synopsis:**
```
gcloud auth login [ACCOUNT] [--no-activate] [--brief] [--no-browser]
    [--cred-file=CRED_FILE] [--enable-gdrive-access] [--force]
    [--no-launch-browser] [--login-config=LOGIN_CONFIG] [--update-adc]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ACCOUNT]
   User account used for authorization. When the account specified has
   valid credentials in the local credential store these credentials will
   be re-used, otherwise a new credential will be fetched. If you need to
   fetch a new credential for an account with valid credentials stored,
   run the command with the --force flag.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--activate` |  |  | Set the new account to active. Enabled by default, use --no-activate to disable. |
| `--brief` |  |  | Minimal user output. |
| `--browser` |  |  | If you want to authorize the gcloud CLI on a machine that doesn't have a browser and you can install the gcloud CLI on another machine with a browser, use the --no-browser flag. 1. To initiate authorization, enter the following command: gcloud auth login --no-browser 2. Copy the long command that begins with gcloud auth login --remote-bootstrap=". 3. Paste and run this command on the command line of a different, trusted machine that has local installations of both a web browser and the gcloud CLI tool version 372.0 or later. 4. Copy the long URL output from the machine with the web browser. 5. Paste the long URL back to the first machine under the prompt, "Enter the output of the above command", and press Enter to complete the authorization. Enabled by default, use --no-browser to disable. |
| `--cred-file` | CRED_FILE |  | Path to the external account configuration file (workload identity pool, generated by the Cloud Console or gcloud iam workload-identity-pools create-cred-config) or service account credential key file (JSON). |
| `--enable-gdrive-access` |  |  | Enable Google Drive access. |
| `--force` |  |  | Re-run the web authorization flow even if the given account has valid credentials. |
| `--launch-browser` |  |  | Launch a browser for authorization. If not enabled or if it is not possible to launch a browser, prints a URL to standard output to be copied. If you want to authorize the gcloud CLI on a machine that doesn't have a browser and you cannot install the gcloud CLI on another machine with a browser, use the --no-launch-browser flag. The --no-launch-browser flag prevents the command from automatically opening a web browser. 1. To initiate authorization, enter the following command: gcloud auth login --no-launch-browser 2. Copy the long URL that begins with https://accounts.google.com/o/oauth2/auth... 3. Paste this URL into the browser of a different, trusted machine that has a web browser. 4. Copy the authorization code from the machine with the web browser. 5. Paste the authorization code back to the first machine at the prompt, "Enter authorization code", and press Enter to complete the authorization. Enabled by default, use --no-launch-browser to disable. |
| `--login-config` | LOGIN_CONFIG |  | Path to the workforce identity federation login configuration file which can be generated using the gcloud iam workforce-pools create-login-config command. Overrides the default auth/login_config_file property value for this command invocation. |
| `--update-adc` |  |  | Write the obtained credentials to the well-known location for Application Default Credentials (ADC). Run $ gcloud auth application-default --help to learn more about ADC. Any credentials previously generated by gcloud auth application-default login will be overwritten. |


**Examples:**
```bash
To obtain access credentials for your user account, run:

    $ gcloud auth login

To obtain access credentials using workload or workforce identity
federation, run:

    $ gcloud auth login --cred-file=/path/to/configuration/file

To obtain access credentials using a browser-based sign-in flow with
workforce identity federation, run:

    $ gcloud auth login --login-config=/path/to/configuration/file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/login)

---
### `gcloud auth print-access-token`

Print an access token for the specified account

Print an access token for the specified account. See RFC6749
(https://tools.ietf.org/html/rfc6749) for more information about access
tokens.

Note that token itself may not be enough to access some services. If you
use the token with curl or similar tools, you may see permission errors
similar to "API has not been used in project 32555940559 before or it is
disabled.". If it happens, you may need to provide a quota project in the
"X-Goog-User-Project" header. For example,

    $ curl -H "X-Goog-User-Project: your-project" \
        -H "Authorization: Bearer $(gcloud auth print-access-token)" \
        foo.googleapis.com

The identity that granted the token must have the serviceusage.services.use
permission on the provided project. See
https://cloud.google.com/apis/docs/system-parameters for more information.

**Synopsis:**
```
gcloud auth print-access-token [ACCOUNT] [--lifetime=LIFETIME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ACCOUNT]
   Account to get the access token for. If not specified, the current
   active account will be used.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lifetime` | LIFETIME |  | Access token lifetime. The default access token lifetime is 3600 seconds, but you can use this flag to reduce the lifetime or extend it up to 43200 seconds (12 hours). The org policy constraint constraints/iam.allowServiceAccountCredentialLifetimeExtension must be set if you want to extend the lifetime beyond 3600 seconds. Note that this flag is for service account impersonation only, so it must be used together with the --impersonate-service-account flag. |


**Examples:**
```bash
To print access tokens:

    $ gcloud auth print-access-token
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/print-access-token)

---
### `gcloud auth print-identity-token`

Print an identity token for the specified account

Print an identity token for the specified account.

**Synopsis:**
```
gcloud auth print-identity-token [ACCOUNT] [--audiences=AUDIENCES]
    [--include-email]
    [--include-license --token-format=TOKEN_FORMAT; default="standard"]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ACCOUNT]
   Account to print the identity token for. If not specified, the current
   active account will be used.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--audiences` | AUDIENCES |  | Intended recipient of the token. Currently, only one audience can be specified. |
| `--include-email` |  |  | Specify whether or not service account email is included in the identity token. If specified, the token will contain 'email' and 'email_verified' claims. This flag should only be used for impersonate service account. |


**Examples:**
```bash
To print identity tokens:

    $ gcloud auth print-identity-token

To print identity token for account 'foo@example.com' whose audience is
'https://service-hash-uc.a.run.app', run:

    $ gcloud auth print-identity-token foo@example.com \
        --audiences="https://service-hash-uc.a.run.app"

To print identity token for an impersonated service account
'my-account@example.iam.gserviceaccount.com' whose audience is
'https://service-hash-uc.a.run.app', run:

    $ gcloud auth print-identity-token \
        --impersonate-service-account="my-account@example.iam.gserviceac\
    count.com" --audiences="https://service-hash-uc.a.run.app"

To print identity token of a Compute Engine instance, which includes
project and instance details as well as license codes for images associated
with the instance, run:

    $ gcloud auth print-identity-token --token-format=full \
        --include-license

To print identity token for an impersonated service account
'my-account@example.iam.gserviceaccount.com', which includes the email
address of the service account, run:

    $ gcloud auth print-identity-token \
        --impersonate-service-account="my-account@example.iam.gserviceac\
    count.com" --include-email
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/print-identity-token)

---
### `gcloud auth revoke`

Revoke access credentials for an account

Revokes credentials for the specified user accounts, service accounts or
external accounts (workload identity pools).

When given a user account, this command revokes the user account token on
the server. If the revocation is successful, or if the token has already
been revoked, this command removes the credential from the local machine.

When given a service account, this command does not revoke the service
account token on the server because service account tokens are not
revocable. Instead, it will print a warning and remove the credential from
the local machine. When used with a service account, this command has only
a local effect and the key associated with the service account is not
deleted. This can be done by executing gcloud iam service-accounts keys
delete after revoke.

When given an external account (workload identity pool), whether
impersonated or not, the command does not revoke the corresponding token on
the server because these tokens are not revocable. The underlying external
credentials (OIDC, AWS, etc.) used to generate these access tokens have to
be revoked too, but gcloud has no control over that. Instead, it will print
a warning and remove the credential from the local machine.

If no account is specified, this command revokes credentials for the
currently active account, effectively logging out of that account. If --all
is given, the behaviors described above apply individually to each account
in the list.

You can revoke credentials when you want to prevent gcloud and other Google
Cloud CLI tools from using the specified account. You do not need to revoke
credentials to switch between accounts.

**Synopsis:**
```
gcloud auth revoke [ACCOUNTS ...] [--all] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ACCOUNTS ...]
   Accounts whose credentials are to be revoked.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all` |  |  | Revoke credentials for all accounts. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/auth/revoke)

---