# gcloud audit-manager audit-reports

command group for Audit Manager Audit Reports

### `gcloud audit-manager audit-reports generate`

Generate Audit Report

Generate a new Audit Report.

**Synopsis:**
```
gcloud audit-manager audit-reports generate
    --compliance-framework=COMPLIANCE_FRAMEWORK --gcs-uri=GCS_URI
    --location=LOCATION --report-format=REPORT_FORMAT
    (--folder=FOLDER | --project=PROJECT) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--compliance-framework` | COMPLIANCE_FRAMEWORK |  | Compliance Framework against which the Report must be generated. Eg: FEDRAMP_MODERATE |
| `--gcs-uri` | GCS_URI |  | Destination Cloud storage bucket where report and evidence must be uploaded. The Cloud storage bucket provided here must be selected among the buckets entered during the enrollment process. |
| `--location` | LOCATION |  | The location where the report should be generated. |
| `--report-format` | REPORT_FORMAT |  | The format in which the audit report should be created. REPORT_FORMAT must be (only one value is supported): odf. |


**Examples:**
```bash
To generate an Audit Report in the us-central1 region, for a project with
ID 123 for compliance framework fedramp_moderate in odf format and store it
in gs://testbucketauditmanager bucket, run:

    $ gcloud audit-manager audit-reports generate --project=123 \
        --location=us-central1 --compliance-framework=fedramp_moderate \
        --report-format=odf --gcs-uri=gs://testbucketauditmanager
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/audit-manager/audit-reports/generate)

---