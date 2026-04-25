<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const partes = [
    { title: 'Categorías propias', desc: 'Tú decides qué subcarpetas tiene wiki/ tras la entrevista de finalidad. El patrón no impone vertical: una página = una idea, las carpetas las nombras tú.' },
    { title: 'Frontmatter YAML', desc: 'tipo, resumen, fuentes, actualizado, tags. Obsidian lo renderiza como Properties; Dataview lo consulta.' },
    { title: 'raw/ con política propia', desc: 'Bandeja de entrada. Tras ingestar: conservar, archivar o eliminar (lo decides tú). Por defecto: conservar — útil si entran notas propias o transcripciones únicas.' },
    { title: 'index.md plano', desc: 'Tabla de contenidos con una línea por página. Sin él, el agente no sabe qué hay y duplica páginas.' },
    { title: 'log.md append-only', desc: 'Cada operación queda registrada con formato "[YYYY-MM-DD] tipo | título". Auditable con grep.' },
    { title: 'MOCs temáticos', desc: 'Cuando un dominio acumula >10 páginas, un Map of Content (wiki/<dominio>.md) agrupa con queries Dataview.' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Anatomía del wiki</span>
      <h2>Seis piezas, ni una más</h2>
      <p class="lead">
        Lo justo para que el wiki sea recuperable, auditable y portable. Si quitas alguna, se rompe; si añades más, sobra.
      </p>
    </div>

    <div class="grid">
      {#each partes as p}
        <div class="card-glass piece">
          <h3>{p.title}</h3>
          <p>{p.desc}</p>
        </div>
      {/each}
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 90% 50%, rgba(59, 130, 246, 0.10) 0%, transparent 50%),
      radial-gradient(ellipse at 10% 50%, rgba(30, 58, 138, 0.14) 0%, transparent 50%);
    z-index: 0;
  }
  .slide-content {
    position: relative; z-index: 1;
    max-width: 1200px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-2xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 720px; margin: 0; }

  .grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--spacing-lg); }
  .piece { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .piece h3 {
    margin: 0; font-size: 1.05rem;
    font-family: var(--font-mono);
    color: var(--color-electric);
    letter-spacing: 0.04em;
  }
  .piece p { margin: 0; opacity: 0.85; line-height: 1.5; font-size: 0.95rem; }

  @media (max-width: 1024px) { .grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 640px) { .grid { grid-template-columns: 1fr; } }
</style>
