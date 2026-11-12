<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Página educativa sobre sensores de luz e radiação solar: LDR, fotodiodos, intensidade luminosa e coletores solares.">
  <meta name="theme-color" content="#8d79b5">
  <meta name="author" content="Projeto de Ciências e Tecnologia">
  <title>Sensores de Luz e Radiação Solar</title>

  <!-- Preload de fontes para performance -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

  <style>
    /* ========== VARIÁVEIS DE DESIGN ========== */
    :root {
      /* Paleta original aprimorada com contraste WCAG AA */
      --color-primary: #6b4f9e;
      --color-primary-dark: #4a3575;
      --color-accent: #b06e9e;
      --color-text: #2d2b3d;
      --color-text-muted: #4a4760;
      --color-bg: #faf8ff;
      --color-bg-alt: #f3eef9;
      --color-card-blue: #e9f2ff;
      --color-card-purple: #f5e9ff;
      --color-card-green: #e4f5eb;
      --color-card-pink: #fff0f5;
      --color-border: #e4dced;
      --color-focus: #ffbf00;
      --color-highlight-border: #c97ba3;

      --shadow-sm: 0 2px 8px rgba(107, 79, 158, 0.08);
      --shadow-md: 0 5px 18px rgba(107, 79, 158, 0.12);
      --radius-sm: 10px;
      --radius-md: 16px;
      --radius-lg: 20px;
      --transition: 0.25s ease-in-out;
      --max-width: 1050px;
      --font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif;
    }

    /* Modo alto contraste */
    [data-contrast="high"] {
      --color-primary: #00008b;
      --color-primary-dark: #000066;
      --color-text: #000000;
      --color-text-muted: #000000;
      --color-bg: #ffffff;
      --color-bg-alt: #f0f0f0;
      --color-border: #000000;
      --color-highlight-border: #000000;
    }

    /* ========== RESET E BASE ========== */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: var(--font-family);
      background: var(--color-bg);
      color: var(--color-text);
      line-height: 1.7;
      font-size: 1rem;
      -webkit-font-smoothing: antialiased;
    }

    /* ========== ACESSIBILIDADE ========== */
    /* Skip link */
    .skip-link {
      position: absolute;
      top: -50px;
      left: 0;
      background: var(--color-primary);
      color: #fff;
      padding: 0.75rem 1.5rem;
      z-index: 1000;
      text-decoration: none;
      font-weight: 600;
      border-radius: 0 0 var(--radius-sm) 0;
      transition: top var(--transition);
    }
    .skip-link:focus {
      top: 0;
      outline: 3px solid var(--color-focus);
      outline-offset: 2px;
    }

    /* Foco visível em todos os elementos interativos */
    a:focus-visible,
    button:focus-visible,
    input:focus-visible,
    select:focus-visible,
    textarea:focus-visible {
      outline: 3px solid var(--color-focus);
      outline-offset: 3px;
      border-radius: 4px;
    }

    /* Respeita preferência por movimento reduzido */
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
        scroll-behavior: auto !important;
      }
    }

    /* ========== HEADER ========== */
    .header {
      background: linear-gradient(135deg, #d9eaff, #eadfff, #ffe2ec);
      text-align: center;
      padding: 4rem 1.5rem;
    }
    .header__title {
      font-size: clamp(1.75rem, 4vw, 2.5rem);
      color: #3d3a5c;
      margin-bottom: 1rem;
      line-height: 1.2;
    }
    .header__subtitle {
      font-size: clamp(1rem, 2vw, 1.15rem);
      color: #4a4760;
      max-width: 600px;
      margin: 0 auto;
    }

    /* ========== NAVEGAÇÃO ========== */
    .nav {
      background: var(--color-bg-alt);
      padding: 1rem;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 100;
      border-bottom: 1px solid var(--color-border);
      box-shadow: var(--shadow-sm);
    }
    .nav__list {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.5rem;
      list-style: none;
    }
    .nav__link {
      color: var(--color-primary-dark);
      text-decoration: none;
      font-weight: 600;
      padding: 0.5rem 1rem;
      border-radius: var(--radius-sm);
      transition: background var(--transition), color var(--transition);
      display: inline-block;
    }
    .nav__link:hover,
    .nav__link:focus {
      background: var(--color-primary);
      color: #fff;
    }

    /* ========== CONTROLES DE ACESSIBILIDADE ========== */
    .a11y-controls {
      position: fixed;
      bottom: 1.5rem;
      left: 1.5rem;
      z-index: 999;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
    .a11y-btn {
      background: var(--color-primary);
      color: #fff;
      border: 2px solid #fff;
      width: 50px;
      height: 50px;
      border-radius: 50%;
      cursor: pointer;
      font-size: 1.25rem;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: var(--shadow-md);
      transition: transform var(--transition), background var(--transition);
    }
    .a11y-btn:hover {
      background: var(--color-primary-dark);
      transform: scale(1.05);
    }
    .a11y-btn[aria-pressed="true"] {
      background: var(--color-primary-dark);
    }

    /* ========== CONTAINER E SEÇÕES ========== */
    .container {
      max-width: var(--max-width);
      margin: 0 auto;
      padding: 2rem 1.25rem;
    }

    .section {
      background: #fff;
      padding: 2rem;
      margin: 1.75rem 0;
      border-radius: var(--radius-lg);
      box-shadow: var(--shadow-sm);
      transition: box-shadow var(--transition);
    }
    .section:hover { box-shadow: var(--shadow-md); }

    .section__title {
      color: var(--color-primary);
      margin-bottom: 1rem;
      font-size: clamp(1.4rem, 3vw, 1.75rem);
      line-height: 1.3;
    }
    .section__subtitle {
      color: var(--color-accent);
      margin: 1.25rem 0 0.75rem;
      font-size: 1.15rem;
    }

    .section p { margin-bottom: 1rem; }
    .section p:last-child { margin-bottom: 0; }

    /* ========== CARDS ========== */
    .cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 1.25rem;
      margin-top: 1.5rem;
    }
    .card {
      padding: 1.5rem;
      border-radius: var(--radius-md);
      background: var(--color-card-blue);
      transition: transform var(--transition), box-shadow var(--transition);
    }
    .card:hover {
      transform: translateY(-3px);
      box-shadow: var(--shadow-md);
    }
    .card:nth-child(2) { background: var(--color-card-purple); }
    .card:nth-child(3) { background: var(--color-card-green); }
    .card:nth-child(4) { background: var(--color-card-pink); }

    .card__icon {
      font-size: 2.25rem;
      margin-bottom: 0.75rem;
      display: block;
    }
    .card__title {
      color: var(--color-primary-dark);
      margin-bottom: 0.5rem;
      font-size: 1.15rem;
    }

    /* ========== DESTAQUE ========== */
    .highlight {
      background: var(--color-card-pink);
      padding: 1.25rem 1.5rem;
      border-left: 5px solid var(--color-highlight-border);
      border-radius: var(--radius-sm);
      margin-top: 1.25rem;
    }
    .highlight strong {
      color: var(--color-primary-dark);
      display: block;
      margin-bottom: 0.25rem;
    }

    /* ========== SIMULADOR ========== */
    .simulator {
      background: var(--color-card-blue);
      padding: 2rem;
      border-radius: var(--radius-md);
      margin-top: 1.5rem;
      text-align: center;
    }
    .simulator__label {
      display: block;
      font-weight: 600;
      color: var(--color-primary-dark);
      margin-bottom: 0.75rem;
      font-size: 1.05rem;
    }
    .simulator input[type="range"] {
      width: 100%;
      max-width: 500px;
      margin: 1rem auto;
      accent-color: var(--color-primary);
      cursor: pointer;
    }
    .simulator__value {
      font-size: clamp(1.5rem, 3vw, 2rem);
      color: var(--color-primary);
      font-weight: 700;
      margin: 0.75rem 0;
      font-variant-numeric: tabular-nums;
    }
    .bar {
      height: 22px;
      border-radius: 20px;
      background: #e0d8ec;
      margin: 1rem auto;
      max-width: 500px;
      overflow: hidden;
      border: 1px solid var(--color-border);
    }
    .fill {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, #a8d8c0, #a8b9ec);
      transition: width 0.4s ease-in-out;
    }
    .simulator__situation {
      color: var(--color-accent);
      margin: 1rem 0 0.5rem;
      font-size: 1.2rem;
    }

    /* ========== TABELA ========== */
    .table-wrapper {
      overflow-x: auto;
      margin-top: 1rem;
      border-radius: var(--radius-sm);
    }
    table {
      width: 100%;
      border-collapse: collapse;
      min-width: 400px;
    }
    td, th {
      border: 1px solid var(--color-border);
      padding: 0.85rem 1rem;
      text-align: left;
    }
    th {
      background: var(--color-bg-alt);
      color: var(--color-primary-dark);
      font-weight: 600;
    }
    tbody tr:nth-child(even) { background: #faf8ff; }
    tbody tr:hover { background: #f0e9fa; }

    /* ========== FOOTER ========== */
    .footer {
      background: var(--color-bg-alt);
      text-align: center;
      padding: 2rem 1.5rem;
      margin-top: 3rem;
      color: var(--color-text-muted);
      border-top: 1px solid var(--color-border);
    }
    .footer__title {
      color: var(--color-primary-dark);
      margin-bottom: 0.5rem;
      font-size: 1.1rem;
    }

    /* ========== RESPONSIVO ========== */
    @media (max-width: 600px) {
      .header { padding: 3rem 1rem; }
      .section { padding: 1.5rem; }
      .cards { grid-template-columns: 1fr; }
      .a11y-controls {
        bottom: 1rem;
        left: 1rem;
      }
      .a11y-btn {
        width: 44px;
        height: 44px;
        font-size: 1.1rem;
      }
    }
  </style>
</head>

<body>

  <!-- Skip link para navegação por teclado -->
  <a href="#main-content" class="skip-link">Pular para o conteúdo principal</a>

  <header class="header" role="banner">
    <h1 class="header__title">☀️ Sensores de Luz e Radiação Solar</h1>
    <p class="header__subtitle">Entendendo como a luz solar pode ser medida e aproveitada.</p>
  </header>

  <nav class="nav" aria-label="Navegação principal">
    <ul class="nav__list">
      <li><a class="nav__link" href="#introducao">Introdução</a></li>
      <li><a class="nav__link" href="#sensores">Sensores</a></li>
      <li><a class="nav__link" href="#intensidade">Intensidade</a></li>
      <li><a class="nav__link" href="#coletor">Coletor Solar</a></li>
      <li><a class="nav__link" href="#limitacoes">Limitações</a></li>
      <li><a class="nav__link" href="#conclusao">Conclusão</a></li>
    </ul>
  </nav>

  <!-- Controles de acessibilidade -->
  <div class="a11y-controls" role="region" aria-label="Controles de acessibilidade">
    <button class="a11y-btn" id="btnContrast" type="button" aria-pressed="false" aria-label="Ativar alto contraste" title="Alto contraste">
      <span aria-hidden="true">◐</span>
    </button>
    <button class="a11y-btn" id="btnFontSize" type="button" aria-pressed="false" aria-label="Aumentar tamanho da fonte" title="Aumentar fonte">
      <span aria-hidden="true">A+</span>
    </button>
  </div>

  <main id="main-content" class="container" role="main">

    <section id="introducao" class="section" aria-labelledby="title-introducao">
      <h2 id="title-introducao" class="section__title">☀️ O que é radiação solar?</h2>

      <p>
        A radiação solar é a energia emitida pelo Sol na forma de
        ondas eletromagnéticas. Ela chega até a Terra e pode ser
        aproveitada para produzir eletricidade e calor.
      </p>

      <p>
        Os sensores de luz são dispositivos que detectam a presença
        e a intensidade da iluminação. Eles ajudam a acompanhar
        a quantidade de luz solar recebida em diferentes locais.
      </p>

      <div class="highlight" role="note">
        <strong>Você sabia?</strong>
        A posição do Sol muda durante o dia. Por isso, a intensidade
        da luz recebida por um painel solar também pode variar.
      </div>
    </section>

    <section id="sensores" class="section" aria-labelledby="title-sensores">
      <h2 id="title-sensores" class="section__title">🔬 Como funcionam os sensores?</h2>

      <div class="cards" role="list">

        <article class="card" role="listitem">
          <span class="card__icon" aria-hidden="true">💡</span>
          <h3 class="card__title">LDR</h3>
          <p>
            O LDR é um resistor dependente de luz.
            Quando recebe mais iluminação, sua resistência elétrica
            geralmente diminui. Quando recebe menos luz,
            sua resistência aumenta.
          </p>
        </article>

        <article class="card" role="listitem">
          <span class="card__icon" aria-hidden="true">📡</span>
          <h3 class="card__title">Fotodiodo</h3>
          <p>
            O fotodiodo transforma a luz recebida em uma corrente
            elétrica. Quanto maior a quantidade de luz,
            maior tende a ser a corrente produzida,
            dentro da faixa de funcionamento do sensor.
          </p>
        </article>

      </div>

      <div class="highlight" role="note">
        <strong>Diferença principal:</strong>
        O LDR varia sua resistência elétrica, enquanto o fotodiodo
        produz uma corrente elétrica relacionada à luz recebida.
      </div>
    </section>

    <section id="intensidade" class="section" aria-labelledby="title-intensidade">
      <h2 id="title-intensidade" class="section__title">📊 Como comparar a intensidade luminosa?</h2>

      <p>
        Podemos colocar sensores em diferentes posições e observar
        a quantidade de luz que cada um recebe.
        Assim, conseguimos identificar os locais mais iluminados.
      </p>

      <div class="table-wrapper">
        <table aria-label="Comparação de intensidade luminosa em diferentes posições">
          <thead>
            <tr>
              <th scope="col">Posição</th>
              <th scope="col">Iluminação</th>
              <th scope="col">Intensidade relativa</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Sol direto</td>
              <td>Alta</td>
              <td>100%</td>
            </tr>
            <tr>
              <td>Sombra parcial</td>
              <td>Média</td>
              <td>50%</td>
            </tr>
            <tr>
              <td>Ambiente fechado</td>
              <td>Baixa</td>
              <td>20%</td>
            </tr>
          </tbody>
        </table>
      </div>

      <p style="margin-top:1rem; font-style: italic; color: var(--color-text-muted);">
        Os valores são exemplos ilustrativos, não medições reais.
      </p>
    </section>

    <section id="coletor" class="section" aria-labelledby="title-coletor">
      <h2 id="title-coletor" class="section__title">🌞 Simulador de intensidade solar</h2>

      <p>
        Movimente a barra para simular diferentes níveis de
        iluminação recebidos por um coletor solar.
      </p>

      <div class="simulator" role="group" aria-label="Simulador de intensidade solar">

        <label class="simulator__label" for="luz">
          Intensidade da iluminação:
        </label>

        <input type="range" id="luz" name="luz"
               min="0" max="100" value="50" step="1"
               aria-valuemin="0" aria-valuemax="100" aria-valuenow="50"
               aria-label="Intensidade da iluminação em porcentagem">

        <div class="simulator__value" id="valor" aria-live="polite">
          50%
        </div>

        <div class="bar" role="progressbar" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100" aria-label="Barra de progresso da intensidade">
          <div class="fill" id="barra"></div>
        </div>

        <h3 class="simulator__situation" id="situacao">🌤️ Iluminação moderada</h3>

        <p id="descricao">
          O coletor recebe uma quantidade intermediária de luz.
        </p>

      </div>

      <h3 class="section__subtitle">Qual é o melhor posicionamento?</h3>

      <p>
        O melhor posicionamento para um coletor solar é aquele
        que permite receber a maior quantidade possível de
        radiação solar durante o período de utilização.
      </p>

      <p>
        Para descobrir esse local, podemos comparar medições
        feitas em diferentes ângulos e posições, durante
        vários horários do dia.
      </p>

      <div class="highlight" role="note">
        <strong>Conclusão:</strong>
        O posicionamento com maior incidência de radiação solar
        tende a favorecer o aproveitamento da energia solar.
      </div>
    </section>

    <section id="limitacoes" class="section" aria-labelledby="title-limitacoes">
      <h2 id="title-limitacoes" class="section__title">⚠️ Quais são as limitações dos sensores?</h2>

      <div class="cards" role="list">

        <article class="card" role="listitem">
          <span class="card__icon" aria-hidden="true">🌥️</span>
          <h3 class="card__title">Condições climáticas</h3>
          <p>
            Nuvens, chuva e neblina alteram a quantidade
            de radiação solar recebida.
          </p>
        </article>

        <article class="card" role="listitem">
          <span class="card__icon" aria-hidden="true">📏</span>
          <h3 class="card__title">Precisão</h3>
          <p>
            Sensores simples podem não fornecer medições
            muito precisas e precisam de calibração.
          </p>
        </article>

        <article class="card" role="listitem">
          <span class="card__icon" aria-hidden="true">🌈</span>
          <h3 class="card__title">Tipo de luz</h3>
          <p>
            Alguns sensores respondem melhor a determinadas
            faixas do espectro eletromagnético.
          </p>
        </article>

        <article class="card" role="listitem">
          <span class="card__icon" aria-hidden="true">🌡️</span>
          <h3 class="card__title">Temperatura</h3>
          <p>
            A temperatura pode alterar o funcionamento
            e as medições de alguns sensores.
          </p>
        </article>

      </div>

      <div class="highlight" role="note">
        <strong>Importante:</strong>
        Medir a intensidade da luz não é o mesmo que medir
        diretamente a energia solar recebida.
        Para medir a irradiância solar com precisão, é indicado
        utilizar instrumentos apropriados, como um piranômetro.
      </div>
    </section>

    <section id="conclusao" class="section" aria-labelledby="title-conclusao">
      <h2 id="title-conclusao" class="section__title">📚 Conclusão</h2>

      <p>
        Os sensores LDR e fotodiodos permitem acompanhar a
        iluminação e comparar diferentes posições em relação
        à incidência solar. Com essas informações, podemos
        investigar qual é o melhor posicionamento para um
        coletor solar.
      </p>

      <p>
        Entretanto, é importante considerar as limitações
        dos sensores e lembrar que a medição da luz não
        representa necessariamente toda a energia solar
        disponível.
      </p>

      <div class="highlight" role="note">
        <strong>Objetivo alcançado:</strong>
        Com o uso de sensores, podemos compreender melhor
        a radiação solar e como aproveitá-la de maneira eficiente.
      </div>
    </section>

  </main>

  <footer class="footer" role="contentinfo">
    <p class="footer__title">☀️ Projeto de Ciências e Tecnologia</p>
    <p>Sensores de Luz e Acompanhamento da Radiação Solar</p>
  </footer>

  <!-- ========== VLIBRAS (WIDGET OFICIAL DO GOVERNO FEDERAL) ========== -->
  <div vw class="enabled">
    <div vw-access-button class="active"></div>
    <div vw-plugin-wrapper>
      <div class="vw-plugin-top-wrapper"></div>
    </div>
  </div>
  <script src="https://vlibras.gov.br/app/vlibras-plugin.js"></script>
  <script>
    new window.VLibras.Widget('https://vlibras.gov.br/app');
  </script>

  <!-- ========== SCRIPTS ========== -->
  <script>
    // ===== Simulador =====
    const luz = document.getElementById("luz");
    const valor = document.getElementById("valor");
    const barra = document.getElementById("barra");
    const situacao = document.getElementById("situacao");
    const descricao = document.getElementById("descricao");
    const progressBar = document.querySelector('.bar');

    function atualizarSimulador() {
      const intensidade = Number(luz.value);

      valor.textContent = intensidade + "%";
      barra.style.width = intensidade + "%";

      // Atualiza ARIA do slider e da barra de progresso
      luz.setAttribute('aria-valuenow', intensidade);
      progressBar.setAttribute('aria-valuenow', intensidade);

      if (intensidade >= 70) {
        situacao.textContent = "☀️ Iluminação alta";
        descricao.textContent =
          "O coletor recebe bastante luz solar e apresenta maior potencial de aproveitamento.";
      } else if (intensidade >= 30) {
        situacao.textContent = "🌤️ Iluminação moderada";
        descricao.textContent =
          "O coletor recebe uma quantidade intermediária de luz.";
      } else {
        situacao.textContent = "☁️ Iluminação baixa";
        descricao.textContent =
          "O coletor recebe pouca luz e pode apresentar menor aproveitamento solar.";
      }
    }

    luz.addEventListener("input", atualizarSimulador);
    atualizarSimulador();

    // ===== Alto Contraste =====
    const btnContrast = document.getElementById('btnContrast');
    const savedContrast = localStorage.getItem('high-contrast') === 'true';

    function aplicarContraste(ativo) {
      if (ativo) {
        document.documentElement.setAttribute('data-contrast', 'high');
        btnContrast.setAttribute('aria-pressed', 'true');
        btnContrast.setAttribute('aria-label', 'Desativar alto contraste');
      } else {
        document.documentElement.removeAttribute('data-contrast');
        btnContrast.setAttribute('aria-pressed', 'false');
        btnContrast.setAttribute('aria-label', 'Ativar alto contraste');
      }
      localStorage.setItem('high-contrast', ativo);
    }

    aplicarContraste(savedContrast);
    btnContrast.addEventListener('click', () => {
      const isHigh = document.documentElement.getAttribute('data-contrast') === 'high';
      aplicarContraste(!isHigh);
    });

    // ===== Aumentar Fonte =====
    const btnFont = document.getElementById('btnFontSize');
    let fontScale = Number(localStorage.getItem('font-scale')) || 1;

    function aplicarFonte() {
      document.documentElement.style.fontSize = (fontScale * 100) + '%';
      btnFont.setAttribute('aria-pressed', fontScale > 1 ? 'true' : 'false');
      localStorage.setItem('font-scale', fontScale);
    }

    aplicarFonte();
    btnFont.addEventListener('click', () => {
      // Alterna entre 100% → 115% → 130% → volta para 100%
      if (fontScale < 1.15) fontScale = 1.15;
      else if (fontScale < 1.3) fontScale = 1.3;
      else fontScale = 1;
      aplicarFonte();
    });
  </script>

</body>
</html>
