# gcloud domains registrations

manage Cloud Domains registrations

### `gcloud domains registrations delete`

Delete a Cloud Domains registration

Delete a registration resource.

Delete can only be called on registrations in state EXPORTED with
expire_time in the past. It also works for registrations in state
REGISTRATION_FAILED, TRANSFER_FAILED, and TRANSFER_PENDING.

**Synopsis:**
```
gcloud domains registrations delete REGISTRATION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to delete. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a registration for example.com, run:

    $ gcloud domains registrations delete example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/delete)

---
### `gcloud domains registrations describe`

Describe an existing Cloud Domains registration

Print information about an existing registration.

**Synopsis:**
```
gcloud domains registrations describe REGISTRATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To describe a registration for example.com, run:

    $ gcloud domains registrations describe example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/describe)

---
### `gcloud domains registrations get-register-parameters`

Get register parameters (including availability) of a specific domain

Get parameters needed to register a new domain, including price,
availability, supported privacy modes and notices.

In contrast to the search-domains command, this command returns up-to-date
domain name availability information.

**Synopsis:**
```
gcloud domains registrations get-register-parameters DOMAIN
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN
   Domain to get register parameters for.
```

**Examples:**
```bash
To check if example.com is available for registration, run:

    $ gcloud domains registrations get-register-parameters example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/get-register-parameters)

---
### `gcloud domains registrations initiate-push-transfer`

Initiates the push transfer process

Initiates the Push Transfer process to transfer the domain to another
registrar. The process might complete instantly or might require
confirmation or additional work. Check the emails sent to the email address
of the registrant. The process is aborted after a timeout if it's not
completed.

This method is only supported for domains that have the
REQUIRE_PUSH_TRANSFER property in the list of domain_properties. The domain
must also be unlocked before it can be transferred to a different
registrar.

**Synopsis:**
```
gcloud domains registrations initiate-push-transfer REGISTRATION [--async]
    [--tag=TAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to transfer. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--tag` | TAG |  | The Tag of the new registrar. Can be found at https://nominet.uk/registrar-list/ |


**Examples:**
```bash
To initiate a push transfer for example.co.uk, run:

    $ gcloud domains registrations initiate-push-transfer \
        example.co.uk --tag=NEW_REGISTRY_TAG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/initiate-push-transfer)

---
### `gcloud domains registrations list`

List Cloud Domains registrations

List Cloud Domains registrations in the project.

**Synopsis:**
```
gcloud domains registrations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all registrations in the project, run:

    $ gcloud domains registrations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/list)

---
### `gcloud domains registrations register`

Register a new domain

Create a new Cloud Domains registration resource by registering a new
domain. The new resource's ID will be equal to the domain name.

After this command executes, the resource will be in state
REGISTRATION_PENDING. The registration process should complete in less than
5 minutes. After that the resource will be in state ACTIVE. In rare cases
this process can take much longer due, for example, to a downtime of the
domain registry.

Also in rare cases, the domain may end up in state REGISTRATION_FAILED. In
that case, delete the registration resource and try again.

When using Cloud DNS Zone DNSSEC will be enabled by default whenever the
Zone is DNSSEC signed. You can choose to not enable DNSSEC by using the
--disable-dnssec flag.

**Synopsis:**
```
gcloud domains registrations register REGISTRATION
    [--contact-data-from-file=CONTACT_DATA_FILE_NAME]
    [--contact-privacy=CONTACT_PRIVACY] [--validate-only]
    [--cloud-dns-zone=CLOUD_DNS_ZONE | --name-servers=NAME_SERVER,...,[...]
      | --use-google-domains-dns] [--async] [--disable-dnssec]
    [--labels=[KEY=VALUE,...]] [--notices=[NOTICE,...]]
    [--yearly-price=YEARLY_PRICE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain name to register. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To register example.com interactively, run:

    $ gcloud domains registrations register example.com

To register example.com using contact data from a YAML file contacts.yaml,
run:

    $ gcloud domains registrations register example.com \
        --contact-data-from-file=contacts.yaml

To register example.com with interactive prompts disabled, provide
--contact-data-from-file, --contact-privacy, --yearly-price flags and one
of the flags for setting authoritative name servers. Sometimes also
--notices flag is required. For example, run:

    $ gcloud domains registrations register example.com \
        --contact-data-from-file=contacts.yaml \
        --contact-privacy=private-contact-data \
        --yearly-price="12.00 USD" --cloud-dns-zone=example-com --quiet
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/register)

---
### `gcloud domains registrations renew-domain`

Renew a recently expired Cloud Domains registration

Use this method to renew domains that expired within the last 30 days.
Renewing your domain extends it for one year from the previous expiration
date and you are charged the yearly renewal price.

**Synopsis:**
```
gcloud domains registrations renew-domain REGISTRATION [--validate-only]
    [--async] [--yearly-price=YEARLY_PRICE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to renew. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To renew a registration for example.com interactively, run:

    $ gcloud domains registrations renew-domain example.com

To renew example.com with interactive prompts disabled, provide the
--yearly-price flag. For example, run:

    $ gcloud domains registrations renew-domain example.com \
        --yearly-price="12.00 USD" --quiet
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/renew-domain)

---
### `gcloud domains registrations search-domains`

Search for available domains

Search for available domains relevant to a specified query.

This command uses cached domain name availability information. Use the
get-register-params command to get up-to-date availability information.

**Synopsis:**
```
gcloud domains registrations search-domains DOMAIN_QUERY
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN_QUERY
   Domain search query. May be a domain name or arbitrary search terms.
```

**Examples:**
```bash
To search for domains for my-new-project, run:

    $ gcloud domains registrations search-domains my-new-project

To search for a specific domain, like example.com, and get suggestions for
other domain endings, run:

    $ gcloud domains registrations search-domains example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/search-domains)

---
### `gcloud domains registrations update`

Update a Cloud Domains registration

Update an existing registration. Currently used for updating labels only.
Run:

    $ gcloud help alpha domains registrations configure

to see how to change management, DNS or contact settings.

**Synopsis:**
```
gcloud domains registrations update REGISTRATION [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to update. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To add a label with key environment and value test for example.com, run:

    $ gcloud domains registrations update example.com \
        --update-labels="project=example,environment=test"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/update)

---

## `gcloud domains registrations authorization-code` — manage Cloud Domains registration's authorization code
### `gcloud domains registrations authorization-code get`

Get authorization code of a specific Cloud Domains registration

Get authorization code of a specific registration.

You can call this API only after 60 days have elapsed since initial
registration.

**Synopsis:**
```
gcloud domains registrations authorization-code get REGISTRATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to get authorization code
for. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To get authorization code of example.com, run:

    $ gcloud domains registrations authorization-code get example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/authorization-code/get)

---
### `gcloud domains registrations authorization-code reset`

Resets authorization code of a specific Cloud Domains registration

Resets authorization code of a specific registration.

You can call this API only after 60 days have elapsed since initial
registration.

**Synopsis:**
```
gcloud domains registrations authorization-code reset REGISTRATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to reset authorization
code for. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To reset authorization code of example.com, run:

    $ gcloud domains registrations authorization-code reset example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/authorization-code/reset)

---

## `gcloud domains registrations configure` — configure Cloud Domains registrations' management, DNS or contact settings
### `gcloud domains registrations configure contacts`

Configure contact settings of a Cloud Domains registration

Configure registration's contact settings: email, phone number, postal
address and also contact privacy.

In some cases such changes have to be confirmed through an email sent to
the registrant before they take effect. In order to resend the email,
execute this command again.

NOTE: Please consider carefully any changes to contact privacy settings
when changing from "redacted-contact-data" to "public-contact-data." There
may be a delay in reflecting updates you make to registrant contact
information such that any changes you make to contact privacy (including
from "redacted-contact-data" to "public-contact-data") will be applied
without delay but changes to registrant contact information may take a
limited time to be publicized. This means that changes to contact privacy
from "redacted-contact-data" to "public-contact-data" may make the previous
registrant contact data public until the modified registrant contact
details are published.

**Synopsis:**
```
gcloud domains registrations configure contacts REGISTRATION
    [--contact-data-from-file=CONTACT_DATA_FILE_NAME]
    [--contact-privacy=CONTACT_PRIVACY] [--validate-only] [--async]
    [--notices=[NOTICE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to configure contact
settings for. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To start an interactive flow to configure contact settings for example.com,
run:

    $ gcloud domains registrations configure contacts example.com

To enable contact privacy for example.com, run:

    $ gcloud domains registrations configure contacts example.com \
        --contact-privacy=private-contact-data

To change contact data for example.com according to information from a YAML
file contacts.yaml, run:

    $ gcloud domains registrations configure contacts example.com \
        --contact-data-from-file=contacts.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/configure/contacts)

---
### `gcloud domains registrations configure dns`

Configure DNS settings of a Cloud Domains registration

Configure DNS settings of a Cloud Domains registration.

In most cases, this command is used for changing the authoritative name
servers and DNSSEC options for the given domain. However, advanced options
like glue records are available.

**Synopsis:**
```
gcloud domains registrations configure dns REGISTRATION [--validate-only]
    [--cloud-dns-zone=CLOUD_DNS_ZONE
      | --dns-settings-from-file=DNS_SETTINGS_FILE_NAME
      | --name-servers=NAME_SERVER,...,[...] | --use-google-domains-dns]
    [--async] [--disable-dnssec] [--unsafe-dns-update]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to configure DNS settings
for. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To start an interactive flow to configure DNS settings for example.com,
run:

    $ gcloud domains registrations configure dns example.com

To use Cloud DNS managed-zone example-zone for example.com, run:

    $ gcloud domains registrations configure dns example.com \
        --cloud-dns-zone=example-zone

DNSSEC will not be enabled as it may not be safe to enable it (e.g. when
the Cloud DNS managed-zone was signed less than 24h ago).

To use a signed Cloud DNS managed-zone example-zone for example.com and
enable DNSSEC, run:

    $ gcloud domains registrations configure dns example.com \
        --cloud-dns-zone=example-zone --no-disable-dnssec

To change DNS settings for example.com according to information from a YAML
file dns_settings.yaml, run:

    $ gcloud domains registrations configure dns example.com \
        --dns-settings-from-file=dns_settings.yaml

To disable DNSSEC, run:

    $ gcloud domains registrations configure dns example.com \
        --disable-dnssec
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/configure/dns)

---
### `gcloud domains registrations configure management`

Configure management settings of a Cloud Domains registration

Configure management settings of a registration. This includes settings
related to transfers, billing and renewals of a registration.

**Synopsis:**
```
gcloud domains registrations configure management REGISTRATION [--async]
    [--preferred-renewal-method=PREFERRED_RENEWAL_METHOD]
    [--transfer-lock-state=TRANSFER_LOCK_STATE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to configure management
settings for. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--preferred-renewal-method` | one of: automatic-renewal The domain is automatically renewed each year |  | Preferred Renewal Method of a registration. It defines how the registration should be renewed. The actual Renewal Method can be set to renewal-disabled in case of e.g. problems with the Billing Account or reporeted domain abuse. PREFERRED_RENEWAL_METHOD must be one of: automatic-renewal The domain is automatically renewed each year. renewal-disabled The domain won't be renewed and will expire at its expiration time. |
| `--transfer-lock-state` | one of: locked The transfer lock is locked |  | Transfer Lock of a registration. It needs to be unlocked in order to transfer the domain to another registrar. TRANSFER_LOCK_STATE must be one of: locked The transfer lock is locked. unlocked The transfer lock is unlocked. |


**Examples:**
```bash
To start an interactive flow to configure management settings for
example.com, run:

    $ gcloud domains registrations configure management example.com

To unlock a transfer lock of a registration for example.com, run:

    $ gcloud domains registrations configure management example.com \
        --transfer-lock-state=unlocked

To disable automatic renewals for example.com, run:

    $ gcloud domains registrations configure management example.com \
        --preferred-renewal-method=renewal-disabled
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/configure/management)

---

## `gcloud domains registrations google-domains-dns` — manage deprecated Google Domains DNS configuration
### `gcloud domains registrations google-domains-dns export-dns-record-sets`

Export your registration's Google Domains DNS zone's record-sets into a file

Export your registration's Google Domains DNS (deprecated) zone's
record-sets into a file. The formats you can export to are YAML records
format (default) and BIND zone file format.

**Synopsis:**
```
gcloud domains registrations google-domains-dns export-dns-record-sets
    REGISTRATION --records-file=RECORDS_FILE [--zone-file-format]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to get the DNS records
for. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--records-file` | RECORDS_FILE |  | File to which record-sets should be exported. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone-file-format` |  |  | Indicates that records-file should be in the zone file format. When using this flag, expect the record-set to be exported to a BIND zone formatted file. If you omit this flag, the record-set is exported into a YAML formatted records file. Note, this format flag determines the format of the output recorded in the records-file; it is different from the global --format flag which affects console output alone. |


**Examples:**
```bash
To export DNS record-sets of example.com into a YAML file, run:

    $ gcloud domains registrations google-domains-dns \
        export-dns-record-sets example.com --records-file=records.yaml

To export DNS record-sets of example.com into a BIND zone formatted file,
run:

    $ gcloud domains registrations google-domains-dns \
        export-dns-record-sets example.com \
        --records-file=records.zonefile --zone-file-format
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/google-domains-dns/export-dns-record-sets)

---
### `gcloud domains registrations google-domains-dns get-forwarding-config`

Get forwarding configuration of a specific Cloud Domains registration

Get forwarding configuration (deprecated) of a specific registration.

**Synopsis:**
```
gcloud domains registrations google-domains-dns get-forwarding-config
    REGISTRATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Registration resource - The domain registration to get the forwarding
config for. This represents a Cloud resource. (NOTE) Some attributes are
not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument registration on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  REGISTRATION
     ID of the registration or fully qualified identifier for the
     registration.

     To set the registration attribute:
     + provide the argument registration on the command line.
```

**Examples:**
```bash
To get forwarding configuration of example.com, run:

    $ gcloud domains registrations google-domains-dns \
        get-forwarding-config example.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/google-domains-dns/get-forwarding-config)

---

## `gcloud domains registrations operations` — manage Cloud Domains operations
### `gcloud domains registrations operations describe`

Show details about a Cloud Domains operation

Print information about a Cloud Domains operation.

**Synopsis:**
```
gcloud domains registrations operations describe OPERATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the registration attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
To describe an operation operation-id, run:

    $ gcloud domains registrations operations describe operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/operations/describe)

---
### `gcloud domains registrations operations list`

List Cloud Domains operations

List Cloud Domains operations in the project.

**Synopsis:**
```
gcloud domains registrations operations list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all operations in the project, run:

    $ gcloud domains registrations operations list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/operations/list)

---
### `gcloud domains registrations operations wait`

Wait for asynchronous operation to complete

Wait for a specified Cloud Domains operation to complete.

**Synopsis:**
```
gcloud domains registrations operations wait OPERATION
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The operation to wait for. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * location is always global.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the registration attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
To wait for an operation operation-id, run:

    $ gcloud domains registrations operations wait operation-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/registrations/operations/wait)

---