<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mundo en Movimiento — Geopolítica Hoy</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Mono:wght@400;500&family=Barlow:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #c9a84c;
    --gold-light: #e8c97a;
    --red: #c0392b;
    --ink: #0d0d0f;
    --surface: #13141a;
    --surface-2: #1c1e28;
    --surface-3: #252838;
    --text: #e8e6df;
    --muted: #8a8980;
    --border: rgba(201,168,76,0.18);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--ink);
    color: var(--text);
    font-family: 'Barlow', sans-serif;
    font-weight: 300;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 0 6vw 8vh;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background: 
      radial-gradient(ellipse 80% 60% at 70% 30%, rgba(201,168,76,0.07) 0%, transparent 60%),
      radial-gradient(ellipse 50% 80% at 10% 80%, rgba(192,57,43,0.08) 0%, transparent 50%),
      linear-gradient(165deg, #0d0d0f 0%, #141520 50%, #0a0b10 100%);
    z-index: -1;
  }

  .hero-grid {
    position: absolute;
    inset: 0;
    background-image: 
      linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
    background-size: 80px 80px;
    z-index: -1;
  }

  .hero-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.25em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 2rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    opacity: 0;
    animation: fadeUp 0.8s ease forwards 0.3s;
  }
  .hero-label::before {
    content: '';
    display: inline-block;
    width: 40px;
    height: 1px;
    background: var(--gold);
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(4rem, 10vw, 9rem);
    font-weight: 900;
    line-height: 0.92;
    letter-spacing: -0.02em;
    color: var(--text);
    max-width: 900px;
    opacity: 0;
    animation: fadeUp 1s ease forwards 0.5s;
  }

  .hero h1 em {
    font-style: normal;
    color: var(--gold);
  }

  .hero-sub {
    margin-top: 2.5rem;
    font-size: 1.05rem;
    font-weight: 400;
    color: var(--muted);
    max-width: 480px;
    line-height: 1.6;
    opacity: 0;
    animation: fadeUp 0.9s ease forwards 0.7s;
  }

  .hero-bar {
    position: absolute;
    right: 6vw;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    opacity: 0;
    animation: fadeIn 1s ease forwards 1s;
  }

  .hero-stat {
    text-align: right;
  }
  .hero-stat span {
    font-family: 'Playfair Display', serif;
    font-size: 3rem;
    font-weight: 700;
    color: var(--gold-light);
    display: block;
    line-height: 1;
  }
  .hero-stat small {
    font-family: 'DM Mono', monospace;
    font-size: 0.62rem;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
  }

  .hero-scroll {
    position: absolute;
    bottom: 3vh;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    opacity: 0;
    animation: fadeIn 1s ease forwards 1.3s;
  }
  .hero-scroll span {
    font-family: 'DM Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
  }
  .hero-scroll-line {
    width: 1px;
    height: 50px;
    background: linear-gradient(to bottom, var(--gold), transparent);
    animation: scrollPulse 2s ease-in-out infinite;
  }

  /* ── NAV ── */
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(13,13,15,0.88);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    padding: 0 6vw;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 60px;
  }

  .nav-brand {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    color: var(--gold);
    text-transform: uppercase;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }
  .nav-links a {
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--gold); }

  /* ── SECTIONS ── */
  section {
    padding: 100px 6vw;
    position: relative;
  }

  .section-tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.25em;
    color: var(--gold);
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1.5rem;
  }
  .section-tag::after {
    content: '';
    flex: 1;
    max-width: 60px;
    height: 1px;
    background: var(--gold);
    opacity: 0.5;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.2rem, 5vw, 4rem);
    font-weight: 700;
    line-height: 1.1;
    letter-spacing: -0.01em;
    margin-bottom: 2.5rem;
    color: var(--text);
  }

  /* ── SECTION 1: DEFINICIÓN ── */
  .def-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .def-body p {
    font-size: 1.1rem;
    color: var(--muted);
    line-height: 1.8;
  }

  .def-body strong { color: var(--text); font-weight: 600; }

  .blockquote {
    border-left: 3px solid var(--gold);
    padding: 2rem 2.5rem;
    margin: 0;
    background: var(--surface-2);
    position: relative;
  }
  .blockquote::before {
    content: '"';
    font-family: 'Playfair Display', serif;
    font-size: 6rem;
    color: var(--gold);
    opacity: 0.15;
    position: absolute;
    top: -1rem;
    left: 1.5rem;
    line-height: 1;
  }
  .blockquote p {
    font-family: 'Playfair Display', serif;
    font-size: 1.25rem;
    font-style: italic;
    color: var(--text);
    line-height: 1.6;
  }

  /* ── SECTION 2: PODER ── */
  .poder-bg { background: var(--surface); }

  .poder-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5px;
    background: var(--border);
    border: 1.5px solid var(--border);
  }

  .poder-card {
    background: var(--surface-2);
    padding: 2.5rem;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .poder-card:hover { background: var(--surface-3); }

  .poder-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--gold), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .poder-card:hover::before { opacity: 1; }

  .poder-num {
    font-family: 'Playfair Display', serif;
    font-size: 4rem;
    font-weight: 900;
    color: var(--gold);
    opacity: 0.12;
    position: absolute;
    top: 1rem;
    right: 1.5rem;
    line-height: 1;
  }

  .poder-icon {
    width: 36px;
    height: 36px;
    border: 1px solid var(--gold);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.5rem;
    color: var(--gold);
    font-size: 0.9rem;
    font-weight: 600;
    font-family: 'DM Mono', monospace;
  }

  .poder-card h3 {
    font-family: 'Barlow', sans-serif;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold-light);
    margin-bottom: 1rem;
  }

  .poder-card p { font-size: 0.95rem; color: var(--muted); line-height: 1.7; }

  /* ── SECTION 3: CHOKE POINTS ── */
  .choke-layout {
    display: grid;
    grid-template-columns: 1fr 480px;
    gap: 5rem;
    align-items: center;
  }

  .choke-list { display: flex; flex-direction: column; gap: 0; }

  .choke-item {
    display: grid;
    grid-template-columns: 3rem 1fr;
    gap: 1.5rem;
    padding: 2rem 0;
    border-bottom: 1px solid var(--border);
    transition: background 0.2s;
    cursor: default;
  }
  .choke-item:first-child { border-top: 1px solid var(--border); }

  .choke-num {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--gold);
    letter-spacing: 0.1em;
    padding-top: 0.3rem;
  }

  .choke-content h3 {
    font-family: 'Barlow', sans-serif;
    font-size: 1rem;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 0.4rem;
  }
  .choke-content p { font-size: 0.9rem; color: var(--muted); }

  .choke-visual {
    aspect-ratio: 1;
    background: var(--surface-2);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
  }

  .choke-visual svg { width: 100%; height: 100%; }

  /* ── SECTION 4: TABLERO ── */
  .tablero-bg { background: var(--surface); }

  .tablero-cards {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--border);
    border: 2px solid var(--border);
    margin-top: 1rem;
  }

  .tablero-card {
    background: var(--ink);
    padding: 3rem;
    position: relative;
    overflow: hidden;
  }

  .tablero-card::after {
    content: '';
    position: absolute;
    bottom: 0; right: 0;
    width: 120px; height: 120px;
    background: radial-gradient(circle, rgba(201,168,76,0.06) 0%, transparent 70%);
  }

  .tablero-card .tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--red);
    margin-bottom: 1.2rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  .tablero-card .tag::before {
    content: '';
    display: inline-block;
    width: 6px; height: 6px;
    background: var(--red);
    border-radius: 50%;
    animation: blink 2s ease-in-out infinite;
  }

  .tablero-card h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 1rem;
    line-height: 1.2;
  }
  .tablero-card p { font-size: 0.95rem; color: var(--muted); line-height: 1.7; }

  /* ── SECTION 5: SUR GLOBAL ── */
  .sur-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .sur-blocks { display: flex; flex-direction: column; gap: 1.5rem; }

  .sur-block {
    padding: 2rem 2rem 2rem 2.5rem;
    border-left: 2px solid var(--gold);
    background: var(--surface-2);
    transition: border-color 0.3s;
  }
  .sur-block:hover { border-color: var(--gold-light); }

  .sur-block h3 {
    font-family: 'Barlow', sans-serif;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.7rem;
  }
  .sur-block p { font-size: 0.95rem; color: var(--muted); }

  .sur-bignum {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    padding-top: 1rem;
  }

  .bignum-item {
    display: flex;
    align-items: flex-end;
    gap: 1.5rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid var(--border);
  }
  .bignum-item:last-child { border-bottom: none; }

  .bignum-val {
    font-family: 'Playfair Display', serif;
    font-size: 4.5rem;
    font-weight: 900;
    line-height: 1;
    color: var(--gold-light);
  }
  .bignum-desc { font-size: 0.9rem; color: var(--muted); line-height: 1.5; max-width: 200px; }

  /* ── SECTION 6: DESAFÍOS ── */
  .challenges-bg { background: var(--surface); }

  .challenges-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    margin-top: 1rem;
  }

  .challenge-card {
    padding: 2.5rem;
    background: var(--ink);
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
  }
  .challenge-card:hover {
    border-color: rgba(201,168,76,0.4);
    transform: translateY(-4px);
  }

  .challenge-accent {
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
  }

  .challenge-card:nth-child(1) .challenge-accent { background: var(--gold); }
  .challenge-card:nth-child(2) .challenge-accent { background: var(--red); }
  .challenge-card:nth-child(3) .challenge-accent { background: #2e7d99; }

  .challenge-icon {
    font-family: 'DM Mono', monospace;
    font-size: 1.8rem;
    color: var(--gold);
    margin-bottom: 1.5rem;
    opacity: 0.7;
  }

  .challenge-card h3 {
    font-family: 'Barlow', sans-serif;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--text);
    margin-bottom: 1rem;
  }
  .challenge-card p { font-size: 0.9rem; color: var(--muted); line-height: 1.7; }

  /* ── FOOTER ── */
  footer {
    padding: 60px 6vw;
    border-top: 1px solid var(--border);
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 2rem;
    align-items: center;
  }

  .footer-brand {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--text);
  }
  .footer-brand span { color: var(--gold); }
  .footer-sub {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
    margin-top: 0.4rem;
  }
  .footer-copy {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.1em;
    color: var(--muted);
    text-transform: uppercase;
    text-align: right;
  }

  /* ── DIVIDER ── */
  .divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    opacity: 0.25;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.2; }
  }
  @keyframes scrollPulse {
    0%, 100% { opacity: 0.3; transform: scaleY(1); }
    50% { opacity: 1; transform: scaleY(1.15); }
  }
  @keyframes dash {
    to { stroke-dashoffset: 0; }
  }

  /* Scroll reveal */
  .reveal {
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-brand">Mundo en Movimiento</div>
  <ul class="nav-links">
    <li><a href="#definicion">Conceptos</a></li>
    <li><a href="#poder">Poder</a></li>
    <li><a href="#chokepoints">Choke Points</a></li>
    <li><a href="#tablero">Tablero</a></li>
    <li><a href="#desafios">Desafíos</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>

  <div class="hero-bar">
    <div class="hero-stat">
      <span>195</span>
      <small>naciones en juego</small>
    </div>
    <div class="hero-stat">
      <span>5</span>
      <small>océanos en disputa</small>
    </div>
    <div class="hero-stat">
      <span>∞</span>
      <small>intereses permanentes</small>
    </div>
  </div>

  <div class="hero-label">Geografía 3.º ESO — Proyecto Escolar 2026</div>
  <h1>El tablero donde juegan<br>las <em>naciones.</em></h1>
  <p class="hero-sub">Un análisis de cómo el espacio, los recursos y el poder dan forma a las relaciones internacionales del siglo XXI.</p>

  <div class="hero-scroll">
    <div class="hero-scroll-line"></div>
    <span>Explorar</span>
  </div>
</div>

<div class="divider"></div>

<!-- SECCIÓN 1: DEFINICIÓN -->
<section id="definicion">
  <div class="def-layout">
    <div class="def-body reveal">
      <div class="section-tag">01 — Concepto</div>
      <h2 class="section-title">¿Qué es la<br>Geopolítica?</h2>
      <p>La <strong>geopolítica</strong> es el estudio de cómo el espacio geográfico —territorio, recursos naturales, clima y ubicación estratégica— influye en el poder político y las relaciones internacionales entre estados.</p>
      <br>
      <p>No es simplemente "política exterior". Es entender por qué un país necesita controlar un estrecho marítimo específico, o por qué una cordillera montañosa puede ser una frontera infranqueable durante siglos.</p>
    </div>
    <blockquote class="blockquote reveal reveal-delay-2">
      <p>"Las naciones no tienen amigos permanentes, solo intereses permanentes."</p>
    </blockquote>
  </div>
</section>

<div class="divider"></div>

<!-- SECCIÓN 2: PODER -->
<section id="poder" class="poder-bg">
  <div class="section-tag reveal">02 — Fundamentos</div>
  <h2 class="section-title reveal">Elementos Clave<br>del Poder</h2>

  <div class="poder-grid reveal">
    <div class="poder-card">
      <div class="poder-num">01</div>
      <div class="poder-icon">R</div>
      <h3>Recursos Naturales</h3>
      <p>Petróleo, gas natural, litio y agua dulce. Quien controla los recursos estratégicos obtiene una ventaja geopolítica directa y duradera.</p>
    </div>
    <div class="poder-card">
      <div class="poder-num">02</div>
      <div class="poder-icon">T</div>
      <h3>Poder Tecnológico</h3>
      <p>Los microchips y la Inteligencia Artificial son el petróleo del siglo XXI. El control de estas cadenas de producción define el liderazgo global.</p>
    </div>
    <div class="poder-card">
      <div class="poder-num">03</div>
      <div class="poder-icon">S</div>
      <h3>Soft Power vs Hard Power</h3>
      <p>El Hard Power opera desde la fuerza militar. El Soft Power actúa desde la influencia cultural, diplomática y económica.</p>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SECCIÓN 3: CHOKE POINTS -->
<section id="chokepoints">
  <div class="choke-layout">
    <div class="reveal">
      <div class="section-tag">03 — Geografía Crítica</div>
      <h2 class="section-title">Cuellos de<br>Botella Globales</h2>

      <div class="choke-list">
        <div class="choke-item">
          <div class="choke-num">01</div>
          <div class="choke-content">
            <h3>Estrecho de Ormuz</h3>
            <p>Punto neurálgico para el suministro de petróleo global. El 20% del crudo mundial pasa por aquí.</p>
          </div>
        </div>
        <div class="choke-item">
          <div class="choke-num">02</div>
          <div class="choke-content">
            <h3>Canal de Suez y Panamá</h3>
            <p>Cruces artificiales que enfrentan crecientes retos logísticos, geopolíticos y climáticos.</p>
          </div>
        </div>
        <div class="choke-item">
          <div class="choke-num">03</div>
          <div class="choke-content">
            <h3>Estrecho de Malaca</h3>
            <p>Principal conexión entre el Océano Índico y el Pacífico. Esencial para el comercio asiático.</p>
          </div>
        </div>
      </div>
    </div>

    <!-- MAPA DECORATIVO SVG -->
    <div class="choke-visual reveal reveal-delay-2">
      <svg viewBox="0 0 440 440" xmlns="http://www.w3.org/2000/svg" fill="none">
        <rect width="440" height="440" fill="#13141a"/>
        <!-- Grid -->
        <line x1="0" y1="110" x2="440" y2="110" stroke="rgba(201,168,76,0.06)" stroke-width="1"/>
        <line x1="0" y1="220" x2="440" y2="220" stroke="rgba(201,168,76,0.06)" stroke-width="1"/>
        <line x1="0" y1="330" x2="440" y2="330" stroke="rgba(201,168,76,0.06)" stroke-width="1"/>
        <line x1="110" y1="0" x2="110" y2="440" stroke="rgba(201,168,76,0.06)" stroke-width="1"/>
        <line x1="220" y1="0" x2="220" y2="440" stroke="rgba(201,168,76,0.06)" stroke-width="1"/>
        <line x1="330" y1="0" x2="330" y2="440" stroke="rgba(201,168,76,0.06)" stroke-width="1"/>
        <!-- Route lines -->
        <path d="M60 200 Q150 180 210 220 Q270 260 330 200 Q370 170 410 190" stroke="rgba(201,168,76,0.3)" stroke-width="1.5" stroke-dasharray="400" stroke-dashoffset="400" style="animation: dash 2s ease forwards 1s;"/>
        <path d="M60 240 Q120 260 180 250 Q240 240 300 260 Q360 280 420 250" stroke="rgba(201,168,76,0.15)" stroke-width="1" stroke-dasharray="400" stroke-dashoffset="400" style="animation: dash 2s ease forwards 1.3s;"/>
        <!-- Points of interest -->
        <circle cx="210" cy="220" r="8" fill="none" stroke="#c9a84c" stroke-width="1.5"/>
        <circle cx="210" cy="220" r="3" fill="#c9a84c"/>
        <circle cx="210" cy="220" r="16" fill="none" stroke="rgba(201,168,76,0.2)" stroke-width="1">
          <animate attributeName="r" values="8;20;8" dur="2.5s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0.5;0;0.5" dur="2.5s" repeatCount="indefinite"/>
        </circle>

        <circle cx="330" cy="200" r="8" fill="none" stroke="#c0392b" stroke-width="1.5"/>
        <circle cx="330" cy="200" r="3" fill="#c0392b"/>
        <circle cx="330" cy="200" r="16" fill="none" stroke="rgba(192,57,43,0.2)" stroke-width="1">
          <animate attributeName="r" values="8;20;8" dur="2.5s" begin="0.8s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0.5;0;0.5" dur="2.5s" begin="0.8s" repeatCount="indefinite"/>
        </circle>

        <circle cx="150" cy="250" r="8" fill="none" stroke="#2e7d99" stroke-width="1.5"/>
        <circle cx="150" cy="250" r="3" fill="#2e7d99"/>
        <circle cx="150" cy="250" r="16" fill="none" stroke="rgba(46,125,153,0.2)" stroke-width="1">
          <animate attributeName="r" values="8;20;8" dur="2.5s" begin="1.6s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="0.5;0;0.5" dur="2.5s" begin="1.6s" repeatCount="indefinite"/>
        </circle>

        <!-- Labels -->
        <text x="222" y="218" fill="#c9a84c" font-family="'DM Mono',monospace" font-size="9" letter-spacing="0.1em">ORMUZ</text>
        <text x="342" y="198" fill="#c0392b" font-family="'DM Mono',monospace" font-size="9" letter-spacing="0.1em">MALACA</text>
        <text x="100" y="268" fill="#2e7d99" font-family="'DM Mono',monospace" font-size="9" letter-spacing="0.1em">SUEZ</text>

        <!-- Corner marks -->
        <path d="M10 10 L30 10 M10 10 L10 30" stroke="rgba(201,168,76,0.3)" stroke-width="1"/>
        <path d="M430 10 L410 10 M430 10 L430 30" stroke="rgba(201,168,76,0.3)" stroke-width="1"/>
        <path d="M10 430 L30 430 M10 430 L10 410" stroke="rgba(201,168,76,0.3)" stroke-width="1"/>
        <path d="M430 430 L410 430 M430 430 L430 410" stroke="rgba(201,168,76,0.3)" stroke-width="1"/>

        <text x="15" y="435" fill="rgba(201,168,76,0.4)" font-family="'DM Mono',monospace" font-size="8">RUTAS ESTRATÉGICAS GLOBALES</text>
      </svg>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SECCIÓN 4: TABLERO -->
<section id="tablero" class="tablero-bg">
  <div class="section-tag reveal">04 — Conflictos Activos</div>
  <h2 class="section-title reveal">El Tablero<br>Mundial Actual</h2>

  <div class="tablero-cards reveal">
    <div class="tablero-card">
      <div class="tag">Tensión geopolítica activa</div>
      <h3>La Rivalidad<br>EE.UU. vs China</h3>
      <p>Una competencia por la primacía tecnológica y comercial del siglo. Taiwán representa el punto crítico: su dominio en la fabricación de semiconductores la convierte en el territorio más estratégico del planeta.</p>
    </div>
    <div class="tablero-card">
      <div class="tag">Zona en disputa</div>
      <h3>La Carrera<br>por el Ártico</h3>
      <p>El deshielo progresivo abre nuevas rutas de navegación y expone enormes yacimientos de gas. Rusia, Estados Unidos y Canadá refuerzan aceleradamente su presencia militar y logística en la región.</p>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SECCIÓN 5: SUR GLOBAL -->
<section id="sur">
  <div class="sur-layout">
    <div class="reveal">
      <div class="section-tag">05 — Nuevas Potencias</div>
      <h2 class="section-title">El Ascenso del<br>Sur Global</h2>
      <div class="sur-blocks">
        <div class="sur-block">
          <h3>Bloque BRICS+</h3>
          <p>Países como India y Brasil buscan alternativas financieras para reducir su dependencia de las instituciones y divisas occidentales. Un contrapeso en construcción.</p>
        </div>
        <div class="sur-block">
          <h3>India como actor pivote</h3>
          <p>Su posición demográfica y su ritmo de crecimiento económico la convierten en el equilibrador clave entre las grandes potencias del siglo XXI.</p>
        </div>
      </div>
    </div>
    <div class="sur-bignum reveal reveal-delay-2">
      <div class="bignum-item">
        <div class="bignum-val">9</div>
        <div class="bignum-desc">miembros activos en el bloque BRICS+ desde 2024</div>
      </div>
      <div class="bignum-item">
        <div class="bignum-val">40%</div>
        <div class="bignum-desc">del PIB mundial que representan en conjunto</div>
      </div>
      <div class="bignum-item">
        <div class="bignum-val">#1</div>
        <div class="bignum-desc">India, la nación más poblada del planeta desde 2023</div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SECCIÓN 6: DESAFÍOS -->
<section id="desafios" class="challenges-bg">
  <div class="section-tag reveal">06 — Siglo XXI</div>
  <h2 class="section-title reveal">Desafíos<br>Emergentes</h2>

  <div class="challenges-grid">
    <div class="challenge-card reveal">
      <div class="challenge-accent"></div>
      <div class="challenge-icon">⬡</div>
      <h3>Ciberseguridad</h3>
      <p>La infraestructura crítica de una nación —energía, finanzas, comunicaciones— puede ser atacada y paralizada sin presencia militar física alguna. El campo de batalla se ha vuelto invisible.</p>
    </div>
    <div class="challenge-card reveal reveal-delay-1">
      <div class="challenge-accent"></div>
      <div class="challenge-icon">◈</div>
      <h3>Cambio Climático</h3>
      <p>Actúa como un multiplicador de conflictos existentes: la escasez de agua, las cosechas devastadas y las migraciones masivas presionan los sistemas políticos más frágiles del mundo.</p>
    </div>
    <div class="challenge-card reveal reveal-delay-2">
      <div class="challenge-accent"></div>
      <div class="challenge-icon">⬖</div>
      <h3>Cadenas de Suministro</h3>
      <p>La pandemia reveló la fragilidad de depender de un solo proveedor para industrias críticas. El reshoring y el friendshoring redefinen la geografía industrial global.</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div>
    <div class="footer-brand">Mundo en <span>Movimiento</span></div>
    <div class="footer-sub">Entender el mapa es entender el mundo</div>
  </div>
  <div class="footer-copy">
    © 2026 Proyecto Escolar<br>
    Geografía 3.º ESO
  </div>
</footer>

<script>
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
      }
    });
  }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
