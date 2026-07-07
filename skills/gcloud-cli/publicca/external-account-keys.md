# gcloud publicca external-account-keys

create ACME external account binding keys

### `gcloud publicca external-account-keys create`

Create a new external account key

**Synopsis:**
```
gcloud publicca external-account-keys create
    [--key-output-file=KEY_OUTPUT_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--key-output-file` | KEY_OUTPUT_FILE |  | The path where the generated external account key is written. |


**Examples:**
```bash
To create an external account key:

    $ gcloud publicca external-account-keys create

To create an external account key and save it to a file:

    $ gcloud publicca external-account-keys create \
      --key-output-file=./external_account_key.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/publicca/external-account-keys/create)

---