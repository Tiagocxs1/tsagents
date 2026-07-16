---
name: hyperframes-heygen
description: HeyGen HyperFrames — open-source framework for turning HTML, CSS, media, and seekable animations into deterministic MP4 videos. Built for agents.
metadata:
  tags: video, rendering, html-to-video, animation, agent, hyperframes
---

# HyperFrames (heygen-com/hyperframes)

Framework open-source para converter HTML + CSS + mídia + animações seekable em vídeos MP4 determinísticos. Feito para agentes de IA (Claude Code, Cursor, Gemini CLI, Codex, OpenCode).

## Repositório local

Clonado em:
```
C:\Users\Admin\Desktop\TS Digitais\IA\.ia-config\vendor\hyperframes
```

GitHub: https://github.com/heygen-com/hyperframes
npm: `hyperframes`
Docs: https://hyperframes.heygen.com/introduction
Playground: https://www.hyperframes.dev/
Showcase: https://hyperframes.heygen.com/showcase

## Como usar

### Instalação via agent (recomendada)

```bash
npx skills add heygen-com/hyperframes --full-depth --yes
```

Use `--full-depth` para clone completo (skills.sh blob pode estar desatualizado). Instala 20 skills que ensinam o agente o ciclo de produção.

Para instalar todas de uma vez:
```bash
npx skills add heygen-com/hyperframes --all --full-depth
```

### Uso

Com os skills instalados, descreva o vídeo desejado:
> Using /hyperframes, create a 10-second product intro with a fade-in title, a background video, and subtle background music.

Ou invoque workflows específicos:

| Workflow | Uso |
|----------|-----|
| `/product-launch-video` | Marketing/lançamento de produto (URL ou brief) |
| `/website-to-video` | Tour de site, showcase de landing page |
| `/faceless-explainer` | Explicar tópico sem vídeo de referência |
| `/pr-to-video` | Transformar PR do GitHub em changelog video |
| `/embedded-captions` | Adicionar legendas a talking-head existente |
| `/talking-head-recut` | Empacotar talking-head com overlays gráficos |
| `/motion-graphics` | Motion graphic curto (~10s) — kinetic type, lower-thirds |
| `/music-to-video` | Vídeo beat-synced a partir de track de áudio |
| `/slideshow` | Deck navegável (não renderizado) |
| `/general-video` | Fallback — qualquer peça multi-cena |
| `/remotion-to-hyperframes` | Portar composição Remotion para HTML HyperFrames |

### Domain skills (carregados sob demanda)

- `/hyperframes-core` — contrato de composição: `data-*` timing, `class="clip"`, tracks, variáveis, regras de determinismo
- `/hyperframes-animation` — regras de animação, blueprints de cena, transições, adaptadores (GSAP/Lottie/Three.js/Anime.js/CSS/WAAPI/TypeGPU)
- `/hyperframes-keyframes` — Authoring de keyframes seek-safe (GSAP timelines, CSS, Anime.js, WAAPI, FLIP, SVG morph, 3D)
- `/hyperframes-creative` — Direção criativa: paletas, tipografia, narração, beat planning, áudio-reativo
- `/media-use` — Resolver mídia (BGM, SFX, imagem, ícone, logo, voz), gerar via TTS/música/imagem, transcrever, legendar
- `/hyperframes-cli` — Loop dev CLI: `init`, `lint`, `check`, `snapshot`, `preview`, `render`, `publish`, `doctor`, Lambda cloud rendering
- `/hyperframes-registry` — Instalar/wire registry blocks e componentes via `hyperframes add`
- `/figma` — Importar assets Figma, tokens, componentes em composições

### CLI manual

```bash
npm install -g hyperframes
# ou
npx hyperframes
```

Comandos: `hyperframes init`, `hyperframes preview`, `hyperframes render`, `hyperframes publish`

## Dependências

- Node.js >= 22
- npm
- ffmpeg (para alguns codecs/outputs)
- Navegador Chromium (bundled pelo HyperFrames)

## Notas

- HyperFrames é o mecanismo de renderização recomendado para animation overlays do video-use
- 20 skills agent-first, cada uma com SKILL.md dedicado
- Suporta rendering local e cloud (AWS Lambda)
- Determinístico: mesmo HTML → mesmo MP4 (ideal para agentes)
