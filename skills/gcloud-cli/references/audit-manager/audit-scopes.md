# gcloud audit-manager audit-scopes

command group for Audit Manager Audit Scopes

### `gcloud audit-manager audit-scopes generate`

Generate Audit Scope

Generate a new Audit Scope.

**Synopsis:**
```
gcloud audit-manager audit-scopes generate
    --compliance-framework=COMPLIANCE_FRAMEWORK --location=LOCATION
    --output-file-name=OUTPUT_FILE_NAME --report-format=REPORT_FORMAT
    (--folder=FOLDER | --project=PROJECT)
    [--output-directory=OUTPUT_DIRECTORY] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--compliance-framework` | COMPLIANCE_FRAMEWORK |  | Compliance Framework against which the Report must be generated. Eg: FEDRAMP_MODERATE |
| `--location` | LOCATION |  | The location where the scope should be generated. |
| `--output-file-name` | OUTPUT_FILE_NAME |  | The name by while scope report should be created . |
| `--report-format` | REPORT_FORMAT |  | The format in which the audit scope report should be created. REPORT_FORMAT must be (only one value is supported): odf. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--output-directory` | OUTPUT_DIRECTORY |  | The directory path where the scope report should be created . |


**Examples:**
```bash
To generate an Audit Scope in the us-central1 region, for a project with ID
123 for compliance framework fedramp_moderate in odf format, run:

    $ gcloud audit-manager audit-scopes generate --project="123" \
        --location="us-central1" \
        --compliance-framework="fedramp_moderate" \
        --report-format="odf" --output-directory="scopes/currentyear" \
        --output-file-name="auditreport"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/audit-manager/audit-scopes/generate)

---