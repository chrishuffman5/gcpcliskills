# gcloud network-security security-profile-groups

manage Network Security - Security Profile Groups

### `gcloud network-security security-profile-groups create`

Create a new Security Profile Group

Create a new Security Profile Group with the given name.

**Synopsis:**
```
gcloud network-security security-profile-groups create
    (SECURITY_PROFILE_GROUP
      : --location=LOCATION --organization=ORGANIZATION)
    ([--custom-intercept-profile=CUSTOM_INTERCEPT_PROFILE
      : --custom-intercept-profile-location=CUSTOM_INTERCEPT_PROFILE_LOCATION --custom-intercept-profile-organization=CUSTOM_INTERCEPT_PROFILE_ORGANIZATION] [--custom-mirroring-profile=CUSTOM_MIRRORING_PROFILE : --custom-mirroring-profile-location=CUSTOM_MIRRORING_PROFILE_LOCATION --custom-mirroring-profile-organization=CUSTOM_MIRRORING_PROFILE_ORGANIZATION] [--threat-prevention-profile=THREAT_PREVENTION_PROFILE : --threat-prevention-profile-location=THREAT_PREVENTION_PROFILE_LOCATION --threat-prevention-profile-organization=THREAT_PREVENTION_PROFILE_ORGANIZATION])
    [--async] [--description=DESCRIPTION] [--labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile group resource - Security Profile Group Name. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SECURITY_PROFILE_GROUP
     ID of the security_profile_group or fully qualified identifier for
     the security_profile_group.

     To set the security_profile_group attribute:
     + provide the argument SECURITY_PROFILE_GROUP on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile_group - Global.

     To set the location attribute:
     + provide the argument SECURITY_PROFILE_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID of Security Profile Group

     To set the organization attribute:
     + provide the argument SECURITY_PROFILE_GROUP on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-intercept-profile` | CUSTOM_INTERCEPT_PROFILE |  | _[resource.]_ ID of the Security Profile or fully qualified identifier for the Security Profile. To set the name attribute: - provide the argument --custom-intercept-profile on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--custom-intercept-profile-location` | CUSTOM_INTERCEPT_PROFILE_LOCATION |  | _[resource.]_ Location of the Security Profile. NOTE: Only global security profiles are supported. To set the location attribute: - provide the argument --custom-intercept-profile on the command line with a fully specified name; - provide the argument --custom-intercept-profile-location on the command line; - provide the argument --location on the command line; - provide the argument networksecurity.organizations.locations.securityProfileGroups on the command line with a fully specified name. |
| `--custom-intercept-profile-organization` | CUSTOM_INTERCEPT_PROFILE_ORGANIZATION |  | _[resource.]_ Organization ID of the Security Profile. To set the organization attribute: - provide the argument --custom-intercept-profile on the command line with a fully specified name; - provide the argument --custom-intercept-profile-organization on the command line; - provide the argument --organization on the command line; - provide the argument networksecurity.organizations.locations.securityProfileGroups on the command line with a fully specified name. |
| `--custom-mirroring-profile` | CUSTOM_MIRRORING_PROFILE |  | _[resource.]_ ID of the Security Profile or fully qualified identifier for the Security Profile. To set the name attribute: - provide the argument --custom-mirroring-profile on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--custom-mirroring-profile-location` | CUSTOM_MIRRORING_PROFILE_LOCATION |  | _[resource.]_ Location of the Security Profile. NOTE: Only global security profiles are supported. To set the location attribute: - provide the argument --custom-mirroring-profile on the command line with a fully specified name; - provide the argument --custom-mirroring-profile-location on the command line; - provide the argument --location on the command line; - provide the argument networksecurity.organizations.locations.securityProfileGroups on the command line with a fully specified name. |
| `--custom-mirroring-profile-organization` | CUSTOM_MIRRORING_PROFILE_ORGANIZATION |  | _[resource.]_ Organization ID of the Security Profile. To set the organization attribute: - provide the argument --custom-mirroring-profile on the command line with a fully specified name; - provide the argument --custom-mirroring-profile-organization on the command line; - provide the argument --organization on the command line; - provide the argument networksecurity.organizations.locations.securityProfileGroups on the command line with a fully specified name. |
| `--threat-prevention-profile` | THREAT_PREVENTION_PROFILE |  | _[resource.]_ ID of the Security Profile or fully qualified identifier for the Security Profile. To set the name attribute: - provide the argument --threat-prevention-profile on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--threat-prevention-profile-location` | THREAT_PREVENTION_PROFILE_LOCATION |  | _[resource.]_ Location of the Security Profile. NOTE: Only global security profiles are supported. To set the location attribute: - provide the argument --threat-prevention-profile on the command line with a fully specified name; - provide the argument --threat-prevention-profile-location on the command line; - provide the argument --security-profile-location on the command line; - provide the argument --location on the command line; - provide the argument networksecurity.organizations.locations.securityProfileGroups on the command line with a fully specified name. |
| `--threat-prevention-profile-organization` | THREAT_PREVENTION_PROFILE_ORGANIZATION |  | _[resource.]_ Organization ID of the Security Profile. To set the organization attribute: - provide the argument --threat-prevention-profile on the command line with a fully specified name; - provide the argument --threat-prevention-profile-organization on the command line; - provide the argument --security-profile-organization on the command line; - provide the argument --organization on the command line; - provide the argument networksecurity.organizations.locations.securityProfileGroups on the command line with a fully specified name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile group |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a Security Profile Group with the name my-security-profile-group,
with a threat prevention profile using --threat-prevention-profile flag and
optional description as optional description, run:

    $ gcloud network-security security-profile-groups create \
      my-security-profile-group --organization=1234 \
      --location=global \
      --threat-prevention-profile=`organizations/1234/locations/\
    global/securityProfiles/my-security-profile` \
        --description='optional description'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profile-groups/create)

---
### `gcloud network-security security-profile-groups delete`

Delete a Security Profile Group

Delete the specified Security Profile Group.

**Synopsis:**
```
gcloud network-security security-profile-groups delete
    (SECURITY_PROFILE_GROUP
      : --location=LOCATION --organization=ORGANIZATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile group resource - Name of the Security Profile Group you
want to delete. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  SECURITY_PROFILE_GROUP
     ID of the security_profile_group or fully qualified identifier for
     the security_profile_group.

     To set the security_profile_group attribute:
     + provide the argument security_profile_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile_group on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile_group on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an Security Profile Group called my-security-profile-group run:

    $ gcloud network-security security-profile-groups delete \
        my-security-profile-group --organization=1234 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profile-groups/delete)

---
### `gcloud network-security security-profile-groups describe`

Describe a Security Profile Group

Show details of a Security Profile Group.

**Synopsis:**
```
gcloud network-security security-profile-groups describe
    (SECURITY_PROFILE_GROUP
      : --location=LOCATION --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile group resource - Name of the Security Profile Group to be
described. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  SECURITY_PROFILE_GROUP
     ID of the security_profile_group or fully qualified identifier for
     the security_profile_group.

     To set the security_profile_group attribute:
     + provide the argument security_profile_group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location ID of the resource.

     To set the location attribute:
     + provide the argument security_profile_group on the command line
       with a fully specified name;
     + provide the argument --location on the command line;
     + use default global location .

  --organization=ORGANIZATION
     Organization number.

     To set the organization attribute:
     + provide the argument security_profile_group on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Examples:**
```bash
To show details of a Security Profile Group named my-security-profile-group
run:

    $ gcloud network-security security-profile-groups describe \
        my-security-profile-group --organization=1234 --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profile-groups/describe)

---
### `gcloud network-security security-profile-groups list`

List Security Profile groups

List all Security Profile Groups in the specified location.

**Synopsis:**
```
gcloud network-security security-profile-groups list
    (--location=LOCATION : --organization=ORGANIZATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ Organization number. To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. |


**Examples:**
```bash
To list Security Profile Groups in specifed location, run:

    $ gcloud network-security security-profile-groups list \
        --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profile-groups/list)

---
### `gcloud network-security security-profile-groups update`

Update a Security Profile Group

Update details of a Security Profile Group.

**Synopsis:**
```
gcloud network-security security-profile-groups update
    (SECURITY_PROFILE_GROUP
      : --location=LOCATION --organization=ORGANIZATION) [--async]
    [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--threat-prevention-profile=THREAT_PREVENTION_PROFILE
      : --threat-prevention-profile-location=THREAT_PREVENTION_PROFILE_LOCATION --threat-prevention-profile-organization=THREAT_PREVENTION_PROFILE_ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Security profile group resource - Security Profile Group Name. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  SECURITY_PROFILE_GROUP
     ID of the security_profile_group or fully qualified identifier for
     the security_profile_group.

     To set the security_profile_group attribute:
     + provide the argument SECURITY_PROFILE_GROUP on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     location of the security_profile_group - Global.

     To set the location attribute:
     + provide the argument SECURITY_PROFILE_GROUP on the command line
       with a fully specified name;
     + provide the argument --location on the command line.

  --organization=ORGANIZATION
     Organization ID of Security Profile Group

     To set the organization attribute:
     + provide the argument SECURITY_PROFILE_GROUP on the command line
       with a fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. The default is False. |
| `--description` | DESCRIPTION |  | Brief description of the security profile group |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update a Security Profile Group with new threat prevention profile
my-new-security-profile, run:

    $ gcloud network-security security-profile-groups update \
      my-security-profile-group --organization=1234 \
      --location=global \
      --threat-prevention-profile=`organizations/1234/locations/\
    global/securityProfiles/my-new-security-profile` \
        --description='New Security Profile of type threat prevention'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-security/security-profile-groups/update)

---