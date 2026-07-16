---
name: google-analytics-mcp
description: "Google Analytics MCP oficial (2.7k stars). 6 tools para consultar Google Analytics via API: run_report, run_funnel_report, run_realtime_report, get_account_summaries, get_property_details, list_google_ads_links. Requer Google Cloud + credenciais OAuth."
---

# Google Analytics MCP

MCP oficial do Google para consultar dados do Google Analytics via APIs Admin e Data.

## MCP Config (Opencode / Claude Code / Cursor)

```json
{
  "analytics-mcp": {
    "type": "local",
    "command": ["pipx", "run", "analytics-mcp"],
    "enabled": true,
    "environment": {
      "GOOGLE_APPLICATION_CREDENTIALS": "C:\\Users\\Admin\\Desktop\\TS Digitais\\IA\\.ia-config\\credentials\\google-analytics.json",
      "GOOGLE_PROJECT_ID": "SEU_PROJECT_ID"
    }
  }
}
```

## Tools (6)

| Tool | Descrição |
|------|-----------|
| `get_account_summaries` | Lista contas e propriedades Google Analytics |
| `get_property_details` | Detalhes de uma propriedade específica |
| `list_google_ads_links` | Links de contas Google Ads vinculadas |
| `run_report` | Relatório Data API (período customizado) |
| `run_funnel_report` | Relatório de funil (abandono/conversão) |
| `run_realtime_report` | Relatório em tempo real (últimos 30 min) |

## Setup

1. Google Cloud: criar/ativar projeto em https://console.cloud.google.com/
2. APIs: ativar Analytics Admin API + Analytics Data API
3. Service Account: criar em IAM > Service Accounts > gerar chave JSON
4. Adicionar service account ao Google Analytics (Ler & Analisar)
5. Salvar JSON em `credentials/google-analytics.json`
6. Pegar Project ID no console.cloud.google.com
7. Setar `GOOGLE_APPLICATION_CREDENTIALS` e `GOOGLE_PROJECT_ID`
8. Dar `pipx run analytics-mcp` pra testar

## Exemplos de prompt

- "quais são as contas GA4 que tenho acesso?"
- "me dá os eventos mais populares dos últimos 30 dias"
- "quantos usuários logados tivemos no último mês?"
- "relatório de funil de compra vs abandono"