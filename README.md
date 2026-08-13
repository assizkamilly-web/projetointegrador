<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AquaSol CEP - Aquecimento Sustentável da Piscina</title>
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

        .system-svg {
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
        <h1>☀️ AquaSol CEP</h1>
        <p>Aquecimento sustentável da piscina através de óptica aplicada e automação inteligente</p>
    </header>

    <div class="container">
       
        <!-- Diagrama SVG do Sistema Solar -->
        <section class="diagram-section">
            <h2>Sistema de Aquecimento Solar</h2>
            <p style="margin-bottom: 1rem; color: var(--text-light);">Clique nos componentes para entender o funcionamento 👇</p>
           
            <svg class="system-svg" viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg">
                <!-- Sol -->
                <circle class="system-part" data-part="sol" cx="100" cy="80" r="50" 
                        fill="#FFF5BA" stroke="#FFDAB9" stroke-width="3" cursor="pointer"/>
                <text x="85" y="85" font-size="14" fill="#5A5A7A" font-weight="600">SOL</text>
               
                <!-- Raios Solares -->
                <line class="light-ray" x1="100" y1="130" x2="250" y2="180" 
                      stroke="#FFF5BA" stroke-width="3" stroke-dasharray="8,4"/>
                <line class="light-ray" x1="130" y1="120" x2="280" y2="170" 
         <!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AquaSol CEP - Aquecimento Sustentável da Piscina</title>
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

        .system-svg {
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
        <h1>☀️ AquaSol CEP</h1>
        <p>Aquecimento sustentável da piscina através de óptica aplicada e automação inteligente</p>
    </header>

    <div class="container">
       
        <!-- Diagrama SVG do Sistema Solar -->
        <section class="diagram-section">
            <h2>Sistema de Aquecimento Solar</h2>
            <p style="margin-bottom: 1rem; color: var(--text-light);">Clique nos componentes para entender o funcionamento 👇</p>
           
            <svg class="system-svg" viewBox="0 0 600 400" xmlns="http://www.w3.org/2000/svg">
                <!-- Sol -->
                <circle class="system-part" data-part="sol" cx="100" cy="80" r="50" 
                        fill="#FFF5BA" stroke="#FFDAB9" stroke-width="3" cursor="pointer"/>
                <text x="85" y="85" font-size="14" fill="#5A5A7A" font-weight="600">SOL</text>
               
                <!-- Raios Solares -->
                <line class="light-ray" x1="100" y1="130" x2="250" y2="180" 
                      stroke="#FFF5BA" stroke-width="3" stroke-dasharray="8,4"/>
                <line class="light-ray" x1="130" y1="120" x2="280" y2="170" 
                      stroke="#FFF5BA" stroke-width="3" stroke-dasharray="8,4"/>
                <line class="light-ray" x1="140" y1="100" x2="300" y2="160" 
                      stroke="#FFF5BA" stroke-width="3" stroke-dasharray="8,4"/>

                <!-- Coletor Solar -->
                <rect class="system-part" data-part="coletor" x="220" y="150" width="180" height="100" 
                      fill="#5A5A7A" stroke="#C8B6FF" stroke-width="3" rx="5" cursor="pointer"/>
                <rect x="230" y="160" width="160" height="80" fill="#2C3E50" opacity="0.8" rx="3"/>
                <text x="260" y="205" font-size="12" fill="#FFFDF9" font-weight="600">Coletor Solar</text>
                <text x="255" y="225" font-size="10" fill="#BFD7EA">(Superfície Absorvedora)</text>

                <!-- Tubulação -->
                <path d="M400,200 Q420,200 420,220 L420,280 Q420,300 440,300 L500,300" 
                      fill="none" stroke="#BFD7EA" stroke-width="8" stroke-linecap="round"/>
                <path d="M220,220 Q200,220 200,240 L200,300 Q200,320 180,320 L120,320" 
                      fill="none" stroke="#FFB7B2" stroke-width="8" stroke-linecap="round"/>

                <!-- Sensor de Temperatura -->
                <circle class="system-part" data-part="sensor" cx="420" cy="250" r="15" 
                        fill="#C1E1C1" stroke="#C8B6FF" stroke-width="2" cursor="pointer"/>
                <text x="405" y="255" font-size="10" fill="#5A5A7A" font-weight="600">T°</text>
                <text x="380" y="275" font-size="10" fill="#8B8BA8">Sensor</text>

                <!-- Controlador/Microcontrolador -->
                <rect class="system-part" data-part="controlador" x="440" y="150" width="80" height="60" 
                      fill="#C8B6FF" stroke="#E0BBE4" stroke-width="2" rx="8" cursor="pointer"/>
                <text x="455" y="185" font-size="10" fill="#5A5A7A" font-weight="600">ESP32</text>
                <text x="450" y="200" font-size="9" fill="#8B8BA8">Controlador</text>

                <!-- Piscina -->
                <path d="M450,280 Q480,260 510,280 T570,280 V350 H450 Z" 
                      fill="#BFD7EA" stroke="#C8B6FF" stroke-width="2" class="system-part" data-part="piscina" cursor="pointer"/>
                <text x="480" y="320" font-size="12" fill="#5A5A7A" font-weight="600">Piscina</text>
                <text x="485" y="335" font-size="10" fill="#8B8BA8">CEP</text>

                <!-- Bomba -->
                <circle class="system-part" data-part="bomba" cx="150" cy="320" r="20" 
                        fill="#FFD1DC" stroke="#C8B6FF" stroke-width="2" cursor="pointer"/>
                <text x="140" y="325" font-size="10" fill="#5A5A7A" font-weight="600">Bomba</text>

                <!-- Setas de fluxo -->
                <path d="M400,200 L410,195 L410,205 Z" fill="#BFD7EA"/>
                <path d="M200,240 L190,235 L190,245 Z" fill="#FFB7B2"/>
            </svg>

            <button class="btn-light" onclick="animateLight()">✨ Animar Fluxo de Energia</button>
        </section>

        <!-- Cards dos Componentes -->
        <h2 style="text-align:center; margin-bottom: 1.5rem; color: var(--text-dark);">Componentes do Sistema</h2>
        <div class="info-grid">
            <article class="card">
                <span class="function">Captação de Energia</span>
                <h3>Coletor Solar</h3>
                <p>Placas com superfície escura mate que absorvem radiação solar em todo o espectro visível e infravermelho. A cor escura maximiza a absorção térmica, convertendo luz em calor.</p>
            </article>

            <article class="card">
                <span class="function">Sensoriamento</span>
                <h3>Sensores de Temperatura</h3>
                <p>Sensores <strong>DS18B20</strong> monitoram a temperatura da água na entrada e saída do coletor em tempo real, fornecendo dados precisos para o sistema de controle.</p>
            </article>

            <article class="card">
                <span class="function">Automação</span>
                <h3>Microcontrolador ESP32</h3>
                <p>Cérebro do sistema que processa dados dos sensores e decide quando acionar a bomba. Implementa lógica de <strong>controle por Delta-T</strong> para máxima eficiência.</p>
            </article>

            <article class="card">
                <span class="function">Circulação</span>
                <h3>Bomba Hidráulica</h3>
                <p>Responsável por circular a água da piscina através dos coletores solares. Controlada por relé via microcontrolador, opera apenas quando há ganho térmico real.</p>
            </article>

            <article class="card">
                <span class="function">Armazenamento</span>
                <h3>Piscina Térmica</h3>
                <p>Corpo d'água que armazena a energia térmica captada. Mantida entre <strong>26°C e 28°C</strong> para conforto e atividades terapêuticas dos alunos.</p>
            </article>

            <article class="card">
                <span class="function">Proteção Térmica</span>
                <h3>Cobertura de Vidro</h3>
                <p>Permite entrada de radiação solar (onda curta) mas bloqueia saída de calor (onda longa), criando <strong>efeito estufa localizado</strong> que aumenta eficiência em até 40%.</p>
            </article>
        </div>

        <!-- Conceitos de Física e Analogias -->
        <section class="physics-box">
            <h2>🔬 Princípios Ópticos e Analogias Científicas</h2>
            <ul>
                <li><strong>Disco de Newton Aplicado:</strong> Assim como o disco decompõe a luz branca em todas as cores do espectro, nossos coletores são projetados para absorver todas essas faixas (comprimentos de onda) sem refletir nenhuma. Cada "cor" do disco de Newton representa energia que é convertida em calor útil para a piscina.</li>
                <li><strong>Câmara Escura Térmica:</strong> O sistema funciona como uma câmara escura invertida: a energia luminosa entra através do vidro (abertura controlada), é convertida em energia térmica nas placas escuras (paredes internas) e permanece confinada no sistema, assim como a imagem se forma e fica contida dentro da câmara escura de orifício.</li>
                <li><strong>Absorção Seletiva:</strong> Superfícies escuras são "corpos negros" que absorvem radiação eletromagnética em todo o espectro visível. Vidro transparente permite passagem de luz (400-700nm) mas bloqueia infravermelho térmico (>700nm), criando uma armadilha de calor eficiente.</li>
                <li><strong>Refração Atmosférica:</strong> Os coletores são instalados com ângulo de 23° (latitude local) para maximizar incidência perpendicular dos raios solares ao meio-dia, compensando a refração atmosférica e otimizando captação energética.</li>
            </ul>
        </section>

        <!-- Seção de Robótica e Programação -->
        <section class="physics-box" style="margin-top: 2rem; background: linear-gradient(135deg, var(--pastel-mint), var(--pastel-lavender));">
            <h2>🤖 Robótica e Controle Automatizado</h2>
            <ul>
                <li><strong>Lógica de Controle:</strong> O microcontrolador lê temperatura do coletor (T_c) e da piscina (T_p). A bomba só é acionada quando: <code>T_c > T_p + 3°C</code> (Delta-T de segurança).</li>
                <li><strong>Proteção Noturna:</strong> Durante a noite, quando T_c < T_p, a bomba permanece desligada para evitar resfriamento da piscina por perda térmica nos coletores.</li>
                <li><strong>Monitoramento Remoto:</strong> Sistema conectado via WiFi permite visualização em tempo real de temperaturas, histórico de operação e consumo energético através de dashboard web acessível.</li>
                <li><strong>Atuadores:</strong> Relés de estado sólido controlam a bomba hidráulica com precisão, evitando picos de corrente e prolongando vida útil do equipamento.</li>
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
        <p>&copy; 2026 - Projeto Integrador CEP: Aquecimento Sustentável da Piscina 🌸</p>
        <p style="margin-top: 0.5rem; font-size: 0.85rem;">Tecnociência • Óptica Aplicada • Robótica • Sustentabilidade</p>
    </footer>

    <script>
        // Dados para o quiz
        const quizData = [
            {
                question: "Por que utilizamos superfícies escuras nos coletores solares?",
                options: [
                    "Para refletir a luz solar e evitar superaquecimento",
                    "Para absorver radiação em todo o espectro visível e infravermelho",
                    "Para combinar esteticamente com a piscina",
                    "Para reduzir o peso do sistema"
                ],
                correct: 1,
                explanation: "Superfícies escuras (corpos negros) absorvem maior quantidade de radiação eletromagnética, convertendo-a eficientemente em energia térmica!"
            },
            {
                question: "Como funciona a analogia da Câmara Escura no sistema de aquecimento?",
                options: [
                    "A luz entra e sai livremente do sistema",
                    "A energia entra, é convertida em calor e permanece confinada no sistema",
                    "O sistema reflete toda a luz de volta",
                    "A câmara escura não tem relação com o projeto"
                ],
                correct: 1,
                explanation: "Assim como na câmara escura a luz entra e fica contida, no coletor a energia solar entra, transforma-se em calor e permanece no sistema!"
            },
            {
                question: "Qual a condição para a bomba ser acionada automaticamente?",
                options: [
                    "Temperatura do coletor igual à da piscina",
                    "Temperatura do coletor menor que a da piscina",
                    "Temperatura do coletor maior que a da piscina + 3°C",
                    "A bomba funciona 24 horas por dia"
                ],
                correct: 2,
                explanation: "O controle por Delta-T garante que a bomba só opere quando há ganho térmico real, evitando desperdício de energia!"
            },
            {
                question: "O que é o efeito estufa localizado nos coletores solares?",
                options: [
                    "Aquecimento global causado pelo sistema",
                    "Vidro permite entrada de luz mas bloqueia saída de calor",
                    "Aumento da temperatura da piscina por produtos químicos",
                    "Reflexão total da luz solar"
                ],
                correct: 1,
                explanation: "O vidro permite passagem de radiação solar (onda curta) mas bloqueia radiação térmica (onda longa), criando uma armadilha de calor eficiente!"
            },
            {
                question: "Por que o sistema desliga a bomba durante a noite?",
                options: [
                    "Para economizar energia elétrica",
                    "Porque não há luz solar suficiente",
                    "Para evitar resfriamento da piscina por perda térmica nos coletores",
                    "Todas as alternativas estão corretas"
                ],
                correct: 3,
                explanation: "Todas as razões são válidas! A proteção noturna evita que os coletores resfriem a piscina quando não há ganho solar!"
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let answered = false;

        // Dados dos tooltips para partes do sistema
        const systemParts = {
            sol: "☀️ SOL: Fonte primária de energia. Radiação solar aquece as placas coletoras.",
            coletor: "🔲 COLETOR SOLAR: Superfície escura que absorve radiação e transfere calor para a água.",
            sensor: "🌡️ SENSOR: Mede temperatura da água em tempo real para controle automático.",
            controlador: "🧠 CONTROLADOR ESP32: Processa dados dos sensores e decide quando acionar a bomba.",
            piscina: "🏊 PISCINA: Armazena água aquecida para uso da comunidade escolar.",
            bomba: "⚙️ BOMBA: Circula água através dos coletores quando há ganho térmico."
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

        // Tooltip para partes do sistema
        function setupTooltips() {
            const tooltip = document.getElementById('tooltip');
            const parts = document.querySelectorAll('.system-part');
            
            parts.forEach(part => {
                part.addEventListener('mouseenter', (e) => {
                    const key = part.dataset.part;
                    tooltip.textContent = systemParts[key];
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
                    alert(systemParts[key]);
                });
            });
        }

        // Animação dos raios de luz e fluxo
        function animateLight() {
            const rays = document.querySelectorAll('.light-ray');
            rays.forEach((ray, index) => {
                ray.style.transition = 'none';
                ray.style.opacity = '0.2';
                
                setTimeout(() => {
                    ray.style.transition = 'opacity 0.8s ease';
                    ray.style.opacity = '1';
                }, index * 200);
            });

            // Animação adicional para mostrar fluxo
            setTimeout(() => {
                alert('✨ Energia solar captada → Convertida em calor → Água aquecida → Piscina pronta para uso!');
            }, 1500);
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
</html>             stroke="#FFF5BA" stroke-width="3" stroke-dasharray="8,4"/>
                <line class="light-ray" x1="140" y1="100" x2="300" y2="160" 
                      stroke="#FFF5BA" stroke-width="3" stroke-dasharray="8,4"/>

                <!-- Coletor Solar -->
                <rect class="system-part" data-part="coletor" x="220" y="150" width="180" height="100" 
                      fill="#5A5A7A" stroke="#C8B6FF" stroke-width="3" rx="5" cursor="pointer"/>
                <rect x="230" y="160" width="160" height="80" fill="#2C3E50" opacity="0.8" rx="3"/>
                <text x="260" y="205" font-size="12" fill="#FFFDF9" font-weight="600">Coletor Solar</text>
                <text x="255" y="225" font-size="10" fill="#BFD7EA">(Superfície Absorvedora)</text>

                <!-- Tubulação -->
                <path d="M400,200 Q420,200 420,220 L420,280 Q420,300 440,300 L500,300" 
                      fill="none" stroke="#BFD7EA" stroke-width="8" stroke-linecap="round"/>
                <path d="M220,220 Q200,220 200,240 L200,300 Q200,320 180,320 L120,320" 
                      fill="none" stroke="#FFB7B2" stroke-width="8" stroke-linecap="round"/>

                <!-- Sensor de Temperatura -->
                <circle class="system-part" data-part="sensor" cx="420" cy="250" r="15" 
                        fill="#C1E1C1" stroke="#C8B6FF" stroke-width="2" cursor="pointer"/>
                <text x="405" y="255" font-size="10" fill="#5A5A7A" font-weight="600">T°</text>
                <text x="380" y="275" font-size="10" fill="#8B8BA8">Sensor</text>

                <!-- Controlador/Microcontrolador -->
                <rect class="system-part" data-part="controlador" x="440" y="150" width="80" height="60" 
                      fill="#C8B6FF" stroke="#E0BBE4" stroke-width="2" rx="8" cursor="pointer"/>
                <text x="455" y="185" font-size="10" fill="#5A5A7A" font-weight="600">ESP32</text>
                <text x="450" y="200" font-size="9" fill="#8B8BA8">Controlador</text>

                <!-- Piscina -->
                <path d="M450,280 Q480,260 510,280 T570,280 V350 H450 Z" 
                      fill="#BFD7EA" stroke="#C8B6FF" stroke-width="2" class="system-part" data-part="piscina" cursor="pointer"/>
                <text x="480" y="320" font-size="12" fill="#5A5A7A" font-weight="600">Piscina</text>
                <text x="485" y="335" font-size="10" fill="#8B8BA8">CEP</text>

                <!-- Bomba -->
                <circle class="system-part" data-part="bomba" cx="150" cy="320" r="20" 
                        fill="#FFD1DC" stroke="#C8B6FF" stroke-width="2" cursor="pointer"/>
                <text x="140" y="325" font-size="10" fill="#5A5A7A" font-weight="600">Bomba</text>

                <!-- Setas de fluxo -->
                <path d="M400,200 L410,195 L410,205 Z" fill="#BFD7EA"/>
                <path d="M200,240 L190,235 L190,245 Z" fill="#FFB7B2"/>
            </svg>

            <button class="btn-light" onclick="animateLight()">✨ Animar Fluxo de Energia</button>
        </section>

        <!-- Cards dos Componentes -->
        <h2 style="text-align:center; margin-bottom: 1.5rem; color: var(--text-dark);">Componentes do Sistema</h2>
        <div class="info-grid">
            <article class="card">
                <span class="function">Captação de Energia</span>
                <h3>Coletor Solar</h3>
                <p>Placas com superfície escura mate que absorvem radiação solar em todo o espectro visível e infravermelho. A cor escura maximiza a absorção térmica, convertendo luz em calor.</p>
            </article>

            <article class="card">
                <span class="function">Sensoriamento</span>
                <h3>Sensores de Temperatura</h3>
                <p>Sensores <strong>DS18B20</strong> monitoram a temperatura da água na entrada e saída do coletor em tempo real, fornecendo dados precisos para o sistema de controle.</p>
            </article>

            <article class="card">
                <span class="function">Automação</span>
                <h3>Microcontrolador ESP32</h3>
                <p>Cérebro do sistema que processa dados dos sensores e decide quando acionar a bomba. Implementa lógica de <strong>controle por Delta-T</strong> para máxima eficiência.</p>
            </article>

            <article class="card">
                <span class="function">Circulação</span>
                <h3>Bomba Hidráulica</h3>
                <p>Responsável por circular a água da piscina através dos coletores solares. Controlada por relé via microcontrolador, opera apenas quando há ganho térmico real.</p>
            </article>

            <article class="card">
                <span class="function">Armazenamento</span>
                <h3>Piscina Térmica</h3>
                <p>Corpo d'água que armazena a energia térmica captada. Mantida entre <strong>26°C e 28°C</strong> para conforto e atividades terapêuticas dos alunos.</p>
            </article>

            <article class="card">
                <span class="function">Proteção Térmica</span>
                <h3>Cobertura de Vidro</h3>
                <p>Permite entrada de radiação solar (onda curta) mas bloqueia saída de calor (onda longa), criando <strong>efeito estufa localizado</strong> que aumenta eficiência em até 40%.</p>
            </article>
        </div>

        <!-- Conceitos de Física e Analogias -->
        <section class="physics-box">
            <h2>🔬 Princípios Ópticos e Analogias Científicas</h2>
            <ul>
                <li><strong>Disco de Newton Aplicado:</strong> Assim como o disco decompõe a luz branca em todas as cores do espectro, nossos coletores são projetados para absorver todas essas faixas (comprimentos de onda) sem refletir nenhuma. Cada "cor" do disco de Newton representa energia que é convertida em calor útil para a piscina.</li>
                <li><strong>Câmara Escura Térmica:</strong> O sistema funciona como uma câmara escura invertida: a energia luminosa entra através do vidro (abertura controlada), é convertida em energia térmica nas placas escuras (paredes internas) e permanece confinada no sistema, assim como a imagem se forma e fica contida dentro da câmara escura de orifício.</li>
                <li><strong>Absorção Seletiva:</strong> Superfícies escuras são "corpos negros" que absorvem radiação eletromagnética em todo o espectro visível. Vidro transparente permite passagem de luz (400-700nm) mas bloqueia infravermelho térmico (>700nm), criando uma armadilha de calor eficiente.</li>
                <li><strong>Refração Atmosférica:</strong> Os coletores são instalados com ângulo de 23° (latitude local) para maximizar incidência perpendicular dos raios solares ao meio-dia, compensando a refração atmosférica e otimizando captação energética.</li>
            </ul>
        </section>

        <!-- Seção de Robótica e Programação -->
        <section class="physics-box" style="margin-top: 2rem; background: linear-gradient(135deg, var(--pastel-mint), var(--pastel-lavender));">
            <h2>🤖 Robótica e Controle Automatizado</h2>
            <ul>
                <li><strong>Lógica de Controle:</strong> O microcontrolador lê temperatura do coletor (T_c) e da piscina (T_p). A bomba só é acionada quando: <code>T_c > T_p + 3°C</code> (Delta-T de segurança).</li>
                <li><strong>Proteção Noturna:</strong> Durante a noite, quando T_c < T_p, a bomba permanece desligada para evitar resfriamento da piscina por perda térmica nos coletores.</li>
                <li><strong>Monitoramento Remoto:</strong> Sistema conectado via WiFi permite visualização em tempo real de temperaturas, histórico de operação e consumo energético através de dashboard web acessível.</li>
                <li><strong>Atuadores:</strong> Relés de estado sólido controlam a bomba hidráulica com precisão, evitando picos de corrente e prolongando vida útil do equipamento.</li>
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
        <p>&copy; 2026 - Projeto Integrador CEP: Aquecimento Sustentável da Piscina 🌸</p>
        <p style="margin-top: 0.5rem; font-size: 0.85rem;">Tecnociência • Óptica Aplicada • Robótica • Sustentabilidade</p>
    </footer>

    <script>
        // Dados para o quiz
        const quizData = [
            {
                question: "Por que utilizamos superfícies escuras nos coletores solares?",
                options: [
                    "Para refletir a luz solar e evitar superaquecimento",
                    "Para absorver radiação em todo o espectro visível e infravermelho",
                    "Para combinar esteticamente com a piscina",
                    "Para reduzir o peso do sistema"
                ],
                correct: 1,
                explanation: "Superfícies escuras (corpos negros) absorvem maior quantidade de radiação eletromagnética, convertendo-a eficientemente em energia térmica!"
            },
            {
                question: "Como funciona a analogia da Câmara Escura no sistema de aquecimento?",
                options: [
                    "A luz entra e sai livremente do sistema",
                    "A energia entra, é convertida em calor e permanece confinada no sistema",
                    "O sistema reflete toda a luz de volta",
                    "A câmara escura não tem relação com o projeto"
                ],
                correct: 1,
                explanation: "Assim como na câmara escura a luz entra e fica contida, no coletor a energia solar entra, transforma-se em calor e permanece no sistema!"
            },
            {
                question: "Qual a condição para a bomba ser acionada automaticamente?",
                options: [
                    "Temperatura do coletor igual à da piscina",
                    "Temperatura do coletor menor que a da piscina",
                    "Temperatura do coletor maior que a da piscina + 3°C",
                    "A bomba funciona 24 horas por dia"
                ],
                correct: 2,
                explanation: "O controle por Delta-T garante que a bomba só opere quando há ganho térmico real, evitando desperdício de energia!"
            },
            {
                question: "O que é o efeito estufa localizado nos coletores solares?",
                options: [
                    "Aquecimento global causado pelo sistema",
                    "Vidro permite entrada de luz mas bloqueia saída de calor",
                    "Aumento da temperatura da piscina por produtos químicos",
                    "Reflexão total da luz solar"
                ],
                correct: 1,
                explanation: "O vidro permite passagem de radiação solar (onda curta) mas bloqueia radiação térmica (onda longa), criando uma armadilha de calor eficiente!"
            },
            {
                question: "Por que o sistema desliga a bomba durante a noite?",
                options: [
                    "Para economizar energia elétrica",
                    "Porque não há luz solar suficiente",
                    "Para evitar resfriamento da piscina por perda térmica nos coletores",
                    "Todas as alternativas estão corretas"
                ],
                correct: 3,
                explanation: "Todas as razões são válidas! A proteção noturna evita que os coletores resfriem a piscina quando não há ganho solar!"
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let answered = false;

        // Dados dos tooltips para partes do sistema
        const systemParts = {
            sol: "☀️ SOL: Fonte primária de energia. Radiação solar aquece as placas coletoras.",
            coletor: "🔲 COLETOR SOLAR: Superfície escura que absorve radiação e transfere calor para a água.",
            sensor: "🌡️ SENSOR: Mede temperatura da água em tempo real para controle automático.",
            controlador: "🧠 CONTROLADOR ESP32: Processa dados dos sensores e decide quando acionar a bomba.",
            piscina: "🏊 PISCINA: Armazena água aquecida para uso da comunidade escolar.",
            bomba: "⚙️ BOMBA: Circula água através dos coletores quando há ganho térmico."
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

        // Tooltip para partes do sistema
        function setupTooltips() {
            const tooltip = document.getElementById('tooltip');
            const parts = document.querySelectorAll('.system-part');
            
            parts.forEach(part => {
                part.addEventListener('mouseenter', (e) => {
                    const key = part.dataset.part;
                    tooltip.textContent = systemParts[key];
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
                    alert(systemParts[key]);
                });
            });
        }

        // Animação dos raios de luz e fluxo
        function animateLight() {
            const rays = document.querySelectorAll('.light-ray');
            rays.forEach((ray, index) => {
                ray.style.transition = 'none';
                ray.style.opacity = '0.2';
                
                setTimeout(() => {
                    ray.style.transition = 'opacity 0.8s ease';
                    ray.style.opacity = '1';
                }, index * 200);
            });

            // Animação adicional para mostrar fluxo
            setTimeout(() => {
                alert('✨ Energia solar captada → Convertida em calor → Água aquecida → Piscina pronta para uso!');
            }, 1500);
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
