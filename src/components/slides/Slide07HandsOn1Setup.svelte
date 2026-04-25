<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label hands-on">⚡ Hands-on 1 · 15-20 min</span>
      <h2>Setup desde el <span class="highlight">starter</span></h2>
      <p class="lead">
        Objetivo: vault abierto en Obsidian, plugins activos, CLAUDE.md adaptado a ti, primer commit.
      </p>
    </div>

    <div class="grid">
      <div class="card-glass">
        <h3>1 · Clona el starter</h3>
        <pre><code>git clone https://github.com/CodigoSinSiesta/taller-llm-wiki-starter mi-wiki
cd mi-wiki</code></pre>
        <p class="hint">Renombra <code>mi-wiki</code> a algo personal y elimina el remote del starter si lo vas a publicar.</p>
      </div>

      <div class="card-glass">
        <h3>2 · Abre como vault en Obsidian</h3>
        <p>File → Open vault → <strong>Open folder as vault</strong> → selecciona <code>mi-wiki/</code>.</p>
        <p>Activa los plugins:</p>
        <ul>
          <li><strong>Templates</strong> (core) → folder = <code>templates</code></li>
          <li><strong>Dataview</strong> (community)</li>
        </ul>
      </div>

      <div class="card-glass">
        <h3>3 · Lanza Claude Code y personaliza</h3>
        <pre><code>claude</code></pre>
        <p>Pídele literalmente:</p>
        <p class="prompt">"Lee CLAUDE.md y la sección Propósito. Hazme 3-5 preguntas cortas para rellenar &lt;TU NOMBRE&gt;, &lt;TU ROL&gt; y los frentes del wiki. Cuando tengas respuestas, edita CLAUDE.md y borra la cita explicativa del starter. No toques nada más."</p>
      </div>

      <div class="card-glass">
        <h3>4 · Primer commit</h3>
        <pre><code>git add .
git commit -m "Personalizo CLAUDE.md y arranco mi wiki"</code></pre>
        <p class="hint">Ya tienes la base. El siguiente hands-on convierte una fuente real en páginas conectadas.</p>
      </div>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 80% 80%, rgba(59, 130, 246, 0.14) 0%, transparent 55%),
      radial-gradient(ellipse at 20% 20%, rgba(167, 139, 250, 0.08) 0%, transparent 55%);
    z-index: 0;
  }
  .slide-content {
    position: relative; z-index: 1;
    max-width: 1300px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-2xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  .label.hands-on {
    display: inline-block; align-self: flex-start;
    padding: 0.4em 0.9em;
    background: rgba(59, 130, 246, 0.18);
    border: 1px solid rgba(96, 165, 250, 0.4);
    border-radius: 999px;
  }
  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 800px; margin: 0; }

  .grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: var(--spacing-lg); }
  .card-glass { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .card-glass h3 {
    margin: 0; font-size: 1rem; font-family: var(--font-mono);
    color: var(--color-electric); letter-spacing: 0.04em;
  }
  .card-glass p { margin: 0; opacity: 0.85; line-height: 1.55; font-size: 0.92rem; }
  .card-glass ul { margin: 0; padding-left: 1.2rem; display: grid; gap: 0.3rem; }
  .card-glass li { line-height: 1.5; opacity: 0.9; font-size: 0.9rem; }

  pre {
    margin: 0;
    padding: var(--spacing-md);
    background: rgba(10, 22, 40, 0.6);
    border: 1px solid rgba(96, 165, 250, 0.18);
    border-radius: var(--radius-md);
    overflow-x: auto;
  }
  pre code {
    font-family: var(--font-mono); font-size: 0.85rem;
    color: var(--color-neutral-light); background: transparent; padding: 0;
  }
  code {
    font-family: var(--font-mono); font-size: 0.85em;
    color: var(--color-electric);
    background: rgba(96, 165, 250, 0.08);
    padding: 0.1em 0.4em; border-radius: 4px;
  }

  .prompt {
    font-style: italic;
    padding: var(--spacing-md);
    background: rgba(96, 165, 250, 0.08);
    border-left: 3px solid var(--color-electric);
    border-radius: var(--radius-sm);
  }

  .hint { font-size: 0.85rem; opacity: 0.7; }

  @media (max-width: 900px) { .grid { grid-template-columns: 1fr; } }
</style>
