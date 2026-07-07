# gcloud iap oauth-clients

manage IAP OAuth clients

### `gcloud iap oauth-clients create`

Create a Cloud IAP OAuth client in the project

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-clients create is used to create an OAuth client in the
project to be used by Cloud IAP. To call this command, the Cloud OAuth
brand for the project must exist and be set for 'internal only'. The new
client is owned by Cloud IAP.

**Synopsis:**
```
gcloud iap oauth-clients create BRAND --display_name=DISPLAY_NAME
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Brand resource - Name of the Cloud OAuth brand to create a Cloud IAP OAuth
client under. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument brand on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BRAND
     ID of the brand or fully qualified identifier for the brand.

     To set the brand attribute:
     + provide the argument brand on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display` | DISPLAY_NAME |  | User friendly name for the Cloud IAP OAuth client. |


**Examples:**
```bash
To create a Cloud IAP OAuth client for the current project, run:

    $ gcloud iap oauth-clients create BRAND --display_name=DISPLAY_NAME

To create a Cloud IAP OAuth client for the project PROJECT_ID, run:

    $ gcloud iap oauth-clients create BRAND \
      --display_name=DISPLAY_NAME --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-clients/create)

---
### `gcloud iap oauth-clients delete`

Delete a Cloud IAP OAuth client

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-clients delete is used to delete a Cloud IAP OAuth client.
Note this command cannot be used to delete any other type of OAuth client
in your project.

**Synopsis:**
```
gcloud iap oauth-clients delete (NAME : --brand=BRAND)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Proxy client resource - Name of the Cloud IAP OAuth client to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the proxy client or fully qualified identifier for the proxy
     client.

     To set the identity_aware_proxy_clients attribute:
     + provide the argument name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --brand=BRAND
     The name of the OAuth brand.

     To set the brand attribute:
     + provide the argument name on the command line with a fully
       specified name;
     + provide the argument --brand on the command line.
```

**Examples:**
```bash
To delete a Cloud IAP OAuth client named CLIENT for the current project and
brand BRAND, run:

    $ gcloud iap oauth-clients delete CLIENT --brand=BRAND

To delete a Cloud IAP OAuth client named CLIENT for a specific project
PROJECT_ID and brand BRAND, run:

    $ gcloud iap oauth-clients delete CLIENT --brand=BRAND \
      --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-clients/delete)

---
### `gcloud iap oauth-clients describe`

Describe a Cloud IAP OAuth client

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-clients describe is used to describe a Cloud IAP OAuth
client. Note this command cannot be used to describe any other type of
OAuth client in your project.

**Synopsis:**
```
gcloud iap oauth-clients describe (NAME : --brand=BRAND)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Proxy client resource - Name of the Cloud IAP OAuth client to describe.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the proxy client or fully qualified identifier for the proxy
     client.

     To set the identity_aware_proxy_clients attribute:
     + provide the argument name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --brand=BRAND
     The name of the OAuth brand.

     To set the brand attribute:
     + provide the argument name on the command line with a fully
       specified name;
     + provide the argument --brand on the command line.
```

**Examples:**
```bash
To describe a Cloud IAP OAuth client for the current project, run:

    $ gcloud iap oauth-clients describe NAME

To describe a Cloud IAP OAuth client for a specific brand, run:

    $ gcloud iap oauth-clients describe NAME --brand=BRAND
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-clients/describe)

---
### `gcloud iap oauth-clients list`

List Cloud IAP OAuth clients in the Cloud OAuth brand

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-clients list is used to list Cloud IAP OAuth clients in a
Cloud OAuth brand. Note this command will not list any other type of OAuth
client in your project.

**Synopsis:**
```
gcloud iap oauth-clients list NAME [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Brand resource - Name of the Cloud OAuth brand to list Cloud IAP OAuth
clients under. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the brand or fully qualified identifier for the brand.

     To set the brand attribute:
     + provide the argument name on the command line.
```

**Examples:**
```bash
To list the Cloud IAP OAuth clients for the current project, run:

    $ gcloud iap oauth-clients list BRAND
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-clients/list)

---
### `gcloud iap oauth-clients reset-secret`

Reset a Cloud IAP OAuth client secret

(DEPRECATED) This command is deprecated and will be non-functional after
the IAP OAuth Admin APIs are turned down. Jan 19, 2026: Google will
discontinue support for the IAP OAuth Admin APIs. New projects will not be
able to use these APIs. March 19, 2026: The IAP OAuth Admin APIs will be
permanently shut down. Access to this feature will no longer be available.

gcloud iap oauth-clients reset-secret is used to reset a Cloud IAP OAuth
client secret. Note this command cannot be used to reset the secret for any
other type of OAuth client in your project.

**Synopsis:**
```
gcloud iap oauth-clients reset-secret (NAME : --brand=BRAND)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Proxy client resource - Name of the Cloud IAP OAuth client whose secret
will be reset. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument name on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the proxy client or fully qualified identifier for the proxy
     client.

     To set the identity_aware_proxy_clients attribute:
     + provide the argument name on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --brand=BRAND
     The name of the OAuth brand.

     To set the brand attribute:
     + provide the argument name on the command line with a fully
       specified name;
     + provide the argument --brand on the command line.
```

**Examples:**
```bash
To reset a Cloud IAP OAuth client secret, run:

    $ gcloud iap oauth-clients reset-secret NAME

To reset a Cloud IAP OAuth client secret for a specific brand, run:

    $ gcloud iap oauth-clients reset-secret NAME --brand=BRAND
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iap/oauth-clients/reset-secret)

---