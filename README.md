# Offline Speech Recognition Research

A small research project comparing transcription errors across open speech-recognition models
in ten languages. The aim is to explore how the models handle recorded speech, compression and
added noise. This repository also preserves a selection of model downloads with source credits,
licences and checksums. No models were trained here.

## Word Error Rate by Model

**Measured 10 November 2026. Lower is better.** Each row uses the same 20 source recordings
within its language, tested clean, after MP3 compression, and with added noise.
Compare models within a language, not across different languages.

| Language | Model | Clean WER | MP3 WER | Noisy WER |
|---|---|---:|---:|---:|
| English | [Moonshine Small streaming](https://github.com/moonshine-ai/moonshine) | 7.13% | 5.46% | 14.73% |
| English | [Whistle](https://huggingface.co/Cactus-Compute/whistle) | 9.74% | 9.50% | 15.91% |
| English | [Moonshine Tiny streaming](https://github.com/moonshine-ai/moonshine) | 18.53% | 13.30% | 23.99% |
| Hebrew | [Zipformer2 66M INT8](https://huggingface.co/ivrit-ai/zipformer2-66m-streaming-he) | 26.10% | 26.10% | 37.83% |
| Hebrew | [Kroko Community 64-L streaming](https://huggingface.co/Banafo/Kroko-ASR) | 34.02% | 35.48% | 42.23% |
| Arabic | [Moonshine Tiny streaming](https://github.com/moonshine-ai/moonshine) | 22.62% | 23.14% | 29.82% |
| German | [Kroko Community 64-L streaming](https://huggingface.co/Banafo/Kroko-ASR) | 12.50% | 13.02% | 15.36% |
| German | [Moonshine Small streaming](https://github.com/moonshine-ai/moonshine) | 14.84% | 15.89% | 36.98% |
| German | [Moonshine Tiny streaming](https://github.com/moonshine-ai/moonshine) | 18.49% | 18.23% | 52.34% |
| German | [Whistle](https://huggingface.co/Cactus-Compute/whistle) | 26.04% | 26.82% | 45.57% |
| Spanish | [Moonshine Small streaming](https://github.com/moonshine-ai/moonshine) | 8.53% | 8.74% | 10.45% |
| Spanish | [Moonshine Tiny streaming](https://github.com/moonshine-ai/moonshine) | 8.96% | 8.96% | 12.15% |
| Spanish | [Whistle](https://huggingface.co/Cactus-Compute/whistle) | 12.79% | 14.29% | 16.63% |
| French | [Kroko Community 64-L streaming](https://huggingface.co/Banafo/Kroko-ASR) | 8.52% | 8.74% | 15.92% |
| French | [Zipformer FR INT8](https://huggingface.co/shaojieli/sherpa-onnx-streaming-zipformer-fr-2023-04-14) | 13.00% | 13.23% | 23.09% |
| French | [Whistle](https://huggingface.co/Cactus-Compute/whistle) | 19.06% | 19.51% | 42.60% |
| Italian | [Kroko Community 64-L streaming](https://huggingface.co/Banafo/Kroko-ASR) | 4.89% | 4.89% | 5.87% |
| Italian | [Whistle](https://huggingface.co/Cactus-Compute/whistle) | 13.69% | 13.20% | 21.27% |
| Portuguese (Brazil) | [Kroko Community 64-L streaming](https://huggingface.co/Banafo/Kroko-ASR) | 9.48% | 9.05% | 11.42% |
| Russian | [T-one (greedy, no language model)](https://github.com/voicekit-team/T-one) | 13.37% | 13.37% | 21.45% |
| Russian | [Vosk small streaming INT8](https://huggingface.co/alphacep/vosk-model-small-streaming-ru) | 13.93% | 15.88% | 17.27% |
| Turkish | [Kroko Community 64-L streaming](https://huggingface.co/Banafo/Kroko-ASR) | 9.51% | 8.93% | 10.95% |

These are measured transcription errors, not a percentage of failed recordings. All 1,320 speech
runs in this table completed without a reported execution error. A completed run can still
produce an inaccurate transcript, as the WER values show.

### How the Errors Were Measured

- **Data:** 200 human read-speech recordings, 20 per language, from the
  [FLEURS validation split](https://huggingface.co/datasets/google/fleurs)
  (CC BY 4.0), revision `70bb2e84b976b7e960aa89f1c648e09c59f894dd`,
  source indices 6 through 25 in each language.
- **Conditions:** clean recordings; a 64 kbps MP3 encode/decode round trip; and synthetic white
  noise at 15 dB signal-to-noise ratio. The three versions share the same source recording and
  are not independent samples.
- **Metric:** WER = 100 x (substitutions + deletions + insertions) / reference words.
  Counts are pooled over all 20 recordings, not averaged per recording.
- **Normalization:** Unicode NFC and case folding; punctuation separates words, except apostrophes
  are removed. Diacritics are retained. Written numbers and digits are not treated as equivalent.
  The table uses this basic WER consistently, not the more permissive accent-folded score.
- **Silence check:** each of the 22 model/language combinations also received one four-second
  silent file. All returned empty transcripts. One control per combination is not enough to
  establish general resistance to hallucination.
- **Scope:** offline, unpaced file transcription. This is not a live microphone, latency, battery
  or memory benchmark. Conversational slang, dialect coverage and real-world background noise
  were not tested.

Twenty recordings per language is a small sample, not a definitive ranking. Differences of a few
percentage points may not hold on a larger corpus. The recordings are public; absence from model
training data has not been established. Additional speakers and spontaneous speech are needed
before drawing broader conclusions. Audio and per-utterance transcripts are not included in this
repository.

## Model Downloads

A subset of the tested models is preserved in
[`models-v1`](https://github.com/JacobTheJacobs/stt-models/releases/tag/models-v1).
This is a research snapshot, not a claim that every mirrored model has the lowest error.
For example, T-one has lower clean WER than Vosk in this sample, while Vosk has lower noisy WER.

[`manifest.json`](manifest.json) contains the exact source revisions, file names, download URLs,
byte sizes and SHA-256 hashes. Verify sizes and hashes after downloading. Model weights are release
assets, not Git source files.

<details>
<summary>Available models, runtimes, sizes and licences</summary>

| Code | Language | Model | Runtime | Size | Licence |
|---|---|---|---|---|---|
| `he` | Hebrew | Zipformer2 66M streaming Hebrew INT8 | sherpa-onnx | 72.3 MB | CC BY 4.0 |
| `fr` | French | Kroko Community 64-L streaming FR | sherpa-onnx | 155.8 MB to run (311.7 MB with the original container) | CC BY-SA |
| `de` | German | Kroko Community 64-L streaming DE | sherpa-onnx | 155.8 MB to run (311.7 MB with the original container) | CC BY-SA |
| `tr` | Turkish | Kroko Community 64-L streaming TR | sherpa-onnx | 155.8 MB to run (311.7 MB with the original container) | CC BY-SA |
| `pt-BR` | Portuguese (Brazil) | Kroko Community 64-L streaming PT | sherpa-onnx | 155.8 MB to run (311.7 MB with the original container) | CC BY-SA |
| `it` | Italian | Kroko Community 64-L streaming IT | sherpa-onnx | 155.8 MB to run (311.7 MB with the original container) | CC BY-SA |
| `en` | English | Moonshine Small streaming English | moonshine | 142.5 MB | MIT |
| `es` | Spanish | Moonshine Small streaming Spanish | moonshine | 121.8 MB | MIT |
| `ar` | Arabic | Moonshine Tiny streaming Arabic | moonshine | 32.3 MB | MIT |
| `ru` | Russian | Vosk small streaming Russian INT8 | sherpa-onnx | 27.8 MB | Apache 2.0 |

Kroko downloads include both the original container and its extracted payloads. The runtime only
needs the extracted files; downloading both doubles the storage. The complete release contains
57 assets totaling approximately 1.96 GB.

</details>

## Files are unmodified

Every file is a byte-for-byte copy of the file published at the source and revision listed, checked
by size and SHA-256 against the original download. Nothing was retrained, converted or
re-quantised.

The Kroko models are the one case where a file was unpacked. Kroko publishes each Community model as
a single `.data` container: a small JSON header followed by four length-prefixed payloads. For
each Kroko language this release carries both the original, unmodified container
(`<lang>-kroko-community.data`) and the four payloads extracted from it without any change to their
bytes (`encoder.onnx`, `decoder.onnx`, `joiner.onnx`, `tokens.txt`), which is the layout the
sherpa-onnx runtime loads. The extracted files are a derivative of the container and are shared
under the same CC BY-SA terms.

## Licences and attribution

### Hebrew: CC BY 4.0

"zipformer2-66m-streaming-he" by **Yakov Kolani and ivrit.ai**, licensed under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Copied from
<https://huggingface.co/ivrit-ai/zipformer2-66m-streaming-he>, which mirrors Yakov Kolani's original
<https://huggingface.co/thewh1teagle/zipformer2-66m-streaming-he>. No changes were made. The model
card states: "CC-BY-4.0. Base model from k2-fsa/icefall (Apache-2.0). Trained on audio from
ivrit.ai." Licence text: [`LICENSES/CC-BY-4.0.txt`](LICENSES/CC-BY-4.0.txt).

### French, German, Turkish, Portuguese, Italian: CC BY-SA

"Kroko ASR" Community models by **Banafo / Kroko** (<https://kroko.ai/>), copied from
<https://huggingface.co/Banafo/Kroko-ASR>. The publisher's model card describes them as
"Community Models (free, open-source). Licensed under **CC-BY-SA**" and states "Models licensed
separately (CC-BY-SA community or commercial OEM)". The publisher does not name a licence version;
the current version, [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/), is reproduced
in [`LICENSES/CC-BY-SA-4.0.txt`](LICENSES/CC-BY-SA-4.0.txt). Changes: the container was unpacked as
described above; the model data is otherwise unchanged. Anything you build from these files and
share must carry the same licence and this attribution.

### English, Spanish, Arabic: MIT

Moonshine streaming models, Copyright (c) 2025 Useful Sensors, Inc. (dba Moonshine AI), from
<https://github.com/moonshine-ai/moonshine>. That repository's LICENSE states: "Moonshine models are
released under the MIT License by default, in every language and at every size. This includes all
streaming speech-to-text models and all English-language models." All three models here are
streaming models; none is one of the legacy non-streaming models that remain under the
non-commercial Moonshine Community License. The copyright and permission notice is in
[`LICENSES/MIT-Moonshine.txt`](LICENSES/MIT-Moonshine.txt). The licence was read at repository
commit `d8d8fa29d05ca67441a7719e70099f9f48917a93`.

### Russian: Apache 2.0

"Vosk Small Russian Model, streaming version" (version 0.54) by **Alpha Cephei**
(<https://alphacephei.com/vosk>), from <https://huggingface.co/alphacep/vosk-model-small-streaming-ru>,
licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0). No
changes were made. Licence text: [`LICENSES/Apache-2.0.txt`](LICENSES/Apache-2.0.txt).

## Disclaimer

The models are provided as is, without warranty of any kind, as stated in their licences.
