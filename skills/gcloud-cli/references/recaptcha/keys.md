# gcloud recaptcha keys

managed reCAPTCHA Keys

### `gcloud recaptcha keys add-ip-override`

Add an IP override to a key

Add an IP override to a key.

**Synopsis:**
```
gcloud recaptcha keys add-ip-override KEY --ip=IP --override=OVERRIDE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA key to add the IP override to. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ip` | IP |  | IP address to override for the key. |
| `--override` | one of: allow, override-type-unspecified |  | If set to allow, the IP address/CIDR range will be allowlisted for the key. OVERRIDE must be one of: allow, override-type-unspecified. |


**Examples:**
```bash
$ gcloud recaptcha keys add-ip-override test-key --ip=1.2.3.4 \
    --override=allow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/add-ip-override)

---
### `gcloud recaptcha keys create`

Create a Key

Create a reCAPTCHA Key.

**Synopsis:**
```
gcloud recaptcha keys create --display-name=DISPLAY_NAME
    (--express | [--android (--allow-all-package-names
      | --package-names=[PACKAGE_NAMES,...])
      : --support-non-google-app-store-distribution]
      | [--ios (--allow-all-bundle-ids | --bundle-ids=[BUNDLE_IDS,...])
      : --key-id=KEY_ID --private-key-file=PATH_TO_FILE --team-id=TEAM_ID]
      | [--web (--allow-all-domains | --domains=[DOMAINS,...])
      : --allow-amp-traffic --integration-type=INTEGRATION_TYPE
      --security-preference=SECURITY_PREFERENCE
      --testing-challenge=TESTING_CHALLENGE
      [--default-score-threshold=DEFAULT_SCORE_THRESHOLD
      : --action-score-thresholds=[ACTION_SCORE_THRESHOLDS,...]]])
    [--labels=[KEY=VALUE,...]] [--testing-score=TESTING_SCORE]
    [--waf-service=WAF_SERVICE : --waf-feature=WAF_FEATURE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | A human-readable name for the key. Typically a site or app name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--testing-score` | TESTING_SCORE |  | If set, all assessments for this key will return this score. Must be between 0 (likely not legitimate) and 1 (likely legitimate) inclusive. |


**Examples:**
```bash
To create a new reCAPTCHA key for websites showing no CAPTCHA challenge,
run:

    $ gcloud recaptcha keys create --display-name=test-key-name --web \
        --allow-all-domains --integration-type=score
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/create)

---
### `gcloud recaptcha keys delete`

Delete one or more reCAPTCHA Keys

Delete one or more reCAPTCHA Keys from a given cloud project.

**Synopsis:**
```
gcloud recaptcha keys delete KEY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA key to delete. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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
```

**Examples:**
```bash
To delete a reCAPTCHA key, run:

    $ gcloud recaptcha keys delete test-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/delete)

---
### `gcloud recaptcha keys describe`

Describe reCAPTCHA Key

Get the details of a reCAPTCHA Key.

**Synopsis:**
```
gcloud recaptcha keys describe KEY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA key to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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
```

**Examples:**
```bash
To get details on a reCAPTCHA key, run:

    $ gcloud recaptcha keys describe test-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/describe)

---
### `gcloud recaptcha keys list`

List reCAPTCHA Keys

List all of the reCAPTCHA Keys that exist in a given project.

**Synopsis:**
```
gcloud recaptcha keys list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the reCAPTCHA keys existing for your project, run:

    $ gcloud recaptcha keys list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/list)

---
### `gcloud recaptcha keys list-ip-overrides`

List IP overrides for a key

List IP overrides for a key.

**Synopsis:**
```
gcloud recaptcha keys list-ip-overrides KEY [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA key for which to list the IP overrides. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
```

**Examples:**
```bash
$ gcloud recaptcha keys list-ip-overrides test-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/list-ip-overrides)

---
### `gcloud recaptcha keys migrate`

Migrate a key to reCAPTCHA Enterprise

Migrate a key from reCAPTCHA to reCAPTCHA Enterprise.

**Synopsis:**
```
gcloud recaptcha keys migrate KEY [--skip-billing-check]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA key to migrate. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--skip-billing-check` |  |  | If true, skips the billing check. If your usage of reCAPTCHA is under the free quota, you can safely skip the billing check. |


**Examples:**
```bash
To migrate a key from reCAPTCHA to reCAPTCHA Enterprise, run:

    $ gcloud recaptcha keys migrate test-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/migrate)

---
### `gcloud recaptcha keys remove-ip-override`

Remove an IP override from a key

Remove an IP override from a key.

**Synopsis:**
```
gcloud recaptcha keys remove-ip-override KEY --ip=IP --override=OVERRIDE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA key from which to remove the IP override.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

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
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--ip` | IP |  | IP address to override for the key. |
| `--override` | one of: allow, override-type-unspecified |  | If set to allow, the IP address/CIDR range will be removed from the allowlisted IPs. OVERRIDE must be one of: allow, override-type-unspecified. |


**Examples:**
```bash
$ gcloud recaptcha keys remove-ip-override test-key --ip=1.2.3.4 \
    --override=allow
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/remove-ip-override)

---
### `gcloud recaptcha keys update`

Update a Key

Update a reCAPTCHA Key.

**Synopsis:**
```
gcloud recaptcha keys update KEY [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]]
    [--express | --android (--allow-all-package-names
      | --package-names=[PACKAGE_NAMES,...])
      | [--ios : --allow-all-bundle-ids | --bundle-ids=[BUNDLE_IDS,...]
      --key-id=KEY_ID --private-key-file=PATH_TO_FILE --team-id=TEAM_ID]
      | [--web : --allow-amp-traffic
      --security-preference=SECURITY_PREFERENCE
      --action-score-thresholds=[ACTION_SCORE_THRESHOLDS,...]
      --default-score-threshold=DEFAULT_SCORE_THRESHOLD --allow-all-domains
      | --domains=[DOMAINS,...]]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Key resource - The reCAPTCHA Key to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

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
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | DISPLAY_NAME |  | A human-readable name for the key. Typically a site or app name. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. |


**Examples:**
```bash
To update the information of a reCAPTCHA key, run:

    $ gcloud recaptcha keys update test-key --labels="foo=bar" --web \
        --domains=test.com.mx
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/keys/update)

---