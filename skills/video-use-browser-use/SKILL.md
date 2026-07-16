---
name: video-use-browser-use
description: Edit videos with Claude Code (or any agent) via browser-use/video-use. Transcribe, cut, color grade, subtitle, and overlay animations.
metadata:
  tags: video, editing, ai-agent, ffmpeg, subtitle, transcription
---

# video-use (browser-use/video-use)

Edição de vídeo via agente de IA (Claude Code, OpenCode, Codex, Hermes). 100% open-source. Basta apontar para uma pasta com takes brutos e um agente edita para MP4 final.

## Repositório local

Clonado em:
```
C:\Users\Admin\Desktop\TS Digitais\IA\.ia-config\vendor\video-use
```

GitHub: https://github.com/browser-use/video-use

## Como usar

### Setup inicial (uma vez)

Cole este prompt no agente com acesso ao shell:
```
Set up C:\Users\Admin\Desktop\TS Digitais\IA\.ia-config\vendor\video-use for me.
Read install.md first to install this repo, wire up ffmpeg, register the skill, and set up the ElevenLabs API key - ask me to paste it when you need it.
```

O agente faz: clone, instala dependências (`uv sync` ou `pip install -e .`), configura ffmpeg, registra a skill, pede a ElevenLabs API key.

### Uso diário

1. Coloque takes brutos em uma pasta
2. Inicie o agente: `claude` (ou opencode, codex)
3. Diga: "edit these into a launch video" (ou descreva o que quer)
4. O agente transcreve → analisa → propõe estratégia → espera OK → renderiza `edit/final.mp4`

### Capacidades

- Corta filler words (`umm`, `uh`, pausas mortas)
- Auto color grading (cinematográfico quente, neutro, ou custom ffmpeg chain)
- Fades de áudio de 30ms em cada corte (sem pops)
- Legendas em estilo customizável (padrão: chunks de 2 palavras em UPPERCASE)
- Animation overlays via HyperFrames, Remotion, Manim, ou PIL
- Auto-avalia o output renderizado (max 3 tentativas de correção)
- Memória persistente em `project.md` entre sessões

### Pipeline

```
Transcribe → Pack → LLM Reasons → EDL → Render → Self-Eval
                                                      ↓
                                          issue? fix + re-render (max 3)
```

## Dependências

- ffmpeg (obrigatório)
- yt-dlp (opcional, para baixar fontes online)
- Python com `uv sync` ou `pip install -e .`
- ElevenLabs API key (para transcrição)

## Notas

- O LLM **nunca assiste** ao vídeo — ele **lê** via transcript + timeline visual composite (PNG)
- Camada 1: transcrição com timestamps por palavra + diarização de falantes (~12KB)
- Camada 2: composite visual (filmstrip + waveform + word labels) sob demanda
- Outputs ficam em `<pasta_videos>/edit/` — a pasta da skill fica limpa
- O repositório inclui helpers/ com scripts de edição
