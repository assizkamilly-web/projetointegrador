<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Página interativa e educativa sobre sensores de luz e radiação solar.">
<meta name="theme-color" content="#6b4f9e">
<title>Sensores de Luz e Radiação Solar</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">

<style>
/* ========== VARIÁVEIS ========== */
:root {
  --primary: #6b4f9e;
  --primary-dark: #4a3575;
  --primary-light: #a58acb;
  --accent: #ff8a65;
  --accent-2: #ffd166;
  --accent-3: #06d6a0;
  --text: #1a1a2e;
  --text-muted: #5a5875;
  --bg: #faf8ff;
  --bg-alt: #f3eef9;
  --card: #ffffff;
  --border: rgba(107, 79, 158, 0.12);
  --focus: #ffd60a;
  --glass: rgba(255, 255, 255, 0.6);
  --glass-border: rgba(255, 255, 255, 0.3);
  --shadow-sm: 0 4px 20px rgba(107, 79, 158, 0.08);
  --shadow-md: 0 10px 40px rgba(107, 79, 158, 0.12);
  --shadow-lg: 0 20px 60px rgba(107, 79, 158, 0.18);
  --radius-sm: 12px;
  --radius-md: 20px;
  --radius-lg: 28px;
  --radius-xl: 40px;
  --transition: 0.35s cubic-bezier(0.4, 0, 0.2, 1);
  --max-width: 1100px;
  --font: 'Plus Jakarta Sans', system-ui, sans-serif;
}

[data-theme="dark"] {
  --text: #f0ecff;
  --text-muted: #b8b3d4;
  --bg: #0f0a1f;
  --bg-alt: #1a1433;
  --card: #1e1740;
  --border: rgba(165, 138, 203, 0.2);
  --glass: rgba(30, 23, 64, 0.6);
  --glass-border: rgba(165, 138, 203, 0.15);
}

/* ========== RESET ========== */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html { scroll-behavior: smooth; }

body {
  font-family: var(--font);
  background: var(--bg);
  color: var(--text);
  line-height: 1.7;
  font-size: 1rem;
  overflow-x: hidden;
  transition: background var(--transition), color var(--transition);
}

/* ========== ACESSIBILIDADE ========== */
.skip-link {
  position: absolute;
  top: -50px;
  left: 0;
  background: var(--primary);
  color: #fff;
  padding: 0.75rem 1.5rem;
  z-index: 1000;
  text-decoration: none;
  font-weight: 600;
  border-radius: 0 0 var(--radius-sm) 0;
  transition: top var(--transition);
}
.skip-link:focus { top: 0; outline: 3px solid var(--focus); }

a:focus-visible, button:focus-visible, input:focus-visible {
  outline: 3px solid var(--focus);
  outline-offset: 3px;
  border-radius: 4px;
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}

/* ========== HERO ========== */
.hero {
  position: relative;
  min-height: 85vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 6rem 1.5rem 4rem;
  overflow: hidden;
  background: linear-gradient(135deg, #d9eaff 0%, #eadfff 50%, #ffe2ec 100%);
}

[data-theme="dark"] .hero {
  background: linear-gradient(135deg, #1a1433 0%, #2d1f5c 50%, #3d1f3d 100%);
}

.hero::before {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(circle at 20% 30%, rgba(255, 209, 102, 0.3), transparent 40%),
    radial-gradient(circle at 80% 70%, rgba(165, 138, 203, 0.3), transparent 40%);
  animation: float 20s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(-30px, 30px) scale(1.1); }
}

.hero__content {
  position: relative;
  z-index: 2;
  max-width: 800px;
}

.hero__badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: var(--glass);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid var(--glass-border);
  padding: 0.5rem 1.25rem;
  border-radius: 50px;
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--primary-dark);
  margin-bottom: 1.5rem;
  box-shadow: var(--shadow-sm);
}

[data-theme="dark"] .hero__badge { color: var(--accent-2); }

.hero__title {
  font-size: clamp(2.25rem, 6vw, 4rem);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 1.5rem;
  background: linear-gradient(135deg, #4a3575, #ff8a65);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  letter-spacing: -0.02em;
}

.hero__subtitle {
  font-size: clamp(1.05rem, 2vw, 1.3rem);
  color: var(--text-muted);
  margin-bottom: 2.5rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.hero__cta {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  background: var(--text);
  color: var(--bg);
  padding: 1rem 2rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 700;
  box-shadow: var(--shadow-md);
  transition: transform var(--transition), box-shadow var(--transition);
}
.hero__cta:hover {
  transform: translateY(-3px);
  box-shadow: var(--shadow-lg);
}
.hero__cta span { transition: transform var(--transition); }
.hero__cta:hover span { transform: translateX(5px); }

/* Sol animado */
.sun {
  position: absolute;
  top: 10%;
  right: 8%;
  width: 120px;
  height: 120px;
  background: radial-gradient(circle, #ffd166 0%, #ff8a65 70%, transparent 100%);
  border-radius: 50%;
  box-shadow: 0 0 80px rgba(255, 209, 102, 0.6), 0 0 120px rgba(255, 138, 101, 0.4);
  animation: pulse 4s ease-in-out infinite;
  z-index: 1;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); opacity: 0.9; }
  50% { transform: scale(1.08); opacity: 1; }
}

/* Raios */
.sun::before, .sun::after {
  content: '';
  position: absolute;
  inset: -20px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 209, 102, 0.3), transparent 70%);
  animation: rays 3s ease-in-out infinite;
}
.sun::after { animation-delay: 1.5s; }

@keyframes rays {
  0%, 100% { transform: scale(1); opacity: 0.5; }
  50% { transform: scale(1.3); opacity: 0.8; }
}

/* Partículas */
.particles {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 1;
}
.particle {
  position: absolute;
  width: 6px;
  height: 6px;
  background: var(--accent-2);
  border-radius: 50%;
  opacity: 0.6;
  animation: particleFloat 15s infinite linear;
}
.particle:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
.particle:nth-child(2) { top: 60%; left: 15%; animation-delay: 3s; background: var(--primary-light); }
.particle:nth-child(3) { top: 30%; left: 85%; animation-delay: 6s; }
.particle:nth-child(4) { top: 70%; left: 75%; animation-delay: 9s; background: var(--accent); }
.particle:nth-child(5) { top: 80%; left: 40%; animation-delay: 12s; background: var(--accent-3); }

@keyframes particleFloat {
  0% { transform: translateY(0) translateX(0); opacity: 0; }
  10% { opacity: 0.6; }
  90% { opacity: 0.6; }
  100% { transform: translateY(-100vh) translateX(50px); opacity: 0; }
}

/* ========== NAVEGAÇÃO ========== */
.nav {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--glass);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
  padding: 1rem;
}
.nav__list {
  max-width: var(--max-width);
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 0.5rem;
  list-style: none;
}
.nav__link {
  color: var(--text);
  text-decoration: none;
  font-weight: 600;
  padding: 0.6rem 1.25rem;
  border-radius: 50px;
  transition: all var(--transition);
  font-size: 0.95rem;
  position: relative;
}
.nav__link:hover {
  background: var(--primary);
  color: #fff;
  transform: translateY(-2px);
}
.nav__link.active {
  background: var(--primary);
  color: #fff;
}

/* ========== CONTAINER ========== */
.container {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 4rem 1.5rem;
}

/* ========== SEÇÕES ========== */
.section {
  margin-bottom: 5rem;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.section.visible {
  opacity: 1;
  transform: translateY(0);
}

.section__header {
  margin-bottom: 2.5rem;
  text-align: center;
}
.section__eyebrow {
  display: inline-block;
  font-size: 0.85rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--primary);
  margin-bottom: 0.75rem;
}
.section__title {
  font-size: clamp(1.75rem, 4vw, 2.5rem);
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 1rem;
  letter-spacing: -0.02em;
}
.section__desc {
  font-size: 1.1rem;
  color: var(--text-muted);
  max-width: 650px;
  margin: 0 auto;
}

/* ========== CARDS GLASSMORPHISM ========== */
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}
.card {
  position: relative;
  padding: 2rem;
  border-radius: var(--radius-lg);
  background: var(--card);
  border: 1px solid var(--border);
  box-shadow: var(--shadow-sm);
  transition: transform var(--transition), box-shadow var(--transition);
  overflow: hidden;
  cursor: pointer;
}
.card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--primary), var(--accent));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform var(--transition);
}
.card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-lg);
}
.card:hover::before { transform: scaleX(1); }

.card__icon-wrap {
  width: 60px;
  height: 60px;
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.75rem;
  margin-bottom: 1.25rem;
  background: linear-gradient(135deg, var(--primary-light), var(--primary));
  color: #fff;
  box-shadow: 0 8px 20px rgba(107, 79, 158, 0.3);
}
.card:nth-child(2) .card__icon-wrap { background: linear-gradient(135deg, #ff8a65, #ff6b6b); box-shadow: 0 8px 20px rgba(255, 138, 101, 0.3); }
.card:nth-child(3) .card__icon-wrap { background: linear-gradient(135deg, #06d6a0, #00b4d8); box-shadow: 0 8px 20px rgba(6, 214, 160, 0.3); }
.card:nth-child(4) .card__icon-wrap { background: linear-gradient(135deg, #ffd166, #ff8a65); box-shadow: 0 8px 20px rgba(255, 209, 102, 0.3); }

.card__title {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: var(--text);
}
.card__text {
  color: var(--text-muted);
  font-size: 0.95rem;
  line-height: 1.6;
}

/* ========== DESTAQUE ========== */
.highlight {
  background: linear-gradient(135deg, var(--primary), var(--primary-dark));
  color: #fff;
  padding: 1.75rem 2rem;
  border-radius: var(--radius-md);
  margin-top: 2rem;
  position: relative;
  overflow: hidden;
  box-shadow: var(--shadow-md);
}
.highlight::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -20%;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(255, 209, 102, 0.3), transparent 70%);
  border-radius: 50%;
}
.highlight strong {
  display: block;
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
  color: var(--accent-2);
  position: relative;
}
.highlight p { position: relative; }

/* ========== SIMULADOR ========== */
.simulator {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-xl);
  padding: 2.5rem;
  box-shadow: var(--shadow-md);
  position: relative;
  overflow: hidden;
}

.simulator__sky {
  position: relative;
  height: 220px;
  background: linear-gradient(to bottom, #87ceeb 0%, #ffd4a3 60%, #ffb088 100%);
  border-radius: var(--radius-md);
  margin-bottom: 2rem;
  overflow: hidden;
  transition: background 0.5s ease;
}

.simulator__sun-visual {
  position: absolute;
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: radial-gradient(circle, #fff5b8 0%, #ffd166 40%, #ff8a65 100%);
  box-shadow: 0 0 60px rgba(255, 209, 102, 0.8), 0 0 120px rgba(255, 138, 101, 0.4);
  transition: all 0.5s ease;
}

.simulator__ground {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 40%;
  background: linear-gradient(to bottom, transparent, rgba(34, 85, 34, 0.3));
}

.simulator__panel {
  position: absolute;
  bottom: 20%;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 60px;
  background: linear-gradient(135deg, #1e3a8a, #3b82f6);
  border: 3px solid #1e293b;
  border-radius: 8px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 2px;
  padding: 4px;
  transition: box-shadow 0.5s ease;
}
.simulator__panel-cell {
  background: rgba(255, 255, 255, 0.15);
  border-radius: 2px;
}

.simulator__controls {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}

.simulator__label {
  font-weight: 600;
  font-size: 1rem;
  color: var(--text);
}

.simulator__slider-wrap {
  width: 100%;
  max-width: 500px;
  position: relative;
}

input[type="range"] {
  -webkit-appearance: none;
  appearance: none;
  width: 100%;
  height: 10px;
  background: linear-gradient(90deg, var(--primary-light), var(--accent-2), var(--accent));
  border-radius: 50px;
  outline: none;
  cursor: pointer;
}
input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 28px;
  height: 28px;
  background: #fff;
  border: 3px solid var(--primary);
  border-radius: 50%;
  cursor: grab;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
  transition: transform 0.2s;
}
input[type="range"]::-webkit-slider-thumb:hover { transform: scale(1.15); }
input[type="range"]::-moz-range-thumb {
  width: 28px;
  height: 28px;
  background: #fff;
  border: 3px solid var(--primary);
  border-radius: 50%;
  cursor: grab;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.simulator__value {
  font-size: clamp(2rem, 5vw, 3rem);
  font-weight: 800;
  background: linear-gradient(135deg, var(--primary), var(--accent));
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-variant-numeric: tabular-nums;
  margin: 0.5rem 0;
}

.simulator__situation {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text);
  margin: 0.5rem 0;
}
.simulator__desc {
  color: var(--text-muted);
  text-align: center;
  max-width: 500px;
  margin: 0 auto;
}

/* ========== GRÁFICO DE BARRAS ========== */
.chart {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 2rem;
  box-shadow: var(--shadow-sm);
  margin-top: 2rem;
}
.chart__title {
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: var(--text);
}
.chart__row {
  display: grid;
  grid-template-columns: 140px 1fr 60px;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1rem;
}
.chart__label {
  font-weight: 600;
  font-size: 0.95rem;
  color: var(--text);
}
.chart__bar {
  height: 32px;
  background: var(--bg-alt);
  border-radius: 50px;
  overflow: hidden;
  position: relative;
}
.chart__fill {
  height: 100%;
  width: 0;
  border-radius: 50px;
  transition: width 1.5s cubic-bezier(0.4, 0, 0.2, 1);
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding-right: 12px;
  color: #fff;
  font-weight: 700;
  font-size: 0.85rem;
}
.chart__fill--high { background: linear-gradient(90deg, #ffd166, #ff8a65); }
.chart__fill--mid { background: linear-gradient(90deg, #a58acb, #6b4f9e); }
.chart__fill--low { background: linear-gradient(90deg, #b8b3d4, #5a5875); }
.chart__percent {
  font-weight: 700;
  color: var(--primary);
  text-align: right;
}

@media (max-width: 500px) {
  .chart__row {
    grid-template-columns: 1fr;
    gap: 0.25rem;
  }
  .chart__percent { text-align: left; }
}

/* ========== ESTATÍSTICAS ========== */
.stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 1.5rem;
  margin: 3rem 0;
}
.stat {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 2rem 1.5rem;
  text-align: center;
  box-shadow: var(--shadow-sm);
  transition: transform var(--transition);
}
.stat:hover { transform: translateY(-5px); }
.stat__number {
  font-size: 2.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, var(--primary), var(--accent));
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1;
  margin-bottom: 0.5rem;
}
.stat__label {
  color: var(--text-muted);
  font-size: 0.9rem;
  font-weight: 500;
}

/* ========== ACORDEÃO ========== */
.accordion {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-top: 2rem;
}
.accordion__item {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  overflow: hidden;
  transition: box-shadow var(--transition);
}
.accordion__item:hover { box-shadow: var(--shadow-sm); }
.accordion__header {
  width: 100%;
  background: none;
  border: none;
  padding: 1.25rem 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  cursor: pointer;
  text-align: left;
  font-family: inherit;
  font-size: 1rem;
  font-weight: 600;
  color: var(--text);
  transition: background var(--transition);
}
.accordion__header:hover { background: var(--bg-alt); }
.accordion__icon {
  width: 40px;
  height: 40px;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--primary-light), var(--primary));
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  flex-shrink: 0;
}
.accordion__title { flex: 1; }
.accordion__arrow {
  width: 24px;
  height: 24px;
  transition: transform var(--transition);
  color: var(--primary);
}
.accordion__item.open .accordion__arrow { transform: rotate(180deg); }
.accordion__content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s ease;
}
.accordion__content-inner {
  padding: 0 1.5rem 1.5rem 4.5rem;
  color: var(--text-muted);
  line-height: 1.7;
}

/* ========== QUIZ ========== */
.quiz {
  background: linear-gradient(135deg, var(--primary), var(--primary-dark));
  color: #fff;
  border-radius: var(--radius-xl);
  padding: 3rem 2rem;
  text-align: center;
  box-shadow: var(--shadow-lg);
  position: relative;
  overflow: hidden;
}
.quiz::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -20%;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(255, 209, 102, 0.2), transparent 70%);
  border-radius: 50%;
}
.quiz__title {
  font-size: clamp(1.5rem, 3vw, 2rem);
  font-weight: 800;
  margin-bottom: 0.5rem;
  position: relative;
}
.quiz__subtitle {
  opacity: 0.9;
  margin-bottom: 2rem;
  position: relative;
}
.quiz__question {
  font-size: 1.15rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  position: relative;
  min-height: 60px;
}
.quiz__options {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 0.75rem;
  max-width: 700px;
  margin: 0 auto 1.5rem;
  position: relative;
}
.quiz__option {
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 2px solid rgba(255, 255, 255, 0.3);
  color: #fff;
  padding: 1rem 1.25rem;
  border-radius: var(--radius-sm);
  cursor: pointer;
  font-family: inherit;
  font-weight: 600;
  font-size: 0.95rem;
  transition: all var(--transition);
  text-align: left;
}
.quiz__option:hover:not(:disabled) {
  background: rgba(255, 255, 255, 0.25);
  transform: translateY(-2px);
}
.quiz__option.correct {
  background: var(--accent-3);
  border-color: var(--accent-3);
  animation: correctPulse 0.5s ease;
}
.quiz__option.wrong {
  background: #ef4444;
  border-color: #ef4444;
  animation: shake 0.5s ease;
}
@keyframes correctPulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}
@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-8px); }
  75% { transform: translateX(8px); }
}
.quiz__feedback {
  min-height: 30px;
  font-weight: 600;
  margin-bottom: 1rem;
  position: relative;
}
.quiz__progress {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  position: relative;
}
.quiz__dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  transition: background var(--transition);
}
.quiz__dot.active { background: var(--accent-2); }
.quiz__dot.correct { background: var(--accent-3); }
.quiz__dot.wrong { background: #ef4444; }
.quiz__btn {
  background: #fff;
  color: var(--primary-dark);
  border: none;
  padding: 0.85rem 2rem;
  border-radius: 50px;
  font-weight: 700;
  cursor: pointer;
  font-family: inherit;
  font-size: 1rem;
  transition: transform var(--transition), box-shadow var(--transition);
  position: relative;
}
.quiz__btn:hover { transform: translateY(-2px); box-shadow: 0 8px 20px rgba(0,0,0,0.2); }
.quiz__btn:disabled { opacity: 0.5; cursor: not-allowed; }
.quiz__score {
  font-size: 3rem;
  font-weight: 800;
  margin: 1rem 0;
  position: relative;
}

/* ========== CONTROLES FLUTUANTES ========== */
.floating-controls {
  position: fixed;
  bottom: 1.5rem;
  right: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  z-index: 999;
}
.fab {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  border: none;
  background: var(--card);
  color: var(--primary);
  cursor: pointer;
  box-shadow: var(--shadow-md);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  font-weight: 700;
  transition: transform var(--transition), background var(--transition);
  border: 2px solid var(--border);
}
.fab:hover {
  transform: scale(1.1) rotate(5deg);
  background: var(--primary);
  color: #fff;
}
.fab[aria-pressed="true"] {
  background: var(--primary);
  color: #fff;
}

/* ========== FOOTER ========== */
.footer {
  background: var(--text);
  color: var(--bg);
  padding: 3rem 1.5rem 2rem;
  text-align: center;
  margin-top: 4rem;
}
[data-theme="dark"] .footer { background: #000; }
.footer__title {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}
.footer__subtitle {
  opacity: 0.7;
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
}
.footer__divider {
  width: 60px;
  height: 3px;
  background: linear-gradient(90deg, var(--accent-2), var(--accent));
  margin: 1.5rem auto;
  border-radius: 50px;
}
.footer__copy {
  font-size: 0.85rem;
  opacity: 0.5;
}

/* ========== RESPONSIVO ========== */
@media (max-width: 768px) {
  .sun { width: 80px; height: 80px; top: 5%; right: 5%; }
  .hero { min-height: 70vh; padding: 5rem 1rem 3rem; }
  .container { padding: 3rem 1rem; }
  .simulator { padding: 1.5rem; }
  .quiz { padding: 2rem 1.25rem; }
  .floating-controls { bottom: 1rem; right: 1rem; }
  .fab { width: 46px; height: 46px; font-size: 1.1rem; }
}
</style>
</head>

<body>

<a href="#main-content" class="skip-link">Pular para o conteúdo principal</a>

<!-- HERO -->
<header class="hero" role="banner">
  <div class="sun" aria-hidden="true"></div>
  <div class="particles" aria-hidden="true">
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
    <div class="particle"></div>
  </div>

  <div class="hero__content">
    <div class="hero__badge">
      <span aria-hidden="true">✨</span>
      Projeto Interativo de Ciências
    </div>
    <h1 class="hero__title">Sensores de Luz<br>e Radiação Solar</h1>
    <p class="hero__subtitle">
      Descubra como a luz solar pode ser medida, simulada e aproveitada
      através de experimentos interativos.
    </p>
    <a href="#introducao" class="hero__cta">
      Começar a explorar
      <span aria-hidden="true">→</span>
    </a>
  </div>
</header>

<!-- NAVEGAÇÃO -->
<nav class="nav" aria-label="Navegação principal">
  <ul class="nav__list">
    <li><a class="nav__link" href="#introducao">Introdução</a></li>
    <li><a class="nav__link" href="#sensores">Sensores</a></li>
    <li><a class="nav__link" href="#intensidade">Intensidade</a></li>
    <li><a class="nav__link" href="#coletor">Simulador</a></li>
    <li><a class="nav__link" href="#limitacoes">Limitações</a></li>
    <li><a class="nav__link" href="#quiz">Quiz</a></li>
  </ul>
</nav>

<main id="main-content">

  <!-- INTRODUÇÃO -->
  <section id="introducao" class="section container" aria-labelledby="title-intro">
    <div class="section__header">
      <span class="section__eyebrow">Conceito básico</span>
      <h2 id="title-intro" class="section__title">☀️ O que é radiação solar?</h2>
      <p class="section__desc">
        A energia do Sol chega até nós de formas que podemos medir e aproveitar.
      </p>
    </div>

    <p style="max-width: 750px; margin: 0 auto 1rem; text-align: center; color: var(--text-muted);">
      A radiação solar é a energia emitida pelo Sol na forma de ondas eletromagnéticas.
      Ela chega até a Terra e pode ser aproveitada para produzir eletricidade e calor.
    </p>
    <p style="max-width: 750px; margin: 0 auto; text-align: center; color: var(--text-muted);">
      Os sensores de luz são dispositivos que detectam a presença e a intensidade da iluminação,
      ajudando a acompanhar a quantidade de luz solar recebida em diferentes locais.
    </p>

    <!-- Estatísticas animadas -->
    <div class="stats">
      <div class="stat">
        <div class="stat__number" data-target="1361">0</div>
        <div class="stat__label">W/m² na atmosfera</div>
      </div>
      <div class="stat">
        <div class="stat__number" data-target="8">0</div>
        <div class="stat__label">min da Terra ao Sol</div>
      </div>
      <div class="stat">
        <div class="stat__number" data-target="100">0</div>
        <div class="stat__label">% energia renovável</div>
      </div>
    </div>

    <div class="highlight" role="note">
      <strong>💡 Você sabia?</strong>
      <p>A posição do Sol muda durante o dia. Por isso, a intensidade da luz recebida por um painel solar também pode variar.</p>
    </div>
  </section>

  <!-- SENSORES -->
  <section id="sensores" class="section container" aria-labelledby="title-sensores">
    <div class="section__header">
      <span class="section__eyebrow">Tecnologia</span>
      <h2 id="title-sensores" class="section__title">🔬 Como funcionam os sensores?</h2>
      <p class="section__desc">
        Clique em cada card para conhecer os principais tipos de sensores de luz.
      </p>
    </div>

    <div class="cards">
      <article class="card" tabindex="0">
        <div class="card__icon-wrap" aria-hidden="true">💡</div>
        <h3 class="card__title">LDR</h3>
        <p class="card__text">
          O LDR é um resistor dependente de luz. Quando recebe mais iluminação,
          sua resistência elétrica geralmente diminui. Quando recebe menos luz,
          sua resistência aumenta.
        </p>
      </article>

      <article class="card" tabindex="0">
        <div class="card__icon-wrap" aria-hidden="true">📡</div>
        <h3 class="card__title">Fotodiodo</h3>
        <p class="card__text">
          O fotodiodo transforma a luz recebida em uma corrente elétrica.
          Quanto maior a quantidade de luz, maior tende a ser a corrente produzida,
          dentro da faixa de funcionamento do sensor.
        </p>
      </article>
    </div>

    <div class="highlight" role="note">
      <strong>🎯 Diferença principal:</strong>
      <p>O LDR varia sua resistência elétrica, enquanto o fotodiodo produz uma corrente elétrica relacionada à luz recebida.</p>
    </div>
  </section>

  <!-- INTENSIDADE -->
  <section id="intensidade" class="section container" aria-labelledby="title-intensidade">
    <div class="section__header">
      <span class="section__eyebrow">Comparação</span>
      <h2 id="title-intensidade" class="section__title">📊 Como comparar a intensidade luminosa?</h2>
      <p class="section__desc">
        Podemos colocar sensores em diferentes posições e observar a quantidade de luz que cada um recebe.
      </p>
    </div>

    <div class="chart" role="figure" aria-label="Gráfico de intensidade luminosa">
      <h3 class="chart__title">Intensidade relativa em diferentes posições</h3>

      <div class="chart__row">
        <span class="chart__label">☀️ Sol direto</span>
        <div class="chart__bar">
          <div class="chart__fill chart__fill--high" data-width="100">Alta</div>
        </div>
        <span class="chart__percent">100%</span>
      </div>

      <div class="chart__row">
        <span class="chart__label">🌤️ Sombra parcial</span>
        <div class="chart__bar">
          <div class="chart__fill chart__fill--mid" data-width="50">Média</div>
        </div>
        <span class="chart__percent">50%</span>
      </div>

      <div class="chart__row">
        <span class="chart__label">🏠 Ambiente fechado</span>
        <div class="chart__bar">
          <div class="chart__fill chart__fill--low" data-width="20">Baixa</div>
        </div>
        <span class="chart__percent">20%</span>
      </div>

      <p style="margin-top: 1.5rem; font-style: italic; color: var(--text-muted); font-size: 0.9rem;">
        * Valores ilustrativos, não representam medições reais.
      </p>
    </div>
  </section>

  <!-- SIMULADOR -->
  <section id="coletor" class="section container" aria-labelledby="title-coletor">
    <div class="section__header">
      <span class="section__eyebrow">Interativo</span>
      <h2 id="title-coletor" class="section__title">🌞 Simulador de intensidade solar</h2>
      <p class="section__desc">
        Arraste o controle para simular diferentes níveis de iluminação recebidos por um coletor solar.
      </p>
    </div>

    <div class="simulator" role="group" aria-label="Simulador de intensidade solar">
      <div class="simulator__sky" id="sky">
        <div class="simulator__sun-visual" id="sunVisual"></div>
        <div class="simulator__ground"></div>
        <div class="simulator__panel" id="panel">
          <div class="simulator__panel-cell"></div>
          <div class="simulator__panel-cell"></div>
          <div class="simulator__panel-cell"></div>
          <div class="simulator__panel-cell"></div>
          <div class="simulator__panel-cell"></div>
          <div class="simulator__panel-cell"></div>
        </div>
      </div>

      <div class="simulator__controls">
        <label class="simulator__label" for="luz">Intensidade da iluminação</label>
        <div class="simulator__slider-wrap">
          <input type="range" id="luz" min="0" max="100" value="50" step="1"
                 aria-valuemin="0" aria-valuemax="100" aria-valuenow="50"
                 aria-label="Intensidade da iluminação em porcentagem">
        </div>
        <div class="simulator__value" id="valor" aria-live="polite">50%</div>
        <h3 class="simulator__situation" id="situacao">🌤️ Iluminação moderada</h3>
        <p class="simulator__desc" id="descricao">
          O coletor recebe uma quantidade intermediária de luz.
        </p>
      </div>
    </div>

    <div class="highlight" role="note" style="margin-top: 2rem;">
      <strong>🎯 Conclusão:</strong>
      <p>O posicionamento com maior incidência de radiação solar tende a favorecer o aproveitamento da energia solar.</p>
    </div>
  </section>

  <!-- LIMITAÇÕES -->
  <section id="limitacoes" class="section container" aria-labelledby="title-limitacoes">
    <div class="section__header">
      <span class="section__eyebrow">Atenção</span>
      <h2 id="title-limitacoes" class="section__title">⚠️ Limitações dos sensores</h2>
      <p class="section__desc">
        Clique em cada item para saber mais sobre as limitações ao medir a luz solar.
      </p>
    </div>

    <div class="accordion">
      <div class="accordion__item">
        <button class="accordion__header" aria-expanded="false">
          <span class="accordion__icon" aria-hidden="true">🌥️</span>
          <span class="accordion__title">Condições climáticas</span>
          <svg class="accordion__arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" aria-hidden="true">
            <path d="M6 9l6 6 6-6"/>
          </svg>
        </button>
        <div class="accordion__content">
          <div class="accordion__content-inner">
            Nuvens, chuva e neblina alteram a quantidade de radiação solar recebida,
            afetando diretamente as medições dos sensores.
          </div>
        </div>
      </div>

      <div class="accordion__item">
        <button class="accordion__header" aria-expanded="false">
          <span class="accordion__icon" aria-hidden="true">📏</span>
          <span class="accordion__title">Precisão</span>
          <svg class="accordion__arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" aria-hidden="true">
            <path d="M6 9l6 6 6-6"/>
          </svg>
        </button>
        <div class="accordion__content">
          <div class="accordion__content-inner">
            Sensores simples podem não fornecer medições muito precisas e precisam
            de calibração constante para resultados confiáveis.
          </div>
        </div>
      </div>

      <div class="accordion__item">
        <button class="accordion__header" aria-expanded="false">
          <span class="accordion__icon" aria-hidden="true">🌈</span>
          <span class="accordion__title">Tipo de luz</span>
          <svg class="accordion__arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" aria-hidden="true">
            <path d="M6 9l6 6 6-6"/>
          </svg>
        </button>
        <div class="accordion__content">
          <div class="accordion__content-inner">
            Alguns sensores respondem melhor a determinadas faixas do espectro
            eletromagnético, o que pode limitar sua aplicação.
          </div>
        </div>
      </div>

      <div class="accordion__item">
        <button class="accordion__header" aria-expanded="false">
          <span class="accordion__icon" aria-hidden="true">🌡️</span>
          <span class="accordion__title">Temperatura</span>
          <svg class="accordion__arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" aria-hidden="true">
            <path d="M6 9l6 6 6-6"/>
          </svg>
        </button>
        <div class="accordion__content">
          <div class="accordion__content-inner">
            A temperatura pode alterar o funcionamento e as medições de alguns
            sensores, exigindo compensação térmica em medições precisas.
          </div>
        </div>
      </div>
    </div>

    <div class="highlight" role="note">
      <strong>⚡ Importante:</strong>
      <p>Medir a intensidade da luz não é o mesmo que medir diretamente a energia solar recebida. Para medições precisas de irradiância, utilize instrumentos apropriados, como um piranômetro.</p>
    </div>
  </section>

  <!-- QUIZ -->
  <section id="quiz" class="section container" aria-labelledby="title-quiz">
    <div class="quiz" role="region" aria-label="Quiz interativo">
      <h2 id="title-quiz" class="quiz__title">🧠 Teste seus conhecimentos</h2>
      <p class="quiz__subtitle">Responda 3 perguntas sobre o que você aprendeu!</p>

      <div class="quiz__progress" id="quizProgress">
        <div class="quiz__dot active"></div>
        <div class="quiz__dot"></div>
        <div class="quiz__dot"></div>
      </div>

      <div class="quiz__question" id="quizQuestion"></div>
      <div class="quiz__options" id="quizOptions"></div>
      <div class="quiz__feedback" id="quizFeedback" aria-live="polite"></div>
      <button class="quiz__btn" id="quizNext" disabled>Próxima →</button>
    </div>
  </section>

</main>

<!-- FOOTER -->
<footer class="footer" role="contentinfo">
  <p class="footer__title">☀️ Projeto de Ciências e Tecnologia</p>
  <p class="footer__subtitle">Sensores de Luz e Acompanhamento da Radiação Solar</p>
  <div class="footer__divider" aria-hidden="true"></div>
  <p class="footer__copy">© 2026 — Desenvolvido com foco em acessibilidade e interatividade</p>
</footer>

<!-- CONTROLES FLUTUANTES -->
<div class="floating-controls" role="region" aria-label="Controles de acessibilidade">
  <button class="fab" id="btnContrast" type="button" aria-pressed="false" aria-label="Alternar modo escuro" title="Modo escuro">
    <span aria-hidden="true">🌙</span>
  </button>
  <button class="fab" id="btnFont" type="button" aria-pressed="false" aria-label="Aumentar tamanho da fonte" title="Aumentar fonte">
    <span aria-hidden="true">A+</span>
  </button>
</div>

<!-- VLIBRAS -->
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

<script>
/* ========== SIMULADOR VISUAL ========== */
const luz = document.getElementById("luz");
const valor = document.getElementById("valor");
const situacao = document.getElementById("situacao");
const descricao = document.getElementById("descricao");
const sky = document.getElementById("sky");
const sunVisual = document.getElementById("sunVisual");
const panel = document.getElementById("panel");

function atualizarSimulador() {
  const i = Number(luz.value);
  valor.textContent = i + "%";
  luz.setAttribute('aria-valuenow', i);

  // Sol visual
  const scale = 0.5 + (i / 100) * 0.8;
  const opacity = 0.3 + (i / 100) * 0.7;
  const glow = 30 + (i / 100) * 90;
  sunVisual.style.transform = `translate(-50%, -50%) scale(${scale})`;
  sunVisual.style.opacity = opacity;
  sunVisual.style.boxShadow = `0 0 ${glow}px rgba(255, 209, 102, 0.8), 0 0 ${glow*1.5}px rgba(255, 138, 101, 0.4)`;

  // Céu
  const skyDark = 100 - i;
  sky.style.background = `linear-gradient(to bottom, 
    hsl(200, 70%, ${30 + i*0.4}%) 0%, 
    hsl(30, 80%, ${40 + i*0.3}%) 60%, 
    hsl(20, 80%, ${50 + i*0.2}%) 100%)`;

  // Painel solar brilho
  const panelGlow = i / 100 * 20;
  panel.style.boxShadow = `0 0 ${panelGlow}px rgba(255, 209, 102, ${i/200})`;

  if (i >= 70) {
    situacao.textContent = "☀️ Iluminação alta";
    descricao.textContent = "O coletor recebe bastante luz solar e apresenta maior potencial de aproveitamento.";
  } else if (i >= 30) {
    situacao.textContent = "🌤️ Iluminação moderada";
    descricao.textContent = "O coletor recebe uma quantidade intermediária de luz.";
  } else {
    situacao.textContent = "☁️ Iluminação baixa";
    descricao.textContent = "O coletor recebe pouca luz e pode apresentar menor aproveitamento solar.";
  }
}

luz.addEventListener("input", atualizarSimulador);
atualizarSimulador();

/* ========== SCROLL REVEAL ========== */
const sections = document.querySelectorAll('.section');
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');

      // Anima gráficos
      entry.target.querySelectorAll('.chart__fill').forEach(fill => {
        const w = fill.dataset.width;
        setTimeout(() => fill.style.width = w + '%', 200);
      });

      // Anima contadores
      entry.target.querySelectorAll('.stat__number').forEach(num => {
        const target = Number(num.dataset.target);
        let current = 0;
        const step = target / 40;
        const timer = setInterval(() => {
          current += step;
          if (current >= target) {
            current = target;
            clearInterval(timer);
          }
          num.textContent = Math.floor(current);
        }, 30);
      });
    }
  });
}, { threshold: 0.15 });

sections.forEach(s => observer.observe(s));

/* ========== NAVEGAÇÃO ATIVA ========== */
const navLinks = document.querySelectorAll('.nav__link');
const sectionIds = Array.from(navLinks).map(l => l.getAttribute('href').substring(1));

window.addEventListener('scroll', () => {
  const scrollPos = window.scrollY + 150;
  sectionIds.forEach((id, i) => {
    const section = document.getElementById(id);
    if (section) {
      const top = section.offsetTop;
      const bottom = top + section.offsetHeight;
      if (scrollPos >= top && scrollPos < bottom) {
        navLinks.forEach(l => l.classList.remove('active'));
        navLinks[i].classList.add('active');
      }
    }
  });
});

/* ========== ACORDEÃO ========== */
document.querySelectorAll('.accordion__header').forEach(header => {
  header.addEventListener('click', () => {
    const item = header.parentElement;
    const content = item.querySelector('.accordion__content');
    const isOpen = item.classList.contains('open');

    // Fecha todos
    document.querySelectorAll('.accordion__item').forEach(i => {
      i.classList.remove('open');
      i.querySelector('.accordion__content').style.maxHeight = null;
      i.querySelector('.accordion__header').setAttribute('aria-expanded', 'false');
    });

    // Abre o clicado
    if (!isOpen) {
      item.classList.add('open');
      content.style.maxHeight = content.scrollHeight + 'px';
      header.setAttribute('aria-expanded', 'true');
    }
  });
});

/* ========== QUIZ ========== */
const quizData = [
  {
    q: "O que acontece com a resistência do LDR quando ele recebe mais luz?",
    options: ["Aumenta", "Diminui", "Permanece igual", "Vira zero"],
    correct: 1
  },
  {
    q: "Qual sensor transforma luz diretamente em corrente elétrica?",
    options: ["LDR", "Termistor", "Fotodiodo", "Resistor"],
    correct: 2
  },
  {
    q: "Em qual posição um coletor solar recebe mais radiação?",
    options: ["Ambiente fechado", "Sombra parcial", "Sol direto", "Noite"],
    correct: 2
  }
];

let currentQ = 0;
let score = 0;
let answered = false;

const quizQuestion = document.getElementById('quizQuestion');
const quizOptions = document.getElementById('quizOptions');
const quizFeedback = document.getElementById('quizFeedback');
const quizNext = document.getElementById('quizNext');
const quizProgress = document.getElementById('quizProgress');

function loadQuestion() {
  answered = false;
  const q = quizData[currentQ];
  quizQuestion.textContent = q.q;
  quizOptions.innerHTML = '';
  quizFeedback.textContent = '';
  quizNext.disabled = true;
  quizNext.textContent = currentQ === quizData.length - 1 ? 'Ver resultado' : 'Próxima →';

  q.options.forEach((opt, i) => {
    const btn = document.createElement('button');
    btn.className = 'quiz__option';
    btn.textContent = opt;
    btn.addEventListener('click', () => selectAnswer(i, btn));
    quizOptions.appendChild(btn);
  });

  // Atualiza dots
  quizProgress.querySelectorAll('.quiz__dot').forEach((dot, i) => {
    dot.classList.remove('active');
    if (i === currentQ) dot.classList.add('active');
  });
}

function selectAnswer(idx, btn) {
  if (answered) return;
  answered = true;
  const correct = quizData[currentQ].correct;
  const options = quizOptions.querySelectorAll('.quiz__option');
  options.forEach(o => o.disabled = true);

  const dot = quizProgress.querySelectorAll('.quiz__dot')[currentQ];

  if (idx === correct) {
    btn.classList.add('correct');
    quizFeedback.textContent = '✅ Correto! Muito bem!';
    quizFeedback.style.color = '#06d6a0';
    score++;
    dot.classList.add('correct');
  } else {
    btn.classList.add('wrong');
    options[correct].classList.add('correct');
    quizFeedback.textContent = '❌ Ops! A resposta correta estava destacada.';
    quizFeedback.style.color = '#ffd166';
    dot.classList.add('wrong');
  }
  quizNext.disabled = false;
}

quizNext.addEventListener('click', () => {
  currentQ++;
  if (currentQ >= quizData.length) {
    showResult();
  } else {
    loadQuestion();
  }
});

function showResult() {
  const percent = Math.round((score / quizData.length) * 100);
  let msg = '';
  if (percent === 100) msg = '🏆 Perfeito! Você dominou o assunto!';
  else if (percent >= 66) msg = '🎉 Muito bom! Você aprendeu bastante!';
  else msg = '📚 Continue estudando, você está no caminho!';

  document.querySelector('.quiz').innerHTML = `
    <h2 class="quiz__title">🎊 Quiz finalizado!</h2>
    <div class="quiz__score">${score}/${quizData.length}</div>
    <p class="quiz__subtitle">${msg}</p>
    <p style="opacity: 0.8; margin: 1rem 0 2rem; position: relative;">
      Você acertou ${percent}% das perguntas.
    </p>
    <button class="quiz__btn" onclick="location.reload()">Tentar novamente</button>
  `;
}

loadQuestion();

/* ========== MODO ESCURO ========== */
const btnContrast = document.getElementById('btnContrast');
const savedTheme = localStorage.getItem('theme');
if (savedTheme === 'dark') {
  document.documentElement.setAttribute('data-theme', 'dark');
  btnContrast.setAttribute('aria-pressed', 'true');
  btnContrast.querySelector('span').textContent = '☀️';
}

btnContrast.addEventListener('click', () => {
  const isDark = document.documentElement.getAttribute('data-theme') === 'dark';
  if (isDark) {
    document.documentElement.removeAttribute('data-theme');
    btnContrast.setAttribute('aria-pressed', 'false');
    btnContrast.querySelector('span').textContent = '🌙';
    localStorage.setItem('theme', 'light');
  } else {
    document.documentElement.setAttribute('data-theme', 'dark');
    btnContrast.setAttribute('aria-pressed', 'true');
    btnContrast.querySelector('span').textContent = '☀️';
    localStorage.setItem('theme', 'dark');
  }
});

/* ========== AUMENTAR FONTE ========== */
const btnFont = document.getElementById('btnFont');
let fontScale = Number(localStorage.getItem('font-scale')) || 1;

function aplicarFonte() {
  document.documentElement.style.fontSize = (fontScale * 100) + '%';
  btnFont.setAttribute('aria-pressed', fontScale > 1 ? 'true' : 'false');
  localStorage.setItem('font-scale', fontScale);
}
aplicarFonte();

btnFont.addEventListener('click', () => {
  if (fontScale < 1.15) fontScale = 1.15;
  else if (fontScale < 1.3) fontScale = 1.3;
  else fontScale = 1;
  aplicarFonte();
});
</script>

</body>
</html>
