# gcloud container (top-level commands)

### `gcloud container get-server-config`

Get Kubernetes Engine server config

Get Kubernetes Engine server config.

**Synopsis:**
```
gcloud container get-server-config
    [--location=LOCATION | --region=REGION | --zone=ZONE, -z ZONE]
    [--filter=EXPRESSION] [--limit=LIMIT] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[At most one of these can be specified:]_ Compute zone or region (e.g. us-central1-a or us-central1) for the cluster. Overrides the default compute/region or compute/zone value for this command invocation. Prefer using this flag over the --region or --zone flags. |
| `--region` | REGION |  | _[At most one of these can be specified:]_ Compute region (e.g. us-central1) for a regional cluster. Overrides the default compute/region property value for this command invocation. |
| `--zone` | ZONE, -z ZONE |  | _[At most one of these can be specified:]_ Compute zone (e.g. us-central1-a) for a zonal cluster. Overrides the default compute/zone property value for this command invocation. |


**Examples:**
```bash
To get the Kubernetes Engine server configuration, run:

    $ gcloud container get-server-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/get-server-config)

---