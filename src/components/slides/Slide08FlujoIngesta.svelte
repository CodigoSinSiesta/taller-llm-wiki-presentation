<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const pasos = [
    { n: '1', t: 'Lee la fuente entera', d: 'Identifica autor, fecha y URL real. El fichero raw es solo un contenedor efímero.' },
    { n: '2', t: 'Comenta antes de escribir', d: 'El agente propone un plan: qué páginas crear o actualizar, agrupadas por tema (no por fichero).' },
    { n: '3', t: 'Itera el plan', d: 'Tú validas: fusiona páginas redundantes, descarta lo que no aporta, añade conexiones que faltan.' },
    { n: '4', t: 'Crea/actualiza desde plantilla', d: 'Cada página parte de templates/<tipo>.md. Frontmatter completo, secciones canónicas, [[wikilinks]].' },
    { n: '5', t: 'Cita la fuente original', d: 'En frontmatter y en cuerpo. NUNCA el fichero raw. La regla protege la portabilidad de tu corpus.' },
    { n: '6', t: 'Actualiza index.md y log.md', d: 'Una línea por página nueva en index, una entrada `## [YYYY-MM-DD] ingest | …` en log.' },
    { n: '7', t: 'Aplica tu política de raw/', d: 'Conservar (default), archivar a raw/_archived/<año>/ o eliminar. Lo decides tú en la Entrevista de finalidad. Notas propias y transcripciones únicas suelen pedir conservar.' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Flujo de ingesta</span>
      <h2>De fuente bruta a páginas conectadas</h2>
      <p class="lead">
        Una sola fuente puede afectar a 5-10 páginas. Es normal. El flujo es siempre el mismo, lo que cambia es el contenido.
      </p>
    </div>

    <ol class="flow card-glass">
      {#each pasos as p}
        <li>
          <span class="step-num">{p.n}</span>
          <div class="step-body">
            <strong>{p.t}</strong>
            <p>{p.d}</p>
          </div>
        </li>
      {/each}
    </ol>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 0% 0%, rgba(59, 130, 246, 0.10) 0%, transparent 55%),
      radial-gradient(ellipse at 100% 100%, rgba(30, 58, 138, 0.14) 0%, transparent 55%);
    z-index: 0;
  }
  .slide-content {
    position: relative; z-index: 1;
    max-width: 1100px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-2xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 800px; margin: 0; }

  .flow {
    list-style: none; padding: var(--spacing-xl); margin: 0;
    display: grid; gap: var(--spacing-md);
  }
  .flow li {
    display: grid; grid-template-columns: 48px 1fr; gap: var(--spacing-md);
    align-items: start;
  }
  .step-num {
    width: 40px; height: 40px;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-mono); font-weight: 700; font-size: 1rem;
    color: var(--color-base-dark);
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    border-radius: 50%;
    box-shadow: 0 0 12px rgba(59, 130, 246, 0.3);
  }
  .step-body strong { display: block; font-size: 1.05rem; color: var(--color-neutral-light); margin-bottom: 0.2em; }
  .step-body p { margin: 0; opacity: 0.8; line-height: 1.5; font-size: 0.92rem; }
</style>
