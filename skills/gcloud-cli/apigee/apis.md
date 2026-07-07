# gcloud apigee apis

manage Apigee API proxies

### `gcloud apigee apis deploy`

Deploy an API proxy to an environment

Deploy an API proxy to an environment.

gcloud apigee apis deploy installs an API proxy revision in an Apigee
runtime environment.

By default, the API proxy's base path must not already be in use by a
deployed proxy in the target environment. To allow Apigee to undeploy any
conflicting API proxy as part of the deployment, use the --override
command.

Once a particular revision of an API proxy has been deployed, that revision
can no longer be modified. Any updates to the API proxy must be saved as a
new revision.

**Synopsis:**
```
gcloud apigee apis deploy
    [[REVISION]
      --api=API --environment=ENVIRONMENT --organization=ORGANIZATION]
    [--override] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - API proxy revision to be deployed and environment in
which to deploy it. Revisions can either be a positive revision number, or
the special value latest, which will deploy the latest revision of the API
proxy. If revision is unspecified, the default is latest. The arguments in
this group can be used to specify the attributes of this resource.

  [REVISION]
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument REVISION on the command line;
     + leave the argument unspecified for it to be chosen automatically.

  --api=API
     API proxy to be deployed. To get a list of available API proxies, run
     gcloud apigee apis list.

     To set the api attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + leave the argument unspecified for it to be chosen automatically
       with a fully specified name;
     + provide the argument --api on the command line.

  --environment=ENVIRONMENT
     Environment in which to deploy the API proxy. To get a list of
     available environments, run gcloud apigee environments list.

     To set the environment attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + leave the argument unspecified for it to be chosen automatically
       with a fully specified name;
     + provide the argument --environment on the command line.

  --organization=ORGANIZATION
     Apigee organization of the proxy and environment. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + leave the argument unspecified for it to be chosen automatically
       with a fully specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--override` |  |  | Force the deployment of the new revision, overriding any currently deployed revision that would conflict with it. If an existing API proxy revision is deployed, set this flag to ensure seamless deployment with zero downtime. In this case, the existing revision remains deployed until the new revision is fully deployed. If unset, gcloud apigee apis deploy will fail unless all conflicting API proxies are first undeployed from the environment. To do this, run gcloud apigee apis undeploy on the conflicting deployment. |


**Examples:**
```bash
To deploy the latest revision of the API proxy named demo to the test
environment, given that the API proxy and environment's matching Cloud
Platform project has been set in gcloud settings, run:

    $ gcloud apigee apis deploy --environment=test --api=demo

To deploy revision 3 of that proxy, owned by an organization named my-org,
run, and replace any conflicting deployment that might already exist, run:

    $ gcloud apigee apis deploy 3 --organization=my-org \
        --environment=test --api=demo --override

To deploy that proxy and print the resulting deployment as a JSON object,
run:

    $ gcloud apigee apis deploy 3 --organization=my-org \
        --environment=test --api=demo --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/apis/deploy)

---
### `gcloud apigee apis describe`

Describe an Apigee API proxy

Describe an Apigee API proxy.

gcloud apigee apis describe shows metadata about an API proxy and its
revisions.

**Synopsis:**
```
gcloud apigee apis describe (API : --organization=ORGANIZATION) [--verbose]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
API proxy resource - API proxy to be described. To get a list of available
API proxies, run gcloud apigee apis list. The arguments in this group can
be used to specify the attributes of this resource.

This must be specified.

  API
     ID of the API proxy or fully qualified identifier for the API proxy.

     To set the api attribute:
     + provide the argument API on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --organization=ORGANIZATION
     Apigee organization containing the API proxy. If unspecified, the
     Cloud Platform project's associated organization will be used.

     To set the organization attribute:
     + provide the argument API on the command line with a fully
       specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--verbose` |  |  | Include proxy revision info in the description. |


**Examples:**
```bash
To describe an API proxy called proxy-name given that its matching Cloud
Platform project has been set in gcloud settings, run:

    $ gcloud apigee apis describe proxy-name

To describe an API proxy called other-proxy-name in another project whose
Apigee organization is named org-name, run:

    $ gcloud apigee apis describe other-proxy-name \
      --organization=org-name

To describe an API proxy called proxy-name and include details on its
revisions, run:

    $ gcloud apigee apis describe proxy-name --verbose

To describe an API proxy called proxy-name as a JSON object, run:

    $ gcloud apigee apis describe proxy-name --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/apis/describe)

---
### `gcloud apigee apis list`

List Apigee API proxies

List Apigee API proxies.

**Synopsis:**
```
gcloud apigee apis list [--organization=ORGANIZATION] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION |  | _[organization will be used. This represents a Cloud resource.]_ ID of the organization or fully qualified identifier for the organization. To set the organization attribute: + provide the argument --organization on the command line; + set the property [project] or provide the argument [--project] on the command line, using a Cloud Platform project with an associated Apigee organization. |


**Examples:**
```bash
To list all API proxies for the active Cloud Platform project, run:

    $ gcloud apigee apis list

To list all API proxies in an organization called my-org, run:

    $ gcloud apigee apis list --organization=my-org

To list all API proxies in an organization called my-org, formatted as a
JSON array, run:

    $ gcloud apigee apis list --organization=my-org --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/apis/list)

---
### `gcloud apigee apis undeploy`

Undeploy an Apigee API proxy from an environment

Undeploy an Apigee API proxy from an environment.

**Synopsis:**
```
gcloud apigee apis undeploy
    [[REVISION]
      --api=API --environment=ENVIRONMENT --organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Revision resource - API proxy revision to be undeployed and environment
from which it should be removed.

Revisions can either be a positive revision number, or the special value
auto, which will undeploy whatever revision is currently deployed. If
revision is unspecified, the default is auto. The arguments in this group
can be used to specify the attributes of this resource.

  [REVISION]
     ID of the revision or fully qualified identifier for the revision.

     To set the revision attribute:
     + provide the argument REVISION on the command line;
     + leave the argument unspecified for it to be chosen automatically.

  --api=API
     API proxy to be undeployed. Must currently be deployed. To get a list
     of available deployed proxies, run gcloud apigee deployments list
     --environment=ENV.

     To set the api attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + leave the argument unspecified for it to be chosen automatically
       with a fully specified name;
     + provide the argument --api on the command line.

  --environment=ENVIRONMENT
     Environment from which to undeploy the API proxy. To get a list of
     available environments, run gcloud apigee environments list.

     To set the environment attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + leave the argument unspecified for it to be chosen automatically
       with a fully specified name;
     + provide the argument --environment on the command line.

  --organization=ORGANIZATION
     Apigee organization of the proxy and environment.

     To set the organization attribute:
     + provide the argument REVISION on the command line with a fully
       specified name;
     + leave the argument unspecified for it to be chosen automatically
       with a fully specified name;
     + provide the argument --organization on the command line;
     + set the property [project] or provide the argument [--project] on
       the command line, using a Cloud Platform project with an associated
       Apigee organization.
```

**Examples:**
```bash
To undeploy an API proxy called my-api from the test environment of the
active Cloud Platform project, run:

    $ gcloud apigee apis undeploy --environment=test --api=my-api

To undeploy revision 3 of an my-api from the test environment of the
organization named test-org, run:

    $ gcloud apigee apis undeploy 3 --organization=test-org \
        --environment=test --api=my-api
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/apis/undeploy)

---