# stt-models

Open speech-recognition models for offline, on-device use, one per language. This repository
holds only text: this README, a machine-readable [`manifest.json`](manifest.json) and the licence
texts in [`LICENSES/`](LICENSES). The model files themselves are assets of the release
[`models-v1`](https://github.com/JacobTheJacobs/stt-models/releases/tag/models-v1)
(57 files, 1.96 GB).

None of these models were trained here. They are redistributed from their publishers under the
licences listed below, and all credit belongs to those publishers.

## Models

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

Download URLs have the form
`https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/<asset>`.
Asset names are `<language>-<model>-<original file name>`; `manifest.json` maps each asset back to
the file name the runtime expects, with its byte size and SHA-256. Verify both after downloading.

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

## Per-model files

### `he` Hebrew: Zipformer2 66M streaming Hebrew INT8

- Licence: CC BY 4.0
- Source: <https://huggingface.co/ivrit-ai/zipformer2-66m-streaming-he>
- Revision: `ee769a2a13b887f91572eec349458bfb0fe79e7a`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `encoder.int8.onnx` | [`he-zipformer-encoder.int8.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/he-zipformer-encoder.int8.onnx) | 70478964 | `6c6febcb74a09435315a1d872a6539f6e7fc2c333533f14c74edc0e85c49ffcd` |
| `decoder.int8.onnx` | [`he-zipformer-decoder.int8.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/he-zipformer-decoder.int8.onnx) | 1049105 | `feb03e7c8aa761593a9284a6fa1e91259be3702de75f630062256c1a59c5a906` |
| `joiner.int8.onnx` | [`he-zipformer-joiner.int8.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/he-zipformer-joiner.int8.onnx) | 771805 | `1d2c6d8e6dabc5eb52de52e95718e9bdfbffbfe7ead3808fb5ffd74e83bd9cae` |
| `tokens.txt` | [`he-zipformer-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/he-zipformer-tokens.txt) | 17086 | `e4ebb5e72a6aeef47437a55fa2308ebbedb7c51c557de7a89bf965c23ea9af4a` |

### `fr` French: Kroko Community 64-L streaming FR

- Licence: CC BY-SA
- Source: <https://huggingface.co/Banafo/Kroko-ASR>
- Revision: `d45212aeb212dd66083dd22710c9954f40ff8cc1`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `Kroko-FR-Community-64-L-Streaming-001.data` | [`fr-kroko-community.data`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/fr-kroko-community.data) | 155839318 | `1af97abc84f28c6765e50d62307d1ac477b50e7fc2e62d6704d6288e7c863d80` |
| `encoder.onnx` | [`fr-kroko-encoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/fr-kroko-encoder.onnx) | 154878660 | `2056f2f0ef052d3c64877c43b89863a665f1ded54dd7ee047c5daf28e3dab331` |
| `decoder.onnx` | [`fr-kroko-decoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/fr-kroko-decoder.onnx) | 617488 | `8646191d6b8bc3d6907f981cbf73ccff40c6ce88c8fd475a5e3b811e7d5281f8` |
| `joiner.onnx` | [`fr-kroko-joiner.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/fr-kroko-joiner.onnx) | 336817 | `bce63118d73bc651cd61e82d3ddc2f49c5c4780324aaed78451590aceb999bf2` |
| `tokens.txt` | [`fr-kroko-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/fr-kroko-tokens.txt) | 6197 | `4416e94e9322203a580830c9a8a14e89959882f512b8fdda10d7fe3182097eb7` |

### `de` German: Kroko Community 64-L streaming DE

- Licence: CC BY-SA
- Source: <https://huggingface.co/Banafo/Kroko-ASR>
- Revision: `d45212aeb212dd66083dd22710c9954f40ff8cc1`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `Kroko-DE-Community-64-L-Streaming-001.data` | [`de-kroko-community.data`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/de-kroko-community.data) | 155839333 | `0013d4b3e1216b4e0c15f18f345aa58ca8bb2cdbeff7a7d55a513f6b400862a5` |
| `encoder.onnx` | [`de-kroko-encoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/de-kroko-encoder.onnx) | 154878660 | `c973664ab297df99faa5b7fc1eb8addabe468a323682cb40af98dc0ec13e985d` |
| `decoder.onnx` | [`de-kroko-decoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/de-kroko-decoder.onnx) | 617488 | `57cfda432138d2a552acfac9a052d8f2157eb9a93774d0cbf997601a2cb0aae5` |
| `joiner.onnx` | [`de-kroko-joiner.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/de-kroko-joiner.onnx) | 336817 | `a9e3759823edbe3e78c5cc114384757ebcb43db3b9cb9ce1e13b4be873e116bf` |
| `tokens.txt` | [`de-kroko-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/de-kroko-tokens.txt) | 6212 | `540e317d5b171908ab109dbe9faa37ae8b05e1fa9b8c87fcc40654efba466965` |

### `tr` Turkish: Kroko Community 64-L streaming TR

- Licence: CC BY-SA
- Source: <https://huggingface.co/Banafo/Kroko-ASR>
- Revision: `d45212aeb212dd66083dd22710c9954f40ff8cc1`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `Kroko-TR-Community-64-L-Streaming-001.data` | [`tr-kroko-community.data`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/tr-kroko-community.data) | 155838546 | `2f75336ba36b2464bcf062f7f6c8611fe2539cab17351ed7ed4ee1a03ed437a4` |
| `encoder.onnx` | [`tr-kroko-encoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/tr-kroko-encoder.onnx) | 154878660 | `d36d8abbcbd9d87c5446f296b59a9fce26ccd87c7edb278f61631ef3d02803a2` |
| `decoder.onnx` | [`tr-kroko-decoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/tr-kroko-decoder.onnx) | 617489 | `08f317129a6ffed14f8755e61d50b1df6ac1cc5af3bdd832b7ea93961199217e` |
| `joiner.onnx` | [`tr-kroko-joiner.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/tr-kroko-joiner.onnx) | 336817 | `aa49f0e96e4ef5ea408cb09f4b2ef5785995513b21fd8f04675d2f5f0ffcd1f3` |
| `tokens.txt` | [`tr-kroko-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/tr-kroko-tokens.txt) | 5423 | `c7e93bbc0f57852154df4e52005ae163d653f3daf0d1dbeb4f75a3ffa4b25c57` |

### `pt-BR` Portuguese (Brazil): Kroko Community 64-L streaming PT

- Licence: CC BY-SA
- Source: <https://huggingface.co/Banafo/Kroko-ASR>
- Revision: `d45212aeb212dd66083dd22710c9954f40ff8cc1`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `Kroko-PT-Community-64-L-Streaming-001.data` | [`pt-BR-kroko-community.data`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/pt-BR-kroko-community.data) | 155839360 | `36c4a92f25c9243cbd8f007cfc624b09986debf2919a1e397891e62e063d0e61` |
| `encoder.onnx` | [`pt-BR-kroko-encoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/pt-BR-kroko-encoder.onnx) | 154878660 | `336b9a62fd37d8b94855fcbe0414000aa5f1bd75d4cb907e112bd6b7ef97c52e` |
| `decoder.onnx` | [`pt-BR-kroko-decoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/pt-BR-kroko-decoder.onnx) | 617488 | `2380832dbb1867779a550aea3948776d6a53ffa1cccd075bb7592ebaf21b7638` |
| `joiner.onnx` | [`pt-BR-kroko-joiner.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/pt-BR-kroko-joiner.onnx) | 336817 | `de7afbc23e7e55af7fed85780690b8f883c62b881fe14d546d9677151581962f` |
| `tokens.txt` | [`pt-BR-kroko-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/pt-BR-kroko-tokens.txt) | 6235 | `e9b9b588c138558388c9a53385007082f58130a0ceddce8df6a4aed032162b3f` |

### `it` Italian: Kroko Community 64-L streaming IT

- Licence: CC BY-SA
- Source: <https://huggingface.co/Banafo/Kroko-ASR>
- Revision: `d45212aeb212dd66083dd22710c9954f40ff8cc1`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `Kroko-IT-Community-64-L-Streaming-001.data` | [`it-kroko-community.data`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/it-kroko-community.data) | 155839229 | `e74cd91f89970639476353cfb7ba5044da10e36d8fb99c3a7a41c8b7c253726d` |
| `encoder.onnx` | [`it-kroko-encoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/it-kroko-encoder.onnx) | 154878660 | `81c436e4f1cc381276859c858e3e881e382d0e0ca77a21bea1fde74c1275f6b2` |
| `decoder.onnx` | [`it-kroko-decoder.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/it-kroko-decoder.onnx) | 617488 | `f9c8093a12cb93b14e82f9205f1c4f57cb19143e0cca0079c6770c717611961c` |
| `joiner.onnx` | [`it-kroko-joiner.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/it-kroko-joiner.onnx) | 336817 | `3056ae55986ba4fb6203599baaeebb5f7eeb776798c3146df3bf76a198d172a9` |
| `tokens.txt` | [`it-kroko-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/it-kroko-tokens.txt) | 6107 | `6c1ce19563e9fa59cc05ad921ccc31106497c1e2895346e2aa3fa936a103ed39` |

### `en` English: Moonshine Small streaming English

- Licence: MIT
- Source: <https://download.moonshine.ai/model/small-streaming-en/quantized_26_11_02/>
- Revision: `quantized_26_11_02`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `adapter.ort` | [`en-moonshine-small-adapter.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-adapter.ort) | 2870320 | `100d4806a3ba19b739fa9ae5c952e4d5267983090eea4a085e08d3e0bfd6875b` |
| `cross_kv.ort` | [`en-moonshine-small-cross_kv.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-cross_kv.ort) | 5356496 | `aa0ed033b7065ef744c36dce00228c708b43f2f2410e8ec782a960105c8595f7` |
| `decoder_kv.ort` | [`en-moonshine-small-decoder_kv.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-decoder_kv.ort) | 82043616 | `e4fae3869851b861177b5e1619c77ec9262365b2747ec322298d11753e88b38d` |
| `encoder.ort` | [`en-moonshine-small-encoder.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-encoder.ort) | 44148536 | `f61486dc7b017cee99196366dcc977a173f45f2f387b0b7977695d0f0565d234` |
| `frontend.model.ort` | [`en-moonshine-small-frontend.model.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-frontend.model.ort) | 26992 | `4a8d5ef7e99a5e3011dbf09ffac4176056587f2aec20f885d606b9f55fbed408` |
| `frontend.weights.ort` | [`en-moonshine-small-frontend.weights.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-frontend.weights.ort) | 7769416 | `5379f3dfebe849c6cbacf84f0aa7441956f9572efe1720d44aa267e7dff93056` |
| `streaming_config.json` | [`en-moonshine-small-streaming_config.json`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-streaming_config.json) | 512 | `26f02b6afb22d60871a5efd85c3d38e569cc0ddb6c5eb6e93d3260152ae8a47a` |
| `tokenizer.bin` | [`en-moonshine-small-tokenizer.bin`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/en-moonshine-small-tokenizer.bin) | 249974 | `6884b35fd6377d4c4d32336a0bc152f36b64d1e45b6503683cdc238250a8472d` |

### `es` Spanish: Moonshine Small streaming Spanish

- Licence: MIT
- Source: <https://download.moonshine.ai/model/small-streaming-es/quantized_26_08_24/>
- Revision: `quantized_26_08_24`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `adapter.ort` | [`es-moonshine-small-adapter.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-adapter.ort) | 2869296 | `04b54114c8aab534222922640f7ca0882948ff9f6ed76777f6e184e55a8e8b15` |
| `cross_kv.ort` | [`es-moonshine-small-cross_kv.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-cross_kv.ort) | 5358752 | `4bfd0a641d72ccdae22751f86bbb2e25ff70c1fba4f81213f2415a1accff9618` |
| `decoder_kv.ort` | [`es-moonshine-small-decoder_kv.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-decoder_kv.ort) | 61314512 | `5b77c3d6baf801ef925a5bc54d7eb3db0c35ebbb86f8eaf5390d7f5bb42fef37` |
| `encoder.ort` | [`es-moonshine-small-encoder.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-encoder.ort) | 44358376 | `a9b8d6d5d9348d0e319cceffdb0196ef622df8e4e9f3fb4797dcd8dfafd50857` |
| `frontend.model.ort` | [`es-moonshine-small-frontend.model.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-frontend.model.ort) | 26776 | `69c76287f49db365aa278d4908ec450e69ca1b4bfb7e836159d963d623ee0c13` |
| `frontend.weights.ort` | [`es-moonshine-small-frontend.weights.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-frontend.weights.ort) | 7769280 | `2f5a0eb5f3004c9447810d74274a352746319a32144e31d95ef410f425b84dda` |
| `streaming_config.json` | [`es-moonshine-small-streaming_config.json`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-streaming_config.json) | 512 | `12d16c7f5ea6734d197b79baf47914ea7e996d6fca8d303a19aca10d0617cecc` |
| `tokenizer.bin` | [`es-moonshine-small-tokenizer.bin`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/es-moonshine-small-tokenizer.bin) | 102888 | `5fbb7d4314dcb18e03c5f975609e4a4cd572b22b01d2b2accb1b3e6830696f36` |

### `ar` Arabic: Moonshine Tiny streaming Arabic

- Licence: MIT
- Source: <https://download.moonshine.ai/model/tiny-streaming-ar/quantized_26_08_24/>
- Revision: `quantized_26_08_24`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `adapter.ort` | [`ar-moonshine-tiny-adapter.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-adapter.ort) | 1318472 | `9c1278a338b4ff268fc5741be01446d56ca9cba9ff5f4a75c5e1b2c2e2739361` |
| `cross_kv.ort` | [`ar-moonshine-tiny-cross_kv.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-cross_kv.ort) | 1288120 | `e317af289233894f49da429d4561150c2f61ca86c1b9ca91c6edd3fb4fdeecb5` |
| `decoder_kv.ort` | [`ar-moonshine-tiny-decoder_kv.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-decoder_kv.ort) | 19717336 | `5c9a2bf2d9fc543fd4596b3ab4ab8d09f791aac5682eb1379fd8d59e34237db0` |
| `encoder.ort` | [`ar-moonshine-tiny-encoder.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-encoder.ort) | 7772792 | `6785ca9932d59265375249a8f3bc62f8333fb4dee6ab7db8dfd6f1daef66f59e` |
| `frontend.model.ort` | [`ar-moonshine-tiny-frontend.model.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-frontend.model.ort) | 23176 | `04c552e66efe3f7206d0a69779864f93bf3cfaf2fa595c9ce5101c8e3854a414` |
| `frontend.weights.ort` | [`ar-moonshine-tiny-frontend.weights.ort`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-frontend.weights.ort) | 2093280 | `6cc4d70efffe757452996574d11065e7dac6a7ff0a9be3e2fec1d0266b062b0e` |
| `streaming_config.json` | [`ar-moonshine-tiny-streaming_config.json`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-streaming_config.json) | 509 | `d31afd7c2dd5ee9ae3fa232312c5b42cb3e4fe1c6e9c53d885f2bea63023790a` |
| `tokenizer.bin` | [`ar-moonshine-tiny-tokenizer.bin`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ar-moonshine-tiny-tokenizer.bin) | 135726 | `3acea39a89cdf44fa11f10bfdd7d05d9015d901999f8c8fa18988f19dcc6b267` |

### `ru` Russian: Vosk small streaming Russian INT8

- Licence: Apache 2.0
- Source: <https://huggingface.co/alphacep/vosk-model-small-streaming-ru>
- Revision: `e18123ee13f694036a1eea82eb43f9895387cb59`

| File | Release asset | Bytes | SHA-256 |
|---|---|---:|---|
| `encoder.int8.onnx` | [`ru-vosk-encoder.int8.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ru-vosk-encoder.int8.onnx) | 26214060 | `e0db705e94ec35d803b1df4f40cda23d064e1142977c80ab288430b109777a9d` |
| `decoder.int8.onnx` | [`ru-vosk-decoder.int8.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ru-vosk-decoder.int8.onnx) | 1326289 | `2b0df458692e1d090075c8249001136ef05240dd0d726a6b56552fd46c538b2d` |
| `joiner.int8.onnx` | [`ru-vosk-joiner.int8.onnx`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ru-vosk-joiner.int8.onnx) | 259417 | `b55784b071ab7512eab4c7c44e4f5478284ef33c83562cc6a249b972515a31e5` |
| `tokens.txt` | [`ru-vosk-tokens.txt`](https://github.com/JacobTheJacobs/stt-models/releases/download/models-v1/ru-vosk-tokens.txt) | 6388 | `93bbbc0bae6b78c0bbb743d4aa9fded3bb5ff3aac5f0200e3a769a5a05e0fdf6` |

For the Moonshine models the revision is the dated folder on the publisher's download server that
the files were fetched from. For the Hugging Face models it is the repository commit.

## How these were chosen

Each model was the best open candidate for its language in a small pilot of 20 recordings per
language, measured on a Mac and not on phones, so treat the selection as provisional.

## Disclaimer

The models are provided as is, without warranty of any kind, as stated in their licences.
