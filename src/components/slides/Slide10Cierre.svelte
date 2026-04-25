<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const takeaways = [
    'Markdown plano + LLM redactor + humano editor. Tres piezas, una arquitectura.',
    'Plantillas y vocabulario controlado son la fuente de verdad estructural — no negociable.',
    'raw/ es efímera. La cita siempre apunta a la fuente original.',
    'El wiki crece por dos vías: ingesta de raw/ y archivado de respuestas valiosas.',
    'Constancia gana al volumen: 30 min semanales mantienen el wiki vivo; los sprints mensuales lo dejan morir entre medias.'
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Cierre</span>
      <h2>Cinco <span class="highlight">takeaways</span></h2>
    </div>

    <ol class="takeaways card-glass">
      {#each takeaways as t, i}
        <li>
          <span class="num">{i + 1}</span>
          <span>{t}</span>
        </li>
      {/each}
    </ol>

    <div class="recursos">
      <div class="card-glass">
        <h3>Recursos</h3>
        <ul>
          <li><strong>Starter</strong>: <a href="https://github.com/CodigoSinSiesta/taller-llm-wiki-starter" target="_blank" rel="noopener">github.com/CodigoSinSiesta/taller-llm-wiki-starter</a></li>
          <li><strong>Patrón Karpathy</strong>: artículo original "LLM Wiki"</li>
          <li><strong>Obsidian</strong>: <a href="https://obsidian.md" target="_blank" rel="noopener">obsidian.md</a></li>
          <li><strong>Dataview</strong>: <a href="https://blacksmithgu.github.io/obsidian-dataview/" target="_blank" rel="noopener">docs.dataview</a></li>
          <li><strong>Comunidad</strong>: <a href="https://codigosinsiesta.github.io" target="_blank" rel="noopener">codigosinsiesta.github.io</a></li>
        </ul>
      </div>

      <div class="card-glass next-step">
        <span class="cta">Siguiente paso accionable</span>
        <p>
          Bloquea <strong>30 minutos</strong> en tu calendario para esta misma semana. Lleva una sola fuente que tengas pendiente —URL, PDF, transcript— e ingéstala con Claude.
        </p>
        <p>
          Si en una semana no has hecho la primera ingesta real, este taller no se habrá traducido en wiki. La inercia es el único enemigo serio.
        </p>
      </div>
    </div>

    <p class="thanks">Gracias. ¿Preguntas?</p>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 50% 0%, rgba(59, 130, 246, 0.12) 0%, transparent 60%),
      radial-gradient(ellipse at 50% 100%, rgba(167, 139, 250, 0.08) 0%, transparent 50%);
    z-index: 0;
  }
  .slide-content {
    position: relative; z-index: 1;
    max-width: 1200px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }

  .takeaways {
    list-style: none; padding: var(--spacing-xl); margin: 0;
    display: grid; gap: var(--spacing-md);
  }
  .takeaways li {
    display: grid; grid-template-columns: 40px 1fr; gap: var(--spacing-md);
    align-items: start; line-height: 1.55; font-size: 1rem;
  }
  .num {
    width: 32px; height: 32px;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-mono); font-weight: 700; font-size: 0.9rem;
    color: var(--color-base-dark);
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    border-radius: 50%;
  }

  .recursos { display: grid; grid-template-columns: 1fr 1fr; gap: var(--spacing-lg); }
  .card-glass { padding: var(--spacing-xl); }
  .card-glass h3 { margin: 0 0 var(--spacing-md) 0; font-size: 1.05rem; color: var(--color-electric); font-family: var(--font-mono); letter-spacing: 0.04em; }
  .card-glass ul { margin: 0; padding-left: 1.2rem; display: grid; gap: 0.4rem; }
  .card-glass li { line-height: 1.5; opacity: 0.9; font-size: 0.92rem; }

  .next-step .cta {
    font-family: var(--font-mono); font-size: 0.85rem;
    color: var(--color-electric); letter-spacing: 0.04em; text-transform: uppercase;
    display: block; margin-bottom: var(--spacing-md);
  }
  .next-step p { margin: 0 0 var(--spacing-sm) 0; opacity: 0.9; line-height: 1.55; font-size: 0.95rem; }

  .thanks {
    margin-top: var(--spacing-xl);
    text-align: center;
    font-family: var(--font-display);
    font-size: clamp(1.5rem, 4vw, 2.5rem);
    font-weight: 700;
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric), #a78bfa);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }

  @media (max-width: 900px) {
    .recursos { grid-template-columns: 1fr; }
  }
</style>
