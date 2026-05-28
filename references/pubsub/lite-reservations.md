# gcloud pubsub lite-reservations

manage Pub/Sub Lite reservations

### `gcloud pubsub lite-reservations create`

Create a Pub/Sub Lite reservation

Create a Pub/Sub Lite reservation.

**Synopsis:**
```
gcloud pubsub lite-reservations create RESERVATION --location=LOCATION
    --throughput-capacity=THROUGHPUT_CAPACITY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RESERVATION
   Reservation ID.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |
| `--throughput-capacity` | THROUGHPUT_CAPACITY |  | _[This must be specified.]_ Reservation throughput capacity. Every unit of throughput capacity is equivalent to 1 MiB/s of published messages or 2 MiB/s of subscribed messages. |


**Examples:**
```bash
To create a Pub/Sub lite-reservation, run:

    $ gcloud pubsub lite-reservations create myreservation \
      --location=us-central1 --throughput-capacity=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-reservations/create)

---
### `gcloud pubsub lite-reservations delete`

Delete a Pub/Sub Lite reservation

Delete a Pub/Sub Lite reservation.

**Synopsis:**
```
gcloud pubsub lite-reservations delete (RESERVATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - Reservation to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To delete a Pub/Sub Lite reservation, run:

    $ gcloud pubsub lite-reservations delete myreservation \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-reservations/delete)

---
### `gcloud pubsub lite-reservations describe`

Describe a Pub/Sub Lite reservation

Describe a Pub/Sub Lite reservation.

**Synopsis:**
```
gcloud pubsub lite-reservations describe
    (RESERVATION : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - Reservation to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a Pub/Sub Lite reservation, run:

    $ gcloud pubsub lite-reservations describe myreservation \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-reservations/describe)

---
### `gcloud pubsub lite-reservations list`

List Pub/Sub Lite reservations

List Pub/Sub Lite reservations.

**Synopsis:**
```
gcloud pubsub lite-reservations list --location=LOCATION
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[This must be specified.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line. |


**Examples:**
```bash
To list Pub/Sub Lite reservations, run:

    $ gcloud pubsub lite-reservations list --location=us-central1 \
      --limit=5
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-reservations/list)

---
### `gcloud pubsub lite-reservations list-topics`

List Pub/Sub Lite topics for a given Lite reservation

List Pub/Sub Lite topics for a given Lite reservation.

**Synopsis:**
```
gcloud pubsub lite-reservations list-topics
    (RESERVATION : --location=LOCATION) [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - Reservation to list topics for. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To list Pub/Sub Lite topics for a given Lite reservation, run:

    $ gcloud pubsub lite-reservations list-topics myreservation \
      --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-reservations/list-topics)

---
### `gcloud pubsub lite-reservations update`

Update a Pub/Sub Lite reservation

Update a Pub/Sub Lite reservation.

**Synopsis:**
```
gcloud pubsub lite-reservations update (RESERVATION : --location=LOCATION)
    --throughput-capacity=THROUGHPUT_CAPACITY [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Reservation resource - Reservation to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument reservation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  RESERVATION
     ID of the reservation or fully qualified identifier for the
     reservation.

     To set the reservation attribute:
     + provide the argument reservation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     ID of the location of the Pub/Sub Lite resource.

     To set the location attribute:
     + provide the argument reservation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--throughput-capacity` | THROUGHPUT_CAPACITY |  | Reservation throughput capacity. Every unit of throughput capacity is equivalent to 1 MiB/s of published messages or 2 MiB/s of subscribed messages. |


**Examples:**
```bash
To update a Pub/Sub Lite reservation, run:

    $ gcloud pubsub lite-reservations update myreservation \
      --location=us-central1 --throughput-capacity=2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/pubsub/lite-reservations/update)

---