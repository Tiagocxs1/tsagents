---
name: cinematic-websites
description: Build Awwwards-quality cinematic websites with React 19, GSAP (ScrollTrigger), and Tailwind CSS 4. Covers scroll-driven narratives, staggered reveals, smooth transitions, and premium motion design patterns.
allowed-tools: [gsap-master, animotion-mcp, threejs-devtools]
---

# Cinematic Websites — Awwwards-Level Motion Design

Build premium, award-worthy websites using React 19, GSAP, and Tailwind CSS 4.

## Core Principles

1. **Scroll-driven narrative** — every section transitions as the user scrolls, creating a story arc
2. **Staggered reveals** — elements enter in sequence (translateY 20px -> 0, opacity 0 -> 1, stagger 0.08s)
3. **Pinned sections** — key content pins while background animations play
4. **Smooth scroll** — use Lenis or locomotive-scroll for fluid parallax
5. **Performance first** — animate only `transform` and `opacity`, use `will-change` sparingly

## Tech Stack

| Layer | Choice | Purpose |
|-------|--------|---------|
| Framework | React 19 | Component model, concurrent features |
| Build | Vite | Fast HMR, optimal production builds |
| Animation | GSAP + ScrollTrigger | Timeline control, scroll-linked motion |
| Smooth Scroll | Lenis (react-lenis) | Fluid parallax, smooth wheel events |
| Styling | Tailwind CSS 4 | Utility-first, `@theme` for design tokens |
| 3D (optional) | Three.js via @react-three/fiber | Immersive WebGL scenes |

## Project Setup

```bash
npm create vite@latest . -- --template react
npm install gsap @gsap/react lenis react-lenis
npm install tailwindcss @tailwindcss/vite
```

Configure GSAP + ScrollPlugin + Lenis:

```js
// src/main.jsx
import { ReactLenis } from 'lenis/react'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { useGSAP } from '@gsap/react'

gsap.registerPlugin(ScrollTrigger, useGSAP)

createRoot(document.getElementById('root')).render(
  <ReactLenis root options={{ lerp: 0.1, duration: 1.2 }}>
    <App />
  </ReactLenis>
)
```

## GSAP Patterns

### 1. Staggered Fade-Up (Section Enter)

```jsx
// Each child fades up with stagger
useGSAP(() => {
  gsap.from('.reveal-item', {
    y: 40, opacity: 0, duration: 0.9,
    stagger: 0.1, ease: 'power3.out',
    scrollTrigger: { trigger: '.section', start: 'top 80%' }
  })
})
```

### 2. Pin Section with Background Animation

```jsx
useGSAP(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: '.pin-section',
      pin: true,
      start: 'top top',
      end: '+=200%',
      scrub: 1
    }
  })
  tl.to('.bg-layer', { scale: 1.4, opacity: 0.3 })
  tl.from('.hero-text', { y: 100, opacity: 0 }, 0)
  tl.from('.hero-cta', { y: 60, opacity: 0 }, 0.3)
})
```

### 3. Parallax on Scroll

```jsx
useGSAP(() => {
  gsap.to('.parallax-bg', {
    yPercent: -30, ease: 'none',
    scrollTrigger: {
      trigger: '.parallax-section',
      start: 'top bottom',
      end: 'bottom top',
      scrub: true
    }
  })
})
```

### 4. Horizontal Scroll Section

```jsx
const sections = gsap.utils.toArray('.panel')
useGSAP(() => {
  gsap.to(sections, {
    xPercent: -100 * (sections.length - 1),
    ease: 'none',
    scrollTrigger: {
      trigger: '.horizontal-section',
      pin: true,
      scrub: 1,
      end: () => `+=${document.querySelector('.horizontal-track').offsetWidth}`
    }
  })
})
```

### 5. Text Split Reveal

```jsx
// Split text into word spans, then stagger each word
const textRef = useRef(null)
useGSAP(() => {
  const chars = textRef.current.textContent.split('')
  textRef.current.innerHTML = chars.map(c =>
    `<span class="char" style="display:inline-block">${c === ' ' ? '&nbsp;' : c}</span>`
  ).join('')
  gsap.from('.char', {
    y: 80, opacity: 0, rotateX: -90, duration: 0.6,
    stagger: 0.02, ease: 'back.out(1.7)',
    scrollTrigger: { trigger: textRef.current, start: 'top 85%' }
  })
}, { scope: textRef })
```

### 6. Animated Cursor

```jsx
useGSAP(() => {
  const cursor = document.createElement('div')
  cursor.className = 'custom-cursor'
  document.body.appendChild(cursor)
  gsap.set(cursor, { xPercent: -50, yPercent: -50 })

  const xTo = gsap.quickTo(cursor, 'x', { duration: 0.6, ease: 'power3.out' })
  const yTo = gsap.quickTo(cursor, 'y', { duration: 0.6, ease: 'power3.out' })

  window.addEventListener('mousemove', e => { xTo(e.clientX); yTo(e.clientY) })
})
```

### 7. Preloader / Loader Sequence

```jsx
useGSAP(() => {
  const tl = gsap.timeline()
  tl.to('.loader-bar', { scaleX: 1, duration: 2, ease: 'power4.inOut' })
  tl.to('.loader', { opacity: 0, duration: 0.5 })
  tl.call(() => document.querySelector('.loader')?.remove())
})
```

## Tailwind CSS 4 Theme

```css
/* app.css */
@import "tailwindcss";

@theme {
  --color-surface: #0a0a0a;
  --color-surface-secondary: #1a1a1a;
  --color-primary: #ffffff;
  --color-accent: #6366f1;
  --font-display: "Instrument Serif", serif;
  --font-body: "Inter", sans-serif;
}
```

## Responsive Breakpoints

Base mobile-first then layer up:
- `sm` (640px): adjust grid cols, reduce font sizes
- `md` (768px): tablet layouts, 2-col grids
- `lg` (1024px): desktop, bento grids, horizontal scroll
- `xl` (1280px): max content width

## Decision Matrix

| Goal | Pattern | GSAP Tool |
|------|---------|-----------|
| Section enter | Staggered fade-up | `gsap.from()`, `stagger` |
| Long scroll story | Pin + timeline | `ScrollTrigger({ pin: true })` + timeline |
| Visual depth | Parallax | `gsap.to()` with `yPercent`, `scrub` |
| Gallery / portfolio | Horizontal scroll | `xPercent: -100 * (N-1)` |
| Typographic impact | Text split reveal | Per-char stagger |
| Ambient feedback | Animated cursor | `gsap.quickTo` |
| First impression | Preloader | Timeline with loader bar |

## Quality Checklist

- [ ] Animations use `transform` and `opacity` only (GPU-composited)
- [ ] `prefers-reduced-motion: reduce` disables all animations
- [ ] ScrollTrigger matches are cleaned up on unmount
- [ ] No layout shift from animated elements (use `opacity: 0` initial state)
- [ ] Lenis `.stop()` during ScrollTrigger pinning active
- [ ] Mobile: animations are shorter, stagger reduced
- [ ] GSAP quick functions used for performance (`gsap.quickTo`, `gsap.utils`)
- [ ] All sections have proper `will-change: transform` on animated parents
