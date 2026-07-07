# gcloud apihub addons

manage Addon resources

### `gcloud apihub addons describe`

Describe an Addon

Describe an addon.

**Synopsis:**
```
gcloud apihub addons describe (ADDON : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Addon resource - The name of the addon to get. Format:
projects/{project}/locations/{location}/addons/{addon} The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument addon on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDON
     ID of the addon or fully qualified identifier for the addon.

     To set the addon attribute:
     + provide the argument addon on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the addon resource.

     To set the location attribute:
     + provide the argument addon on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe an addon with the ID my-addon, run:

    $ gcloud apihub addons describe my-addon --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/addons/describe)

---
### `gcloud apihub addons list`

List Addons

List addons.

**Synopsis:**
```
gcloud apihub addons list --location=LOCATION [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ Location resource - The parent resource where this addon will be created. Format: projects/{project}/locations/{location}. ID of the location or fully qualified identifier for the location. To set the location attribute: provide the argument --location on the command line. To set the project attribute: provide the argument --location on the command line with a fully specified name; provide the argument --project on the command line; set the property core/project. |

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--filter` | EXPRESSION |  | Apply a Boolean filter EXPRESSION to each resource item to be listed. If the expression evaluates True, then that item is listed. For more details and examples of filter expressions, run $ gcloud topic filters. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--limit` | LIMIT | unlimited | Maximum number of resources to list. The default is unlimited. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--page-size` | PAGE_SIZE | determined by service | Some services group resource list output into pages. This flag specifies the maximum number of resources per page. The default is determined by the service if it supports paging, otherwise it is unlimited (no paging). Paging may be applied before or after --filter and --limit depending on the service. |
| `--sort-by` | [FIELD,...] | ascending | Comma-separated list of resource field key names to sort by. The default order is ascending. Prefix a field with "~" for descending order on that field. This flag interacts with other flags that are applied in this order: --flatten, --sort-by, --filter, --limit. |
| `--uri` |  |  | Print a list of resource URIs instead of the default output, and change the command output to a list of URIs. If this flag is used with --format, the formatting is applied on this URI list. To display URIs alongside other keys instead, use the uri() transform. |

**Examples:**
```bash
To list all addons in project my-project and location us-central1, run:

    $ gcloud apihub addons list --project=my-project \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/addons/list)

---
### `gcloud apihub addons manage-config`

Manage the Config of an Addon

Manage the config of an addon.

**Synopsis:**
```
gcloud apihub addons manage-config (ADDON : --location=LOCATION) [--async]
    [--[no-]all-data-addon-config-enabled
      | --gateway-plugin-addon-config-configs=[apigeeEdgeConfig=APIGEEEDGECONFIG],[apigeeOpdkConfig=APIGEEOPDKCONFIG],[apigeeXHybridConfig=APIGEEXHYBRIDCONFIG],[pluginInstance=PLUGININSTANCE]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Addon resource - The name of the addon for which the config is to be
managed. Format: projects/{project}/locations/{location}/addons/{addon}
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument addon on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ADDON
     ID of the addon or fully qualified identifier for the addon.

     To set the addon attribute:
     + provide the argument addon on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the addon resource.

     To set the location attribute:
     + provide the argument addon on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--[no-]all-data-addon-config-enabled` |  |  | _[At most one of these can be specified:]_ If true, the addon is enabled for all data in the API hub. Use --all-data-addon-config-enabled to enable and --no-all-data-addon-config-enabled to disable. |
| `--gateway-plugin-addon-config-configs` | [apigeeEdgeConfig=APIGEEEDGECONFIG],[apigeeOpdkConfig=APIGEEOPDKCONFIG],[apigeeXHybridConfig=APIGEEXHYBRIDCONFIG],[pluginInstance=PLUGININSTANCE] |  | _[At most one of these can be specified:]_ The list of gateway plugin configs for which the addon is enabled. Each gateway plugin config should have a unique plugin instance. Keys: apigeeEdgeConfig (configuration for Apigee Edge gateways), apigeeOpdkConfig (configuration for Apigee OPDK gateways), apigeeXHybridConfig (configuration for Apigee X and Apigee Hybrid gateways), pluginInstance (the name of the gateway plugin instance for which the config is to be specified). |

**Examples:**
```bash
To manage the config of an addon with the ID system-advanced-api-security,
run:

    $ gcloud apihub addons manage-config system-advanced-api-security \
        --gateway-plugin-addon-config-configs="pluginInstance=projects/my-project/locations/us-central1/plugins/system-apigee-x-and-hybrid/instances/my-instance-1,apigeeXHybridConfig={environmentFilter={allEnvironments=true}}" \
        --gateway-plugin-addon-config-configs="pluginInstance=projects/my-project/locations/us-central1/plugins/system-edge-public-cloud/instances/my-instance-2,apigeeEdgeConfig={environmentFilter={environments=['env1']}}" \
        --project=my-project --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/apihub/addons/manage-config)

---
