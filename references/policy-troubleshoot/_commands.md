# gcloud policy-troubleshoot (top-level commands)

### `gcloud policy-troubleshoot iam`

Troubleshoot the IAM Policy

Performs a check on whether a principal is granted a permission on a
resource and how that access is determined according to the resource's
effective IAM policy interpretation.

**Synopsis:**
```
gcloud policy-troubleshoot iam RESOURCE --permission=PERMISSION
    --principal-email=PRINCIPAL_EMAIL [--destination-ip=DESTINATION_IP]
    [--destination-port=DESTINATION_PORT] [--request-time=REQUEST_TIME]
    [--resource-name=RESOURCE_NAME] [--resource-service=RESOURCE_SERVICE]
    [--resource-type=RESOURCE_TYPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESOURCE
   Full resource name that access is checked against. See:
   https://cloud.google.com/iam/docs/resource-names.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--permission` | PERMISSION |  | Cloud IAM permission to check, e.g. "resourcemanager.projects.get". |
| `--principal-email` | PRINCIPAL_EMAIL |  | Email address that identifies the principal to check. Only Google Accounts and service accounts are supported. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination-ip` | DESTINATION_IP |  | The request destination IP address to use when checking conditional bindings. For example, 198.1.1.1. |
| `--destination-port` | DESTINATION_PORT |  | The request destination port to use when checking conditional bindings. For example, 8080. |
| `--request-time` | REQUEST_TIME |  | The request timestamp to use when checking conditional bindings. This string must adhere to UTC format (RFC 3339). For example,2021-01-01T00:00:00Z. See: https://tools.ietf.org/html/rfc3339 |
| `--resource-name` | RESOURCE_NAME |  | The resource name value to use when checking conditional bindings. See: https://cloud.google.com/iam/docs/conditions-resource-attributes#resource-name. |
| `--resource-service` | RESOURCE_SERVICE |  | The resource service value to use when checking conditional bindings. See: https://cloud.google.com/iam/docs/conditions-resource-attributes#resource-service |
| `--resource-type` | RESOURCE_TYPE |  | The resource type value to use when checking conditional bindings. See: https://cloud.google.com/iam/docs/conditions-resource-attributes#resource-type |


**Examples:**
```bash
To troubleshoot a permission of a principal on a resource, run:

    $ gcloud policy-troubleshoot iam \
        //cloudresourcemanager.googleapis.com/projects/project-id \
        --principal-email=my-iam-account@somedomain.com \
        --permission=resourcemanager.projects.get

See https://cloud.google.com/iam/help/allow-policies/overview for more
information about IAM policies.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/policy-troubleshoot/iam)

---