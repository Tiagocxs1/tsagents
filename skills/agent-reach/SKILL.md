# Agent Reach — Internet Capability Layer for AI Agents

Dá ao agente capacidade de ler/escrever/pesquisar na internet. 45.6k★ no GitHub.

## Como Ativar

Peça ao agente:

```
Me instale Agent Reach: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
```

Ou manualmente: `pip install agent-reach`

## Canais Zero-Config (funcionam de imediato)
- **Web**: `curl https://r.jina.ai/URL` — ler qualquer webpage (Jina Reader, grátis)
- **YouTube**: `yt-dlp --write-auto-subs ...` — extrair legendas
- **GitHub**: `gh repo view owner/repo` — ler repositórios públicos
- **Bilibili**: `bili search <query>` — busca sem login (bili-cli)
- **RSS**: `feedparser` — ler qualquer feed RSS/Atom
- **V2EX**: tópicos quentes, posts, replies (sem config)
- **Busca semântica**: Exa via MCP (grátis, sem API key)

## Canais que Precisam Login
Peça ao agente "me ajuda a configurar [plataforma]":
- **Twitter/X** — twitter-cli ou OpenCLI
- **Reddit** — OpenCLI (desktop) ou rdt-cli + cookie
- **Facebook** — OpenCLI (reusa sessão Chrome)
- **Instagram** — OpenCLI (reusa sessão Chrome)
- **小红书** — OpenCLI (desktop) ou xiaohongshu-mcp (server)
- **LinkedIn** — linkedin-scraper-mcp ou Jina Reader

## Diagnóstico
```bash
agent-reach doctor
```
Mostra cada canal: ✅ funcionando / ❌ precisa config / qual backend em uso

## Design
- Multi-backend por canal (ex: twitter → twitter-cli ▸ OpenCLI ▸ bird)
- Se backend morre → troca rota automaticamente
- Config em `~/.agent-reach/config.yaml` (permissão 600)
- Safe mode: `agent-reach install --safe`