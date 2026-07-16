---
name: trend-intelligence
description: "Inteligencia de tendencias para conteudo digital. Classifica sinais em Modismo/Hype/Trend/Microtendencia/Contratendencia/Macrotendencia/Megatendencia + Early Adopters/Sinais Fracos. Estrategia por plataforma (TikTok vs Instagram). Integra Content Radar, Pulse CN MCP, social-media-mcp, agent-reach."
---

# Trend Intelligence

Camada de inteligencia que classifica tendencias e define estrategia de conteudo por plataforma.

## Framework de Classificacao

### Escala de Maturacao de Tendencias

Sinal Fraco (hoje) → Early Adopters (1-3a) → Microtendencia (6m-2a) → Trend (6m-2a) → Hype (semanas) → Mainstream (saturacao) → Modismo (extinto)
                                                                               ↓
                                                                   Contratendencia (2-5a)

### Tabela de Classificacao

| Termo | Janela | Assinatura | Estrategia |
|-------|--------|-----------|------------|
| **Sinal Fraco** | Hoje → 5-10 anos | Indicios isolados, laboratorios, papers, comportamento emergente em nichos minusculos | Conteudo teorico/analise de futuro. Gera autoridade + salvamentos. |
| **Early Adopters** | Hoje → 1-3 anos | Pioneiros testando, comunidades pequenas, sem cobertura mainstream | Conteudo de "antecipacao". Nicho engajado, baixa concorrencia. |
| **Microtendencia** | 6 meses - 2 anos | Hiperfocada em um nicho/comunidade, alto engajamento interno | Posts tecnicos para fidelizar nicho. Excelente para TikTok. |
| **Trend (Curto Prazo)** | 6 meses - 2 anos | Direcao visivel, adotada em redes sociais, esteticas de nicho | Tutoriais, listas, videos surfando audios/formatos do momento. |
| **Hype** | Semanas - meses | Expectativa artificial criada por marketing, lancamentos aguardados | Noticias, reviews, reacts ao vivo. Nao construir autoridade. |
| **Modismo (Fad)** | Semanas | Popularidade explosiva e passageira. Desaparece sem impacto. | Post rapido para engajar. Parar se foco for inovacao. |
| **Contratendencia** | 2-5 anos | Reacao de resistencia a uma tendencia dominante | Posts analiticos e polemicos. Altissimo engajamento em comentarios. |
| **Macrotendencia** | 5-10 anos | Mudanca estrutural que afeta multiplos setores | Conteudos educativos profundos. Imas de salvamento (Instagram). |
| **Megatendencia** | 20-30 anos | Movimento global que redefine a sociedade | Documentarios, series, reflexoes. Posicionamento de marca. |
| **Mainstream** | Ponto de saturacao | Fenomeno adotado pela massa | Parar de postar se foco for inovacao. |

## Estrategia por Plataforma

### TikTok: Velocidade e Nicho
Algoritmo focado em interesse imediato e entrega para nao-seguidores (For You).

| O que funciona | Tempo de reacao | Formato |
|---------------|:---------------:|---------|
| Hype, Trend, Microtendencia | Horas a 3 dias (max 7) | Videos curtos com audios do momento |

**Regras:**
- Hook nos primeiros 2 segundos — interromper atencao
- Audio do momento + formato reconhecivel
- Uma ideia, um demo, um CTA
- Microtendencias entregam para a bolha certa → maior chance de viralizar nichado

### Instagram: Autoridade e Comunidade
Algoritmo prioriza relacionamento e retencao.

| O que funciona | Tempo de reacao | Formato |
|---------------|:---------------:|---------|
| Trend adaptada, Contratendencia, Macrotendencia | Moderado (dias) | Reels opinativos + Carrosseis |

**Regras:**
- Nao copiar trend do TikTok — contextualizar
- Contratendencias geram altissimo engajamento em comentarios e Direct
- Macrotendencias em carrossel = "imas de salvamento"

### Cross-Platform Matrix

| Tipo | TikTok | Instagram | YouTube | LinkedIn |
|:----|:------:|:---------:|:-------:|:--------:|
| Sinal Fraco | — | Carrossel | Documentario | Thought leadership |
| Early Adopters | Antecipacao | Antecipacao visual | Video | Texto |
| Microtendencia | Otimo | Bom | Video | Texto |
| Trend | Otimo | Adaptada | Tutorial | Texto |
| Hype | React | — | Review | — |
| Contratendencia | Polemica | Otimo (debate) | Analise | Opiniao |
| Macrotendencia | Video | Otimo (salvamento) | Serie | Otimo |
| Megatendencia | — | Serie | Documentario | Artigo |

## Workflow: Sinal → Estrategia

### Fase 1: Coletar Sinais
Usar ferramentas em paralelo:

- **agent-reach** → Web, YouTube, GitHub, RSS, Reddit, X
- **Pulse CN MCP** → 18 plataformas chinesas (Weibo, Douyin, Bilibili, Zhihu, Baidu)
- **social-media-mcp** → 649 tools (YouTube, LinkedIn, FB, IG, TikTok, X)
- **Content Radar** → `content_radar.py --keyword X --days 7`
- **content-radar-news** → Noticias em tempo real
- **content-radar-rss** → RSS feeds
- **content-radar-agent-news** → Noticias verificadas
- **n8n-mcp** → 2.352 templates de workflow
- **china-bridge** → Fornecedores e tendencias de sourcing

### Fase 2: Classificar
Classificar sinal em UM dos 10 tipos.

**Perguntas:**
- Alcance atual? (nicho / comunidade / setor / massa)
- Ha quanto tempo existe? (dias / meses / anos / decadas)
- Crescendo ou saturando? (momentum)
- Quem esta falando? (pioneiros / early adopters / imprensa / massa)
- Existe reacao contraria? (contratendencia)
- Potencial de profundidade? (modismo passageiro ou mudanca estrutural?)

### Fase 3: Estrategia de Conteudo
Para cada classificacao gerar:
1. Formato recomendado (Reel, Carrossel, Post, Thread, Video, Serie)
2. Angulo principal (hook + abordagem)
3. CTA especifico (salvar, comentar, compartilhar, clicar)
4. Timing ideal (imediato, essa semana, esse mes)
5. O que NAO fazer (anti-padroes)

### Fase 4: Produzir e Publicar
trend-intelligence → copy-engineering → content-engine → copy-thief → audio-sound-design → video-editing → banner-design → social-publishing

## Metricas de Performance

| Tipo de Post | Principal Metrica | Plataforma |
|-------------|:----------------:|:----------:|
| Hype/Trend | Views / Compartilhamentos | TikTok |
| Microtendencia | Engajamento do nicho | TikTok |
| Contratendencia | Comentarios / Directs | Instagram |
| Macrotendencia | Salvamentos | Instagram / LinkedIn |
| Early Adopters | Seguidores novos | TikTok / Instagram |
| Sinal Fraco | Autoridade / Citacoes | LinkedIn / YouTube |

## Sistema de Trend Score

| Fonte | Peso | Ferramenta |
|------|:----:|-----------|
| Google Trends | 0.30 | Content Radar |
| News API | 0.20 | Content Radar |
| Reddit | 0.15 | Content Radar / agent-reach |
| Pulse CN | 0.15 | Pulse CN MCP |
| X / Twitter | 0.10 | agent-reach |
| YouTube/TikTok/IG | 0.10 | social-media-mcp |

Score 0-100: 0-20 (Sinal Fraco) | 20-40 (Microtendencia) | 40-60 (Trend/Hype) | 60-80 (Mainstream) | 80-100 (Saturado)

## Quality Gates

- [ ] Tendencia classificada com justificativa
- [ ] Estrategia especifica por plataforma
- [ ] Timing calculado (horas/dias/semanas)
- [ ] Ferramentas de coleta citadas
- [ ] Formato recomendado
- [ ] Anti-padrao identificado
- [ ] CTA alinhado com o estadio da tendencia

## Integracoes

| Skill | Papel |
|-------|-------|
| content-engine | Conteudo nativo por plataforma |
| copy-engineering | Roteiros com gatilhos mentais |
| copy-thief | Landing pages para trafego frio |
| social-publishing | Publicacao via SocialClaw |
| audio-sound-design | TTS, SFX, audio |
| video-editing | Pos-producao e reframing |
| banner-design | Capas e thumbnails |
| design-taste-frontend | Design system visual |
| agent-reach | Pesquisa web |
| content-radar-news | Sinais em tempo real |
| content-radar-rss | Agregacao RSS |
| content-radar-agent-news | Noticias verificadas |
| pulse-cn-mcp | Tendencias chinesas |
| n8n-mcp | Automacao de workflows |

## Comandos Rapidos

```bash
# Coletar sinais
python ".../content-radar/content_radar.py" --keyword "topico" --days 7 --output json

# Tendencias chinesas
# (usar Pulse CN MCP: weibo_hot, douyin_hot, bilibili_hot, zhihu_hot)

# Publicar
# (usar social-publishing via SocialClaw API)
```
