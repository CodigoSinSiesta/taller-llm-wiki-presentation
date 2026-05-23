<script lang="ts">
  import SlideHandsOn from '@codigosinsiesta/theme/slides/SlideHandsOn.svelte';
</script>

<SlideHandsOn
  eyebrow="Hands-on 1 · 20-25 min"
  title="Setup + Entrevista de finalidad"
  titleHighlight="Entrevista de finalidad"
  intro="Objetivo: vault abierto en Obsidian, plugins activos, finalidad del wiki definida con el agente, primer commit."
  current={2}
  steps={[
    {
      title: 'Clona el starter',
      body: 'Renombra `mi-wiki` a algo personal. Elimina el remote del starter si lo vas a publicar.',
      code: '$ git clone https://github.com/CodigoSinSiesta/taller-llm-wiki-starter mi-wiki\n$ cd mi-wiki'
    },
    {
      title: 'Obsidian + plugins + Web Clipper',
      body: '**File → Open vault → Open folder as vault → `mi-wiki/`**. Activa Templates (core, folder=`templates`) + Dataview (community) + Web Clipper (extensión navegador, Default folder = `raw/`).',
    },
    {
      title: 'Arranca el agente y haz la Entrevista de finalidad',
      body: 'Pídele literalmente: *"Lee AGENTS.md entero. Hazme una Entrevista de finalidad: 5-7 preguntas sobre finalidad, fuentes, política de raw/. No escribas nada hasta que apruebe el plan."*',
      code: '$ claude\n# o: codex | opencode | Copilot | Cursor\n> Lee AGENTS.md entero. Después hazme una Entrevista de finalidad...'
    },
    {
      title: 'Primer commit',
      body: 'Ya tienes la base con la forma de tu caso.',
      code: '$ git add .\n$ git commit -m "Setup inicial: AGENTS.md personalizado y estructura definida"'
    }
  ]}
/>
