# gcloud network-services route-views

view Network Services Route Views

### `gcloud network-services route-views describe`

Route View for a Mesh or Gateway

Describe a Route Views for a Mesh or Gateway

**Synopsis:**
```
gcloud network-services route-views describe
    (--route-view=ROUTE_VIEW
      : --gateway=GATEWAY --location=LOCATION --mesh=MESH)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--route-view` | ROUTE_VIEW |  | _[This must be specified.]_ ID of the mesh_or_gateway_route_view or fully qualified identifier for the mesh_or_gateway_route_view. To set the route_view attribute: + provide the argument --route-view on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--gateway` | GATEWAY |  | _[This must be specified.]_ Parent Gateway of the mesh_or_gateway_route_view To set the gateway attribute: + provide the argument --route-view on the command line with a fully specified name; + provide the argument --gateway on the command line. Must be specified for resource of type [networkservices.projects.locations.gateways.routeViews]. |
| `--location` | LOCATION |  | _[This must be specified.]_ Location of the mesh_or_gateway_route_view To set the location attribute: + provide the argument --route-view on the command line with a fully specified name; + provide the argument --location on the command line. |
| `--mesh` | MESH |  | _[This must be specified.]_ Parent Mesh of the mesh_or_gateway_route_view To set the mesh attribute: + provide the argument --route-view on the command line with a fully specified name; + provide the argument --mesh on the command line. Must be specified for resource of type [networkservices.projects.locations.meshes.routeViews]. |


**Examples:**
```bash
Describe a Route Views for a Mesh

    $ gcloud network-services route-views describe \
        --project=$PROJECT_ID --location=$LOCATION --mesh mesh1 \
        --route-view $ROUTE_VIEW_ID
    $ gcloud network-services route-views describe \
        --route-view=projects/-/locations/-/meshes/-/routeViews/\
    $ROUTE_VIEW_ID

Describe a Route Views for a Gateway

    $ gcloud network-services route-views describe \
        --project=$PROJECT_ID --location=$LOCATION --gateway gateway1 \
        --route-view $ROUTE_VIEW_ID
    $ gcloud network-services route-views describe \
        --route-view=projects/-/locations/-/gateways/-/routeViews/\
    $ROUTE_VIEW_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/route-views/describe)

---
### `gcloud network-services route-views list`

Route View for a Mesh or Gateway

List all Route Views for a Mesh or Gateway

**Synopsis:**
```
gcloud network-services route-views list (--gateway=GATEWAY | --mesh=MESH)
    [--location=LOCATION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gateway` | GATEWAY |  | _[+ provide the argument --location on the command line.]_ ID of the gateway or fully qualified identifier for the gateway. To set the gateway attribute: - provide the argument --gateway on the command line. |
| `--mesh` | MESH |  | _[+ provide the argument --location on the command line.]_ ID of the mesh or fully qualified identifier for the mesh. To set the mesh attribute: - provide the argument --mesh on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
List Route Views for a mesh.

    $ gcloud network-services route-views list \
        --mesh projects/-/locations/-/meshes/mesh1
    $ gcloud network-services route-views list --project $PROJECT \
        --location $LOCATION \
        --mesh projects/-/locations/-/meshes/mesh1 List Route Views \
        for a gateway.

    $ gcloud network-services route-views list \
        --gateway projects/-/locations/-/gateways/gateway1
    $ gcloud network-services route-views list --project $PROJECT \
        --location $LOCATION \
        --gateway projects/-/locations/-/gateways/gateway1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/route-views/list)

---