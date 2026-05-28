# gcloud billing — Cloud Billing

## Overview
Cloud Billing controls how you are charged for Google Cloud usage. The `gcloud billing` command group manages billing accounts (and their IAM access), links and unlinks projects to billing accounts, and creates spend budgets with threshold alerts. Reach for it to audit which accounts and projects you have access to, to enable or disable billing on a project, to grant billing roles, and to set up cost-control budgets and notifications.

## Quick reference — common workflows

### Discover billing accounts and linked projects
```bash
# List all active billing accounts you can access
gcloud billing accounts list

# Show only open accounts
gcloud billing accounts list --filter=open=true

# Inspect one account
gcloud billing accounts describe 0X0X0X-0X0X0X-0X0X0X

# List projects paying through that account
gcloud billing projects list --billing-account=0X0X0X-0X0X0X-0X0X0X
```

### Link, move, or disable billing on a project
```bash
# Check a project's current billing status
gcloud billing projects describe my-project

# Link the project to an account (also moves it if already linked elsewhere)
gcloud billing projects link my-project \
    --billing-account=0X0X0X-0X0X0X-0X0X0X

# Disable billing — unlink the project from its account
gcloud billing projects unlink my-project
```
> To move a project between accounts, run `projects link` directly — you do not need to `unlink` first.

### Manage billing account IAM
```bash
# View the current IAM policy
gcloud billing accounts get-iam-policy 0X0X0X-0X0X0X-0X0X0X

# Grant the Billing Account User role to a principal
gcloud billing accounts add-iam-policy-binding 0X0X0X-0X0X0X-0X0X0X \
    --member='user:someone@example.com' \
    --role='roles/billing.user'

# Remove that binding
gcloud billing accounts remove-iam-policy-binding 0X0X0X-0X0X0X-0X0X0X \
    --member='user:someone@example.com' \
    --role='roles/billing.user'
```

### Create a budget with threshold alerts
```bash
# Requires the Cloud Billing Budget API
gcloud services enable billingbudgets.googleapis.com

# $100.75 budget on account 123, alerting at 50% actual and 75% forecasted spend
gcloud billing budgets create \
    --billing-account=123 \
    --display-name="BUDGET1" \
    --budget-amount=100.75USD \
    --threshold-rule=percent=0.50 \
    --threshold-rule=percent=0.75,basis=forecasted-spend

# Budget scoped to a project, with a Pub/Sub notification topic
gcloud billing budgets create \
    --billing-account=123 \
    --display-name="Team Budget" \
    --budget-amount=1000USD \
    --filter-projects=projects/my-project \
    --notifications-rule-pubsub-topic=projects/my-project/topics/budget-alerts \
    --threshold-rule=percent=0.90
```

### Inspect, update, and delete budgets
```bash
# List budgets (requires --billing-account)
gcloud billing budgets list --billing-account=123

# Describe a budget by ID
gcloud billing budgets describe abc --billing-account=123

# Change the budget amount
gcloud billing budgets update abc --billing-account=123 \
    --budget-amount=987.65

# Delete a budget
gcloud billing budgets delete abc --billing-account=123
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `billing accounts` | [`accounts.md`](accounts.md) | 6 | Manage billing accounts and their IAM policies |
| `billing budgets` | [`budgets.md`](budgets.md) | 5 | Manage budgets and threshold alerts for billing accounts |
| `billing projects` | [`projects.md`](projects.md) | 4 | Manage the billing account configuration of your projects |

See [`index.md`](index.md) for a one-line index of all 15 GA commands.

## Common flags & tips
- **Billing account IDs** are of the form `0X0X0X-0X0X0X-0X0X0X`; run `gcloud billing accounts list` to find them. Subaccounts show a non-empty `MASTER_ACCOUNT_ID`.
- **`--billing-account` is required** for `budgets list/create` and `projects list`. For `budgets describe/update/delete` you can either pass `--billing-account` plus the budget ID, or supply the fully qualified name `billingAccounts/123/budgets/abc` as the positional argument.
- **Budget amounts** accept a bare number (`987.65`, uses the account currency) or a currency-qualified value (`100.75USD`). Currency, if given, must match the billing account currency.
- **`--threshold-rule` repeats** to add multiple alert points. `percent` is a 1.0-based fraction (`0.50` = 50%); `basis` is `current-spend` (default) or `forecasted-spend`.
- **Filter outputs**: `--filter=open=true` on `accounts list`; standard `--filter`, `--sort-by`, `--limit`, and `--format` flags work on the `list` and `get-iam-policy` commands.
- **Scope budgets** with `--filter-projects=projects/{id}`, `--filter-services=services/{id}`, `--filter-labels=KEY=VALUE`, or `--filter-resource-ancestors=folders/{id}`.
- **Notifications**: route budget alerts to Pub/Sub via `--notifications-rule-pubsub-topic`, or to Cloud Monitoring channels via `--notifications-rule-monitoring-notification-channels`; use `--disable-default-iam-recipients` to suppress the default emails to billing admins/users.
- **IAM**: `accounts get-iam-policy` output is a valid policy file for `accounts set-iam-policy`. Note `set-iam-policy` replaces the entire policy — prefer `add-/remove-iam-policy-binding` for incremental changes.

## Required IAM roles
- **List accounts / inspect billing:** `roles/billing.viewer`
- **Link/unlink projects:** `roles/billing.user` or `roles/billing.projectManager`
- **Create self-serve billing accounts (org-level):** `roles/billing.creator`
- **Manage account IAM, payments, exports:** `roles/billing.admin`
- **Create/update budgets:** `roles/billing.costsManager` (or `roles/billing.projectCostsManager` scoped to projects)

## beta / alpha
`gcloud beta billing` and `gcloud alpha billing` exist and surface the same three subgroups as GA (`accounts`, `budgets`, `projects`). No alpha/beta-exclusive commands were identified — the pre-release tracks mirror GA for this service. Use the GA commands unless you specifically need pre-release behavior.

## Official documentation
- [Cloud Billing docs home](https://cloud.google.com/billing/docs) — hub for accounts, invoices, budgets, and cost analysis.
- [Cloud Billing overview / concepts](https://cloud.google.com/billing/docs/concepts) — account structure, resource hierarchy, and billing concepts.
- [Manage your Cloud Billing account](https://cloud.google.com/billing/docs/how-to/manage-billing-account) — create, modify, and close billing accounts.
- [Enable, disable, or change billing for a project](https://cloud.google.com/billing/docs/how-to/modify-project) — linking and unlinking projects.
- [Cloud Billing access control](https://cloud.google.com/billing/docs/how-to/billing-access) — predefined IAM roles and permissions for billing.
- [Create, edit, or delete budgets and budget alerts](https://cloud.google.com/billing/docs/how-to/budgets) — budget creation and threshold alerts.
- [Set up programmatic budget notifications](https://cloud.google.com/billing/docs/how-to/budgets-programmatic-notifications) — Pub/Sub integration for automated cost control.
- [gcloud billing CLI reference](https://cloud.google.com/sdk/gcloud/reference/billing) — full GA command and flag reference.
