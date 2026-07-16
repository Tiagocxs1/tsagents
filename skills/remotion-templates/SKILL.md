---
name: remotion-templates
description: Catálogo completo de templates Remotion + comandos de scaffold. Use para escolher e iniciar qualquer projeto Remotion a partir dos templates oficiais. Includes Prompt Showcase e Remotion Skills.
---

# Remotion Templates

Catálogo completo em: `.ia-config/docs/remotion-templates-reference.md`

## Como Usar

Para scaffoldar um template:
```bash
bun create video --<template-name>
# ou
npx create-video@latest --<template-name>
```

## Templates Mais Relevantes para Reels/Vídeo

| Template | Comando | Para quê |
|----------|---------|----------|
| Prompt to Video | `--prompt-to-video` | Script + imagens + voz (OpenAI + ElevenLabs) |
| TikTok | `--tiktok` | Legendas animadas palavra-por-palavra (Whisper.cpp) |
| Overlay | `--overlay` | Overlays para OBS/Premiere |
| Prompt to Motion Graphics | `--prompt-to-motion-graphics` | SaaS geração animação por prompt |
| Audiogram | `--audiogram` | Podcast → vídeo social com waveform |

## Templates SaaS

| Template | Comando |
|----------|---------|
| Next.js | `--next` |
| Render Server (Express) | `--render-server` |
| Electron | `--electron` |
| React Router 7 | `--react-router` |

## Templates Criativos

| Template | Comando |
|----------|---------|
| 3D (React Three Fiber) | `--three` |
| Skia | `--skia` |
| Code Hike | `--code-hike` |
| Stargazer | `--stargazer` |

## Remotion Skills Instaladas (8)

Use `/remotion-best-practices` como master (carrega as demais conforme necessário).
Skills individuais: create, markup, render, captions, saas, interactivity, mediabunny.

## Prompt Showcase (remotion.dev/prompts)

36+ prompts comunitários. Estrutura: tool, model, prompt text, thumbnail, source code.
Top prompts viáveis para inspiração de Reels: Travel Route Map, Cinematic Tech Intro, Transparent CTA Overlay, Product Demo.
