# gcloud developer-connect connections

manage connection resources

### `gcloud developer-connect connections create`

Create a connection resource

Create a connection resource.

**Synopsis:**
```
gcloud developer-connect connections create CONNECTION
    [--annotations=[ANNOTATIONS,...]] [--async] [--disabled] [--etag=ETAG]
    [--git-proxy-config-enabled] [--labels=[LABELS,...]]
    [--location=LOCATION] [--namespace=NAMESPACE] [--request-id=REQUEST_ID]
    [--secret=SECRET] [--validate-only]
    [--bitbucket-cloud-config-authorizer-credential-user-token-secret-version=BITBUCKET_CLOUD_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-cloud-config-read-authorizer-credential-user-token-secret-version=BITBUCKET_CLOUD_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-cloud-config-webhook-secret-version=BITBUCKET_CLOUD_CONFIG_WEBHOOK_SECRET_VERSION --bitbucket-cloud-config-workspace=BITBUCKET_CLOUD_CONFIG_WORKSPACE | [--bitbucket-data-center-config-authorizer-credential-user-token-secret-version=BITBUCKET_DATA_CENTER_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-data-center-config-host-uri=BITBUCKET_DATA_CENTER_CONFIG_HOST_URI --bitbucket-data-center-config-read-authorizer-credential-user-token-secret-version=BITBUCKET_DATA_CENTER_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-data-center-config-webhook-secret-version=BITBUCKET_DATA_CENTER_CONFIG_WEBHOOK_SECRET_VERSION : --bitbucket-data-center-config-service-directory=BITBUCKET_DATA_CENTER_CONFIG_SERVICE_DIRECTORY --bitbucket-data-center-config-ssl-ca-certificate=BITBUCKET_DATA_CENTER_CONFIG_SSL_CA_CERTIFICATE] | [--github-config-app=GITHUB_CONFIG_APP : --github-config-app-installation-id=GITHUB_CONFIG_APP_INSTALLATION_ID --github-config-authorizer-credential-oauth-token-secret-version=GITHUB_CONFIG_AUTHORIZER_CREDENTIAL_OAUTH_TOKEN_SECRET_VERSION] | [--github-enterprise-config-host-uri=GITHUB_ENTERPRISE_CONFIG_HOST_URI : --github-enterprise-config-app-id=GITHUB_ENTERPRISE_CONFIG_APP_ID --github-enterprise-config-app-installation-id=GITHUB_ENTERPRISE_CONFIG_APP_INSTALLATION_ID --github-enterprise-config-private-key-secret-version=GITHUB_ENTERPRISE_CONFIG_PRIVATE_KEY_SECRET_VERSION --github-enterprise-config-service-directory=GITHUB_ENTERPRISE_CONFIG_SERVICE_DIRECTORY --github-enterprise-config-ssl-ca-certificate=GITHUB_ENTERPRISE_CONFIG_SSL_CA_CERTIFICATE --github-enterprise-config-webhook-secret-version=GITHUB_ENTERPRISE_CONFIG_WEBHOOK_SECRET_VERSION] | --gitlab-config-authorizer-credential-user-token-secret-version=GITLAB_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-config-read-authorizer-credential-user-token-secret-version=GITLAB_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-config-webhook-secret-version=GITLAB_CONFIG_WEBHOOK_SECRET_VERSION | [--gitlab-enterprise-config-authorizer-credential-user-token-secret-version=GITLAB_ENTERPRISE_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-enterprise-config-host-uri=GITLAB_ENTERPRISE_CONFIG_HOST_URI --gitlab-enterprise-config-read-authorizer-credential-user-token-secret-version=GITLAB_ENTERPRISE_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-enterprise-config-webhook-secret-version=GITLAB_ENTERPRISE_CONFIG_WEBHOOK_SECRET_VERSION : --gitlab-enterprise-config-service-directory=GITLAB_ENTERPRISE_CONFIG_SERVICE_DIRECTORY --gitlab-enterprise-config-ssl-ca-certificate=GITLAB_ENTERPRISE_CONFIG_SSL_CA_CERTIFICATE] | [--http-config-host-uri=HTTP_CONFIG_HOST_URI : --http-config-service-directory=HTTP_CONFIG_SERVICE_DIRECTORY --http-config-ssl-ca-certificate=HTTP_CONFIG_SSL_CA_CERTIFICATE --http-config-bearer-token-authentication-secret-version=HTTP_CONFIG_BEARER_TOKEN_AUTHENTICATION_SECRET_VERSION | [--http-config-basic-authentication-username=HTTP_CONFIG_BASIC_AUTHENTICATION_USERNAME : --http-config-basic-authentication-password-secret-version=HTTP_CONFIG_BASIC_AUTHENTICATION_PASSWORD_SECRET_VERSION]]]
    [(--crypto-key-config-reference=CRYPTO_KEY_CONFIG_REFERENCE
      : --key-ring=KEY_RING)] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Identifier. The resource name of the connection, in
the format
projects/{project}/locations/{location}/connections/{connection_id}. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [ANNOTATIONS,...] |  | Allows clients to store small amounts of arbitrary data. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --annotations=string=string JSON Example: --annotations='{"string": "string"}' File Example: --annotations=path_to_file.(yaml\|json) |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--disabled` |  |  | If disabled is set to true, functionality is disabled for this connection. Repository based API methods and webhooks processing for repositories in this connection will be disabled. |
| `--etag` | ETAG |  | This checksum is computed by the server based on the value of other fields, and may be sent on update and delete requests to ensure the client has an up-to-date value before proceeding. |
| `--labels` | [LABELS,...] |  | _[git operations on the repositories linked in the connection.]_ Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--location` | LOCATION |  | _[git operations on the repositories linked in the connection.]_ For resources [connection, bitbucket-cloud-config-authorizer-credential-user-token-secret-version, bitbucket-cloud-config-read-authorizer-credential-user-token-secret-version, bitbucket-cloud-config-webhook-secret-version, bitbucket-data-center-config-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-read-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-service-directory, bitbucket-data-center-config-webhook-secret-version, crypto-key-config-reference, github-config-authorizer-credential-oauth-token-secret-version, github-enterprise-config-private-key-secret-version, github-enterprise-config-service-directory, github-enterprise-config-webhook-secret-version, gitlab-config-authorizer-credential-user-token-secret-version, gitlab-config-read-authorizer-credential-user-token-secret-version, gitlab-config-webhook-secret-version, gitlab-enterprise-config-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-read-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-service-directory, gitlab-enterprise-config-webhook-secret-version, http-config-basic-authentication-password-secret-version, http-config-bearer-token-authentication-secret-version, http-config-service-directory], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--namespace` | NAMESPACE |  | _[git operations on the repositories linked in the connection.]_ For resources [bitbucket-data-center-config-service-directory, github-enterprise-config-service-directory, gitlab-enterprise-config-service-directory, http-config-service-directory], provides fallback value for resource namespace attribute. When the resource's full URI path is not provided, namespace will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | _[git operations on the repositories linked in the connection.]_ An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--secret` | SECRET |  | _[git operations on the repositories linked in the connection.]_ For resources [bitbucket-cloud-config-authorizer-credential-user-token-secret-version, bitbucket-cloud-config-read-authorizer-credential-user-token-secret-version, bitbucket-cloud-config-webhook-secret-version, bitbucket-data-center-config-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-read-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-webhook-secret-version, github-config-authorizer-credential-oauth-token-secret-version, github-enterprise-config-private-key-secret-version, github-enterprise-config-webhook-secret-version, gitlab-config-authorizer-credential-user-token-secret-version, gitlab-config-read-authorizer-credential-user-token-secret-version, gitlab-config-webhook-secret-version, gitlab-enterprise-config-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-read-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-webhook-secret-version, http-config-basic-authentication-password-secret-version, http-config-bearer-token-authentication-secret-version], provides fallback value for resource secret attribute. When the resource's full URI path is not provided, secret will fallback to this flag value. |
| `--validate-only` |  |  | _[git operations on the repositories linked in the connection.]_ If set, validate the request, but do not actually post it. |


**Examples:**
```bash
To create a GitHub connection named my-connection in us-central1 run:

    $ gcloud developer-connect connections create my-connection \
        --github-config-app=developer-connect \
        --github-config-authorizer-credential-oauth-token-secret-version\
    =projects/my-project/secrets/my-oauth-token/versions/1 \
        --github-config-app-installation-id=12345 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/create)

---
### `gcloud developer-connect connections delete`

Delete a single connection

Delete a single connection.

**Synopsis:**
```
gcloud developer-connect connections delete
    (CONNECTION : --location=LOCATION) [--async] [--etag=ETAG]
    [--request-id=REQUEST_ID] [--validate-only] [GCLOUD_WIDE_FLAG ...]
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

  --location=LOCATION
     The location id of the connection resource.

     To set the location attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | The current etag of the Connection. If an etag is provided and does not match the current etag of the Connection, deletion will be blocked and an ABORTED error will be returned. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--validate-only` |  |  | If set, validate the request, but do not actually post it. |


**Examples:**
```bash
To delete a connection my-comection in location us-central1 run:

    $ gcloud developer-connect connections delete my-connection \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/delete)

---
### `gcloud developer-connect connections describe`

Get details of a single connection resource

Get details of a single connection resource.

**Synopsis:**
```
gcloud developer-connect connections describe
    (CONNECTION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
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

  --location=LOCATION
     The location id of the connection resource.

     To set the location attribute:
     + provide the argument connection on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the details of a single conenction my-connection in location
us-central1 run:

    $ gcloud developer-connect connections describe my-connection \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/describe)

---
### `gcloud developer-connect connections list`

List connections

List connections.

**Synopsis:**
```
gcloud developer-connect connections list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all connections in location us-central1 run:

    $ gcloud developer-connect connections list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/list)

---
### `gcloud developer-connect connections update`

Update the parameters of a single connection

Update a connection.

**Synopsis:**
```
gcloud developer-connect connections update CONNECTION
    [--[no-]allow-missing] [--async] [--[no-]disabled] [--etag=ETAG]
    [--location=LOCATION] [--namespace=NAMESPACE] [--request-id=REQUEST_ID]
    [--secret=SECRET] [--[no-]validate-only]
    [--annotations=[ANNOTATIONS,...]
      | --update-annotations=[UPDATE_ANNOTATIONS,...] --clear-annotations
      | --remove-annotations=REMOVE_ANNOTATIONS]
    [--bitbucket-cloud-config-authorizer-credential-user-token-secret-version=BITBUCKET_CLOUD_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-cloud-config-read-authorizer-credential-user-token-secret-version=BITBUCKET_CLOUD_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-cloud-config-workspace=BITBUCKET_CLOUD_CONFIG_WORKSPACE --clear-bitbucket-cloud-config | --bitbucket-data-center-config-authorizer-credential-user-token-secret-version=BITBUCKET_DATA_CENTER_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-data-center-config-host-uri=BITBUCKET_DATA_CENTER_CONFIG_HOST_URI --bitbucket-data-center-config-read-authorizer-credential-user-token-secret-version=BITBUCKET_DATA_CENTER_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --bitbucket-data-center-config-service-directory=BITBUCKET_DATA_CENTER_CONFIG_SERVICE_DIRECTORY --bitbucket-data-center-config-ssl-ca-certificate=BITBUCKET_DATA_CENTER_CONFIG_SSL_CA_CERTIFICATE --clear-bitbucket-data-center-config | --clear-github-config --github-config-app-installation-id=GITHUB_CONFIG_APP_INSTALLATION_ID --github-config-authorizer-credential-oauth-token-secret-version=GITHUB_CONFIG_AUTHORIZER_CREDENTIAL_OAUTH_TOKEN_SECRET_VERSION | --clear-github-enterprise-config --github-enterprise-config-app-id=GITHUB_ENTERPRISE_CONFIG_APP_ID --github-enterprise-config-app-installation-id=GITHUB_ENTERPRISE_CONFIG_APP_INSTALLATION_ID --github-enterprise-config-host-uri=GITHUB_ENTERPRISE_CONFIG_HOST_URI --github-enterprise-config-service-directory=GITHUB_ENTERPRISE_CONFIG_SERVICE_DIRECTORY --github-enterprise-config-ssl-ca-certificate=GITHUB_ENTERPRISE_CONFIG_SSL_CA_CERTIFICATE --clear-github-enterprise-config-private-key-secret-version | --github-enterprise-config-private-key-secret-version=GITHUB_ENTERPRISE_CONFIG_PRIVATE_KEY_SECRET_VERSION --clear-github-enterprise-config-webhook-secret-version | --github-enterprise-config-webhook-secret-version=GITHUB_ENTERPRISE_CONFIG_WEBHOOK_SECRET_VERSION | --clear-gitlab-config --gitlab-config-authorizer-credential-user-token-secret-version=GITLAB_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-config-read-authorizer-credential-user-token-secret-version=GITLAB_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION | --clear-gitlab-enterprise-config --gitlab-enterprise-config-authorizer-credential-user-token-secret-version=GITLAB_ENTERPRISE_CONFIG_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-enterprise-config-host-uri=GITLAB_ENTERPRISE_CONFIG_HOST_URI --gitlab-enterprise-config-read-authorizer-credential-user-token-secret-version=GITLAB_ENTERPRISE_CONFIG_READ_AUTHORIZER_CREDENTIAL_USER_TOKEN_SECRET_VERSION --gitlab-enterprise-config-service-directory=GITLAB_ENTERPRISE_CONFIG_SERVICE_DIRECTORY --gitlab-enterprise-config-ssl-ca-certificate=GITLAB_ENTERPRISE_CONFIG_SSL_CA_CERTIFICATE | --clear-http-config --http-config-service-directory=HTTP_CONFIG_SERVICE_DIRECTORY --http-config-ssl-ca-certificate=HTTP_CONFIG_SSL_CA_CERTIFICATE --clear-http-config-bearer-token-authentication-secret-version | --http-config-bearer-token-authentication-secret-version=HTTP_CONFIG_BEARER_TOKEN_AUTHENTICATION_SECRET_VERSION | --http-config-basic-authentication-username=HTTP_CONFIG_BASIC_AUTHENTICATION_USERNAME --clear-http-config-basic-authentication-password-secret-version | --http-config-basic-authentication-password-secret-version=HTTP_CONFIG_BASIC_AUTHENTICATION_PASSWORD_SECRET_VERSION]
    [--clear-crypto-key-config
      [--crypto-key-config-reference=CRYPTO_KEY_CONFIG_REFERENCE
      : --key-ring=KEY_RING]]
    [--clear-git-proxy-config --[no-]git-proxy-config-enabled]
    [--labels=[LABELS,...]
      | --update-labels=[UPDATE_LABELS,...] --clear-labels
      | --remove-labels=REMOVE_LABELS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Connection resource - Identifier. The resource name of the connection, in
the format
projects/{project}/locations/{location}/connections/{connection_id}. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument connection on the command line with a fully
   specified name;
 * provide the argument --location on the command line.

This must be specified.

  CONNECTION
     ID of the connection or fully qualified identifier for the
     connection.

     To set the connection attribute:
     + provide the argument connection on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--[no-]allow-missing` |  |  | If set to true, and the connection is not found a new connection will be created. In this situation update_mask is ignored. The creation will succeed only if the input connection has all the necessary information (e.g a github_config with both user_oauth_token and installation_id properties). Use --allow-missing to enable and --no-allow-missing to disable. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--[no-]disabled` |  |  | If disabled is set to true, functionality is disabled for this connection. Repository based API methods and webhooks processing for repositories in this connection will be disabled. Use --disabled to enable and --no-disabled to disable. |
| `--etag` | ETAG |  | This checksum is computed by the server based on the value of other fields, and may be sent on update and delete requests to ensure the client has an up-to-date value before proceeding. |
| `--location` | LOCATION |  | For resources [connection, bitbucket-cloud-config-authorizer-credential-user-token-secret-version, bitbucket-cloud-config-read-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-read-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-service-directory, crypto-key-config-reference, github-config-authorizer-credential-oauth-token-secret-version, github-enterprise-config-private-key-secret-version, github-enterprise-config-service-directory, github-enterprise-config-webhook-secret-version, gitlab-config-authorizer-credential-user-token-secret-version, gitlab-config-read-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-read-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-service-directory, http-config-basic-authentication-password-secret-version, http-config-bearer-token-authentication-secret-version, http-config-service-directory], provides fallback value for resource location attribute. When the resource's full URI path is not provided, location will fallback to this flag value. |
| `--namespace` | NAMESPACE |  | For resources [bitbucket-data-center-config-service-directory, github-enterprise-config-service-directory, gitlab-enterprise-config-service-directory, http-config-service-directory], provides fallback value for resource namespace attribute. When the resource's full URI path is not provided, namespace will fallback to this flag value. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--secret` | SECRET |  | For resources [bitbucket-cloud-config-authorizer-credential-user-token-secret-version, bitbucket-cloud-config-read-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-authorizer-credential-user-token-secret-version, bitbucket-data-center-config-read-authorizer-credential-user-token-secret-version, github-config-authorizer-credential-oauth-token-secret-version, github-enterprise-config-private-key-secret-version, github-enterprise-config-webhook-secret-version, gitlab-config-authorizer-credential-user-token-secret-version, gitlab-config-read-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-authorizer-credential-user-token-secret-version, gitlab-enterprise-config-read-authorizer-credential-user-token-secret-version, http-config-basic-authentication-password-secret-version, http-config-bearer-token-authentication-secret-version], provides fallback value for resource secret attribute. When the resource's full URI path is not provided, secret will fallback to this flag value. |
| `--[no-]validate-only` |  |  | If set, validate the request, but do not actually post it. Use --validate-only to enable and --no-validate-only to disable. |


**Examples:**
```bash
To update the labels of a connection my-connection in location us-central1
run:

    $ gcloud developer-connect connections update my-connection \
        --labels=key1=value1 --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/update)

---

## `gcloud developer-connect connections git-repository-links` — manage git repository link resources
### `gcloud developer-connect connections git-repository-links create`

Create a git repository link

Create a git repository link.

**Synopsis:**
```
gcloud developer-connect connections git-repository-links create
    (GIT_REPOSITORY_LINK : --connection=CONNECTION --location=LOCATION)
    --clone-uri=CLONE_URI [--annotations=[ANNOTATIONS,...]] [--async]
    [--etag=ETAG] [--labels=[LABELS,...]] [--request-id=REQUEST_ID]
    [--validate-only] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GitRepositoryLink resource - Identifier. Resource name of the repository,
in the format projects/*/locations/*/connections/*/gitRepositoryLinks/*.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument git_repository_link on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GIT_REPOSITORY_LINK
     ID of the gitRepositoryLink or fully qualified identifier for the
     gitRepositoryLink.

     To set the git_repository_link attribute:
     + provide the argument git_repository_link on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     The connection id of the gitRepositoryLink resource.

     To set the connection attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --connection on the command line.

  --location=LOCATION
     The location id of the gitRepositoryLink resource.

     To set the location attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--clone-uri` | CLONE_URI |  | Git Clone URI. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [ANNOTATIONS,...] |  | Allows clients to store small amounts of arbitrary data. KEY Sets KEY value. VALUE Sets VALUE value. Shorthand Example: --annotations=string=string JSON Example: --annotations='{"string": "string"}' File Example: --annotations=path_to_file.(yaml\|json) |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | This checksum is computed by the server based on the value of other fields, and may be sent on update and delete requests to ensure the client has an up-to-date value before proceeding. |
| `--labels` | [LABELS,...] |  | Labels as key value pairs. KEY Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. VALUE Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. Shorthand Example: --labels=string=string JSON Example: --labels='{"string": "string"}' File Example: --labels=path_to_file.(yaml\|json) |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes since the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--validate-only` |  |  | If set, validate the request, but do not actually post it. |


**Examples:**
```bash
To create a git repository link 'my-git-repository-link' in a connection
my-connection in us-central1 run:

    $ gcloud developer-connect connections git-repository-links create \
        my-git-repository-link \
        --clone-uri=https://github.com/my-org/my-repo.git \
        --connection=my-connection --location=us-central1

Or run:

    $ gcloud developer-connect connections git-repository-links create \
        projects/my-project/locations/us-central1/connections/\
    my-connection/gitRepositoryLinks/my-git-repository-link \
        --clone-uri=https://github.com/my-org/my-repo.git \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/git-repository-links/create)

---
### `gcloud developer-connect connections git-repository-links delete`

Delete a single git repository link

Delete a single git repository link.

**Synopsis:**
```
gcloud developer-connect connections git-repository-links delete
    (GIT_REPOSITORY_LINK : --connection=CONNECTION --location=LOCATION)
    [--async] [--etag=ETAG] [--request-id=REQUEST_ID] [--validate-only]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GitRepositoryLink resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument git_repository_link on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GIT_REPOSITORY_LINK
     ID of the gitRepositoryLink or fully qualified identifier for the
     gitRepositoryLink.

     To set the git_repository_link attribute:
     + provide the argument git_repository_link on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     The connection id of the gitRepositoryLink resource.

     To set the connection attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --connection on the command line.

  --location=LOCATION
     The location id of the gitRepositoryLink resource.

     To set the location attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--etag` | ETAG |  | This checksum is computed by the server based on the value of other fields, and may be sent on update and delete requests to ensure the client has an up-to-date value before proceeding. |
| `--request-id` | REQUEST_ID |  | An optional request ID to identify requests. Specify a unique request ID so that if you must retry your request, the server will know to ignore the request if it has already been completed. The server will guarantee that for at least 60 minutes after the first request. For example, consider a situation where you make an initial request and the request times out. If you make the request again with the same request ID, the server can check if original operation with the same request ID was received, and if so, will ignore the second request. This prevents clients from accidentally creating duplicate commitments. The request ID must be a valid UUID with the exception that zero UUID is not supported (00000000-0000-0000-0000-000000000000). |
| `--validate-only` |  |  | If set, validate the request, but do not actually post it. |


**Examples:**
```bash
To delete a git repository link my-git-repository-link in a connection
my-connection in location us-central1 run:

    $ gcloud developer-connect connections git-repository-links delete \
        my-git-repository-link --connection=my-connection \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/git-repository-links/delete)

---
### `gcloud developer-connect connections git-repository-links describe`

Get details of a single git repository link

Get details of a single git repository link.

**Synopsis:**
```
gcloud developer-connect connections git-repository-links describe
    (GIT_REPOSITORY_LINK : --connection=CONNECTION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GitRepositoryLink resource - Name of the resource The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument git_repository_link on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GIT_REPOSITORY_LINK
     ID of the gitRepositoryLink or fully qualified identifier for the
     gitRepositoryLink.

     To set the git_repository_link attribute:
     + provide the argument git_repository_link on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     The connection id of the gitRepositoryLink resource.

     To set the connection attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --connection on the command line.

  --location=LOCATION
     The location id of the gitRepositoryLink resource.

     To set the location attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the details of a single git repository link my-git-repository-link
in a conenction my-connection in location us-central1 run:

$ gcloud developer-connect connections git-repository-links \        describe my-git-repository-link --connection=my-connection \
    --location=us-central1-a
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/git-repository-links/describe)

---
### `gcloud developer-connect connections git-repository-links fetch-read-token`

Fetch the read token of a given gitRepositoryLink

Fetch the read token of a given gitRepositoryLink.

**Synopsis:**
```
gcloud developer-connect connections git-repository-links fetch-read-token
    (GIT_REPOSITORY_LINK : --connection=CONNECTION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GitRepositoryLink resource - Developer Connect GitRepositoryLink from
which to fetch the read token. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument git_repository_link on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GIT_REPOSITORY_LINK
     ID of the gitRepositoryLink or fully qualified identifier for the
     gitRepositoryLink.

     To set the git_repository_link attribute:
     + provide the argument git_repository_link on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     The connection id of the gitRepositoryLink resource.

     To set the connection attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --connection on the command line.

  --location=LOCATION
     The location id of the gitRepositoryLink resource.

     To set the location attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the read token of a GitRepositoryLink named "my-git-repository-link"
in a Connection named "my-connection" in location "us-central1":

    $ gcloud developer-connect connections git-repository-links \
        fetch-read-token fetch-read-token my-git-repository-link \
        --connection=my-connection --location=us-central1 \
        --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/git-repository-links/fetch-read-token)

---
### `gcloud developer-connect connections git-repository-links fetch-read-write-token`

Fetch the read/write token of a given gitRepositoryLink

Fetch the read/write token of a given gitRepositoryLink.

**Synopsis:**
```
gcloud developer-connect connections git-repository-links
    fetch-read-write-token
    (GIT_REPOSITORY_LINK : --connection=CONNECTION --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
GitRepositoryLink resource - Developer Connect GitRepositoryLink from
which to fetch the read/write token. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument git_repository_link on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GIT_REPOSITORY_LINK
     ID of the gitRepositoryLink or fully qualified identifier for the
     gitRepositoryLink.

     To set the git_repository_link attribute:
     + provide the argument git_repository_link on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --connection=CONNECTION
     The connection id of the gitRepositoryLink resource.

     To set the connection attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --connection on the command line.

  --location=LOCATION
     The location id of the gitRepositoryLink resource.

     To set the location attribute:
     + provide the argument git_repository_link on the command line with
       a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get the read/write token of a GitRepositoryLink named
"my-git-repository-link" in a Connection named "my-connection":

    $ gcloud developer-connect connections git-repository-links \
        fetch-read-write-token fetch-read-write-token \
        my-git-repository-link --connection=my-connection \
        --location=us-central1 --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/git-repository-links/fetch-read-write-token)

---
### `gcloud developer-connect connections git-repository-links list`

List all git repository links in a connection

List all git repository links in a connection.

**Synopsis:**
```
gcloud developer-connect connections git-repository-links list
    (--connection=CONNECTION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--connection` | CONNECTION |  | _[This must be specified.]_ ID of the connection or fully qualified identifier for the connection. To set the connection attribute: + provide the argument --connection on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[This must be specified.]_ The location id of the connection resource. To set the location attribute: + provide the argument --connection on the command line with a fully specified name; + provide the argument --location on the command line. |


**Examples:**
```bash
To list all git repository links in a connection my-connection in location
us-central1 run:

    $ gcloud developer-connect connections git-repository-links list \
        --connection=my-connection --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/developer-connect/connections/git-repository-links/list)

---