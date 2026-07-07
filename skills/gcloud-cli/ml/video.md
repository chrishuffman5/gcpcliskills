# gcloud ml video

cloud ML Video-Intelligence command groups

### `gcloud ml video detect-explicit-content`

Detect explicit content in videos

Detect adult content within a video. Adult content is content generally
appropriate for 18 years of age and older, including but not limited to
nudity, sexual activities, and pornography (including cartoons or anime).

The response includes a bucketized likelihood value, from VERY_UNLIKELY to
VERY_LIKELY. When Explicit Content Detection evaluates a video, it does so
on a per-frame basis and considers visual content only (not audio).

**Synopsis:**
```
gcloud ml video detect-explicit-content INPUT_PATH [--async]
    [--output-uri=OUTPUT_URI] [--region=REGION] [--segments=[SEGMENTS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_PATH
   Path to the video to be analyzed. Must be a local path or a Google
   Cloud Storage URI.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--output-uri` | OUTPUT_URI |  | Location to which the results should be written. Must be a Google Cloud Storage URI. |
| `--region` | one of: asia-east1, europe-west1, us-east1, us-west1 |  | Optional Cloud region where annotation should take place. If no region is specified, a region will be determined based on video file location. REGION must be one of: asia-east1, europe-west1, us-east1, us-west1. |
| `--segments` | [SEGMENTS,...] |  | Segments from the video which you want to analyze (by default, the entire video will be treated as one segment). Must be in the format START1:END1[,START2:END2,...] (inclusive). START and END of segments must be a properly formatted duration string of the form HhMmSs where: * H is the number of hours from beginning of video * M is the number of minutes from the beginning of video * S is the number of seconds from the beginning of the video H, M and S can be specified as ints or floats for fractional units (to microsecond resolution). Unit chars (e.g. h, m or s) are required. Microseconds can be specified using fractional seconds e.g. 0.000569s == 569 microseconds. Examples: 0s:23.554048s,24s:29.528064s 0:1m40s,3m50s:5m10.232265s |


**Examples:**
```bash
To detect explicit content in a video file named
'gs://my_bucket/input_file.mp4', run the following command.:

    $ gcloud ml video detect-explicit-content \
        gs://my_bucket/input_file.mp4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/video/detect-explicit-content)

---
### `gcloud ml video detect-labels`

Detect general labels for videos

Detect general categories in videos, such as modes of transportation or
animals. Use the --detection-mode flag to control whether labels are
detected for shots, frames, or both.

**Synopsis:**
```
gcloud ml video detect-labels INPUT_PATH [--async]
    [--detection-mode=DETECTION_MODE; default="shot"]
    [--output-uri=OUTPUT_URI] [--region=REGION] [--segments=[SEGMENTS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_PATH
   Path to the video to be analyzed. Must be a local path or a Google
   Cloud Storage URI.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--detection-mode` | one of: frame Detect labels at the per-frame level | shot | The mode of label detection requested. DETECTION_MODE must be one of: frame Detect labels at the per-frame level. shot Detect labels at the per-shot level. shot-and-frame Detect labels at both the per-shot and per-frame level. |
| `--output-uri` | OUTPUT_URI |  | Location to which the results should be written. Must be a Google Cloud Storage URI. |
| `--region` | one of: asia-east1, europe-west1, us-east1, us-west1 |  | Optional Cloud region where annotation should take place. If no region is specified, a region will be determined based on video file location. REGION must be one of: asia-east1, europe-west1, us-east1, us-west1. |
| `--segments` | [SEGMENTS,...] |  | Segments from the video which you want to analyze (by default, the entire video will be treated as one segment). Must be in the format START1:END1[,START2:END2,...] (inclusive). START and END of segments must be a properly formatted duration string of the form HhMmSs where: * H is the number of hours from beginning of video * M is the number of minutes from the beginning of video * S is the number of seconds from the beginning of the video H, M and S can be specified as ints or floats for fractional units (to microsecond resolution). Unit chars (e.g. h, m or s) are required. Microseconds can be specified using fractional seconds e.g. 0.000569s == 569 microseconds. Examples: 0s:23.554048s,24s:29.528064s 0:1m40s,3m50s:5m10.232265s |


**Examples:**
```bash
To detect labels in video file 'gs://my_bucket/input_file.mp4':

    $ gcloud ml video detect-labels gs://my_bucket/input_file.mp4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/video/detect-labels)

---
### `gcloud ml video detect-shot-changes`

Detect shot changes in videos

Detect when the shot changes in a video.

**Synopsis:**
```
gcloud ml video detect-shot-changes INPUT_PATH [--async]
    [--output-uri=OUTPUT_URI] [--region=REGION] [--segments=[SEGMENTS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_PATH
   Path to the video to be analyzed. Must be a local path or a Google
   Cloud Storage URI.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--output-uri` | OUTPUT_URI |  | Location to which the results should be written. Must be a Google Cloud Storage URI. |
| `--region` | one of: asia-east1, europe-west1, us-east1, us-west1 |  | Optional Cloud region where annotation should take place. If no region is specified, a region will be determined based on video file location. REGION must be one of: asia-east1, europe-west1, us-east1, us-west1. |
| `--segments` | [SEGMENTS,...] |  | Segments from the video which you want to analyze (by default, the entire video will be treated as one segment). Must be in the format START1:END1[,START2:END2,...] (inclusive). START and END of segments must be a properly formatted duration string of the form HhMmSs where: * H is the number of hours from beginning of video * M is the number of minutes from the beginning of video * S is the number of seconds from the beginning of the video H, M and S can be specified as ints or floats for fractional units (to microsecond resolution). Unit chars (e.g. h, m or s) are required. Microseconds can be specified using fractional seconds e.g. 0.000569s == 569 microseconds. Examples: 0s:23.554048s,24s:29.528064s 0:1m40s,3m50s:5m10.232265s |


**Examples:**
```bash
To detect shot changes in a video file named
'gs://my_bucket/input_file.mp4', run the following command:

    $ gcloud ml video detect-shot-changes gs://my_bucket/input_file.mp4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/video/detect-shot-changes)

---

## `gcloud ml video operations` — command group for working with Cloud Video Intelligence operations
### `gcloud ml video operations describe`

Get description of a long-running video analysis operation

Get information about a long-running video analysis operation.

**Synopsis:**
```
gcloud ml video operations describe (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To get information about a long-running operation with name
'projects/my-project/locations/us-east1/operations/123', run the following
command:

    $ gcloud ml video operations describe \
        projects/my-project/locations/us-east1/operations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/video/operations/describe)

---
### `gcloud ml video operations wait`

Poll long-running video analysis operation until it completes

Poll a long-running video analysis operation until it completes. When the
operation is complete, this command will display the results of the
analysis.

**Synopsis:**
```
gcloud ml video operations wait (OPERATION : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - ID for the operation to poll until complete. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location of the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To poll a long-running video analysis operation named
'projects/my-project/locations/us-east1/operations/123' until it completes,
run the following:

    $ gcloud ml video operations wait \
        projects/my-project/locations/us-east1/operations/123
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/video/operations/wait)

---