<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const elementos = [
    { tag: 'NODE', title: 'Una cosa', desc: 'Persona, idea, lugar, evento, concepto. En tu wiki: una página .md.', ejemplo: '[[mcp]]' },
    { tag: 'EDGE', title: 'Una relación nombrada', desc: 'Causa, depende de, referencia, deriva en. En tu wiki: un [[wiki-link]] dentro de una página.', ejemplo: 'X usa Y' },
    { tag: 'TRIPLE', title: 'El átomo del grafo', desc: 'Sujeto + relación + objeto. La unidad mínima del conocimiento estructurado.', ejemplo: 'mcp · expone · tools' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Base teórica · 30 segundos</span>
      <h2>Tu wiki es un <span class="highlight">knowledge graph</span> en markdown</h2>
      <p class="lead">
        El mismo modelo formal que usan Google, Wikipedia y Obsidian. Tres elementos. Si tomas notas con cuidado, el grafo emerge solo.
      </p>
    </div>

    <div class="grid">
      {#each elementos as e}
        <div class="card-glass piece">
          <span class="piece-tag">{e.tag}</span>
          <h3>{e.title}</h3>
          <p>{e.desc}</p>
          <code class="ejemplo">{e.ejemplo}</code>
        </div>
      {/each}
    </div>

    <div class="card-glass aha">
      <h3>El insight</h3>
      <p>
        No diseñas el grafo top-down. <strong>Emerge</strong> cada vez que enlazas una página a otra con <code>[[…]]</code>. El resultado: un mapa de tu pensamiento que se compone con el tiempo, no se acumula. Wikipedia visualizada en Obsidian (1,1% de su contenido) ya forma una constelación densa — el tuyo lo hará al cabo de meses.
      </p>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }

  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 20% 20%, rgba(167, 139, 250, 0.10) 0%, transparent 55%),
      radial-gradient(ellipse at 80% 80%, rgba(59, 130, 246, 0.10) 0%, transparent 55%);
    z-index: 0;
  }

  .slide-content {
    position: relative; z-index: 1;
    max-width: 1200px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-2xl);
  }

  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label {
    font-family: var(--font-mono); font-size: 0.85rem;
    color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase;
  }
  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 720px; margin: 0; }

  .grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-lg);
  }

  .piece { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .piece-tag {
    font-family: var(--font-mono); font-size: 0.75rem;
    color: var(--color-electric); letter-spacing: 0.14em;
  }
  .piece h3 { margin: 0; font-size: 1.2rem; }
  .piece p { margin: 0; opacity: 0.85; line-height: 1.55; font-size: 0.95rem; flex: 1; }
  .ejemplo {
    font-family: var(--font-mono); font-size: 0.85rem;
    color: var(--color-accent-bright);
    background: rgba(59, 130, 246, 0.10);
    padding: var(--spacing-xs) var(--spacing-sm);
    border-radius: 4px; align-self: flex-start;
  }

  .aha { padding: var(--spacing-xl); }
  .aha h3 { margin: 0 0 var(--spacing-sm) 0; font-size: 1.1rem; color: var(--color-electric); }
  .aha p { margin: 0; opacity: 0.9; line-height: 1.6; }
  .aha strong { color: var(--color-accent-bright); font-weight: 600; }
  .aha code {
    font-family: var(--font-mono); font-size: 0.95em;
    background: rgba(59, 130, 246, 0.12);
    padding: 1px 6px; border-radius: 3px;
  }

  @media (max-width: 900px) {
    .grid { grid-template-columns: 1fr; }
  }
</style>
