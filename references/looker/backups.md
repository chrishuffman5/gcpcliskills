# gcloud looker backups

manage Looker instances

### `gcloud looker backups create`

Create a backup of a Looker instance

Create a backup of a Looker instance.

**Synopsis:**
```
gcloud looker backups create --instance=INSTANCE --region=REGION
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | ID of the instance or fully qualified identifier for the instance. To set the instance attribute: * provide the argument --instance on the command line. |
| `--region` | REGION |  | The name of the Looker region of the instance. Overrides the default looker/region property value for this command invocation. |


**Examples:**
```bash
To create a backup of an instance with the name my-looker-instance, in
region us-central1 run:

    $ gcloud looker backups create --instance='my-looker-instance' \
        --region='us-central1'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/backups/create)

---
### `gcloud looker backups delete`

Delete a backup of a Looker instance

Delete a backup of a Looker instance.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The backup does not exist.
  o The active account does not have permission to access the given
    instance.

**Synopsis:**
```
gcloud looker backups delete (BACKUP : --instance=INSTANCE --region=REGION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The instance of the backup to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Looker instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.

  --region=REGION
     The name of the Looker region of the backup. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a backup with ID c24ad631-ad83-42f0-9f98-41e2b493263e on instance
with name my-looker-instance, run:

    $ gcloud looker backups delete \
        c24ad631-ad83-42f0-9f98-41e2b493263e \
        --instance='my-looker-instance'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/backups/delete)

---
### `gcloud looker backups describe`

Show metadata of a backup for a Looker instance

Show metadata of a backup for a Looker instance.

Displays all metadata associated with a backup of a Looker instance given a
valid backup and instance name.

This command can fail for the following reasons:
  o The instance specified does not exist.
  o The backup specified does not exist.
  o The active account does not have permission to access the given
    instance and backups.

**Synopsis:**
```
gcloud looker backups describe
    (BACKUP : --instance=INSTANCE --region=REGION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Backup resource - The instance of the backup to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument backup on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BACKUP
     ID of the backup or fully qualified identifier for the backup.

     To set the backup attribute:
     + provide the argument backup on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The name of the Looker instance.

     To set the instance attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --instance on the command line.

  --region=REGION
     The name of the Looker region of the backup. Overrides the default
     looker/region property value for this command invocation.

     To set the region attribute:
     + provide the argument backup on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + set the property looker/region.
```

**Examples:**
```bash
To display the metadata for a backup with id of
c24ad631-ad83-42f0-9f98-41e2b493263e on instance with name
my-looker-instance, and in the region us-central1, run:

    $ gcloud looker backups describe \
        c24ad631-ad83-42f0-9f98-41e2b493263e \
        --instance='my-looker-instance' --region='us-central1'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/backups/describe)

---
### `gcloud looker backups list`

List backups of a Looker instance

List all backups of a Looker instance under the specified project and
region.

To specify the maximum number of backups to list, use the --limit flag.

**Synopsis:**
```
gcloud looker backups list (--instance=INSTANCE : --region=REGION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--instance` | INSTANCE |  | _[This must be specified.]_ ID of the instance or fully qualified identifier for the instance. To set the instance attribute: + provide the argument --instance on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--region` | REGION |  | _[This must be specified.]_ The name of the Looker region of the instance. Overrides the default looker/region property value for this command invocation. To set the region attribute: + provide the argument --instance on the command line with a fully specified name; + provide the argument --region on the command line; + set the property looker/region. |


**Examples:**
```bash
To list up to five backups, of a Looker instance named my-looker-instance
in the region us-central1 run:

    $ gcloud looker backups list --instance='my-looker-instance' \
        --limit=5 --region='us-central1'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/looker/backups/list)

---