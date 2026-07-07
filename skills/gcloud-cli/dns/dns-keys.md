# gcloud dns dns-keys

manage Cloud DNS DNSKEY records

### `gcloud dns dns-keys describe`

Show details about a DNS key resource

This command displays the details of a single DNS key resource.

**Synopsis:**
```
gcloud dns dns-keys describe KEY-ID --zone=ZONE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
KEY-ID
   The DNS key identifier.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | The name of the managed-zone the DNSKEY record belongs to |


**Examples:**
```bash
To show details about a DNS key resource with ID 3 in a managed zone
my_zone, run:

    $ gcloud dns dns-keys describe --zone=my_zone 3

To get the DS record corresponding for the DNSKEY record from the previous
example, run (the DNSKEY record must be for a key-signing key):

    $ gcloud dns dns-keys describe --zone=my_zone 3 \
        --format='value(ds_record())'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/dns-keys/describe)

---
### `gcloud dns dns-keys list`

List DNS key resources

List DNS key resources in a managed zone.

**Synopsis:**
```
gcloud dns dns-keys list --zone=ZONE [--filter=EXPRESSION] [--limit=LIMIT]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--zone` | ZONE |  | The name of the managed-zone you want to list DNSKEY records for. |


**Examples:**
```bash
To see the list of all DNS key resources for a managed zone my_zone, run:

    $ gcloud dns dns-keys list --zone=my_zone

To see the DS records for every key-signing DnsKey in a managed zone, run:

    $ gcloud dns dns-keys list --zone=my_zone \
        --filter='type=keySigning' --format='value(ds_record())'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/dns-keys/list)

---