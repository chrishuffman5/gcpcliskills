# gcloud billing projects

manage the billing account configuration of your projects

### `gcloud billing projects describe`

Show detailed billing information for a project

This command shows billing info for a project, given its ID.

This call can fail for the following reasons:

  o The project specified does not exist.
  o The active user does not have permission to access the given project.

**Synopsis:**
```
gcloud billing projects describe PROJECT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   Specify a project id.
```

**Examples:**
```bash
To see detailed billing information for a project my-project, run:

    $ gcloud billing projects describe my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/projects/describe)

---
### `gcloud billing projects link`

Link a project with a billing account

This command sets or updates the billing account associated with a project.

Billing is enabled on a project when the project is linked to a valid,
active Cloud Billing account. The billing account accrues charges for the
usage of resources in all of the linked projects. If the project is already
linked to a billing account, this command moves the project to the billing
account you specify, updating the billing account that is linked to the
project.

Note that associating a project with a closed billing account has the same
effect as disabling billing on the project: any paid resources in use by
the project are shut down, and your application stops functioning. Unless
you want to disable billing, you should always specify a valid, active
Cloud Billing account when you run this command. Learn how to confirm the
status of a Cloud Billing account at
https://cloud.google.com/billing/docs/how-to/verify-billing-enabled#billing_account_status

**Synopsis:**
```
gcloud billing projects link PROJECT_ID --billing-account=ACCOUNT_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   Specify a project id.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | ACCOUNT_ID |  | Specify a billing account ID. Billing account IDs are of the form 0X0X0X-0X0X0X-0X0X0X. To see available IDs, run $ gcloud billing accounts list. |


**Examples:**
```bash
To link a billing account 0X0X0X-0X0X0X-0X0X0X with a project my-project,
run:

    $ gcloud billing projects link my-project \
        --billing-account=0X0X0X-0X0X0X-0X0X0X
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/projects/link)

---
### `gcloud billing projects list`

List all active projects associated with the specified billing account

gcloud billing projects list ACCOUNT_ID -- lists all active projects, for
the specified billing account id.

**Synopsis:**
```
gcloud billing projects list --billing-account=ACCOUNT_ID
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--billing-account` | ACCOUNT_ID |  | Specify a billing account ID. Billing account IDs are of the form 0X0X0X-0X0X0X-0X0X0X. To see available IDs, run $ gcloud billing accounts list. |


**Examples:**
```bash
To list projects linked to billing account 0X0X0X-0X0X0X-0X0X0X, run:

    $ gcloud billing projects list --billing-account=0X0X0X-0X0X0X-0X0X0X
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/projects/list)

---
### `gcloud billing projects unlink`

Unlink the account (if any) linked with a project

This command unlinks a project from its associated billing account. This
action disables billing on the project. Any billable resources and services
in use in your project are stopped, and your application stops functioning.
Any costs accrued prior to disabling billing on the project are charged to
the previously associated billing account.

Note: To link a project to a different billing account, use the billing
projects link command. You do not need to unlink the project first.

**Synopsis:**
```
gcloud billing projects unlink PROJECT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROJECT_ID
   Specify a project id.
```

**Examples:**
```bash
To unlink the project my-project from its linked billing account, run:

    $ gcloud billing projects unlink my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/projects/unlink)

---