# gcloud domains (top-level commands)

### `gcloud domains list-user-verified`

Lists the user's verified domains

Lists the user's verified domains.

**Synopsis:**
```
gcloud domains list-user-verified [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list domains that have been verified by the current user, run:

    $ gcloud domains list-user-verified

Use the gcloud domains verify command to verify additional domains.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/list-user-verified)

---
### `gcloud domains verify`

Verifies a domain via an in-browser workflow

Verifies a domain via an in-browser workflow.

**Synopsis:**
```
gcloud domains verify DOMAIN [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DOMAIN
   The domain to be verified.
```

**Examples:**
```bash
To verify a domain for the current user, run:

    $ gcloud domains verify example.com

This will allow the domain to be used with App Engine through gcloud
domains app domain-mappings and across Google Cloud products.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/domains/verify)

---