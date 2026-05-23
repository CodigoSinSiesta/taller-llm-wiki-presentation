<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Más allá del markdown"
  title="Cuatro extensiones opcionales"
  titleHighlight="extensiones"
  columns={2}
  items={[
    {
      title: 'Dataview',
      body: '**Queries SQL-like** sobre tu frontmatter YAML. Lista todos los conceptos con `tipo: herramienta`, busca referencias de 2026, agrupa por tags. Tu wiki como base de datos.'
    },
    {
      title: 'Graph view + MOCs',
      body: 'Visualización del grafo de `[[wikilinks]]`. Los **MOCs** (Maps of Content) son páginas índice temáticas que agrupan nodos relacionados y revelan la estructura emergente del conocimiento.'
    },
    {
      title: 'Lint asistido',
      body: 'El agente **audita el wiki periódicamente**: detecta páginas huérfanas (sin links entrantes), frontmatter incompleto, inconsistencias en el vocabulario controlado.'
    },
    {
      title: 'Graphify (auditoría puntual)',
      body: 'Indexa el vault completo como knowledge graph y permite **consultas semánticas** complejas: "¿qué conceptos están relacionados con X pero no linkeados directamente?"'
    }
  ]}
/>
