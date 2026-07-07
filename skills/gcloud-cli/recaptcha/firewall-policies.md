# gcloud recaptcha firewall-policies

managed reCAPTCHA Firewall Policies

### `gcloud recaptcha firewall-policies create`

Create a Firewall Policy

Create a reCAPTCHA Firewall Policy.

**Synopsis:**
```
gcloud recaptcha firewall-policies create [--actions=ACTIONS]
    [--condition=CONDITION] [--description=DESCRIPTION] [--path=PATH]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--actions` | ACTIONS |  | The actions that the caller should take regarding the user. There should be at most 1 terminal action. A terminal action is any action that forces a response, such as Allow, Block or Substitute. If it makes sense for it to happen multple times, such as SetHeader, the action is non-terminal. Examples: * Block and set the header with key foo to value bar + --actions=block,set_header=foo=bar * Substitute with path google.com and set two headers, one with key key1 to value value1 and one with key key2 to value value2 + --actions=substitute=google.com,set_header=key1=value1,set_header=key2=value2 |
| `--condition` | CONDITION |  | A CEL (Common Expression Language) conditional expression that specifies if this policy applies to an incoming user request. If this condition evaluates to true and the requested path matched the path pattern, the associated actions should be executed by the caller. The condition string is checked for CEL syntax correctness on creation. For more information, see the CEL spec: https://github.com/google/cel-spec and its language definition: https://github.com/google/cel-spec/blob/master/doc/langdef.md |
| `--description` | DESCRIPTION |  | A description of what this policy aims to achieve, for convenience purposes. The description can at most include 256 UTF-8 characters. |
| `--path` | PATH |  | The path for which this policy applies, specified as a glob pattern. For more information on glob, see the manual page: https://man7.org/linux/man-pages/man7/glob.7.html. |


**Examples:**
```bash
To create a new reCAPTCHA firewall policy covering the path "/login/" for
all requests with a reCAPTCHA Lite score of >= 0.5 to allow the requests
and set the header 'foo' to the value 'bar':

    $ gcloud recaptcha firewall-policies create --path='/login/*' \
        --condition='recaptcha.assessment_type == AssessmentType.LITE
    && recaptcha.score >= 0.5' --actions=allow,set_header=foo=bar
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/firewall-policies/create)

---
### `gcloud recaptcha firewall-policies delete`

Delete one or more reCAPTCHA Firewall Policies

Delete one or more reCAPTCHA Firewall Policies from a given cloud project.

**Synopsis:**
```
gcloud recaptcha firewall-policies delete FIREWALL_POLICY
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall policy resource - The reCAPTCHA firewall policy to delete. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument firewall_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIREWALL_POLICY
     ID of the firewall_policy or fully qualified identifier for the
     firewall_policy.

     To set the firewall_policy attribute:
     + provide the argument firewall_policy on the command line.
```

**Examples:**
```bash
To delete a reCAPTCHA firewall policies, run:

    $ gcloud recaptcha firewall-policies delete policy-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/firewall-policies/delete)

---
### `gcloud recaptcha firewall-policies describe`

Describe reCAPTCHA Firewall Policy

Get the details of a reCAPTCHA Firewall Policy.

**Synopsis:**
```
gcloud recaptcha firewall-policies describe FIREWALL_POLICY
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall policy resource - The reCAPTCHA firewall policy to describe. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument firewall_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIREWALL_POLICY
     ID of the firewall_policy or fully qualified identifier for the
     firewall_policy.

     To set the firewall_policy attribute:
     + provide the argument firewall_policy on the command line.
```

**Examples:**
```bash
To get details on a reCAPTCHA firewall policy, run:

    $ gcloud recaptcha firewall-policies describe policy-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/firewall-policies/describe)

---
### `gcloud recaptcha firewall-policies list`

List reCAPTCHA Firewall Policies

List all of the reCAPTCHA Firewall Policies that exist in a given project.

**Synopsis:**
```
gcloud recaptcha firewall-policies list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all the reCAPTCHA firewall policies existing for your project, run:

    $ gcloud recaptcha firewall-policies list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/firewall-policies/list)

---
### `gcloud recaptcha firewall-policies reorder`

Reorder all Firewall Policies

Reorder all reCAPTCHA Firewall Policies.

**Synopsis:**
```
gcloud recaptcha firewall-policies reorder --names=[NAMES,...]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--names` | [NAMES,...] |  | Names of all firewall policies in desired order. |


**Examples:**
```bash
To reorder the list of reCAPTCHA firewall policies, run:

    $ gcloud recaptcha firewall-policies reorder \
        --names=policy-name,policy-name,policy-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/firewall-policies/reorder)

---
### `gcloud recaptcha firewall-policies update`

Update a Firewall Policy

Update a reCAPTCHA Firewall Policy.

**Synopsis:**
```
gcloud recaptcha firewall-policies update FIREWALL_POLICY
    [--actions=ACTIONS] [--condition=CONDITION] [--description=DESCRIPTION]
    [--path=PATH] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Firewall policy resource - The reCAPTCHA firewall policy to update. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument firewall_policy on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  FIREWALL_POLICY
     ID of the firewall_policy or fully qualified identifier for the
     firewall_policy.

     To set the firewall_policy attribute:
     + provide the argument firewall_policy on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--actions` | ACTIONS |  | The actions that the caller should take regarding the user. There should be at most 1 terminal action. A terminal action is any action that forces a response, such as Allow, Block or Substitute. If it makes sense for it to happen multple times, such as SetHeader, the action is non-terminal. Examples: * Block and set the header with key foo to value bar + --actions=block,set_header=foo=bar * Substitute with path google.com and set two headers, one with key key1 to value value1 and one with key key2 to value value2 + --actions=substitute=google.com,set_header=key1=value1,set_header=key2=value2 |
| `--condition` | CONDITION |  | A CEL (Common Expression Language) conditional expression that specifies if this policy applies to an incoming user request. If this condition evaluates to true and the requested path matched the path pattern, the associated actions should be executed by the caller. The condition string is checked for CEL syntax correctness on creation. For more information, see the CEL spec: https://github.com/google/cel-spec and its language definition: https://github.com/google/cel-spec/blob/master/doc/langdef.md |
| `--description` | DESCRIPTION |  | A description of what this policy aims to achieve, for convenience purposes. The description can at most include 256 UTF-8 characters. |
| `--path` | PATH |  | The path for which this policy applies, specified as a glob pattern. For more information on glob, see the manual page: https://man7.org/linux/man-pages/man7/glob.7.html. |


**Examples:**
```bash
To update the information of a reCAPTCHA firewall policy, run:

    $ gcloud recaptcha firewall-policies update policy-id \
        --description='updated description' --actions=block
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/recaptcha/firewall-policies/update)

---