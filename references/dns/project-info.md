# gcloud dns project-info

view Cloud DNS related information for a project

### `gcloud dns project-info describe`

View Cloud DNS related information for a project

This command displays Cloud DNS related information for your project
including quotas for various resources and operations.

**Synopsis:**
```
gcloud dns project-info describe PROJECT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   The identifier for the project you want DNS related info for.
```

**Examples:**
```bash
To display Cloud DNS related information for your project, run:

    $ gcloud dns project-info describe my_project_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/dns/project-info/describe)

---