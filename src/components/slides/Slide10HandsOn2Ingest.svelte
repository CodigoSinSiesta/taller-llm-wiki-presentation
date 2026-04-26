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
      <span class="label hands-on">⚡ Hands-on 2 · 25-30 min</span>
      <h2>Ingest + <span class="highlight">archivado</span> de respuesta</h2>
      <p class="lead">
        Convierte <code>raw/ejemplo-articulo.md</code> en páginas conectadas, después haz una pregunta al wiki y guarda la respuesta.
      </p>
    </div>

    <div class="grid">
      <div class="card-glass">
        <h3>Parte A · Ingesta (15 min)</h3>
        <ol>
          <li>Lee <code>raw/ejemplo-articulo.md</code> en Obsidian.</li>
          <li>Pídele a tu agente:
            <p class="prompt">"Léelo entero, identifica la fuente original y proponme un plan: qué páginas crearías o actualizarías, agrupadas por tema. No escribas nada todavía."</p>
          </li>
          <li>Itera el plan hasta que te convenza.</li>
          <li>Dale luz verde. Recuérdale plantilla, citación, wikilinks, index, log.</li>
          <li>Verifica con <code>git diff</code>.</li>
          <li>Elimina el raw cuando estés conforme.</li>
        </ol>
      </div>

      <div class="card-glass">
        <h3>Parte B · Pregunta y archiva (10 min)</h3>
        <ol>
          <li>Pregunta algo cuya respuesta esté <em>parcialmente</em> en el wiki.
            <p class="prompt">"¿Cuándo recomiendas usar &lt;concepto-X&gt; y cuándo no? Mira primero index.md y las páginas creadas en el ejercicio anterior. Señala qué partes son del wiki y qué partes vienen de fuera."</p>
          </li>
          <li>Aporta tú un dato propio que no está.</li>
          <li>Pídele a tu agente que decida: <em>página nueva o sección de una existente</em>.</li>
          <li>Aplica la decisión + entrada <code>meta</code> en log.</li>
        </ol>
      </div>
    </div>

    <div class="card-glass note">
      <strong>Por qué Parte B importa</strong>
      <p>El wiki no solo crece por ingesta de raw/. Cada conversación útil con tu agente es conocimiento candidato a guardarse. Si no lo archivas, lo pierdes en la siguiente sesión.</p>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 30% 80%, rgba(59, 130, 246, 0.13) 0%, transparent 55%),
      radial-gradient(ellipse at 80% 30%, rgba(167, 139, 250, 0.08) 0%, transparent 55%);
    z-index: 0;
  }
  .slide-content {
    position: relative; z-index: 1;
    max-width: 1300px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  .label.hands-on {
    display: inline-block; align-self: flex-start;
    padding: 0.4em 0.9em;
    background: rgba(59, 130, 246, 0.18);
    border: 1px solid rgba(96, 165, 250, 0.4);
    border-radius: 999px;
  }
  h2 { margin: 0; font-size: clamp(1.8rem, 4.6vw, 3.2rem); line-height: 1.1; }
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }
  .lead { font-size: clamp(1rem, 1.5vw, 1.15rem); opacity: 0.85; max-width: 900px; margin: 0; }

  .grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: var(--spacing-lg); }
  .card-glass { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .card-glass h3 {
    margin: 0; font-size: 1.05rem;
    color: var(--color-electric);
    font-family: var(--font-mono); letter-spacing: 0.04em;
  }
  .card-glass ol { margin: 0; padding-left: 1.2rem; display: grid; gap: 0.6rem; }
  .card-glass li { line-height: 1.5; font-size: 0.92rem; opacity: 0.9; }

  code {
    font-family: var(--font-mono); font-size: 0.85em;
    color: var(--color-electric);
    background: rgba(96, 165, 250, 0.08);
    padding: 0.1em 0.4em; border-radius: 4px;
  }

  .prompt {
    font-style: italic;
    margin: 0.5em 0 0 0;
    padding: var(--spacing-sm) var(--spacing-md);
    background: rgba(96, 165, 250, 0.08);
    border-left: 3px solid var(--color-electric);
    border-radius: var(--radius-sm);
    font-size: 0.85rem;
  }

  .note { padding: var(--spacing-lg) var(--spacing-xl); }
  .note strong { color: var(--color-electric); font-family: var(--font-mono); letter-spacing: 0.04em; font-size: 0.9rem; text-transform: uppercase; }
  .note p { margin: 0.4em 0 0 0; opacity: 0.9; line-height: 1.55; }

  @media (max-width: 900px) { .grid { grid-template-columns: 1fr; } }
</style>
