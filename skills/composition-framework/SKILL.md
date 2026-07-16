# Composition Architecture Framework

Framework de composição arquitetônica para design visual em camadas, com profundidade, assets 3D, fotografia, glassmorfismo e componentes funcionais.

**Carregue esta skill PARA QUALQUER design que precise de qualidade premium.** Deve ser usada EM CONJUNTO com a skill de output (social-posts-html, banner-design, etc.).

---

## Layer Model (Modelo de Camadas)

Todo design de alta qualidade tem MÚLTIPLAS CAMADAS de profundidade. Planeje a pilha de z-index ANTES de codificar.

```
z-index  Composição
─────────────────────────────────────────
20       Interativos (botões, CTAs, links)
19       Glass cards (stat, pricing, feature)
18       Tipografia hero (headlines com gradiente)
17       Assets 3D (FluentUI emoji, Pixcap, etc.)
16       Fotografia / imagem principal
15       Componentes decorativos (badges, pills)
14       Formas decorativas (blobs, diagonais, rings)
13       Linhas de grid estruturais
12       Camadas de gradiente atmosférico (2-3)
11       Máscaras / recortes orgânicos
10       Textura / grão (grain overlay)
 1       Fundo base (cor sólida)
```

**REGRAS:**
- Mínimo 3-4 camadas de profundidade visível (não contar grain)
- Nunca centralizar tudo verticalmente — distribua no eixo Z
- Cada camada deve ter intenção (não é decoração)

---

## Composition Planning (Planeje antes de codificar)

Antes de escrever HTML, defina:

### 1. Estrutura de Camadas
```
Fundo: [cor sólida / gradiente simples / gradiente atmosférico múltiplo]
Grid:  [linhas / colunas visíveis?]
Asset: [qual 3D? qual foto?]
Cards: [glass? stat? pricing?]
CTA:   [gradiente com glow? outline? pill?]
```

### 2. Asset Check
- [ ] Tem 3D asset disponível? (FluentUI, Pixcap, IconScout)
- [ ] Tem foto real? (Unsplash, Pexels)
- [ ] Precisa de ícone? (Phosphor)

### 3. Técnicas Selecionadas (mínimo 5-6)
Marque quais vai usar antes de começar e NÃO ABRA MÃO:
- [ ] Gradiente atmosférico múltiplo (2-3 radiais)
- [ ] Grid estrutural (linhas verticais ou guias)
- [ ] 3D asset real (não CSS sphere)
- [ ] Foto real com overlay e borda
- [ ] Glassmorphism card (border-top highlight + inset)
- [ ] Gradiente em texto (background-clip: text)
- [ ] Sombra multi-camada (box-shadow stack + drop-shadow)
- [ ] Stat card (número grande + label)
- [ ] Pricing card (preço + período + CTA)
- [ ] Badge premium com dot glow

---

## Técnicas (com código)

### 1. Gradiente Atmosférico Múltiplo

```css
.canvas {
  background:
    radial-gradient(ellipse at 20% 10%, rgba(59,130,246,0.15) 0%, transparent 55%),
    radial-gradient(ellipse at 80% 90%, rgba(168,85,247,0.12) 0%, transparent 55%),
    radial-gradient(ellipse at 50% 50%, rgba(236,72,153,0.08) 0%, transparent 50%),
    #030305;
}
```

### 2. Grid Estrutural (linhas guia)

```css
.grid-guide-v {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 1px;
  background: rgba(255,255,255,0.03);
  pointer-events: none;
}
/* Posicionar em left: 20%, 40%, 60%, 80% ou medidas fixas estilo editorial */
```

### 3. Gradient Text

```css
.gradient-text {
  background: linear-gradient(135deg, #ffffff 30%, #94a3b8 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.gradient-text--brand {
  background: linear-gradient(135deg, #3b82f6 0%, #a855f7 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

### 4. Glassmorphism Card

```css
.glass-card {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.08);
  border-top: 1px solid rgba(255,255,255,0.25);
  border-radius: 30px;
  padding: 25px 35px;
  box-shadow:
    inset 0 0 40px rgba(255,255,255,0.02),
    0 20px 40px rgba(0,0,0,0.4);
  backdrop-filter: blur(12px);
}
```

### 5. Badge Premium com Glow Dot

```css
.badge-premium {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 22px;
  border-radius: 100px;
  background: rgba(59,130,246,0.1);
  border: 1px solid rgba(59,130,246,0.3);
}
.badge-premium .dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: linear-gradient(135deg, #3b82f6, #a855f7);
  box-shadow: 0 0 15px rgba(168,85,247,0.8);
}
```

### 6. Stat Card (2 colunas)

```css
.stats { display: flex; gap: 20px; width: 100%; }
.stat-card { flex: 1; padding: 25px 35px; border-radius: 30px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.08);
  border-top: 1px solid rgba(255,255,255,0.25);
  box-shadow: inset 0 0 40px rgba(255,255,255,0.02), 0 20px 40px rgba(0,0,0,0.4);
}
.stat-card .label { color: #94a3b8; font-size: 13px; font-weight: 800; letter-spacing: 2px; text-transform: uppercase; }
.stat-card .value { color: white; font-size: 38px; font-weight: 900; letter-spacing: -1px; margin-top: 4px; }
```

### 7. CTA Gradient Button

```css
.cta-btn {
  display: inline-flex;
  align-items: center;
  padding: 18px 40px;
  border-radius: 30px;
  background: linear-gradient(135deg, #2563eb, #7c3aed);
  color: white;
  font-weight: 900;
  font-size: 20px;
  letter-spacing: 0.5px;
  box-shadow: 0 15px 30px rgba(124,58,237,0.4);
  border: 1px solid rgba(255,255,255,0.3);
  cursor: pointer;
  transition: transform .2s, box-shadow .2s;
}
.cta-btn:hover { transform: translateY(-2px); box-shadow: 0 20px 40px rgba(124,58,237,0.5); }
```

### 8. Pricing Card (preço + período)

```css
.pricing-row { 
  display: flex; align-items: flex-end; 
  background: rgba(255,255,255,0.08);
  border-radius: 40px;
  padding: 15px 15px 15px 40px;
  border: 1px solid rgba(255,255,255,0.2);
  border-top: 1px solid rgba(255,255,255,0.4);
  box-shadow: 0 30px 60px rgba(0,0,0,0.6);
}
.pricing-row .price { color: white; font-size: 42px; font-weight: 900; line-height: 1; }
.pricing-row .period { color: #94a3b8; font-size: 18px; font-weight: 800; margin-left: 6px; }
```

### 9. Multi-Layer Shadow Stack

```css
.shadow-premium {
  filter: drop-shadow(0 25px 35px rgba(0,0,0,0.6));
  box-shadow: 0 30px 60px rgba(0,0,0,0.8);
}
```

### 10. Photo Card com Moldura

```css
.photo-card { position: relative; border-radius: 40px; overflow: hidden; }
.photo-card img { width: 100%; height: 100%; object-fit: cover; border-radius: 40px; display: block; }
.photo-card .glow { position: absolute; top: 15px; left: 15px; right: -15px; bottom: -15px;
  background: rgba(59,130,246,0.15); border-radius: 40px; filter: blur(30px); z-index: -1; }
.photo-card .frame { position: absolute; inset: 0; border-radius: 40px;
  border: 2px solid rgba(255,255,255,0.2); pointer-events: none; }
```

---

## Component Templates (Combináveis)

### Hero Section (cover slide)
```
Layer stack (top → bottom):
10: CTA/badge
 9: Headline gradient text
 8: Subheadline + divider
 7: 3D asset (canto superior direito)
 6: Grid vertical lines
 5: Multiple atmospheric gradients
 4: Grain texture
 3: Base color
```

### Feature Card (slide de conteúdo)
```
10: CTA link
 9: Body text
 8: Numbered badge
 7: Glass card container
 6: Stat or feature list inside
 5: Background gradient layer
```

---

## Asset Sourcing (3D)

### Microsoft FluentUI 3D Emoji (Open Source)
```html
<!-- Formato: raw.githubusercontent.com/microsoft/fluentui-emoji/main/assets/NOME/3D/nome_3d.png -->
<img src="https://raw.githubusercontent.com/microsoft/fluentui-emoji/main/assets/Airplane/3D/airplane_3d.png">
```
Use qualquer emoji do repositório: `https://github.com/microsoft/fluentui-emoji/tree/main/assets`

### Pixcap (3D Icons)
```bash
https://pixcap.com/free-3d-icons
```

### IconScout 3D
```bash
https://iconscout.com/free-3d-illustrations
```
