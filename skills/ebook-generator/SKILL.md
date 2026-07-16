# Skill: Gerador de eBooks (Multi-Provider)

Gera eBooks profissionais com capa por IA usando qualquer LLM (OpenAI, Gemini, Anthropic, DeepSeek).

## Localização

- **ebook-maker CLI**: `C:\Users\Admin\Desktop\TS Digitais\ebook-maker\`
- **IA-Books Web UI**: `C:\Users\Admin\Desktop\TS Digitais\ia-books\`

## Modo CLI (ebook-maker)

Geração completa via terminal:
```bash
cd C:\Users\Admin\Desktop\TS Digitais\ebook-maker
python build_ebook.py --topic "Seu Tópico" --type ebook --chapters 6 --layout mckinsey
```

### Parâmetros
| Flag | Opções | Padrão |
|---|---|---|
| `--topic` | Texto do tópico | Obrigatório |
| `--type` | `apostila`, `ebook`, `livro` | `ebook` |
| `--lang` | `pt-BR`, `en` | `pt-BR` |
| `--chapters` | Número | `6` |
| `--layout` | `mckinsey`, `classico`, `moderno`, `suico` | `mckinsey` |
| `--provider` | `openai`, `gemini`, `anthropic`, `deepseek`, `pollinations` | do `.env` |

### Layouts
| Layout | Estilo | Inspiração |
|---|---|---|
| `mckinsey` | Corporativo, roxo/dourado | McKinsey |
| `classico` | Serifado (Georgia), elegante | Penguin Classics |
| `moderno` | Caixas coloridas, Arial | O'Reilly |
| `suico` | Minimalista, grid, preto/branco | Brockmann |

## Modo Web UI (IA-Books)

Interface visual com agentes (Planner, Writer, Art Director):
```bash
cd C:\Users\Admin\Desktop\TS Digitais\ia-books
npm run dev
```
Acesse em `http://localhost:3000`

### Configuração de Provider
Na UI, selecione o provedor de IA: Gemini, OpenAI, Claude ou DeepSeek.
A chave API é inserida pelo usuário no navegador.

## Provedores Suportados

| Provider | Texto | Imagem | Custo |
|---|---|---|---|
| Pollinations | — | Flux (gratuito) | Grátis |
| OpenAI | GPT-4o | DALL-E 3 | Pago |
| Gemini | 2.5 Flash/Pro | 3 Pro Image | Grátis (quota) |
| Anthropic | Claude Sonnet 4 | Pollinations (fallback) | Pago |
| DeepSeek | DeepSeek Chat | DeepSeek Image | Barato |

## Dependências

- ebook-maker: Python 3+, Node.js 16+, LibreOffice (para PDF)
- IA-Books: Node.js 18+

## Fluxo de Uso

1. Perguntar tópico, tipo, idioma, número de capítulos e layout
2. Executar `python build_ebook.py --topic "..."` com os parâmetros coletados
3. Arquivos gerados em `output/` (capa.png, .docx, .pdf)