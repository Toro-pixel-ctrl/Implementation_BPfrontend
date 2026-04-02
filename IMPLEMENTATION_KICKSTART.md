# IMPLEMENTATION_KICKSTART.md
## BlackPoint — Systems & Intelligence Firm Landing Page

---

## 1. ARCHITECTURE & STACK DECISIONS

### Stack
- **Single HTML file** (index.html) — no bundler, no build process
- **Vanilla JavaScript** — no frameworks
- **Tailwind CSS v3** — CDN (JIT mode)
- **Google Fonts** — Geist Sans, Geist Mono via CDN with font-display: swap
- **Canvas API** — particle field (vanilla rAF loop)
- **No backend** — contact form captures data locally (localStorage + console)
- **Deployment** — Vercel → blackpointgroup.eu DNS

### Key Constraints
- All CSS and JS inline in single HTML file
- No external build tools or Node processes
- Mobile particles disabled (performance)
- No external API calls for form submission
- prefers-reduced-motion: instant, no transitions

### File Structure (Post-Implementation)
```
/project
  ├── index.html (complete, single file)
  ├── .env (existing, untouched)
  ├── package.json (can remain for future tooling)
  └── IMPLEMENTATION_KICKSTART.md (this file)
```

---

## 2. DESIGN TOKENS

### Color Palette (60/30/10)
```css
/* Primary Dark Backgrounds */
--color-bg-primary: #050505;
--color-bg-secondary: #0A0A0A;

/* Text & Content */
--color-text-primary: #FFFFFF;
--color-text-muted: #606060;

/* Accent & Interactions */
--color-accent-gold: #B8A020;

/* Borders & Overlays */
--color-border-subtle: rgba(255, 255, 255, 0.07);
--color-overlay-dark: rgba(5, 5, 5, 0.92);
```

### Typography
```
FONT FAMILIES (Google Fonts CDN):
  - Geist Sans (weights: 300, 400, 500, 800)
  - Geist Mono (weight: 500)

SCALE & HIERARCHY:
  Hero H1:
    - Font: Geist Sans 800
    - Size: clamp(56px, 8vw, 92px)
    - Line-height: 0.92
    - Letter-spacing: -0.03em

  Section H2:
    - Font: Geist Sans 800
    - Size: clamp(36px, 5vw, 68px)
    - Line-height: 1.2

  Body:
    - Font: Geist Sans 300
    - Size: 18px
    - Line-height: 1.8

  Label/Mono:
    - Font: Geist Mono 500
    - Size: 11px
    - Letter-spacing: 0.18em
    - Text-transform: uppercase

  Metric Numbers:
    - Font: Geist Mono 500
    - Size: 56px
    - Color: #FFFFFF
```

### Spacing System (8px base)
```
8px, 12px, 16px, 20px, 24px, 32px, 40px, 48px, 56px, 64px, 80px, 96px
```

---

## 3. SECTION SPECIFICATIONS WITH COPY

### HEADER (Fixed, Sticky >80px scroll)
**Height:** 64px
**Elements:**
- Left: Wordmark "BLACKPOINT" (Geist Sans 500, 13px, letter-spacing wide)
- Right: Ghost pill "Solicitar Mapeo" → smooth scroll to #contact
- Scroll State: bg rgba(5,5,5,0.92) + backdrop-filter: blur(20px)

**Mobile:**
- Hamburger icon (three-line menu)
- Click reveals fullscreen overlay with single CTA "Solicitar Mapeo Estructurado"

---

### SECTION 1: HERO
**Full Viewport Height**
**Background:** Particle canvas (100 white dashes/dots, slow drift, wraps edges) + dark gradient overlay
**Mobile:** Solid dark bg, particles disabled

**Copy:**
```
H1 (centered, max 2 lines):
"Instalamos inteligencia
donde el negocio pierde control."

Primary CTA: "Solicitar Mapeo Estructurado" → #contact
Ghost CTA: "Cómo operamos" → #proceso

Scroll Indicator: Chevron down + "Desplazar" (center bottom)
```

**Visual:** Particle field behind, typography centered, radial gradient fade at top/bottom

---

### SECTION 2: EL PROBLEMA
**Layout:** Editorial, left-aligned, max-width 820px
**Padding:** 96px vertical, 40px horizontal (desktop)

**Copy:**
```
H2 (3 lines, enormous):
"Datos fragmentados.
Decisiones lentas.
Ejecución inconsistente."

Body paragraph:
"Las operaciones complejas requieren visibilidad integrada.
Sin esto, cada sistema funciona en silos.
El resultado: retrasos costosos, oportunidades perdidas,
y equipos frustrados ejecutando tácticas desconectadas."

Cards (3x, dark surfaces, no glass):
  1. Icon + "Datos fragmentados"
     → "Tus sistemas no hablan entre sí.
        La verdad vive en múltiples plataformas."

  2. Icon + "Decisiones lentas"
     → "Recopilación manual es mortal.
        Los análisis llegan días después de los eventos."

  3. Icon + "Ejecución inconsistente"
     → "Cada equipo improvisa su propio proceso.
        Nada escala. Nada mejora."
```

**Cards Animation:** Stagger 120ms per child on scroll entry

---

### SECTION 3: CÓMO OPERAMOS (id="proceso")
**Layout:** 4 horizontal steps (desktop) / vertical stack (mobile, breakpoint 768px)
**Background:** Subtle gradient, darker than hero

**Copy:**
```
H2: "Diagnóstico primero. Integración después."

Steps (numbered, gold accent):
  01 MAPEO
     → "Cartografiamos tu arquitectura operativa.
        Identificamos puntos de fractura."

  02 ESTRUCTURA
     → "Definimos flujos de datos y lógica de negocio.
        Reducimos ruido, exponemos verdad."

  03 INTEGRACIÓN
     → "Conectamos sistemas críticos en fases.
        Cada integración es una victoria visible."

  04 CALIBRACIÓN
     → "Ajustamos en producción.
        Medimos, aprendemos, escalamos."

Primary CTA (centered below): "Comenzar Mapeo Estructurado" → #contact
```

**Visual:** Each step has large gold number on left, title white, body muted. Horizontal line connects steps on desktop; vertical on mobile.

---

### SECTION 4: QUÉ INSTALAMOS
**Layout:** Split 40% text / 60% visual (cards offset/staggered)
**Background:** Darkest shade (#050505)

**Copy:**
```
H2: "Lo que construimos contigo"

Left Column (40%, max-width 420px):
Body text:
"No instalamos herramientas. Instalamos sistemas.
Cada componente que agregamos resuelve un punto de fractura específico.
Nada es genérico. Todo es medible."

CTA: "Ver caso de estudio" → (future link or scroll to metrics)

Right Column (60%, cards staggered):
  CARD 1: INTERACCIÓN
    Tag: "INTERACCIÓN" (gold mono)
    Title: "Visibilidad en Tiempo Real"
    Outcomes:
      • Estado operativo visible en un dashboard
      • Alertas antes de que fallen los procesos
      • Acciones contextuales para cada anomalía

  CARD 2: OUTREACH
    Tag: "OUTREACH" (gold mono)
    Title: "Automatización de Contacto"
    Outcomes:
      • Sequencias sin intervención manual
      • Datos frescos directamente en tu CRM
      • Sincronización bidireccional de contexto

  CARD 3: CONTENIDO
    Tag: "CONTENIDO" (gold mono)
    Title: "Relevancia Distribuida"
    Outcomes:
      • Contenido adaptado a ciclo de venta
      • Publicación en canales correctos, momento correcto
      • Rendimiento medido por impacto, no por volumen
```

**Visual:** Cards have dark surfaces, gold accent borders/tags. Staggered: first card at top, second middle-right, third bottom-left (or similar offset pattern). Entry animations on scroll.

---

### SECTION 5: PARA QUIÉN
**Layout:** Two-column comparison, no card wrappers
**Background:** Subtle pattern or gradient

**Copy:**
```
Column 1: ENCAJA CON BLACKPOINT
  ✓ Operaciones B2B complejas (>10M en revenue anual)
  ✓ Múltiples sistemas legacy + nuevos en paralelo
  ✓ Decisiones que requieren datos integrados
  ✓ Equipos distribuidos entre sales, ops, producto
  ✓ Crecimiento sostenido es prioridad, no urgencia tctica

Column 2: NO ES PARA
  – Startups en fase MVP (aún sin datos operativos)
  – Organizaciones buscando "herramienta barata rápida"
  – Equipos sin dueño claro de la integración
  – Empresas que no miden el impacto de sus decisiones
```

**Visual:** Row separators between items. Gold checks (✓) for positive. Muted dashes (–) for negative. No background cards, clean typography contrast.

---

### SECTION 6: MÉTRICAS
**Layout:** Narwh-style comparison table + 2x2 metric grid below

**Copy:**
```
COMPARISON TABLE (3 columns):
Header: MÉTRICA | OPERACIÓN MANUAL | CON BLACKPOINT

Row 1: Tiempo de integración de datos
  Manual: 2-4 semanas por fuente
  BlackPoint: 5-7 días ✓

Row 2: Latencia de visibilidad
  Manual: 24-48 horas mínimo
  BlackPoint: <15 minutos ✓

Row 3: Errores de sincronización anual
  Manual: 300-800 incidencias
  BlackPoint: <5 incidencias ✓

Row 4: Costo operativo por integración
  Manual: $40-80K (personas + herramientas)
  BlackPoint: $12-18K (una sola vez) ✓

Row 5: Escalabilidad a nuevos datos
  Manual: Requiere nueva asignación de personas
  BlackPoint: Agregable sin rediseño ✓

METRIC CALLOUTS (2x2 grid below table):
  Top-left: 86% — Reducción en tiempo de decisión
  Top-right: 24/7 — Visibilidad operativa continua
  Bottom-left: 94% — Exactitud de sincronización
  Bottom-right: 3-6mo — Payback típico
```

**Visual:** Table has BlackPoint column highlighted with gold accents and checkmarks. Numbers in grid are 56px Geist Mono white, labels below in 11px gold mono.

---

### SECTION 7: CONTACTO (id="contact")
**Layout:** 3-step qualification flow → form reveal

**Copy:**
```
STEP 1: "¿Cuál es tu sector operativo principal?"
  Pill options:
    • Servicios financieros
    • Manufactura & supply chain
    • SaaS B2B
    • Otro (especificar)

STEP 2: "¿Dónde está el mayor cuello de botella?"
  Pill options:
    • Toma de decisiones lenta
    • Duplicación de datos
    • Pérdida de contexto entre equipos
    • Falta de visibilidad operativa

STEP 3: "¿Qué nivel de automatización tienes hoy?"
  Pill options:
    • Casi todo manual
    • Herramientas sin integración
    • Algunos flujos automatizados
    • Arquitectura establecida, necesita optimización

[After Step 3, form fades in]

FORM:
  Name: "Nombre completo"
  Company: "Empresa"
  Email: "Correo electrónico"
  Message: "Describa su situación operativa en 2-3 líneas"

  Submit button: "Enviar Solicitud"

  Confirmation message (post-submit):
    "Recibido. Nos pondremos en contacto en 24 horas."
```

**Visual:** Progress dots (3) at top. Each step is a card with pill options. Form appears with fade-in after step 3. Form data stored in localStorage + logged to console (no backend).

---

### FOOTER
**Height:** 80px
**Layout:** Two columns, centered content

**Left Column:**
```
Wordmark: "BLACKPOINT"
Tagline: "Systems & Intelligence Firm"
```

**Right Column:**
```
blackpointgroup.eu
© 2025 BlackPoint. All rights reserved.
```

**Fixed Element:**
- Back-to-top button (bottom-right, always visible)
- Smooth scroll to top on click

---

## 4. COMPONENT LIST

### Header
- Sticky header with fade-in background >80px scroll
- Wordmark (left)
- Primary CTA pill (right, desktop)
- Hamburger menu (mobile, opens fullscreen overlay)

### Hero Section
- Particle canvas (100 particles, drift animation, disabled mobile)
- Centered H1 headline (2 lines)
- Two CTA pills (primary + ghost)
- Scroll indicator (bottom center)

### Problem Section
- Left-aligned H2 (3 lines)
- Body paragraph (muted)
- 3x problem cards (icon + title + body)
- Card stagger animation on scroll entry

### Process Section
- H2 headline
- 4 steps: horizontal desktop / vertical mobile
- Step number (gold), title (white), body (muted)
- Horizontal/vertical connector line
- Centered primary CTA below

### What We Build Section
- Split layout: 40% text / 60% cards
- Left: body text + CTA
- Right: 3 offset cards (INTERACCIÓN, OUTREACH, CONTENIDO)
- Gold mono tags, white titles, muted outcomes

### Fit / Not Fit Section
- Two-column layout
- Gold checks for "fits"
- Muted dashes for "doesn't fit"
- Row separators between items

### Metrics Section
- 3-column comparison table (MÉTRICA | MANUAL | BLACKPOINT)
- 5 data rows with gold checkmarks in BlackPoint column
- 2x2 metric callout grid below (56px numbers, 11px labels)

### Contact Section
- 3-step qualification flow
- Progress dots
- Pill option selectors
- Form (4 fields + submit)
- Confirmation message

### Footer
- Wordmark + tagline (left)
- Domain + copyright (right)
- Fixed back-to-top button (bottom-right)

---

## 5. ANIMATION CATALOG

### Global
- `prefers-reduced-motion: all instant, no transitions`

### Particle Canvas
- Continuous rAF loop (disabled mobile)
- ~100 particles with random drift velocity
- Wraps viewport edges (loop back)
- No mouse interaction
- Speed: ~0.5-1.5px per frame

### Scroll Entry (0.7s ease-out)
- Initial: translateY(32px), opacity 0
- Final: translateY(0), opacity 1
- Applied to: cards, metric callouts, section blocks

### Card Stagger
- Base animation: scroll entry (0.7s ease-out)
- Delay per child: 120ms increments
- Applied to: problem cards, what-we-build cards, metric callouts

### Metric Count-Up
- Duration: 1.4s on viewport enter
- From: 0 to final number
- Font: Geist Mono 56px (white)
- Applied to: 2x2 metric grid numbers

### Scroll Header Fade-In
- Trigger: >80px scroll
- Background: fade from transparent to rgba(5,5,5,0.92)
- Backdrop filter: blur(20px)
- Duration: 0.3s linear

### Form Step Transitions
- Step fade-in: 0.4s ease-out
- Step fade-out: 0.3s ease-in
- Form reveal (after step 3): 0.6s ease-out

### Button Hover/Focus
- Text color fade to gold (0.2s)
- Border highlight (0.2s)

---

## 6. SEO CONFIGURATION

### Meta Tags (All Required)
```html
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <!-- SEO -->
  <title>BlackPoint — Systems & Intelligence Firm</title>
  <meta name="description" content="Firma de integración de inteligencia para empresas B2B complejas. Diagnóstico estructural, integración por fases, apalancamiento medible.">
  <meta name="keywords" content="integración de sistemas, inteligencia operativa, B2B, automatización">

  <!-- Open Graph -->
  <meta property="og:type" content="website">
  <meta property="og:title" content="BlackPoint — Systems & Intelligence Firm">
  <meta property="og:description" content="Firma de integración de inteligencia para empresas B2B complejas. Diagnóstico estructural, integración por fases, apalancamiento medible.">
  <meta property="og:url" content="https://blackpointgroup.eu">
  <meta property="og:site_name" content="BlackPoint">

  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary">
  <meta name="twitter:title" content="BlackPoint — Systems & Intelligence Firm">
  <meta name="twitter:description" content="Firma de integración de inteligencia para empresas B2B complejas. Diagnóstico estructural, integración por fases, apalancamiento medible.">

  <!-- Favicon -->
  <link rel="icon" type="image/svg+xml" href="/favicon.svg">

  <!-- Fonts (Google CDN with font-display: swap) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Geist:wght@300;400;500;800&family=Geist+Mono:wght@500&display=swap" rel="stylesheet">
</head>
```

### Structured Data
- Schema.org Organization markup (minimal, no pricing/testimonials)
- LocalBusiness type with contact info

### Performance Hints
- `preconnect` to Google Fonts
- `dns-prefetch` for external resources (if any added later)

---

## 7. CONSTRAINTS & NON-NEGOTIABLE RULES

### Brand
- NEVER mention tool names (no "Zapier", "HubSpot", "API", etc.)
- NEVER use "AI agency" language or hype
- NEVER include pricing, real testimonials, competitor names, or urgency tactics
- Voice: Direct, zero hype, enterprise. Outcomes-first.

### Technical
- Single HTML file only (no external CSS/JS files)
- Vanilla JS, no frameworks
- Tailwind CDN v3 (JIT mode)
- No backend form submission (localStorage + console logging only)
- Particles disabled on mobile (breakpoint <768px)
- All fonts via Google CDN with swap strategy

### Visual
- No purple, indigo, or violet hues
- Gold (#B8A020) used ONLY for CTAs, labels, and accents (never backgrounds)
- Sufficient contrast: gold on dark tested for WCAG AA
- Responsive: clamp() for typography, mobile-first media queries
- Radical dark space: sections breathe, generous padding/margins

### Animation
- prefers-reduced-motion: all instant, no transitions
- Particle canvas: rAF loop with performance throttle
- Scroll animations: 0.7s ease-out (translateY + opacity)
- No auto-play videos, no parallax depth (performance)

### Deployment
- Single index.html in project root
- Remove Vite template files (main.js, counter.js, style.css, javascript.svg)
- Keep .env, .gitignore, package.json as-is (no modifications needed)
- Push to GitHub
- Deploy to Vercel (connected to GitHub repo)
- DNS: blackpointgroup.eu points to Vercel deployment

---

## 8. IMPLEMENTATION NOTES

### File Approach
The entire landing page will be a single `index.html` with:
1. Inline `<style>` block (Tailwind CDN + custom CSS for animations)
2. Inline `<script>` block (particle canvas, scroll animations, form handling)
3. All semantic HTML5 structure
4. No external dependencies except Google Fonts & Tailwind CDN

### Particle Canvas
- Create `<canvas id="particles">` in hero
- rAF loop for animation
- ~100 particles with random velocity
- Wraps viewport edges (particles reset position on edge cross)
- Disabled on mobile via CSS display: none + JS feature detection

### Form Data Handling
- localStorage key: `blackpoint_contact_inquiries` (array of objects)
- Each submit stores: { name, company, email, message, timestamp, sector, bottleneck, automation }
- Console log for QA/testing
- Success message clears form and shows confirmation modal

### Responsive Breakpoints
- Mobile: <768px (hamburger, full-width, particles off, vertical steps)
- Tablet: 768px-1024px (adjusted spacing, single-column for metrics table)
- Desktop: >1024px (full layout, horizontal steps, particle canvas)

### Performance Optimization
- Particle count: 0 on mobile, 100 on desktop
- Intersection Observer for scroll animations (lazy trigger)
- Font preload for Geist Sans 800 (critical hero text)
- Minimal repaints: use transform/opacity for animations (not top/left)

### Accessibility
- Semantic HTML: `<header>`, `<nav>`, `<section>`, `<main>`, `<footer>`
- ARIA labels for particle canvas, hamburger, back-to-top
- Keyboard navigation: Tab through CTAs, form fields, pill options
- Color contrast tested: gold on dark meets WCAG AA
- Focus states visible: outline or background highlight

---

## 9. DEPLOYMENT TO VERCEL & DOMAIN SETUP

### GitHub Push
```bash
git add .
git commit -m "Initial BlackPoint landing page"
git push origin main
```

### Vercel Deployment
1. Connect GitHub repo to Vercel (if not already)
2. Vercel detects single index.html, auto-deploys
3. Production deployment at `blackpoint.vercel.app` (or custom domain)
4. Environment: Production only (no staging needed)

### Domain Configuration (blackpointgroup.eu)
**DNS Setup (at domain registrar):**
- CNAME record: `blackpointgroup.eu` → `cname.vercel.sh`
- Or use Vercel's nameserver delegation for full control

**Vercel Dashboard:**
1. Go to Project Settings → Domains
2. Add `blackpointgroup.eu`
3. Follow Vercel's domain verification steps
4. Auto-provision SSL via Vercel (free)

**DNS Propagation:** 24-48 hours typical

### Environment Variables
- No secrets needed (form is client-side only)
- .env file stays as-is (not used by landing page)

---

## 10. SUCCESS CRITERIA

### Performance
- [ ] Page loads in <3s on 4G (LCP <2.5s)
- [ ] No CLS issues (layout shifts <0.1)
- [ ] Particle canvas 60fps on desktop
- [ ] Animations smooth on mobile (no janky scrolls)

### Visual
- [ ] All text readable on all backgrounds (WCAG AA)
- [ ] Responsive across all breakpoints
- [ ] Gold accents pop without overpower
- [ ] Typography hierarchy clear at all sizes

### Functionality
- [ ] All CTAs scroll smoothly to target sections
- [ ] Hamburger menu opens/closes on mobile
- [ ] Contact form qualifies through 3 steps
- [ ] Form submit saves to localStorage + logs
- [ ] Back-to-top button visible, functional
- [ ] Particles animate on desktop, disabled mobile
- [ ] Scroll animations trigger at correct viewport %

### SEO & Brand
- [ ] Meta tags populate correctly
- [ ] OG cards show in social shares
- [ ] No tool names or "AI agency" language in copy
- [ ] Brand voice consistent: direct, enterprise, outcomes-first
- [ ] Mobile menu shows single primary CTA only

### Deployment
- [ ] Repository pushed to GitHub
- [ ] Vercel deployment live
- [ ] blackpointgroup.eu resolves correctly
- [ ] SSL certificate valid
- [ ] Vite template files removed
- [ ] index.html is single source of truth

---

**END IMPLEMENTATION_KICKSTART.md**

*This document is the complete specification for building the BlackPoint landing page. All sections are defined, copy is provided, and technical decisions are documented. Ready for development.*
