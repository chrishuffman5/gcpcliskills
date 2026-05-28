# gcloud ml — Cloud ML APIs (Natural Language, Speech-to-Text, Video Intelligence, Vision)

## Overview

`gcloud ml` is an umbrella for helper commands that call four pretrained Google Cloud AI inference APIs without writing any client code: **Natural Language** (`ml language`), **Speech-to-Text** (`ml speech`), **Video Intelligence** (`ml video`), and **Vision** (`ml vision`). Each subgroup sends a local file or a Google Cloud Storage object to the corresponding API and prints the JSON annotation result. Reach for these commands for quick experiments, scripting, and one-off analysis from the terminal; production workloads usually use the client libraries instead. Each API is independent and must be enabled separately.

## Quick reference — common workflows

### 1. Analyze sentiment and entities in text (Natural Language)
```bash
gcloud services enable language.googleapis.com

# Sentiment of inline text
gcloud ml language analyze-sentiment --content='I love this product!'

# Sentiment of a local file
gcloud ml language analyze-sentiment --content-file='review.txt'

# Analyze an HTML doc in GCS, with an explicit language
gcloud ml language analyze-entities \
    --content-file='gs://my-bucket/article.html' \
    --content-type=html \
    --language=en

# Entity-level sentiment (English only) and content classification (English only)
gcloud ml language analyze-entity-sentiment --content-file='review.txt'
gcloud ml language classify-text --content-file='article.txt'
```

### 2. Transcribe short audio synchronously (Speech-to-Text, < 60 s)
```bash
gcloud services enable speech.googleapis.com

# Local WAV/FLAC needs no --encoding
gcloud ml speech recognize 'my-recording.wav' --language-code=en-US

# GCS audio with explicit encoding, punctuation, and a chosen model
gcloud ml speech recognize 'gs://my-bucket/audio.flac' \
    --language-code=en-US \
    --encoding=flac \
    --enable-automatic-punctuation \
    --model=latest_short
```

### 3. Transcribe long audio asynchronously (Speech-to-Text, up to 80 min)
```bash
# Submit the job and return immediately with an operation ID
gcloud ml speech recognize-long-running 'gs://my-bucket/long-audio.mp3' \
    --language-code=en-US \
    --encoding=mp3 \
    --async \
    --output-uri='gs://my-bucket/transcripts/result.json'

# Check status, then block until the transcript is ready
gcloud ml speech operations describe OPERATION_ID
gcloud ml speech operations wait OPERATION_ID
```

### 4. Analyze video content (Video Intelligence)
```bash
gcloud services enable videointelligence.googleapis.com

# Detect labels (per-shot by default; --detection-mode controls shot/frame)
gcloud ml video detect-labels gs://my-bucket/video.mp4

# Detect shot changes and explicit content asynchronously into GCS
gcloud ml video detect-shot-changes gs://my-bucket/video.mp4 --region=us-east1
gcloud ml video detect-explicit-content gs://my-bucket/video.mp4 \
    --async \
    --output-uri='gs://my-bucket/results/out.json' \
    --region=us-east1

# Poll the async video operation (fully qualified operation name)
gcloud ml video operations wait \
    projects/my-project/locations/us-east1/operations/123
```

### 5. Run OCR and image detection (Vision)
```bash
gcloud services enable vision.googleapis.com

# OCR: sparse text (signs/labels) vs. dense document text
gcloud ml vision detect-text gs://my-bucket/sign.jpg
gcloud ml vision detect-document gs://my-bucket/page.jpg --language-hints=ja,ko

# OCR a multi-page PDF/TIFF in GCS to an output prefix (input + output positionals)
gcloud ml vision detect-text-pdf gs://my-bucket/input.pdf gs://my-bucket/output-prefix

# Label / face / landmark / logo / object detection
gcloud ml vision detect-labels gs://my-bucket/photo.jpg --max-results=10
gcloud ml vision detect-faces gs://my-bucket/photo.jpg
gcloud ml vision detect-landmarks gs://my-bucket/photo.jpg

# Safe-search moderation and crop-hint suggestion
gcloud ml vision detect-safe-search gs://my-bucket/image.jpg
gcloud ml vision suggest-crop gs://my-bucket/image.jpg --aspect-ratios=16:9,4:3
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `ml language` | [`language.md`](language.md) | 5 | Use the Cloud Natural Language API to analyze text (sentiment, entities, entity sentiment, syntax, classification) |
| `ml speech` | [`speech.md`](speech.md) | 4 | Use Cloud Speech-to-Text to transcribe audio (sync, long-running, operations) |
| `ml video` | [`video.md`](video.md) | 5 | Cloud Video Intelligence — label / shot-change / explicit-content detection and operations |
| `ml vision` | [`vision.md`](vision.md) | 13 | Use Cloud Vision to analyze images (OCR, faces, labels, landmarks, logos, objects, safe-search, web, crop hints) |

See [`index.md`](index.md) for a one-line index of all 27 GA commands.

## Common flags & tips

- **Input source.** `ml language` takes text via `--content` (inline) or `--content-file` (local path or `gs://` URI) — exactly one is required. `ml speech` takes an `AUDIO` positional, and `ml video` / most `ml vision` commands take an `IMAGE_PATH` / `INPUT_PATH` positional that may be a local file or a `gs://` URI (Vision image commands also accept an `http(s)://` URL). `detect-text-pdf` / `detect-text-tiff` require two positionals — a GCS `INPUT_FILE` and a GCS `OUTPUT_PATH` — and both must be `gs://` URIs.
- **Language selection.** Natural Language uses `--language` (ISO like `en`, or BCP-47 like `ja-JP`); Speech requires `--language-code` (BCP-47, e.g. `en-US`); Vision OCR uses `--language-hints=ja,ko`. Omitting language usually lets the server auto-detect.
- **Audio encoding.** `--encoding` is only required when the file is not WAV or FLAC. Valid values: `alaw, amr, amr-wb, encoding-unspecified, flac, linear16, mp3, mulaw, ogg-opus, speex-with-header-byte, webm-opus`. Pick a `--model` (e.g. `latest_long`, `latest_short`, `phone_call`, `telephony`, `medical_dictation`) to suit your domain.
- **Async + operations.** `ml speech recognize-long-running` and all `ml video detect-*` commands accept `--async` to return an operation immediately and `--output-uri` to write results to GCS. Poll with `operations describe` / `operations wait`. Speech operations take a bare numeric `OPERATION` ID; video operations take a fully qualified `projects/.../locations/REGION/operations/ID` name (or an ID plus `--location`).
- **Video regions.** `--region` for `ml video` is restricted to `asia-east1, europe-west1, us-east1, us-west1`; if omitted the region is inferred from the file location. Use `--segments=START:END[,...]` (e.g. `0s:23.554s,24s:29.528s`) to analyze only parts of a video, and `--detection-mode` (`shot`, `frame`, `shot-and-frame`) for `detect-labels`.
- **Result formatting.** All commands print JSON; shape the output with global flags, e.g.
  - `gcloud ml language analyze-sentiment --content='Great!' --format='value(documentSentiment.score)'`
  - `gcloud ml vision detect-labels gs://my-bucket/photo.jpg --format='table(responses[0].labelAnnotations[].description, responses[0].labelAnnotations[].score)'`
- **Result tuning.** `--max-results` caps results on most Vision detectors (`detect-faces`, `detect-labels`, `detect-landmarks`, `detect-logos`, `detect-web`); `--max-alternatives` (0–30) controls Speech hypotheses; `--filter-profanity`, `--hints`, and `--include-word-time-offsets` refine transcripts.

## beta / alpha

`gcloud beta ml` and `gcloud alpha ml` mirror the GA surface; the GA `gcloud ml` group covers all 27 commands across the four subgroups, and no ml-specific features are documented only under beta/alpha in this reference. Use the pre-release tracks only if you need a feature not yet promoted to GA.

## Official documentation

- gcloud ml command reference: https://cloud.google.com/sdk/gcloud/reference/ml — the `ml` group and its `language`, `speech`, `video`, `vision` subgroups.
- Cloud Natural Language docs: https://cloud.google.com/natural-language/docs — sentiment, entity, syntax, and content classification concepts and how-tos.
  - Basics: https://cloud.google.com/natural-language/docs/basics — sentiment score/magnitude, entity types, syntax tokens, categories.
  - Analyzing sentiment: https://cloud.google.com/natural-language/docs/analyzing-sentiment — sentiment how-to via CLI and client libraries.
- Cloud Speech-to-Text docs: https://cloud.google.com/speech-to-text/docs — sync, async, and streaming transcription.
  - Sync recognition: https://cloud.google.com/speech-to-text/docs/sync-recognize — synchronous recognition (< 60 s audio).
  - IAM roles: https://cloud.google.com/speech-to-text/docs/iam — Speech-to-Text role reference.
- Cloud Video Intelligence docs: https://cloud.google.com/video-intelligence/docs — label, shot-change, and explicit-content detection.
  - Quickstart: https://cloud.google.com/video-intelligence/docs/quickstart — analyze a video with gcloud and curl.
- Cloud Vision docs: https://cloud.google.com/vision/docs — OCR plus face, landmark, logo, label, and object detection.
  - Detecting text: https://cloud.google.com/vision/docs/detecting-text — `TEXT_DETECTION` and `DOCUMENT_TEXT_DETECTION` how-to.
  - Setup: https://cloud.google.com/vision/docs/setup — enabling the API and required IAM roles.
