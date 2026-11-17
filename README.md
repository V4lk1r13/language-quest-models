# language-quest-models

Speech models downloaded on demand by the **Language Quest** Android app.
The app fetches each archive from this repository's releases and falls back to the original
[k2-fsa/sherpa-onnx releases](https://github.com/k2-fsa/sherpa-onnx/releases) if a download fails.

Every archive is redistributed **unchanged** from sherpa-onnx. Each one still contains its original
`MODEL_CARD` and licence files. Do not edit or remove them.

## Releases

| Release tag | Contents |
|---|---|
| `tts-models` | Piper voices (text to speech), one `.tar.bz2` per voice |
| `asr-models` | Speech recognition: Whisper tiny, and the optional Russian Zipformer |

Download URL pattern used by the app:

```
https://github.com/V4lk1r13/language-quest-models/releases/download/<tag>/<archive>.tar.bz2
```

## Credits and licences

The software that runs these models is licensed separately from the models themselves.
**Each voice carries the licence of the recordings it was trained on.** That licence comes from the voice's
`MODEL_CARD`, not from this repository.

### Voices (`tts-models`)

| Archive | Language | Dataset (from MODEL_CARD) | Dataset licence (from MODEL_CARD) | Fine-tuned from |
|---|---|---|---|---|
| `vits-piper-de_DE-thorsten-medium` | German | [Thorsten-Voice](https://github.com/thorstenMueller/Thorsten-Voice) by Thorsten Müller | CC0 1.0 | Piper "lessac" (en_US) |
| `vits-piper-fr_FR-siwis-medium` | French | SIWIS French Speech Synthesis Database | CC BY 4.0 | see MODEL_CARD |
| `vits-piper-es_ES-sharvard-medium` | Spanish | [Sharvard corpus](https://datashare.ed.ac.uk/handle/10283/574), University of Edinburgh | CC BY 3.0 | see MODEL_CARD |
| `vits-piper-en_GB-alba-medium` | English (UK) | see MODEL_CARD | see MODEL_CARD (to be confirmed) | see MODEL_CARD |
| `vits-piper-zh_CN-huayan-medium` | Mandarin | [HuaYan_TTS](https://github.com/PlayVoice/HuaYan_TTS) | **Unknown** | Piper "lessac" (en_US) |
| `vits-piper-ru_RU-irina-medium` | Russian | [RHVoice](https://github.com/RHVoice/RHVoice) | **Unknown** | Piper "lessac" (en_US) |

Attribution required by CC BY voices:

- French voice: "SIWIS French Speech Synthesis Database", CC BY 4.0, https://creativecommons.org/licenses/by/4.0/
- Spanish voice: "Sharvard corpus", University of Edinburgh, CC BY 3.0, https://creativecommons.org/licenses/by/3.0/

Notes on use:

- Several Piper voices were fine-tuned from the Piper "lessac" voice. That voice was trained on the
  Blizzard 2013 Lessac recordings, whose licence limits use to research purposes. The Piper project says it
  "is intended for text to speech research" and does not add its own licence. Get your own advice before
  using any voice built on lessac in a paid product.
- The Mandarin (huayan) and Russian (irina) voices list their dataset licence as **Unknown**. Treat them as
  personal use only until their licences are confirmed.
- The app plays the voices with sherpa-onnx (Apache 2.0). It does not use the Piper engine code. The voice
  files are in Piper's format.
- Each voice archive also contains an `espeak-ng-data` folder from eSpeak NG (GPL-3.0). sherpa-onnx uses it to
  turn text into phonemes. Credit it as GPL-3.0 data.
- Piper's development moved in 2025. The original rhasspy/piper repository (MIT) was archived in October 2025.
  Work continues at [OHF-Voice/piper1-gpl](https://github.com/OHF-Voice/piper1-gpl) (GPL-3.0) under the Open
  Home Foundation. The voice files mirrored here are the published Piper voices, and each keeps its own
  dataset licence.

### Speech recognition (`asr-models`)

| Archive | Model | Licence |
|---|---|---|
| `sherpa-onnx-whisper-tiny` | OpenAI Whisper tiny, ONNX export by sherpa-onnx | MIT (OpenAI Whisper code and weights) |
| `sherpa-onnx-streaming-zipformer-small-ru-vosk-int8-2025-08-16` | Vosk small Russian Zipformer (Alpha Cephei), trained with k2-fsa/icefall | Apache 2.0 |

### Tools

- [sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx), Apache 2.0: packaging of all archives
- [Piper](https://github.com/OHF-Voice/piper1-gpl): trained the voices (original repository rhasspy/piper, MIT, archived; current repository GPL-3.0)
- [eSpeak NG](https://github.com/espeak-ng/espeak-ng), GPL-3.0: `espeak-ng-data` phoneme data inside each voice archive

## Integrity

`SHA256SUMS.txt` in each release lists the SHA-256 checksum of every archive. Create it when uploading:

```bash
sha256sum *.tar.bz2 > SHA256SUMS.txt
```

## Disclaimer

This repository only mirrors files that are already public. It is not a lawyer's opinion on any licence.
If a rights holder asks for a file to be removed, it will be removed.
