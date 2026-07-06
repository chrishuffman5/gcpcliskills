# gcloud datalineage config

manage Data Lineage configurations

### `gcloud datalineage config describe`

Describe Data Lineage configuration

**Synopsis:**
```
gcloud datalineage config describe
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

At most one of `--folder` / `--organization` / `--project` can be specified.

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | Folder ID. |
| `--organization` | ORGANIZATION |  | Organization ID. |
| `--project` | PROJECT | current project | Project ID or number. If none of `--project`, `--folder`, or `--organization` are provided, the current project will be used. |

**Examples:**
```bash
# To describe the configuration for the current project, run:
gcloud datalineage config describe

# To describe the configuration for the project my-project, run:
gcloud datalineage config describe --project=my-project

# To describe the configuration for the folder 123456, run:
gcloud datalineage config describe --folder=123456

# To describe the configuration for the organization 789012, run:
gcloud datalineage config describe --organization=789012
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/config/describe)

---
### `gcloud datalineage config update`

Update Data Lineage configuration

**Synopsis:**
```
gcloud datalineage config update --config=CONFIG
    [--folder=FOLDER | --organization=ORGANIZATION | --project=PROJECT]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | Inline JSON/YAML config or path to a file containing it. |

**Optional flags:**

At most one of `--folder` / `--organization` / `--project` can be specified.

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER |  | Folder ID. |
| `--organization` | ORGANIZATION |  | Organization ID. |
| `--project` | PROJECT | current project | Project ID or number. If none of `--project`, `--folder`, or `--organization` are provided, the current project will be used. |

**Examples:**
```bash
# To update the configuration for the current project using a JSON file
# my_config.json, run:
gcloud datalineage config update --config=my_config.json

# To update the configuration for the project my-project using an inline
# JSON string, run:
gcloud datalineage config update --project=my-project --config='{"ingestion": {"rules":
[{"integrationSelector": {"integration": "BIGQUERY"},
"lineageEnablement": {"enabled": true}}]}}'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datalineage/config/update)

---
