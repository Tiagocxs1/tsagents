# Content Radar

```bash
python "C:\Users\Admin\Desktop\TS Digitais\IA\.ia-config\scripts\content-radar\content_radar.py" --keyword "seu topico" --days 7 --output text
```

## Opções
- `--keyword`, `-k` (obrigatório): Tópico/palavra-chave
- `--days`, `-d` (default: 7): Janela em dias
- `--output`, `-o` (text|json): Formato
- `--sources` (trends news reddit): Quais fontes verificar

## Exemplos
```bash
# Texto simples
python content_radar.py -k "IA agentes" -d 30

# JSON para processamento
python content_radar.py -k "ecommerce" -o json

# Fonte específica
python content_radar.py -k "marketing" --sources news
```

## APIs configuradas
- Google Trends (PyTrends)
- NewsAPI (key: d840d4c966c04afb8c0502bdac272bc4)
- Reddit (público)
- Mediastack (key: 5f20383ab33e2a3af38baf535a4a37f8)
- NewsData.io (key: pub_71559d4cd1a9a1ebe3aff3436d9d110b3028f)

## MCPs ativos para content radar
- `social-media-mcp` - 649 tools (YouTube, LinkedIn, Facebook, Instagram, TikTok, X)
- `pulse-cn-mcp` - 18 plataformas chinesas
- `content-radar-news` - mcp-hot-news-server
- `content-radar-rss` - mcp-rss-news-agent
- `content-radar-agent-news` - agent-news (fontes verificadas)
- `n8n-mcp` - workflows de automação
