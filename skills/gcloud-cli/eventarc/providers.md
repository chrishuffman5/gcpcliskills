# gcloud eventarc providers

explore event providers available in Eventarc

### `gcloud eventarc providers describe`

Describe an Eventarc event provider

Describe an Eventarc event provider.

**Synopsis:**
```
gcloud eventarc providers describe (PROVIDER : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Provider resource - The event provider to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument provider on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  PROVIDER
     ID of the provider or fully qualified identifier for the provider.

     To set the provider attribute:
     + provide the argument provider on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the Eventarc provider, which should be either global
     or one of the supported regions. Alternatively, set the
     [eventarc/location] property.

     To set the location attribute:
     + provide the argument provider on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property eventarc/location.
```

**Examples:**
```bash
To describe the provider my-provider, run:

    $ gcloud eventarc providers describe my-provider
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/providers/describe)

---
### `gcloud eventarc providers list`

List event providers available in Eventarc

List event providers available in Eventarc.

**Synopsis:**
```
gcloud eventarc providers list [--location=LOCATION] [--name=NAME]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + set the property eventarc/location; + use '-' location to aggregate results for all Eventarc locations. |
| `--name` | NAME |  | _[* set the property core/project.]_ A provider name (e.g. storage.googleapis.com) List results will be filtered on this provider. Only exact match of the provider name is supported. |


**Examples:**
```bash
To list all providers in location us-central1, run:

    $ gcloud eventarc providers list --location=us-central1

To list all providers in all locations, run:

    $ gcloud eventarc providers list --location=-

or

    $ gcloud eventarc providers list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/eventarc/providers/list)

---