<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Decisión arquitectónica"
  title="Tu pensamiento vs síntesis del agente"
  titleHighlight="síntesis del agente"
  columns={3}
  items={[
    {
      title: 'Vault único',
      body: 'Todo en el mismo vault. Tus notas personales y las síntesis del agente conviven. **Simple** pero sin firewall entre lo tuyo y lo generado.'
    },
    {
      title: 'Dos vaults (firewall)',
      body: 'Un vault personal (tus notas), un vault wiki (síntesis del agente). **Separación clara** entre pensamiento propio y conocimiento destilado. Recomendado si tienes mucho diario personal.'
    },
    {
      title: 'Mismo vault, namespace separado',
      body: 'Un vault pero carpetas bien diferenciadas: `diario/`, `wiki/`. **Compromiso**: acceso fácil cruzado + separación semántica. El más común en la práctica.'
    }
  ]}
/>
