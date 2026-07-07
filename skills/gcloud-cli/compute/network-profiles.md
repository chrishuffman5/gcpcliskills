# gcloud compute network-profiles

read Compute Engine network profiles

### `gcloud compute network-profiles describe`

Describe a network profile

Describe a network profile.

**Synopsis:**
```
gcloud compute network-profiles describe NETWORK_PROFILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Network profile resource - Name of the network profile you want to
inspect. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument network_profile on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NETWORK_PROFILE
     ID of the network_profile or fully qualified identifier for the
     network_profile.

     To set the network_profile attribute:
     + provide the argument network_profile on the command line.
```

**Examples:**
```bash
To retrieve a single network profile and print its properties, run the
following command:        $ gcloud compute network-profiles describe my-network-profile
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-profiles/describe)

---
### `gcloud compute network-profiles list`

List network profiles

List network profiles.

**Synopsis:**
```
gcloud compute network-profiles list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists all network profiles:

    $ gcloud compute network-profiles list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/network-profiles/list)

---