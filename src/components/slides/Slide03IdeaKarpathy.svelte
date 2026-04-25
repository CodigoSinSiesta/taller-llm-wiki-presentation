<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const piezas = [
    { tag: '01', title: 'Markdown plano', desc: 'Ficheros .md versionados con git. Sin lock-in, sin BBDD, sin builds. Tu corpus es portable y dura décadas.' },
    { tag: '02', title: 'LLM como redactor', desc: 'Tu agente (Claude, Codex, OpenCode, Copilot…) lee fuentes en bruto, sintetiza, conecta páginas, mantiene índice y log. Trabajo barato y reproducible.' },
    { tag: '03', title: 'Humano como editor', desc: 'Tú decides qué entra, citas las fuentes, validas el plan antes de escribir, refinas el resultado. La calidad sigue siendo humana.' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">La idea (Karpathy)</span>
      <h2>El patrón <span class="highlight">LLM Wiki</span> en una frase</h2>
      <p class="lead">
        Markdown plano + LLM como redactor + humano como editor. Tres piezas, una arquitectura.
      </p>
    </div>

    <div class="pipeline">
      {#each piezas as p, i}
        <div class="card-glass piece">
          <span class="piece-tag">{p.tag}</span>
          <h3>{p.title}</h3>
          <p>{p.desc}</p>
        </div>
        {#if i < piezas.length - 1}
          <div class="arrow" aria-hidden="true">→</div>
        {/if}
      {/each}
    </div>

    <div class="card-glass why-now">
      <h3>¿Por qué ahora?</h3>
      <p>
        Hasta 2024, mantener un wiki personal cuidado costaba más de lo que valía. Con un LLM-redactor barato, el equilibrio se invierte: el coste marginal de añadir una página es cercano a cero, y la fricción de consultarla baja porque está bien escrita y conectada.
      </p>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }

  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 50% 0%, rgba(59, 130, 246, 0.10) 0%, transparent 60%),
      radial-gradient(ellipse at 50% 100%, rgba(167, 139, 250, 0.06) 0%, transparent 50%);
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
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 720px; margin: 0; }

  .pipeline {
    display: grid;
    grid-template-columns: 1fr auto 1fr auto 1fr;
    align-items: stretch;
    gap: var(--spacing-md);
  }

  .piece { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .piece-tag {
    font-family: var(--font-mono); font-size: 0.8rem; color: var(--color-electric); letter-spacing: 0.1em;
  }
  .piece h3 { margin: 0; font-size: 1.25rem; }
  .piece p { margin: 0; opacity: 0.8; line-height: 1.5; font-size: 0.95rem; }

  .arrow {
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem; font-family: var(--font-mono);
    color: var(--color-electric); opacity: 0.6;
    padding: 0 var(--spacing-sm);
  }

  .why-now { padding: var(--spacing-xl); }
  .why-now h3 { margin: 0 0 var(--spacing-sm) 0; font-size: 1.1rem; color: var(--color-electric); }
  .why-now p { margin: 0; opacity: 0.9; line-height: 1.6; }

  @media (max-width: 900px) {
    .pipeline { grid-template-columns: 1fr; }
    .arrow { transform: rotate(90deg); padding: 0; }
  }
</style>
