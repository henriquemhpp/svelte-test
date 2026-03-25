<script>
  import { fly, fade, scale } from 'svelte/transition';
  let selected = 'gpt4';
  let scrollY = 0;

  const llms = [
    {
      id: 'gpt4',
      name: 'GPT-4',
      dev: 'OpenAI',
      modalidade: 'Texto/Imagem',
      mmlu: '~86.4%',
      desc: 'Alta precisão em tarefas complexas',
      icon: '🤖',
      cor: '#a3bffa'
    },
    {
      id: 'gpt4o',
      name: 'GPT-4o',
      dev: 'OpenAI',
      modalidade: 'Texto/Imagem/Áudio',
      mmlu: '~88.7%',
      desc: 'Mais rápido, barato e multimodal',
      icon: '🌐',
      cor: '#b8f2e6'
    },
    {
      id: 'gpt5mini',
      name: 'GPT-5-mini',
      dev: 'OpenAI',
      modalidade: 'Texto',
      mmlu: '~80-83%',
      desc: 'Eficiente e bom custo-benefício',
      icon: '⚡',
      cor: '#ffe5ec'
    },
    {
      id: 'raptor',
      name: 'Raptor Mini (preview)',
      dev: 'Microsoft',
      modalidade: 'Texto',
      mmlu: '~70-75%',
      desc: 'Otimizado para edge e local',
      icon: '🚀',
      cor: '#f0d9ff'
    }
  ];
</script>

<svelte:window bind:scrollY />

<main class="apple-landing">
  <!-- Hero Section -->
  <section class="hero-section" style="transform: translateY({scrollY * 0.5}px); opacity: {Math.max(0.3, 1 - scrollY / 800)}">
    <div class="hero-content">
      <h1 class="hero-title">Modelos de IA Modernos</h1>
      <p class="hero-subtitle">Conheça as diferenças entre GPT-4, GPT-4o, GPT-5-mini e Raptor Mini</p>
    </div>
    <div class="hero-gradient"></div>
  </section>

  <!-- Cards Grid -->
  <section class="cards-grid">
    <h2 class="section-title">Comparação de Modelos</h2>
    <div class="cards-wrapper">
      {#each llms as llm (llm.id)}
        <div
          class="apple-card {selected === llm.id ? 'active' : ''}"
          on:click={() => selected = llm.id}
          on:mouseenter={() => selected = llm.id}
          in:fly={{y: 40, duration: 600}}
        >
          <div class="card-glass"></div>
          <div class="card-content">
            <div class="card-icon" style="color: {llm.cor}">{llm.icon}</div>
            <h3>{llm.name}</h3>
            <p class="card-dev">{llm.dev}</p>
            
            {#if selected === llm.id}
              <div class="card-expanded" in:fade={{duration: 300}}>
                <div class="stat-row">
                  <span class="stat-label">Modalidade</span>
                  <span class="stat-value">{llm.modalidade}</span>
                </div>
                <div class="stat-row">
                  <span class="stat-label">Benchmark MMLU</span>
                  <span class="stat-value mmlu-highlight">{llm.mmlu}</span>
                </div>
                <p class="card-desc">{llm.desc}</p>
              </div>
            {:else}
              <p class="card-desc-short">{llm.desc}</p>
            {/if}
          </div>
          <div class="card-accent" style="background-color: {llm.cor}; opacity: {selected === llm.id ? 1 : 0.4}"></div>
        </div>
      {/each}
    </div>
  </section>

  <!-- Comparison Table -->
  <section class="table-section">
    <h2 class="section-title">Benchmark Comparativo</h2>
    <div class="table-wrapper">
      <table class="comparison-table">
        <thead>
          <tr>
            <th>Modelo</th>
            <th>MMLU</th>
            <th>Modalidade</th>
            <th>Descrição</th>
          </tr>
        </thead>
        <tbody>
          {#each llms as llm}
            <tr 
              class:selected-row={selected === llm.id}
              on:mouseenter={() => selected = llm.id}
            >
              <td class="model-name">{llm.name}</td>
              <td><span class="badge">{llm.mmlu}</span></td>
              <td>{llm.modalidade}</td>
              <td>{llm.desc}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    </div>
  </section>

  <!-- CTA Section -->
  <section class="cta-section">
    <h2>Pronto para explorar?</h2>
    <p>Escolha o modelo ideal para seu projeto de IA</p>
    <button class="cta-button">Começar Agora</button>
  </section>

  <footer class="apple-footer">
    <p>Landing Page • Comparativo de Modelos de IA • 2026</p>
  </footer>
</main>

<style>
  :global(*) {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  .apple-landing {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    background: linear-gradient(180deg, #ffffff 0%, #f5f5f7 100%);
    min-height: 100vh;
    color: #1d1d1f;
    padding: 0;
    margin: 0;
  }

  /* Hero Section */
  .hero-section {
    position: relative;
    height: 600px;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    text-align: center;
    background: radial-gradient(circle at top, #ffffff 0%, #f5f5f7 50%, #efefef 100%);
    backdrop-filter: blur(10px);
  }

  .hero-gradient {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 100%;
    background: radial-gradient(ellipse at center top, rgba(163, 191, 250, 0.15), transparent 60%);
    pointer-events: none;
  }

  .hero-content {
    position: relative;
    z-index: 1;
    animation: fadeInDown 1s ease-out;
  }

  .hero-title {
    font-size: 4.5rem;
    font-weight: 700;
    letter-spacing: -0.02em;
    line-height: 1.1;
    margin: 0 0 1rem 0;
    background: linear-gradient(135deg, #1d1d1f 0%, #a3bffa 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-subtitle {
    font-size: 1.5rem;
    color: #86868b;
    font-weight: 400;
    margin: 0;
    max-width: 600px;
  }

  /* Cards Section */
  .cards-grid {
    padding: 4rem 2rem;
    max-width: 1400px;
    margin: 0 auto;
  }

  .section-title {
    font-size: 2.5rem;
    font-weight: 600;
    text-align: center;
    margin-bottom: 3rem;
    color: #1d1d1f;
  }

  .cards-wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    perspective: 1200px;
  }

  .apple-card {
    position: relative;
    height: 380px;
    border-radius: 20px;
    background: rgba(255, 255, 255, 0.7);
    border: 1px solid rgba(0, 0, 0, 0.08);
    backdrop-filter: blur(20px);
    cursor: pointer;
    transition: all 0.5s cubic-bezier(0.23, 1, 0.320, 1);
    overflow: hidden;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.06);
  }

  .apple-card.active {
    transform: translateY(-12px) scale(1.02);
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
    background: rgba(255, 255, 255, 0.95);
  }

  .apple-card:hover:not(.active) {
    transform: translateY(-6px);
    box-shadow: 0 12px 40px rgba(0, 0, 0, 0.1);
  }

  .card-glass {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.2) 0%, rgba(255, 255, 255, 0) 50%);
    pointer-events: none;
  }

  .card-content {
    position: relative;
    z-index: 1;
    padding: 2rem 1.5rem;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .card-icon {
    font-size: 3.5rem;
    margin-bottom: 1rem;
    transition: transform 0.3s ease;
    filter: drop-shadow(0 4px 12px rgba(0, 0, 0, 0.08));
  }

  .apple-card.active .card-icon {
    transform: scale(1.15) translateY(-8px);
  }

  .apple-card h3 {
    font-size: 1.5rem;
    font-weight: 600;
    margin: 0 0 0.3rem 0;
    color: #1d1d1f;
  }

  .card-dev {
    font-size: 0.95rem;
    color: #86868b;
    margin: 0 0 1rem 0;
  }

  .card-desc-short {
    color: #555;
    font-size: 1rem;
    line-height: 1.5;
    margin: 0;
  }

  .card-expanded {
    width: 100%;
    animation: expandCard 0.4s ease;
  }

  .stat-row {
    display: flex;
    justify-content: space-between;
    padding: 0.8rem 0;
    border-bottom: 1px solid rgba(0, 0, 0, 0.06);
    font-size: 0.95rem;
  }

  .stat-label {
    color: #86868b;
    font-weight: 500;
  }

  .stat-value {
    color: #1d1d1f;
    font-weight: 600;
  }

  .mmlu-highlight {
    background: linear-gradient(90deg, #a3bffa, #b8f2e6);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .card-desc {
    margin-top: 1rem;
    color: #555;
    font-size: 0.95rem;
    line-height: 1.5;
  }

  .card-accent {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 4px;
    transition: all 0.5s ease;
  }

  /* Table Section */
  .table-section {
    padding: 4rem 2rem;
    max-width: 1100px;
    margin: 0 auto;
  }

  .table-wrapper {
    background: rgba(255, 255, 255, 0.8);
    backdrop-filter: blur(20px);
    border-radius: 20px;
    border: 1px solid rgba(0, 0, 0, 0.08);
    overflow: hidden;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.06);
  }

  .comparison-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 1rem;
  }

  .comparison-table thead {
    background: rgba(0, 0, 0, 0.03);
    border-bottom: 1px solid rgba(0, 0, 0, 0.08);
  }

  .comparison-table th {
    padding: 1.2rem;
    text-align: left;
    font-weight: 600;
    color: #1d1d1f;
  }

  .comparison-table td {
    padding: 1.2rem;
    border-bottom: 1px solid rgba(0, 0, 0, 0.05);
    color: #555;
    transition: all 0.3s ease;
  }

  .comparison-table tr.selected-row {
    background: rgba(163, 191, 250, 0.1);
  }

  .comparison-table tbody tr:hover {
    background: rgba(0, 0, 0, 0.02);
  }

  .model-name {
    font-weight: 600;
    color: #1d1d1f;
  }

  .badge {
    display: inline-block;
    background: linear-gradient(90deg, #a3bffa, #b8f2e6);
    color: white;
    padding: 0.3rem 0.8rem;
    border-radius: 12px;
    font-weight: 600;
    font-size: 0.9rem;
  }

  /* CTA Section */
  .cta-section {
    padding: 4rem 2rem;
    text-align: center;
    background: linear-gradient(135deg, rgba(163, 191, 250, 0.1), rgba(184, 242, 230, 0.1));
    border-top: 1px solid rgba(0, 0, 0, 0.08);
  }

  .cta-section h2 {
    font-size: 2.5rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #1d1d1f;
  }

  .cta-section p {
    font-size: 1.1rem;
    color: #86868b;
    margin-bottom: 2rem;
  }

  .cta-button {
    padding: 0.8rem 2.5rem;
    font-size: 1.05rem;
    font-weight: 600;
    border: none;
    border-radius: 12px;
    background: linear-gradient(90deg, #a3bffa, #b8f2e6);
    color: white;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 8px 20px rgba(163, 191, 250, 0.3);
  }

  .cta-button:hover {
    transform: scale(1.05);
    box-shadow: 0 12px 30px rgba(163, 191, 250, 0.4);
  }

  /* Footer */
  .apple-footer {
    padding: 2rem;
    text-align: center;
    color: #86868b;
    font-size: 0.95rem;
    border-top: 1px solid rgba(0, 0, 0, 0.08);
  }

  /* Animations */
  @keyframes fadeInDown {
    from {
      opacity: 0;
      transform: translateY(-30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @keyframes expandCard {
    from {
      opacity: 0;
      transform: translateY(-10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* Responsive */
  @media (max-width: 900px) {
    .hero-title {
      font-size: 3rem;
    }

    .hero-subtitle {
      font-size: 1.2rem;
    }

    .cards-wrapper {
      grid-template-columns: 1fr;
    }

    .section-title {
      font-size: 2rem;
    }
  }

  @media (max-width: 600px) {
    .hero-section {
      height: 400px;
    }

    .hero-title {
      font-size: 2rem;
    }

    .hero-subtitle {
      font-size: 1rem;
    }

    .cards-grid,
    .table-section,
    .cta-section {
      padding: 2rem 1rem;
    }

    .apple-card {
      height: auto;
    }

    .section-title {
      font-size: 1.5rem;
      margin-bottom: 1.5rem;
    }

    .comparison-table {
      font-size: 0.85rem;
    }

    .comparison-table th,
    .comparison-table td {
      padding: 0.8rem;
    }
  }
</style>
