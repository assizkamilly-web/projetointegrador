<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Óptica da Visão: Estrutura do Olho</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --accent-color: #3498db;
            --bg-color: #f4f7f6;
            --text-color: #333;
            --card-bg: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--bg-color);
        }

        /* Header */
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 2rem 1rem;
            text-align: center;
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }

        header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* Container Principal */
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        /* Seção do Diagrama */
        .diagram-section {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
            text-align: center;
        }

        .eye-svg {
            width: 100%;
            max-width: 600px;
            height: auto;
        }

        /* Grid de Informações */
        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
        }

        .card {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            transition: transform 0.3s ease;
            border-left: 4px solid var(--accent-color);
        }

        .card:hover {
            transform: translateY(-5px);
        }

        .card h3 {
            color: var(--primary-color);
            margin-bottom: 0.5rem;
            font-size: 1.3rem;
        }

        .card .function {
            font-weight: bold;
            color: var(--accent-color);
            font-size: 0.9rem;
            text-transform: uppercase;
            margin-bottom: 0.5rem;
            display: block;
        }

        /* Seção de Física/Óptica */
        .physics-box {
            background-color: #e8f4fc;
            border: 1px solid #bde0fe;
            padding: 1.5rem;
            border-radius: 8px;
            margin-top: 2rem;
        }

        .physics-box h2 {
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        footer {
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
            color: #666;
            font-size: 0.9rem;
        }

        /* Responsividade */
        @media (max-width: 600px) {
            header h1 { font-size: 1.8rem; }
            .container { padding: 1rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>Óptica da Visão Humana</h1>
        <p>Entendendo a anatomia e a física por trás de como enxergamos</p>
    </header>

    <div class="container">
       
        <!-- Diagrama SVG do Olho -->
        <section class="diagram-section">
            <h2>Corte Transversal do Olho</h2>
            <p style="margin-bottom: 1rem; color: #666;">Esquema simplificado mostrando o caminho da luz</p>
           
            <svg class="eye-svg" viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg">
                <!-- Fundo do Olho (Esclera/Coroide) -->
                <path d="M150,200 Q150,50 300,50 Q450,50 450,200 Q450,350 300,350 Q150,350 150,200 Z" fill="#fff" stroke="#333" stroke-width="3"/>
               
                <!-- Retina (Fundo vermelho/laranja) -->
                <path d="M160,200 Q160,70 300,70 Q440,70 440,200 Q440,330 300,330 Q160,330 160,200" fill="#ffcccc" stroke="none"/>
               
                <!-- Nervo Óptico -->
                <rect x="440" y="185" width="80" height="30" fill="#f1c40f" stroke="#333" stroke-width="2"/>
                <text x="460" y="240" font-size="12" fill="#333">Nervo Óptico</text>

                <!-- Cristalino (Lente) -->
                <ellipse cx="220" cy="200" rx="25" ry="45" fill="#aaddff" stroke="#333" stroke-width="2" opacity="0.8"/>
                <text x="205" y="260" font-size="12" fill="#333">Cristalino</text>

                <!-- Íris e Pupila -->
                <line x1="180" y1="150" x2="180" y2="250" stroke="#8B4513" stroke-width="8"/> <!-- Íris -->
                <circle cx="180" cy="200" r="12" fill="black"/> <!-- Pupila -->
                <text x="140" y="140" font-size="12" fill="#333">Íris/Pupila</text>

                <!-- Córnea -->
                <path d="M180,150 Q140,200 180,250" fill="none" stroke="#3498db" stroke-width="4"/>
                <text x="110" y="200" font-size="12" fill="#333">Córnea</text>

                <!-- Raios de Luz -->
                <line x1="50" y1="160" x2="180" y2="190" stroke="#f1c40f" stroke-width="2" stroke-dasharray="5,5"/>
                <line x1="50" y1="240" x2="180" y2="210" stroke="#f1c40f" stroke-width="2" stroke-dasharray="5,5"/>
               
                <!-- Refração no Cristalino -->
                <line x1="180" y1="190" x2="220" y2="195" stroke="#f1c40f" stroke-width="2" stroke-dasharray="5,5"/>
                <line x1="180" y1="210" x2="220" y2="205" stroke="#f1c40f" stroke-width="2" stroke-dasharray="5,5"/>

                <!-- Foco na Retina -->
                <line x1="220" y1="195" x2="430" y2="200" stroke="#f1c40f" stroke-width="2" stroke-dasharray="5,5"/>
                <line x1="220" y1="205" x2="430" y2="200" stroke="#f1c40f" stroke-width="2" stroke-dasharray="5,5"/>
               
                <circle cx="430" cy="200" r="4" fill="red"/>
                <text x="380" y="180" font-size="12" fill="#333">Imagem Invertida</text>
            </svg>
        </section>

        <!-- Cards de Anatomia -->
        <h2>Estruturas Principais</h2>
        <div class="info-grid">
            <article class="card">
                <span class="function">Proteção e Refração</span>
                <h3>Córnea</h3>
                <p>É a membrana transparente e curva na frente do olho. É a principal lente do sistema óptico, responsável por cerca de 2/3 da refração (focalização) da luz que entra no olho.</p>
            </article>

            <article class="card">
                <span class="function">Controle de Luz</span>
                <h3>Íris e Pupila</h3>
                <p>A <strong>Íris</strong> é a parte colorida que funciona como um diafragma muscular. A <strong>Pupila</strong> é o orifício central. Elas regulam a quantidade de luz que entra: dilatam no escuro e contraem na claridade.</p>
            </article>

            <article class="card">
                <span class="function">Acomodação Visual</span>
                <h3>Cristalino (Lente)</h3>
                <p>Uma lente biconvexa natural e flexível localizada atrás da íris. Ela muda de forma (acomodação) para focar objetos próximos ou distantes, ajustando a distância focal.</p>
            </article>

            <article class="card">
                <span class="function">Meio Transparente</span>
                <h3>Humor Vítreo</h3>
                <p>Substância gelatinosa e transparente que preenche o espaço entre o cristalino e a retina. Mantém a forma esférica do globo ocular e permite a passagem da luz.</p>
            </article>

            <article class="card">
                <span class="function">Sensoriamento</span>
                <h3>Retina</h3>
                <p>Camada de tecido nervoso no fundo do olho. Contém fotorreceptores (<strong>Cones</strong> para cores/detalhes e <strong>Bastonetes</strong> para luz fraca) que convertem luz em impulsos elétricos.</p>
            </article>

            <article class="card">
                <span class="function">Transmissão</span>
                <h3>Nervo Óptico</h3>
                <p>O "cabo" que transporta os sinais elétricos gerados na retina para o cérebro (córtex visual), onde a imagem é processada e interpretada.</p>
            </article>
        </div>

        <!-- Conceitos de Física -->
        <section class="physics-box">
            <h2>⚡ Princípios Ópticos</h2>
            <ul>
                <li><strong>Refração:</strong> A luz sofre desvio ao passar da córnea para o humor aquoso e pelo cristalino. Isso converge os raios luminosos.</li>
                <li><strong>Formação da Imagem:</strong> Na retina, a imagem se forma <strong>real, invertida e menor</strong>. O cérebro corrige essa inversão automaticamente.</li>
                <li><strong>Miopía vs. Hipermetropia:</strong> Erros refrativos onde a imagem foca antes da retina (miopia) ou depois dela (hipermetropia).</li>
            </ul>
        </section>

    </div>

    <footer>
        <p>&copy; 2026 - Material Educativo sobre Óptica da Visão</p>
    </footer>

</body>
</html>
