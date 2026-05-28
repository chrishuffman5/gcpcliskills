# gcloud essential-contacts (top-level commands)

### `gcloud essential-contacts compute`

Compute the essential contacts that are subscribed to the specified notification categories for a resource

This command will return the contacts subscribed to any of the notification
categories that have been set on the requested resource or any of its
ancestors.

**Synopsis:**
```
gcloud essential-contacts compute
    --notification-categories=[NOTIFICATION_CATEGORIES,...]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--notification-categories` | one of: all, billing, legal, notification-category-unspecified, product-updates, security, suspension, technical, technical-incidents |  | list of notification categories contact is subscribed to. NOTIFICATION_CATEGORIES must be one of: all, billing, legal, notification-category-unspecified, product-updates, security, suspension, technical, technical-incidents. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ folder number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ organization number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ project number or id where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |


**Examples:**
```bash
To compute contacts subscribed to the technical category for the current
project, run:

    $ gcloud essential-contacts compute \
    --notification-categories=technical

To compute contacts subscribed to the product-updates or billing categories
for the folder with id 123, run:

    $ gcloud essential-contacts compute \
    --notification-categories=product-updates,billing --folder=123

To compute contacts subscribed to the legal category for the organization
with id 456, run:

    $ gcloud essential-contacts compute \
    --notification-categories=legal --organization=456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts/compute)

---
### `gcloud essential-contacts create`

Create an essential contact

**Synopsis:**
```
gcloud essential-contacts create --email=EMAIL --language=LANGUAGE
    --notification-categories=[NOTIFICATION_CATEGORIES,...]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--email` | EMAIL |  | email address of contact. |
| `--language` | LANGUAGE |  | preferred language of contact. Must be a valid ISO 639-1 language code. |
| `--notification-categories` | one of: all, billing, legal, notification-category-unspecified, product-updates, security, suspension, technical, technical-incidents |  | list of notification categories contact is subscribed to. NOTIFICATION_CATEGORIES must be one of: all, billing, legal, notification-category-unspecified, product-updates, security, suspension, technical, technical-incidents. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ folder number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ organization number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ project number or id where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |


**Examples:**
```bash
To create a contact in the current project, run:

    $ gcloud essential-contacts create \
    --email=contact-email@example.com \
    --notification-categories=technical,product-updates \
    --language=en-US

To create a contact in the folder with id 456, run:

    $ gcloud essential-contacts create \
    --email=contact-email@example.com \
    --notification-categories=technical,product-updates \
    --language=en-US --folder=456

To create a contact in the organization with id 456, run:

    $ gcloud essential-contacts create \
    --email=contact-email@example.com \
    --notification-categories=technical,product-updates \
    --language=en-US --organization=456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts/create)

---
### `gcloud essential-contacts delete`

Delete an essential contact

**Synopsis:**
```
gcloud essential-contacts delete CONTACT_ID
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONTACT_ID
   id of contact to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ folder number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ organization number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ project number or id where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |


**Examples:**
```bash
To delete the contact with id 123 in the current project, run:

    $ gcloud essential-contacts delete 123

To delete the contact with id 123 in the folder with id 456, run:

    $ gcloud essential-contacts delete 123 --folder=456

To delete the contact with id 123 in the organization with id 456, run:

    $ gcloud essential-contacts delete 123 --organization=456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts/delete)

---
### `gcloud essential-contacts describe`

Describe an essential contact

**Synopsis:**
```
gcloud essential-contacts describe CONTACT_ID
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONTACT_ID
   id of contact to describe.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ folder number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ organization number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ project number or id where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |


**Examples:**
```bash
To describe the contact with id 123 in the current project, run:

    $ gcloud essential-contacts describe 123

To describe the contact with id 123 in the folder with id 456, run:

    $ gcloud essential-contacts describe 123 --folder=456

To describe the contact with id 123 in the organization with id 456, run:

    $ gcloud essential-contacts describe 123 --organization=456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts/describe)

---
### `gcloud essential-contacts list`

List essential contacts for a resource

**Synopsis:**
```
gcloud essential-contacts list
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | _[At most one of these can be specified:]_ folder number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--organization` | ORGANIZATION |  | _[At most one of these can be specified:]_ organization number where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |
| `--project` | PROJECT |  | _[At most one of these can be specified:]_ project number or id where contacts are set. If neither --project, --folder, nor --organization are provided then the config property [core/project] will be used as the resource. |


**Examples:**
```bash
To list the contacts set on the current project:

    $ gcloud essential-contacts list [--page_size=10] [--limit=20]

To list the contacts set on the folder with id 456, run:

    $ gcloud essential-contacts list --folder=456 [--page_size=10] \
      [--limit=20]

To list the contacts set on the organization with id 456, run:

    $ gcloud essential-contacts list --organization=456 \
    [--page_size=10] [--limit=20]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts/list)

---
### `gcloud essential-contacts update`

Update an essential contact

**Synopsis:**
```
gcloud essential-contacts update CONTACT_ID [--language=LANGUAGE]
    [--notification-categories=[NOTIFICATION_CATEGORIES,...]]
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONTACT_ID
   id of contact
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--language` | LANGUAGE |  | preferred language of contact. Must be a valid ISO 639-1 language code. |
| `--notification-categories` | one of: all, billing, legal, notification-category-unspecified, product-updates, security, suspension, technical, technical-incidents |  | list of notification categories contact is subscribed to. NOTIFICATION_CATEGORIES must be one of: all, billing, legal, notification-category-unspecified, product-updates, security, suspension, technical, technical-incidents. |


**Examples:**
```bash
To update the notification category subscriptions for the contact with id
123 in the current project, run:

    $ gcloud essential-contacts update 123 \
    --notification-categories=legal,suspension

To update the language preference for the contact with id 123 in the folder
with id 456, run:

    $ gcloud essential-contacts update 123 --language=es --folder=456

To update the notification category subscriptions and language preference
for the contact with id 123 in the organization with id 456, run:

    $ gcloud essential-contacts update 123 \
    --notification-categories=legal --language=en-US \
    --organization=456
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/essential-contacts/update)

---