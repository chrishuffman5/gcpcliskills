# gcloud compute diagnose

debugging tools for Compute Engine virtual machine instances

### `gcloud compute diagnose export-logs`

Triggers instance to gather logs and upload them to a Cloud Storage Bucket

Gathers logs from a running Compute Engine VM and exports them to a Google
Cloud Storage Bucket. Outputs a path to the logs within the Bucket.

**Synopsis:**
```
gcloud compute diagnose export-logs INSTANCE_NAME
    [--collect-process-traces] [--zone=ZONE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INSTANCE_NAME
   Name of the instance to operate on. For details on valid instance
   names, refer to the criteria documented under the field 'name' at:
   https://cloud.google.com/compute/docs/reference/rest/v1/instances
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--collect-process-traces` |  |  | Collect a 10 minute trace of the running system. On Windows, this utilizes Windows Performance Recorder. It records CPU, disk, file, and network activity during that time. |
| `--zone` | ZONE |  | Zone of the instance to operate on. If not specified, you might be prompted to select a zone (interactive mode only). gcloud attempts to identify the appropriate zone by searching for resources in your currently active project. If the zone cannot be determined, gcloud prompts you for a selection with all available Google Cloud Platform zones. To avoid prompting when this flag is omitted, the user can set the compute/zone property: $ gcloud config set compute/zone ZONE A list of zones can be fetched by running: $ gcloud compute zones list To unset the property, run: $ gcloud config unset compute/zone Alternatively, the zone can be stored in the environment variable CLOUDSDK_COMPUTE_ZONE. |


**Examples:**
```bash
To export logs and upload them to a Cloud Storage Bucket, run:

    $ gcloud compute diagnose export-logs example-instance \
        --zone=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/diagnose/export-logs)

---
### `gcloud compute diagnose routes`

Routes to/from Compute Engine virtual machine instances

Routes to/from Compute Engine virtual machine instances.

NOTE: The name filtering will cycle through all the VMs in the project.
Depending on the size of the project, this could be a considerable amount
of work.

If that is the case, use the --regexp flag to filter down the amount of VMs
considered in the filtering.

**Synopsis:**
```
gcloud compute diagnose routes [NAME ...] [--container=CONTAINER]
    [--dry-run] [--external-route-ip=EXTERNAL_ROUTE_IP]
    [--force-key-file-overwrite] [--plain] [--regexp=REGEXP, -r REGEXP]
    [--reverse-traceroute] [--ssh-flag=SSH_FLAG]
    [--ssh-key-file=SSH_KEY_FILE]
    [--strict-host-key-checking=STRICT_HOST_KEY_CHECKING] [--user=USER]
    [--zones=ZONE,[ZONE,...]]
    [--ssh-key-expiration=SSH_KEY_EXPIRATION
      | --ssh-key-expire-after=SSH_KEY_EXPIRE_AFTER] [GCLOUD_WIDE_FLAG ...]
    [-- TRACEROUTE_ARGS ...]
```

**Positional arguments:**
```
[NAME ...]
   If provided, show details for the specified names and/or URIs of
   resources.

[-- TRACEROUTE_ARGS ...]
   Flags and positionals passed to the underlying traceroute call.

   The '--' argument must be specified between gcloud specific args on the
   left and TRACEROUTE_ARGS on the right. Example:

       $ gcloud compute diagnose routes example-instance -- -w 0.5 -q 5 42
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--container` | CONTAINER |  | The name or ID of a container inside of the virtual machine instance to connect to. This only applies to virtual machines that are using a Container-Optimized OS virtual machine image. For more information, see https://cloud.google.com/compute/docs/containers |
| `--dry-run` |  |  | Print the equivalent scp/ssh command that would be run to stdout, instead of executing it. |
| `--external-route-ip` | EXTERNAL_ROUTE_IP |  | For reverse traceroute, this will be the ip given to the VM instance to traceroute to. This will override all obtained ips. |
| `--force-key-file-overwrite` |  |  | If enabled, the gcloud command-line tool will regenerate and overwrite the files associated with a broken SSH key without asking for confirmation in both interactive and non-interactive environments. If disabled, the files associated with a broken SSH key will not be regenerated and will fail in both interactive and non-interactive environments. |
| `--plain` |  |  | Suppress the automatic addition of ssh(1)/scp(1) flags. This flag is useful if you want to take care of authentication yourself or use specific ssh/scp features. |
| `--regexp` | REGEXP, -r REGEXP |  | Regular expression to filter the names of the results on. Any names that do not match the entire regular expression will be filtered out. |
| `--reverse-traceroute` |  |  | If enabled, will also run traceroute from the VM to the host |
| `--ssh-flag` | SSH_FLAG |  | Additional flags to be passed to ssh(1). It is recommended that flags be passed using an assignment operator and quotes. This flag will replace occurences of %USER% and %INSTANCE% with their dereferenced values. Example: $ gcloud compute diagnose routes example-instance \ --zone us-central1-a --ssh-flag="-vvv" \ --ssh-flag="-L 80:%INSTANCE%:80" is equivalent to passing the flags --vvv and -L 80:162.222.181.197:80 to ssh(1) if the external IP address of 'example-instance' is 162.222.181.197. |
| `--ssh-key-file` | SSH_KEY_FILE |  | The path to the SSH key file. By default, this is ~\.ssh\google_compute_engine. |
| `--strict-host-key-checking` | one of: yes, no, ask |  | Override the default behavior of StrictHostKeyChecking for the connection. By default, StrictHostKeyChecking is set to 'no' the first time you connect to an instance, and will be set to 'yes' for all subsequent connections. STRICT_HOST_KEY_CHECKING must be one of: yes, no, ask. |
| `--user` | USER |  | User for login to the selected VMs. If not specified, the default user will be used. |
| `--zones` | ZONE,[ZONE,...] |  | If provided, only resources from the given zones are queried. |


**Examples:**
```bash
To route to/from Compute Engine virtual machine instances, run:

    $ gcloud compute diagnose routes
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/diagnose/routes)

---