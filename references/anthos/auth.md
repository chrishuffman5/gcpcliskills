# gcloud anthos auth

authenticate clusters using the Anthos client

### `gcloud anthos auth login`

Authenticate clusters using the Anthos client

Authenticate clusters using the Anthos client.

**Synopsis:**
```
gcloud anthos auth login [--no-browser] [--cluster=CLUSTER] [--dry-run]
    [--kubeconfig=KUBECONFIG] [--login-config=LOGIN_CONFIG]
    [--login-config-cert=LOGIN_CONFIG_CERT]
    [--remote-bootstrap=REMOTE_BOOTSTRAP] [--server=SERVER]
    [--set-preferred-auth] [--user=USER] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--no-browser` |  |  | Option to indicate login completion on a second device with browser.Used with server option. |
| `--cluster` | CLUSTER |  | Cluster to authenticate against. If no cluster is specified, the command will print a list of available options. |
| `--dry-run` |  |  | Print out the generated kubectl commands but do not execute them. |
| `--kubeconfig` | KUBECONFIG |  | Specifies the destination kubeconfig file where credentials will be stored. |
| `--login-config` | LOGIN_CONFIG |  | Specifies the configuration yaml file for login. Can be a file path or a URL. |
| `--login-config-cert` | LOGIN_CONFIG_CERT |  | Specifies the CA certificate file to be added to trusted pool for making HTTPS connections to a --login-config URL. |
| `--remote-bootstrap` | REMOTE_BOOTSTRAP |  | Option to complete login that was started using no-browser optionon a remote device that does not have a browser. |
| `--server` | SERVER |  | Specifies the URL of API server of the cluster to authenticate against. |
| `--set-preferred-auth` |  |  | If set, forces update of preferred authentication for given cluster |
| `--user` | USER |  | If configuring multiple user accounts in the same kubecconfig file, you can specify a user to differentiate between them. |


**Examples:**
```bash
To add credentials to default kubeconfig file:

    $ gcloud anthos auth login --cluster=testcluster \
      --login-config=kubectl-anthos-config.yaml

To add credentials to custom kubeconfig file:

    $ gcloud anthos auth login --cluster=testcluster \
      --login-config=kubectl-anthos-config.yaml \
      --kubeconfig=my.kubeconfig

To generate the commands without executing them:

    $ gcloud anthos auth login --cluster=testcluster \
      --login-config=kubectl-anthos-config.yaml --dry-run

To add credentials to default kubeconfig file using server side login:

    $ gcloud anthos auth login --cluster=testcluster \
      --server=<server-url>

To add credentials to custom kubeconfig file using server side login:

    $ gcloud anthos auth login --cluster=testcluster \
      --server=<server-url> --kubeconfig=my.kubeconfig

To add credentials to custom kubeconfig file with server side login using a
remote-device for login:

    $ gcloud anthos auth login --cluster=testcluster \
      --server=<server-url> --kubeconfig=my.kubeconfig --no-browser
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/anthos/auth/login)

---