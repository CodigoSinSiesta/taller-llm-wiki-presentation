# taller-llm-wiki-presentation

Presentación interactiva (10 slides, 90-120 min) para el taller **LLM Wiki: tu baúl de conocimiento mantenido por Claude Code**.

Acompaña al repo starter [`taller-llm-wiki-starter`](https://github.com/CodigoSinSiesta/taller-llm-wiki-starter), que es el código de partida que clonan los participantes.

## Stack

- **Astro 5** + **Svelte 5** + **Tailwind CSS 4** + **TypeScript** estricto.
- **GSAP 3** para animaciones de entrada y stagger.
- Patrón visual canónico de las presentaciones de [Código Sin Siesta](https://codigosinsiesta.github.io): `slide-background` + orbs radiales + grid animado + `card-glass` + breakpoints `900/768/480/390`.

## Requisitos

- Node.js ≥ 20
- pnpm (recomendado) o npm

## Comandos

```sh
pnpm install
pnpm dev          # http://localhost:4327
pnpm build        # genera dist/
pnpm preview      # sirve dist/ para revisar el build
```

## Estructura

```
src/
├── components/
│   ├── Navigation.svelte           # arrows, drawer, swipe, hash routing
│   └── slides/
│       ├── Slide01Hero.svelte
│       ├── Slide02Problema.svelte
│       ├── Slide03IdeaKarpathy.svelte
│       ├── Slide04Anatomia.svelte
│       ├── Slide05Plantillas.svelte
│       ├── Slide06FlujoIngesta.svelte
│       ├── Slide07HandsOn1Setup.svelte
│       ├── Slide08HandsOn2Ingest.svelte
│       ├── Slide09MasAlla.svelte
│       └── Slide10Cierre.svelte
├── layouts/PresentationLayout.astro
├── pages/index.astro
├── styles/{global,animations}.css
└── utils/animations.ts
```

## Estructura del taller

| # | Slide | Bloque |
|---|-------|--------|
| 1 | Hero | 0 — bienvenida |
| 2 | El problema | 1 — encuadre |
| 3 | La idea (Karpathy) | 1 — encuadre |
| 4 | Anatomía del wiki | 1 — encuadre |
| 5 | Plantillas y vocabulario | 2 — fundamentos |
| 6 | Flujo de ingesta | 3 — fundamentos |
| 7 | Hands-on 1 · Setup | 4 — práctica |
| 8 | Hands-on 2 · Ingest + archivado | 5 — práctica |
| 9 | Más allá (Dataview, MOCs, lint, Graphify) | 6 — extensiones |
| 10 | Cierre — 5 takeaways | 7 — cierre |

Para la versión 90 min, se omiten las extensiones de la slide 9 y se acorta el hands-on 2.

## Despliegue

GitHub Pages desde `main`. La `base` está fijada a `/taller-llm-wiki-presentation` en `astro.config.mjs`.

## Atribución de diseño

El sistema de diseño (colors, tipografías, `card-glass`, animaciones, Navigation) se basa fielmente en [`spec-driven-development-presentation`](https://github.com/CodigoSinSiesta/spec-driven-development-presentation) — única fuente de verdad del patrón visual canónico para presentaciones de la organización.
