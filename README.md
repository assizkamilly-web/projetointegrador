<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Óptica do Olho Humano 🌸</title>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --pastel-pink: #FFD6E0;
            --pastel-lavender: #D4C5F9;
            --pastel-mint: #C8F0D8;
            --pastel-peach: #FFDAB9;
            --pastel-yellow: #FFF4B8;
            --pastel-blue: #B8D8F0;
            --text-dark: #3D3D5C;
            --text-light: #6B6B8C;
            --soft-white: #FFFDFB;
            --shadow-soft: rgba(180, 160, 200, 0.25);
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
            top: -50%; left: -50%;
            width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.4) 0%, transparent 70%);
            animation: float 8s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(30px, -30px); }
        }

        header h1 { font-size: 2.8rem; margin-bottom: 0.5rem; position: relative; z-index: 1; font-weight: 600; }
        header p { font-size: 1.1rem; opacity: 0.9; position: relative; z-index: 1; }

        .container { max-width: 1000px; margin: 0 auto; padding: 2rem 1rem; }

        .diagram-section {
            background: var(--soft-white);
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 8px 30px var(--shadow-soft);
            margin-bottom: 2rem;
            text-align: center;
            border: 2px solid var(--pastel-blue);
        }

        .diagram-section h2 { color: var(--text-dark); margin-bottom: 0.5rem; font-weight: 600; }
        .diagram-section .subtitle { color: var(--text-light); margin-bottom: 1.5rem; font-size: 0.95rem; }

        .system-svg { width: 100%; max-width: 600px; height: auto; cursor: pointer; }
        .system-svg .eye-part { transition: all 0.3s; cursor: pointer; }
        .system-svg .eye-part:hover { filter: brightness(1.1); stroke-width: 3; }

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
            font-family: inherit;
        }

        .btn-light:hover { transform: translateY(-3px); box-shadow: 0 6px 20px rgba(255, 218, 185, 0.6); }

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

        .card.visible { opacity: 1; transform: translateY(0); }

        .card:nth-child(1) { border-left-color: var(--pastel-pink); }
        .card:nth-child(2) { border-left-color: var(--pastel-lavender); }
        .card:nth-child(3) { border-left-color: var(--pastel-mint); }
        .card:nth-child(4) { border-left-color: var(--pastel-peach); }
        .card:nth-child(5) { border-left-color: var(--pastel-yellow); }
        .card:nth-child(6) { border-left-color: var(--pastel-blue); }

        .card::before {
            content: '';
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: linear-gradient(135deg, transparent, rgba(255,255,255,0.3));
            opacity: 0;
            transition: opacity 0.4s;
        }

        .card:hover { transform: translateY(-8px); box-shadow: 0 12px 35px var(--shadow-soft); }
        .card:hover::before { opacity: 1; }

        .card h3 { color: var(--text-dark); margin-bottom: 0.5rem; font-size: 1.4rem; font-weight: 600; }

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

        .card p { color: var(--text-dark); }

        .physics-box {
            background: linear-gradient(135deg, var(--pastel-blue), var(--pastel-lavender));
            padding: 2rem;
            border-radius: 20px;
            margin-top: 2rem;
            box-shadow: 0 8px 30px var(--shadow-soft);
        }

        .physics-box h2 { color: var(--text-dark); margin-bottom: 1.2rem; font-weight: 600; }

        .physics-box ul { list-style: none; }

        .physics-box li {
            background: var(--soft-white);
            padding: 1rem 1.2rem;
            margin-bottom: 0.8rem;
            border-radius: 12px;
            box-shadow: 0 2px 10px var(--shadow-soft);
            transition: transform 0.3s;
        }

        .physics-box li:hover { transform: translateX(5px); }
        .physics-box li strong { color: var(--text-dark); }

        .formula {
            background: var(--pastel-yellow);
            padding: 0.8rem 1.2rem;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-weight: 700;
            text-align: center;
            margin: 1rem 0;
            color: var(--text-dark);
            font-size: 1.1rem;
            box-shadow: 0 2px 8px var(--shadow-soft);
        }

        .quiz-section {
            background: var(--soft-white);
            padding: 2rem;
            border-radius: 20px;
            margin-top: 2rem;
            border: 2px solid var(--pastel-pink);
            box-shadow: 0 8px 30px var(--shadow-soft);
        }

        .quiz-section h2 { color: var(--text-dark); margin-bottom: 1rem; }
        .quiz-question { font-size: 1.1rem; margin-bottom: 1rem; font-weight: 600; }

        .quiz-options { display: flex; flex-direction: column; gap: 0.8rem; margin-bottom: 1rem; }

        .quiz-option {
            background: var(--pastel-mint);
            padding: 1rem;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s;
            border: 2px solid transparent;
            font-family: inherit;
            text-align: left;
            font-size: 1rem;
            color: var(--text-dark);
        }

        .quiz-option:hover { transform: scale(1.02); border-color: var(--text-light); }
        .quiz-option.correct { background: #A8E6CF; border-color: #56C596; }
        .quiz-option.wrong { background: #FFB7B2; border-color: #E57373; }
        .quiz-option:disabled { cursor: not-allowed; }

        .quiz-feedback {
            padding: 1rem;
            border-radius: 12px;
            margin-top: 1rem;
            display: none;
            font-weight: 600;
        }

        .quiz-feedback.show { display: block; animation: fadeIn 0.5s; }
        .quiz-feedback.success { background: var(--pastel-mint); color: var(--text-dark); }
        .quiz-feedback.error { background: #FFB7B2; color: var(--text-dark); }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

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

        .tooltip.show { opacity: 1; }

        footer {
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        @media (max-width: 600px) {
            header h1 { font-size: 1.8rem; }
            .container { padding: 1rem; }
            .diagram-section, .physics-box, .quiz-section { padding: 1.2rem; }
        }
    </style>
</head>
<body>

<header>
    <h1>👁️ Óptica do Olho Humano</h1>
    <p>Descubra como a física da luz nos permite enxergar o mundo ✨</p>
</header>

<div class="container">

    <!-- Seção do Diagrama -->
    <section class="diagram-section">
        <h2>Anatomia Óptica do Olho</h2>
        <p class="subtitle">Passe o mouse sobre as estruturas para saber mais</p>
        <svg class="system-svg" viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg">
            <!-- Globo ocular -->
            <ellipse cx="320" cy="200" rx="180" ry="150" fill="#FFE8EE" stroke="#D4C5F9" stroke-width="2"/>

            <!-- Córnea -->
            <path class="eye-part" data-info="Córnea: primeira superfície de refração do olho (n≈1,376). Curvatura fixa responsável por ~2/3 do poder dióptrico."
                  d="M 160 200 Q 140 140 170 100 Q 190 150 180 200 Q 190 250 170 300 Q 140 260 160 200 Z"
                  fill="#B8D8F0" stroke="#6B9BC3" stroke-width="2"/>

            <!-- Câmara anterior (humor aquoso) -->
            <ellipse cx="200" cy="200" rx="30" ry="70" fill="#E6F0FF" opacity="0.7"/>

            <!-- Íris -->
            <path class="eye-part" data-info="Íris: diafragma muscular que controla o diâmetro da pupila, regulando a quantidade de luz que entra no olho."
                  d="M 210 130 Q 220 150 215 170 M 210 270 Q 220 250 215 230"
                  stroke="#8B6BAE" stroke-width="6" fill="none" stroke-linecap="round"/>

            <!-- Pupila -->
            <ellipse class="eye-part" data-info="Pupila: abertura central que permite a passagem da luz. Dilata no escuro e contrai na luz (reflexo pupilar)."
                     cx="215" cy="200" rx="12" ry="30" fill="#3D3D5C"/>

            <!-- Cristalino -->
            <ellipse class="eye-part" data-info="Cristalino: lente biconvexa flexível (n≈1,406). Muda de forma pela acomodação para focalizar objetos próximos e distantes."
                     cx="260" cy="200" rx="25" ry="55"
                     fill="#FFF4B8" stroke="#E6C547" stroke-width="2"/>

            <!-- Humor vítreo -->
            <ellipse cx="380" cy="200" rx="100" ry="110" fill="#F0FFF0" opacity="0.5"/>

            <!-- Retina -->
            <path class="eye-part" data-info="Retina: camada fotossensora onde a imagem real e invertida é formada. Contém cones (cor) e bastonetes (luz fraca)."
                  d="M 470 120 Q 500 200 470 280"
                  stroke="#FFB7B2" stroke-width="8" fill="none" stroke-linecap="round"/>

            <!-- Ponto focal (imagem na retina) -->
            <circle cx="480" cy="200" r="6" fill="#E57373"/>
            <circle cx="480" cy="200" r="12" fill="none" stroke="#E57373" stroke-width="1" opacity="0.5"/>

            <!-- Raios de luz entrando -->
            <line x1="40" y1="120" x2="160" y2="160" stroke="#FFD700" stroke-width="2" stroke-dasharray="5,3"/>
            <line x1="40" y1="200" x2="160" y2="200" stroke="#FFD700" stroke-width="2" stroke-dasharray="5,3"/>
            <line x1="40" y1="280" x2="160" y2="240" stroke="#FFD700" stroke-width="2" stroke-dasharray="5,3"/>

            <!-- Raios refratados até a retina -->
            <line x1="160" y1="160" x2="480" y2="200" stroke="#FFD700" stroke-width="1.5" opacity="0.6"/>
            <line x1="160" y1="200" x2="480" y2="200" stroke="#FFD700" stroke-width="1.5" opacity="0.6"/>
            <line x1="160" y1="240" x2="480" y2="200" stroke="#FFD700" stroke-width="1.5" opacity="0.6"/>

            <!-- Nervos ópticos -->
            <path d="M 495 200 Q 530 200 550 180" stroke="#D4C5F9" stroke-width="3" fill="none"/>

            <!-- Legendas -->
            <text x="100" y="90" font-size="13" fill="#3D3D5C" font-weight="600">Córnea</text>
            <text x="190" y="110" font-size="13" fill="#3D3D5C" font-weight="600">Íris</text>
            <text x="240" y="140" font-size="13" fill="#3D3D5C" font-weight="600">Cristalino</text>
            <text x="440" y="100" font-size="13" fill="#3D3D5C" font-weight="600">Retina</text>
            <text x="30" y="105" font-size="12" fill="#E6C547" font-weight="600">Luz</text>
        </svg>
        <button class="btn-light" onclick="animateLight()">✨ Animar Raios de Luz</button>
    </section>

    <!-- Cards de Informações -->
    <section class="info-grid">
        <div class="card">
            <span class="function">Refração Inicial</span>
            <h3>Córnea</h3>
            <p>Primeira e mais poderosa superfície refratora do olho. Com índice de refração ≈ 1,376 e curvatura fixa, responde por cerca de <strong>+43 dioptrias</strong> do poder óptico total.</p>
        </div>
        <div class="card">
            <span class="function">Lente Ajustável</span>
            <h3>Cristalino</h3>
            <p>Lente biconvexa e flexível que complementa a refração (+20 dioptrias em repouso). Através da <strong>acomodação</strong>, o músculo ciliar altera sua curvatura para focalizar objetos próximos.</p>
        </div>
        <div class="card">
            <span class="function">Sensor de Imagem</span>
            <h3>Retina</h3>
            <p>Camada fotossensora onde se forma uma <strong>imagem real, invertida e menor</strong>. Os fotorreceptores (cones e bastonetes) convertem luz em impulsos nervosos enviados ao cérebro.</p>
        </div>
        <div class="card">
            <span class="function">Controle de Luz</span>
            <h3>Íris e Pupila</h3>
            <p>A íris funciona como o <strong>diafragma</strong> de uma câmera: regula o diâmetro da pupila (de 2 a 8 mm) controlando a quantidade de luz que atinge a retina.</p>
        </div>
        <div class="card">
            <span class="function">Meio Transparente</span>
            <h3>Humor Aquoso e Vítreo</h3>
            <p>Géis transparentes (n≈1,336) que preenchem o olho, mantendo sua forma e permitindo a passagem da luz sem dispersão significativa até a retina.</p>
        </div>
        <div class="card">
            <span class="function">Processamento</span>
            <h3>Nervo Óptico</h3>
            <p>Transporta os sinais elétricos da retina até o <strong>córtex visual</strong>, onde a imagem invertida é "desvirada" e interpretada pelo cérebro como visão consciente.</p>
        </div>
    </section>

    <!-- Seção de Física/Óptica -->
    <section class="physics-box">
        <h2>🔬 Princípios Físicos da Visão</h2>
        <ul>
            <li>
                <strong>Sistema Óptico Composto:</strong> O olho funciona como uma lente convergente com distância focal de aproximadamente <strong>17 mm</strong> (no ar), formando imagem real na retina.
            </li>
            <li>
                <strong>Equação dos Pontos Conjugados (Gauss):</strong>
                <div class="formula">1/f = 1/p + 1/p'</div>
                Onde <em>f</em> é a distância focal, <em>p</em> a distância do objeto e <em>p'</em> a distância da imagem (≈ 24 mm no olho).
            </li>
            <li>
                <strong>Poder Dióptrico Total:</strong> O olho emetropic possui cerca de <strong>+60 dioptrias</strong>, sendo +43 da córnea e +17 do cristalino em acomodação máxima.
            </li>
            <li>
                <strong>Acomodação Visual:</strong> O músculo ciliar ajusta a curvatura do cristalino, variando o poder dióptrico em até <strong>+10 dioptrias</strong> para focalizar objetos próximos (ponto próximo ≈ 25 cm em jovens).
            </li>
            <li>
                <strong>Lei de Snell-Descartes:</strong> A refração ocorre nas interfaces ar/córnea e humor aquoso/cristalino:
                <div class="formula">n₁ · sen(θ₁) = n₂ · sen(θ₂)</div>
            </li>
            <li>
                <strong>Miopia:</strong> Globo ocular alongado → imagem forma-se <em>antes</em> da retina. Corrigida com lente <strong>divergente (côncava)</strong>.
            </li>
            <li>
                <strong>Hipermetropia:</strong> Globo ocular curto → imagem forma-se <em>depois</em> da retina. Corrigida com lente <strong>convergente (convexa)</strong>.
            </li>
            <li>
                <strong>Astigmatismo:</strong> Curvatura irregular da córnea → focos múltiplos. Corrigido com lente <strong>cilíndrica (tórica)</strong>.
            </li>
            <li>
                <strong>Presbiopia:</strong> Perda de elasticidade do cristalino com a idade, reduzindo a acomodação. Corrigida com lentes convergentes para leitura.
            </li>
        </ul>
    </section>

    <!-- Quiz -->
    <section class="quiz-section">
        <h2>🧠 Teste seus Conhecimentos</h2>
        <div class="quiz-question">Qual estrutura é responsável pela maior parte da refração da luz no olho humano?</div>
        <div class="quiz-options">
            <button class="quiz-option" data-correct="false">Cristalino</button>
            <button class="quiz-option" data-correct="true">Córnea</button>
            <button class="quiz-option" data-correct="false">Retina</button>
            <button class="quiz-option" data-correct="false">Íris</button>
        </div>
        <div class="quiz-feedback"></div>
    </section>

</div>

<div class="tooltip" id="tooltip"></div>

<footer>
    <p>✨ Feito com carinho para aprender sobre a física da visão ✨</p>
</footer>

<script>
    // Animação dos cards ao rolar
    const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry, i) => {
            if (entry.isIntersecting) {
                setTimeout(() => entry.target.classList.add('visible'), i * 100);
            }
        });
    }, { threshold: 0.1 });

    document.querySelectorAll('.card').forEach(card => observer.observe(card));

    // Tooltip interativo no SVG
    const tooltip = document.getElementById('tooltip');
    document.querySelectorAll('.eye-part').forEach(part => {
        part.addEventListener('mousemove', (e) => {
            tooltip.textContent = part.dataset.info;
            tooltip.style.left = (e.clientX + 15) + 'px';
            tooltip.style.top = (e.clientY + 15) + 'px';
            tooltip.classList.add('show');
        });
        part.addEventListener('mouseleave', () => {
            tooltip.classList.remove('show');
        });
    });

    // Animação dos raios de luz
    function animateLight() {
        const lines = document.querySelectorAll('.system-svg line[stroke="#FFD700"]');
        lines.forEach((line, i) => {
            line.style.transition = 'opacity 0.3s';
            line.style.opacity = '0';
            setTimeout(() => {
                line.style.opacity = '1';
                line.style.animation = 'fadeIn 0.5s';
            }, i * 100);
        });
    }

    // Quiz interativo
    document.querySelectorAll('.quiz-option').forEach(option => {
        option.addEventListener('click', function() {
            const feedback = document.querySelector('.quiz-feedback');
            const isCorrect = this.dataset.correct === 'true';

            document.querySelectorAll('.quiz-option').forEach(btn => {
                btn.disabled = true;
                if (btn.dataset.correct === 'true') btn.classList.add('correct');
            });

            if (isCorrect) {
                this.classList.add('correct');
                feedback.textContent = '🎉 Correto! A córnea responde por cerca de +43 das +60 dioptrias totais do olho.';
                feedback.className = 'quiz-feedback show success';
            } else {
                this.classList.add('wrong');
                feedback.textContent = '💡 Quase! A córnea, com sua curvatura fixa e diferença de índice de refração ar-tecido, faz a maior parte da refração.';
                feedback.className = 'quiz-feedback show error';
            }
        });
    });
</script>

</body>
</html>
<!-- Seção de Materiais para Experimentos -->
<section class="experiment-section">
    <h2>🧪 Materiais para Experimentos de Óptica</h2>
    <p class="subtitle">Itens essenciais para reproduzir os fenômenos de refração, reflexão e formação de imagens em sala de aula ou em casa.</p>
    
    <div class="experiment-grid">
        <!-- Item 1 -->
        <div class="experiment-card">
            <span class="icon">🔍</span>
            <span class="function" style="background-color: var(--pastel-blue); color: #2A5A6A;">Refração</span>
            <h3>Kit de Lentes</h3>
            <p>Lentes biconvexas (convergentes) e bicôncavas (divergentes) de acrílico ou vidro. Essenciais para demonstrar como a luz se curva e forma imagens reais ou virtuais, simulando o cristalino do olho.</p>
        </div>

        <!-- Item 2 -->
        <div class="experiment-card">
            <span class="icon">🌈</span>
            <span class="function" style="background-color: var(--pastel-pink); color: #7A3A5A;">Dispersão</span>
            <h3>Prisma Óptico</h3>
            <p>Prisma triangular de vidro ou acrílico. Ao atravessá-lo, a luz branca se decompõe no espectro visível (arco-íris), provando que diferentes cores possuem índices de refração ligeiramente diferentes.</p>
        </div>

        <!-- Item 3 -->
        <div class="experiment-card">
            <span class="icon">📏</span>
            <span class="function" style="background-color: var(--pastel-green); color: #2E5A32;">Medição</span>
            <h3>Bancada Óptica</h3>
            <p>Um trilho graduado com suportes deslizantes para fonte de luz, lentes e anteparo (tela). Permite medir com precisão a distância do objeto (<em>p</em>) e da imagem (<em>p'</em>) para validar a Equação de Gauss.</p>
        </div>

        <!-- Item 4 -->
        <div class="experiment-card">
            <span class="icon">🔦</span>
            <span class="function" style="background-color: var(--pastel-yellow); color: #7A6A3A;">Trajetória</span>
            <h3>Ponteiro Laser e Fumaça</h3>
            <p>Um ponteiro laser de baixa potência (verde ou vermelho) fornece um feixe de luz coerente e reto. Usar um pouco de fumaça ou vapor de água no trajeto torna o feixe visível, mostrando a reflexão e refração.</p>
        </div>

        <!-- Item 5 -->
        <div class="experiment-card">
            <span class="icon">💧</span>
            <span class="function" style="background-color: var(--pastel-orange); color: #7A5A3A;">Interface</span>
            <h3>Cuba de Vidro ou Recipiente</h3>
            <p>Recipiente transparente com água. Adicionar algumas gotas de leite ou fluoresceína torna a água levemente turva, permitindo visualizar o feixe de luz mudando de direção ao passar do ar para a água (Lei de Snell).</p>
        </div>

        <!-- Item 6 -->
        <div class="experiment-card">
            <span class="icon">🕶️</span>
            <span class="function" style="background-color: var(--pastel-purple); color: #5A3A7A;">Filtragem</span>
            <h3>Filtros de Cores</h3>
            <p>Lâminas de acetato colorido (vermelho, verde, azul). Usados para estudar a absorção e transmissão seletiva da luz, demonstrando por que os objetos possuem cores específicas sob iluminação branca.</p>
        </div>
    </div>
    
    <div style="text-align: center; margin-top: 30px; background: rgba(255,255,255,0.6); padding: 15px; border-radius: 12px; max-width: 800px; margin-left: auto; margin-right: auto;">
        <p style="margin: 0; color: #5C5C7A; font-size: 0.95rem;">
            💡 <strong>Dica de Segurança:</strong> Ao realizar experimentos com luz, <strong>nunca</strong> aponte lasers diretamente para os olhos. Use óculos de proteção se estiver trabalhando com fontes de luz intensa ou vidro.
        </p>
    </div>
</section>
