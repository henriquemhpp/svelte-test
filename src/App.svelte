<script>
  // ...existing code...
</script>

<main class="landing-tech">
  <header class="header-tech">
    <h1>Diferenças entre GPT-4, GPT-4o, GPT-5-mini e Raptor Mini (preview)</h1>
    <p class="subtitle">Comparativo de LLMs modernas para aplicações em tecnologia</p>
  </header>

  <section class="llm-cards">
    <div class="llm-card gpt4">
      <h2>GPT-4</h2>
      <ul>
        <li>Desenvolvedor: OpenAI</li>
        <li>Modalidade: Texto/Imagem</li>
        <li>Precisão (MMLU): ~86.4%</li>
        <li>Alta precisão, mais caro/lento</li>
      </ul>
    </div>
    <div class="llm-card gpt4o">
      <h2>GPT-4o</h2>
      <ul>
        <li>Desenvolvedor: OpenAI</li>
        <li>Modalidade: Texto/Imagem/Áudio</li>
        <li>Precisão (MMLU): ~88.7%</li>
        <li>Mais rápido/barato, multimodal</li>
      </ul>
    </div>
    <div class="llm-card gpt5mini">
      <h2>GPT-5-mini</h2>
      <ul>
        <li>Desenvolvedor: OpenAI</li>
        <li>Modalidade: Texto</li>
        <li>Precisão (MMLU): ~80-83%</li>
        <li>Eficiente, bom custo-benefício</li>
      </ul>
    </div>
    <div class="llm-card raptor">
      <h2>Raptor Mini (preview)</h2>
      <ul>
        <li>Desenvolvedor: Microsoft</li>
        <li>Modalidade: Texto</li>
        <li>Precisão (MMLU): ~70-75%</li>
        <li>Otimizado para edge/local</li>
      </ul>
    </div>
  </section>

  <section class="llm-table-section">
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
        <tr>
          <td>GPT-4</td>
          <td>~86.4</td>
          <td>Texto/Imagem</td>
          <td>Alta precisão, mais caro/lento</td>
        </tr>
        <tr>
          <td>GPT-4o</td>
          <td>~88.7</td>
          <td>Texto/Imagem/Áudio</td>
          <td>Mais rápido/barato, multimodal</td>
        </tr>
        <tr>
          <td>GPT-5-mini</td>
          <td>~80-83</td>
          <td>Texto</td>
          <td>Eficiente, bom custo-benefício</td>
        </tr>
        <tr>
          <td>Raptor Mini</td>
          <td>~70-75</td>
          <td>Texto</td>
          <td>Otimizado para edge/local</td>
        </tr>
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
  }
  .header-tech {
    text-align: center;
    padding: 2rem 1rem 1rem 1rem;
    background: #e0e7ef;
    border-radius: 0 0 2rem 2rem;
    box-shadow: 0 2px 12px #b6bbc933;
  }
  .header-tech h1 {
    font-size: 2.2rem;
    color: #232946;
    margin-bottom: 0.5rem;
  }
  .subtitle {
    color: #6d6d8b;
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }
  .llm-cards {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1.5rem;
    margin: 2rem 0 1rem 0;
  }
  .llm-card {
    background: #f6f6fa;
    border-radius: 1.2rem;
    box-shadow: 0 2px 8px #b6bbc933;
    padding: 1.5rem 1.2rem;
    min-width: 220px;
    max-width: 260px;
    flex: 1 1 220px;
    transition: transform 0.2s;
    border: 2px solid #e0e7ef;
  }
  .llm-card:hover {
    transform: translateY(-6px) scale(1.03);
    border-color: #a3bffa;
  }
  .llm-card h2 {
    color: #232946;
    font-size: 1.3rem;
    margin-bottom: 0.7rem;
  }
  .llm-card ul {
    list-style: none;
    padding: 0;
    color: #6d6d8b;
    font-size: 1rem;
  }
  .llm-table-section {
    margin: 2rem auto;
    max-width: 700px;
    background: #f6f6fa;
    border-radius: 1.2rem;
    box-shadow: 0 2px 8px #b6bbc933;
    padding: 2rem 1rem;
  }
  .llm-table {
    width: 100%;
    border-collapse: collapse;
    background: #f6f6fa;
  }
  .llm-table th, .llm-table td {
    border: 1px solid #e0e7ef;
    padding: 0.7rem 0.5rem;
    text-align: center;
    font-size: 1rem;
  }
  .llm-table th {
    background: #e0e7ef;
    color: #232946;
    font-weight: 600;
  }
  .llm-table td {
    color: #6d6d8b;
  }
  .footer-tech {
    text-align: center;
    padding: 2rem 1rem 1rem 1rem;
    color: #6d6d8b;
    font-size: 1rem;
    background: transparent;
  }
  @media (max-width: 900px) {
    .llm-cards {
      flex-direction: column;
      align-items: center;
    }
  }
</style>
