# gcloud observability scopes

manage Scope resources

### `gcloud observability scopes describe`

Describe scopes

Describe a scope

**Synopsis:**
```
gcloud observability scopes describe (SCOPE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - Name of the resource. The format is:

    projects/{project}/locations/{location}/scopes/{scope}

The {location} field must be set to global. The {scope} field must be set
to Default. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the scope resource.

     To set the location attribute:
     + provide the argument scope on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe the scope, run:

    $ gcloud observability scopes describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/observability/scopes/describe)

---
### `gcloud observability scopes update`

Update scopes

Update a scope

**Synopsis:**
```
gcloud observability scopes update (SCOPE : --location=LOCATION)
    [--log-scope=LOG_SCOPE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - Identifier. Name of the resource. The format is:

    projects/{project}/locations/{location}/scopes/{scope}

The {location} field must be set to global. The {scope} field must be set
to Default. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location id of the scope resource.

     To set the location attribute:
     + provide the argument scope on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--log-scope` | LOG_SCOPE |  | The full resource name of the LogScope. For example: //logging.googleapis.com/projects/myproject/locations/global/logScopes/my-log-scope |


**Examples:**
```bash
To update the scope, run:

    $ gcloud observability scopes update
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/observability/scopes/update)

---