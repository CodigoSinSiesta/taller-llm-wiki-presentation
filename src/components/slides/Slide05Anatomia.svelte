<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Anatomía del wiki"
  title="Tres capas, seis piezas"
  titleHighlight="seis piezas"
  columns={3}
  items={[
    {
      title: 'Bandeja de entrada',
      body: '`raw/` — fuentes en bruto sin procesar. Artículos, transcripciones, notas propias. **Efímera**: se vacía tras cada ingesta.'
    },
    {
      title: 'Wiki compilado',
      body: '`wiki/` — el conocimiento destilado. Páginas conectadas con `[[wikilinks]]`, frontmatter YAML y plantillas tipadas. **Persistente**.'
    },
    {
      title: 'Auditoría periódica',
      body: '`wiki/log.md` — registro append-only de ingestas. `wiki/index.md` — directorio plano de todas las páginas. **Mantenimiento**.'
    },
    {
      title: 'YAML frontmatter',
      body: 'Metadata estructurada: `tipo`, `tags`, `fecha`, `fuente`. El agente lo rellena; tú lo validas. Permite consultas con **Dataview**.'
    },
    {
      title: 'Plantillas tipadas',
      body: '`templates/` — `concepto.md`, `referencia.md`, `nota.md`. La base que garantiza **consistencia** entre páginas del mismo tipo.'
    },
    {
      title: 'AGENTS.md',
      body: 'La constitución del wiki. Define propósito, vocabulario, política de `raw/` y reglas de citación. El **contrato con el agente**.'
    }
  ]}
/>
