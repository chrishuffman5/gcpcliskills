# gcloud apigee products

manage Apigee API products

### `gcloud apigee products create`

Create an Apigee API product

Create an Apigee API product.

gcloud apigee products create publishes a collection of API proxy resources
as an API product.

API products combine their underlying API proxies with quota settings and
metadata, to deliver customized and productized API bundles to the
developer community.

API products enable the repackaging of APIs on-the-fly, without having to
do any additional coding or configuration. Apigee recommends starting with
a simple API product including only required elements, and then
provisioning credentials to apps to enable them to start testing those
APIs.

At minimum, a new API product requires an internal name, access policy, and
declaration of what environments and API proxies to include in the product.
If these aren't provided, interactive calls will prompt for the missing
values, and non-interactive calls will fail.

**Synopsis:**
```
gcloud apigee products create [INTERNAL_NAME : --organization=ORGANIZATION]
    [--attributes=[NAME=VALUE,...]] [--description=DESCRIPTION]
    [--display-name=DISPLAY_NAME] [--manual-approval]
    [--oauth-scopes=[SCOPE,...]]
    [--all-environments | --environments=ENVIRONMENT,[ENVIRONMENT,...]]
    [--all-proxies | --apis=[API,...] --resources=RESOURCE#[RESOURCE#...]]
    [--internal-access | --private-access | --public-access]
    [--quota=QUOTA --quota-interval=QUOTA_INTERVAL --quota-unit=QUOTA_UNIT]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
API product resource - API product to be created. Characters in a
product's internal name are restricted to: A-Za-z0-9._-$ %. The arguments
in this group can be used to specify the attributes of this resource.

  INTERNAL_NAME
     ID of the API product or fully qualified identifier for the API
     product.

     To set the product attribute:
     + provide the argument INTERNAL_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the API product. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument INTERNAL_NAME on the command line with a
       fully specified name;
     + provide the argument --organization on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attributes` | [NAME=VALUE,...] |  | Key-value attribute pairs that may be used to extend the default API product profile with customer-specific metadata. Up to 17 attributes can be specified. |
| `--description` | DESCRIPTION |  | Overview of the API product. Include key information about the API product that is not captured by other fields. |
| `--display-name` | DISPLAY_NAME |  | Name to be displayed in the UI or developer portal to developers registering for API access. |
| `--manual-approval` |  |  | Require manual approval of developer requests to access this API product before their consumer keys can be used. If unset, the consumer key is generated in an "approved" state and can be used immediately. |
| `--oauth-scopes` | [SCOPE,...] |  | Comma-separated list of OAuth scopes that are validated at runtime. Apigee validates that the scopes in any access token presented match the scopes defined in the OAuth policy assoicated with the API product. |


**Examples:**
```bash
To create a basic API product in the active Cloud Platform project by
answering interactive prompts, run:

    $ gcloud apigee products create

To create an API product that publicly exposes all API proxies deployed to
the prod environment, run:

    $ gcloud apigee products create kitchen-sink --environments=prod \
      --all-proxies --public-access

To require manual approval of developers before they can access the new API
product, run:

    $ gcloud apigee products create kitchen-sink --environments=prod \
      --all-proxies --public-access --manual-approval

To hide the new API product while still making it accessible to developers,
run:

    $ gcloud apigee products create kitchen-sink --environments=prod \
      --all-proxies --private-access

To restrict the new API product to internal users only, run:

    $ gcloud apigee products create kitchen-sink --environments=prod \
      --all-proxies --internal-access

To expose all API proxies that are deployed to a URI fragment beginning
with /v1 or /v0, run:

    $ gcloud apigee products create legacy --all-environments \
      --resources="/v0/**#/v1/**" --public-access

To expose a few specific API proxies on all URI paths where they're
deployed, run:

    $ gcloud apigee products create consumer --environments=prod \
      --apis=menu,cart,delivery-tracker --public-access

To expose only those API calls that match both a set of API proxies and a
set of API resources, run:

    $ gcloud apigee products create legacy-consumer \
      --environments=prod --apis=menu,cart,delivery-tracker \
      --resources="/v0/**#/v1/**" --public-access

To impose a quota of 50 calls per half-hour on a new all-inclusive API
product, and output the new API product as a JSON object, run:

    $ gcloud apigee products create kitchen-sink --environments=prod \
      --all-proxies --public-access --quota=50 --quota-interval=30 \
      --quota-unit=minute --format=json

To specify a human-friendly display name and description for the product,
run:

    $ gcloud apigee products create consumer --environments=prod \
      --apis=menu,cart,delivery-tracker --public-access \
      --display-name="Consumer APIs" \
      --description="APIs for the consumer side of the delivery \
    network: ordering food and tracking deliveries."
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/products/create)

---
### `gcloud apigee products delete`

Delete an Apigee API product

Delete an Apigee API product.

**Synopsis:**
```
gcloud apigee products delete (PRODUCT : --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
API product resource - API product to be deleted. To get a list of
available API products, run:

    $ gcloud apigee products list

    The arguments in this group can be used to specify the attributes of this resource.

This must be specified.

  PRODUCT
     ID of the API product or fully qualified identifier for the API
     product.

     To set the product attribute:
     + provide the argument PRODUCT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the API product. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument PRODUCT on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Examples:**
```bash
To delete an API product called product-name from the active Cloud Platform
project, run:

    $ gcloud apigee products delete product-name

To delete an API product called other-product from an Apigee organization
called org-name, run:

    $ gcloud apigee products delete other-product --organization=org-name
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/products/delete)

---
### `gcloud apigee products describe`

Describe an Apigee API product

Describe an Apigee API product.

**Synopsis:**
```
gcloud apigee products describe (PRODUCT : --organization=ORGANIZATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
API product resource - API product to be described. To get a list of
available API products, run:

    $ gcloud apigee products list

    The arguments in this group can be used to specify the attributes of this resource.

This must be specified.

  PRODUCT
     ID of the API product or fully qualified identifier for the API
     product.

     To set the product attribute:
     + provide the argument PRODUCT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the API product. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument PRODUCT on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Examples:**
```bash
To describe an API product called product-name in the active Cloud Platform
project, run:

    $ gcloud apigee products describe product-name

To describe an API product called other-product in an Apigee organization
called org-name, run:

    $ gcloud apigee products describe other-product \
      --organization=org-name

To describe an API product called product-name as a JSON object, run:

    $ gcloud apigee products describe product-name --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/products/describe)

---
### `gcloud apigee products list`

List Apigee API products

List Apigee API products.

**Synopsis:**
```
gcloud apigee products list [--organization=ORGANIZATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[organization will be used. This represents a Cloud resource.]_ ID of the organization or fully qualified identifier for the organization. To set the organization attribute: + provide the argument --organization on the command line; + set the property [project] or provide the argument [--project] on the command line, using a Cloud Platform project with an associated Apigee organization. |


**Examples:**
```bash
To list all API products for the active Cloud Platform project, run:

    $ gcloud apigee products list

To get a JSON array of all the API products in an organization named
my-org, run:

    $ gcloud apigee products list --organization=my-org --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/products/list)

---
### `gcloud apigee products update`

Update an existing Apigee API product

Update an existing Apigee API product.

gcloud apigee products update applies a set of modifications to an existing
API product.

To create a new API product, run:

    $ gcloud apigee products create

**Synopsis:**
```
gcloud apigee products update (PRODUCT : --organization=ORGANIZATION)
    [--display-name=SET_DISPLAYNAME]
    [--all-apis | --add-api=[API,...] --remove-api=[API,...]]
    [--all-environments | --add-environment=[ENVIRONMENT,...]
      --remove-environment=[ENVIRONMENT,...]]
    [--all-resources
      | --add-resource=[RESOURCE#...] --remove-resource=[RESOURCE#...]]
    [--automatic-approval | --manual-approval]
    [--clear-attributes
      | --add-attribute=[NAME=VALUE,...] --remove-attribute=[NAME,...]]
    [--clear-description | --description=SET_DESCRIPTION]
    [--clear-oauth-scopes | --add-oauth-scope=[OAUTH-SCOPE,...]
      --remove-oauth-scope=[OAUTH-SCOPE,...]]
    [--clear-quota | --quota=QUOTA
      --quota-interval=QUOTA_INTERVAL --quota-unit=QUOTA_UNIT]
    [--internal-access | --private-access | --public-access]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
API product resource - API product to be updated. To get a list of
available API products, run:

    $ gcloud apigee products list

    The arguments in this group can be used to specify the attributes of this resource.

This must be specified.

  PRODUCT
     ID of the API product or fully qualified identifier for the API
     product.

     To set the product attribute:
     + provide the argument PRODUCT on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the API product. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument PRODUCT on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--display-name` | SET_DISPLAYNAME |  | Name to be displayed in the UI or developer portal to developers registering for API access. |


**Examples:**
```bash
To update the display name of the API product with the internal name
my-prod, run:

    $ gcloud apigee products update my-prod \
      --display-name="Example Project"

To update the description of the API product, run:

    $ gcloud apigee products update my-prod \
      --description="This API is famous for appearing in a YouTube \
    video."

To remove the API product's description, run:

    $ gcloud apigee products update my-prod --clear-description

To remove manual approval requirements from the API and change its access
level to public, run:

    $ gcloud apigee products update my-prod --public-access \
      --automatic-approval

To impose a quota of 45 calls per minute per application on the API
product, run:

    $ gcloud apigee products update my-prod --quota=45 \
      --quota-interval=1 --quota-unit=minute

To remove a quota on the API product and switch it to unlisted access with
manual approval, run:

    $ gcloud apigee products update my-prod --manual-approval \
      --private-access --clear-quota

To set the API product's custom attribute foo to the value bar, updating
that attribute if it exists and creating it if it doesn't, and remove the
attribute baz if it exists, run:

    $ gcloud apigee products update my-prod --add-attribute="foo=bar" \
      --remove-attribute=baz

To update the list of API proxies included in the API product, run:

    $ gcloud apigee products update my-prod --add-api=NEW_ONE,NEW_TWO \
      --remove-api=OLD_ONE,OLD_TWO

To switch the API product to including all test environment APIs no matter
what API proxy or resource they expose, run:

    $ gcloud apigee products update my-prod --add-environment=test \
      --all-apis --all-resources

To update the list of API resources included in the API product, and output
the updated API product as a JSON object, run:

    $ gcloud apigee products update my-prod \
      --add-resource="NEW_ONE#NEW_TWO" \
      --remove-resource="OLD_ONE#OLD_TWO" --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/products/update)

---