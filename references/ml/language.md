# gcloud ml language

use the Google Cloud Natural Language API to analyze text

### `gcloud ml language analyze-entities`

Use Google Cloud Natural Language API to identify entities in text

Entity Analysis inspects the given text for common names or known entities
(proper nouns such as public figures, landmarks, etc.), and returns
information about those entities.

Currently English, Spanish, and Japanese are supported.

**Synopsis:**
```
gcloud ml language analyze-entities
    (--content=CONTENT | --content-file=CONTENT_FILE)
    [--content-type=CONTENT_TYPE; default="plain-text"]
    [--encoding-type=ENCODING_TYPE; default="utf8"] [--language=LANGUAGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content` | CONTENT |  | _[Exactly one of these must be specified:]_ Specify input text on the command line. Useful for experiments, or for extremely short text. |
| `--content-file` | CONTENT_FILE |  | _[Exactly one of these must be specified:]_ Specify a local file or Google Cloud Storage (format gs://bucket/object) file path containing the text to be analyzed. More useful for longer text or data output from another system. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content-type` | one of: html, plain-text | plain-text | Specify the format of the input text. CONTENT_TYPE must be one of: html, plain-text. |
| `--encoding-type` | one of: none, utf16, utf32, utf8 | utf8 | The encoding type used by the API to calculate offsets. If set to none, encoding-dependent offsets will be set at -1. This is an optional flag only used for the entity mentions in results, and does not affect how the input is read or analyzed. ENCODING_TYPE must be one of: none, utf16, utf32, utf8. |
| `--language` | LANGUAGE |  | Specify the language of the input text. If omitted, the server will attempt to auto-detect. Both ISO (such as en or es) and BCP-47 (such as en-US or ja-JP) language codes are accepted. |


**Examples:**
```bash
To analyze entites in raw content 'puppies':

    $ gcloud ml language analyze-entities --content='puppies'

To analyze entites in file 'myfile.txt':

    $ gcloud ml language analyze-entities --content-file='myfile.txt'

To analyze entites in a remote file 'gs://bucket_name/mycontent.html' for
Japanese language using UTF-8 encoding:

    $ gcloud ml language analyze-entities \
        --content-file='gs://bucket_name/mycontent.html' \
        --content-type=HTML --encoding-type=utf8 --language=ja-JP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/language/analyze-entities)

---
### `gcloud ml language analyze-entity-sentiment`

Use Google Cloud Natural Language API to identify entity-level sentiment

Entity level sentiment combines both entity analysis and sentiment analysis
and attempts to determine the sentiment (positive or negative) expressed
about entities within the text.

Currently only English is supported for this feature.

**Synopsis:**
```
gcloud ml language analyze-entity-sentiment
    (--content=CONTENT | --content-file=CONTENT_FILE)
    [--content-type=CONTENT_TYPE; default="plain-text"]
    [--encoding-type=ENCODING_TYPE; default="utf8"] [--language=LANGUAGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content` | CONTENT |  | _[Exactly one of these must be specified:]_ Specify input text on the command line. Useful for experiments, or for extremely short text. |
| `--content-file` | CONTENT_FILE |  | _[Exactly one of these must be specified:]_ Specify a local file or Google Cloud Storage (format gs://bucket/object) file path containing the text to be analyzed. More useful for longer text or data output from another system. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content-type` | one of: html, plain-text | plain-text | Specify the format of the input text. CONTENT_TYPE must be one of: html, plain-text. |
| `--encoding-type` | one of: none, utf16, utf32, utf8 | utf8 | The encoding type used by the API to calculate offsets. If set to none, encoding-dependent offsets will be set at -1. This is an optional flag only used for the entity mentions in results, and does not affect how the input is read or analyzed. ENCODING_TYPE must be one of: none, utf16, utf32, utf8. |
| `--language` | LANGUAGE |  | Specify the language of the input text. If omitted, the server will attempt to auto-detect. Both ISO (such as en or es) and BCP-47 (such as en-US or ja-JP) language codes are accepted. |


**Examples:**
```bash
To analyze entity sentiment in raw content 'puppies':

    $ gcloud ml language analyze-entity-sentiment --content='puppies'

To analyze entity sentiment in file 'myfile.txt':

    $ gcloud ml language analyze-entity-sentiment \
        --content-file='myfile.txt'

To analyze entity sentiment in a remote file
'gs://bucket_name/mycontent.html' for Japanese language using UTF-8
encoding:

    $ gcloud ml language analyze-entity-sentiment \
        --content-file='gs://bucket_name/mycontent.html' \
        --content-type=HTML --encoding-type=utf8 --language=ja-JP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/language/analyze-entity-sentiment)

---
### `gcloud ml language analyze-sentiment`

Use Google Cloud Natural Language API to identify sentiments in a text

Sentiment Analysis inspects the given text and identifies the prevailing
emotional opinion within the text, especially to determine a writer's
attitude as positive, negative, or neutral.

Currently English, Spanish, and Japanese are supported.

**Synopsis:**
```
gcloud ml language analyze-sentiment
    (--content=CONTENT | --content-file=CONTENT_FILE)
    [--content-type=CONTENT_TYPE; default="plain-text"]
    [--encoding-type=ENCODING_TYPE; default="utf8"] [--language=LANGUAGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content` | CONTENT |  | _[Exactly one of these must be specified:]_ Specify input text on the command line. Useful for experiments, or for extremely short text. |
| `--content-file` | CONTENT_FILE |  | _[Exactly one of these must be specified:]_ Specify a local file or Google Cloud Storage (format gs://bucket/object) file path containing the text to be analyzed. More useful for longer text or data output from another system. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content-type` | one of: html, plain-text | plain-text | Specify the format of the input text. CONTENT_TYPE must be one of: html, plain-text. |
| `--encoding-type` | one of: none, utf16, utf32, utf8 | utf8 | The encoding type used by the API to calculate offsets. If set to none, encoding-dependent offsets will be set at -1. This is an optional flag only used for the entity mentions in results, and does not affect how the input is read or analyzed. ENCODING_TYPE must be one of: none, utf16, utf32, utf8. |
| `--language` | LANGUAGE |  | Specify the language of the input text. If omitted, the server will attempt to auto-detect. Both ISO (such as en or es) and BCP-47 (such as en-US or ja-JP) language codes are accepted. |


**Examples:**
```bash
To analyze sentiment in raw content 'I love puppies.':

    $ gcloud ml language analyze-sentiment --content='I love puppies.'

To analyze sentiment in file 'myfile.txt':

    $ gcloud ml language analyze-sentiment --content-file='myfile.txt'

To analyze sentiment in a remote file 'gs://bucket_name/mycontent.html' for
Japanese language using UTF-8 encoding:

    $ gcloud ml language analyze-sentiment \
        --content-file='gs://bucket_name/mycontent.html' \
        --content-type=HTML --encoding-type=utf8 --language=ja-JP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/language/analyze-sentiment)

---
### `gcloud ml language analyze-syntax`

Use Google Cloud Natural Language API to identify linguistic information

Syntactic Analysis extracts linguistic information, breaking up the given
text into a series of sentences and tokens (generally, word boundaries),
providing further analysis on those tokens.

Currently English, Spanish, and Japanese are supported.

**Synopsis:**
```
gcloud ml language analyze-syntax
    (--content=CONTENT | --content-file=CONTENT_FILE)
    [--content-type=CONTENT_TYPE; default="plain-text"]
    [--encoding-type=ENCODING_TYPE; default="utf8"] [--language=LANGUAGE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content` | CONTENT |  | _[Exactly one of these must be specified:]_ Specify input text on the command line. Useful for experiments, or for extremely short text. |
| `--content-file` | CONTENT_FILE |  | _[Exactly one of these must be specified:]_ Specify a local file or Google Cloud Storage (format gs://bucket/object) file path containing the text to be analyzed. More useful for longer text or data output from another system. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content-type` | one of: html, plain-text | plain-text | Specify the format of the input text. CONTENT_TYPE must be one of: html, plain-text. |
| `--encoding-type` | one of: none, utf16, utf32, utf8 | utf8 | The encoding type used by the API to calculate offsets. If set to none, encoding-dependent offsets will be set at -1. This is an optional flag only used for the entity mentions in results, and does not affect how the input is read or analyzed. ENCODING_TYPE must be one of: none, utf16, utf32, utf8. |
| `--language` | LANGUAGE |  | Specify the language of the input text. If omitted, the server will attempt to auto-detect. Both ISO (such as en or es) and BCP-47 (such as en-US or ja-JP) language codes are accepted. |


**Examples:**
```bash
To analyze syntax in raw content 'They drink.':

    $ gcloud ml language analyze-syntax --content='They drink'

To analyze syntax in file 'myfile.txt':

    $ gcloud ml language analyze-syntax --content-file='myfile.txt'

To analyze syntax in a remote file 'gs://bucket_name/mycontent.html' for
Japanese language using UTF-8 encoding:

    $ gcloud ml language analyze-syntax \
        --content-file='gs://bucket_name/mycontent.html' \
        --content-type=HTML --encoding-type=utf8 --language=ja-JP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/language/analyze-syntax)

---
### `gcloud ml language classify-text`

Classifies input document into categories

Classifies input document into categories. Returns a list of categories
representing the document. Only the most relevant categories a document are
returned e.g. if /Science and /Science/Astronomy both apply to a document,
then only the /Science/Astronomy category is returned, as it is the more
specific result.

Currently only English is supported for this feature.

**Synopsis:**
```
gcloud ml language classify-text
    (--content=CONTENT | --content-file=CONTENT_FILE)
    [--content-type=CONTENT_TYPE; default="plain-text"]
    [--language=LANGUAGE] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content` | CONTENT |  | _[Exactly one of these must be specified:]_ Specify input text on the command line. Useful for experiments, or for extremely short text. |
| `--content-file` | CONTENT_FILE |  | _[Exactly one of these must be specified:]_ Specify a local file or Google Cloud Storage (format gs://bucket/object) file path containing the text to be analyzed. More useful for longer text or data output from another system. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--content-type` | one of: html, plain-text | plain-text | Specify the format of the input text. CONTENT_TYPE must be one of: html, plain-text. |
| `--language` | LANGUAGE |  | Specify the language of the input text. If omitted, the server will attempt to auto-detect. Both ISO (such as en or es) and BCP-47 (such as en-US or ja-JP) language codes are accepted. |


**Examples:**
```bash
To classify text in raw content 'Long Political Text.':

    $ gcloud ml language classify-text --content='Long Political Text.'

To classify text in file 'myfile.txt':

    $ gcloud ml language classify-text --content-file='myfile.txt'

To classify text in a remote file 'gs://bucket_name/mycontent.html' for
Japanese language:

    $ gcloud ml language classify-text \
        --content-file='gs://bucket_name/mycontent.html' \
        --content-type=HTML --language=ja-JP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/language/classify-text)

---