# gcloud artifacts rules

manage Artifact Registry rules

### `gcloud artifacts rules create`

Create an Artifact Registry rule

Create a new Artifact Registry rule.

This command can fail for the following reasons:
  o A rule with the same name already exists.
  o The active account does not have permission to create repositories.
  o A rule with given package already exists.

**Synopsis:**
```
gcloud artifacts rules create
    (RULE : --location=LOCATION --repository=REPOSITORY) --action=ACTION
    [--condition=CONDITION] [--operation=OPERATION; default="DOWNLOAD"]
    [--package=PACKAGE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rule resource - The Artifact Registry rule to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument rule on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RULE
     ID of the rule or fully qualified identifier for the rule.

     To set the rule attribute:
     + provide the argument rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the rule. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the rule. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow, deny |  | The action the rule would make, can only be DENY or ALLOW. ACTION must be one of: allow, deny. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--condition` | CONDITION |  | The CEL expression for the rule. |
| `--operation` | OPERATION | DOWNLOAD | The operation the rule applies to. OPERATION must be (only one value is supported): download. |
| `--package` | PACKAGE |  | The package the rule applies to. Empty means the rule is set for the entire repository. |


**Examples:**
```bash
To create a rule with the name my-rule for package my-pkg with action deny
under the current project, repository, run:

    $ gcloud artifacts rules create my-rule --package=my-pkg \
        --action=deny
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/rules/create)

---
### `gcloud artifacts rules delete`

Delete an Artifact Registry rule

Delete an Artifact Registry rule.

This command can fail for the following reasons:
  o The specified rule does not exist.
  o The active account does not have permission to delete rules.

**Synopsis:**
```
gcloud artifacts rules delete
    (RULE : --location=LOCATION --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rule resource - The Artifact Registry rule to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument rule on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RULE
     ID of the rule or fully qualified identifier for the rule.

     To set the rule attribute:
     + provide the argument rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the rule. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the rule. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To delete a rule named my-rule under the current project, repository, and
location, run:

    $ gcloud artifacts rules delete my-repo
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/rules/delete)

---
### `gcloud artifacts rules describe`

Describe an Artifact Registry rule

Describe an Artifact Registry rule.

This command can fail for the following reasons:
  o The specified rule does not exist.
  o The active account does not have permission to view rules.

**Synopsis:**
```
gcloud artifacts rules describe
    (RULE : --location=LOCATION --repository=REPOSITORY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rule resource - The Artifact Registry rule to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument rule on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RULE
     ID of the rule or fully qualified identifier for the rule.

     To set the rule attribute:
     + provide the argument rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the rule. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the rule. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Examples:**
```bash
To describe a rule named my-rule under the current project, repository, and
location, run:

    $ gcloud artifacts rules describe my-rule
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/rules/describe)

---
### `gcloud artifacts rules list`

List Artifact Registry rules

List all Artifact Registry rules for the specified repository.

This command can fail for the following reasons:
  o The specified repository does not exist.
  o The active account does not have permission to list rules.

To specify the maximum number of rules to list, use the --limit flag.

**Synopsis:**
```
gcloud artifacts rules list [--location=LOCATION --repository=REPOSITORY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location of the repository. Overrides the default artifacts/location property value for this command invocation. To configure the default location, use the command: gcloud config set artifacts/location. To set the location attribute: + provide the argument --repository on the command line with a fully specified name; + set the property artifacts/repository with a fully specified name; + provide the argument --location on the command line; + set the property artifacts/location. |
| `--repository` | REPOSITORY |  | _[* set the property core/project.]_ ID of the repository or fully qualified identifier for the repository. To set the repository attribute: + provide the argument --repository on the command line; + set the property artifacts/repository. |


**Examples:**
```bash
The following command lists a maximum of five rules for repository my-repo:

    $ gcloud artifacts rules list --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/rules/list)

---
### `gcloud artifacts rules update`

Update an Artifact Registry rule

Update an Artifact Registry rule.

This command can fail for the following reasons:
  o The rule does not exist.
  o A rule with the same name already exists.
  o The active account does not have permission to create repositories.
  o A rule with given package already exists.

**Synopsis:**
```
gcloud artifacts rules update
    (RULE : --location=LOCATION --repository=REPOSITORY) [--action=ACTION]
    [--condition=CONDITION] [--operation=OPERATION] [--package=PACKAGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rule resource - The Artifact Registry rule to update. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument rule on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RULE
     ID of the rule or fully qualified identifier for the rule.

     To set the rule attribute:
     + provide the argument rule on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the rule. Overrides the default artifacts/location
     property value for this command invocation. To configure the default
     location, use the command: gcloud config set artifacts/location.

     To set the location attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property artifacts/location.

  --repository=REPOSITORY
     The repository associated with the rule. Overrides the default
     artifacts/repository property value for this command invocation. To
     configure the default repository, use the command: gcloud config set
     artifacts/repository.

     To set the repository attribute:
     + provide the argument rule on the command line with a fully
       specified name;
     + provide the argument --repository on the command line;
     + set the property artifacts/repository.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--action` | one of: allow, deny |  | The action the rule would make, can only be DENY or ALLOW. ACTION must be one of: allow, deny. |
| `--condition` | CONDITION |  | The CEL expression for the rule. |
| `--operation` | OPERATION |  | The operation the rule applies to. OPERATION must be (only one value is supported): download. |
| `--package` | PACKAGE |  | The package the rule applies to. |


**Examples:**
```bash
To create a rule with the name my-rule for package my-pkg with action deny
under the current project, repository, run:

    $ gcloud artifacts rules update my-rule --package=my-pkg \
        --action=deny
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/rules/update)

---