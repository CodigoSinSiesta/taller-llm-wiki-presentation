<script lang="ts">
  import SlideResources from '@codigosinsiesta/theme/slides/SlideResources.svelte';
</script>

<SlideResources
  eyebrow="Cierre"
  title="Cinco takeaways"
  titleHighlight="takeaways"
  closing="Código Sin Siesta · 2026 · ¿Preguntas?"
  takeaways={[
    { text: '**Markdown plano + LLM redactor + humano editor**. Tres piezas, una arquitectura.' },
    { text: 'Plantillas y vocabulario controlado son la **fuente de verdad estructural** — no negociable.' },
    { text: '`raw/` es efímera. La cita **siempre apunta a la fuente original**, nunca al fichero raw.' },
    { text: 'El wiki crece por dos vías: **ingesta de raw/** y **archivado de respuestas valiosas**.' },
    { text: '**Constancia gana al volumen**: 30 min semanales mantienen el wiki vivo; los sprints mensuales lo dejan morir.' }
  ]}
  links={[
    { icon: '🚀', title: 'Starter repo', url: 'https://github.com/CodigoSinSiesta/taller-llm-wiki-starter', tag: 'github' },
    { icon: '💎', title: 'Obsidian', url: 'https://obsidian.md', tag: 'tool' },
    { icon: '📊', title: 'Dataview plugin', url: 'https://blacksmithgu.github.io/obsidian-dataview/', tag: 'docs' },
    { icon: '🌐', title: 'Código Sin Siesta', url: 'https://codigosinsiesta.github.io', tag: 'web' }
  ]}
  qr={{ title: 'Starter del taller', url: 'https://github.com/CodigoSinSiesta/taller-llm-wiki-starter' }}
/>
