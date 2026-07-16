# Lenis — Smooth Scroll Library

Lenis is a lightweight (<4kb), dependency-free smooth scroll library by [darkroom.engineering](https://darkroom.engineering). Use when implementing smooth scrolling, parallax, scroll-linked animations, or integrating with GSAP ScrollTrigger/R3F.

## Installation

```bash
npm i lenis
# React adapter
npm i lenis
```

## Quick Setup

```js
import Lenis from 'lenis'
import 'lenis/dist/lenis.css'

const lenis = new Lenis({ autoRaf: true })
```

## GSAP ScrollTrigger Integration

```js
import Lenis from 'lenis'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const lenis = new Lenis()
lenis.on('scroll', ScrollTrigger.update)
gsap.ticker.add((time) => lenis.raf(time * 1000))
gsap.ticker.lagSmoothing(0)
```

## React

```jsx
import { ReactLenis } from 'lenis/react'
import 'lenis/dist/lenis.css'

export default function Layout({ children }) {
  return (
    <ReactLenis root options={{ lerp: 0.1, duration: 1.2 }}>
      {children}
    </ReactLenis>
  )
}
```

## Key Settings

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `lerp` | number | 0.1 | Linear interpolation intensity (0-1) |
| `duration` | number | 1.2 | Scroll animation duration (seconds) |
| `easing` | function | custom | Easing function (ignored if lerp set) |
| `orientation` | string | `vertical` | `vertical`, `horizontal`, or `both` |
| `smoothWheel` | boolean | true | Smooth mouse wheel scroll |
| `syncTouch` | boolean | false | Sync touch inertia (unstable iOS<16) |
| `wheelMultiplier` | number | 1 | Mouse wheel speed multiplier |
| `touchMultiplier` | number | 1 | Touch speed multiplier |
| `infinite` | boolean | false | Infinite scroll |
| `autoRaf` | boolean | false | Auto requestAnimationFrame loop |
| `anchors` | boolean/object | false | Smooth anchor links |

## Methods

| Method | Description |
|--------|-------------|
| `scrollTo(target, options)` | Scroll to target (number, selector, element) |
| `on(id, fn)` | Listen to events (`scroll`, `virtual-scroll`) |
| `start()` / `stop()` | Resume/pause scroll |
| `destroy()` | Remove instance and events |
| `raf(time)` | Call every frame (unless autoRaf) |
| `resize()` | Recompute dimensions (if autoResize=false) |

### scrollTo Options

| Option | Type | Description |
|--------|------|-------------|
| `offset` | number | Equivalent to scroll-padding-top |
| `lerp` | number | Override lerp for this animation |
| `duration` | number | Override duration |
| `immediate` | boolean | Skip animation |
| `lock` | boolean | Prevent user scroll until target reached |
| `onComplete` | function | Callback when target reached |

## HTML Attributes for Nested Scroll

```html
<div data-lenis-prevent>block all smooth scroll</div>
<div data-lenis-prevent-wheel>block wheel only</div>
<div data-lenis-prevent-touch>block touch only</div>
```

## Events

```js
lenis.on('scroll', (e) => {
  console.log(e.velocity, e.direction, e.progress)
})
// e: { velocity, direction, progress, scroll, limit }
```

## CSS

```css
/* Must be imported or linked */
@import 'lenis/dist/lenis.css';
```