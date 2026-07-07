# gcloud bigtable materialized-views

manage Bigtable materialized views

### `gcloud bigtable materialized-views create`

Create a new Bigtable materialized view

Create a new Bigtable materialized view.

**Synopsis:**
```
gcloud bigtable materialized-views create
    (MATERIALIZED_VIEW : --instance=INSTANCE) --query=QUERY [--async]
    [--deletion-protection=DELETION_PROTECTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Materialized view resource - The materialized view to create. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument materialized_view on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MATERIALIZED_VIEW
     ID of the materialized view or fully qualified identifier for the
     materialized view.

     To set the name attribute:
     + provide the argument materialized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the materialized view.

     To set the instance attribute:
     + provide the argument materialized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--query` | QUERY |  | The query of the view. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--deletion-protection` | DELETION_PROTECTION |  | Whether the view is protected from deletion. |


**Examples:**
```bash
To create a materialized view, run:        $ gcloud bigtable materialized-views create \
        my-materialized-view-id --instance=my-instance-id \
        --query="SELECT my-column-family FROM my-table \
    --deletion-protection=false"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/materialized-views/create)

---
### `gcloud bigtable materialized-views delete`

Delete a Bigtable materialized view

Delete a Bigtable materialized view.

**Synopsis:**
```
gcloud bigtable materialized-views delete
    (MATERIALIZED_VIEW : --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Materialized view resource - The materialized view to delete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument materialized_view on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MATERIALIZED_VIEW
     ID of the materialized view or fully qualified identifier for the
     materialized view.

     To set the name attribute:
     + provide the argument materialized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the materialized view.

     To set the instance attribute:
     + provide the argument materialized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.
```

**Examples:**
```bash
To delete a materialized view, run:

    $ gcloud bigtable materialized-views delete \
        my-materialized-view-id --instance=my-instance-id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/materialized-views/delete)

---
### `gcloud bigtable materialized-views describe`

Describe an existing Bigtable materialized view

Describe an existing Bigtable materialized view.

**Synopsis:**
```
gcloud bigtable materialized-views describe
    (MATERIALIZED_VIEW : --instance=INSTANCE)
    [--view=VIEW; default="schema"] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Materialized view resource - The materialized view to describe. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument materialized_view on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MATERIALIZED_VIEW
     ID of the materialized view or fully qualified identifier for the
     materialized view.

     To set the name attribute:
     + provide the argument materialized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the materialized view.

     To set the instance attribute:
     + provide the argument materialized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: full, replication, schema | schema | Specifies what type of information to return about the view. VIEW must be one of: full, replication, schema. |


**Examples:**
```bash
To get back information related to a view's schema (for example,
description), run:

    $ gcloud bigtable materialized-views describe \
        my-materialized-view-id --instance=my-instance-id --view=schema

or (because schema is the default view) simply:

    $ gcloud bigtable materialized-views describe \
        my-materialized-view-id --instance=my-instance-id

To get back information related to the view's replication state, run:

    $ gcloud bigtable materialized-views describe \
        my-materialized-view-id --instance=my-instance-id \
        --view=replication

To get back all information for the view, run:

    $ gcloud bigtable materialized-views describe \
        my-materialized-view-id --instance=my-instance-id --view=full
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/materialized-views/describe)

---
### `gcloud bigtable materialized-views list`

List existing Bigtable materialized views

List existing Bigtable materialized views.

**Synopsis:**
```
gcloud bigtable materialized-views list --instance=INSTANCE
    [--view=VIEW; default="schema"] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[This must be specified.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--view` | one of: full, replication, schema | schema | Specifies what type of information to return about the view. VIEW must be one of: full, replication, schema. |


**Examples:**
```bash
To list all materialized views for an instance, run:

    $ gcloud bigtable materialized-views list --instance=my-instance-id

You may also specify what information to return by supplying the --view
flag, such as:

    $ gcloud bigtable materialized-views list \
        --instance=my-instance-id --view=schema

Currently, only the schema view is supported for this command. This is the
default view, and it returns information about the schemas of your
materialized views.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/materialized-views/list)

---
### `gcloud bigtable materialized-views update`

Update a Bigtable materialized view

Update a Bigtable materialized view.

**Synopsis:**
```
gcloud bigtable materialized-views update
    (MATERIALIZED_VIEW : --instance=INSTANCE)
    --deletion-protection=DELETION_PROTECTION [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Materialized view resource - The materialized view to update. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument materialized_view on the command line with a
   fully specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MATERIALIZED_VIEW
     ID of the materialized view or fully qualified identifier for the
     materialized view.

     To set the name attribute:
     + provide the argument materialized_view on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     Bigtable instance for the materialized view.

     To set the instance attribute:
     + provide the argument materialized_view on the command line with a
       fully specified name;
     + provide the argument --instance on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--deletion-protection` | DELETION_PROTECTION |  | Whether the view is protected from deletion. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To update a materialized view, run:

    $ gcloud bigtable materialized-views update \
        my-materialized-view-id --instance=my-instance-id \
        --deletion-protection=true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bigtable/materialized-views/update)

---