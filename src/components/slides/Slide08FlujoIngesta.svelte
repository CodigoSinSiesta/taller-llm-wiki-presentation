<script lang="ts">
  import SlideHandsOn from '@codigosinsiesta/theme/slides/SlideHandsOn.svelte';
</script>

<SlideHandsOn
  eyebrow="Flujo de ingesta"
  title="De fuente bruta a páginas conectadas"
  titleHighlight="páginas conectadas"
  intro="Una sola fuente puede afectar a 5-10 páginas. Es normal. El flujo es siempre el mismo; lo que cambia es el contenido."
  current={null}
  steps={[
    {
      title: 'Lee la fuente entera',
      body: 'Identifica autor, fecha y URL real. El fichero raw es **solo un contenedor efímero**.',
    },
    {
      title: 'Comenta antes de escribir',
      body: 'El agente propone un plan: qué páginas crear o actualizar, **agrupadas por tema** (no por fichero). No escribe nada todavía.',
    },
    {
      title: 'Itera el plan',
      body: 'Tú validas: **fusiona páginas redundantes**, descarta lo que no aporta, añade conexiones que faltan.',
    },
    {
      title: 'Crea/actualiza desde plantilla',
      body: 'Cada página parte de `templates/<tipo>.md`. Frontmatter completo, secciones canónicas, `[[wikilinks]]`.',
      code: '$ Crea wiki/claude-code.md desde templates/herramienta.md\n✓ Frontmatter: tipo, tags, fuente, fecha\n✓ Wikilinks: [[MCP]], [[skills]], [[AGENTS.md]]'
    },
    {
      title: 'Cita la fuente original',
      body: 'En frontmatter y en cuerpo. **NUNCA el fichero raw**. La regla protege la portabilidad de tu corpus.',
    },
    {
      title: 'Actualiza index.md y log.md',
      body: 'Una línea por página nueva en index, una entrada `## [YYYY-MM-DD] ingest | …` en log.',
      code: '$ echo "- [[claude-code]] — herramienta CLI de Anthropic" >> wiki/index.md\n$ echo "## 2026-05-23 ingest | claude-code.md creada" >> wiki/log.md'
    },
    {
      title: 'Aplica tu política de raw/',
      body: '**Conservar** (default), archivar a `raw/_archived/<año>/` o eliminar. Lo decides en la Entrevista de finalidad.',
    }
  ]}
/>
