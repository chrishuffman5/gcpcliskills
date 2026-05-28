# gcloud kms single-tenant-hsm

commands for managing single tenant HSM instances

### `gcloud kms single-tenant-hsm create`

Create a single tenant HSM instance

**Synopsis:**
```
gcloud kms single-tenant-hsm create --location=LOCATION
    --total-approver-count=TOTAL_APPROVER_COUNT
    [--single-tenant-hsm-instance-id=SINGLE_TENANT_HSM_INSTANCE_ID]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--total-approver-count` | TOTAL_APPROVER_COUNT |  | _[This must be specified.]_ The total number of approvers. This is the N value used for M of N quorum auth. Must be greater than or equal to 3 and less than or equal to 16. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--single-tenant-hsm-instance-id` | SINGLE_TENANT_HSM_INSTANCE_ID |  | Specify an ID for the single tenant HSM instance. It must be unique within a location and match the regular expression [a-zA-Z0-9-]{1,63}. |


**Examples:**
```bash
The following command creates a single tenant HSM instance within the
location us-central1 with a total approver count of 3:

    $ gcloud kms single-tenant-hsm create --location=us-central1 \
        --total-approver-count=3

The following command creates a single tenant HSM instance within the
location us-central1 with a total approver count of 3, and the single
tenant HSM instance ID my_stchi:

    $ gcloud kms single-tenant-hsm create --location=us-central1 \
        --total-approver-count=3 \
        --single-tenant-hsm-instance-id=my_stchi
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/create)

---
### `gcloud kms single-tenant-hsm describe`

Get metadata for a single tenant HSM instance

Returns metadata for the given single tenant HSM instance.

    ## EXAMPLES

The following command returns the metadata for the single tenant HSM
instance with the name my_sthi in the location us-east1`using the fully
specified name:

    $ gcloud kms single-tenant-hsm describe
    projects/my-project/locations/us-east1/singleTenantHsmInstances/mysthi

The following command returns the metadata for the singletenanthsm instance
with the name mysthi in the location us-east1 using the location and
resource id:

    $ gcloud kms single-tenant-hsm describe mysthi --location=us-east1

**Synopsis:**
```
gcloud kms single-tenant-hsm describe
    (SINGLE_TENANT_HSM_INSTANCE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstance resource - The KMS single tenant HSM instance
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance on the command line
   with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE
     ID of the singleTenantHsmInstance or fully qualified identifier for
     the singleTenantHsmInstance.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstance.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/describe)

---
### `gcloud kms single-tenant-hsm list`

List single tenant HSM instances within a location

**Synopsis:**
```
gcloud kms single-tenant-hsm list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list all single tenant HSM instances in a location:

    $ gcloud kms single-tenant-hsm list --location={location}
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/list)

---

## `gcloud kms single-tenant-hsm proposal` — commands for managing single tenant HSM instance proposals
### `gcloud kms single-tenant-hsm proposal approve`

Approve a single tenant HSM instance proposal

**Synopsis:**
```
gcloud kms single-tenant-hsm proposal approve
    (SINGLE_TENANT_HSM_INSTANCE_PROPOSAL : --location=LOCATION
      --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE)
    (--quorum-challenge-replies=QUORUM_CHALLENGE_REPLIES
      --required-challenge-replies=REQUIRED_CHALLENGE_REPLIES)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstanceProposal resource - The KMS single tenant HSM
instance proposal resource. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance_proposal on the
   command line with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE_PROPOSAL
     ID of the singleTenantHsmInstanceProposal or fully qualified
     identifier for the singleTenantHsmInstanceProposal.

     To set the proposal attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstanceProposal.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE
     The KMS single tenant HSM instance of the
     singleTenantHsmInstanceProposal.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --single_tenant_hsm_instance on the command
       line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--quorum-challenge-replies` | QUORUM_CHALLENGE_REPLIES |  | _[At least one of these must be specified:]_ The challenge replies to approve the proposal. Challenge replies can be sent across multiple requests. Each tuple should be ("signed_challenge_file", "public_key_file"). |
| `--required-challenge-replies` | REQUIRED_CHALLENGE_REPLIES |  | _[At least one of these must be specified:]_ A list of tuples, each containing the file paths for a required challenge reply. Each tuple should be ("signed_challenge_file", "public_key_file"). |


**Examples:**
```bash
The following command approves a single tenant HSM instance proposal with
quorum challenge replies:

    $ gcloud kms single-tenant-hsm proposal approve \
        projects/my-project/locations/us-east1/\
    singleTenantHsmInstances/ my_sthi/proposals/my_proposal \
        --quorum-challenge-replies="[('signed_challenge_1.txt','public_k\
    ey_1.pem'),
('signed_challenge_2.txt','public_key_2.pem'),
('signed_challenge_3.txt','public_key_3.pem')]"

To approve a proposal with required challenges and quorum challenges:

    $ gcloud kms single-tenant-hsm proposal approve \
        projects/my-project/locations/us-east1/\
    singleTenantHsmInstances/ my_sthi/proposals/my_proposal \
        --required-challenge-replies="[('required_challenge.txt','public\
    _key_1.pem')]" \
        --quorum-challenge-replies="[('quorum_challenge_1.txt','public_k\
    ey_2.pem'),
('quorum_challenge_2.txt','public_key_3.pem')]"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/proposal/approve)

---
### `gcloud kms single-tenant-hsm proposal create`

Create a single tenant HSM instance proposal

$ gcloud kms single-tenant-hsm proposal create
  my_stchi
  --location=us-central1 \
  --required-approver-count=1  \
  --two-factor-public-key-pems=public_key_1.pem,public_key_2.pem

**Synopsis:**
```
gcloud kms single-tenant-hsm proposal create
    (SINGLE_TENANT_HSM_INSTANCE : --location=LOCATION)
    --operation-type=OPERATION_TYPE
    [--member-public-key-pem=MEMBER_PUBLIC_KEY_PEM]
    [--required-approver-count=REQUIRED_APPROVER_COUNT]
    [--single-tenant-hsm-instance-proposal-id=SINGLE_TENANT_HSM_INSTANCE_PROPOSAL_ID]
    [--two-factor-public-key-pems=[PEM_FILE_PATH,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstance resource - The KMS single tenant HSM instance
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance on the command line
   with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE
     ID of the singleTenantHsmInstance or fully qualified identifier for
     the singleTenantHsmInstance.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstance.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--operation-type` | OPERATION_TYPE |  | The type of operation for the single tenant HSM instance proposal. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member-public-key-pem` | MEMBER_PUBLIC_KEY_PEM |  | The PEM file containing the public key of the quorum member to add or remove. This field is required for add_quorum_member and remove_quorum_member operation types. |
| `--required-approver-count` | REQUIRED_APPROVER_COUNT |  | The number of approvers required for the single tenant HSM instance. This is the M value used for M of N quorum. Must be greater than or equal to 1 and less than or equal to the total approver count of the single tenant HSM instance minus 1. This field is required for the register_2fa_keys operation type. |
| `--single-tenant-hsm-instance-proposal-id` | SINGLE_TENANT_HSM_INSTANCE_PROPOSAL_ID |  | The ID to use for the single tenant HSM instance proposal, which will become the final component of the single tenant HSM instance resource name. |
| `--two-factor-public-key-pems` | [PEM_FILE_PATH,...] |  | The PEM files containing the two factor public keys 2FA keys for M of N quorum auth tenant HSM instance. This field is required for register_2fa_keys operation type. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/proposal/create)

---
### `gcloud kms single-tenant-hsm proposal delete`

Delete a single tenant HSM instance proposal

**Synopsis:**
```
gcloud kms single-tenant-hsm proposal delete
    (SINGLE_TENANT_HSM_INSTANCE_PROPOSAL : --location=LOCATION
      --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstanceProposal resource - The KMS single tenant HSM
instance proposal resource. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance_proposal on the
   command line with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE_PROPOSAL
     ID of the singleTenantHsmInstanceProposal or fully qualified
     identifier for the singleTenantHsmInstanceProposal.

     To set the proposal attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstanceProposal.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE
     The KMS single tenant HSM instance of the
     singleTenantHsmInstanceProposal.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --single_tenant_hsm_instance on the command
       line.
```

**Examples:**
```bash
The following command deletes a single tenant HSM instance proposal:

    $ gcloud kms single-tenant-hsm proposal delete \
        projects/my-project/locations/us-east1/\
    singleTenantHsmInstances/ my_sthi/proposals/my_proposal
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/proposal/delete)

---
### `gcloud kms single-tenant-hsm proposal describe`

Get metadata for a single tenant HSM instance proposal

**Synopsis:**
```
gcloud kms single-tenant-hsm proposal describe
    (SINGLE_TENANT_HSM_INSTANCE_PROPOSAL : --location=LOCATION
      --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstanceProposal resource - The KMS single tenant HSM
instance proposal resource. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance_proposal on the
   command line with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE_PROPOSAL
     ID of the singleTenantHsmInstanceProposal or fully qualified
     identifier for the singleTenantHsmInstanceProposal.

     To set the proposal attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstanceProposal.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE
     The KMS single tenant HSM instance of the
     singleTenantHsmInstanceProposal.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --single_tenant_hsm_instance on the command
       line.
```

**Examples:**
```bash
The following command returns the metadata for the single tenant HSM
instance proposal with the name my_proposal, of the instance my_sthi, and
in the location us-east1 using the fully specified resource name.

      $ gcloud kms single-tenant-hsm proposal describe \
          projects/my-project/locations/us-east1/\
      singleTenantHsmInstances/ my_sthi/proposals/my_proposal ```

    The following command returns the metadata for the single tenant HSM instance
    proposal with the name `my_proposal`, of the instance `my_sthi`, and in the
    location `us-east1` using the location, instance id, and proposal id.

    $ gcloud kms single-tenant-hsm proposal describe my_proposal \
        --single_tenant_hsm_instance=my_sthi --location=us-east1 ```
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/proposal/describe)

---
### `gcloud kms single-tenant-hsm proposal execute`

Executes a single tenant HSM proposal

Executes a single tenant HSM proposal. The proposal must be in an approved
state.

**Synopsis:**
```
gcloud kms single-tenant-hsm proposal execute
    (SINGLE_TENANT_HSM_INSTANCE_PROPOSAL : --location=LOCATION
      --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstanceProposal resource - The KMS single tenant HSM
instance proposal resource. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance_proposal on the
   command line with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE_PROPOSAL
     ID of the singleTenantHsmInstanceProposal or fully qualified
     identifier for the singleTenantHsmInstanceProposal.

     To set the proposal attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstanceProposal.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --location on the command line.

  --single_tenant_hsm_instance=SINGLE_TENANT_HSM_INSTANCE
     The KMS single tenant HSM instance of the
     singleTenantHsmInstanceProposal.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance_proposal on the
       command line with a fully specified name;
     + provide the argument --single_tenant_hsm_instance on the command
       line.
```

**Examples:**
```bash
The following command executes a single tenant HSM proposal named
my_proposal associated with the single tenant HSM instance my_sthi within
the location us-central1 with the fully specified name.

    $ gcloud kms single-tenant-hsm proposal execute \
        projects/my-project/locations/us-central1/\
    singleTenantHsmInstances/ my_sthi/proposals/my_proposal

The following command executes a single tenant HSM proposal named
my_proposal associated with the single tenant HSM instance my_sthi within
the location us-central1 using the location, single-tenant-hsm-instance,
and proposal id.

    $ gcloud kms single-tenant-hsm proposal execute my_proposal \
        --location=us-central1 --single_tenant_hsm_instance=my_sthi \
        proposal_id=my_proposal
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/proposal/execute)

---
### `gcloud kms single-tenant-hsm proposal list`

List single tenant HSM instance proposals within a single tenant HSM instance

**Synopsis:**
```
gcloud kms single-tenant-hsm proposal list
    (SINGLE_TENANT_HSM_INSTANCE : --location=LOCATION)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SingleTenantHsmInstance resource - The KMS single tenant HSM instance
resource. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument single_tenant_hsm_instance on the command line
   with a fully specified name;
 * set the property core/project.

This must be specified.

  SINGLE_TENANT_HSM_INSTANCE
     ID of the singleTenantHsmInstance or fully qualified identifier for
     the singleTenantHsmInstance.

     To set the single_tenant_hsm_instance attribute:
     + provide the argument single_tenant_hsm_instance on the command
       line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The Google Cloud location for the singleTenantHsmInstance.

     To set the location attribute:
     + provide the argument single_tenant_hsm_instance on the command
       line with a fully specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To list all single tenant HSM instance proposals in a single tenant
instance using the single tenant HSM instance name my_sthi and the location
us-east1:

    $ gcloud kms single-tenant-hsm proposal list my_sthi \
        --location=us-east1

To list all single tenant HSM instance proposals in a single tenant
instance using the single tenant HSM instance name my_sthi and the location
us-east1 with the full single tenant HSM instance resource name:

    $ gcloud kms single-tenant-hsm proposal list \
        projects/my-project/locations/us-east1/\
    singleTenantHsmInstances/my_sthi
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/kms/single-tenant-hsm/proposal/list)

---