# gcloud transfer (top-level commands)

### `gcloud transfer authorize`

Authorize an account for all Transfer Service features

Authorize a Google account for all Transfer Service features.

This command provides admin and owner rights for simplicity. If that's too
much authority for your use case, see custom setups here:
https://cloud.google.com/storage-transfer/docs/on-prem-set-up

**Synopsis:**
```
gcloud transfer authorize [--add-missing] [--creds-file=CREDS_FILE]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-missing` |  |  | Add IAM roles necessary to use all Transfer Service features to the specified account. By default, this command just prints missing roles. |
| `--creds-file` | CREDS_FILE |  | The path to the creds file for an account to authorize. The file should be in JSON format and contain a "type" and "client_email", which are automatically generated for most creds files downloaded from Google (e.g. service account tokens). If this flag is not present, the command authorizes the user currently logged into gcloud. |


**Examples:**
```bash
To see what Transfer Service IAM roles the account logged into gcloud may
be missing, run:

    $ gcloud transfer authorize

To add the missing IAM roles, run:

    $ gcloud transfer authorize --add-missing

To check a custom service account for missing roles, run:

    $ gcloud transfer authorize \
        --creds-file=path/to/service-account-key.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/transfer/authorize)

---