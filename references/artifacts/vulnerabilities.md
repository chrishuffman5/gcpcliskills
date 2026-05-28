# gcloud artifacts vulnerabilities

manage Artifact Vulnerabilities

### `gcloud artifacts vulnerabilities list`

Command for listing vulnerabilities. To see all fields, use --format=json

Command for listing vulnerabilities. To see all fields, use --format=json.

**Synopsis:**
```
gcloud artifacts vulnerabilities list URI [--location=LOCATION]
    [--occurrence-filter=OCCURRENCE_FILTER] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URI
   An URI identifying a container image or package in Artifact Registry or
   Google Cloud Registry.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | If specified, all requests to Artifact Analysis for occurrences will go to location specified |
| `--occurrence-filter` | OCCURRENCE_FILTER |  | A filter for the occurrences which will be summarized. See link for officially supported filters: https://cloud.google.com/container-analysis/docs/os-scanning-automatically#filtering |


**Examples:**
```bash
To list vulnerabilities for an artifact, run:

    $ gcloud artifacts vulnerabilities list \
        us-east1-docker.pkg.dev/project123/repository123/\
    someimage@sha256:49765698074d6d7baa82f
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/vulnerabilities/list)

---
### `gcloud artifacts vulnerabilities load-vex`

Load VEX data from a CSAF file into Artifact Analysis

Command loads VEX data from a Common Security Advisory Framework (CSAF)
file into Artifact Analysis as VulnerabilityAssessment Notes. VEX data
tells Artifact Analysis whether vulnerabilities are relevant and how.

**Synopsis:**
```
gcloud artifacts vulnerabilities load-vex --source=SOURCE --uri=URI
    [--location=LOCATION] [--project=PROJECT] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | The path of the VEX file. |
| `--uri` | URI |  | The path of the artifact in Artifact Registry. A 'gcr.io' image can also be used if redirection is enabled in Artifact Registry. Make sure 'artifactregistry.projectsettings.get' permission is granted to the current gcloud user to verify the redirection status. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | If specified, all requests to Artifact Analysis for occurrences will go to location specified |
| `--project` | PROJECT |  | The parent project to load security advisory into. |


**Examples:**
```bash
To load a CSAF security advisory file given an artifact in Artifact
Registry and the file on disk, run:

    $ gcloud artifacts vulnerabilities load-vex \
    --uri=us-east1-docker.pkg.dev/project123/repository123/\
    someimage@sha256:49765698074d6d7baa82f --source=/path/to/vex/file

To load a CSAF security advisory file given an artifact with a tag and a
file on disk, run:

    $ gcloud artifacts vulnerabilities load-vex \
    --uri=us-east1-docker.pkg.dev/project123/repository123/\
    someimage:latest --source=/path/to/vex/file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/artifacts/vulnerabilities/load-vex)

---