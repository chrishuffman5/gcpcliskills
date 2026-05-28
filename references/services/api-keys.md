# gcloud services api-keys

manage API keys

### `gcloud services api-keys create`

Create an API key

Create an API key.

**Synopsis:**
```
gcloud services api-keys create [--annotations=[KEY=VALUE,...]] [--async]
    [--display-name=DISPLAY_NAME] [--key-id=KEY_ID]
    [--service-account=SERVICE_ACCOUNT]
    [--api-target=service=SERVICE,[...]
      --allowed-application=[sha1_fingerprint=SHA1_FINGERPRINT,
      package_name=PACKAGE_NAME,...]
      | --allowed-bundle-ids=[ALLOWED_BUNDLE_IDS,...]
      | --allowed-ips=[ALLOWED_IPS,...]
      | --allowed-referrers=[ALLOWED_REFERRERS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--annotations` | [KEY=VALUE,...] |  | Annotations are key resource. Specify annotations as a key-value dictionary for small amounts of arbitrary client data. |
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name of the key to create. |
| `--key-id` | KEY_ID |  | User-specified ID of the key to create. |
| `--service-account` | SERVICE_ACCOUNT |  | The email of the service account the key is bound to. If this field is specified, the key is a service account bound key and auth enabled. |
| `--api-target` | service=SERVICE,[...] |  | Repeatable. Specify service and optionally one or multiple specific methods. Both fields are case insensitive. If you need to specify methods, it should be specified with the --flags-file. See $ gcloud topic flags-file for details. See the examples section for how to use --api-target in --flags-file. |


**Examples:**
```bash
To create a key with display name and allowed IPs specified:

    $ gcloud services api-keys create --display-name="test name" \
        --allowed-ips=2620:15c:2c4:203:2776:1f90:6b3b:217,104.133.8.78

To create a key with annotations:

    $ gcloud services api-keys create --annotations=foo=bar,abc=def

To create a key with user-specified key ID:

    $ gcloud services api-keys create --key-id="my-key-id"

To create a key with allowed referrers restriction:

    $ gcloud services api-keys create \
        --allowed-referrers="https://www.example.com/*,http://sub.exampl\
    e.com/*"

To create a key with allowed IOS app bundle IDs:

    $ gcloud services api-keys create --allowed-bundle-ids=my.app

To create a key with allowed Android application:

    $ gcloud services api-keys create \
        --allowed-application=sha1_fingerprint=foo1,\
    package_name=bar.foo \
        --allowed-application=sha1_fingerprint=foo2,package_name=foo.bar

To create a key with allowed API targets (service name only):

    $ gcloud services api-keys create \
        --api-target=service=bar.service.com \
        --api-target=service=foo.service.com

To create a key with service account:

    $ gcloud services api-keys create \
        --service-account=my-service-account

To create a key with allowed API targets (service and methods are
specified):

    $ gcloud services api-keys create --flags-file=my-flags.yaml

The content of 'my-flags.yaml' is as follows:

    - --api-target:
        service: "foo.service.com"
    - --api-target:
        service: "bar.service.com"
        methods:
          - "foomethod"
          - "barmethod"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/create)

---
### `gcloud services api-keys delete`

Delete an API key

Delete an API key.

**Synopsis:**
```
gcloud services api-keys delete (KEY : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The name of the key to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + location will default to global.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
Delete an API Key :

    $ gcloud services api-keys delete \
        projects/myproject/locations/global/keys/1234

    $ gcloud services api-keys delete 1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/delete)

---
### `gcloud services api-keys describe`

Describe an API key's metadata

Describe an API key's metadata.

**Synopsis:**
```
gcloud services api-keys describe (KEY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The name of the key to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + location will default to global.
```

**Examples:**
```bash
To describe an API key using Key:

    $ gcloud services api-keys describe 1234 OR
    $ gcloud services api-keys describe \
        projects/myproject/locations/global/keys/1234

To describe an API key with key and project:

    $ gcloud services api-keys describe 1234 --project=myproject

To describe an API key with key, project, and location:

    $ gcloud services api-keys describe 1234 --project=myproject \
      --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/describe)

---
### `gcloud services api-keys get-key-string`

Get the key string of an API key

**Synopsis:**
```
gcloud services api-keys get-key-string (KEY : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The name of the key to retrieve key string. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + location will default to global.
```

**Examples:**
```bash
To get the key string of API key 1234, run:

    $ gcloud services api-keys get-key-string 1234

To get the key string of API key 1234 in project myproject using the fully
qualified API key name, run:

    $ gcloud services api-keys get-key-string \
         projects/myproject/locations/global/keys/1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/get-key-string)

---
### `gcloud services api-keys list`

Lists API keys

Lists the API keys of a given project.

**Synopsis:**
```
gcloud services api-keys list [--show-deleted] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-deleted` |  |  | Show soft-deleted keys by specifying this flag. |


**Examples:**
```bash
List keys of a given project:

    $ gcloud services api-keys list

List keys of a given project, including keys that were soft-deleted in the
past 30 days.:

    $ gcloud services api-keys list --show-deleted --project=my_project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/list)

---
### `gcloud services api-keys lookup`

Look up resource name of a key string

Look up resource name of a key string.

**Synopsis:**
```
gcloud services api-keys lookup KEY_STRING [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
KEY_STRING
   Key string of the key
```

**Examples:**
```bash
Look up resource name of a key string named my-key-string:

    $ gcloud services api-keys lookup my-key-string
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/lookup)

---
### `gcloud services api-keys undelete`

Undelete an API key

API Keys that are deleted will be retained in the system for 30 days. If a
key is still within this retention window, it can be undeleted with this
command.

**Synopsis:**
```
gcloud services api-keys undelete
    ([KEY : --location=LOCATION] --key-string=KEY_STRING) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Exactly one of these must be specified:

  Key resource - The name of the key to undelete. The arguments in this
  group can be used to specify the attributes of this resource. (NOTE)
  Some attributes are not given arguments in this group but can be set in
  other ways.

  To set the project attribute:
   + provide the argument key on the command line with a fully specified
     name;
   + provide the argument --project on the command line;
   + set the property core/project.

    KEY
       ID of the key or fully qualified identifier for the key.

       To set the key attribute:
       - provide the argument key on the command line.

       This positional argument must be specified if any of the other
       arguments in this group are specified.

    --location=LOCATION
       Location of the key.

       To set the location attribute:
       - provide the argument key on the command line with a fully
         specified name;
       - provide the argument --location on the command line;
       - location will default to global.

  --key-string=KEY_STRING
     Key String of the key.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
UnDelete an API Key (Key or key-string should be specified):

To undelete with key 1234, run:

    $ gcloud services api-keys undelete 1234

To undelete with 1234 in project myproject using the fully qualified API
key name, run:

    $ gcloud services api-keys undelete \
      projects/myproject/locations/global/keys/1234

To undelete using a Key-string, run:

    $ gcloud services api-keys undelete --key-string='my-key-string'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/undelete)

---
### `gcloud services api-keys update`

Update an API key's metadata

Update an API key's metadata.

**Synopsis:**
```
gcloud services api-keys update (KEY : --location=LOCATION) [--async]
    [--display-name=DISPLAY_NAME]
    [--annotations=[KEY=VALUE,...] | --clear-annotations]
    [--clear-restrictions | --api-target=service=SERVICE,[...]
      --allowed-application=[sha1_fingerprint=SHA1_FINGERPRINT,
      package_name=PACKAGE_NAME,...]
      | --allowed-bundle-ids=[ALLOWED_BUNDLE_IDS,...]
      | --allowed-ips=[ALLOWED_IPS,...]
      | --allowed-referrers=[ALLOWED_REFERRERS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The name of the key to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument key on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  KEY
     ID of the key or fully qualified identifier for the key.

     To set the key attribute:
     + provide the argument key on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the key.

     To set the location attribute:
     + provide the argument key on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + location will default to global.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name of the key to update. |


**Examples:**
```bash
To remove all restrictions of the key:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id --clear-restrictions

To update display name and set allowed ips as server key restrictions:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id --display-name="test name" \
        --allowed-ips=2620:15c:2c4:203:2776:1f90:6b3b:217,104.133.8.78

To update annotations:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id --annotations=foo=bar,abc=def

To update key's allowed referrers restriction:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id \
        --allowed-referrers="https://www.example.com/*,http://sub.exampl\
    e.com/*"

To update key's allowed ios app bundle ids:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id --allowed-bundle-ids=my.app

To update key's allowed android application:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id \
        --allowed-application=sha1_fingerprint=foo1,package_name=bar1 \
        --allowed-application=sha1_fingerprint=foo2,package_name=bar2

To update keys' allowed api target with multiple services:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id \
        --api-target=service=bar.service.com \
        --api-target=service=foo.service.com

To update keys' allowed api target with service and method:

    $ gcloud services api-keys update \
        projects/myproject/keys/my-key-id --flags-file=my-flags.yaml

    The content of 'my-flags.yaml' is as following:

      - --api-target:
          service: "foo.service.com"
      - --api-target:
          service: "bar.service.com"
          methods:
          - "foomethod"
          - "barmethod"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/services/api-keys/update)

---