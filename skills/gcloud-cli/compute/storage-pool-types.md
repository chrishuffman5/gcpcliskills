# gcloud compute storage-pool-types

read storage pool types

### `gcloud compute storage-pool-types describe`

Describe a storage pool type

Describe a storage pool.

**Synopsis:**
```
gcloud compute storage-pool-types describe
    (STORAGE_POOL_TYPE : --zone=ZONE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Storage pool type resource - Name of the storage pool you want to inspect.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument storage_pool_type on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  STORAGE_POOL_TYPE
     ID of the storage pool type or fully qualified identifier for the
     storage pool type.

     To set the storage_pool_type attribute:
     + provide the argument storage_pool_type on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --zone=ZONE
     The name of the Google Compute Engine zone.

     To set the zone attribute:
     + provide the argument storage_pool_type on the command line with a
       fully specified name;
     + provide the argument --zone on the command line;
     + set the property compute/zone.
```

**Examples:**
```bash
To retrieve a single storage pool type and print its properties, run the
following command:

    $ gcloud compute storage-pool-types describe my-storage-pool
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pool-types/describe)

---
### `gcloud compute storage-pool-types list`

View storage pools types

View storage pools.

**Synopsis:**
```
gcloud compute storage-pool-types list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To display all storage pool types and their locations visible the project,
run the following command:

    $ gcloud compute storage-pool-types list

The --filter option can be used to filter down available options. To
display all available storage pool types in US-based zones, run the
following command:

    $ gcloud compute storage-pool-types list --filter="zone ~ us"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/compute/storage-pool-types/list)

---