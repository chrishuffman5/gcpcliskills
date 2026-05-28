# gcloud functions event-types

list types of events that can be a trigger for a Google Cloud Function

### `gcloud functions event-types list`

List types of events that can be a trigger for a Google Cloud Function

gcloud functions event-types list displays types of events that can be a
trigger for a Google Cloud Function.

  o For an event type, EVENT_TYPE_DEFAULT marks whether the given event
    type is the default (in which case the --trigger-event flag may be
    omitted).
  o For a resource, RESOURCE_OPTIONAL marks whether the resource has a
    corresponding default value (in which case the --trigger-resource flag
    may be omitted).

**Synopsis:**
```
gcloud functions event-types list [--gen2] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gen2` |  |  | If enabled, this command will use Cloud Functions (Second generation). If disabled with --no-gen2, Cloud Functions (First generation) will be used. If not specified, the value of this flag will be taken from the functions/gen2 configuration property. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/functions/event-types/list)

---