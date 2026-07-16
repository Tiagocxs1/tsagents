# SEO & Digital Performance Complete Audit

Skill unificada para auditoria e otimização completa de SEO moderno, performance e experiência digital.
Cobre 11 módulos: SEO, AEO, GEO, AIO, FAQ, TOC, CWV, SXO, CRO, MEO, E-E-A-T.

## Quando Usar

- Auditar e otimizar sites para mecanismos de busca modernos (Google, Bing)
- Otimizar para IA generativa (ChatGPT, Perplexity, Gemini, Claude)
- Melhorar performance (Core Web Vitals)
- Otimizar conversão (CRO) e experiência de busca (SXO)
- SEO Local (MEO)

## Módulo 1: Nova Era da Busca (IA e Linguagem Natural)

### 1. SEO (Search Engine Optimization)
**Checklist:**
- [ ] Palavras-chave principais no H1, URL e primeiro parágrafo
- [ ] Meta description otimizada (155 caracteres com CTA)
- [ ] URLs amigáveis e descritivas
- [ ] Heading hierarchy (H1 -> H2 -> H3) sem pular níveis
- [ ] Conteúdo resolve Search Intent do usuário
- [ ] Técnica do "Próximo Passo Lógico" na estrutura de tópicos

### 2. AEO (Answer Engine Optimization)
**Checklist:**
- [ ] Respostas diretas de 40-60 palavras no início da página
- [ ] Formato Pergunta (H2) -> Resposta direta
- [ ] Listas com marcadores e tabelas curtas para assistentes de voz
- [ ] Featured snippet targeting nos primeiros 40-50 words
- [ ] Linguagem natural (como as pessoas falam)

### 3. GEO (Generative Engine Optimization)
**Checklist:**
- [ ] Estatísticas, porcentagens e dados verificáveis no conteúdo
- [ ] Citações de especialistas reais e jargões técnicos do nicho
- [ ] Links para fontes científicas/governamentais
- [ ] Dados estruturados (Schema.org) implementados
- [ ] Conteúdo com profundidade que IAs usam como fonte

### 4. AIO (AI Optimization)
**Checklist:**
- [ ] Marca mencionada positivamente em fóruns e portais (Digital PR)
- [ ] Perfil no Google Business Profile atualizado
- [ ] Avaliações positivas em plataformas (Trustpilot, Reclame Aqui)
- [ ] Menções textuais à marca (unlinked mentions) monitoradas
- [ ] Google AI Overviews compatível (conteúdo raso descartado)

## Módulo 2: Elementos Estruturais e On-Page

### 5. FAQ (Frequently Asked Questions)
**Checklist:**
- [ ] Seção de FAQ com perguntas reais dos usuários
- [ ] Marcacão FAQ Schema (Schema.org) implementada
- [ ] Respostas começam repetindo parte da pergunta
- [ ] Perguntas validadas via "As pessoas também perguntam" do Google
- [ ] FAQ visível e acessível na página

### 6. TOC (Table of Contents)
**Checklist:**
- [ ] Índice clicável com âncoras HTML
- [ ] IDs de âncora limpos nas tags H2 e H3
- [ ] Palavras-chave secundárias nos títulos do índice
- [ ] TOC visível no topo de artigos/páginas longas
- [ ] Sitelinks funcionando (Google exibe links diretos)

## Módulo 3: Performance Técnica e UX

### 7. CWV (Core Web Vitals)
**Checklist:**
- [ ] LCP < 2.5s (hero image preloaded, sem lazy loading no banner)
- [ ] INP < 200ms (remover scripts pesados de terceiros)
- [ ] CLS < 0.1 (width/height definidos em imagens e anúncios)
- [ ] WebP/AVIF para compressão de imagens
- [ ] Testar com Google PageSpeed Insights semanalmente
- [ ] `next/image` com `priority` no hero
- [ ] Fontes com `font-display: swap`

### 8. SXO (Search Experience Optimization)
**Checklist:**
- [ ] Fontes mínimas 16px
- [ ] Parágrafos máximos 3 linhas
- [ ] Elementos visuais a cada ~300 palavras
- [ ] Tempo de permanência > 10 segundos (monitorar bounce rate)
- [ ] Navegação intuitiva e mobile-first
- [ ] Sem pogo-sticking (usuário não volta ao Google)

### 9. CRO (Conversion Rate Optimization)
**Checklist:**
- [ ] CTA principal visível Above the Fold
- [ ] Botão de conversão nos primeiros segundos de scroll
- [ ] Testes A/B (cor/texto do botão)
- [ ] Formulários otimizados (menos campos = mais conversão)
- [ ] Provas sociais próximas ao CTA
- [ ] CTA único por seção (sem duplicar intenção)

## Módulo 4: Especialidades e Negócios

### 10. MEO (Map Engine Optimization)
**Checklist:**
- [ ] NAP (Name, Address, Phone) idêntico em toda internet
- [ ] Google Business Profile verificado e completo
- [ ] Categoria correta no GBP
- [ ] Fotos reais semanais no perfil
- [ ] Respostas a avaliações com palavras-chave do serviço
- [ ] Posts no Google Meu Negócio

### 11. E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness)
**Checklist:**
- [ ] Página "Quem Somos" robusta com biografia dos autores
- [ ] Perfil do LinkedIn linkado nos artigos
- [ ] Certificações e diplomas listados
- [ ] Política de Privacidade e Termos de Uso no rodapé
- [ ] Página de Contato com informações reais
- [ ] Conteúdo YMYL (saúde/finanças) com autores qualificados

## Módulo 5: Design e Acessibilidade (Cross-skill)

### 12. Acessibilidade (WCAG)
- [ ] Contraste de cor mínimo 4.5:1 (texto normal)
- [ ] Focus states visíveis em elementos interativos
- [ ] Alt text descritivo em imagens
- [ ] ARIA labels em botões de ícone
- [ ] Navegação por teclado funcional
- [ ] Labels em formulários com atributo `for`

### 13. Performance Frontend
- [ ] Imagens em WebP com lazy loading (exceto hero)
- [ ] `prefers-reduced-motion` respeitado
- [ ] Sem layout shift (dimensões fixas em mídia)
- [ ] Bundle size otimizado
- [ ] CSS crítico inline

### 14. UX Writing
- [ ] Copy sem AI-isms (texto genérico de LLM)
- [ ] Headlines claras e específicas
- [ ] CTAs com ação única e benefício claro
- [ ] Sem jargão desnecessário
- [ ] Tom de voz consistente

## Fluxo de Execução

1. **Diagnóstico**: Ler páginas do site e identificar estado atual
2. **Auditar**: Verificar cada checklist item por item
3. **Reportar**: Listar problemas encontrados com localização (file:line)
4. **Corrigir**: Aplicar correções automaticamente onde possível
5. **Verificar**: Re-testar após correções

## Output

Para cada módulo auditado, gerar:
```
## [Módulo] - [Status: ✅ / ⚠️ / ❌]

### Encontrados:
- [file:line] - Problema (severidade)

### Corrigido:
- [file:line] - O que foi feito

### Pendente (requer decisão sua):
- [item] - O que precisa decidir
```