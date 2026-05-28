# gcloud datastore operations

manage Long Running Operations for Cloud Datastore

### `gcloud datastore operations cancel`

Cancel a currently-running Cloud Datastore admin operation

Cancel a currently-running Cloud Datastore admin operation.

**Synopsis:**
```
gcloud datastore operations cancel NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The unique name of the Operation to cancel, formatted as either the
   full or relative resource path:

       projects/my-app-id/operations/foo

   or:

       foo
```

**Examples:**
```bash
To cancel the currently-running operation with id exampleId, run:

    $ gcloud datastore operations cancel exampleId

or

    $ gcloud datastore operations cancel \
        projects/your-project-id/operations/exampleId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/operations/cancel)

---
### `gcloud datastore operations delete`

Delete a completed Cloud Datastore admin operation

Delete a completed Cloud Datastore admin operation.

**Synopsis:**
```
gcloud datastore operations delete NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The unique name of the Operation to delete, formatted as either the
   full or relative resource path:

       projects/my-app-id/operations/foo

   or:

       foo
```

**Examples:**
```bash
To delete the completed operation with id exampleId, run:

    $ gcloud datastore operations delete exampleId

or

    $ gcloud datastore operations delete \
        projects/your-project-id/operations/exampleId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/operations/delete)

---
### `gcloud datastore operations describe`

Retrieves information about a Cloud Datastore admin operation

Retrieves information about a Cloud Datastore admin operation.

**Synopsis:**
```
gcloud datastore operations describe NAME [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   The unique name of the Operation to retrieve, formatted as either the
   full or relative resource path:

       projects/my-app-id/operations/foo

   or:

       foo
```

**Examples:**
```bash
To see information on the operation with id exampleId, run:

    $ gcloud datastore operations describe exampleId

or

    $ gcloud datastore operations describe \
        projects/your-project-id/operations/exampleId
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/operations/describe)

---
### `gcloud datastore operations list`

List pending Cloud Datastore admin operations and their status

Filters are case-sensitive and have the following syntax:

    field = value [AND [field = value]] ...

where field is one of kind, namespace, type, or labels.[KEY], and [KEY] is
a label key. kind and namespace may be * to query for operations on all
kinds and/or all namespaces. type may be one of export_entities or
import_entities.

Only the logical AND operator is supported; space-separated items are
treated as having an implicit AND operator.

**Synopsis:**
```
gcloud datastore operations list [--filter=EXPRESSION]
    [--limit=LIMIT; default=100] [--page-size=PAGE_SIZE; default=100]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To see the list of all operations, run:

    $ gcloud datastore operations list

To see the list of all export operations, run:

    $ gcloud datastore operations list --filter='type:export_entities'

To see the list of all export operations for kind 'MyKind', run:

    $ gcloud datastore operations list \
        --filter='type:export_entities AND kind:MyKind'

To see the list of all operations with particular labels, run:

    $ gcloud datastore operations list --filter='labels.run = daily'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/datastore/operations/list)

---