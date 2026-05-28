# gcloud pam (top-level commands)

### `gcloud pam check-onboarding-status`

Check Privileged Access Manager onboarding status for a resource

Check Privileged Access Manager (PAM) onboarding status for a
project/organization/folder location.

**Synopsis:**
```
gcloud pam check-onboarding-status
    (--location=LOCATION : --folder=FOLDER --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--folder` | FOLDER |  | _[This must be specified.]_ The name of the folder To set the folder attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --folder on the command line. Must be specified for resource of type [privilegedaccessmanager.folders.locations]. |
| `--organization` | ORGANIZATION |  | _[This must be specified.]_ The name of the organization To set the organization attribute: + provide the argument --location on the command line with a fully specified name; + provide the argument --organization on the command line. Must be specified for resource of type [privilegedaccessmanager.organizations.locations]. |


**Examples:**
```bash
The following command checks the PAM onboarding status for a project named
sample-project and in location global:

    $ gcloud pam check-onboarding-status --project=sample-project \
        --location=global

The following command checks the PAM onboarding status for a folder with ID
FOLDER_ID and in location global:

    $ gcloud pam check-onboarding-status --folder=FOLDER_ID \
        --location=global

The following command checks the PAM onboarding status for an organization
with ID ORGANIZATION_ID and in location global:

    $ gcloud pam check-onboarding-status \
        --organization=ORGANIZATION_ID --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pam/check-onboarding-status)

---