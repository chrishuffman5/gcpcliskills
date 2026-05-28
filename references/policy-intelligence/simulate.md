# gcloud policy-intelligence simulate

simulate changes to organization policies

### `gcloud policy-intelligence simulate orgpolicy`

Understand how changes to organization policies could affect your resources

Understand how changes to organization policies could affect your
resources.

**Synopsis:**
```
gcloud policy-intelligence simulate orgpolicy
    --organization=ORGANIZATION_ID
    [--custom-constraints=[CUSTOM_CONSTRAINTS,...]]
    [--policies=[POLICIES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION_ID |  | Organization ID. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-constraints` | [CUSTOM_CONSTRAINTS,...] |  | Path to the JSON or YAML file that contains the custom constraints to simulate. Multiple custom constraints can be simulated by providing multiple, comma-separated paths. For example: --custom-constraints=constraint1.json,constraint2.json |
| `--policies` | [POLICIES,...] |  | Path to the JSON or YAML file that contains the organization policy to simulate. Multiple policies can be simulated by providing multiple, comma-separated paths. For example: --policies=p1.json,p2.json |


**Examples:**
```bash
To simulate changes to custom constraints defined in
./custom-constraint.json, run:

    $ gcloud policy-intelligence simulate orgpolicy \
        --organization=ORGANIZATION_ID \
        --custom-constraints=custom-constraint.json

To simulate changes to organization policies defined in ./policy.json, run:

    $ gcloud policy-intelligence simulate orgpolicy \
        --organization=ORGANIZATION_ID --policies=policy.json

To simulate changes to both custom constraints defined in
./custom-constraint.json and organization policies defined in
./policy.json, run:

    $ gcloud policy-intelligence simulate orgpolicy \
        --organization=ORGANIZATION_ID --policies=policy.json \
        --custom-constraints=custom-constraint.json

See
https://cloud.google.com/policy-intelligence/docs/test-organization-policies
for more information about Policy Simulator for Organization Policy.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/policy-intelligence/simulate/orgpolicy)

---