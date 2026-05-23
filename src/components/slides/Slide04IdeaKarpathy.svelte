<script lang="ts">
  import SlideEquation from '@codigosinsiesta/theme/slides/SlideEquation.svelte';
</script>

<SlideEquation
  eyebrow="La idea (Karpathy)"
  title="El patrón LLM Wiki en una frase"
  titleHighlight="LLM Wiki"
  note="Lo que necesitas no es un chatbot — es un bibliotecario que lee, sintetiza y conecta. Tú supervisas; el agente ejecuta. El conocimiento queda en tus ficheros, no en la sesión."
  terms={[
    { kind: 'term', label: 'Tu corpus', value: 'Markdown plano' },
    { kind: 'op', symbol: '+' },
    { kind: 'term', label: 'Redactor', value: 'LLM como agente' },
    { kind: 'op', symbol: '+' },
    { kind: 'term', label: 'Control', value: 'Humano como editor' },
    { kind: 'op', symbol: '=' },
    { kind: 'term', label: 'Resultado', value: 'Wiki vivo y consultable', outcome: true }
  ]}
/>
