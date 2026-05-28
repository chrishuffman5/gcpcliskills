# gcloud app (top-level commands)

### `gcloud app browse`

Open the current app in a web browser

Open the current app in a web browser.

**Synopsis:**
```
gcloud app browse [--no-launch-browser] [--service=SERVICE, -s SERVICE]
    [--version=VERSION, -v VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--launch-browser` |  |  | Launch a browser if possible. When disabled, only displays the URL. Enabled by default, use --no-launch-browser to disable. |
| `--service` | SERVICE, -s SERVICE |  | The service that should be opened. If not specified, use the default service. May be used in conjunction with --version. |
| `--version` | VERSION, -v VERSION |  | The version of the app that should be opened. If not specified, choose a version based on the service's traffic split. |


**Examples:**
```bash
To open the default service, run:

    $ gcloud app browse

To open a specific service, run:

    $ gcloud app browse --service="myService"

To open a specific version, run:

    $ gcloud app browse --service="myService" --version="v1"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/browse)

---
### `gcloud app create`

Create an App Engine app within the current Google Cloud Project

Create an App Engine app within the current Google Cloud Project.

**Synopsis:**
```
gcloud app create [--region=REGION] [--service-account=SERVICE_ACCOUNT]
    [--ssl-policy=SSL_POLICY] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--region` | REGION |  | The region to create the app within. Use gcloud app regions list to list available regions. If not provided, select region interactively. |
| `--service-account` | SERVICE_ACCOUNT |  | The app-level default service account to create the app with. Note that you can specify a distinct service account for each App Engine version with gcloud app deploy --service-account. However if you do not specify a version-level service account, this default will be used. If this parameter is not provided for app creation, the app-level default will be set to be the out-of-box App Engine Default Service Account, https://cloud.google.com/appengine/docs/standard/python3/service-account outlines the limitation of that service account. |
| `--ssl-policy` | one of: TLS_VERSION_1_0, TLS_VERSION_1_2 |  | The app-level SSL policy to create the app with. SSL_POLICY must be one of: TLS_VERSION_1_0, TLS_VERSION_1_2. |


**Examples:**
```bash
To create an app with region chosen interactively, run:

    $ gcloud app create

To create an app in the us-central region, run:

    $ gcloud app create --region=us-central

To create an app that with a user-managed service account, run:

    $ gcloud app create --service-account=SERVICE_ACCOUNT

To create an app with minimum SSL policy allowing TLS 1.2 and above, run:

    $ gcloud app create --ssl-policy=TLS_VERSION_1_2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/create)

---
### `gcloud app deploy`

Deploy the local code and/or configuration of your app to App Engine

This command is used to deploy both code and configuration to the App
Engine server. As an input it takes one or more DEPLOYABLES that should be
uploaded. A DEPLOYABLE can be a service's .yaml file or a configuration's
.yaml file (for more information about configuration files specific to your
App Engine environment, refer to
https://cloud.google.com/appengine/docs/standard/configuration-files or
https://cloud.google.com/appengine/docs/flexible/configuration-files).
Note, for Java 8 Standard apps or Java 11/17/21 Standard apps using bundled
services, you must add the path to the appengine-web.xml file inside the
WEB-INF directory. gcloud app deploy skips files specified in the
.gcloudignore file (see gcloud topic gcloudignore for more information).
For Java 11 Standard, you can either use the yaml file, a Maven pom.xml, or
a Gradle build.gradle. Alternatively, if the application is a single
self-contained jar, you can give the path to the jar and a simple service
configuration will be generated. You can deploy Java 11 Maven source
projects by specifying the location of your project's pom.xml file, and it
will be built and deployed using App Engine Buildpacks.

**Synopsis:**
```
gcloud app deploy [DEPLOYABLES ...] [--appyaml=APPYAML] [--bucket=BUCKET]
    [--no-cache] [--ignore-file=IGNORE_FILE] [--image-url=IMAGE_URL]
    [--no-promote] [--service-account=SERVICE_ACCOUNT]
    [--no-stop-previous-version] [--version=VERSION, -v VERSION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[DEPLOYABLES ...]
   The yaml files for the services or configurations you want to deploy.
   If not given, defaults to app.yaml in the current directory. If that is
   not found, attempts to automatically generate necessary configuration
   files (such as app.yaml) in the current directory.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--appyaml` | APPYAML |  | Deploy with a specific app.yaml that will replace the one defined in the DEPLOYABLE. |
| `--bucket` | BUCKET |  | The Google Cloud Storage bucket used to stage files associated with the deployment. If this argument is not specified, the application's default code bucket is used. |
| `--cache` |  |  | Enable caching mechanisms involved in the deployment process, particularly in the build step. Enabled by default, use --no-cache to disable. |
| `--ignore-file` | IGNORE_FILE |  | Override the .gcloudignore file and use the specified file instead. |
| `--image-url` | IMAGE_URL |  | (App Engine flexible environment only.) Deploy with a specific Docker image. Docker url must be from one of the valid Artifact Registry hostnames. |
| `--promote` |  |  | Promote the deployed version to receive all traffic. Overrides the default app/promote_by_default property value for this command invocation. Use --no-promote to disable. |
| `--service-account` | SERVICE_ACCOUNT |  | The service account that this deployed version will run as. If this argument is not specified, the App Engine default service account will be used for your current deployed version. |
| `--stop-previous-version` |  |  | Stop the previously running version when deploying a new version that receives all traffic. Note that if the version is running on an instance of an auto-scaled service in the App Engine Standard environment, using --stop-previous-version will not work and the previous version will continue to run because auto-scaled service instances are always running. Overrides the default app/stop_previous_version property value for this command invocation. Use --no-stop-previous-version to disable. |
| `--version` | VERSION, -v VERSION |  | The version of the app that will be created or replaced by this deployment. If you do not specify a version, one will be generated for you. |


**Examples:**
```bash
To deploy a single service, run:

    $ gcloud app deploy ~/my_app/app.yaml

To deploy an App Engine Standard Java8 service or a Java11 service using
bundled services, run:

    $ gcloud app deploy ~/my_app/WEB-INF/appengine-web.xml

To deploy an App Engine Standard Java11 single jar, run:

    $ gcloud app deploy ~/my_app/my_jar.jar

To deploy an App Engine Standard Java11 Maven source project, run:

    $ gcloud app deploy ~/my_app/pom.xml

To deploy an App Engine Standard Java11 Gradle source project, run:

    $ gcloud app deploy ~/my_app/build.gradle

By default, the service is deployed to the current project configured via:

    $ gcloud config set core/project PROJECT

To override this value for a single deployment, use the --project flag:

    $ gcloud app deploy ~/my_app/app.yaml --project=PROJECT

To deploy multiple services, run:

    $ gcloud app deploy ~/my_app/app.yaml ~/my_app/another_service.yaml

To change the default --promote behavior for your current environment, run:

    $ gcloud config set app/promote_by_default false

To deploy a service that will run as a service account, run:

    $ gcloud app deploy ~/my_app/app.yaml \
        --service-account=SERVICE_ACCOUNT
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/deploy)

---
### `gcloud app describe`

Display all data about an existing service

Display all data about an existing service.

**Synopsis:**
```
gcloud app describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To show all the data about the current application, run

    $ gcloud app describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/describe)

---
### `gcloud app open-console`

Open the App Engine dashboard, or log viewer, in a web browser

Open the App Engine dashboard, or log viewer, in a web browser.

**Synopsis:**
```
gcloud app open-console [--logs, -l] [--service=SERVICE, -s SERVICE]
    [--version=VERSION, -v VERSION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--logs, -l` |  |  | Open the log viewer instead of the App Engine dashboard. |
| `--service` | SERVICE, -s SERVICE |  | The service to consider. If not specified, use the default service. |
| `--version` | VERSION, -v VERSION |  | The version to consider. If not specified, all versions for the given service are considered. |


**Examples:**
```bash
Open the App Engine dashboard for the default service:

    $ gcloud app open-console

Open the service specific dashboard view:

    $ gcloud app open-console --service="myService"

Open the version specific dashboard view:

    $ gcloud app open-console --service="myService" --version="v1"

Open the log viewer for the default service:

    $ gcloud app open-console --logs
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/open-console)

---
### `gcloud app update`

Updates an App Engine application

This command is used to update settings on an app engine application.

**Synopsis:**
```
gcloud app update [--service-account=SERVICE_ACCOUNT]
    [--[no-]split-health-checks] [--ssl-policy=SSL_POLICY]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--service-account` | SERVICE_ACCOUNT |  | The app-level default service account to update the app with. |
| `--[no-]split-health-checks` |  |  | Enables/disables split health checks by default on new deployments. Use --split-health-checks to enable and --no-split-health-checks to disable. |
| `--ssl-policy` | one of: TLS_VERSION_1_0, TLS_VERSION_1_2 |  | The app-level SSL policy to update the app with. SSL_POLICY must be one of: TLS_VERSION_1_0, TLS_VERSION_1_2. |


**Examples:**
```bash
To enable split health checks on an application:

    $ gcloud app update --split-health-checks

To update the app-level service account on an application:

    $ gcloud app update --service-account=SERVICE_ACCOUNT

To update the app-level minimum SSL policy of the application:

    $ gcloud app update --ssl-policy=TLS_VERSION_1_2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/app/update)

---