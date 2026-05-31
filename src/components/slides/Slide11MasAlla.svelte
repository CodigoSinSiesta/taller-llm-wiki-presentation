<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const items = [
    { icon: '🔎', title: 'Dataview', desc: 'Queries sobre tu frontmatter: tablas de páginas por tag, listados de stale notes, conteos por tipo. Hace que el wiki responda preguntas, no solo guarde.' },
    { icon: '🌐', title: 'Graph view + MOCs', desc: 'El graph view de Obsidian detecta clusters y huérfanas. Cuando un cluster pasa de 10 páginas, conviértelo en MOC (wiki/<dominio>.md).' },
    { icon: '🧪', title: 'Lint asistido', desc: 'Cada 2-4 semanas pide a tu agente un lint: huérfanas, contradicciones, conceptos sin página, citas mal apuntadas, data gaps con consultas web.' },
    { icon: '🕸️', title: 'Graphify (auditoría puntual)', desc: 'Convierte tu vault en grafo de conocimiento con clusters Leiden. Útil como auditoría, no como pipeline regular. ROI bajo si tu wiki es pequeño.' }
  ];

  const trayectoria = [
    { tiempo: '1 mes', estado: '~10-20 páginas. Pocos enlaces. Sensación de "carpeta vacía con frontmatter".', recompensa: 'Casi ninguna. Es el tramo más frustrante.' },
    { tiempo: '6 meses', estado: '~80-150 páginas. Clusters temáticos visibles. El agente empieza a conectar páginas que tú olvidaste.', recompensa: 'Primeras sorpresas: "ya tenía una nota de esto hace 4 meses".' },
    { tiempo: '3 años', estado: 'Constelación densa. Cada idea nueva se acopla a 3-5 existentes. El wiki piensa contigo.', recompensa: 'Compounding pleno. La inversión semanal de 30 min vale más que cualquier libro.' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Más allá del markdown</span>
      <h2>Cuatro extensiones <span class="highlight">opcionales</span></h2>
      <p class="lead">
        El wiki funciona con solo markdown + tu agente. Estas cuatro extensiones aportan ROI distinto según el tamaño de tu corpus.
      </p>
    </div>

    <div class="grid">
      {#each items as it}
        <div class="card-glass piece">
          <div class="icon">{it.icon}</div>
          <h3>{it.title}</h3>
          <p>{it.desc}</p>
        </div>
      {/each}
    </div>

    <div class="trayectoria">
      <h3 class="tray-title">Trayectoria realista del compounding</h3>
      <div class="tray-grid">
        {#each trayectoria as t}
          <div class="card-glass tray-card">
            <span class="tray-tiempo">{t.tiempo}</span>
            <p class="tray-estado">{t.estado}</p>
            <p class="tray-recompensa"><strong>Recompensa:</strong> {t.recompensa}</p>
          </div>
        {/each}
      </div>
    </div>

    <div class="card-glass routine">
      <strong>La rutina que importa</strong>
      <p>30 min de ingesta semanal &gt; 4h de sprint mensual. La constancia gana al volumen porque el wiki necesita conexiones, no acumulación. <em>El primer mes es el más caro y el menos rentable</em> — atravesarlo es el filtro real.</p>
    </div>
  </div>
</div>

<style>
  .swiper-slide { position: relative; min-height: 100vh; display: flex; align-items: flex-start; justify-content: center; }
  .slide-background {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse at 100% 50%, rgba(59, 130, 246, 0.10) 0%, transparent 50%),
      radial-gradient(ellipse at 0% 50%, rgba(167, 139, 250, 0.08) 0%, transparent 50%);
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

  .grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: var(--spacing-lg); }
  .piece { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .icon { font-size: 1.8rem; }
  h3 { margin: 0; font-size: 1.15rem; }
  .piece p { margin: 0; opacity: 0.85; line-height: 1.55; font-size: 0.95rem; }

  .trayectoria { display: flex; flex-direction: column; gap: var(--spacing-md); }
  .tray-title {
    margin: 0;
    font-family: var(--font-mono); font-size: 0.9rem; color: var(--color-electric);
    letter-spacing: 0.08em; text-transform: uppercase;
  }
  .tray-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--spacing-md); }
  .tray-card {
    padding: var(--spacing-md) var(--spacing-lg);
    display: flex; flex-direction: column; gap: var(--spacing-xs);
    border-top: 2px solid var(--color-electric);
  }
  .tray-tiempo {
    font-family: var(--font-mono); font-size: 0.85rem;
    color: var(--color-accent-bright); letter-spacing: 0.06em;
  }
  .tray-estado { margin: 0; opacity: 0.88; line-height: 1.5; font-size: 0.9rem; }
  .tray-recompensa { margin: 0; opacity: 0.78; line-height: 1.5; font-size: 0.85rem; }
  .tray-recompensa strong { color: var(--color-electric); font-family: var(--font-mono); font-size: 0.78rem; text-transform: uppercase; letter-spacing: 0.06em; }

  .routine { padding: var(--spacing-lg) var(--spacing-xl); }
  .routine strong { color: var(--color-electric); font-family: var(--font-mono); letter-spacing: 0.04em; font-size: 0.9rem; text-transform: uppercase; }
  .routine p { margin: 0.4em 0 0 0; opacity: 0.9; line-height: 1.55; }
  .routine em { color: var(--color-accent-bright); font-style: italic; }

  @media (max-width: 900px) {
    .grid { grid-template-columns: 1fr; }
    .tray-grid { grid-template-columns: 1fr; }
  }
</style>
