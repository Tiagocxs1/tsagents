# Typography Master — Auditoria e Correção Tipográfica Definitiva

Use quando o usuário disser "tipografia não está boa", "arrumar tipografia", "texto não está legível", "fontes estão feias", "espaçamento estranho", "harmonia tipográfica", ou ao gerar qualquer conteúdo visual com texto (posts, landing pages, cards, slides).

## 1. Fundamentos (Design Read)

Antes de qualquer correção, faça o **design read** de 3 eixos:

| Eixo | Pergunta | Resposta |
|------|----------|----------|
| Canvas | Tamanho fixo (1080×1080, 1080×1350) ou fluido (web)? | |
| Público | Mobile-first? Desktop? Ambos? | |
| Conteúdo | Headline curta (<30 chars) ou longa (>50 chars)? Body texto ou labels? | |

Declare em uma linha: **"Lendo como: [tipo de canvas] para [público], com [estilo]."**

## 2. Regras de Ouro (20 fontes, prioridade decrescente)

### P0 — CRÍTICO (quebra o design)

| # | Regra | Fonte | Implementação |
|---|-------|-------|---------------|
| 1 | **Medida (line length):** 45-75 caracteres por linha, 66 é ideal | Medium #9, CM #10 | Container width = `min(65ch, 100%)` para body. Headline: max 8-12 palavras |
| 2 | **Contraste WCAG:** Body ≥ 4.5:1 (AA), ideal 7:1 (AAA). Muted ≥ 4.5:1 | CM #11, Strikingly | `color: rgba(255,255,255,0.6)` = 4.5:1 em bg #04344C. Texto claro em bg claro = mínimo #475569 |
| 3 | **Leading (line-height):** Body = 1.5-1.8×. Headline = 1.0-1.2×. Nunca abaixo de 1.5 para parágrafos | Medium #10, CM #11 | Body: `line-height:1.55`. Headline Space Grotesk 800: `line-height:1.1` |
| 4 | **Tracking em uppercase:** Todo texto em CAIXA ALTA precisa de letter-spacing (0.05-0.15em) | Medium #22, CM #9 | CTAs: `letter-spacing:0.08em`. Tags/badges: `letter-spacing:0.06em`. Footer: `letter-spacing:0.08em` |

### P1 — ALTA (legibilidade)

| # | Regra | Fonte | Implementação |
|---|-------|-------|---------------|
| 5 | **Hierarquia visual:** Título 3× maior que body. Max 2-3 famílias tipográficas | CM #6, #8, Guizang PPT | Display 800 weight + sans body 400 weight. Proporção ~2.5-3:1 |
| 6 | **Espaçamento vertical proporcional:** Gap entre .hl → .sub → .ct deve seguir escala | Format, guizang-ppt | .hl→.sub gap = 1.5-2× line-height do body. .sub→.ct gap = 1.2-1.5× |
| 7 | **Widows & Orphans:** Última linha de parágrafo deve ter ≥3 palavras | CM #13, Medium #16 | `text-wrap: balance` em headlines. `text-wrap: pretty` em body. Nunca 1 palavra isolada |
| 8 | **Flush left por padrão:** Justificado só com >60 chars/linha E hifenização ativa | Medium #11 | Em cards sociais: left ou center. Justify só para body >60 chars |
| 9 | **Tracking em títulos grandes:** Reduzir tracking proporcional ao aumentar font-size | Medium #19, Medium #21 | Títulos >40px: `letter-spacing:-0.015em` a `-0.02em`. Nunca letter-spacing em lowercase body |
| 10 | **Line length em títulos:** Max 8-12 palavras. Se passar, reduz font-size ou quebra linha | CM #6, Guizang | Headline >60 chars → reduz `--title` ou usa grid que acomoda texto longo |

### P2 — MÉDIA (polimento)

| # | Regra | Fonte | Implementação |
|---|-------|-------|---------------|
| 11 | **Sem stretching de fontes:** Nunca `transform: scaleX()` em texto | CM #14, Medium #25 | Use fontes condensed se precisar de largura menor |
| 12 | **White space ativo:** ~40% do canvas deve ser "respiro". Espaço vazio é desenhado | CM #15, social-posts-html | Margens mínimas: `clamp(36px, 5.5cqw, 80px)`. Conteúdo ≤ 70% largura |
| 13 | **Modular scale:** Use ratio 1.25 (major third) ou 1.333 (perfect fourth) para escala tipográfica | CM #10, Format | `--fo:9px → --bs:11px → --body:15px → --cta:13px → --title:38px` |
| 14 | **Font pairing:** Sans display + sans body OU serif display + sans body. Máx 2 famílias | CM #8, #9, Medium #5, #6 | Space Grotesk (display) + DM Sans (body) = contraste por peso, não por família |
| 15 | **x-height similar:** Fontes emparelhadas devem ter x-height próxima | Medium #7 | Space Grotesk e DM Sans têm x-height similar (~0.5x cap height) |
| 16 | **Kerning:** Não kern manualmente a menos que seja headline de logo | Medium #18, CM #3 | Use `letter-spacing` (tracking) para ajuste geral, não kerning par-a-par |

### P3 — BAIXA (validação)

| # | Regra | Fonte | Implementação |
|---|-------|-------|---------------|
| 17 | **Hanging punctuation:** Pontuação deve "pendurar" fora da margem em textos justificados | Medium #15 | `text-indent: -0.5em` para aspas em citações |
| 18 | **Captions:** Texto estreito = condensed typeface. Máx 3 linhas | Medium #14 | `font-size: var(--bs)` com `letter-spacing: 0.05em` |
| 19 | **Números por extenso:** Spell numbers em texto corrido (exceto dados/matemática) | Medium #26 | "três dias" não "3 dias" em body text |
| 20 | **Nenhuma ênfase em uppercase no body:** Use bold/italic, não ALL CAPS | Medium #20, #23 | Body em caixa baixa. Uppercase só para labels, CTAs, badges |

## 3. Workflow de Correção

### Fase 1: Auditoria Automática

```python
# Para cada post/HTML gerado, verificar:
def audit_typography(html_content):
    issues = []
    css = extract_css(html_content)  # pega o <style>
    
    # P0 checks
    if 'line-height:1.5' not in css and 'line-height:1.55' not in css:
        issues.append('P0-3: Body line-height ausente ou abaixo de 1.5')
    if 'letter-spacing:0.08em' not in css and 'letter-spacing:0.06em' not in css:
        issues.append('P0-4: Uppercase sem letter-spacing')
    if 'color:#506A76' in css:  # GRAFITE sem alpha
        issues.append('P0-2: Cor fixa #506A76 muda para rgba com alpha')
    
    # P1 checks
    if 'line-height:1.1' not in css and 'line-height:1.2' not in css:
        issues.append('P1-5: Headline line-height muito apertado')
    if 'letter-spacing:-0.015em' not in css and 'letter-spacing:-0.02em' not in css:
        issues.append('P1-9: Tracking negativo ausente em títulos')
    
    # Check gaps between elements
    h1_pos = extract_position(css, '.hl', 'bottom')
    sub_pos = extract_position(css, '.sub', 'bottom')
    gap = h1_pos - sub_pos if h1_pos and sub_pos else 0
    if gap > 10:  # cqw
        issues.append(f'P1-6: Gap hl→sub de {gap}cqw é grande (>10)')
    
    return issues
```

### Fase 2: CSS Tokens Canônicos

Sempre que aplicar tipografia, use este sistema de tokens como referência (adaptar por canvas):

```css
:root {
  /* Escala modular (ratio 1.25) */
  --fo: clamp(9px, 1.2cqw, 11px);    /* footer */
  --bs: clamp(11px, 1.6cqw, 13px);   /* badge/small */
  --cta: clamp(13px, 2cqw, 16px);    /* button */
  --body: clamp(15px, 2.4cqw, 20px); /* body/subtitle */
  --title: clamp(38px, 7.5cqw, 64px);/* headline */
  
  /* Medida */
  --tw: min(56cqw, 520px);           /* content width ~65 chars at 16px */
}

/* Headline display (800 weight) */
.hl {
  font-family: 'Space Grotesk', sans-serif;
  font-weight: 800;
  font-size: var(--title);
  color: #FFFFFF;
  line-height: 1.1;
  letter-spacing: -0.015em;
  text-wrap: balance;
  text-shadow: 0 1px 4px rgba(0,0,0,0.15);  /* legibilidade em bg escuro */
}

/* Body / Subtitle (400 weight) */
.sub {
  font-family: 'DM Sans', sans-serif;
  font-weight: 400;
  font-size: var(--body);
  color: rgba(255,255,255,0.6);      /* WCAG AA 4.5:1 em #04344C */
  line-height: 1.55;
  text-wrap: pretty;
  text-shadow: 0 1px 3px rgba(0,0,0,0.2);
}

/* CTA Button (uppercase) */
.cb {
  font-family: 'DM Sans', sans-serif;
  font-weight: 700;
  font-size: var(--cta);
  text-transform: uppercase;
  letter-spacing: 0.08em;            /* P0-4: uppercase tracking */
}

/* Footer */
.f {
  font-size: var(--fo);
  color: rgba(255,255,255,0.25);
  letter-spacing: 0.08em;
}

/* Awareness Tag */
.aw {
  font-size: var(--bs);
  font-weight: 700;
  letter-spacing: 0.06em;
}
```

### Fase 3: Correção Por Grid

Cada grid system tem espaçamentos verticais específicos. Tabela de referência:

| Grid | .hl bottom | .sub bottom | .ct bottom | Gap hl→sub | Gap sub→ct |
|------|-----------|------------|-----------|-----------|-----------|
| Simétrico | relative | margin-top:1.5cqw | margin-top:2.5cqw | 1.5cqw | 1.0cqw |
| Assimétrico | relative | margin-top:1.5cqw | margin-top:2.5cqw | 1.5cqw | 1.0cqw |
| Split-Diagonal | relative | margin-top:1.5cqw | margin-top:2.5cqw | 1.5cqw | 1.0cqw |
| Radial | relative | margin-top:1.5cqw | margin-top:2.5cqw | 1.5cqw | 1.0cqw |
| Full-Bleed | 30cqw | 20cqw | 4cqw | **10cqw** | 16cqw |
| Grid Cards | relative | margin-top:1.5cqw | margin-top:2.5cqw | 1.5cqw | 1.0cqw |
| Livre | relative | margin-top:1.2cqw | margin-top:1.8cqw | 1.2cqw | 0.6cqw |
| Magazine | 18cqw | 11cqw | 3cqw | **7cqw** | 8cqw |

**Regra de ouro do gap:** O espaço entre .hl e .sub deve ser suficiente para o descender do título não encostar no ascendente do subtitle — mas não tão grande que pareçam elementos desconectados. Em absolute positioning (full-bleed, magazine), o gap visual = `(hl_bottom - sub_bottom) - hl_line_height`. Para hl com line-height 1.1 e font-size 48px ≈ 53px, gap visual de ~1-2 linhas é ideal.

### Fase 4: Pós-Validação (Checklist)

Após aplicar correções, verificar:

- [ ] **P0-1:** Container de texto ≤ 65ch de largura
- [ ] **P0-2:** Todo texto body passa 4.5:1 no fundo
- [ ] **P0-3:** Body `line-height` ≥ 1.5
- [ ] **P0-4:** Todo uppercase tem `letter-spacing` ≥ 0.05em
- [ ] **P1-5:** Headline `line-height` entre 1.0-1.2
- [ ] **P1-6:** Gap hl→sub proporcional (não > 12cqw)
- [ ] **P1-7:** `text-wrap: balance` em headings, `pretty` em body
- [ ] **P1-8:** Texto flush left ou center, não justify sem hifenização
- [ ] **P1-9:** Títulos grandes com tracking negativo
- [ ] **P1-10:** Nenhuma headline > 12 palavras sem quebra
- [ ] **P2-11:** Nenhum `transform: scaleX()` ou `font-stretch` em texto
- [ ] **P2-13:** Escala segue ratio consistente (1.25 ou 1.333)

## 4. Script de Correção Automática (Python)

```python
"""
fix-typography-master.py
Aplica as 20 regras tipográficas em HTMLs de cards sociais/landing pages.

Uso: python fix-typography-master.py <dir|file>
"""
import re, sys, os, glob

RULES = [
    # (old_pattern, new_pattern, rule_id, description)
    
    # P0-3: Body line-height
    (r'line-height:1\.3[0-9](?![0-9])', 'line-height:1.55', 'P0-3', 'Body line-height mínimo 1.5'),
    (r'line-height:1\.4[0-9](?![0-9])', 'line-height:1.55', 'P0-3', 'Body line-height mínimo 1.5'),
    
    # P0-4: Uppercase letter-spacing
    (r'(text-transform:\s*upper)[^}]*(?<!letter-spacing)', r'\1case;letter-spacing:0.08em', 'P0-4', 'Uppercase sem tracking'),
    
    # P1-5: Headline line-height
    (r'line-height:1\.0[0-4]', 'line-height:1.1', 'P1-5', 'Headline line-height mínimo 1.1'),
    (r'line-height:1\.0[5-9]', 'line-height:1.1', 'P1-5', 'Headline line-height 1.1'),
    
    # P1-9: Headline tracking
    (r'(font-size:var\(--title\).*?)letter-spacing:0', r'\1letter-spacing:-0.015em', 'P1-9', 'Título sem tracking negativo'),
    
    # P0-2: Cor fixa -> rgba
    (r'color:#506A76', 'color:rgba(255,255,255,0.6)', 'P0-2', 'GRAFITE -> rgba body'),
    
    # Spacing: full-bleed .sub bottom 17->20
    (r'\.sub\{[^}]*bottom:17cqw[^}]*\}', lambda m: m.group(0).replace('bottom:17cqw','bottom:20cqw'), 'P1-6', 'Full-bleed sub bottom 17→20cqw'),
    
    # Spacing: magazine .sub bottom 7->11
    (r'\.sub\{position:absolute;left:2cqw;bottom:7cqw[^}]*\}', lambda m: m.group(0).replace('bottom:7cqw','bottom:11cqw'), 'P1-6', 'Magazine sub bottom 7→11cqw'),
]

def fix_file(filepath):
    with open(filepath, encoding='utf-8') as f:
        content = f.read()
    
    fixes = []
    for old, new, rule_id, desc in RULES:
        if isinstance(new, str):
            new_content = re.sub(old, new, content)
        else:
            new_content = re.sub(old, new, content)
        if new_content != content:
            fixes.append(f'  [{rule_id}] {desc}')
            content = new_content
    
    if fixes:
        with open(filepath, 'w', encoding='utf-8') as f:
            f.write(content)
        print(f'Fixed: {filepath}')
        for f in fixes:
            print(f)
        return True
    return False

if __name__ == '__main__':
    target = sys.argv[1] if len(sys.argv) > 1 else '.'
    if os.path.isfile(target):
        fix_file(target)
    else:
        for f in sorted(glob.glob(os.path.join(target, '*.html'))):
            fix_file(f)
```

## 5. Anti-Padrões (Nunca Fazer)

| Anti-padrão | Por que | Alternativa |
|-------------|---------|-------------|
| `color:#506A76` em bg escuro | Falha WCAG AA (ratio ~2.5:1) | `rgba(255,255,255,0.6)` |
| `line-height:1.04` em Space Grotesk 800 | Descendentes colidem com linha seguinte | `line-height:1.1` |
| `letter-spacing:0` em CTAs uppercase | Uppercase sem tracking é ilegível | `letter-spacing:0.08em` |
| Body text com `font-family:'Space Grotesk'` | Display font em body = ilegível em parágrafos | DM Sans (400) para body |
| Gap hl→sub > 12cqw | Elementos parecem desconectados | Reduzir gap para 7-10cqw |
| Mais de 2 famílias tipográficas | Poluição visual, parece amador | Max 2: 1 display + 1 body |
| Justify sem hifenização | Rivers (espaços brancos verticais) | Flush left ou hifenização ativa |

## 6. Exemplo de Uso

```
Usuário: "a tipografia dos posts está ruim, espaçamento estranho"
→ Ativar Typography Master
→ Design Read: Canvas 1080×1350, mobile-first Instagram, conteúdo editorial
→ Auditoria: encontra P0-2 (cor fixa), P1-6 (gap hl→sub 13cqw), P0-4 (CTA sem tracking)
→ Aplicar correção: fix-typography-master.py nos HTMLs
→ Verificar checklist
→ Reportar: "Corrigido: gap hl→sub reduzido de 13cqw para 9cqw, CTA tracking adicionado, body color ajustado para WCAG AA"
```