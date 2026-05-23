<script lang="ts">
  import SlideDidactic from '@codigosinsiesta/theme/slides/SlideDidactic.svelte';
</script>

<SlideDidactic
  eyebrow="Base teórica · 30 segundos"
  title="Tu wiki es un knowledge graph en markdown"
  titleHighlight="knowledge graph"
  definition={{
    title: 'El átomo del grafo',
    body: '**Sujeto + relación + objeto**. La unidad mínima del conocimiento conectado. `Claude Code` → `usa` → `herramientas MCP`. Cada `[[wikilink]]` en Obsidian es una arista del grafo.'
  }}
  analogy={{
    title: 'Personas, ideas, relaciones',
    body: '**Una cosa** (persona, idea, lugar, evento, concepto) + **una relación nombrada** (causa, depende de, referencia, deriva en) + otra cosa. No necesitas una base de datos — markdown plano es suficiente.'
  }}
  examples={{
    title: 'Por qué markdown plano',
    items: [
      'Sin vendor lock-in: tus archivos son tuyos para siempre',
      'Cualquier LLM puede leerlos y actualizarlos sin herramientas especiales',
      'YAML frontmatter como metadata estructurada (tipo, tags, fecha, fuente)',
      'Obsidian visualiza el grafo sin coste adicional'
    ]
  }}
/>
