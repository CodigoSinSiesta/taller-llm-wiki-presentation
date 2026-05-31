<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const opciones = [
    {
      tag: 'A',
      title: 'Vault único',
      ratio: 'Mismo repo · sin separación',
      pros: 'Simple. Un solo sitio que abrir. El agente lo ve todo y conecta libremente.',
      cons: 'Borrosa la frontera entre lo que pensaste tú y lo que sintetizó el agente. Difícil de auditar al cabo de meses.',
      cuando: 'Empezando. Wiki pequeño (<50 páginas). Fuentes mayoritariamente externas (artículos, papers).',
      recom: false
    },
    {
      tag: 'B',
      title: 'Dos vaults (firewall)',
      ratio: 'human-vault/ + llm-vault/',
      pros: 'Sabes siempre qué viene de tu cabeza y qué del agente. El agente solo lee/escribe en llm-vault. Auditable.',
      cons: 'Dos repos que mantener. El agente no puede tirar de tus notas humanas para enriquecer el LLM Wiki.',
      cuando: 'Tomas notas humanas en serio (Zettelkasten, journaling). Quieres separación deontológica clara humano/IA.',
      recom: false
    },
    {
      tag: 'C',
      title: 'Mismo vault, namespace separado',
      ratio: 'wiki/humano/ + wiki/llm/',
      pros: 'Una sola raíz. Frontera explícita por subcarpeta. El agente puede leer humano/ pero solo escribir en llm/.',
      cons: 'Disciplina de namespace al crear cada página. Si te saltas la regla, el firewall se erosiona.',
      cuando: 'Punto medio. Caso más común para conocimiento personal mixto (síntesis IA + reflexión propia).',
      recom: true
    }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Decisión arquitectónica</span>
      <h2>Tu pensamiento <span class="highlight">vs</span> síntesis del agente</h2>
      <p class="lead">
        Antes del Hands-on tienes que decidir: ¿el agente toca tus notas propias o solo el material que sintetiza? Tres opciones, una pregunta en la <em>Entrevista de finalidad</em>.
      </p>
    </div>

    <div class="grid">
      {#each opciones as o}
        <div class="card-glass option" class:recommended={o.recom}>
          <div class="opt-head">
            <span class="opt-tag">Opción {o.tag}</span>
            {#if o.recom}<span class="badge">Recomendada</span>{/if}
          </div>
          <h3>{o.title}</h3>
          <code class="ratio">{o.ratio}</code>
          <dl>
            <dt>Pros</dt><dd>{o.pros}</dd>
            <dt>Contras</dt><dd>{o.cons}</dd>
            <dt>Cuándo</dt><dd>{o.cuando}</dd>
          </dl>
        </div>
      {/each}
    </div>

    <div class="card-glass nota">
      <p>
        Sea cual sea la decisión, el agente <strong>siempre cita la fuente original</strong> (URL, libro, repo) y nunca un fichero <code>raw/</code> intermedio. Esa regla es independiente del firewall que elijas.
      </p>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }

  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 0% 50%, rgba(167, 139, 250, 0.10) 0%, transparent 55%),
      radial-gradient(ellipse at 100% 50%, rgba(59, 130, 246, 0.10) 0%, transparent 55%);
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
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 760px; margin: 0; }

  .grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--spacing-lg); }

  .option {
    padding: var(--spacing-lg);
    display: flex; flex-direction: column; gap: var(--spacing-sm);
  }
  .option.recommended {
    border: 1px solid rgba(96, 165, 250, 0.45);
    box-shadow: 0 0 0 1px rgba(96, 165, 250, 0.15) inset;
  }
  .opt-head { display: flex; align-items: center; gap: var(--spacing-sm); justify-content: space-between; }
  .opt-tag {
    font-family: var(--font-mono); font-size: 0.78rem;
    color: var(--color-electric); letter-spacing: 0.12em;
  }
  .badge {
    font-family: var(--font-mono); font-size: 0.7rem;
    color: var(--color-accent-bright);
    background: rgba(59, 130, 246, 0.18);
    padding: 2px 8px; border-radius: 999px;
    text-transform: uppercase; letter-spacing: 0.08em;
  }
  .option h3 { margin: 0; font-size: 1.1rem; }
  .ratio {
    font-family: var(--font-mono); font-size: 0.82rem;
    color: var(--color-accent-bright);
    background: rgba(59, 130, 246, 0.10);
    padding: 4px 8px; border-radius: 4px; align-self: flex-start;
  }
  dl { margin: 0; display: flex; flex-direction: column; gap: 4px; }
  dt {
    font-family: var(--font-mono); font-size: 0.7rem;
    color: var(--color-electric); letter-spacing: 0.1em;
    text-transform: uppercase; margin-top: var(--spacing-xs);
  }
  dd { margin: 0; opacity: 0.85; line-height: 1.5; font-size: 0.88rem; }

  .nota { padding: var(--spacing-lg); }
  .nota p { margin: 0; opacity: 0.88; line-height: 1.6; font-size: 0.95rem; }
  .nota strong { color: var(--color-accent-bright); font-weight: 600; }
  .nota code {
    font-family: var(--font-mono); font-size: 0.9em;
    background: rgba(59, 130, 246, 0.12);
    padding: 1px 6px; border-radius: 3px;
  }

  @media (max-width: 1024px) { .grid { grid-template-columns: 1fr; } }
</style>
