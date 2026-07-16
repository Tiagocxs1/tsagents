---
name: audio-sound-design
description: >
  Sound design and audio production toolkit — SFX generation, TTS, STT, and audio processing.
  Use when generating sound effects, synthesizing voice, transcribing audio, or searching sounds.
---

# Audio & Sound Design

## Sound Effects (SFX)
- **bfxr2** (`sfx-bfxr` MCP): 5 tools, SFX retro (laser, explosion, powerup, hit, jump, blip). Gratuito, MIT.
- **Freesound** (`freesound` MCP): `search_sounds(query)`. API key: `fkNUFctbZQ6PtOg95UXY`. Instalado em `mcps/freesound-mcp-server/`. Gratuito.

## Text-to-Speech (TTS)
- **Kokoro-TTS** (`kokoro-tts` MCP, Node.js): 67 vozes, PT-BR (`pf_dora`/`pm_alex`/`pm_santa`). `text_to_speech(text,voice?,speed?)`. `npm i -g @ross_tchnologies/kokoro-tts-mcp-server`. Gratuito.
- **Web Speech API** (browser): Francisca Neural, Antonio Neural (PT-BR nativo). `useSpeech()` hook. Gratuito.
- **edge-tts** (Python): ~400 vozes, `pt-BR-Francisca`. Gratuito.

## Speech-to-Text
- **faster-whisper**: CTranslate2, multilíngue, local. Gratuito.

## Audio Processing
- librosa (BPM/pitch), pydub (corte/mix), soundfile (I/O), torchaudio, soxr
- FFmpeg: `C:\ffmpeg\bin\ffmpeg.exe`

## Workflows
- **SFX**: Freesound search → bfxr2 gen → FFmpeg mix
- **Narração**: Kokoro `pf_dora` → MP3 → FFmpeg sync video
- **Transcrição**: faster-whisper → legendas SRT
