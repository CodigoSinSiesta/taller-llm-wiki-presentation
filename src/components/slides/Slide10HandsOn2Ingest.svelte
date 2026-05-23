<script lang="ts">
  import SlideHandsOn from '@codigosinsiesta/theme/slides/SlideHandsOn.svelte';
</script>

<SlideHandsOn
  eyebrow="Hands-on 2 · 25-30 min"
  title="Ingest + archivado de respuesta"
  titleHighlight="archivado"
  intro="Convierte `raw/ejemplo-articulo.md` en páginas conectadas, después haz una pregunta al wiki y guarda la respuesta."
  current={0}
  steps={[
    {
      title: 'Parte A · Ingesta (15 min)',
      body: 'Pídele al agente: *"Léelo entero, identifica la fuente original y proponme un plan: qué páginas crearías o actualizarías, agrupadas por tema. No escribas nada todavía."* Itera el plan, dale luz verde, verifica con `git diff`.',
      code: '$ git diff\n✓ wiki/concepto-x.md (nueva)\n✓ wiki/herramienta-y.md (actualizada, +3 líneas)\n✓ wiki/index.md (+2 entradas)\n✓ wiki/log.md (+1 entrada ingesta)'
    },
    {
      title: 'Parte B · Pregunta y archiva (10 min)',
      body: 'Pregunta algo cuya respuesta esté **parcialmente** en el wiki. Aporta un dato propio que no está. Pídele al agente que decida: *página nueva o sección de una existente*.',
      code: '> "¿Cuándo usar <concepto-X> y cuándo no?\n  Mira index.md primero. Señala qué partes son\n  del wiki y qué vienen de fuera."'
    }
  ]}
/>
