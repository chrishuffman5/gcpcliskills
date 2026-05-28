# gcloud anthos (top-level commands)

### `gcloud anthos create-login-config`

Generates a login configuration file

Generates the file containing configuration information developers will use
to authenticate to an AWS Anthos cluster.

**Synopsis:**
```
gcloud anthos create-login-config --kubeconfig=KUBECONFIG
    [--merge-from=MERGE_FROM] [--output=OUTPUT] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--kubeconfig` | KUBECONFIG |  | Specifies the input kubeconfig file to access user cluster for login configuration data. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--merge-from` | MERGE_FROM |  | Specifies the file path of an existing login configuration file to merge with. |
| `--output` | OUTPUT |  | Destination to write login configuration file. Defaults to "kubectl-anthos-config.yaml". |


**Examples:**
```bash
To generate the default login config file (kubectl-anthos-config.yaml)
using the kubeconfig file 'my-kube-config.yaml':

    $ gcloud anthos create-login-config \
        --kubeconfig 'my-kube-config.yaml'

To generate a config named 'myconfg.yaml' the --kubeconfig file
'my-kube-config.yaml':

    $ gcloud anthos create-login-config \
        --kubeconfig 'my-kube-config.yaml' --output 'myconfg.yaml'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/create-login-config)

---