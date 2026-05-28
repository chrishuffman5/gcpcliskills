# gcloud network-security security-profiles

manage Network Security - Security Profiles


## `gcloud network-security security-profiles custom-intercept` — manage Security Profiles - Custom Intercept Profile
### `gcloud network-security security-profiles custom-intercept create`

Create a new Custom Intercept Profile

Create a new Custom Intercept Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles custom-intercept create
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    (--intercept-endpoint-group=INTERCEPT_ENDPOINT_GROUP
      : --intercept-endpoint-group-location=INTERCEPT_ENDPOINT_GROUP_LOCATION)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--intercept-endpoint-group` | INTERCEPT_ENDPOINT_GROUP |  | _[This must be specified.]_ ID of the intercept endpoint group or fully qualified identifier for the intercept endpoint group. To set the id attribute: + provide the argument --intercept-endpoint-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--intercept-endpoint-group-location` | INTERCEPT_ENDPOINT_GROUP_LOCATION |  | _[This must be specified.]_ Location of the intercept endpoint group. To set the location attribute: + provide the argument --intercept-endpoint-group on the command line with a fully specified name; + provide the argument --intercept-endpoint-group-location on the command line; + provide the argument --location on the command line; + provide the argument networksecurity.projects.locations.interceptEndpointGroupAssociations on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Custom Intercept Security Profile named intercept-profile
linked to a Intercept Endpoint Group (q.v.), run:

    $ gcloud network-security security-profiles custom-intercept \
      create intercept-profile --description="An Intercept Profile" \
      --intercept-endpoint-group=projects/my-project/locations/\
    global/interceptEndpointGroups/my-mep
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-intercept/create)

---
### `gcloud network-security security-profiles custom-intercept delete`

Delete a Security Profile

Delete the specified Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles custom-intercept delete
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Name of the Security Profile you want to
delete. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Security Profile called my-security-profile run:

    $ gcloud network-security security-profiles custom-intercept \
        delete my-security-profile
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-intercept/delete)

---
### `gcloud network-security security-profiles custom-intercept describe`

Describe a Custom InterceptSecurity Profile

Show details of the Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles custom-intercept describe
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Name of the Security Profile to be described.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To show details of a Security Profile named my-intercept-sp run:

    $ gcloud network-security security-profiles custom-intercept \
        describe my-intercept-sp --organization=1234 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-intercept/describe)

---
### `gcloud network-security security-profiles custom-intercept list`

List Custom Intercept Security Profiles

List Custom Intercept Security Profiles.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles custom-intercept list
    [--location=LOCATION : --organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[in this group can be used to specify the attributes of this resource.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[in this group can be used to specify the attributes of this resource.]_ Organization ID of the location. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list Custom Intercept security profiles in an organization, run:

    $ gcloud network-security security-profiles custom-intercept list \
        --organization=12345 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-intercept/list)

---
### `gcloud network-security security-profiles custom-intercept update`

Updates a Custom Intercept Profile

Update a Custom Intercept Security Profile.

The supported fields for update are description and labels.

**Synopsis:**
```
gcloud network-security security-profiles custom-intercept update
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a Custom Intercept Security Profile named
intercept-profile, run:

    $ gcloud network-security security-profiles custom-intercept \
      update intercept-profile --description="A new description" \
      --organization=1234567890 --location=global

To change the labels of a Custom Intercept Security Profile named
intercept-profile, run:

    $ gcloud network-security security-profiles custom-intercept \
      update intercept-profile \
      --update-labels=key1=value1,key2=value2 \
      --delete-labels=key3,key4 --organization=1234567890 \
      --location=glob
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-intercept/update)

---

## `gcloud network-security security-profiles custom-mirroring` — manage Security Profiles - Custom Mirroring Profile
### `gcloud network-security security-profiles custom-mirroring create`

Create a new Custom Mirroring Profile

Create a new Custom Mirroring Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles custom-mirroring create
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    (--mirroring-endpoint-group=MIRRORING_ENDPOINT_GROUP
      : --mirroring-endpoint-group-location=MIRRORING_ENDPOINT_GROUP_LOCATION)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--mirroring-endpoint-group` | MIRRORING_ENDPOINT_GROUP |  | _[This must be specified.]_ ID of the mirroring endpoint group or fully qualified identifier for the mirroring endpoint group. To set the id attribute: + provide the argument --mirroring-endpoint-group on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--mirroring-endpoint-group-location` | MIRRORING_ENDPOINT_GROUP_LOCATION |  | _[This must be specified.]_ Location of the mirroring endpoint group. To set the location attribute: + provide the argument --mirroring-endpoint-group on the command line with a fully specified name; + provide the argument --mirroring-endpoint-group-location on the command line; + provide the argument --location on the command line; + provide the argument networksecurity.projects.locations.mirroringEndpointGroupAssociations on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Custom Mirroring Security Profile named mirroring-profile
linked to a Mirroring Endpoint Group (q.v.), run:

    $ gcloud network-security security-profiles custom-mirroring \
      create mirroring-profile --description="A Mirroring Profile" \
      --mirroring-endpoint-group=projects/my-project/locations/\
    global/mirroringEndpointGroups/my-mep
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-mirroring/create)

---
### `gcloud network-security security-profiles custom-mirroring delete`

Delete a Security Profile

Delete the specified Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles custom-mirroring delete
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Name of the Security Profile you want to
delete. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Security Profile called my-security-profile run:

    $ gcloud network-security security-profiles custom-mirroring \
        delete my-security-profile
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-mirroring/delete)

---
### `gcloud network-security security-profiles custom-mirroring describe`

Describe a Custom MirroringSecurity Profile

Show details of the Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles custom-mirroring describe
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Name of the Security Profile to be described.
The arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To show details of a Security Profile named my-mirroring-sp run:

    $ gcloud network-security security-profiles custom-mirroring \
        describe my-mirroring-sp --organization=1234 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-mirroring/describe)

---
### `gcloud network-security security-profiles custom-mirroring list`

List Custom Mirroring Security Profiles

List Custom Mirroring Security Profiles.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles custom-mirroring list
    [--location=LOCATION : --organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[in this group can be used to specify the attributes of this resource.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[in this group can be used to specify the attributes of this resource.]_ Organization ID of the location. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list Custom Mirroring security profiles in an organization, run:

    $ gcloud network-security security-profiles custom-mirroring list \
        --organization=12345 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-mirroring/list)

---
### `gcloud network-security security-profiles custom-mirroring update`

Updates a Custom Mirroring Profile

Update a Custom Mirroring Security Profile.

The supported fields for update are description and labels.

**Synopsis:**
```
gcloud network-security security-profiles custom-mirroring update
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a Custom Mirroring Security Profile named
mirroring-profile, run:

    $ gcloud network-security security-profiles custom-mirroring \
      update mirroring-profile --description="A new description" \
      --organization=1234567890 --location=global

To change the labels of a Custom Mirroring Security Profile named
mirroring-profile, run:

    $ gcloud network-security security-profiles custom-mirroring \
      update mirroring-profile \
      --update-labels=key1=value1,key2=value2 \
      --delete-labels=key3,key4 --organization=1234567890 \
      --location=glob
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/custom-mirroring/update)

---

## `gcloud network-security security-profiles threat-prevention` — manage Security Profiles - Threat Prevention Profile
### `gcloud network-security security-profiles threat-prevention add-override`

Add overrides to Threat Prevention Profile

Add antivirus, severities, or threat-ids to existing threat prevention
profile with intended action on each specified. Check the updates of
add-override command by using gcloud network-security security-profiles
threat-prevention list-override my-security-profile.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention add-override
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    --action=ACTION
    (--antivirus=[PROTOCOL,...] | --severities=[SEVERITY_LEVEL,...]
      | --threat-ids=[THREAT-ID,...]) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: DEFAULT_ACTION, ALLOW, ALERT, DENY |  | Action associated with antivirus, severity, or threat-id. ACTION must be one of: DEFAULT_ACTION, ALLOW, ALERT, DENY. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To add an override, run:

    $ gcloud network-security security-profiles threat-prevention \
        add-override my-security-profile --severities=MEDIUM \
        --action=ALLOW

my-security-profile is the name of the Security Profile in the format
organizations/{organizationID}/locations/{location}/securityProfiles/
{security_profile_id} where organizationID is the organization ID to which
the changes should apply, location - global specified and
security_profile_id the Security Profile Identifier
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/add-override)

---
### `gcloud network-security security-profiles threat-prevention create`

Create a new Threat Prevention Profile

Create a new Security Profile with the given name.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention create
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Security Profile with the name my-security-profile and an
optional description as New Security Profile, run:

    $ gcloud network-security security-profiles threat-prevention \
      create my-security-profile --description="New Security Profile"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/create)

---
### `gcloud network-security security-profiles threat-prevention delete`

Delete a Security Profile

Delete the specified Security Profile.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention delete
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Name of the Security Profile you want to
delete. The arguments in this group can be used to specify the attributes
of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a Security Profile called my-security-profile run:

    $ gcloud network-security security-profiles threat-prevention \
        delete my-security-profile
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/delete)

---
### `gcloud network-security security-profiles threat-prevention delete-override`

Delete overrides of Threat Prevention Profile

To delete existing antivirus, severities, or threat-ids of threat
prevention profile. Check the updates of update-override command by using
gcloud network-security security-profiles threat-prevention list-override
my-security-profile.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention delete-override
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    (--antivirus=[PROTOCOL,...] | --severities=[SEVERITY_LEVEL,...]
      | --threat-ids=[THREAT-ID,...]) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--antivirus` | [PROTOCOL,...] |  | _[Exactly one of these must be specified:]_ List of comma-separated protocols where each value in the list indicates the protocol of the antivirus threat. |
| `--severities` | [SEVERITY_LEVEL,...] |  | _[Exactly one of these must be specified:]_ List of comma-separated severities where each value in the list indicates the severity of the threat. |
| `--threat-ids` | [THREAT-ID,...] |  | _[Exactly one of these must be specified:]_ List of comma-separated threat identifiers where each identifier in the list is a vendor-specified Signature ID representing a threat type. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To delete an override, run:

    $ gcloud network-security security-profiles threat-prevention \
        delete-override my-security-profile --severities=MEDIUM

my-security-profile is the name of the Security Profile in the format
organizations/{organizationID}/locations/{location}/securityProfiles/
{security_profile_id} where organizationID is the organization ID to which
the changes should apply, location - global specified and
security_profile_id the Security Profile Identifier
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/delete-override)

---
### `gcloud network-security security-profiles threat-prevention list`

List Threat Prevention Security Profiles

List Threat Prevention Security Profiles.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention list
    (--location=LOCATION : --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ Organization ID of the location. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list Threat Prevention security profiles in an organization, run:

    $ gcloud network-security security-profiles threat-prevention list \
        --organization=12345 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/list)

---
### `gcloud network-security security-profiles threat-prevention list-overrides`

List overrides of Threat Prevention Profile

To list existing antivirus, severities, or threat-ids of threat prevention
profile.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention list-overrides
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To list overrides, run:

    $ gcloud network-security security-profiles threat-prevention \
        list-overrides my-security-profile

my-security-profile is the name of the Security Profile in the format
organizations/{organizationID}/locations/{location}/securityProfiles/
{security_profile_id} where organizationID is the organization ID to which
the changes should apply, location - global specified and
security_profile_id the Security Profile Identifier
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/list-overrides)

---
### `gcloud network-security security-profiles threat-prevention update-override`

Update Overrides of Threat Prevention Profile

To update existing antivirus, severities, or threat-ids of threat
prevention profile with intended action on each specified. Check the
updates of update-override command by using gcloud network-security
security-profiles threat-prevention list-override my-security-profile.

For more examples, refer to the EXAMPLES section below.

**Synopsis:**
```
gcloud network-security security-profiles threat-prevention update-override
    (SECURITY_PROFILE : --location=LOCATION --organization=ORGANIZATION)
    --action=ACTION
    (--antivirus=[PROTOCOL,...] | --severities=[SEVERITY_LEVEL,...]
      | --threat-ids=[THREAT-ID,...]) [--async]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile resource - Security Profile Name. The arguments in this
group can be used to specify the attributes of this resource.

This must be specified.

  SECURITY_PROFILE
     ID of the security_profile or fully qualified identifier for the
     security_profile.

     To set the security_profile attribute:
     + provide the argument security_profile on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile - Global.

     To set the location attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID to which the changes should apply.

     To set the organization attribute:
     + provide the argument security_profile on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: DEFAULT_ACTION, ALLOW, ALERT, DENY |  | Action associated with antivirus, severity, or threat-id. ACTION must be one of: DEFAULT_ACTION, ALLOW, ALERT, DENY. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update an override, run:

    $ gcloud network-security security-profiles threat-prevention \
        update-override my-security-profile --severities=MEDIUM \
        --action=ALLOW

my-security-profile is the name of the Security Profile in the format
organizations/{organizationID}/locations/{location}/securityProfiles/
{security_profile_id} where organizationID is the organization ID to which
the changes should apply, location - global specified and
security_profile_id the Security Profile Identifier
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profiles/threat-prevention/update-override)

---