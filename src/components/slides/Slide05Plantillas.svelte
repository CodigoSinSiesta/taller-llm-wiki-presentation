<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const tipos = [
    { tipo: 'concepto', carpeta: 'wiki/conceptos/', uso: 'Idea reutilizable entre proyectos' },
    { tipo: 'herramienta', carpeta: 'wiki/herramientas/', uso: 'Una herramienta concreta' },
    { tipo: 'proyecto', carpeta: 'wiki/proyectos/', uso: 'Un proyecto o repo' },
    { tipo: 'identidad', carpeta: 'wiki/identidad/', uso: 'Perfil, trayectoria, stack' },
    { tipo: 'comunidad', carpeta: 'wiki/comunidad/', uso: 'Marca, audiencia, canales' },
    { tipo: 'referencia', carpeta: 'wiki/referencias/', uso: 'Fuente externa (artículo, paper, vídeo)' },
    { tipo: 'operativa', carpeta: 'wiki/operativa/', uso: 'Roadmap, idea, playbook, ADR' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Plantillas y vocabulario</span>
      <h2>Una plantilla por <span class="highlight">tipo</span></h2>
      <p class="lead">
        Las plantillas son la fuente de verdad estructural. Garantizan frontmatter completo, secciones canónicas y enlaces relacionados. Sin ellas, cada página inventa su propio formato.
      </p>
    </div>

    <div class="grid">
      <div class="card-glass">
        <h3>Tipos disponibles</h3>
        <table class="types">
          <thead>
            <tr><th>tipo</th><th>carpeta</th><th>uso</th></tr>
          </thead>
          <tbody>
            {#each tipos as t}
              <tr>
                <td><code>{t.tipo}</code></td>
                <td><code>{t.carpeta}</code></td>
                <td>{t.uso}</td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>

      <div class="card-glass">
        <h3>Vocabulario controlado</h3>
        <p>
          Los <code>tags</code> del frontmatter siguen un vocabulario común para que las queries Dataview funcionen. Empieza con pocos y deja que converjan.
        </p>
        <ul>
          <li><strong>Temáticos genéricos</strong>: <code>aprendizaje</code>, <code>producto</code>, <code>cliente</code>, <code>tecnico</code>.</li>
          <li><strong>Específicos del dominio</strong>: si tu wiki es de IA, <code>agentes</code>, <code>mcp</code>, <code>sdd</code>.</li>
          <li><strong>Regla</strong>: cada nuevo tag debe aparecer en al menos 2-3 páginas para ganarse su sitio.</li>
        </ul>
      </div>
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
  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 800px; margin: 0; }

  .grid { display: grid; grid-template-columns: 1.2fr 1fr; gap: var(--spacing-lg); }
  .card-glass { padding: var(--spacing-xl); }
  .card-glass h3 {
    margin: 0 0 var(--spacing-md) 0; font-size: 1.1rem;
    color: var(--color-electric); font-family: var(--font-mono); letter-spacing: 0.04em;
  }

  table.types { width: 100%; border-collapse: collapse; font-size: 0.9rem; }
  table.types th, table.types td {
    text-align: left; padding: var(--spacing-sm) var(--spacing-md);
    border-bottom: 1px solid rgba(96, 165, 250, 0.15);
  }
  table.types th { font-family: var(--font-mono); color: var(--color-electric); font-weight: 600; font-size: 0.8rem; letter-spacing: 0.05em; text-transform: uppercase; }
  table.types tr:last-child td { border-bottom: none; }

  code {
    font-family: var(--font-mono); font-size: 0.85em;
    color: var(--color-electric);
    background: rgba(96, 165, 250, 0.08);
    padding: 0.1em 0.4em; border-radius: 4px;
  }

  .card-glass p { margin: 0 0 var(--spacing-md) 0; opacity: 0.85; line-height: 1.5; }
  .card-glass ul { margin: 0; padding-left: 1.2rem; display: grid; gap: 0.5rem; }
  .card-glass li { line-height: 1.5; opacity: 0.9; font-size: 0.9rem; }

  @media (max-width: 900px) { .grid { grid-template-columns: 1fr; } }
</style>
