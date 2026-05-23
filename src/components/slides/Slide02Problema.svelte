<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="El problema"
  title="El conocimiento personal se evapora"
  titleHighlight="evapora"
  columns={3}
  items={[
    {
      title: 'Chats sin estado',
      body: 'Cada sesión empieza de cero. Lo que le explicas a tu agente hoy, **lo olvida mañana**. El conocimiento queda atrapado en conversaciones efímeras.'
    },
    {
      title: 'Contexto fragmentado',
      body: 'Notion, Obsidian, Google Docs, Slack, email… El conocimiento está **disperso entre 5-10 herramientas** y ninguna lo conecta.'
    },
    {
      title: 'Bookmarks que nunca relees',
      body: '**Notion como cementerio**: guardas links, artículos, notas… que nunca vuelves a consultar. El 90% del conocimiento guardado muere en el archivo.'
    }
  ]}
/>
