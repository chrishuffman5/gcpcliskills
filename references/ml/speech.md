# gcloud ml speech

use Google Cloud Speech to get transcripts of audio

### `gcloud ml speech recognize`

Get transcripts of short (less than 60 seconds) audio from an audio file

Get a transcript of an audio file that is less than 60 seconds. You can use
an audio file that is on your local drive or a Google Cloud Storage URL.

If the audio is longer than 60 seconds, you will get an error. Please use
gcloud ml speech recognize-long-running instead.

**Synopsis:**
```
gcloud ml speech recognize AUDIO --language-code=LANGUAGE_CODE
    [--enable-automatic-punctuation]
    [--encoding=ENCODING; default="encoding-unspecified"]
    [--filter-profanity] [--hints=[HINT,...]] [--include-word-time-offsets]
    [--max-alternatives=MAX_ALTERNATIVES; default=1] [--model=MODEL]
    [--sample-rate=SAMPLE_RATE]
    [--audio-channel-count=AUDIO_CHANNEL_COUNT
      --separate-channel-recognition] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AUDIO
   The location of the audio file to transcribe. Must be a local path or a
   Google Cloud Storage URL (in the format gs://bucket/object).
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--language-code` | LANGUAGE_CODE |  | The language of the supplied audio as a BCP-47 (https://www.rfc-editor.org/rfc/bcp/bcp47.txt) language tag. Example: "en-US". See https://cloud.google.com/speech/docs/languages for a list of the currently supported language codes. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--enable-automatic-punctuation` |  |  | Adds punctuation to recognition result hypotheses. |
| `--encoding` | one of: alaw, amr, amr-wb, encoding-unspecified, flac, linear16, mp3, mulaw, ogg-opus, speex-with-header-byte, webm-opus | encoding-unspecified | The type of encoding of the file. Required if the file format is not WAV or FLAC. ENCODING must be one of: alaw, amr, amr-wb, encoding-unspecified, flac, linear16, mp3, mulaw, ogg-opus, speex-with-header-byte, webm-opus. |
| `--filter-profanity` |  |  | If True, the server will attempt to filter out profanities, replacing all but the initial character in each filtered word with asterisks, e.g. f***. |
| `--hints` | [HINT,...] |  | A list of strings containing word and phrase "hints" so that the speech recognition is more likely to recognize them. This can be used to improve the accuracy for specific words and phrases, for example, if specific commands are typically spoken by the user. This can also be used to add additional words to the vocabulary of the recognizer. See https://cloud.google.com/speech/limits#content. |
| `--include-word-time-offsets` |  |  | If True, the top result includes a list of words with the start and end time offsets (timestamps) for those words. If False, no word-level time offset information is returned. |
| `--max-alternatives` | MAX_ALTERNATIVES | 1 | Maximum number of recognition hypotheses to be returned. The server may return fewer than max_alternatives. Valid values are 0-30. A value of 0 or 1 will return a maximum of one. |
| `--model` | one of: command_and_search short queries such as voice commands or voice search |  | Select the model best suited to your domain to get best results. If you do not explicitly specify a model, Speech-to-Text will auto-select a model based on your other specified parameters. Some models are premium and cost more than standard models (although you can reduce the price by opting into https://cloud.google.com/speech-to-text/docs/data-logging). MODEL must be one of: command_and_search short queries such as voice commands or voice search. default audio that is not one of the specific audio models. For example, long-form audio. Ideally the audio is high-fidelity, recorded at a 16khz or greater sampling rate. latest_long Use this model for any kind of long form content such as media or spontaneous speech and conversations. Consider using this model in place of the video model, especially if the video model is not available in your target language. You can also use this in place of the default model. latest_short Use this model for short utterances that are a few seconds in length. It is useful for trying to capture commands or other single shot directed speech use cases. Consider using this model instead of the command and search model. medical_conversation Best for audio that originated from a conversation between a medical provider and patient. medical_dictation Best for audio that originated from dictation notes by a medical provider. phone_call audio that originated from a phone call (typically recorded at an 8khz sampling rate). phone_call_enhanced audio that originated from a phone call (typically recorded at an 8khz sampling rate). This is a premium model and can produce better results but costs more than the standard rate. telephony Improved version of the "phone_call" model, best for audio that originated from a phone call, typically recorded at an 8kHz sampling rate. telephony_short Dedicated version of the modern "telephony" model for short or even single-word utterances for audio that originated from a phone call, typically recorded at an 8kHz sampling rate. video_enhanced audio that originated from video or includes multiple speakers. Ideally the audio is recorded at a 16khz or greater sampling rate. This is a premium model that costs more than the standard rate. |
| `--sample-rate` | SAMPLE_RATE |  | The sample rate in Hertz. For best results, set the sampling rate of the audio source to 16000 Hz. If that's not possible, use the native sample rate of the audio source (instead of re-sampling). |


**Examples:**
```bash
To get a transcript of an audio file 'my-recording.wav':

    $ gcloud ml speech recognize 'my-recording.wav' --language-code=en-US

To get a transcript of an audio file in bucket 'gs://bucket/myaudio' with a
custom sampling rate and encoding that uses hints and filters profanity:

    $ gcloud ml speech recognize 'gs://bucket/myaudio' \
      --language-code=es-ES --sample-rate=2200 --hints=Bueno \
      --encoding=OGG_OPUS --filter-profanity
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/speech/recognize)

---
### `gcloud ml speech recognize-long-running`

Get transcripts of longer audio from an audio file

Get a transcript of audio up to 80 minutes in length. If the audio is under
60 seconds, you may also use gcloud ml speech recognize to analyze it.

**Synopsis:**
```
gcloud ml speech recognize-long-running AUDIO --language-code=LANGUAGE_CODE
    [--async] [--enable-automatic-punctuation]
    [--encoding=ENCODING; default="encoding-unspecified"]
    [--filter-profanity] [--hints=[HINT,...]] [--include-word-time-offsets]
    [--max-alternatives=MAX_ALTERNATIVES; default=1] [--model=MODEL]
    [--output-uri=OUTPUT_URI] [--sample-rate=SAMPLE_RATE]
    [--audio-channel-count=AUDIO_CHANNEL_COUNT
      --separate-channel-recognition] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
AUDIO
   The location of the audio file to transcribe. Must be a local path or a
   Google Cloud Storage URL (in the format gs://bucket/object).
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--language-code` | LANGUAGE_CODE |  | The language of the supplied audio as a BCP-47 (https://www.rfc-editor.org/rfc/bcp/bcp47.txt) language tag. Example: "en-US". See https://cloud.google.com/speech/docs/languages for a list of the currently supported language codes. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--enable-automatic-punctuation` |  |  | Adds punctuation to recognition result hypotheses. |
| `--encoding` | one of: alaw, amr, amr-wb, encoding-unspecified, flac, linear16, mp3, mulaw, ogg-opus, speex-with-header-byte, webm-opus | encoding-unspecified | The type of encoding of the file. Required if the file format is not WAV or FLAC. ENCODING must be one of: alaw, amr, amr-wb, encoding-unspecified, flac, linear16, mp3, mulaw, ogg-opus, speex-with-header-byte, webm-opus. |
| `--filter-profanity` |  |  | If True, the server will attempt to filter out profanities, replacing all but the initial character in each filtered word with asterisks, e.g. f***. |
| `--hints` | [HINT,...] |  | A list of strings containing word and phrase "hints" so that the speech recognition is more likely to recognize them. This can be used to improve the accuracy for specific words and phrases, for example, if specific commands are typically spoken by the user. This can also be used to add additional words to the vocabulary of the recognizer. See https://cloud.google.com/speech/limits#content. |
| `--include-word-time-offsets` |  |  | If True, the top result includes a list of words with the start and end time offsets (timestamps) for those words. If False, no word-level time offset information is returned. |
| `--max-alternatives` | MAX_ALTERNATIVES | 1 | Maximum number of recognition hypotheses to be returned. The server may return fewer than max_alternatives. Valid values are 0-30. A value of 0 or 1 will return a maximum of one. |
| `--model` | one of: command_and_search short queries such as voice commands or voice search |  | Select the model best suited to your domain to get best results. If you do not explicitly specify a model, Speech-to-Text will auto-select a model based on your other specified parameters. Some models are premium and cost more than standard models (although you can reduce the price by opting into https://cloud.google.com/speech-to-text/docs/data-logging). MODEL must be one of: command_and_search short queries such as voice commands or voice search. default audio that is not one of the specific audio models. For example, long-form audio. Ideally the audio is high-fidelity, recorded at a 16khz or greater sampling rate. latest_long Use this model for any kind of long form content such as media or spontaneous speech and conversations. Consider using this model in place of the video model, especially if the video model is not available in your target language. You can also use this in place of the default model. latest_short Use this model for short utterances that are a few seconds in length. It is useful for trying to capture commands or other single shot directed speech use cases. Consider using this model instead of the command and search model. medical_conversation Best for audio that originated from a conversation between a medical provider and patient. medical_dictation Best for audio that originated from dictation notes by a medical provider. phone_call audio that originated from a phone call (typically recorded at an 8khz sampling rate). phone_call_enhanced audio that originated from a phone call (typically recorded at an 8khz sampling rate). This is a premium model and can produce better results but costs more than the standard rate. telephony Improved version of the "phone_call" model, best for audio that originated from a phone call, typically recorded at an 8kHz sampling rate. telephony_short Dedicated version of the modern "telephony" model for short or even single-word utterances for audio that originated from a phone call, typically recorded at an 8kHz sampling rate. video_enhanced audio that originated from video or includes multiple speakers. Ideally the audio is recorded at a 16khz or greater sampling rate. This is a premium model that costs more than the standard rate. |
| `--output-uri` | OUTPUT_URI |  | Location to which the results should be written. Must be a Google Cloud Storage URI. |
| `--sample-rate` | SAMPLE_RATE |  | The sample rate in Hertz. For best results, set the sampling rate of the audio source to 16000 Hz. If that's not possible, use the native sample rate of the audio source (instead of re-sampling). |


**Examples:**
```bash
To block the command from completing until analysis is finished, run:

    $ gcloud ml speech recognize-long-running AUDIO_FILE \
        --language-code=LANGUAGE_CODE --sample-rate=SAMPLE_RATE

You can also receive an operation as the result of the command by running:

    $ gcloud ml speech recognize-long-running AUDIO_FILE \
        --language-code=LANGUAGE_CODE --sample-rate=SAMPLE_RATE --async

This will return information about an operation. To get information about
the operation, run:

    $ gcloud ml speech operations describe OPERATION_ID

To poll the operation until it's complete, run:

    $ gcloud ml speech operations wait OPERATION_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/speech/recognize-long-running)

---

## `gcloud ml speech operations` — interact with Google Cloud Speech operations
### `gcloud ml speech operations describe`

Get description of a long-running speech recognition operation

Get information about a long-running speech recognition operation.

**Synopsis:**
```
gcloud ml speech operations describe OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to describe. This represents
a Cloud resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
To fetch details for the operation '12345':

    $ gcloud ml speech operations describe 12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/speech/operations/describe)

---
### `gcloud ml speech operations wait`

Poll long-running speech recognition operation until it completes

Poll a long-running speech recognition operation until it completes. When
the operation is complete, this command will display the results of the
transcription.

**Synopsis:**
```
gcloud ml speech operations wait OPERATION [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - The ID of the operation to wait for. This represents
a Cloud resource.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the operation attribute:
     + provide the argument operation on the command line.
```

**Examples:**
```bash
To wait for the result of operation '12345':

    $ gcloud ml speech operations wait 12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/ml/speech/operations/wait)

---