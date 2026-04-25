<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const sintomas = [
    { icon: '💬', title: 'Chats sin estado', desc: 'Cada sesión con Claude/ChatGPT empieza desde cero. Lo bueno que descubriste ayer no llega a hoy.' },
    { icon: '📂', title: 'Notas dispersas', desc: 'Apple Notes, Notion, Bear, Drafts, post-its. Cinco apps, cero recuperación.' },
    { icon: '🔖', title: 'Bookmarks que nunca relees', desc: 'Pinboard, Raindrop, una carpeta de favoritos del navegador. URLs sin contexto, fríos al volver.' },
    { icon: '🪦', title: 'Notion como cementerio', desc: 'Bases de datos preciosas que nadie consulta. Estructura sin uso = ruido caro.' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="slide-content">
    <div class="slide-header">
      <span class="label">El problema</span>
      <h2>El conocimiento personal <span class="highlight">se evapora</span></h2>
      <p class="lead">
        Cuatro síntomas que reconocerás. Si te pasan los cuatro, este taller es para ti.
      </p>
    </div>

    <div class="grid">
      {#each sintomas as item}
        <div class="card-glass card">
          <div class="icon">{item.icon}</div>
          <h3>{item.title}</h3>
          <p>{item.desc}</p>
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
      radial-gradient(ellipse at 80% 10%, rgba(59, 130, 246, 0.10) 0%, transparent 55%),
      radial-gradient(ellipse at 10% 90%, rgba(30, 58, 138, 0.14) 0%, transparent 55%);
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
    color: var(--color-electric); letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  h2 { margin: 0; font-size: clamp(2rem, 5vw, 3.6rem); line-height: 1.1; }
  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }

  .lead { font-size: clamp(1rem, 1.6vw, 1.2rem); opacity: 0.85; max-width: 720px; margin: 0; }

  .grid {
    display: grid; grid-template-columns: repeat(2, 1fr);
    gap: var(--spacing-lg);
  }

  .card { padding: var(--spacing-xl); display: flex; flex-direction: column; gap: var(--spacing-sm); }
  .icon { font-size: 2rem; }
  h3 { margin: 0; font-size: 1.25rem; }
  .card p { margin: 0; opacity: 0.8; line-height: 1.5; font-size: 0.95rem; }

  @media (max-width: 768px) {
    .grid { grid-template-columns: 1fr; gap: var(--spacing-md); }
    .card { padding: var(--spacing-lg); }
  }
</style>
