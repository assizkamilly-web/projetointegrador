<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AquaSol CEP - Projeto Integrador</title>
    <!-- Fonte Quicksand para estética suave -->
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600;700&display=swap" rel="stylesheet">
    
    <style>
        /* --- VARIÁVEIS DE CORES E ACESSIBILIDADE --- */
        :root {
            /* Cores Pastéis do Design Original */
            --pastel-pink: #FFD1DC;
            --pastel-lavender: #E6E6FA;
            --pastel-blue: #AEC6CF;
            --pastel-mint: #B5EAD7;
            --pastel-peach: #FFDAC1;
            --pastel-yellow: #FDFD96;
            
            /* Cores de Texto Ajustadas para Contraste (WCAG AA) */
            --text-dark: #2C3E50;      /* Azul Petróleo Escuro - Excelente leitura */
            --text-light: #546E7A;     /* Cinza Azulado - Textos secundários */
            --soft-white: #FFFFFF;     /* Branco puro para cartões */
            --shadow-soft: rgba(44, 62, 80, 0.08);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Quicksand', 'Segoe UI', sans-serif;
            line-height: 1.7;
            color: var(--text-dark);
            background: linear-gradient(135deg, #FFF0F5 0%, #E6F0FF 50%, #F0FFF0 100%);
            background-attachment: fixed;
            overflow-x: hidden;
        }

        /* --- NAVEGAÇÃO ACESSÍVEL --- */
        nav {
            background: rgba(255,255,255,0.9);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            position: sticky; top: 0; z-index: 100;
            display: flex; justify-content: space-between; align-items: center;
            box-shadow: 0 2px 10px var(--shadow-soft);
        }
        .logo { font-weight: 700; font-size: 1.4rem; color: var(--text-dark); text-decoration: none; }
        .nav-links { display: flex; gap: 1.5rem; list-style: none; }
        .nav-links a { text-decoration: none; color: var(--text-dark); font-weight: 600; transition: 0.3s; }
        .nav-links a:hover { color: #88C0D0; }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--pastel-pink) 0%, var(--pastel-lavender) 100%);
            color: var(--text-dark);
            padding: 4rem 1rem;
            text-align: center;
            position: relative;
            overflow: hidden;
            box-shadow: 0 4px 20px var(--shadow-soft);
        }

        header::before {
            content: ''; position: absolute; top: -50%; left: -50%; width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.4) 0%, transparent 70%);
            animation: float 8s ease-in-out infinite;
        }

        @keyframes float { 0%, 100% { transform: translate(0, 0); } 50% { transform: translate(30px, -30px); } }

        header h1 { font-size: 2.8rem; margin-bottom: 0.5rem; position: relative; z-index: 1; font-weight: 700; }
        header p { font-size: 1.2rem; opacity: 0.95; position: relative; z-index: 1; max-width: 700px; margin: 0 auto; }

        /* Container Principal */
        .container { max-width: 1000px; margin: 0 auto; padding: 3rem 1rem; }

        /* Seção do Diagrama (Robótica) */
        .diagram-section {
            background: var(--soft-white); padding: 2.5rem; border-radius: 20px;
            box-shadow: 0 8px 30px var(--shadow-soft); margin-bottom: 3rem; text-align: center;
            border: 2px solid var(--pastel-blue);
        }

        .diagram-section h2 { color: var(--text-dark); margin-bottom: 1rem; font-weight: 700; }
        
        /* SVG Simplificado do Sistema */
        .system-svg { width: 100%; max-width: 600px; height: auto; margin: 1rem 0; }
        .svg-part { transition: all 0.3s ease; cursor: pointer; }
        .svg-part:hover { filter: brightness(0.9); transform: scale(1.02); }

        /* Grid de Informações */
        .info-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; margin-bottom: 3rem; }

        .card {
            background: var(--soft-white); padding: 2rem; border-radius: 18px;
            box-shadow: 0 4px 20px var(--shadow-soft);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border-left: 6px solid var(--pastel-lavender);
            opacity: 0; transform: translateY(30px); position: relative; overflow: hidden;
        }

        .card.visible { opacity: 1; transform: translateY(0); }
        .card:nth-child(1) { border-left-color: var(--pastel-pink); }
        .card:nth-child(2) { border-left-color: var(--pastel-blue); }
        .card:nth-child(3) { border-left-color: var(--pastel-mint); }
        .card:nth-child(4) { border-left-color: var(--pastel-peach); }

        .card:hover { transform: translateY(-8px); box-shadow: 0 12px 35px var(--shadow-soft); }
        .card h3 { color: var(--text-dark); margin-bottom: 0.8rem; font-size: 1.4rem; font-weight: 700; }
        
        .tag {
            display: inline-block; padding: 4px 12px; border-radius: 12px;
            font-size: 0.75rem; font-weight: 700; text-transform: uppercase; letter-spacing: 1px;
            margin-bottom: 1rem; color: var(--text-dark);
        }
        .tag-optica { background: var(--pastel-yellow); }
        .tag-robotica { background: var(--pastel-blue); }
        .tag-social { background: var(--pastel-mint); }

        /* Seção de Física/Óptica (Analogias) */
        .physics-box {
            background: linear-gradient(135deg, var(--pastel-blue), var(--pastel-lavender));
            padding: 2.5rem; border-radius: 20px; margin-top: 2rem;
            box-shadow: 0 8px 30px var(--shadow-soft);
        }
        .physics-box h2 { margin-bottom: 1.5rem; font-weight: 700; }
        .physics-box li {
            background: var(--soft-white); padding: 1.2rem; margin-bottom: 1rem;
            border-radius: 12px; box-shadow: 0 2px 10px var(--shadow-soft);
            transition: transform 0.3s; list-style: none;
        }
        .physics-box li:hover { transform: translateX(8px); }
        .physics-box strong { color: #2980b9; }

        /* Quiz Section */
        .quiz-section {
            background: var(--soft-white); padding: 2.5rem; border-radius: 20px; margin-top: 3rem;
            border: 2px solid var(--pastel-pink); box-shadow: 0 8px 30px var(--shadow-soft);
        }
        .quiz-options { display: flex; flex-direction: column; gap: 0.8rem; margin: 1.5rem 0; }
        .quiz-option {
            background: #f8f9fa; padding: 1rem 1.5rem; border-radius: 12px; cursor: pointer;
            transition: all 0.3s; border: 2px solid transparent; font-weight: 600;
        }
        .quiz-option:hover { background: var(--pastel-mint); transform: scale(1.01); }
        .quiz-option.correct { background: #d4edda; border-color: #c3e6cb; color: #155724; }
        .quiz-option.wrong { background: #f8d7da; border-color: #f5c6cb; color: #721c24; }
        .quiz-feedback { margin-top: 1rem; padding: 1rem; border-radius: 12px; display: none; font-weight: 600; }

        footer { text-align: center; padding: 3rem 1rem; color: var(--text-light); font-size: 0.9rem; }

        /* Responsividade */
        @media (max-width: 600px) {
            header h1 { font-size: 2rem; }
            .nav-links { display: none; } /* Simplificado para mobile */
            .container { padding: 1.5rem 1rem; }
        }
    </style>
</head>
<body>

    <nav aria-label="Navegação Principal">
        <a href="#" class="logo">AquaSol CEP</a>
        <ul class="nav-links">
            <li><a href="#optica">Óptica</a></li>
            <li><a href="#robotica">Robótica</a></li>
            <li><a href="#quiz">Quiz Interativo</a></li>
        </ul>
    </nav>

    <header>
        <h1>Aquecimento Sustentável da Piscina CEP</h1>
        <p>Integração de Óptica Aplicada, Automação Inteligente e Acessibilidade Digital para uma comunidade escolar inclusiva.</p>
    </header>

    <main class="container">
        
        <!-- SEÇÃO ROBÓTICA E DIAGRAMA -->
        <section id="robotica" class="diagram-section" aria-labelledby="robotica-title">
            <h2 id="robotica-title">Automação e Controle Térmico</h2>
            <p style="margin-bottom: 1.5rem; color: var(--text-light);">Passe o mouse ou toque nos componentes para entender o fluxo de automação.</p>
            
            <!-- SVG Interativo Simples -->
            <svg class="system-svg" viewBox="0 0 600 200" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Diagrama do sistema de aquecimento solar automatizado">
                <!-- Sol -->
                <circle cx="80" cy="50" r="30" fill="#FDFD96" class="svg-part" data-info="Radiação Solar: Fonte primária de energia." />
                <!-- Coletor -->
                <rect x="150" y="80" width="120" height="60" rx="5" fill="#2C3E50" class="svg-part" data-info="Coletor Solar: Superfície escura para máxima absorção óptica." />
                <!-- Sensor -->
                <circle cx="320" cy="110" r="15" fill="#FFD1DC" stroke="#2C3E50" stroke-width="2" class="svg-part" data-info="Sensor DS18B20: Mede a temperatura da água em tempo real." />
                <!-- Microcontrolador -->
                <rect x="380" y="70" width="80" height="80" rx="10" fill="#AEC6CF" class="svg-part" data-info="ESP32: Processa dados e decide se liga a bomba." />
                <!-- Piscina -->
                <path d="M500,150 Q530,130 560,150 T620,150 V190 H500 Z" fill="#88C0D0" class="svg-part" data-info="Piscina CEP: Água mantida entre 26°C e 28°C." />
                <!-- Tubulação -->
                <line x1="270" y1="110" x2="305" y2="110" stroke="#546E7A" stroke-width="4" />
                <line x1="335" y1="110" x2="380" y2="110" stroke="#546E7A" stroke-width="4" />
            </svg>
            <div id="diagram-tooltip" style="min-height: 1.5em; font-weight: 600; color: var(--text-dark); margin-top: 1rem;"></div>
        </section>

        <!-- GRID DE CONTEÚDO -->
        <section class="info-grid" aria-label="Detalhes do Projeto">
            <article class="card">
                <span class="tag tag-optica">Óptica</span>
                <h3>Absorção Seletiva</h3>
                <p>Utilizamos placas escuras mate que absorvem todo o espectro visível e infravermelho, minimizando a reflexão e maximizando a conversão térmica.</p>
            </article>
            <article class="card">
                <span class="tag tag-optica">Óptica</span>
                <h3>Efeito Estufa Localizado</h3>
                <p>Cobertura de vidro permite entrada de onda curta (luz) e bloqueia saída de onda longa (calor), aumentando a eficiência em até 40%.</p>
            </article>
            <article class="card">
                <span class="tag tag-robotica">Automação</span>
                <h3>Controle por Delta-T</h3>
                <p>A bomba só ativa quando T_coletor > T_piscina + 3°C. Isso evita resfriamento noturno e desperdício energético.</p>
            </article>
            <article class="card">
                <span class="tag tag-social">Impacto</span>
                <h3>Inclusão Aquática</h3>
                <p>Água térmica possibilita terapia e educação física para alunos com deficiência motora ou sensibilidade térmica.</p>
            </article>
        </section>

        <!-- ANALOGIAS FÍSICAS -->
        <section id="optica" class="physics-box" aria-labelledby="fisica-title">
            <h2 id="fisica-title">🔬 Analogias Científicas Aplicadas</h2>
            <ul>
                <li><strong>Disco de Newton:</strong> Assim como o disco decompõe a luz branca, nosso coletor é projetado para "recompor" essa energia, absorvendo todas as faixas de cores (comprimentos de onda) sem refletir nenhuma, transformando todo o arco-íris em calor útil.</li>
                <li><strong>Câmara Escura:</strong> O sistema funciona como uma câmara escura invertida: a energia luminosa entra por uma abertura controlada (vidro), é convertida em energia térmica nas paredes internas (placas) e permanece confinada no sistema, assim como a imagem se forma e fica contida dentro da câmara.</li>
                <li><strong>Refração:</strong> O ângulo de instalação das placas (23° para Curitiba) considera a refração atmosférica para garantir incidência perpendicular dos raios solares ao meio-dia, maximizando a transferência energética.</li>
            </ul>
        </section>

        <!-- QUIZ INTERATIVO -->
        <section id="quiz" class="quiz-section" aria-labelledby="quiz-title">
            <h2 id="quiz-title">🧠 Teste seu Conhecimento</h2>
            <p class="quiz-question">Por que utilizamos superfícies escuras nos coletores solares?</p>
            <div class="quiz-options" role="radiogroup">
                <div class="quiz-option" onclick="checkAnswer(this, false)">Para refletir a luz solar e evitar superaquecimento.</div>
                <div class="quiz-option" onclick="checkAnswer(this, true)">Para maximizar a absorção de radiação em todo o espectro visível.</div>
                <div class="quiz-option" onclick="checkAnswer(this, false)">Para combinar esteticamente com a piscina do CEP.</div>
            </div>
            <div id="quiz-feedback" class="quiz-feedback" aria-live="polite"></div>
        </section>

    </main>

    <footer>
        <p>Projeto Integrador CEP © 2026 | Tecnociência, Óptica e Robótica Aplicada</p>
        <p style="margin-top: 0.5rem; font-size: 0.8rem;">Desenvolvido com foco em Acessibilidade Digital WCAG AA</p>
    </footer>

    <script>
        // --- ANIMAÇÃO DE SCROLL PARA CARDS ---
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) entry.target.classList.add('visible');
            });
        }, { threshold: 0.1 });
        document.querySelectorAll('.card').forEach(card => observer.observe(card));

        // --- TOOLTIP DO DIAGRAMA SVG ---
        const tooltip = document.getElementById('diagram-tooltip');
        document.querySelectorAll('.svg-part').forEach(part => {
            part.addEventListener('mouseenter', () => {
                tooltip.textContent = part.getAttribute('data-info');
                tooltip.style.opacity = '1';
            });
            part.addEventListener('mouseleave', () => {
                tooltip.textContent = '';
                tooltip.style.opacity = '0.5';
            });
            // Acessibilidade via teclado/foco
            part.setAttribute('tabindex', '0');
            part.addEventListener('focus', () => tooltip.textContent = part.getAttribute('data-info'));
            part.addEventListener('blur', () => tooltip.textContent = '');
        });

        // --- LÓGICA DO QUIZ ---
        function checkAnswer(element, isCorrect) {
            // Resetar estados anteriores
            document.querySelectorAll('.quiz-option').forEach(opt => {
                opt.classList.remove('correct', 'wrong');
            });
            
            const feedback = document.getElementById('quiz-feedback');
            
            if (isCorrect) {
                element.classList.add('correct');
                feedback.textContent = "✅ Correto! Superfícies escuras (corpos negros) absorvem maior quantidade de radiação eletromagnética, convertendo-a em energia térmica.";
                feedback.style.background = "#d4edda";
                feedback.style.color = "#155724";
            } else {
                element.classList.add('wrong');
                feedback.textContent = "❌ Incorreto. Releia a seção sobre Absorção Seletiva e a analogia do Disco de Newton.";
                feedback.style.background = "#f8d7da";
                feedback.style.color = "#721c24";
            }
            feedback.style.display = "block";
        }
    </script>
</body>
</html>
