# gcloud network-services meshes

manage Network Services Meshes

### `gcloud network-services meshes delete`

Delete a mesh

Delete the specified mesh.

**Synopsis:**
```
gcloud network-services meshes delete (MESH : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mesh resource - Name of the mesh you want to delete. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument mesh on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESH
     ID of the mesh or fully qualified identifier for the mesh.

     To set the mesh attribute:
     + provide the argument mesh on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument mesh on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a mesh named 'my-mesh', run:

    $ gcloud network-services meshes delete my-mesh --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/meshes/delete)

---
### `gcloud network-services meshes describe`

Describe a mesh

Show details of a mesh.

**Synopsis:**
```
gcloud network-services meshes describe (MESH : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mesh resource - Name of the mesh to be described. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument mesh on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESH
     ID of the mesh or fully qualified identifier for the mesh.

     To set the mesh attribute:
     + provide the argument mesh on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument mesh on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
Show details about a mesh named 'my-mesh'.

    $ gcloud network-services meshes describe my-mesh --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/meshes/describe)

---
### `gcloud network-services meshes export`

Export a mesh

Export a mesh.

**Synopsis:**
```
gcloud network-services meshes export (MESH : --location=LOCATION)
    [--destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mesh resource - Name of the mesh to export. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument mesh on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESH
     ID of the mesh or fully qualified identifier for the mesh.

     To set the mesh attribute:
     + provide the argument mesh on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument mesh on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--destination` | DESTINATION |  | Path to a YAML file where the configuration will be exported. The exported data will not contain any output-only fields. Alternatively, you may omit this flag to write to standard output. For a schema describing the export/import format, see $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... |


**Examples:**
```bash
To export a mesh named 'my-mesh' to a YAML file, run:

    $ gcloud network-services meshes export my-mesh \
        --destination=my-mesh.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/meshes/export)

---
### `gcloud network-services meshes import`

Import a mesh

Import a mesh.

**Synopsis:**
```
gcloud network-services meshes import (MESH : --location=LOCATION)
    [--async] [--source=SOURCE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Mesh resource - Name of the mesh to import. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument mesh on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MESH
     ID of the mesh or fully qualified identifier for the mesh.

     To set the mesh attribute:
     + provide the argument mesh on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location Id.

     To set the location attribute:
     + provide the argument mesh on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--source` | SOURCE |  | Path to a YAML file containing the configuration export data. The YAML file must not contain any output-only fields. Alternatively, you may omit this flag to read from standard input. For a schema describing the export/import format, see: $CLOUDSDKROOT/lib/googlecloudsdk/schemas/... $CLOUDSDKROOT is can be obtained with the following command: $ gcloud info --format='value(installation.sdk_root)' |


**Examples:**
```bash
To import a mesh named 'my-mesh' from a YAML file, run:

    $ gcloud network-services meshes import my-mesh \
        --source=my-mesh.yaml --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/meshes/import)

---
### `gcloud network-services meshes list`

List meshes

List all meshes in the specified location of the current project.

**Synopsis:**
```
gcloud network-services meshes list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list meshes in the current project, run:

    $ gcloud network-services meshes list --location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-services/meshes/list)

---