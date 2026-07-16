---
description: Invoca o Squad-Agência — orquestrador A00 + agentes especialistas para demandas de marketing, design, conteúdo, vídeo, tráfego e performance.
---

# Squad Command

## Usage

`/squad [descrição da demanda]`

## Fluxo

1. **Carrega A00** — lê `docs/squad-agencia/10-orquestracao/A00-orchestrator.md`
2. **Diagnostica** — classifica a demanda (campanha completo, post, carrossel, vídeo, artigo, landing, tráfego, etc.)
3. **Roteia** — ativa os agentes corretos na sequência do pipeline
4. **Acompanha** — garante handoffs e quality gates (A20, A21, A22)
5. **Entrega** — output final passa por A25 (score preditivo) antes de aprovação

## Rotas Principais

| Demanda | Pipeline |
|---------|----------|
| Post social | A07 → A09 → A20 → A22 (IT ≥ 6) → A25 |
| Carrossel | A07 → A10 → A11 → A20 → A22 → A25 |
| Campanha completa | A01 → A02 → taste brief → A04/A08 → produção → A20/A21 → A22 → A00 → A17/A25 |
| Vídeo | A12 → A23 → A13/A14 → A21 → A22 |
| Artigo SEO | A06 → A16 → A20 → A22 |
| Tráfego pago | A17 → A25 → catálogo performance |
| Landing page | A15 → A16 → A17 → A22 |
| Storytelling | A04/A07 → catálogo storytelling → A20 → A22 |
| Estratégia de marca | A01/A02 → catálogo brand-squad → A20 |
| Oferta/funil | A04/A17 → catálogo hormozi-squad |

## Catálogos de Especialistas

O squad tem acesso a especialistas da central IA:

| Área | Catálogo |
|------|----------|
| Estratégia | `01-estrategia/XX-referencia-especialistas-centrais.md` |
| Storytelling | `02-conteudo/XX-referencia-storytelling.md` |
| Design complementar | `03-design/XX-referencia-design-centrais.md` |
| Performance + tráfego | `06-performance/XX-referencia-especialistas-centrais.md` |
| MCPs e skills | `05-tecnologia/XX-referencia-mcps-centrais.md` |

## Quality Gates (Obrigatórios)

- A20 (Brand Guardian) — consistência de marca
- A21 (QA Conteúdo) — qualidade técnica
- A22 (Curador de Gosto) — nota IT 0-10, veto se necessário
- A25 (Creative Performance Analyst) — score preditivo de performance
