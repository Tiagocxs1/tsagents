---
name: originkit
description: "Free animated UI component library with 50+ production-ready React/TypeScript components. MCP server at mcp.originkit.dev/mcp. Supports framer, react, vite, and nextjs stacks."
---

# Originkit - Animated Component Library

Free animated UI component library with 50+ production-ready components. MCP endpoint at `https://mcp.originkit.dev/mcp`.

## MCP Tools

| Tool | Description |
|-----|-------------|
| `list_components` | Returns the component index from the registry. Filterable by category. |
| `get_component` | Returns source for a registry component, adapted to your stack (framer, react, nextjs, vite) with optional tweak values. |

## MCP Configuration

```json
{
  "originkit": {
    "type": "url",
    "url": "https://mcp.originkit.dev/mcp",
    "enabled": true
  }
}
```

## Component Categories (50+)

| Category | Components |
|----------|------------|
| **interactive-elements** (12) | Black Hole, Draggable Sticker, Fluid Trail, Gravity Gallery, Juice Effect, Kinetic Grid, Particle Sphere, Pixel Drift, Pixelate Image, Proximity Orbit, SVG Particle, User Cursor |
| **image-gallery** (10) | Blur Carousel, Box Carousel, Coverflow Carousel, Coverflow Gallery, Draggable Grid, Image Gallery, Infinity Canvas, Magnetic Carousel, Spin Image, Spiral Images, Swipe Stack |
| **text** (13) | Direction Hover, Dynamic Weight, Flicker Text, Inkbleed, Mesh Text Hover, Random Letter Swap, Scramble Text, Shiny Pill, Smoky Text, Spotlight Text, Text Lift, Text Morph, Text Path, Type Writer, Weight Hover |
| **background-animation** (4) | Blinking Squares, Character Waves, Pixel Card, Snow Fall |
| **button** (2) | Emoji Burst, Link Preview |
| **animation** (5) | Glitter Wrap, Particle Tunnel, Pixel Reveal, Rising Lines, Star Burst, Sticker Peel |

## Tech Stack

- React + TypeScript
- Framer Motion
- Tailwind CSS
- First-class Framer code components with property panel bindings
- Stack targets: framer, react/vite, nextjs

## Workflow

1. Agent calls `list_components` to browse components
2. Agent calls `get_component` with component name + target stack
3. Agent integrates production-ready source into the project