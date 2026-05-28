# gcloud firestore user-creds

manage the user creds for a Cloud Firestore Database

### `gcloud firestore user-creds create`

Creates a Cloud Firestore user creds

**Synopsis:**
```
gcloud firestore user-creds create USER_CREDS --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USER_CREDS
   The user creds to operate on.

   For example, to operate on user creds creds-name-1:

       $ gcloud firestore user-creds create creds-name-1
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds create --database='foo' |


**Examples:**
```bash
To create a user creds called test-user-creds-id under database testdb.

    $ gcloud firestore user-creds create test-user-creds-id \
      --database=testdb
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/create)

---
### `gcloud firestore user-creds delete`

Deletes a Cloud Firestore user creds

**Synopsis:**
```
gcloud firestore user-creds delete USER_CREDS --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USER_CREDS
   The user creds to operate on.

   For example, to operate on user creds creds-name-1:

       $ gcloud firestore user-creds delete creds-name-1
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds delete --database='foo' |


**Examples:**
```bash
To delete user creds 'test-user-creds-id' under database testdb.

    $ gcloud firestore user-creds delete test-user-creds-id \
      --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/delete)

---
### `gcloud firestore user-creds describe`

Describes a Cloud Firestore user creds

**Synopsis:**
```
gcloud firestore user-creds describe USER_CREDS --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USER_CREDS
   The user creds to operate on.

   For example, to operate on user creds creds-name-1:

       $ gcloud firestore user-creds describe creds-name-1
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds describe --database='foo' |


**Examples:**
```bash
To describe user creds 'test-user-creds-id' under database testdb.

    $ gcloud firestore user-creds describe test-user-creds-id \
      --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/describe)

---
### `gcloud firestore user-creds disable`

Disables a Cloud Firestore user creds

**Synopsis:**
```
gcloud firestore user-creds disable USER_CREDS --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USER_CREDS
   The user creds to operate on.

   For example, to operate on user creds creds-name-1:

       $ gcloud firestore user-creds disable creds-name-1
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds disable --database='foo' |


**Examples:**
```bash
To disable user creds 'test-user-creds-id' under database testdb.

    $ gcloud firestore user-creds disable test-user-creds-id \
      --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/disable)

---
### `gcloud firestore user-creds enable`

Enables a Cloud Firestore user creds

**Synopsis:**
```
gcloud firestore user-creds enable USER_CREDS --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USER_CREDS
   The user creds to operate on.

   For example, to operate on user creds creds-name-1:

       $ gcloud firestore user-creds enable creds-name-1
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds enable --database='foo' |


**Examples:**
```bash
To enable user creds 'test-user-creds-id' under database testdb.

    $ gcloud firestore user-creds enable test-user-creds-id \
      --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/enable)

---
### `gcloud firestore user-creds list`

Lists user creds under a Cloud Firestore database

**Synopsis:**
```
gcloud firestore user-creds list --database=DATABASE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds list --database='foo' |


**Examples:**
```bash
To list all user creds under database testdb.

    $ gcloud firestore user-creds list --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/list)

---
### `gcloud firestore user-creds reset-password`

Resets a Cloud Firestore user creds

**Synopsis:**
```
gcloud firestore user-creds reset-password USER_CREDS --database=DATABASE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
USER_CREDS
   The user creds to operate on.

   For example, to operate on user creds creds-name-1:

       $ gcloud firestore user-creds reset-password creds-name-1
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database` | DATABASE |  | The database to operate on. For example, to operate on database foo: $ gcloud firestore user-creds reset-password --database='foo' |


**Examples:**
```bash
To reset password for user creds 'test-user-creds-id' under database
testdb.

    $ gcloud firestore user-creds reset-password test-user-creds-id \
      --database='testdb'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firestore/user-creds/reset-password)

---