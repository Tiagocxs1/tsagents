# Social Posts HTML — Direção de Arte para Redes Sociais

Diretor de arte + front-end designer. Gera posts em HTML/CSS com composição em camadas, assets externos reais (imagens, 3D, ícones), máscaras, sombras, blend modes e profundidade visual.

Inspirado por: frontend-design (vipulgupta2048), social-media-graphic-designer (ArnavPuri), frontend-social-media-design (dikaizm), Super Skills asset library.

---

## Core Philosophy

1. **Zero Dependencies locais** — HTML único com CSS/JS inline. Assets vêm de APIs/CDNs externos.
2. **Show, Don't Tell** — Gere previews visuais, não escolhas abstratas.
3. **Canvas sizing fixo** — pixel-perfect. Sem scroll. `overflow: hidden`.
4. **Composição arquitetônica em camadas** — Não é "texto em fundo decorado". É composição com 6-15 técnicas visuais simultâneas: gradiente atmosférico múltiplo + grid estrutural + asset 3D + fotografia + glass card + gradient text + multi-shadow + badges. Mínimo 6 camadas de profundidade.
5. **Assets reais > CSS puro** — fotos (Unsplash), 3D (FluentUI/Pixcap/IconScout), ícones (Phosphor), texturas externas.

> **IMPORTANTE:** Antes de gerar qualquer design, carregue a skill `composition-framework` para o modelo de camadas, planejamento de composição e biblioteca de técnicas premium.

---

## External Asset Sources

### Unsplash API (Fotos)
```bash
# Buscar foto por tema
curl -s "https://api.unsplash.com/search/photos?query=QUERY&orientation=squarish&per_page=5" \
  -H "Authorization: Client-ID ${UNSPLASH_ACCESS_KEY}" | python3 -c "
import json, sys
d = json.load(sys.stdin)
for p in d.get('results', []):
  print(f\"{p['id']} | {p.get('alt_description','')} | {p['urls']['regular']} | Por {p['user']['name']}\")
"

# Usar direto no CSS
background: url('https://images.unsplash.com/photo-XXXXX?w=1080&q=85') center/cover;
```

### Pictify MCP (24 tools — ícones, 3D, ilustrações)
Via MCP já configurado no ecossistema. Buscar:
- `pictify_search_icons` — ícones por tema
- `pictify_search_3d` — objetos 3D
- `pictify_search_illustrations` — ilustrações

### IconScout (3D, PNG, SVG, ícones)
```bash
https://iconscout.com/free-3d-illustrations
```

### Pixcap (objetos 3D gratuitos)
```bash
https://pixcap.com/free-3d-icons
```

### Microsoft FluentUI 3D Emoji (Open Source — PREMIUM)
Repositório oficial com centenas de emojis 3D em PNG. Ideal para dar profundidade tátil a cards e hero sections.

```html
<!-- Estrutura: assets/NOME_DO_EMOJI/3D/nome_3d.png -->
<img src="https://raw.githubusercontent.com/microsoft/fluentui-emoji/main/assets/Airplane/3D/airplane_3d.png"
     style="filter:drop-shadow(0 25px 35px rgba(0,0,0,0.6))">
```

Buscar em: https://github.com/microsoft/fluentui-emoji/tree/main/assets
Usar qualquer pasta de emoji (Fire, Rocket, Star, Money, etc.) no formato 3D.

### SVGMaker MCP
Criar SVGs customizados (formas, badges, stickers) sob demanda.

### Universal Icons MCP
Buscar ícones de qualquer biblioteca por descrição.

### Biblioteca Icons CDN
```html
<script src="https://unpkg.com/@phosphor-icons/web@2.1.1"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
```

### Fontes
```html
<link href="https://api.fontshare.com/v2/css?f[]=cabinet-grotesk@700,800,900&f[]=satoshi@300,400,500,700" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Space+Grotesk:wght@400;500;600;700" rel="stylesheet">
```

**PROIBIDO usar**: Inter, Roboto, Poppins, system-ui, sans-serif genérico.

---

## Image Banks Directory

### General Free
| Site | URL | Best For |
|------|-----|----------|
| Unsplash | https://unsplash.com/ | Editorial, lifestyle, technology |
| Pexels | https://www.pexels.com/ | People, business, nature |
| Pixabay | https://pixabay.com/ | Vectors, illustrations, photos |
| Wikimedia Commons | https://commons.wikimedia.org/ | Historical, cultural, educational |
| Burst by Shopify | https://burst.shopify.com/ | E-commerce, product, business |
| Reshot | https://www.reshot.com/ | Unique, non-stocky visuals |
| Kaboompics | https://kaboompics.com/ | Warm, lifestyle, feminine |
| StockSnap | https://stocksnap.io/ | High-res, varied categories |
| Gratisography | https://gratisography.com/ | Quirky, artistic, creative |
| Life of Pix | https://www.lifeofpix.com/ | Documentary, atmospheric |
| Picjumbo | https://picjumbo.com/ | Business, tech, lifestyle |
| Rawpixel Free | https://www.rawpixel.com/ | Vintage, artistic, premium feel |
| Dreamstime Free | https://www.dreamstime.com/free-images | Stock, varied categories |
| Morguefile | https://morguefile.com/ | Reference, raw, editorial |
| Flickr Commons | https://www.flickr.com/commons | Historical archives |
| Openverse | https://openverse.org/ | Search across multiple catalogs |
| Freeimages | https://www.freeimages.com/ | General stock |
| ISO Republic | https://isorepublic.com/ | High-res, commercial use |
| Barnimages | https://barnimages.com/ | Editorial, nature |
| SplitShire | https://www.splitshire.com/ | Creative, abstract |
| Little Visuals | https://littlevisuals.co/ | Minimal, nature |
| Jay Mantri | https://jaymantri.com/ | Minimal, atmospheric |
| NegativeSpace | https://negativespace.co/ | Clean, professional |
| Skitterphoto | https://skitterphoto.com/ | Travel, architecture |
| Stockvault | https://www.stockvault.net/ | General stock |
| Good Free Photos | https://www.goodfreephotos.com/ | Nature, landscapes |
| LibreShot | https://libreshot.com/ | Travel, lifestyle |
| PxHere | https://pxhere.com/ | High-res, varied |
| Foodiesfeed | https://www.foodiesfeed.com/ | Food, beverages |
| Startup Stock Photos | https://startupstockphotos.com/ | Startup, office, tech |

### PNG & Transparency
| Site | URL | Best For |
|------|-----|----------|
| PNGAll | https://www.pngall.com/ | PNG recortados variados |
| PNGTree | https://pngtree.com/ | PNGs, backgrounds, templates |
| CleanPNG | https://www.cleanpng.com/ | PNGs com fundo transparente |
| StickPNG | https://www.stickpng.com/ | Stickers, logos, objects |
| KissPNG | https://www.kisspng.com/ | PNGs variados |
| PNGWing | https://www.pngwing.com/ | PNGs por categoria |
| PNGItem | https://www.pngitem.com/ | PNGs editáveis |
| PNGEgg | https://www.pngegg.com/ | PNGs high-res |
| NicePNG | https://www.nicepng.com/ | PNGs, clipart |
| FreePNGImg | https://freepngimg.com/ | PNGs gratuitos |
| SVG Repo | https://www.svgrepo.com/ | SVGs, icons, illustrations |
| Openclipart | https://openclipart.org/ | Clipart, vectors |
| Public Domain Vectors | https://publicdomainvectors.org/ | Vectors domínio público |
| Vectorportal | https://www.vectorportal.com/ | Vectors free |
| Vecteezy Free | https://www.vecteezy.com/ | Vectors, PNGs, patterns |
| Clker | https://www.clker.com/ | Clipart royalty-free |
| ClipSafari | https://clipsafari.com/ | Clipart SVG |
| Iconduck | https://iconduck.com/ | Open source icons |
| Seeklogo | https://seeklogo.com/ | Logos de marcas |
| Brands of the World | https://www.brandsoftheworld.com/ | Logos vetoriais |
| PNGAAA | https://pngaaa.com/ | PNGs variados |
| PNGDownload | https://www.pngdownload.io/ | PNGs free download |
| PNGPix | https://www.pngpix.com/ | PNGs profissionais |
| Transparent PNG | https://transparentpng.com/ | PNGs transparentes |
| FreeIconsPNG | https://www.freeiconspng.com/ | Icons em PNG |

### Latino-Americano & Brasileiro
| Site | URL | Best For |
|------|-----|----------|
| Wikimedia Brasil | https://commons.wikimedia.org/wiki/Category:Images_from_Brazil | Cultura, natureza, história BR |
| Flickr Commons Brasil | https://www.flickr.com/commons | Arquivos históricos BR |
| Brasil com S | https://brasilcoms.com/ | Fotografia brasileira autoral |
| Brazil Photos | https://www.brazilphotos.com/ | Turismo, paisagens BR |
| Visit Brasil | https://www.visitbrasil.com/ | Turismo, cultura BR |
| Pixabay PT | https://pixabay.com/pt/ | Busca em português |
| Pexels PT-BR | https://www.pexels.com/pt-br/ | Busca em português |
| Unsplash PT-BR | https://unsplash.com/pt-br | Busca em português |
| Freepik | https://www.freepik.com/ | Vectors, PSDs, fotos |
| Flaticon | https://www.flaticon.com/ | Ícones vetoriais |
| Iconfinder | https://www.iconfinder.com/ | Ícones por estilo |
| Noun Project | https://thenounproject.com/ | Ícones conceituais |
| Vexels | https://www.vexels.com/ | Merch, estampas, vectors |
| Dreamstime Brasil | https://br.dreamstime.com/ | Stock em português |
| Adobe Stock Free | https://stock.adobe.com/br/free | Fotos gratuitas Adobe |
| Shutterstock Brasil | https://www.shutterstock.com/pt/ | Editorial, stock BR |
| Agência Brasil | https://agenciabrasil.ebc.com.br/ | Fotojornalismo BR |
| IBGE Imagens | https://www.ibge.gov.br/ | Mapas, dados visuais BR |
| Embratur | https://embratur.com.br/ | Turismo Brasil |
| Flickr Brasil Search | https://www.flickr.com/search/?text=Brazil | Busca Flickr por BR |

### Vectors & Illustrations
| Site | URL | Best For |
|------|-----|----------|
| Freepik | https://br.freepik.com/ | General vectors, illustrations, PSDs |
| Freepik Free Vectors | https://br.freepik.com/vetores/recursos-gratuitos | Gratuitos destacados |
| Freepik Online Design | https://br.freepik.com/vetores/design-online | Design vectors |
| Vecteezy | https://pt.vecteezy.com/ | Vectors, illustrations, patterns |
| Vecteezy Illustrations | https://pt.vecteezy.com/vetor-gratis/ilustra%C3%A7%C3%B5es | Illustration focus |
| Icons8 Illustrations | https://icons8.com.br/illustrations | Consistent illustration system |
| unDraw | https://undraw.co/ | Open-source illustrations, customizable color |
| Open Peeps | https://www.openpeeps.com/ | Hand-drawn people illustrations |
| Open Doodles | https://www.opendoodles.com/ | Free sketchy illustrations |
| DrawKit | https://www.drawkit.com/ | MIT-licensed illustrations |
| ManyPixels Illustrations | https://www.manypixels.co/gallery | Isometric & 2D illustrations |
| Storyset by Freepik | https://storyset.com/ | Animated/customizable illustrations |
| IRA Design | https://iradesign.io/ | Gradient illustrations, customizable |
| Humaaans | https://www.humaaans.com/ | Mix-and-match people illustrations |
| Blush | https://blush.design/ | Customizable illustration system |
| Lukasz Adam | https://lukaszadam.com/illustrations | Free SVG illustrations |
| Ouch! by Icons8 | https://icons8.com/illustrations | Consistent illustration packs |
| Isometric | https://isometric.online/ | Isometric illustrations free |
| Isoflat | https://isoflat.com/ | Isometric flat vectors |
| Shapefest | https://www.shapefest.com/ | 3D shapes, objects, scenes |
| Openclipart | https://openclipart.org/ | Public domain clipart |
| SVG Repo | https://www.svgrepo.com/ | Free SVG vectors & icons |
| Public Domain Vectors | https://publicdomainvectors.org/ | Vectors domínio público |
| Vectorportal | https://www.vectorportal.com/ | Free vectors by category |
| Vector4Free | https://www.vector4free.com/ | Free vector art |
| ClipSafari | https://clipsafari.com/ | Clipart SVG collection |
| Clker | https://www.clker.com/ | Royalty-free clipart |
| Noun Project | https://thenounproject.com/ | Icon & illustration concepts |
| Iconduck | https://iconduck.com/ | Open-source icons & illustrations |
| Iconfinder | https://www.iconfinder.com/ | Icons & illustrations by style |
| Flaticon | https://www.flaticon.com/ | SVG icons, stickers, illustrations |
| Seeklogo | https://seeklogo.com/ | Brand logos |
| Brands of the World | https://www.brandsoftheworld.com/ | Vector brand logos |
| FreeSVG | https://freesvg.org/ | Public domain SVGs |
| SVG Silh | https://svgsilh.com/ | Free SVG silhouettes |
| Rawpixel Vectors | https://www.rawpixel.com/ | Vintage, artistic vectors |
| Pixabay Vectors | https://pixabay.com/vectors/ | Free vector images |
| Pexels Graphics | https://www.pexels.com/ | Free graphics & videos |
| Canva Elements | https://www.canva.com/ | Design elements (requires account) |
| Adobe Express Assets | https://www.adobe.com/express/ | Free Adobe templates & assets |
| Shutterstock Vectors | https://www.shutterstock.com/ | Premium vectors (some free) |
| Dreamstime Vectors | https://www.dreamstime.com/ | Stock vectors |
| Depositphotos Vectors | https://depositphotos.com/ | Royalty-free vectors |
| Vexels | https://www.vexels.com/ | Merch-ready vectors, PNGs |
| UI8 | https://ui8.net/ | Premium UI & illustration packs |
| 99designs Resources | https://99designs.com/ | Design inspirations |
| Creative Market Graphics | https://creativemarket.com/ | Design assets (free + paid) |
| Craftwork | https://craftwork.design/ | UI kits, illustrations |
| LS Graphics | https://www.ls.graphics/ | Mockups, 3D, illustrations |
| Kittl Assets | https://www.kittl.com/ | Design assets & templates |
| Humbleicons | https://humbleicons.com/ | Free SVG icons |
| Streamline | https://www.streamlinehq.com/ | Icon & illustration system |
| Iconscout | https://iconscout.com/ | Icons, 3D, illustrations |
| GraphicBurger | https://graphicburger.com/ | Free design resources |
| Pixeltrue | https://www.pixeltrue.com/ | Illustrations & design assets |
| Delesign | https://www.delesign.com/ | Free design resources |
| 3Dicons | https://3dicons.co/ | Free 3D icons |
| 3D Illustrations | https://3dillustrations.co/ | Free 3D scenes |

### Icon Libraries
| Site | URL | Format | Notes |
|------|-----|--------|-------|
| Flaticon | https://www.flaticon.com/br/ | SVG, PNG | Maior biblioteca de ícones, pacotes por tema |
| Flaticon SVG | https://www.flaticon.es/iconos-gratis/svg | SVG | Filtro só SVG |
| Icons8 | https://icons8.com.br/icons | SVG, PNG, 3D | Ícones, ilustrações, 3D |
| Icons8 SVG | https://icons8.com.br/icons/set/svg | SVG | Filtro SVG |
| IconScout | https://iconscout.com/pt/icons | SVG, 3D, Lottie | Ícones, 3D, animações |
| IconScout SVG | https://iconscout.com/fr/icons/svg | SVG | Filtro SVG |
| Vecteezy Icons SVG | https://pt.vecteezy.com/svg-gratis/icones | SVG | Vetores gratuitos |
| Freepik Icons SVG | https://br.freepik.com/vetores | SVG, EPS | Parte da biblioteca Freepik |
| Freepik SVG Icons | https://www.freepik.es/iconos/svg | SVG | Filtro SVG Freepik |
| Noun Project | https://thenounproject.com/ | SVG | Ícones conceituais, universal |
| Iconduck | https://iconduck.com/ | SVG | Open source, 350k+ ícones |
| Iconfinder | https://www.iconfinder.com/ | SVG, PNG | Por estilo e licença |
| SVG Repo | https://www.svgrepo.com/ | SVG | 500k+ SVGs gratuitos |
| Openclipart | https://openclipart.org/ | SVG, PNG | Clipart domínio público |
| FreeSVG | https://freesvg.org/ | SVG | SVG domínio público |
| Clker | https://www.clker.com/ | SVG, PNG | Clipart royalty-free |
| ClipSafari | https://clipsafari.com/ | SVG | Clipart SVG gratuito |
| SVG Silh | https://svgsilh.com/ | SVG | SVG silhouettes free |
| Iconmonstr | https://iconmonstr.com/ | SVG, PNG | Ícones minimalistas gratuitos |
| Streamline | https://www.streamlinehq.com/ | SVG | Sistema de ícones + ilustrações |
| Lordicon | https://lordicon.com/ | SVG, Lottie | Ícones animados |
| Remix Icon | https://remixicon.com/ | SVG | Open source, 2900+ ícones |
| Heroicons | https://heroicons.com/ | SVG | Por Tailwind Labs, outline + solid |
| Tabler Icons | https://tabler.io/icons | SVG | 5200+ ícones open source |
| Phosphor Icons | https://phosphoricons.com/ | SVG, Webfont | Nosso preferido, 6 pesos |
| Lucide | https://lucide.dev/ | SVG | Open source, ~1500 ícones |
| Material Symbols | https://fonts.google.com/icons | SVG, Font | Google, variable weight |
| Font Awesome | https://fontawesome.com/ | SVG, Webfont | Clássico, free + pro |
| Bootstrap Icons | https://icons.getbootstrap.com/ | SVG, Font | Free, 2000+ ícones |
| Feather Icons | https://feathericons.com/ | SVG | Minimalistas, open source |
| Boxicons | https://boxicons.com/ | SVG, Webfont | 2000+ ícones free |
| Ionicons | https://ionic.io/ionicons | SVG | Open source, 1300+ |
| Simple Icons | https://simpleicons.org/ | SVG | Logos de marcas |
| Weather Icons | https://erikflowers.github.io/weather-icons/ | Font, CSS | Ícones climáticos |
| Iconoir | https://iconoir.com/ | SVG | Open source, 1500+ |
| Eva Icons | https://akveo.github.io/eva-icons/ | SVG, Font | Outline + fill |
| Jam Icons | https://jam-icons.com/ | SVG | 1000+ ícones free |
| Teenyicons | https://teenyicons.com/ | SVG | Mini ícones (16px otimizado) |
| Radix Icons | https://www.radix-ui.com/icons | SVG | Por Radix UI, 300+ |
| Map Icons | https://mapicons.mapsmarker.com/ | PNG, SVG | Ícones de mapa |
| Game-Icons | https://game-icons.net/ | SVG | 4000+ ícones de jogos |
| Material Design Icons | https://pictogrammers.com/library/mdi/ | SVG | 7000+ ícones, vasta |
| Octicons | https://primer.style/octicons/ | SVG | Por GitHub |
| CSS.gg | https://css.gg/ | CSS, SVG | Ícones via CSS puro |
| Circum Icons | https://circumicons.com/ | SVG | Circular design, 300+ |
| Line Awesome | https://icons8.com/line-awesome | Font | Alternativa free ao Font Awesome |
| Untitled UI Icons | https://www.untitledui.com/icons | SVG | 4200+, por Figma |
| Hugeicons | https://hugeicons.com/ | SVG, 3D | 3500+ ícones gratuitos |
| Akar Icons | https://akaricons.com/ | SVG | 630+, open source |
| Solar Icons | https://www.svgrepo.com/collection/solar-icons/ | SVG | Coleção Solar no SVG Repo |
| Tiny Icons | https://www.tinyicons.com/ | SVG | 450+, minimalistas |

### Usage Rules
- Sempre verificar licença antes de usar (alguns pedem atribuição)
- Para Unsplash: attribution opcional mas recomendada
- Para Wikimedia/Flickr Commons: verificar licença específica de cada imagem
- Preferir imagens com `w=1080` ou maior para qualidade em telas retina
- Usar PNG com fundo transparente para elementos recortados (stickers, pessoas, 3D)

---

## Platform Dimensions

| Plataforma | Formato | Dimensões (px) |
|------------|---------|----------------|
| Instagram | Post | 1080 × 1080 |
| Instagram | Story / Reel | 1080 × 1920 |
| Instagram | Carrossel | 1080 × 1080 (cada) |
| Facebook | Post | 1200 × 630 |
| Twitter/X | Post | 1200 × 675 |
| LinkedIn | Post | 1200 × 628 |
| LinkedIn | Banner | 1584 × 396 |
| YouTube | Thumbnail | 1280 × 720 |
| Pinterest | Pin | 1000 × 1500 |
| TikTok | Cover | 1080 × 1920 |

---

## Grid Systems de Composição

Escolher UM antes de começar:

| Grid | Descrição | Quando usar |
|------|-----------|-------------|
| **Simétrico** | Conteúdo centralizado, margens iguais | Quotes, CTAs, minimalista |
| **Assimétrico** | Conteúdo em 1 lado, imagem/3D no outro | Produto, feature |
| **Split Diagonal** | Fundo dividido na diagonal com clip-path | Conflito, comparação |
| **Radial** | Conteúdo no centro, elementos orbitando | Hooks, CTAs |
| **Full Bleed** | Imagem ocupa tudo, texto overlay | Editorial, lifestyle |
| **Grid Cards** | Múltiplos cards em grid | Features, dados |
| **Livre** | Elementos fora da grade, transbordamento | Criativo, experimental |

---

## Content Density Limits

| Tipo | Máximo por canvas |
|------|-------------------|
| Quote post | 1 frase curta + autor + logo |
| Headline post | 1 headline + 1 subtitle + CTA |
| Feature post | Headline + 3-4 bullets/icons |
| Carrossel página | 1 heading + 3-4 pontos OU imagem |
| Story | 1 headline curto + CTA |

Se exceder → split em carrossel.

---

## Mockups

| Site | URL | Best For |
|------|-----|----------|
| Placeit | https://placeit.net/ | Mockups de produtos, camisetas, dispositivos |
| Artboard Studio | https://artboard.studio/ | Mockups profissionais online |
| The Mockup Club | https://themockup.club/ | Mockups gratuitos selecionados |
| Mockup World | https://www.mockupworld.co/ | Maior coleção de mockups free |
| Mckups | https://mckups.com/ | Mockups grátis em PSD |
| Mockuuups Studio | https://mockuuups.studio/ | Mockups de dispositivos |
| Smartmockups | https://smartmockups.com/ | Mockups online instantâneos |
| Magnific Mockups | https://www.magnific.com/br/mockups | Mockups grátis em português |
| LS Graphics Mockups | https://www.ls.graphics/ | Mockups 3D premium free |
| Mockup Tree | https://mockuptree.com/ | Mockups PSD gratuitos |
| Pixeden Mockups | https://www.pixeden.com/ | Mockups profissionais free |
| GraphicBurger Mockups | https://graphicburger.com/ | Mockups gratuitos PSD |
| Original Mockups | https://originalmockups.com/ | Mockups free originais |
| Free Mockup Zone | https://freemockupzone.com/ | Mockups variados free |
| Pixel Buddha Mockups | https://pixelbuddha.net/ | Mockups gratuitos |
| MockupsJar | https://mockupsjar.com/ | Mockups free para download |
| Medialoot Mockups | https://medialoot.com/ | Mockups + design resources |
| Mr.Mockup | https://mrmockup.com/ | Mockups gratuitos selecionados |
| Mockup Maison | https://mockupmaison.com/ | Mockups grátis elegantes |
| Good Mockups | https://goodmockups.com/ | Mockups free de qualidade |
| MockupBro | https://mockupbro.com/ | Mockups gratuitos variados |
| Mockup Love | https://mockuplove.com/ | Coleção de mockups free |
| MockupDen | https://mockupden.com/ | Mockups PSD gratuitos |
| Freemockups | https://freemockups.org/ | Mockups grátis gerais |
| Mockup Free | https://mockupfree.co/ | Mockups minimalistas free |
| Yellow Images Mockups | https://yellowimages.com/ | Mockups premium (alguns free) |
| Envato Elements Mockups | https://elements.envato.com/ | Milhares de mockups (assinatura) |
| Freepik Mockups | https://www.freepik.com/mockups | Mockups vetoriais gratuitos |
| Canva Mockups | https://www.canva.com/ | Mockups online (requer conta) |
| Adobe Express | https://www.adobe.com/express/ | Mockups gratuitos Adobe |
| PSD Repo | https://psdrepo.com/ | Mockups e templates PSD |
| Graphic Pear | https://graphicpear.com/ | Mockups gratuitos |
| Unblast Mockups | https://unblast.com/mockups/ | Mockups free selecionados |
| Dribbble Resources | https://dribbble.com/ | Inspiração + mockups da comunidade |
| Behance | https://www.behance.net/ | Portfólios com mockups free |
| UI8 | https://ui8.net/ | Mockups UI profissionais |
| Crew Mockups | https://www.crewmockups.com/ | Mockups de time/escritório |
| Mediamodifier | https://mediamodifier.com/ | Gerador de mockups online |

---

## Textures & Backgrounds

| Site | URL | Best For |
|------|-----|----------|
| Unsplash Textures | https://unsplash.com/pt-br/backgrounds/art/texture | Texturas fotográficas |
| Magnific Textures | https://www.magnific.com/br/fotos-vetores-gratis/textura-do-fundo | Texturas grátis em português |
| Envato Elements Textures | https://elements.envato.com/pt-br/graphics/textures | Texturas premium |
| Shutterstock Textures | https://www.shutterstock.com/pt/search/fundos-texturas | Banco profissional |
| Canva Textures | https://www.canva.com/ | Texturas online (conta grátis) |
| Pexels Backgrounds | https://www.pexels.com/ | Fundos fotográficos gratuitos |
| Pixabay Backgrounds | https://pixabay.com/ | Fundos variados gratuitos |
| Freepik Backgrounds | https://br.freepik.com/ | Vetores de fundo grátis |
| Vecteezy Backgrounds | https://pt.vecteezy.com/ | Fundos vetoriais gratuitos |
| TextureKing | https://textureking.com/ | Texturas fotográficas gratuitas |
| Textures.com | https://www.textures.com/ | Maior acervo de texturas (algumas free) |
| Texture Fabrik | https://texturefabrik.com/ | Texturas seamless grátis |
| Transparent Textures | https://www.transparenttextures.com/ | Padrões transparentes CSS |
| Hero Patterns | https://heropatterns.com/ | Padrões SVG repetitivos |
| Subtle Patterns | https://www.toptal.com/designers/subtlepatterns/ | Padrões sutis gratuitos |
| PatternPad | https://patternpad.com/ | Padrões customizáveis |
| Pattern Monster | https://pattern.monster/ | Padrões SVG gratuitos |
| Patternico | https://patternico.com/ | Padrões seamless free |
| BGJar | https://bgjar.com/ | Backgrounds SVG gratuitos |
| SVG Backgrounds | https://www.svgbackgrounds.com/ | Fundos SVG free |
| Haikei | https://app.haikei.app/ | Gerador de backgrounds SVG |
| Cool Backgrounds | https://coolbackgrounds.io/ | Fundos abstratos free |
| Gradient Hunt | https://gradienthunt.com/ | Paletas gradientes curadas |
| UI Gradients | https://uigradients.com/ | Gradientes prontos |
| Grabient | https://www.grabient.com/ | Gerador de gradientes |
| Noise & Grain | https://www.noiseandgrain.com/ | Texturas de ruído |
| Grainy Gradients | https://www.grainy-gradients.com/ | Gradientes granulados |

---

## Free Fonts

| Site | URL | Best For |
|------|-----|----------|
| Google Fonts | https://fonts.google.com/ | Fontes web gratuitas, vasta biblioteca |
| Font Squirrel | https://www.fontsquirrel.com/ | Fontes comerciais free, curadas |
| Fontshare | https://www.fontshare.com/ | Fontes exclusivas (Cabinet Grotesk, Satoshi) |
| DaFont | https://www.dafont.com/ | Fontes decorativas, display |
| Adobe Fonts | https://fonts.adobe.com/ | Fontes premium (requer Creative Cloud) |
| Typewolf | https://www.typewolf.com/ | Recomendações e pares tipográficos |
| Fontfabric | https://www.fontfabric.com/ | Fontes display modernas free |
| 1001 Fonts | https://www.1001fonts.com/ | Fontes gratuitas variadas |
| The League of Moveable Type | https://www.theleagueofmoveabletype.com/ | Open source, qualidade editorial |
| Lost Type | https://www.losttype.com/ | Fontes indie pagas (PAY WHAT YOU WANT) |
| Velvetyne | https://velvetyne.fr/ | Fontes experimentais francesas |
| Fontesk | https://fontesk.com/ | Fontes free curadas |
| Creative Fabrica Free | https://www.creativefabrica.com/ | Fontes gratuitas semanais |
| Befonts | https://befonts.com/ | Fontes free modernas |
| FontSpace | https://www.fontspace.com/ | Fontes gratuitas por designer |
| Pixel Surplus | https://pixelsurplus.com/ | Fontes + design resources |
| Unblast Fonts | https://unblast.com/fonts/ | Fontes free selecionadas |
| Open Foundry | https://open-foundry.com/ | Fontes open source curadas |
| Libre Fonts | https://librefonts.com/ | Buscador de fontes livres |
| Freebiesbug Fonts | https://freebiesbug.com/fonts/ | Fontes gratuitas |
| Fontspring | https://www.fontspring.com/ | Fontes premium (free trials) |
| MyFonts Free | https://www.myfonts.com/ | Fontes gratuitas selecionadas |
| FontGet | https://www.fontget.com/ | Fontes free download |

---

## Color Palettes

| Site | URL | Best For |
|------|-----|----------|
| Adobe Color | https://color.adobe.com/br/explore | Paletas por regra de cor |
| Color Hunt | https://colorhunt.co/ | Paletas curadas pela comunidade |
| Coolors | https://coolors.co/ | Gerador de paletas rápido |
| Khroma | https://www.khroma.co/ | Paletas por IA treinada no seu gosto |
| Picular | https://picular.co/ | Paletas a partir de palavras |
| Paletton | https://paletton.com/ | Círculo cromático avançado |
| Material Palette | https://www.materialpalette.com/ | Cores Material Design |
| Cohesive Colors | https://cohesivecolors.com/ | Paletas coesas |
| Colordot | https://color.hailpixel.com/ | Paletas minimalistas |
| Colour Contrast Check | https://webaim.org/resources/contrastchecker/ | Contraste AA/AAA |
| Color Lisa | https://colorlisa.com/ | Paletas de obras de arte |
| Blend | https://www.blend.new/ | Gradientes suaves |
| Happy Hues | https://www.happyhues.co/ | Paletas com contexto de uso |
| Mycolor.space | https://mycolor.space/ | Gradientes por cor |
| HueSnap | https://huesnap.com/ | Paletas de imagens |
| Eva Design System | https://eva.design/ | Cores para design systems |
| Tailwind Colors | https://tailwindcss.com/docs/customizing-colors | Paleta Tailwind referência |
| Gradient Hunt | https://gradienthunt.com/ | Gradientes curados |
| UI Gradients | https://uigradients.com/ | Gradientes prontos UI |

---

## Visual References

| Site | URL | Best For |
|------|-----|----------|
| Behance | https://www.behance.net/ | Portfólios completos |
| Dribbble | https://dribbble.com/ | UI shots, componentes |
| Awwwards | https://www.awwwards.com/ | Sites premiados |
| SiteInspire | https://www.siteinspire.com/ | Web design selecionado |
| Land-book | https://land-book.com/ | Landing pages inspiradoras |
| Lapa Ninja | https://www.lapa.ninja/ | Landing pages curadas |
| Muzli | https://muz.li/ | Design inspiration feed |
| CSS Design Awards | https://www.cssdesignawards.com/ | Sites premiados CSS |
| One Page Love | https://onepagelove.com/ | One page websites |
| pttrns | https://pttrns.com/ | Mobile UI patterns |
| Mobile Patterns | https://www.mobile-patterns.com/ | Padrões mobile |
| UI Movement | https://uimovement.com/ | UI animations |
| Minimal Gallery | https://minimal.gallery/ | Design minimalista |
| Godly | https://godly.website/ | Sites extraordinários |
| Commerce Cream | https://commercecream.com/ | E-commerce inspiração |
| Collect UI | https://collectui.com/ | UI diário curado |
| Refero | https://refero.design/ | Busca por referências |
| Designspiration | https://www.designspiration.com/ | Inspiração visual |
| Pinterest | https://www.pinterest.com/ | Mood boards |
| Mobbin | https://mobbin.com/ | Screenshots de apps reais |
| Screenlane | https://screenlane.com/ | UI mobile patterns |
| Figma Community | https://www.figma.com/community | Templates, plugins, assets |
| Best Website Gallery | https://bestwebsite.gallery/ | Sites bem desenhados |
| SaaS UI | https://saasui.design/ | Interfaces SaaS |
| UI Garage | https://uigarage.net/ | UI inspirations |
| Really Good Emails | https://reallygoodemails.com/ | Email design |
| Email Love | https://emaillove.com/ | Email inspiration |

---

## Brazilian Resources

| Site | URL | Best For |
|------|-----|----------|
| Acervos Digitais FAU USP | https://www.acervosdigitais.fau.usp.br/ | Acervo digital de design |
| Acervo Colaborativo de Design | https://acervocolaborativodedesign.com.br/ | Design brasileiro colaborativo |
| Arquivo Contemporâneo | https://arquivocontemporaneo.com.br/O-Arquivo | Design contemporâneo BR |
| ESDI / História do Design BR | https://www.esdi.uerj.br/ | História do design brasileiro |
| Designi Brasil | https://www.designi.com.br/ | Design brasileiro |
| Banco de Imagens Gov.br | https://www.gov.br/ | Imagens governamentais BR |
| Agência Brasil | https://agenciabrasil.ebc.com.br/ | Fotojornalismo BR |
| IBGE | https://www.ibge.gov.br/ | Mapas, dados visuais BR |
| Instituto Moreira Salles | https://ims.com.br/ | Fotografia e cultura BR |
| Museu da Imagem e do Som | https://www.mis-sp.org.br/ | Acervo audiovisual SP |
| Biblioteca Nacional Digital | https://bndigital.bn.gov.br/ | Acervo histórico digital |
| Museu Paulista USP | https://museu.paulusp.br/ | Acervo histórico |
| MASP | https://masp.org.br/ | Acervo de arte brasileira |
| Itaú Cultural | https://itaucultural.org.br/ | Arte e cultura brasileira |
| Pinacoteca de São Paulo | https://pinacoteca.org.br/ | Acervo de arte |
| Arquivo Nacional | https://www.gov.br/arquivonacional/ | Documentos históricos |
| Fundação Joaquim Nabuco | https://www.gov.br/fundaj/ | Cultura nordestina |
| Museu Afro Brasil | https://museuafrobrasil.org.br/ | Arte afro-brasileira |
| MAC USP | https://mac.usp.br/ | Arte contemporânea |
| Sesc Digital | https://www.sescsp.org.br/ | Cultura digital |
| IEB USP | https://www.ieb.usp.br/ | Estudos brasileiros |
| Brasiliana Guita e Mindlin | https://www.bbm.usp.br/ | Acervo raro brasileiro |
| Funarte | https://www.gov.br/funarte/ | Arte e cultura BR |

---

## Latin American Resources

| Site | URL | Best For |
|------|-----|----------|
| Memoria Chilena | https://www.memoriachilena.gob.cl/ | Cultura e história chilena |
| Museo Nacional de Bellas Artes Chile | https://www.mnba.gob.cl/ | Acervo de arte chilena |
| Museo del Diseño Chile | https://www.museodeldiseno.cl/ | Design chileno |
| Archivo General Argentina | https://www.argentina.gob.ar/interior/archivo-general-de-la-nacion | Arquivo histórico ARG |
| Museo Nacional de Bellas Artes ARG | https://www.bellasartes.gob.ar/ | Acervo de arte argentina |
| CAC Quito | https://www.cacq.gob.ec/ | Arte contemporânea Equador |
| MALI Lima | https://www.mali.pe/ | Acervo de arte peruana |
| Biblioteca Nacional del Perú | https://www.bnp.gob.pe/ | Acervo cultural peruano |
| AGN México | https://www.gob.mx/agn | Arquivo geral México |
| MUNAL México | https://www.munal.mx/ | Acervo de arte mexicana |
| Museo Tamayo | https://www.museotamayo.org/ | Arte contemporânea MX |
| Banrepcultural Colombia | https://www.banrepcultural.org/ | Cultura colombiana Banrep |
| Biblioteca Luis Ángel Arango | https://www.banrepcultural.org/biblioteca-luis-angel-arango | Acervo cultural COL |
| MAM Bogotá | https://www.mam.org.co/ | Arte moderna Bogotá |
| MAM Medellín | https://www.elmamm.org/ | Arte moderna Medellín |
| Museo Nacional de Arte Bolivia | https://www.museonacionaldearte.gob.bo/ | Acervo de arte boliviana |
| Museo Nacional de Antropología MX | https://www.mna.inah.gob.mx/ | Antropologia mexicana |
| MAM Santo Domingo | https://www.mamd.do/ | Arte moderna dominicana |
| MNAV Uruguai | https://mnav.gub.uy/ | Acervo de arte uruguaia |

## Composition Rules (ANTI-TEMPLATE)

- Imagem principal NÃO precisa ocupar fundo inteiro
- Elemento pode atravessar limite do card
- Máscara orgânica > corte reto (quando pede emoção)
- Sombras com direção, distância e intenção (nunca default)
- Espaço vazio também é desenhado (~40% respiro recomendado)
- Nunca repetir mesma estrutura em posts diferentes
- Toda peça precisa de 3+ camadas: base, sujeito, profundidade
- Conteúdo NÃO precisa estar centralizado — use assimetria

---

## CSS Architecture (Required)

```css
:root {
  --canvas-width: 1080px;
  --canvas-height: 1080px;
  --pad: clamp(36px, 5.5cqw, 80px);
  --font-display: 'Cabinet Grotesk', sans-serif; /* NUNCA Inter/Roboto */
  --font-body: 'Satoshi', sans-serif;
  --title: clamp(40px, 8.5cqw, 88px);
  --body: clamp(16px, 2.2cqw, 24px);
}

.canvas {
  width: var(--canvas-width);
  height: var(--canvas-height);
  overflow: hidden;
  position: relative;
  container-type: inline-size;
}
```

---

## Carousel HTML Architecture

```html
<div class="carousel">
  <div class="carousel-track">
    <div class="carousel-page"><!-- slide --></div>
    <div class="carousel-page"><!-- slide --></div>
  </div>
  <div class="carousel-dots"></div>
</div>
```

Com CarouselController JS (swipe, teclado, dots). Sem setas visíveis.

---

## Mask Library (CSS)

```css
.mask-organic { mask-image: radial-gradient(ellipse at 45% 50%, black 40%, transparent 60%); }
.mask-fade-b { mask-image: linear-gradient(to bottom, black 30%, transparent 100%); }
.mask-fade-t { mask-image: linear-gradient(to top, black 30%, transparent 100%); }
.mask-circle-irregular { mask-image: url("data:image/svg+xml,..."); }
.mask-torn { mask-image: url("data:image/svg+xml,..."); }
```

Sempre incluir `-webkit-mask-image` com o mesmo valor.

---

## Clip Paths

```css
.clip-diagonal { clip-path: polygon(0 0, 100% 0, 100% 100%, 0 85%); }
.clip-hex { clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%); }
```

---

## Shadow Library

```css
.shadow-soft  { box-shadow: 0 18px 50px rgba(0,0,0,.18); }
.shadow-hard  { box-shadow: 8px 8px 0 rgba(0,0,0,.9); }
.shadow-float { box-shadow: 0 24px 80px rgba(0,0,0,.22); }
.shadow-dual  { box-shadow: 0 4px 12px rgba(0,0,0,.12), 0 18px 40px rgba(0,0,0,.1); }
.shadow-accent { box-shadow: 0 20px 60px rgba(255,214,10,.15); }
.shadow-inner { box-shadow: inset 0 2px 8px rgba(0,0,0,.12); }
```

---

## CSS Effects Library

### Texture & Grain

```css
/* Grain / Film noise */
.grain { opacity: 0.035; mix-blend-mode: overlay; background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='5'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E"); }

.grain-heavy { opacity: 0.07; mix-blend-mode: overlay; background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='nh'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.4' numOctaves='5'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23nh)'/%3E%3C/svg%3E"); }

/* Conic noise overlay */
.noise-overlay { opacity: 0.15; background: repeating-conic-gradient(rgba(255,255,255,0.02) 0%, transparent 0.5%) 50% / 3px 3px; mix-blend-mode: soft-light; }

/* Paper texture */
.texture-paper { background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512'%3E%3Cfilter id='p'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.04' numOctaves='5'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23p)' opacity='0.12'/%3E%3C/svg%3E"); background-size: 512px 512px; mix-blend-mode: multiply; }

/* Halftone pattern */
.texture-halftone { background: radial-gradient(circle, rgba(0,0,0,0.03) 1px, transparent 1px); background-size: 12px 12px; }
```

### Glass & Frost

```css
.glass { background: rgba(255,255,255,0.04); backdrop-filter: blur(16px) saturate(1.3); border: 1px solid rgba(255,255,255,0.06); }
.glass-heavy { background: rgba(255,255,255,0.08); backdrop-filter: blur(30px) saturate(1.5); border: 1px solid rgba(255,255,255,0.1); }
.glass-dark { background: rgba(0,0,0,0.3); backdrop-filter: blur(20px); border: 1px solid rgba(255,255,255,0.05); }
.glass-edge { background: rgba(255,255,255,0.02); backdrop-filter: blur(8px); border-top: 1px solid rgba(255,255,255,0.15); }
```

### Glow & Light Effects

```css
/* Neon glow (texto) */
.glow-text { text-shadow: 0 0 10px var(--accent), 0 0 40px var(--accent), 0 0 80px var(--accent); }

/* Soft glow (elemento) */
.glow-soft { box-shadow: 0 0 30px rgba(255,214,10,0.15), 0 0 60px rgba(255,214,10,0.05); }

/* Inner light */
.glow-inner { box-shadow: inset 0 0 40px rgba(255,255,255,0.05); }

/* Edge light / rim light */
.glow-rim { box-shadow: inset 0 1px 0 rgba(255,255,255,0.12), inset 0 -1px 0 rgba(0,0,0,0.3); }

/* Lens flare / light leak (decorativo) */
.light-leak { background: linear-gradient(135deg, rgba(255,200,100,0.08) 0%, transparent 40%, rgba(100,150,255,0.05) 100%); pointer-events: none; }

/* Vignette escura */
.vignette { box-shadow: inset 0 0 150px rgba(0,0,0,0.4); }

/* Vignette clara */
.vignette-light { box-shadow: inset 0 0 120px rgba(255,255,255,0.05); }
```

### Shadow System

```css
/* Curtas e precisas */
.shadow-short { box-shadow: 0 2px 8px rgba(0,0,0,0.12); }
.shadow-sharp { box-shadow: 3px 3px 0 rgba(0,0,0,0.8); }
.shadow-sharp-color { box-shadow: 4px 4px 0 var(--accent); }

/* Profundidade média */
.shadow-soft { box-shadow: 0 18px 50px rgba(0,0,0,.18); }
.shadow-card { box-shadow: 0 4px 12px rgba(0,0,0,.08), 0 8px 24px rgba(0,0,0,.06); }
.shadow-dual { box-shadow: 0 4px 12px rgba(0,0,0,.12), 0 18px 40px rgba(0,0,0,.1); }

/* Flutuantes / hero */
.shadow-float { box-shadow: 0 24px 80px rgba(0,0,0,.22); }
.shadow-hero { box-shadow: 0 40px 120px rgba(0,0,0,.3); }

/* Coloridas */
.shadow-accent { box-shadow: 0 20px 60px rgba(255,214,10,.15); }
.shadow-purple { box-shadow: 0 20px 60px rgba(123,44,191,.15); }
.shadow-green { box-shadow: 0 20px 60px rgba(45,139,94,.15); }

/* Inner */
.shadow-inner { box-shadow: inset 0 2px 8px rgba(0,0,0,.12); }
.shadow-inner-soft { box-shadow: inset 0 1px 4px rgba(0,0,0,.06); }

/* Longas (brutalistas) */
.shadow-long { box-shadow: 12px 12px 0 rgba(0,0,0,0.1); }
.shadow-long-accent { box-shadow: 12px 12px 0 var(--accent); }
```

### Borders & Strokes

```css
/* Traço fino */
.stroke-thin { border: 1px solid rgba(255,255,255,0.08); }
.stroke-thin-dark { border: 1px solid rgba(0,0,0,0.1); }

/* Traço médio */
.stroke { border: 1.5px solid rgba(255,255,255,0.12); }
.stroke-accent { border: 1.5px solid var(--accent); }

/* Traço pesado */
.stroke-bold { border: 3px solid rgba(255,255,255,0.15); }
.stroke-bold-accent { border: 3px solid var(--accent); }

/* Borda dupla */
.stroke-dual { box-shadow: 0 0 0 1px rgba(255,255,255,0.08), 0 0 0 3px rgba(255,255,255,0.02); }

/* Borda gradiente (pseudo-elemento) */
.stroke-gradient::after { content: ''; position: absolute; inset: 0; border-radius: inherit; padding: 1.5px; background: linear-gradient(135deg, var(--accent), transparent); -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); -webkit-mask-composite: xor; mask-composite: exclude; pointer-events: none; }

/* Borda interna */
.stroke-inset { box-shadow: inset 0 0 0 1px rgba(255,255,255,0.06); }

/* Top line apenas */
.stroke-top { border-top: 1px solid rgba(255,255,255,0.06); }

/* Bottom line apenas */
.stroke-bottom { border-bottom: 1px solid rgba(255,255,255,0.06); }
```

### Blend Modes

```css
.blend-overlay { mix-blend-mode: overlay; }
.blend-multiply { mix-blend-mode: multiply; }
.blend-screen { mix-blend-mode: screen; }
.blend-soft-light { mix-blend-mode: soft-light; }
.blend-hard-light { mix-blend-mode: hard-light; }
.blend-luminosity { mix-blend-mode: luminosity; }
.blend-color { mix-blend-mode: color; }
.blend-difference { mix-blend-mode: difference; }
.blend-exclusion { mix-blend-mode: exclusion; }
```

### Filters

```css
.filter-blur-sm { filter: blur(4px); }
.filter-blur-md { filter: blur(12px); }
.filter-blur-lg { filter: blur(30px); }
.filter-blur-xl { filter: blur(60px); }

.filter-bright { filter: brightness(1.2); }
.filter-dim { filter: brightness(0.7); }
.filter-contrast { filter: contrast(1.3); }
.filter-saturate { filter: saturate(1.5); }
.filter-desaturate { filter: saturate(0.3); }
.filter-grayscale { filter: grayscale(1); }
.filter-sepia { filter: sepia(0.4); }
.filter-hue-rotate { filter: hue-rotate(45deg); }

.filter-drop-shadow { filter: drop-shadow(0 10px 20px rgba(0,0,0,0.3)); }
.filter-drop-shadow-glow { filter: drop-shadow(0 0 20px var(--accent)); }
```

### Clip Paths (Shapes)

```css
/* Geométricos */
.clip-circle { clip-path: circle(50%); }
.clip-ellipse { clip-path: ellipse(40% 50% at 50% 50%); }
.clip-triangle { clip-path: polygon(50% 0%, 0% 100%, 100% 100%); }
.clip-hexagon { clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%); }
.clip-octagon { clip-path: polygon(30% 0%, 70% 0%, 100% 30%, 100% 70%, 70% 100%, 30% 100%, 0% 70%, 0% 30%); }
.clip-diamond { clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%); }
.clip-star { clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%); }

/* Diagonal / split */
.clip-diagonal-tl { clip-path: polygon(0 0, 100% 0, 100% 85%, 0 100%); }
.clip-diagonal-tr { clip-path: polygon(0 0, 100% 0, 100% 100%, 0 85%); }
.clip-diagonal-bl { clip-path: polygon(0 15%, 100% 0, 100% 100%, 0 100%); }
.clip-diagonal-br { clip-path: polygon(0 0, 100% 15%, 100% 100%, 0 100%); }
.clip-split-v { clip-path: polygon(0 0, 50% 0, 50% 100%, 0 100%); }

/* Orgânicos */
.clip-blob { clip-path: polygon(25% 5%, 75% 0%, 100% 30%, 95% 70%, 75% 95%, 30% 100%, 5% 75%, 0% 30%); }
.clip-blob-2 { clip-path: polygon(20% 10%, 70% 5%, 95% 25%, 100% 60%, 80% 90%, 40% 95%, 5% 80%, 0% 40%); }
.clip-organic { clip-path: polygon(15% 8%, 85% 3%, 98% 35%, 92% 78%, 65% 95%, 25% 98%, 2% 72%, 5% 28%); }

/* Bordas irregulares */
.clip-curl-br { clip-path: polygon(0 0, 100% 0, 100% 85%, 85% 100%, 0 100%); }
.clip-notch-tr { clip-path: polygon(0 0, 85% 0, 100% 15%, 100% 100%, 0 100%); }

/* Frames */
.clip-frame { clip-path: polygon(5% 5%, 95% 5%, 95% 95%, 5% 95%); }
.clip-frame-rounded { clip-path: polygon(10% 0%, 90% 0%, 100% 10%, 100% 90%, 90% 100%, 10% 100%, 0% 90%, 0% 10%); }
```

### Mask Patterns

```css
/* Gradiente */
.mask-fade-b { mask-image: linear-gradient(to bottom, black 30%, transparent 100%); -webkit-mask-image: linear-gradient(to bottom, black 30%, transparent 100%); }
.mask-fade-t { mask-image: linear-gradient(to top, black 30%, transparent 100%); }
.mask-fade-l { mask-image: linear-gradient(to left, black 30%, transparent 100%); }
.mask-fade-r { mask-image: linear-gradient(to right, black 30%, transparent 100%); }
.mask-fade-radial { mask-image: radial-gradient(ellipse at 50% 50%, black 35%, transparent 55%); }
.mask-fade-radial-offset { mask-image: radial-gradient(ellipse at 45% 50%, black 40%, transparent 60%); }

/* Orgânico */
.mask-organic { mask-image: radial-gradient(ellipse at 45% 50%, black 40%, transparent 60%); }
.mask-blob { mask-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'%3E%3Cpath d='M30 100 C30 40 80 20 100 20 C120 20 170 40 170 100 C170 160 120 180 100 180 C80 180 30 160 30 100Z' fill='black'/%3E%3C/svg%3E"); mask-size: contain; mask-repeat: no-repeat; mask-position: center; }

/* Circular irregular */
.mask-circle-irregular { mask-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 200 200'%3E%3Cpath d='M100 10 C140 10 190 50 190 100 C190 150 150 190 100 190 C50 190 10 150 10 100 C10 50 60 10 100 10Z' fill='black'/%3E%3C/svg%3E"); mask-size: contain; mask-repeat: no-repeat; mask-position: center; }

/* Diagonal */
.mask-diagonal { mask-image: linear-gradient(135deg, black 50%, transparent 55%); }

/* Horizontal split */
.mask-split-h { mask-image: linear-gradient(to right, black 50%, transparent 52%); }
```

### Decorative Elements

```css
/* Bolha decorativa (blob) */
.deco-blob { width: 300px; height: 300px; border-radius: 60% 40% 50% 50% / 40% 50% 60% 50%; background: radial-gradient(circle at 30% 30%, rgba(255,255,255,0.04), transparent); animation: blob-morph 8s ease-in-out infinite alternate; }

@keyframes blob-morph { 0% { border-radius: 60% 40% 50% 50% / 40% 50% 60% 50%; } 100% { border-radius: 40% 60% 60% 40% / 50% 40% 50% 60%; } }

/* Anéis concêntricos */
.deco-ring { border: 1px solid rgba(255,255,255,0.04); border-radius: 50%; pointer-events: none; }

/* Linha horizontal decorativa */
.deco-line { width: 60px; height: 1.5px; background: var(--accent); border-radius: 2px; }

/* Barra gradiente horizontal */
.deco-bar { height: 4px; background: linear-gradient(90deg, color1, color2, color3); border-radius: 2px; }

/* Cantos decorativos */
.deco-corner { position: absolute; width: 20px; height: 20px; border-color: rgba(255,255,255,0.08); }
.deco-corner-tl { top: 20px; left: 20px; border-top: 1px solid; border-left: 1px solid; }
.deco-corner-tr { top: 20px; right: 20px; border-top: 1px solid; border-right: 1px solid; }
.deco-corner-bl { bottom: 20px; left: 20px; border-bottom: 1px solid; border-left: 1px solid; }
.deco-corner-br { bottom: 20px; right: 20px; border-bottom: 1px solid; border-right: 1px solid; }
```

### Depth & Perspective

```css
.depth-flat { transform: perspective(800px) rotateX(2deg); }
.depth-card { transform: perspective(1000px) rotateY(-3deg) rotateX(2deg); }
.depth-tilt { transform: perspective(900px) rotateY(-2deg); }
.depth-parallax { transform: translateZ(-20px) scale(1.05); }

/* Esfera 3D (cromada / metálica) */
.sphere {
  width: 200px; height: 200px; border-radius: 50%;
  background: radial-gradient(circle at 35% 30%, #fff 0%, #c0c0c0 12%, #666 30%, #333 48%, #888 62%, #ddd 78%, #fff 95%);
  box-shadow: inset 0 -30px 60px rgba(0,0,0,0.4), 0 20px 60px rgba(0,0,0,0.3);
}
.sphere::after {
  content: ''; position: absolute; top: 8%; left: 15%;
  width: 35%; height: 25%; border-radius: 50%;
  background: radial-gradient(circle at 50% 50%, rgba(255,255,255,0.6), transparent);
}
```

### Gradient Text

```css
.gradient-text {
  background: linear-gradient(135deg, #ffffff 30%, #94a3b8 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.gradient-text--brand {
  background: linear-gradient(135deg, var(--accent1) 0%, var(--accent2) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.gradient-text--glow {
  text-shadow: 0 20px 40px rgba(59,130,246,0.3);
}
```

### Glassmorphism Cards

```css
.glass-card {
  background: rgba(255,255,255,0.03);
  border-radius: 30px;
  padding: 25px 35px;
  border: 1px solid rgba(255,255,255,0.08);
  border-top: 1px solid rgba(255,255,255,0.25);
  box-shadow: inset 0 0 40px rgba(255,255,255,0.02), 0 20px 40px rgba(0,0,0,0.4);
  backdrop-filter: blur(12px);
}
.glass-card--dark {
  background: rgba(15,23,42,0.8);
  backdrop-filter: blur(12px);
}
```

### Badge Premium com Glow Dot

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
  width: 10px; height: 10px; border-radius: 50%;
  background: linear-gradient(135deg, var(--accent1), var(--accent2));
  box-shadow: 0 0 15px rgba(var(--accent-rgb),0.8);
}
```

### Stat Cards (2 colunas)

```css
.stats { display: flex; gap: 20px; width: 100%; }
.stat-card { flex: 1; padding: 25px 35px; border-radius: 30px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.08);
  border-top: 1px solid rgba(255,255,255,0.25);
  box-shadow: inset 0 0 40px rgba(255,255,255,0.02), 0 20px 40px rgba(0,0,0,0.4); }
.stat-card .label { color: var(--muted); font-size: 13px; font-weight: 800; letter-spacing: 2px; text-transform: uppercase; }
.stat-card .value { color: white; font-size: 38px; font-weight: 900; letter-spacing: -1px; margin-top: 4px; }
```

### CTA Button com Gradiente

```css
.cta-gradient {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 18px 40px; border-radius: 30px;
  background: linear-gradient(135deg, #2563eb, #7c3aed);
  color: white; font-weight: 900; font-size: 20px; letter-spacing: 0.5px;
  box-shadow: 0 15px 30px rgba(124,58,237,0.4);
  border: 1px solid rgba(255,255,255,0.3);
  cursor: pointer; transition: transform .2s, box-shadow .2s;
}
.cta-gradient:hover { transform: translateY(-2px); box-shadow: 0 20px 40px rgba(124,58,237,0.5); }
```

### Pricing Row

```css
.pricing-row {
  display: flex; align-items: center; justify-content: space-between;
  background: rgba(255,255,255,0.08); border-radius: 40px;
  padding: 15px 15px 15px 40px;
  border: 1px solid rgba(255,255,255,0.2);
  border-top: 1px solid rgba(255,255,255,0.4);
  box-shadow: 0 30px 60px rgba(0,0,0,0.6);
}
.pricing-row .price { color: white; font-size: 42px; font-weight: 900; line-height: 1; }
.pricing-row .period { color: var(--muted); font-size: 18px; font-weight: 800; margin-left: 6px; }
```

### Photo Card com Moldura e Glow

```css
.photo-card { position: relative; border-radius: 40px; overflow: hidden; }
.photo-card img { width: 100%; height: 100%; object-fit: cover; border-radius: 40px; display: block; position: relative; z-index: 1; }
.photo-card .glow-bg { position: absolute; top: 15px; left: 15px; right: -15px; bottom: -15px;
  background: rgba(59,130,246,0.15); border-radius: 40px; filter: blur(30px); z-index: 0; }
.photo-card .frame-border { position: absolute; inset: 0; z-index: 2; pointer-events: none;
  border-radius: 40px; border: 2px solid rgba(255,255,255,0.2); }
```

### Multi-Layer Atmospheric Gradients

```css
.atmosphere {
  background:
    radial-gradient(ellipse at 20% 10%, rgba(59,130,246,0.15) 0%, transparent 55%),
    radial-gradient(ellipse at 80% 90%, rgba(168,85,247,0.12) 0%, transparent 55%),
    radial-gradient(ellipse at 50% 50%, rgba(236,72,153,0.08) 0%, transparent 50%),
    #030305;
}
```

### Grid Estrutural (linhas guia verticais)

```css
.grid-line { position: absolute; top: 0; bottom: 0; width: 1px;
  background: rgba(255,255,255,0.03); pointer-events: none; z-index: 3; }
```

---

## Style Presets (14) + Paletas Sugeridas

| Preset | Vibe | Paleta |
|--------|------|--------|
| Bold Signal | Alto impacto | Preto + Amarelo + Vermelho |
| Electric Studio | Profissional | Azul marinho + Ciano + Branco |
| Creative Voltage | Energético | Laranja + Preto + Amarelo neon |
| Dark Botanical | Elegante | Verde escuro + Ouro + Marfim |
| Notebook Tabs | Editorial | Azul slate + Cinza quente + Laranja |
| Pastel Geometry | Amigável | Rosa pastel + Azul + Verde menta |
| Vintage Editorial | Personalidade | Marrom sépia + Creme + Verde militar |
| Neon Cyber | Tech | Preto + Rosa neon + Ciano |
| Swiss Modern | Minimalista | Branco + Preto + Vermelho |
| Paper & Ink | Literário | Off-white + Preto + Terracota |
| Terminal Green | Dev | Preto + Verde neon + Cinza |
| Neural Research | Acadêmico | Azul royal + Cinza + Verde |
| Stripe Blueprint | Startup | Azul + Branco + Laranja |
| Collage Digital | Experimental | Multicolorido + Preto |

---

## Coherence Rules (Multi-Slide)

- **Mesmo elemento 3D/gráfico** em todas as páginas OU progressão intencional
- **Mesma paleta** em todos os slides (pode variar tom, não cor)
- **Mesma espessura de fonte** pro mesmo papel
- **CTA** sempre no mesmo canto
- Dot navigation + page counter em todas as páginas

---

## Pipeline

### Draft Mode
HTML mínimo, sem refinamento, só pra mostrar direção visual rápida. Use assets placeholder.

### Final Mode
- Pixel perfect
- 6+ camadas visuais (arquitetura em profundidade, não só "texto em fundo")
- 5+ técnicas simultâneas (gradiente atmosférico + 3D + glass card + gradient text + multi-shadow + grid)
- Assets 3D reais (FluentUI emoji, Pixcap) + fotografia (Unsplash) + ícones (Phosphor)
- Máscara + sombra + textura aplicados
- Coerência entre slides verificada

### Etapas
1. **Brief** — plataforma, formato, conteúdo, imagens (Unsplash/Pictify/próprias/nenhuma)
2. **Composition Planning (OBRIGATÓRIO)** — antes de qualquer código, defina:
   - Layer stack (z-index) com mínimo 6 camadas
   - Asset Check: 3D? Foto? Ícone?
   - Técnicas selecionadas: marque 5+ da lista abaixo
   - Esboço: qual camada vai onde no slide
3. **Grid** — escolher sistema de composição
4. **Style Discovery** — presets + mood + paleta → 3 previews rascunho → escolha
5. **Asset Busca** — FluentUI 3D (raw.githubusercontent), Unsplash, Pictify MCP, IconScout, SVGMaker
6. **Geração Final** — HTML único (ou carrossel) com assets via CDN/URLs externas
7. **Export** — screenshot ou Puppeteer para PNG

---

## VALIDAÇÃO OBRIGATÓRIA (antes de finalizar)

- [ ] Canvas tem `overflow: hidden`?
- [ ] Dimensões exatas da plataforma?
- [ ] Conteúdo cabe sem scroll? (ver density limits)
- [ ] 6+ camadas visuais? (gradiente atmosférico → grid → 3D → foto → glass card → texto)
- [ ] Usou 5+ técnicas simultâneas? (gradient text, glassmorphism, multi-shadow, stat card, badge premium, CTA gradient, etc.)
- [ ] Tem asset 3D real (FluentUI/Pixcap)?
- [ ] Tem asset de foto real (Unsplash/Pexels)?
- [ ] Usou máscara ou recorte não-quadrado?
- [ ] Sombra multi-camada (não box-shadow único)?
- [ ] Fonte não é Inter, Roboto, Poppins ou system-ui?
- [ ] Gradiente não é genérico (roxo+branco)?
- [ ] Não centralizou tudo?
- [ ] Contraste AA+?
- [ ] Não parece template genérico?
- [ ] Assets são de fonte real (Unsplash/Pictify/FluentUI/etc), não CSS inventado?
- [ ] Coerência entre slides (se carrossel)?

Se parecer template genérico → falha. Refaça composição com mais profundidade e técnicas simultâneas.

---

## Fontes & Icons (Allowed)

**Fontes:** Anton, Cabinet Grotesk, Satoshi, Space Grotesk, Sora, DM Sans, Gambetta, Switzer, Clash Display, Stardom, Zodiak, Panchang, Bonny, Raleway (apenas pesos finos), Playfair Display.

**PROIBIDO:** Inter, Roboto, Poppins, Open Sans, Lato, Montserrat (exceto pesos extrabold display), system-ui.

**Ícones:** Phosphor Icons (preferido) > Font Awesome > Bootstrap Icons. Proibido emoji para elementos decorativos.