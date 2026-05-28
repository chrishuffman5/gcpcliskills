# gcloud apigee deployments

manage deployments of Apigee API proxies in runtime environments

### `gcloud apigee deployments describe`

Describe an Apigee API proxy deployment

Describe an Apigee API proxy deployment.

gcloud apigee deployments describe retrieves the status of a specific API
proxy's deployment to a specific environment.

**Synopsis:**
```
gcloud apigee deployments describe
    [[REVISION]
      --api=API --environment=ENVIRONMENT --organization=ORGANIZATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
 Revision resource - API proxy revision and environment of the deployment
 to be described.

 To get a list of deployed proxies and their environments, run:

     $ gcloud apigee deployments list

 REVISION can either be a positive revision number, or the special value
 auto, which will choose whichever revision of API is currently deployed in
 ENVIRONMENT, or return an error if more than one revision is deployed.

If REVISION is unspecified, the default is auto.

    The arguments in this group can be used to specify the attributes of this resource.

     [REVISION]
        ID of the revision or fully qualified identifier for the revision.

        To set the revision attribute:
        + provide the argument REVISION on the command line;
        + leave the argument unspecified for it to be chosen
          automatically.

     --api=API
        Deployed API proxy.

        To set the api attribute:
        + provide the argument REVISION on the command line with a fully
          specified name;
        + leave the argument unspecified for it to be chosen
          automatically with a fully specified name;
        + provide the argument --api on the command line.

     --environment=ENVIRONMENT
        Environment in which the proxy was deployed.

        To set the environment attribute:
        + provide the argument REVISION on the command line with a fully
          specified name;
        + leave the argument unspecified for it to be chosen
          automatically with a fully specified name;
        + provide the argument --environment on the command line.

     --organization=ORGANIZATION
        Apigee Organization of the proxy and environment. If unspecified,
        the Cloud Platform project's associated organization will be used.

        To set the organization attribute:
        + provide the argument REVISION on the command line with a fully
          specified name;
        + leave the argument unspecified for it to be chosen
          automatically with a fully specified name;
        + provide the argument --organization on the command line;
        + set the property [project] or provide the argument [--project]
          on the command line, using a Cloud Platform project with an
          associated Apigee organization.
```

**Examples:**
```bash
To get the status of a deployment in the active Cloud Platform project,
which deploys my-proxy into the prod environment, run:

    $ gcloud apigee deployments describe --api=my-proxy \
      --environment=prod

To get the status of that deployment as a JSON object, run:

    $ gcloud apigee deployments describe --api=my-proxy \
      --environment=prod --format=json

To get the status of a deployment in an organization called my-org, which
deploys version 3 of the proxy my-proxy into the test environment, run:

    $ gcloud apigee deployments describe 3 --organization=my-org \
      --environment=test --api=my-proxy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/deployments/describe)

---
### `gcloud apigee deployments list`

List Apigee API proxy deployments

List Apigee API proxy deployments.

gcloud apigee deployments list lists deployments of API proxies, optionally
filtered by environment, proxy name, proxy revision, or a combination of
these.

**Synopsis:**
```
gcloud apigee deployments list
    [--api=API --environment=ENVIRONMENT
      --organization=ORGANIZATION --revision=REVISION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--api` | API |  | _[used to specify the attributes of this resource.]_ The API proxy whose deployments should be listed. If not provided, all proxies will be listed. To get a list of existing API proxies, run gcloud apigee apis list. To set the api attribute: + provide the argument --revision on the command line with a fully specified name; + leave the argument unspecified for it to be chosen automatically with a fully specified name; + provide the argument --api on the command line; + leave the argument unspecified for it to be chosen automatically. |
| `--environment` | ENVIRONMENT |  | _[used to specify the attributes of this resource.]_ The environment whose deployments should be listed. If not provided, all environments will be listed. To get a list of available environments, run gcloud apigee environments list. To set the environment attribute: + provide the argument --revision on the command line with a fully specified name; + leave the argument unspecified for it to be chosen automatically with a fully specified name; + provide the argument --environment on the command line; + leave the argument unspecified for it to be chosen automatically. |
| `--organization` | ORGANIZATION |  | _[used to specify the attributes of this resource.]_ The organization whose deployments should be listed.If unspecified, the Cloud Platform project's associated organization will be used. To set the organization attribute: + provide the argument --revision on the command line with a fully specified name; + leave the argument unspecified for it to be chosen automatically with a fully specified name; + provide the argument --organization on the command line; + set the property [project] or provide the argument [--project] on the command line, using a Cloud Platform project with an associated Apigee organization. |
| `--revision` | REVISION |  | _[used to specify the attributes of this resource.]_ ID of the revision or fully qualified identifier for the revision. To set the revision attribute: + provide the argument --revision on the command line; + leave the argument unspecified for it to be chosen automatically. |


**Examples:**
```bash
To list all deployments for the active Cloud Platform project, run:

    $ gcloud apigee deployments list

To list all deployments in an Apigee organization called my-org, run:

    $ gcloud apigee deployments list --organization=my-org

To list all deployments of an API proxy called my-proxy in the active Cloud
Platform project, run:

    $ gcloud apigee deployments list --api=my-proxy

To list all deployments to the test environment of the active Cloud
Platform project, formatted as a JSON array, run:

    $ gcloud apigee deployments list --environment=test --format=json

To list all deployments of my-proxy to the test environment in an Apigee
organization called my-org, run:

    $ gcloud apigee deployments list --organization=my-org \
      --api=my-proxy --environment=test
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apigee/deployments/list)

---