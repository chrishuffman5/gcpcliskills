# gcloud artifacts print-settings

print snippets to add to native tools settings files

### `gcloud artifacts print-settings gradle`

Print a snippet to add a repository to the Gradle build.gradle file

Print a snippet to add a repository to the Gradle build.gradle file.

**Synopsis:**
```
gcloud artifacts print-settings gradle [--json-key=JSON_KEY]
    [--location=LOCATION --repository=REPOSITORY] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-key` | JSON_KEY |  | Path to service account JSON key. If not specified, current active service account credentials or a placeholder for gcloud credentials is used. |


**Examples:**
```bash
To print a snippet for the repository set in the artifacts/repository
property in the default location:

    $ gcloud artifacts print-settings gradle

To print a snippet for repository my-repository in the default location:

    $ gcloud artifacts print-settings gradle --repository="my-repository"

To print a snippet using service account key:

    $ gcloud artifacts print-settings gradle --json-key=path/to/key.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/print-settings/gradle)

---
### `gcloud artifacts print-settings mvn`

Print a snippet to add a Maven repository to the pom.xml file

Print a snippet to add a Maven repository to the pom.xml file.

**Synopsis:**
```
gcloud artifacts print-settings mvn [--json-key=JSON_KEY]
    [--location=LOCATION --repository=REPOSITORY] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-key` | JSON_KEY |  | Path to service account JSON key. If not specified, current active service account credentials or a placeholder for gcloud credentials is used. |


**Examples:**
```bash
To print a snippet for the repository set in the artifacts/repository
property in the default location:

    $ gcloud artifacts print-settings mvn

To print a snippet for repository my-repository in the default location:

    $ gcloud artifacts print-settings mvn --repository="my-repository"

To print a snippet using service account key:

    $ gcloud artifacts print-settings mvn --json-key=path/to/key.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/print-settings/mvn)

---
### `gcloud artifacts print-settings npm`

Print credential settings to add to the .npmrc file

Print credential settings to add to the .npmrc file for connecting to an
npm repository.

**Synopsis:**
```
gcloud artifacts print-settings npm [--json-key=JSON_KEY] [--scope=SCOPE]
    [--location=LOCATION --repository=REPOSITORY] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-key` | JSON_KEY |  | Path to service account JSON key. If not specified, current active service account credentials or a placeholder for gcloud credentials is used. |
| `--scope` | SCOPE |  | The scope to associate with the Artifact Registry registry. If not specified, Artifact Registry is set as the default registry. |


**Examples:**
```bash
To print a snippet for the repository set in the artifacts/repository
property in the default location:

    $ gcloud artifacts print-settings npm

To print a snippet for repository my-repository in the default location:

    $ gcloud artifacts print-settings npm --repository="my-repository"

To print a snippet using service account key:

    $ gcloud artifacts print-settings npm --json-key=path/to/key.json

To print a snippet for the repository set in the artifacts/repository
property with scope @my-company:

    $ gcloud artifacts print-settings npm --scope=@my-company
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/print-settings/npm)

---
### `gcloud artifacts print-settings python`

Print credential settings to add to the .pypirc and pip.conf files

Print credential settings to add to the .pypirc and pip.conf files for
connecting to a Python package repository.

**Synopsis:**
```
gcloud artifacts print-settings python [--json-key=JSON_KEY]
    [--location=LOCATION --repository=REPOSITORY] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--json-key` | JSON_KEY |  | Path to service account JSON key. If not specified, output returns either credentials for an active service account or a placeholder for the current user account. |


**Examples:**
```bash
To print a snippet for the repository set in the artifacts/repository
property in the default location:

    $ gcloud artifacts print-settings python

To print a snippet for repository my-repository in the default location:

    $ gcloud artifacts print-settings python --repository="my-repository"

To print a snippet using service account key:

    $ gcloud artifacts print-settings python --json-key=path/to/key.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/print-settings/python)

---