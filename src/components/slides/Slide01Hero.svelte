<script lang="ts">
  import SlideHero from '@codigosinsiesta/theme/slides/SlideHero.svelte';
</script>

<SlideHero
  eyebrow="Taller · Código Sin Siesta · 2026"
  title="LLM Wiki"
  titleHighlight="Wiki"
  subtitle="Tu baúl de conocimiento mantenido por tu agente de IA.\n90-120 min para salir con tu propio wiki personal funcionando."
  tools={[
    { label: 'Markdown' },
    { label: 'YAML frontmatter' },
    { label: 'Obsidian' },
    { label: 'AGENTS.md' },
    { label: 'Karpathy pattern', highlight: true },
  ]}
  author={{
    name: 'Alejandro de la Fuente',
    role: 'Technical Leader · NTT Data · GDNE',
    avatarUrl: 'https://www.gravatar.com/avatar/8461e0b8674185c1df153079e820504b?s=120',
    links: [
      { url: 'https://tellmealex.dev', label: 'tellmealex.dev' },
      { url: 'https://codigosinsiesta.github.io', label: 'codigosinsiesta.github.io' }
    ]
  }}
/>
