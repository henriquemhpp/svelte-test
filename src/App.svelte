<script>
  import { fly, fade, scale } from 'svelte/transition';
  let selected = 'gpt4';
  const llms = [
    {
      id: 'gpt4',
      name: 'GPT-4',
      dev: 'OpenAI',
      modalidade: 'Texto/Imagem',
      mmlu: '~86.4%',
      desc: 'Alta precisão, mais caro/lento',
      color: 'linear-gradient(120deg, #e0e7ef 0%, #b6bbc9 100%)',
      icon: '🤖'
    },
    {
      id: 'gpt4o',
      name: 'GPT-4o',
      dev: 'OpenAI',
      modalidade: 'Texto/Imagem/Áudio',
      mmlu: '~88.7%',
      desc: 'Mais rápido/barato, multimodal',
      color: 'linear-gradient(120deg, #e0e7ef 0%, #a3bffa 100%)',
      icon: '🌐'
    },
    {
      id: 'gpt5mini',
      name: 'GPT-5-mini',
      dev: 'OpenAI',
      modalidade: 'Texto',
      mmlu: '~80-83%',
      desc: 'Eficiente, bom custo-benefício',
      color: 'linear-gradient(120deg, #e0e7ef 0%, #ffe5ec 100%)',
      icon: '⚡'
    },
    {
      id: 'raptor',
      name: 'Raptor Mini (preview)',
      dev: 'Microsoft',
      modalidade: 'Texto',
      mmlu: '~70-75%',
      desc: 'Otimizado para edge/local',
      color: 'linear-gradient(120deg, #e0e7ef 0%, #b8f2e6 100%)',
      icon: '🦖'
    }
  ];
</script>

<main class="landing-tech">
  <header class="header-tech">
    <h1 class="apple-title" in:fly={{y: -40, duration: 800}}>Diferenças entre GPT-4, GPT-4o, GPT-5-mini e Raptor Mini (preview)</h1>
    <p class="subtitle" in:fade={{duration: 1200}}>Comparativo de LLMs modernas para aplicações em tecnologia</p>
  </header>

  <section class="llm-cards-immersive">
    {#each llms as llm}
      <div
        class="llm-card-immersive {selected === llm.id ? 'active' : ''}"
        style="background: {llm.color}"
        on:click={() => selected = llm.id}
        in:scale={{duration: 400}}
        out:fade={{duration: 200}}
      >
        <div class="llm-icon">{llm.icon}</div>
        <h2>{llm.name}</h2>
        <p class="llm-dev">{llm.dev}</p>
        <p class="llm-modalidade">{llm.modalidade}</p>
        <p class="llm-mmlu">MMLU: <b>{llm.mmlu}</b></p>
        <p class="llm-desc">{llm.desc}</p>
        {#if selected === llm.id}
          <div class="llm-highlight" in:fade={{duration: 400}}></div>
        {/if}
      </div>
    {/each}
  </section>

  <section class="llm-table-section-immersive" in:fade={{duration: 800}}>
    <h2>Benchmark Comparativo</h2>
    <table class="llm-table">
      <thead>
        <tr>
          <th>Modelo</th>
          <th>MMLU (%)</th>
          <th>Modalidade</th>
          <th>Observações</th>
        </tr>
      </thead>
      <tbody>
        {#each llms as llm}
        <tr class:selected={selected === llm.id} on:mouseenter={() => selected = llm.id}>
          <td>{llm.name}</td>
          <td>{llm.mmlu}</td>
          <td>{llm.modalidade}</td>
          <td>{llm.desc}</td>
        </tr>
        {/each}
      </tbody>
    </table>
  </section>

  <footer class="footer-tech">
    <p>Landing page criada com Svelte, tema pastel e tecnologia.</p>
  </footer>
</main>

<style>
  .landing-tech {
    font-family: 'Inter', Arial, sans-serif;
    background: linear-gradient(120deg, #f8fafc 0%, #e0e7ef 100%);
    min-height: 100vh;
    color: #232946;
    padding: 0;
    margin: 0;
    overflow-x: hidden;
  }
  .header-tech {
    text-align: center;
    padding: 3rem 1rem 2rem 1rem;
    background: #e0e7ef;
    border-radius: 0 0 2rem 2rem;
    box-shadow: 0 2px 24px #b6bbc933;
    position: relative;
    z-index: 2;
  }
  .apple-title {
    font-size: 2.8rem;
    font-weight: 700;
    letter-spacing: -1px;
    color: #232946;
    margin-bottom: 0.5rem;
    background: linear-gradient(90deg, #232946 60%, #a3bffa 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .subtitle {
    color: #6d6d8b;
    font-size: 1.25rem;
    margin-bottom: 0.5rem;
    font-weight: 400;
  }
  .llm-cards-immersive {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 2.5rem;
    margin: 3rem 0 2rem 0;
    perspective: 1200px;
  }
  .llm-card-immersive {
    background: #f6f6fa;
    border-radius: 1.5rem;
    box-shadow: 0 4px 24px #b6bbc933, 0 1.5px 8px #a3bffa22;
    padding: 2.2rem 1.5rem 1.5rem 1.5rem;
    min-width: 240px;
    max-width: 270px;
    flex: 1 1 240px;
    transition: transform 0.3s, box-shadow 0.3s, border 0.3s;
    border: 2.5px solid #e0e7ef;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transform-style: preserve-3d;
    will-change: transform;
    opacity: 0.96;
  }
  .llm-card-immersive.active, .llm-card-immersive:hover {
    transform: scale(1.07) rotateY(-6deg) translateY(-10px);
    box-shadow: 0 8px 32px #a3bffa55, 0 2px 12px #b6bbc933;
    border-color: #a3bffa;
    opacity: 1;
    z-index: 2;
  }
  .llm-icon {
    font-size: 2.5rem;
    margin-bottom: 0.7rem;
    filter: drop-shadow(0 2px 8px #a3bffa33);
  }
  .llm-card-immersive h2 {
    color: #232946;
    font-size: 1.4rem;
    margin-bottom: 0.3rem;
    font-weight: 600;
  }
  .llm-dev, .llm-modalidade, .llm-mmlu, .llm-desc {
    color: #6d6d8b;
    font-size: 1.05rem;
    margin: 0.2rem 0;
  }
  .llm-mmlu b {
    color: #232946;
    font-weight: 600;
  }
  .llm-highlight {
    position: absolute;
    left: 0; right: 0; bottom: 0;
    height: 8px;
    background: linear-gradient(90deg, #a3bffa 0%, #ffe5ec 100%);
    border-radius: 0 0 1.5rem 1.5rem;
    box-shadow: 0 2px 8px #a3bffa33;
    animation: highlightBar 1.2s cubic-bezier(.4,1.6,.6,1) infinite alternate;
  }
  @keyframes highlightBar {
    0% { opacity: 0.7; }
    100% { opacity: 1; }
  }
  .llm-table-section-immersive {
    margin: 2.5rem auto 2rem auto;
    max-width: 800px;
    background: #f6f6fa;
    border-radius: 1.2rem;
    box-shadow: 0 2px 12px #b6bbc933;
    padding: 2.5rem 1.5rem;
    animation: fadeIn 1.2s;
  }
  .llm-table {
    width: 100%;
    border-collapse: collapse;
    background: #f6f6fa;
    font-size: 1.08rem;
  }
  .llm-table th, .llm-table td {
    border: 1.5px solid #e0e7ef;
    padding: 0.9rem 0.7rem;
    text-align: center;
    font-size: 1.08rem;
    transition: background 0.2s, color 0.2s;
  }
  .llm-table th {
    background: #e0e7ef;
    color: #232946;
    font-weight: 700;
  }
  .llm-table tr.selected, .llm-table tr:hover {
    background: linear-gradient(90deg, #a3bffa22 0%, #ffe5ec22 100%);
    color: #232946;
  }
  .footer-tech {
    text-align: center;
    padding: 2.5rem 1rem 1.5rem 1rem;
    color: #6d6d8b;
    font-size: 1.1rem;
    background: transparent;
    margin-top: 2rem;
  }
  @media (max-width: 900px) {
    .llm-cards-immersive {
      flex-direction: column;
      align-items: center;
    }
    .llm-table-section-immersive {
      padding: 1.2rem 0.2rem;
    }
  }
  @media (max-width: 600px) {
    .apple-title {
      font-size: 1.5rem;
    }
    .llm-card-immersive {
      min-width: 90vw;
      max-width: 98vw;
      padding: 1.2rem 0.5rem;
    }
  }
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(40px); }
    to { opacity: 1; transform: none; }
  }
</style>
