# Handoff: Laila Andrade — Portfolio

## Overview

Portfolio pessoal de uma Product Designer Sênior. Site de página única (home) com 4 páginas de case study detalhadas. Construído em HTML/CSS/JS puro, sem framework — mas totalmente migrável para Next.js / React se necessário.

## Sobre os Arquivos

Os arquivos `.html` neste pacote são **protótipos de design de alta fidelidade** — implementação funcional e completa, não apenas referência visual. Podem ser servidos diretamente como site estático (Vercel, Netlify, GitHub Pages) ou migrados para React/Next.js aproveitando a estrutura existente.

## Fidelidade

**Alta fidelidade (hifi)**: Cores, tipografia, espaçamentos, interações e animações estão implementados e funcionais. O código pode ser usado diretamente como produção ou servir de referência pixel-perfect para migração.

---

## Estrutura de Arquivos

```
index.html              ← Home page principal
iplp.html               ← Case study: iPLP Branded
ies.html                ← Case study: IES Page Branded
card.html               ← Case study: Card de Oferta
paystation.html         ← Case study: Paystation Checkout
assets/
  foto-sobre-mim.png        ← Foto da Laila (Sobre mim + nav avatar + favicon)
  capa-case-iplp.png        ← Thumbnail do case iPLP
  capa-case-iespage.png     ← Thumbnail do case IES
  capa-case-card.png        ← Thumbnail do case Card de Oferta
  capa-case-paystation.png  ← Thumbnail do case Paystation
  logo-qeevo.png            ← Logo Qeevo (experiência)
  logo-cuponomia.png        ← Logo Cuponomia (experiência)
  logo-quero.png            ← Logo Quero Educação (experiência)
  logo-studio7.png          ← Logo Studio 7 (experiência)
  logo-essence.png          ← Logo Essence (experiência)
```

---

## Design Tokens

### Cores
```css
--dark:        #0d0f14   /* Background principal */
--dark-2:      #13171f   /* Background secundário (covers) */
--dark-3:      #1a1f2a   /* Borders / dividers */
--dark-card:   #1e2330   /* Cards */
--brand-blue:  #304FFE   /* Accent primário */
--brand-light: #6E95FF   /* Accent labels / links */
--white:       #ffffff
--muted:       #b8bdd4   /* Texto secundário */
--subtle:      #6b7280   /* Texto terciário / dates */
```

### Tipografia
```
Família display:  DM Serif Display (Google Fonts)
Família corpo:    DM Sans (Google Fonts), pesos 300/400/500/600

Hero título:        DM Serif Display, clamp(28px–46px), weight 400, lh 1.14, ls -0.02em
Section headings:   DM Sans, 24px, weight 600, ls -0.015em
Body:               DM Sans, 16px, weight 400, lh 1.6–1.8
Muted body:         DM Sans, 15px, weight 400, color #b8bdd4
Labels uppercase:   DM Sans, 11px, weight 600, ls 0.14em, uppercase, color #6E95FF
Captions:           DM Sans, 13px, weight 400, color #6b7280
```

### Espaçamento
```
Container max-width:  1160px (home) / 1400px (cases)
Container padding:    40px (home) / 48px (cases)
Section padding:      88px vertical (home) / 120px (cases)
Gap entre cards:      16px
Gap competências:     72px (entre colunas)
```

### Border Radius
```
Cards:         14px
Logo avatars:  10px
Botões pill:   100px
Nav avatar:    50% (circular)
Foto about:    12px
```

### Sombras / Elevação
```css
/* Card hover */
box-shadow: 0 20px 48px rgba(48,79,254,0.12);
/* Nav scrolled */
background: rgba(13,15,20,0.88); backdrop-filter: blur(16px);
```

---

## Screens / Views

### 1. Home (`index.html`)

#### Nav (fixed/sticky)
- Position: `fixed`, top 0, full width, z-index 200
- Height: ~56px (padding 18px vertical)
- Fundo: transparente → `rgba(13,15,20,0.88)` + `backdrop-filter: blur(16px)` ao scrollar > 56px
- Borda inferior: `1px solid rgba(255,255,255,0.07)` ao scrollar
- Esquerda: avatar circular 28px (foto da Laila, `object-fit: cover`, `object-position: top center`) + "Laila Andrade" 14px/500
- Direita: links "Cases" / "Sobre" + botão pill "Entrar em contato" (cor `rgba(48,79,254,0.1)`, borda `rgba(110,149,255,0.2)`, texto `#6E95FF`)

#### Hero
- Padding: 148px top / 88px bottom
- Border-bottom: `1px solid #1a1f2a`
- Título: DM Serif Display, clamp(28px–46px), max-width 680px, lh 1.14, ls -0.02em
- Subtítulo: 15px, color `#b8bdd4`, max-width none, lh 1.7
- CTA "Entrar em contato →": border `1px solid rgba(255,255,255,0.18)`, padding 11px 22px, border-radius 100px
- Animações de entrada: `opacity 0 → 1`, `translateY(22px → 0)`, delays 0.1s / 0.28s / 0.46s

#### Progress Bar
- `position: fixed`, top 0, height 2px, z-index 300
- Gradiente: `linear-gradient(90deg, #304FFE 0%, #6E95FF 100%)`
- Largura proporcional ao scroll da página

#### Cases Selecionados
- Heading: 24px / 600, underline animado 32px (`#304FFE`) ao entrar no viewport
- Grid: `grid-template-columns: 1fr 1fr`, gap 16px
- Cards: `background #1e2330`, border `1px solid #252b3d`, border-radius 14px
- Hover: `translateY(-4px)`, border `rgba(110,149,255,0.35)`, shadow `0 20px 48px rgba(48,79,254,0.12)`
- Imagem: `aspect-ratio: 16/10`, `object-fit: cover`, `object-position: top`
- Hover imagem: `transform: scale(1.02)`, transition 0.5s
- Texto descrição: 15px, color `#b8bdd4`
- Arrow circle: 28px, border `rgba(110,149,255,0.2)`, hover background `rgba(48,79,254,0.15)`
- 4 cases: iPLP / IES / Card de Oferta / Paystation

#### Competências + Experiência
- Grid externo unificado: `grid-template-columns: 1fr 1fr`, column-gap 72px
- Headings nas colunas + 5 rows intercaladas (skill / exp por linha)
- Cada row: `border-bottom: 1px solid #1a1f2a`, padding 20px 0
- Skill icon: 36×36px, border-radius 8px, background `rgba(48,79,254,0.1)`, ícone SVG stroke `#6E95FF`
- Exp logo: 40×40px, border-radius 10px, imagem real com `object-fit: cover`
- Animação: skills deslizam da esquerda (`translateX(-24px)`), exp da direita (`translateX(24px)`)

#### Sobre Mim
- Grid: `grid-template-columns: 380px 1fr`, gap 44px
- Foto: 380px col, `height: 100%`, `object-fit: cover`, `object-position: top center`, border-radius 12px
- Texto: `align-self: start`, 4 parágrafos + nome + link LinkedIn
- Animação: foto da esquerda, texto da direita

#### Questionamentos (FAQ)
- Grid 2×2: `background: #1a1f2a` (gap), `border: 1px solid #1a1f2a`, border-radius 14px, overflow hidden
- Cada item: `background #1e2330`, hover `#212840`
- Toggle: `+` rotaciona 45° (`.open`) com cubic-bezier, fundo `rgba(48,79,254,0.15)`
- Resposta: `max-height: 0 → 240px`, `opacity: 0 → 1`, transition 0.4s
- 4 perguntas / respostas (ver HTML para copy exato)

#### CTA / Disponível
- Grid: `grid-template-columns: 1fr auto`, gap 64px
- Título: DM Serif Display, clamp(24px–34px)
- Botão email: border `1px solid rgba(255,255,255,0.14)`, padding 15px 28px, border-radius 100px

#### Footer
- Border-top `1px solid #1a1f2a`, padding 24px
- Esquerda: "© 2026 Laila Andrade", 13px, color `#6b7280`
- Direita: link LinkedIn, 13px, color `#b8bdd4`

---

### 2. Case Pages (`iplp.html`, `ies.html`, `card.html`, `paystation.html`)

Todas as 4 páginas seguem a mesma estrutura e design system.

#### Nav de Case
- `position: sticky`, top 0, background `rgba(13,15,20,0.92)` + blur(16px)
- Esquerda: `← Laila Andrade` (link para `index.html`)
- Direita: links para os outros 3 cases
- Max-width: 1400px

#### Cover (Capa)
- Background: `#13171f`, padding: 100px top / 72px bottom
- Radial gradient decorativo no canto superior direito
- Tags: `font-size 11px`, uppercase, `background rgba(48,79,254,0.12)`, border `rgba(110,149,255,0.2)`, border-radius 100px
- Título: DM Serif Display, clamp(38px–62px)
- Subtítulo: 17px, color `#b8bdd4`
- Author avatar: 32×32px circular (foto da Laila), nome + role

#### Seções de Conteúdo
- Padding: 120px vertical, `border-bottom: 1px solid #1a1f2a`
- Section-label: 11px uppercase, `#6E95FF`, com linha decorativa `::after`
- Section-title: DM Serif Display, clamp(24px–36px)
- Section-body: 17px, color `#b8bdd4`, max-width 960px

#### Componentes dos Cases
- `two-col`: `grid-template-columns: 1fr 1fr`, gap 64px
- `decision-box`: `background rgba(48,79,254,0.06)`, border `rgba(48,79,254,0.2)`, border-radius 16px
- `steps`: numbered list com linha conectora, circles 48×48px
- `metrics-grid`: `repeat(4,1fr)`, metric-cards com top border 2px
- `image-full`: border-radius 16px, border `1px solid #1e2438`

#### Footer de Navegação Entre Cases
- Background `#13171f`, padding 56px/64px
- Label "Outros cases" uppercase `#6E95FF`
- Grid 3 colunas com cards dos outros cases
- Link "← Voltar para o portfólio"

---

## Animações

### Scroll Reveal
```css
/* Classes disponíveis */
.reveal       { opacity:0; transform:translateY(28px); }
.reveal-left  { opacity:0; transform:translateX(-24px); }
.reveal-right { opacity:0; transform:translateX(24px); }
.reveal-scale { opacity:0; transform:scale(0.97); }
/* Ao entrar no viewport: adiciona classe .in */
/* Delays: .d1=0.08s .d2=0.16s .d3=0.24s .d4=0.32s .d5=0.40s */
```

IntersectionObserver com `threshold: 0.08`, `rootMargin: '0px 0px -32px 0px'`.

### Section Headings
`.s-heading::after` anima `width: 0 → 32px` quando `.in` é adicionado.

### Hero (page load)
`@keyframes fadeUp` com delays escalonados 0.1s / 0.28s / 0.46s.

---

## Interações

| Elemento | Interação | Detalhe |
|---|---|---|
| Nav | Scroll > 56px | Background blur + border bottom aparecem |
| Progress bar | Scroll | Width proporcional ao scroll total da página |
| Case cards | Hover | translateY(-4px), glow azul, scale da imagem |
| FAQ items | Click | Accordion suave, toggle + rotaciona 45° |
| Exp logos | - | object-fit: cover, preenche container sem branco |

---

## Assets Usados

| Arquivo | Uso |
|---|---|
| `assets/foto-sobre-mim.png` | Foto Laila — About, nav avatar home, cover avatar cases, favicon |
| `assets/capa-case-iplp.png` | Thumbnail card iPLP na home |
| `assets/capa-case-iespage.png` | Thumbnail card IES na home |
| `assets/capa-case-card.png` | Thumbnail card Card de Oferta na home |
| `assets/capa-case-paystation.png` | Thumbnail card Paystation na home |
| `assets/logo-qeevo.png` | Logo Qeevo — seção Experiência |
| `assets/logo-cuponomia.png` | Logo Cuponomia — seção Experiência |
| `assets/logo-quero.png` | Logo Quero Educação — seção Experiência |
| `assets/logo-studio7.png` | Logo Studio 7 — seção Experiência |
| `assets/logo-essence.png` | Logo Essence — seção Experiência |

Imagens dos cases (dentro dos case studies) são carregadas de `framerusercontent.com`.

---

## Deploy

O projeto é **HTML estático puro** — nenhuma build step necessária.

### Opção 1 — Direto (recomendado)
Arraste a pasta para **Vercel**, **Netlify** ou **GitHub Pages**. Funciona imediatamente.

### Opção 2 — Migrar para Next.js
Cada `.html` vira uma page (`/`, `/iplp`, `/ies`, `/card`, `/paystation`).
CSS pode ser convertido para CSS Modules ou Tailwind.
Componentes compartilhados: `<Nav>`, `<CaseFooter>`, `<ScrollReveal>`.
