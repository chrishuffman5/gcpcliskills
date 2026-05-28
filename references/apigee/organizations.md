# gcloud apigee organizations

manage Apigee organizations

### `gcloud apigee organizations list`

List Apigee organizations and their paired Cloud Platform projects

List Apigee organizations and their paired Cloud Platform projects.

gcloud apigee organizations list lists all organizations to which the
user's gcloud auth credentials have access, even if they don't match the
active Cloud Platform project.

Apigee organizations are distinct from Cloud Platform organizations, and
usually have a one-to-one relationship with Cloud Platform projects.

**Synopsis:**
```
gcloud apigee organizations list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all accessible organizations and their associated Cloud Platform
projects, run:

    $ gcloud apigee organizations list

To get a JSON array of all organizations whose Cloud Platform project names
contain the word sandbox, run:

    $ gcloud apigee organizations list --format=json \
      --filter="project:(sandbox)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/organizations/list)

---