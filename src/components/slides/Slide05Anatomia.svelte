<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const capas = [
    { num: '01', label: 'raw/', title: 'Bandeja de entrada', desc: 'Fuentes en bruto: artículos clipped, PDFs, transcripciones, notas. Sin tocar. Política propia tras ingestar (conservar / archivar / eliminar).' },
    { num: '02', label: 'wiki/', title: 'Wiki compilado', desc: 'Páginas .md sintetizadas e interconectadas. Frontmatter YAML, [[wiki-links]], index.md plano, log.md append-only, MOCs temáticos cuando un dominio crece.' },
    { num: '03', label: 'mantenimiento', title: 'Auditoría periódica', desc: 'El agente revisa contradicciones, páginas huérfanas, datos obsoletos, conceptos sin página propia. La salud del baúl no la mantienes tú: la dirige tu agente.' }
  ];

  const partes = [
    { title: 'Categorías propias', desc: 'Tú decides qué subcarpetas tiene wiki/ tras la entrevista de finalidad. El patrón no impone vertical: una página = una idea, las carpetas las nombras tú.' },
    { title: 'Frontmatter YAML', desc: 'tipo, resumen, fuentes, actualizado, tags. Obsidian lo renderiza como Properties; Dataview lo consulta.' },
    { title: 'index.md plano', desc: 'Tabla de contenidos con una línea por página. Sin él, el agente no sabe qué hay y duplica páginas.' },
    { title: 'log.md append-only', desc: 'Cada operación queda registrada con formato "[YYYY-MM-DD] tipo | título". Auditable con grep.' },
    { title: 'MOCs temáticos', desc: 'Cuando un dominio acumula >10 páginas, un Map of Content (wiki/<dominio>.md) agrupa con queries Dataview.' },
    { title: 'Plantillas tipadas', desc: 'Una plantilla por tipo (concepto, referencia, nota, …) garantiza frontmatter consistente y secciones canónicas.' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Anatomía del wiki</span>
      <h2>Tres capas, seis piezas</h2>
      <p class="lead">
        El patrón se descompone en tres capas explícitas. Dentro del wiki compilado, seis piezas hacen que sea recuperable, auditable y portable.
      </p>
    </div>

    <div class="capas">
      {#each capas as c}
        <div class="card-glass capa">
          <div class="capa-head">
            <span class="capa-num">{c.num}</span>
            <code class="capa-label">{c.label}</code>
          </div>
          <h3>{c.title}</h3>
          <p>{c.desc}</p>
        </div>
      {/each}
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
    min-height: 80vh;
    padding: var(--spacing-2xl) var(--spacing-content);
    display: flex; flex-direction: column; justify-content: center; gap: var(--spacing-2xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 720px; margin: 0; }

  .capas {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-lg);
  }
  .capa {
    padding: var(--spacing-lg);
    display: flex; flex-direction: column; gap: var(--spacing-sm);
    border-top: 3px solid var(--color-electric);
  }
  .capa-head { display: flex; align-items: baseline; gap: var(--spacing-sm); }
  .capa-num {
    font-family: var(--font-mono); font-size: 0.8rem;
    color: var(--color-electric); letter-spacing: 0.1em;
  }
  .capa-label {
    font-family: var(--font-mono); font-size: 1rem;
    color: var(--color-accent-bright);
    background: rgba(59, 130, 246, 0.12);
    padding: 2px 8px; border-radius: 4px;
  }
  .capa h3 { margin: 0; font-size: 1.05rem; color: var(--color-neutral-light); }
  .capa p { margin: 0; opacity: 0.82; line-height: 1.55; font-size: 0.9rem; }

  .grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--spacing-lg); }
  .piece {
    padding: var(--spacing-lg) var(--spacing-xl);
    display: flex; flex-direction: column; gap: var(--spacing-sm);
    min-height: 160px;
  }
  .piece h3 {
    margin: 0; font-size: 1.15rem;
    font-family: var(--font-mono);
    color: var(--color-electric);
    letter-spacing: 0.04em;
  }
  .piece p { margin: 0; opacity: 0.85; line-height: 1.6; font-size: 1rem; }

  @media (max-width: 1024px) { .grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 640px) { .grid { grid-template-columns: 1fr; } }
</style>
