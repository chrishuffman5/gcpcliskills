# gcloud spanner rows

manage the rows in Cloud Spanner databases

### `gcloud spanner rows delete`

Delete a row in a Cloud Spanner database

**Synopsis:**
```
gcloud spanner rows delete --keys=[KEY,...] --table=TABLE
    (--database=DATABASE : --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--keys` | [KEY,...] |  | The primary key values of the row to delete. |
| `--table` | TABLE |  | The Cloud Spanner table name. |


**Examples:**
```bash
To delete a row with primary keys of SingerId=1,SingName=abc in table
Singers under my-database and my-instance, run:

    $ gcloud spanner rows delete --table=Singers \
      --database=my-database --instance=my-instance --keys=1,abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/rows/delete)

---
### `gcloud spanner rows insert`

Insert a row in a Cloud Spanner database

**Synopsis:**
```
gcloud spanner rows insert --data=[COLUMN_NAME=VALUE,...] --table=TABLE
    (--database=DATABASE : --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data` | [COLUMN_NAME=VALUE,...] |  | The column names and values for the row being added. For complicated input values, such as arrays, use the --flags-file flag. See $ gcloud topic flags-file for more information. |
| `--table` | TABLE |  | The Cloud Spanner table name. |


**Examples:**
```bash
To insert a row with SingerId=1,SingName=abc in table Singers under
my-database and my-instance, run:

    $ gcloud spanner rows insert --table=Singers \
        --database=my-database --instance=my-instance \
        --data=SingerId=1,SingerName=abc

    $ gcloud spanner rows insert --table=Singers \
        --database=my-database --instance=my-instance \
        --flags-file=path/to/file.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/rows/insert)

---
### `gcloud spanner rows update`

Update a row in a Cloud Spanner database

**Synopsis:**
```
gcloud spanner rows update --data=[COLUMN_NAME=VALUE,...] --table=TABLE
    (--database=DATABASE : --instance=INSTANCE) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--data` | [COLUMN_NAME=VALUE,...] |  | The column names and values for the row being updated. For complicated input values, such as arrays, use the --flags-file flag. See $ gcloud topic flags-file for more information. |
| `--table` | TABLE |  | The Cloud Spanner table name. |


**Examples:**
```bash
To update a row with SingerId=1,SingName=abc in table Singers under
my-database and my-instance, run:

    $ gcloud spanner rows update --table=Singers \
        --database=my-database --instance=my-instance \
        --data=SingerId=1,SingerName=abc

    $ gcloud spanner rows update --table=Singers \
        --database=my-database --instance=my-instance \
        --flags-file=path/to/file.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/rows/update)

---