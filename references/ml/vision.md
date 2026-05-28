# gcloud ml vision

use Google Cloud Vision to analyze images

### `gcloud ml vision detect-document`

Detect dense text in an image

Detect dense text in an image, such as books and research reports.

Google Cloud Vision uses OCR (Optical Character Recognition) to analyze
text. This is a premium feature for dense text such as books, research
reports, and PDFs. To detect small amounts of text such as on signs, use
detect-text instead. For more information on this feature, see the Google
Cloud Vision documentation at https://cloud.google.com/vision/docs/.

Language hints can be provided to Google Cloud Vision API. In most cases,
an empty value yields the best results since it enables automatic language
detection. For languages based on the Latin alphabet, setting
language_hints is not needed. Text detection returns an error if one or
more of the specified languages is not one of the supported languages. (See
https://cloud.google.com/vision/docs/languages.) To provide language hints
run:

    $ gcloud ml vision detect-document --language-hints ja,ko

**Synopsis:**
```
gcloud ml vision detect-document IMAGE_PATH
    [--language-hints=[LANGUAGE_HINTS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--language-hints` | [LANGUAGE_HINTS,...] |  | List of languages to use for text detection. |


**Examples:**
```bash
To detect dense text in image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-document gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-document)

---
### `gcloud ml vision detect-faces`

Detect faces within an image

Detect faces within an image.

**Synopsis:**
```
gcloud ml vision detect-faces IMAGE_PATH [--max-results=MAX_RESULTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-results` | MAX_RESULTS |  | Maximum number of results to be provided. |


**Examples:**
```bash
To detect faces in image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-faces gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-faces)

---
### `gcloud ml vision detect-image-properties`

Detect general attributes of an image

Detect general attributes of an image, such as dominant color.

**Synopsis:**
```
gcloud ml vision detect-image-properties IMAGE_PATH [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Examples:**
```bash
To detect general attributes of image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-image-properties gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-image-properties)

---
### `gcloud ml vision detect-labels`

Detect broad sets of categories within an image

Label Detection detects categories in an image, ranging from modes of
transportation to animals.

**Synopsis:**
```
gcloud ml vision detect-labels IMAGE_PATH [--max-results=MAX_RESULTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-results` | MAX_RESULTS |  | Maximum number of results to be provided. |


**Examples:**
```bash
To detect categories in an image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-labels gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-labels)

---
### `gcloud ml vision detect-landmarks`

Detect popular natural and man-made structures within an image

Google Cloud Vision will recognize landmarks in an image, such as "Palace
of Fine Arts."

**Synopsis:**
```
gcloud ml vision detect-landmarks IMAGE_PATH [--max-results=MAX_RESULTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-results` | MAX_RESULTS |  | Maximum number of results to be provided. |


**Examples:**
```bash
To recognize landmarks in an image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-landmarks gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-landmarks)

---
### `gcloud ml vision detect-logos`

Detect popular product logos within an image

Detect popular product logos within an image.

**Synopsis:**
```
gcloud ml vision detect-logos IMAGE_PATH [--max-results=MAX_RESULTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-results` | MAX_RESULTS |  | Maximum number of results to be provided. |


**Examples:**
```bash
To detect product logos in an image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-logos gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-logos)

---
### `gcloud ml vision detect-objects`

Detect and extract multiple objects in an image with object localization

Detect and extract multiple objects in an image with object localization.

Object localization identifies multiple objects in an image and provides a
LocalizedObjectAnnotation for each object in the image.

**Synopsis:**
```
gcloud ml vision detect-objects IMAGE_PATH [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Examples:**
```bash
To detect objects for image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-objects gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-objects)

---
### `gcloud ml vision detect-safe-search`

Detect explicit content in an image

Safe Search Detection detects adult content, violent content, medical
content and spoof content in an image.

**Synopsis:**
```
gcloud ml vision detect-safe-search IMAGE_PATH [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Examples:**
```bash
To detect adult content, violent content, medical content and spoof content
in an image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-safe-search gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-safe-search)

---
### `gcloud ml vision detect-text`

Detect and extract text within an image

Detect and extract text within an image.

Google Cloud Vision uses OCR (Optical Character Recognition) to detect text
within an image, with support for a broad array of languages and automatic
label detection.

Language hints can be provided to Google Cloud Vision API. In most cases,
an empty value yields the best results since it enables automatic language
detection. For languages based on the Latin alphabet, setting
language_hints is not needed. Text detection returns an error if one or
more of the specified languages is not one of the supported languages. (See
https://cloud.google.com/vision/docs/languages.) To provide language hints
run:

    $ gcloud ml vision detect-text --language-hints ja,ko

**Synopsis:**
```
gcloud ml vision detect-text IMAGE_PATH
    [--language-hints=[LANGUAGE_HINTS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--language-hints` | [LANGUAGE_HINTS,...] |  | List of languages to use for text detection. |


**Examples:**
```bash
To detect and extract text within an image 'gs://my_bucket/input_file':

    $ gcloud ml vision detect-text gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-text)

---
### `gcloud ml vision detect-text-pdf`

Detect and transcribe text from PDF files stored in Google Cloud Storage

Detect and transcribe text from PDF files stored in Google Cloud Storage.

The Vision API accepts PDF files up to 2000 pages. Larger files will return
an error.

**Synopsis:**
```
gcloud ml vision detect-text-pdf INPUT_FILE OUTPUT_PATH
    [--batch-size=BATCH_SIZE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_FILE
   Google Cloud Storage location to read the input from. It must be in
   Google Cloud Storage format (gs://bucket/object)

OUTPUT_PATH
   Google Cloud Storage location to store the output file. It must be in
   Google Cloud Storage format (gs://bucket/object)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--batch-size` | BATCH_SIZE |  | Maximum number of response protos to put into each output JSON file on Google Cloud Storage. The valid range is [1, 100]. If not specified, the default value is 20. |


**Examples:**
```bash
To detect text for input PDF file 'gs://my_bucket/input_file' and store
output in 'gs://my_bucket/out_put_prefix':

    $ gcloud ml vision detect-text-pdf gs://my_bucket/input_file \
        gs://my_bucket/out_put_prefix
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-text-pdf)

---
### `gcloud ml vision detect-text-tiff`

Detect and transcribe text from TIFF files stored in Google Cloud Storage

Detect and transcribe text from TIFF files stored in Google Cloud Storage.

The Vision API accepts TIFF files up to 2000 pages. Larger files will
return an error.

**Synopsis:**
```
gcloud ml vision detect-text-tiff INPUT_FILE OUTPUT_PATH
    [--batch-size=BATCH_SIZE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
INPUT_FILE
   Google Cloud Storage location to read the input from. It must be in
   Google Cloud Storage format (gs://bucket/object)

OUTPUT_PATH
   Google Cloud Storage location to store the output file. It must be in
   Google Cloud Storage format (gs://bucket/object)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--batch-size` | BATCH_SIZE |  | Maximum number of response protos to put into each output JSON file on Google Cloud Storage. The valid range is [1, 100]. If not specified, the default value is 20. |


**Examples:**
```bash
To detect text for input TIFF file gs://my_bucket/input_file and store
output in gs://my_bucket/out_put_prefix:

    $ gcloud ml vision detect-text-tiff gs://my_bucket/input_file \
        gs://my_bucket/out_put_prefix
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-text-tiff)

---
### `gcloud ml vision detect-web`

Detect entities in an image from similar images on the web

Detect entities in an image from similar images on the web.

**Synopsis:**
```
gcloud ml vision detect-web IMAGE_PATH [--max-results=MAX_RESULTS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--max-results` | MAX_RESULTS |  | Maximum number of results to be provided. |


**Examples:**
```bash
To detect entities in an image gs://my_bucket/input_file:

    $ gcloud ml vision detect-web gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/detect-web)

---
### `gcloud ml vision suggest-crop`

Suggest a bounding box in an image

Returns the coordinates of a bounding box that surrounds the dominant
object or face in an image.

**Synopsis:**
```
gcloud ml vision suggest-crop IMAGE_PATH
    [--aspect-ratios=[ASPECT_RATIOS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
IMAGE_PATH
   Path to the image to be analyzed. This can be either a local path or a
   URL. If you provide a local file, the contents will be sent directly to
   Google Cloud Vision. If you provide a URL, it must be in Google Cloud
   Storage format (gs://bucket/object) or an HTTP URL (http://... or
   https://...)
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--aspect-ratios` | [ASPECT_RATIOS,...] |  | A list of aspect ratio hints for the suggested bounding box. Aspect ratios may be specified either as a decimal number (ex. 1.333) or as a ratio of width to height (ex 4:3). |


**Examples:**
```bash
To get the coordinates of a bounding box that surrounds the dominant object
or face in an image gs://my_bucket/input_file:

    $ gcloud ml vision suggest-crop gs://my_bucket/input_file
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/vision/suggest-crop)

---