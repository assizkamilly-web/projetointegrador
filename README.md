<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Óptica da Visão: Estrutura do Olho</title>
    <style>
        :root {
            --pastel-pink: #FFD1DC;
            --pastel-blue: #BFD7EA;
            --pastel-mint: #C1E1C1;
            --pastel-lavender: #C8B6FF;
            --pastel-peach: #FFDAB9;
            --pastel-yellow: #FFF5BA;
            --pastel-lilac: #E0BBE4;
            --soft-white: #FFFDF9;
            --text-dark: #5A5A7A;
            --text-light: #8B8BA8;
            --shadow-soft: rgba(160, 150, 200, 0.15);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Quicksand', 'Segoe UI', sans-serif;
            line-height: 1.7;
            color: var(--text-dark);
            background: linear-gradient(135deg, #FFF0F5 0%, #E6F0FF 50%, #F0FFF0 100%);
            background-attachment: fixed;
            overflow-x: hidden;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--pastel-pink) 0%, var(--pastel-lavender) 100%);
            color: var(--text-dark);
            padding: 3rem 1rem;
            text-align: center;
            position: relative;
            overflow: hidden;
            box-shadow: 0 4px 20px var(--shadow-soft);
        }

        header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.4) 0%, transparent 70%);
            animation: float 8s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(30px, -30px); }
        }

        header h1 {
            font-size: 2.8rem;
            margin-bottom: 0.5rem;
            position: relative;
            z-index: 1;
            font-weight: 600;
        }

        header p {
            font-size: 1.1rem;
            opacity: 0.9;
            position: relative;
            z-index: 1;
        }

        /* Container Principal */
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        /* Seção do Diagrama */
        .diagram-section {
            background: var(--soft-white);
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 8px 30px var(--shadow-soft);
            margin-bottom: 2rem;
            text-align: center;
            border: 2px solid var(--pastel-blue);
        }

        .diagram-section h2 {
            color: var(--text-dark);
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .eye-svg {
            width: 100%;
            max-width: 600px;
            height: auto;
            cursor: pointer;
        }

        .btn-light {
            background: linear-gradient(135deg, var(--pastel-yellow), var(--pastel-peach));
            color: var(--text-dark);
            border: none;
            padding: 0.8rem 2rem;
            border-radius: 30px;
            font-size: 1rem;
            cursor: pointer;
            margin-top: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255, 218, 185, 0.4);
        }

        .btn-light:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(255, 218, 185, 0.6);
        }

        /* Grid de Informações */
        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .card {
            background: var(--soft-white);
            padding: 1.8rem;
            border-radius: 18px;
            box-shadow: 0 4px 20px var(--shadow-soft);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border-left: 6px solid var(--pastel-lavender);
            opacity: 0;
            transform: translateY(30px);
            position: relative;
            overflow: hidden;
        }

        .card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .card:nth-child(1) { border-left-color: var(--pastel-pink); }
        .card:nth-child(2) { border-left-color: var(--pastel-lavender); }
        .card:nth-child(3) { border-left-color: var(--pastel-mint); }
        .card:nth-child(4) { border-left-color: var(--pastel-peach); }
        .card:nth-child(5) { border-left-color: var(--pastel-yellow); }
        .card:nth-child(6) { border-left-color: var(--pastel-blue); }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, transparent, rgba(255,255,255,0.3));
            opacity: 0;
            transition: opacity 0.4s;
        }

        .card:hover {
            transform: translateY(-8px);
            box-shadow: 0 12px 35px var(--shadow-soft);
        }

        .card:hover::before {
            opacity: 1;
        }

        .card h3 {
            color: var(--text-dark);
            margin-bottom: 0.5rem;
            font-size: 1.4rem;
            font-weight: 600;
        }

        .card .function {
            font-weight: 700;
            color: var(--text-light);
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 0.8rem;
            display: inline-block;
            background: var(--pastel-mint);
            padding: 4px 12px;
            border-radius: 12px;
        }

        .card:nth-child(1) .function { background: var(--pastel-pink); }
        .card:nth-child(2) .function { background: var(--pastel-lavender); color: var(--text-dark); }
        .card:nth-child(3) .function { background: var(--pastel-mint); }
        .card:nth-child(4) .function { background: var(--pastel-peach); }
        .card:nth-child(5) .function { background: var(--pastel-yellow); }
        .card:nth-child(6) .function { background: var(--pastel-blue); }

        .card p {
            color: var(--text-dark);
        }

        /* Seção de Física/Óptica */
        .physics-box {
            background: linear-gradient(135deg, var(--pastel-blue), var(--pastel-lavender));
            padding: 2rem;
            border-radius: 20px;
            margin-top: 2rem;
            box-shadow: 0 8px 30px var(--shadow-soft);
        }

        .physics-box h2 {
            color: var(--text-dark);
            margin-bottom: 1.2rem;
            font-weight: 600;
        }

        .physics-box ul {
            list-style: none;
        }

        .physics-box li {
            background: var(--soft-white);
            padding: 1rem 1.2rem;
            margin-bottom: 0.8rem;
            border-radius: 12px;
            box-shadow: 0 2px 10px var(--shadow-soft);
            transition: transform 0.3s;
        }

        .physics-box li:hover {
            transform: translateX(5px);
        }

        /* Quiz Section */
        .quiz-section {
            background: var(--soft-white);
            padding: 2rem;
            border-radius: 20px;
            margin-top: 2rem;
            border: 2px solid var(--pastel-pink);
            box-shadow: 0 8px 30px var(--shadow-soft);
        }

        .quiz-section h2 {
            color: var(--text-dark);
            margin-bottom: 1rem;
        }

        .quiz-question {
            font-size: 1.1rem;
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .quiz-options {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
            margin-bottom: 1rem;
        }

        .quiz-option {
            background: var(--pastel-mint);
            padding: 1rem;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid transparent;
        }

        .quiz-option:hover {
            transform: scale(1.02);
            border-color: var(--text-light);
        }

        .quiz-option.correct {
            background: #A8E6CF;
            border-color: #56C596;
        }

        .quiz-option.wrong {
            background: #FFB7B2;
            border-color: #E57373;
        }

        .quiz-feedback {
            padding: 1rem;
            border-radius: 12px;
            margin-top: 1rem;
            display: none;
            font-weight: 600;
        }

        .quiz-feedback.show {
            display: block;
            animation: fadeIn 0.5s;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Tooltip */
        .tooltip {
            position: fixed;
            background: var(--soft-white);
            padding: 0.8rem 1.2rem;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.15);
            border: 2px solid var(--pastel-pink);
            pointer-events: none;
            opacity: 0;
            transition: opacity 0.3s;
            z-index: 1000;
            max-width: 250px;
            font-size: 0.9rem;
        }

        .tooltip.show {
            opacity: 1;
        }

        footer {
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        /* Responsividade */
        @media (max-width: 600px) {
            header h1 { font-size: 1.8rem; }
            .container { padding: 1rem; }
            .diagram-section, .physics-box, .quiz-section { padding: 1.2rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>👁️ Óptica da Visão Humana</h1>
        <p>Entendendo a anatomia e a física por trás de como enxergamos</p>
    </header>

    <div class="container">
       
        <!-- Diagrama SVG do Olho -->
        <section class="diagram-section">
            <h2>Corte Transversal do Olho</h2>
            <p style="margin-bottom: 1rem; color: var(--text-light);">Clique nas partes do olho para ver mais detalhes 👇</p>
           
            <svg class="eye-svg" viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg">
                <!-- Fundo do Olho -->
                <path d="M150,200 Q150,50 300,50 Q450,50 450,200 Q450,350 300,350 Q150,350 150,200 Z" 
                      fill="#FFF0F5" stroke="#C8B6FF" stroke-width="3"/>
               
                <!-- Retina -->
                <path d="M160,200 Q160,70 300,70 Q440,70 440,200 Q440,330 300,330 Q160,330 160,200" 
                      fill="#FFD1DC" stroke="none" opacity="0.6"/>
               
                <!-- Nervo Óptico -->
                <rect class="eye-part" data-part="nervo" x="440" y="185" width="80" height="30" 
                      fill="#FFDAB9" stroke="#C8B6FF" stroke-width="2" cursor="pointer"/>
                <text x="460" y="240" font-size="12" fill="#5A5A7A">Nervo Óptico</text>

                <!-- Cristalino -->
                <ellipse class="eye-part" data-part="cristalino" cx="220" cy="200" rx="25" ry="45" 
                         fill="#BFD7EA" stroke="#C8B6FF" stroke-width="2" opacity="0.9" cursor="pointer"/>
                <text x="205" y="260" font-size="12" fill="#5A5A7A">Cristalino</text>

                <!-- Íris e Pupila -->
                <line class="eye-part" data-part="iris" x1="180" y1="150" x2="180" y2="250" 
                      stroke="#E0BBE4" stroke-width="8" cursor="pointer"/>
                <circle cx="180" cy="200" r="12" fill="#5A5A7A"/>
                <text x="140" y="140" font-size="12" fill="#5A5A7A">Íris/Pupila</text>

                <!-- Córnea -->
                <path class="eye-part" data-part="cornea" d="M180,150 Q140,200 180,250" 
                      fill="none" stroke="#C1E1C1" stroke-width="4" cursor="pointer"/>
                <text x="110" y="200" font-size="12" fill="#5A5A7A">Córnea</text>

                <!-- Raios de Luz -->
                <line class="light-ray" x1="50" y1="160" x2="180" y2="190" 
                      stroke="#FFF5BA" stroke-width="2" stroke-dasharray="5,5"/>
                <line class="light-ray" x1="50" y1="240" x2="180" y2="210" 
                      stroke="#FFF5BA" stroke-width="2" stroke-dasharray="5,5"/>
               
                <line class="light-ray" x1="180" y1="190" x2="220" y2="195" 
                      stroke="#FFF5BA" stroke-width="2" stroke-dasharray="5,5"/>
                <line class="light-ray" x1="180" y1="210" x2="220" y2="205" 
                      stroke="#FFF5BA" stroke-width="2" stroke-dasharray="5,5"/>

                <line class="light-ray" x1="220" y1="195" x2="430" y2="200" 
                      stroke="#FFF5BA" stroke-width="2" stroke-dasharray="5,5"/>
                <line class="light-ray" x1="220" y1="205" x2="430" y2="200" 
                      stroke="#FFF5BA" stroke-width="2" stroke-dasharray="5,5"/>
               
                <circle cx="430" cy="200" r="6" fill="#FFB7B2" opacity="0.8"/>
                <text x="380" y="180" font-size="12" fill="#5A5A7A">Imagem Invertida</text>
            </svg>

            <button class="btn-light" onclick="animateLight()">✨ Animar Luz</button>
        </section>

        <!-- Cards de Anatomia -->
        <h2 style="text-align:center; margin-bottom: 1.5rem; color: var(--text-dark);">Estruturas Principais</h2>
        <div class="info-grid">
            <article class="card">
                <span class="function">Proteção e Refração</span>
                <h3>Córnea</h3>
                <p>É a membrana transparente e curva na frente do olho. É a principal lente do sistema óptico, responsável por cerca de 2/3 da refração da luz que entra no olho.</p>
            </article>

            <article class="card">
                <span class="function">Controle de Luz</span>
                <h3>Íris e Pupila</h3>
                <p>A <strong>Íris</strong> é a parte colorida que funciona como um diafragma muscular. A <strong>Pupila</strong> é o orifício central. Elas regulam a quantidade de luz que entra.</p>
            </article>

            <article class="card">
                <span class="function">Acomodação Visual</span>
                <h3>Cristalino (Lente)</h3>
                <p>Uma lente biconvexa natural e flexível localizada atrás da íris. Ela muda de forma para focar objetos próximos ou distantes, ajustando a distância focal.</p>
            </article>

            <article class="card">
                <span class="function">Meio Transparente</span>
                <h3>Humor Vítreo</h3>
                <p>Substância gelatinosa e transparente que preenche o espaço entre o cristalino e a retina. Mantém a forma esférica do globo ocular.</p>
            </article>

            <article class="card">
                <span class="function">Sensoriamento</span>
                <h3>Retina</h3>
                <p>Camada de tecido nervoso no fundo do olho. Contém <strong>Cones</strong> (cores/detalhes) e <strong>Bastonetes</strong> (luz fraca) que convertem luz em impulsos elétricos.</p>
            </article>

            <article class="card">
                <span class="function">Transmissão</span>
                <h3>Nervo Óptico</h3>
                <p>Transporta os sinais elétricos gerados na retina para o cérebro (córtex visual), onde a imagem é processada e interpretada.</p>
            </article>
        </div>

        <!-- Conceitos de Física -->
        <section class="physics-box">
            <h2>⚡ Princípios Ópticos</h2>
            <ul>
                <li><strong>Refração:</strong> A luz sofre desvio ao passar da córnea para o humor aquoso e pelo cristalino, convergindo os raios luminosos.</li>
                <li><strong>Formação da Imagem:</strong> Na retina, a imagem se forma <strong>real, invertida e menor</strong>. O cérebro corrige essa inversão automaticamente.</li>
                <li><strong>Miopia vs. Hipermetropia:</strong> Erros refrativos onde a imagem foca antes da retina (miopia) ou depois dela (hipermetropia).</li>
            </ul>
        </section>

        <!-- Quiz Interativo -->
        <section class="quiz-section">
            <h2>🧠 Teste seus Conhecimentos</h2>
            <div id="quiz-container"></div>
            <div class="quiz-feedback" id="quiz-feedback"></div>
            <button class="btn-light" onclick="nextQuestion()">Próxima Pergunta →</button>
            <p style="margin-top: 1rem; color: var(--text-light);">Pontuação: <span id="score">0</span></p>
        </section>

    </div>

    <div class="tooltip" id="tooltip"></div>

    <footer>
        <p>&copy; 2026 - Material Educativo sobre Óptica da Visão 🌸</p>
    </footer>

    <script>
        // Dados para o quiz
        const quizData = [
            {
                question: "Qual parte do olho é responsável pela maior parte da refração da luz?",
                options: ["Retina", "Córnea", "Íris", "Nervo Óptico"],
                correct: 1,
                explanation: "A córnea é responsável por cerca de 2/3 da refração da luz que entra no olho!"
            },
            {
                question: "Como a imagem se forma na retina?",
                options: ["Virtual e direita", "Real, invertida e menor", "Virtual e ampliada", "Real e direita"],
                correct: 1,
                explanation: "A imagem se forma real, invertida e menor na retina. O cérebro corrige essa inversão!"
            },
            {
                question: "Qual estrutura controla a quantidade de luz que entra no olho?",
                options: ["Cristalino", "Retina", "Íris e Pupila", "Córnea"],
                correct: 2,
                explanation: "A íris funciona como um diafragma, abrindo ou fechando a pupila conforme a luminosidade."
            },
            {
                question: "O que são os cones da retina?",
                options: [
                    "Células para visão noturna",
                    "Células para cores e detalhes",
                    "Parte do nervo óptico",
                    "Uma camada protetora"
                ],
                correct: 1,
                explanation: "Os cones são fotorreceptores responsáveis pela visão em cores e alta acuidade visual!"
            },
            {
                question: "Na miopia, onde a imagem é focalizada?",
                options: [
                    "Diretamente na retina",
                    "Depois da retina",
                    "Antes da retina",
                    "No cristalino"
                ],
                correct: 2,
                explanation: "Na miopia, a imagem se forma antes da retina, causando dificuldade para enxergar de longe."
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let answered = false;

        // Dados dos tooltips para partes do olho
        const eyeParts = {
            cornea: "Córnea: Membrana transparente frontal, responsável por 2/3 da refração!",
            cristalino: "Cristalino: Lente flexível que ajusta o foco (acomodação).",
            iris: "Íris: Parte colorida que controla o tamanho da pupila.",
            nervo: "Nervo Óptico: Transmite sinais elétricos ao cérebro."
        };

        // Inicializar quiz
        function loadQuestion() {
            answered = false;
            const q = quizData[currentQuestion];
            const container = document.getElementById('quiz-container');
            
            container.innerHTML = `
                <div class="quiz-question">${currentQuestion + 1}. ${q.question}</div>
                <div class="quiz-options">
                    ${q.options.map((opt, i) => `
                        <div class="quiz-option" onclick="checkAnswer(${i})">${opt}</div>
                    `).join('')}
                </div>
            `;
            
            document.getElementById('quiz-feedback').classList.remove('show');
        }

        function checkAnswer(selected) {
            if (answered) return;
            answered = true;
            
            const q = quizData[currentQuestion];
            const options = document.querySelectorAll('.quiz-option');
            const feedback = document.getElementById('quiz-feedback');
            
            if (selected === q.correct) {
                options[selected].classList.add('correct');
                score++;
                document.getElementById('score').textContent = score;
                feedback.style.background = '#C1E1C1';
                feedback.textContent = `✅ Correto! ${q.explanation}`;
            } else {
                options[selected].classList.add('wrong');
                options[q.correct].classList.add('correct');
                feedback.style.background = '#FFD1DC';
                feedback.textContent = `❌ Ops! ${q.explanation}`;
            }
            
            feedback.classList.add('show');
        }

        function nextQuestion() {
            if (!answered) return;
            currentQuestion = (currentQuestion + 1) % quizData.length;
            loadQuestion();
        }

        // Animação de entrada dos cards
        function observeCards() {
            const cards = document.querySelectorAll('.card');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach((entry, index) => {
                    if (entry.isIntersecting) {
                        setTimeout(() => {
                            entry.target.classList.add('visible');
                        }, index * 100);
                    }
                });
            }, { threshold: 0.1 });
            
            cards.forEach(card => observer.observe(card));
        }

        // Tooltip para partes do olho
        function setupTooltips() {
            const tooltip = document.getElementById('tooltip');
            const parts = document.querySelectorAll('.eye-part');
            
            parts.forEach(part => {
                part.addEventListener('mouseenter', (e) => {
                    const key = part.dataset.part;
                    tooltip.textContent = eyeParts[key];
                    tooltip.classList.add('show');
                });
                
                part.addEventListener('mousemove', (e) => {
                    tooltip.style.left = e.clientX + 15 + 'px';
                    tooltip.style.top = e.clientY + 15 + 'px';
                });
                
                part.addEventListener('mouseleave', () => {
                    tooltip.classList.remove('show');
                });

                part.addEventListener('click', (e) => {
                    const key = part.dataset.part;
                    alert(eyeParts[key]);
                });
            });
        }

        // Animação dos raios de luz
        function animateLight() {
            const rays = document.querySelectorAll('.light-ray');
            rays.forEach((ray, index) => {
                ray.style.transition = 'none';
                ray.style.opacity = '0.3';
                
                setTimeout(() => {
                    ray.style.transition = 'opacity 0.5s ease';
                    ray.style.opacity = '1';
                }, index * 150);
            });
        }

        // Inicializar tudo quando a página carregar
        document.addEventListener('DOMContentLoaded', () => {
            loadQuestion();
            observeCards();
            setupTooltips();
            
            // Mostrar cards iniciais
            setTimeout(() => {
                document.querySelectorAll('.card').forEach(card => {
                    card.classList.add('visible');
                });
            }, 300);
        });
    </script>

</body>
</html>
