# gcloud bms os-images

manage bare metal os images in Bare Metal Solution

### `gcloud bms os-images describe`

Describe Bare Metal Solution OS images in a project

Describe Bare Metal Solution OS image in a project.

**Synopsis:**
```
gcloud bms os-images describe (OS_IMAGE : --region=REGION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Os image resource - os_image. The arguments in this group can be used to
specify the attributes of this resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument os_image on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OS_IMAGE
     ID of the os_image or fully qualified identifier for the os_image.

     To set the os_image attribute:
     + provide the argument os_image on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --region=REGION
     Region of the resource.

     To set the region attribute:
     + provide the argument os_image on the command line with a fully
       specified name;
     + provide the argument --region on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
To describe given OS image within the project, run:

    $ gcloud bms os-images describe my-os-image --project=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/os-images/describe)

---
### `gcloud bms os-images list`

List Bare Metal Solution OS images in a project

List Bare Metal Solution OS images in a project.

**Synopsis:**
```
gcloud bms os-images list [--filter=EXPRESSION] [--limit=LIMIT]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all OS images within the project, run:

    $ gcloud bms os-images list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/bms/os-images/list)

---