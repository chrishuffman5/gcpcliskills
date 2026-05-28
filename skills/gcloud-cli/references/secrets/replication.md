# gcloud secrets replication

manage secret replication

### `gcloud secrets replication get`

Describe a secret's replication

**Synopsis:**
```
gcloud secrets replication get SECRET [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to describe. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Examples:**
```bash
To describe the replication of a secret named 'my-secret', run:

    $ gcloud secrets replication get my-secret
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/replication/get)

---
### `gcloud secrets replication set`

Set a secret's replication

Sets the replication policy for the given secret as defined in a JSON or
YAML file. The locations that a Secret is replicated to cannot be changed.

**Synopsis:**
```
gcloud secrets replication set SECRET
    --replication-policy-file=REPLICATION-POLICY-FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to update. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--replication-policy-file` | REPLICATION-POLICY-FILE |  | JSON or YAML file to use to read the replication policy. The file must conform to https://cloud.google.com/secret-manager/docs/reference/rest/v1/projects.secrets#replication.Set this to "-" to read from stdin. |


**Examples:**
```bash
To set the replication of a secret named 'my-secret' to the contents of
my-file.json, run:

    $ gcloud secrets replication set my-secret \
        --replication-policy-file=my-file.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/replication/set)

---
### `gcloud secrets replication update`

Update a secret replica's metadata

Update a secret replica's metadata (e.g. cmek policy). This command will
return an error if given a secret that does not exist or if given a
location that the given secret doesn't exist in.

The --remove-kms-key flag is only valid for Secrets that have an automatic
replication policy or exist in a single location. To remove keys from a
Secret with multiple user managed replicas, please use the set-replication
command.

**Synopsis:**
```
gcloud secrets replication update SECRET
    [--remove-cmek | --location=REPLICA-LOCATION --set-kms-key=SET-KMS-KEY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Secret resource - The secret to update. This represents a Cloud resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument SECRET on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SECRET
     ID of the secret or fully qualified identifier for the secret.

     To set the secret attribute:
     + provide the argument SECRET on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--remove-cmek` |  |  | _[At most one of these can be specified:]_ Remove customer managed encryption key so that future versions will be encrypted by a Google managed encryption key. |


**Examples:**
```bash
To remove CMEK from a secret called 'my-secret', run:

    $ gcloud secrets replication update my-secret --remove-cmek

To set the CMEK key on an automatic secret called my-secret to a specified
KMS key, run:

    $ gcloud secrets replication update my-secret \
        --set-kms-key=projects/my-project/locations/global/keyRings/\
    my-keyring/cryptoKeys/my-key

To set the CMEK key on a secret called my-secret to a specified KMS key in
a specified location in its replication, run:

    $ gcloud secrets replication update my-secret \
        --set-kms-key=projects/my-project/locations/us-central1/\
    keyRings/my-keyring/cryptoKeys/my-key --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/secrets/replication/update)

---