# AGENTS.md — taller-llm-wiki-presentation

Presentación interactiva del taller LLM Wiki. Acompaña al repo starter
[`taller-llm-wiki-starter`](https://github.com/CodigoSinSiesta/taller-llm-wiki-starter).

Este fichero es la convención cross-agent (lo leen Codex, OpenCode, Aider y
otros). Para Claude Code existe `CLAUDE.md` en la raíz que solo importa este
mismo fichero.

## Stack

- Astro 5 + Svelte 5 + Tailwind CSS 4 + TypeScript estricto.
- GSAP 3 para animaciones.
- `pnpm` como gestor por defecto.

## Convenciones

- **Patrón visual canónico**: `slide-background` (radial gradients) + `animated-grid` (solo Hero) + orbs decorativos + `card-glass` para todo bloque de contenido + breakpoints en 900/768/480/390 + height-aware (`max-height: 900px and min-width: 769px`).
- **Header de slide**: `.slide-header` con `.label` (mono, mayúsculas, color electric) + `<h2>` con un `<span class="highlight">` opcional + `.lead` opcional.
- **Tipografía**: `--font-display` (Space Grotesk) para títulos, `--font-mono` (JetBrains Mono) para labels y código, `--font-body` (IBM Plex Sans) para cuerpo.
- **Color tokens**: `--color-base-dark`, `--color-electric`, `--color-accent-bright`, `--color-neutral-light` (ver `src/styles/global.css`).
- **Animaciones**: cada slide importa `animateSlideEntrance` de `@/utils/animations` y la llama desde `onMount`. No reinventes animaciones — usa las clases utilitarias de `animations.css` (`stagger-children`, `animate-fade-in`, etc.).
- **Responsive**: `clamp(min, vw, max)` para tipografías y tamaños. Probar a 1920x1080, 1440x768, 1024x768, 768, 480 y 390.
- **Lenguaje agent-agnóstico**: el contenido de los slides debe hablar de "tu agente" o listar varios (Claude · Codex · OpenCode · Copilot · Cursor) en vez de asumir Claude Code. La presentación es para cualquier agente moderno que lea ficheros del workspace.

## Cómo añadir un slide nuevo

1. Crea `src/components/slides/SlideXXName.svelte`. Empieza con el patrón:

```svelte
<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Etiqueta</span>
      <h2>Título <span class="highlight">resaltado</span></h2>
      <p class="lead">Frase corta de encuadre.</p>
    </div>
    <!-- contenido en card-glass -->
  </div>
</div>
```

2. Importa el slide en `src/pages/index.astro` y añádelo dentro de `<Navigation>`.
3. Añade el nombre y el título en los arrays `slideNames` / `slideTitles` de `src/components/Navigation.svelte`.
4. `pnpm dev` y comprueba en navegador.

## No hacer

- No usar Tailwind utility classes en los componentes — el patrón canónico se basa en CSS custom properties + `<style>` scoped por slide. Tailwind 4 está cargado por consistencia de stack pero no es la primera opción.
- No crear nuevos colores fuera de los `--color-*` definidos en `global.css`. Si hace falta, extiende los tokens — no inventes valores hex sueltos.
- No olvidar el bloque `@media (max-width: 768px)` mínimo en cada slide. Tres breakpoints es lo razonable: 900, 768, 480.
- No editar `src/styles/global.css` ni `src/styles/animations.css` salvo para añadir tokens — son herencia directa de la presentación canónica.
- No reintroducir lenguaje Claude-only en los slides (corrección 2026-04-25 — la presentación es agent-agnóstica).

## Contenido del taller (sin re-diseñar)

El contenido de cada slide ya está plasmado en los componentes y resumido en [`README.md`](README.md). Si necesitas re-diseñar un slide, parte del componente existente y conserva su estructura semántica (`label`, `h2`, `lead`, cards). El contenido textual debe seguir alineado con el repo starter:
[`taller-llm-wiki-starter`](https://github.com/CodigoSinSiesta/taller-llm-wiki-starter).
