# gcloud identity groups

manage Cloud Identity Groups

### `gcloud identity groups create`

Create a new group

Create a new group.

**Synopsis:**
```
gcloud identity groups create EMAIL
    (--customer=CUSTOMER | --organization=ORGANIZATION)
    [--description=DESCRIPTION] [--display-name=DISPLAY_NAME]
    [--dynamic-user-query=DYNAMIC_USER_QUERY]
    [--with-initial-owner=WITH_INITIAL_OWNER]
    [--group-type=GROUP_TYPE; default="discussion" | --labels=LABELS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
EMAIL
   The email address of the group to be created.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--customer` | CUSTOMER |  | _[Exactly one of these must be specified:]_ The customer ID for the customer\'s G Suite account. Example of customer: "C01k1e9nw" |
| `--organization` | ORGANIZATION |  | _[Exactly one of these must be specified:]_ The organization the Group being created belongs to. This can be specified either as an ID ("123456789") or as the associated domain ("example.com"). |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | An extended description to help users determine the purpose of a Group. For example, you can include information about who should join the Group, the types of messages to send to the Group, links to FAQs about the Group, or related Groups. Maximum length is 4,096 characters. |
| `--display-name` | DISPLAY_NAME |  | The Group's display name. |
| `--dynamic-user-query` | DYNAMIC_USER_QUERY |  | Query that determines the memberships of the dynamic group. Example of a query: --dynamic-user-query="user.organizations.exists(org,org.title=='SWE')" |
| `--with-initial-owner` | one of: empty The creator of the group will not be the owner of the group |  | If specified the user making the request will be added as the initial owner of the group being created. WITH_INITIAL_OWNER must be one of: empty The creator of the group will not be the owner of the group. This is the default for dynamic groups. with-initial-owner The creator of the group will be the owner of the group. This is the default for non-dynamic groups. |


**Examples:**
```bash
To quickly create a new Google Groups discussion group with default
settings:

    $ gcloud identity groups create eng-discuss@example.com \
        --organization="example.com"

To create a new Google Groups discussion group with a display name and
descripton:

    $ gcloud identity groups create eng-discuss@example.com \
        --organization="example.com" --display-name="Engineer Discuss" \
        --description="Group for engineering discussions"

To create a new security group:

    $ gcloud identity groups create security-group@example.com \
        --organization="example.com" --group-type="security" \
        --display-name="Security Group" \
        --description="Description of Security Group"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/create)

---
### `gcloud identity groups delete`

Delete an existing group

Delete an existing group.

**Synopsis:**
```
gcloud identity groups delete EMAIL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
EMAIL
   The email address of the group being deleted.
```

**Examples:**
```bash
To delete a group:

    $ gcloud identity groups delete eng-discuss@foo.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/delete)

---
### `gcloud identity groups describe`

Describe an existing group

Describe an existing group.

**Synopsis:**
```
gcloud identity groups describe EMAIL [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
EMAIL
   The email address of the group being described.
```

**Examples:**
```bash
To describe a group:

    $ gcloud identity groups describe eng-discuss@foo.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/describe)

---
### `gcloud identity groups search`

Searches for Groups matching a specified query

Searches for Groups matching a specified query.

**Synopsis:**
```
gcloud identity groups search --labels=LABELS
    (--customer=CUSTOMER | --organization=ORGANIZATION)
    [--page-size=PAGE_SIZE] [--page-token=PAGE_TOKEN]
    [--view=VIEW; default="basic"] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | LABELS |  | One or more label entries that apply to the Group. Currently supported labels contain a key with an empty value. Google Groups are the default type of group and have a label with a key of 'cloudidentity.googleapis.com/groups.discussion_forum' and an empty value. Existing Google Groups can have an additional label with a key of 'cloudidentity.googleapis.com/groups.security' and an empty value added to them. This is an immutable change and the security label cannot be removed once added. POSIX groups have a label with a key of 'cloudidentity.googleapis.com/groups.posix'. Dynamic groups have a label with a key of 'cloudidentity.googleapis.com/groups.dynamic'. Identity-mapped groups for Cloud Search have a label with a key of 'system/groups/external' and an empty value. Examples: {"cloudidentity.googleapis.com/groups.discussion_forum": ""} or {"system/groups/external": ""}. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-size` | PAGE_SIZE |  | The maximum number of results to return. Note that the number of results returned may be less than this value even if there are more available results. To fetch all results, clients must continue calling this method repeatedly until the response no longer contains a nextPageToken. If unspecified, defaults to 200 'basic' view and to 50 for 'full' view. Must not be greater than 1000 for 'basic' view or 500 for 'full' view. |
| `--page-token` | PAGE_TOKEN |  | The nextPageToken value returned from a previous search request, if any. |
| `--view` | one of: basic Default | basic | The level of detail to be returned. There are two possible views: 'basic' and 'full'. If unspecified, default to 'basic'. VIEW must be one of: basic Default. Only basic group information is returned. full All group information is returned. |


**Examples:**
```bash
To Search groups:

    $ gcloud identity groups search --organization="5149234212" \
        --labels="cloudidentity.googleapis.com/groups.discussion_forum" \
    --page-size=3 --page-token="ala9glealanal908"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/search)

---
### `gcloud identity groups update`

Update a group

Update a group.

**Synopsis:**
```
gcloud identity groups update EMAIL
    [--dynamic-user-query=DYNAMIC_USER_QUERY] [--labels=LABELS]
    [--clear-description | --description=DESCRIPTION]
    [--clear-display-name | --display-name=DISPLAY_NAME]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
EMAIL
   The email address of the group to be updated.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--dynamic-user-query` | DYNAMIC_USER_QUERY |  | Query that determines the memberships of the dynamic group. Example of a query: --dynamic-user-query="user.organizations.exists(org,org.title=='SWE')" |
| `--labels` | LABELS |  | One or more label entries that apply to the group. Currently supported labels contain a key with an empty value. Google Groups are the default type of group and have a label with a key of 'cloudidentity.googleapis.com/groups.discussion_forum' and an empty value. Existing Google Groups can have an additional label with a key of 'cloudidentity.googleapis.com/groups.security' and an empty value added to them. This is an immutable change and the security label cannot be removed once added. Dynamic groups have a label with a key of 'cloudidentity.googleapis.com/groups.dynamic'. Identity-mapped groups for Cloud Search have a label with a key of 'system/groups/external' and an empty value. Examples: {"cloudidentity.googleapis.com/groups.discussion_forum": ""} or {"system/groups/external": ""}. |


**Examples:**
```bash
To update a group:

    $ gcloud identity groups update eng-discuss@foo.com \
        --display-name="New Engineer Discuss" \
        --description="Group for engineering discussions"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/update)

---

## `gcloud identity groups memberships` — manage Cloud Identity Groups Memberships
### `gcloud identity groups memberships add`

Create a new membership in an existing group

Create a new membership in an existing group.

**Synopsis:**
```
gcloud identity groups memberships add --group-email=GROUP_EMAIL
    --member-email=MEMBER_EMAIL [--expiration=EXPIRATION]
    [--roles=[ROLES,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group the new membership is being added to. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the group or user being added to a group. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--expiration` | EXPIRATION |  | Optional time of expiration for the membership. This is given as a duration from now, for example '30d', '6m', '3y' for 30 days, 6 months, or 3 years respectively. |
| `--roles` | [ROLES,...] |  | A comma-separated list of roles for a member within the Group. If not specified, MEMBER will be used as a default value. |


**Examples:**
```bash
To create a new membership in a group:

    $ gcloud identity groups memberships add \
        --group-email="eng-discuss@foo.com" \
        --member-email="user@foo.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/add)

---
### `gcloud identity groups memberships check-transitive-membership`

Check a potential member for transitive membership in a group

Check a potential member for transitive membership in a group.

**Synopsis:**
```
gcloud identity groups memberships check-transitive-membership
    --group-email=GROUP_EMAIL --member-email=MEMBER_EMAIL
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group to check transitive membership for. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the member to check transitive membership for. |


**Examples:**
```bash
To check if a potential member has a transitive membership in a group.

    $ gcloud identity groups memberships check-transitive-membership \
        --group-email=eng@foo.com --member-email=eng-discuss@foo.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/check-transitive-membership)

---
### `gcloud identity groups memberships delete`

Delete a membership from an existing group

Delete a membership from an existing group.

**Synopsis:**
```
gcloud identity groups memberships delete --group-email=GROUP_EMAIL
    --member-email=MEMBER_EMAIL [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group the new membership is being removed from. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the group or user being removed from the group identified by group-email. |


**Examples:**
```bash
To delete a memberships from a group:

    $ gcloud identity groups memberships delete \
        --group-email="eng-discuss@foo.com" \
        --member-email="user@foo.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/delete)

---
### `gcloud identity groups memberships describe`

Describe a membership in a group

Describe a membership in a group.

**Synopsis:**
```
gcloud identity groups memberships describe --group-email=GROUP_EMAIL
    --member-email=MEMBER_EMAIL [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group whose membership is being described. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the member whose membership is being described. |


**Examples:**
```bash
To describe a membership in a group:

    $ gcloud identity groups memberships describe \
        --group-email="eng-discuss@foo.com" \
        --member-email="user@foo.com"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/describe)

---
### `gcloud identity groups memberships get-membership-graph`

Get a membership graph of just a member or both a member and a group

Get a membership graph of just a member or both a member and a group.

**Synopsis:**
```
gcloud identity groups memberships get-membership-graph --labels=LABELS
    --member-email=MEMBER_EMAIL [--group-email=GROUP_EMAIL]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | LABELS |  | The labels of the groups in the membership graph. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the member to get the membership graph for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group to constrain the membership graph with. |


**Examples:**
```bash
To get a membership graph of just a member.

    $ gcloud identity groups memberships get-membership-graph \
        --member-email=eng-discuss@foo.com \
        --labels=cloudidentity.googleapis.com/groups.discussion_forum

To get a membership graph between a member and a group.

    $ gcloud identity groups memberships get-membership-graph \
        --member-email=eng-discuss@foo.com --group-email=eng@foo.com \
        --labels=cloudidentity.googleapis.com/groups.discussion_forum
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/get-membership-graph)

---
### `gcloud identity groups memberships list`

List memberships in an existing group

List memberships in an existing group.

**Synopsis:**
```
gcloud identity groups memberships list --group-email=GROUP_EMAIL
    [--page-token=PAGE_TOKEN] [--view=VIEW; default="basic"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group to show members for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-token` | PAGE_TOKEN |  | The next_page_token value returned from a previous list request, if any. |
| `--view` | one of: basic Response only basic information of the Groups | basic | There are two possible views, 'basic' and 'full', default is 'basic'. VIEW must be one of: basic Response only basic information of the Groups. (e.g. 'display_name', 'name') full Response includes all the fields of the Groups |


**Examples:**
```bash
To list memberships of a group:

    $ gcloud identity groups memberships list \
        --group-email="eng-discuss@foo.com" --limit=50
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/list)

---
### `gcloud identity groups memberships modify-membership-roles`

Add/remove/modify membership roles of a membership in a group

Add/remove/modify membership roles OR update expiry details of membership
in a group.

**Synopsis:**
```
gcloud identity groups memberships modify-membership-roles
    --group-email=GROUP_EMAIL --member-email=MEMBER_EMAIL
    [--update-roles-params=UPDATE_ROLES_PARAMS
      | --add-roles=ADD_ROLES --remove-roles=[REMOVE_ROLES,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group that member-email belongs to. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the group or user that is being updated |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-roles-params` | UPDATE_ROLES_PARAMS |  | _[At most one of these can be specified:]_ Resource representing the parameters to update membership roles. An example would be --update-roles-params MEMBER=expiry_details.expire_time. |
| `--add-roles` | ADD_ROLES |  | _[At most one of these can be specified:]_ Membership roles to be added. Currently supported MembershipRole: 'MEMBER', 'OWNER', 'MANAGER'. |
| `--remove-roles` | [REMOVE_ROLES,...] |  | _[At most one of these can be specified:]_ Membership role names to be removed. Currently supported MembershipRole: 'OWNER', 'MANAGER'. MEMBER-less owner is not supported so removing just MEMBER role won't be possible. |


**Examples:**
```bash
To add a new membership role to an existing group-member pair.

    $ gcloud identity groups memberships modify-membership-roles \
        --group-email="eng-discuss@foo.com" \
        --member-email="user@foo.com" --add-roles=OWNER
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/modify-membership-roles)

---
### `gcloud identity groups memberships search-transitive-groups`

Search transitive groups of a member

Search transitive groups of a member.

**Synopsis:**
```
gcloud identity groups memberships search-transitive-groups --labels=LABELS
    --member-email=MEMBER_EMAIL [--page-size=PAGE_SIZE]
    [--page-token=PAGE_TOKEN] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | LABELS |  | The labels of the transitive groups. |
| `--member-email` | MEMBER_EMAIL |  | The email address of the member to search transitive groups for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-size` | PAGE_SIZE |  | The maximum number of results to return. |
| `--page-token` | PAGE_TOKEN |  | The next_page_token value returned from a previous search request, if any. |


**Examples:**
```bash
To search transitive groups of a member.

    $ gcloud identity groups memberships search-transitive-groups \
        --labels=cloudidentity.googleapis.com/groups.discussion_forum \
        --member-email=eng-discuss@foo.com --page-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/search-transitive-groups)

---
### `gcloud identity groups memberships search-transitive-memberships`

Search transitive memberships of a group

Search transitive memberships of a group.

**Synopsis:**
```
gcloud identity groups memberships search-transitive-memberships
    --group-email=GROUP_EMAIL [--page-size=PAGE_SIZE]
    [--page-token=PAGE_TOKEN] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-email` | GROUP_EMAIL |  | The email address of the group to search transitive memberships for. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page-size` | PAGE_SIZE |  | The maximum number of results to return. |
| `--page-token` | PAGE_TOKEN |  | The next_page_token value returned from a previous search request, if any. |


**Examples:**
```bash
To search transitive memberships of a group.        $ gcloud identity groups memberships search-transitive-memberships \
        --group-email=eng@foo.com --page-size=10
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/identity/groups/memberships/search-transitive-memberships)

---