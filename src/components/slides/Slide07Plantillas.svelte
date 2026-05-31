<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const universales = [
    { tipo: 'concepto', uso: 'Idea reutilizable que se cita desde varias páginas' },
    { tipo: 'referencia', uso: 'Fuente externa (artículo, paper, vídeo, libro, repo)' },
    { tipo: 'nota', uso: 'Entrada genérica — la más flexible' }
  ];

  const opcionales = [
    { tipo: 'proyecto', uso: 'Una página por proyecto, repo, cliente o iniciativa' },
    { tipo: 'herramienta', uso: 'Una herramienta concreta del stack' },
    { tipo: 'identidad', uso: 'Perfil, trayectoria, valores (si tu wiki incluye marca personal)' },
    { tipo: 'comunidad', uso: 'Marca, audiencia, canales (si gestionas una comunidad o producto)' },
    { tipo: 'operativa', uso: 'Roadmap, ideas, playbooks, ADRs' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Plantillas y vocabulario</span>
      <h2>Tres plantillas <span class="highlight">universales</span> + un menú opcional</h2>
      <p class="lead">
        El starter no impone una vertical. Vienen activas tres plantillas que sirven para casi cualquier caso, y el agente activa las opcionales que encajen tras la entrevista de finalidad.
      </p>
    </div>

    <div class="grid">
      <div class="card-glass">
        <h3>Universales · siempre activas</h3>
        <table class="types">
          <thead>
            <tr><th>tipo</th><th>cuándo usarla</th></tr>
          </thead>
          <tbody>
            {#each universales as t}
              <tr>
                <td><code>{t.tipo}</code></td>
                <td>{t.uso}</td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>

      <div class="card-glass">
        <h3>Opcionales · activadas según finalidad</h3>
        <p>En <code>templates/opcionales/</code>. El agente recomienda mover a <code>templates/</code> las que encajen con tu caso.</p>
        <table class="types">
          <thead>
            <tr><th>tipo</th><th>cuándo encaja</th></tr>
          </thead>
          <tbody>
            {#each opcionales as t}
              <tr>
                <td><code>{t.tipo}</code></td>
                <td>{t.uso}</td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
    </div>

    <div class="card-glass tags-note">
      <h3>Vocabulario controlado de tags</h3>
      <p>
        Los <code>tags</code> del frontmatter siguen un vocabulario común para que las queries Dataview funcionen. <strong>Empieza con pocos</strong> — si una finalidad es estudio, prueba <code>tema</code>, <code>examen</code>; si es cliente, <code>requisito</code>, <code>incidencia</code>; si es hobby, los términos de tu dominio. Regla: cada nuevo tag debería aparecer en 2-3 páginas para ganarse su sitio.
      </p>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 100% 0%, rgba(59, 130, 246, 0.10) 0%, transparent 55%),
      radial-gradient(ellipse at 0% 100%, rgba(167, 139, 250, 0.07) 0%, transparent 50%);
    z-index: 0;
  }
  .slide-content {
    position: relative; z-index: 1;
    max-width: 1300px; width: 100%;
    padding: var(--spacing-content);
    display: flex; flex-direction: column; gap: var(--spacing-xl);
  }
  .slide-header { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .label { font-family: var(--font-mono); font-size: 0.85rem; color: var(--color-electric); letter-spacing: 0.12em; text-transform: uppercase; }
  h2 { margin: 0; font-size: clamp(1.8rem, 4.6vw, 3.2rem); line-height: 1.1; }
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }
  .lead { font-size: clamp(1rem, 1.5vw, 1.15rem); opacity: 0.85; max-width: 900px; margin: 0; }

  .grid { display: grid; grid-template-columns: 1fr 1fr; gap: var(--spacing-lg); align-items: start; }
  .card-glass { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-md); }
  .card-glass h3 {
    margin: 0; font-size: 1.05rem;
    color: var(--color-electric); font-family: var(--font-mono); letter-spacing: 0.04em;
  }
  .card-glass p { margin: 0; opacity: 0.85; line-height: 1.5; font-size: 0.92rem; }

  table.types { width: 100%; border-collapse: collapse; font-size: 0.88rem; }
  table.types th, table.types td {
    text-align: left; padding: var(--spacing-sm) var(--spacing-md);
    border-bottom: 1px solid rgba(96, 165, 250, 0.15);
  }
  table.types th { font-family: var(--font-mono); color: var(--color-electric); font-weight: 600; font-size: 0.78rem; letter-spacing: 0.05em; text-transform: uppercase; }
  table.types tr:last-child td { border-bottom: none; }

  code {
    font-family: var(--font-mono); font-size: 0.85em;
    color: var(--color-electric);
    background: rgba(96, 165, 250, 0.08);
    padding: 0.1em 0.4em; border-radius: 4px;
  }

  .tags-note { padding: var(--spacing-lg) var(--spacing-xl); }

  @media (max-width: 900px) { .grid { grid-template-columns: 1fr; } }
</style>
