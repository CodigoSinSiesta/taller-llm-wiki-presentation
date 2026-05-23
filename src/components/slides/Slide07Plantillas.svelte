<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Plantillas y vocabulario"
  title="Tres plantillas universales + menú opcional"
  titleHighlight="universales"
  columns={2}
  items={[
    {
      title: 'concepto',
      body: '**Siempre activa** — Idea reutilizable que se cita desde varias páginas. El tipo más común y el más linkado en el grafo.'
    },
    {
      title: 'referencia',
      body: '**Siempre activa** — Fuente externa: artículo, paper, vídeo, libro, repo. Obligatoria en toda ingesta de contenido externo.'
    },
    {
      title: 'nota',
      body: '**Siempre activa** — Entrada genérica, la más flexible. Para todo lo que no encaja en concepto o referencia.'
    },
    {
      title: 'Opcionales (según finalidad)',
      body: '`proyecto` · `herramienta` · `identidad` · `comunidad` · `operativa` — El agente recomienda activar las que encajen tras la **Entrevista de finalidad**.'
    }
  ]}
/>
