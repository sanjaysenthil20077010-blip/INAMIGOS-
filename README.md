
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>InAmigos Foundation — Internship Program</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Inter:wght@300;400;500&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet" />
<style>
  /* ── TOKENS ────────────────────────────────────── */
  :root {
    --ink:       #0D0D0D;
    --paper:     #F7F4EE;
    --electric:  #FF4D00;     /* bold tangerine-red — signature */
    --mint:      #00C98D;
    --slate:     #1A1A2E;
    --mid:       #6B6B6B;
    --rule:      rgba(13,13,13,.12);
    --font-display: 'Syne', sans-serif;
    --font-body:    'Inter', sans-serif;
    --font-mono:    'Space Mono', monospace;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--paper);
    color: var(--ink);
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ── CURSOR TRAIL ──────────────────────────────── */
  .cursor-dot {
    width: 8px; height: 8px;
    background: var(--electric);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%,-50%);
    transition: transform .1s ease;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid var(--electric);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%,-50%);
    transition: transform .18s ease, width .2s, height .2s, border-color .2s;
    opacity: .6;
  }

  /* ── NAV ───────────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 4rem;
    backdrop-filter: blur(14px);
    background: rgba(247,244,238,.85);
    border-bottom: 1px solid var(--rule);
  }
  .nav-logo {
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1.35rem;
    letter-spacing: -.03em;
    color: var(--ink);
    text-decoration: none;
  }
  .nav-logo span { color: var(--electric); }
  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a {
    font-family: var(--font-mono);
    font-size: .78rem;
    letter-spacing: .08em;
    text-transform: uppercase;
    color: var(--mid);
    text-decoration: none;
    transition: color .2s;
  }
  .nav-links a:hover { color: var(--electric); }
  .nav-cta {
    background: var(--electric);
    color: #fff !important;
    padding: .5rem 1.3rem;
    border-radius: 2px;
    transition: background .2s, transform .15s !important;
  }
  .nav-cta:hover { background: var(--ink) !important; color: #fff !important; transform: translateY(-1px); }

  /* ── HERO ──────────────────────────────────────── */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 4rem;
    padding-top: 80px;
    gap: 0;
    position: relative;
    overflow: hidden;
  }
  .hero-left {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-right: 4rem;
    border-right: 1px solid var(--rule);
  }
  .hero-eyebrow {
    font-family: var(--font-mono);
    font-size: .72rem;
    letter-spacing: .14em;
    text-transform: uppercase;
    color: var(--electric);
    margin-bottom: 1.4rem;
    display: flex;
    align-items: center;
    gap: .7rem;
  }
  .hero-eyebrow::before {
    content: '';
    display: block;
    width: 2rem;
    height: 1px;
    background: var(--electric);
  }
  h1 {
    font-family: var(--font-display);
    font-weight: 800;
    font-size: clamp(3rem, 5.5vw, 5.4rem);
    line-height: .95;
    letter-spacing: -.04em;
    color: var(--ink);
    margin-bottom: 1.8rem;
  }
  h1 em {
    font-style: normal;
    color: var(--electric);
    position: relative;
  }
  h1 em::after {
    content: '';
    position: absolute;
    bottom: 4px;
    left: 0; right: 0;
    height: 4px;
    background: var(--mint);
    opacity: .6;
    border-radius: 2px;
  }
  .hero-sub {
    font-size: 1.08rem;
    color: var(--mid);
    max-width: 420px;
    line-height: 1.75;
    margin-bottom: 2.8rem;
  }
  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }
  .btn-primary {
    background: var(--electric);
    color: #fff;
    padding: .9rem 2rem;
    font-family: var(--font-display);
    font-weight: 700;
    font-size: .95rem;
    border: none;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    border-radius: 2px;
    transition: background .2s, transform .15s, box-shadow .2s;
    letter-spacing: .01em;
  }
  .btn-primary:hover {
    background: var(--ink);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(255,77,0,.22);
  }
  .btn-ghost {
    background: transparent;
    color: var(--ink);
    padding: .9rem 2rem;
    font-family: var(--font-display);
    font-weight: 600;
    font-size: .95rem;
    border: 1.5px solid var(--ink);
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    border-radius: 2px;
    transition: background .2s, color .2s, transform .15s;
  }
  .btn-ghost:hover { background: var(--ink); color: var(--paper); transform: translateY(-2px); }
  .hero-right {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 4rem;
  }
  .hero-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2.4rem;
  }
  .stat-card {
    padding: 2rem;
    border: 1px solid var(--rule);
    border-radius: 4px;
    background: #fff;
    position: relative;
    overflow: hidden;
    transition: transform .2s, box-shadow .2s;
  }
  .stat-card:hover { transform: translateY(-4px); box-shadow: 0 12px 32px rgba(0,0,0,.08); }
  .stat-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    height: 3px; width: 100%;
    background: var(--electric);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform .3s ease;
  }
  .stat-card:hover::before { transform: scaleX(1); }
  .stat-num {
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 2.8rem;
    line-height: 1;
    color: var(--ink);
    letter-spacing: -.04em;
  }
  .stat-num .accent { color: var(--electric); }
  .stat-label {
    font-size: .8rem;
    color: var(--mid);
    margin-top: .4rem;
    font-family: var(--font-mono);
    text-transform: uppercase;
    letter-spacing: .06em;
  }
  .scroll-hint {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: .5rem;
    opacity: .45;
  }
  .scroll-hint span {
    font-family: var(--font-mono);
    font-size: .68rem;
    letter-spacing: .12em;
    text-transform: uppercase;
  }
  .scroll-arrow {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, transparent, var(--ink));
    animation: scrollBounce 2s ease-in-out infinite;
  }
  @keyframes scrollBounce {
    0%, 100% { transform: scaleY(1); opacity: .4; }
    50% { transform: scaleY(.6); opacity: 1; }
  }

  /* ── MARQUEE ───────────────────────────────────── */
  .marquee-strip {
    background: var(--electric);
    padding: .7rem 0;
    overflow: hidden;
    white-space: nowrap;
  }
  .marquee-inner {
    display: inline-flex;
    animation: marqueeScroll 22s linear infinite;
    gap: 3rem;
  }
  .marquee-item {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: .9rem;
    color: #fff;
    letter-spacing: .08em;
    text-transform: uppercase;
  }
  .marquee-dot { opacity: .5; }
  @keyframes marqueeScroll {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }

  /* ── SECTION SHARED ────────────────────────────── */
  section { padding: 7rem 4rem; }
  .section-eyebrow {
    font-family: var(--font-mono);
    font-size: .72rem;
    letter-spacing: .14em;
    text-transform: uppercase;
    color: var(--electric);
    margin-bottom: 1rem;
    display: flex; align-items: center; gap: .7rem;
  }
  .section-eyebrow::before {
    content: '';
    display: block;
    width: 2rem; height: 1px;
    background: var(--electric);
  }
  h2 {
    font-family: var(--font-display);
    font-weight: 800;
    font-size: clamp(2.2rem, 4vw, 3.6rem);
    line-height: 1.02;
    letter-spacing: -.035em;
    color: var(--ink);
    margin-bottom: 1.2rem;
  }
  h2 em { font-style: normal; color: var(--electric); }

  /* ── ABOUT ─────────────────────────────────────── */
  #about {
    background: var(--slate);
    color: var(--paper);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
  }
  #about h2 { color: var(--paper); }
  #about h2 em { color: var(--mint); }
  #about .section-eyebrow { color: var(--mint); }
  #about .section-eyebrow::before { background: var(--mint); }
  .about-body {
    font-size: 1.05rem;
    color: rgba(247,244,238,.7);
    line-height: 1.8;
  }
  .about-body p + p { margin-top: 1rem; }
  .about-right { display: flex; flex-direction: column; gap: 1.6rem; }
  .about-card {
    border: 1px solid rgba(247,244,238,.1);
    padding: 1.8rem 2rem;
    border-radius: 4px;
    display: flex; gap: 1.4rem; align-items: flex-start;
    transition: border-color .2s, background .2s;
  }
  .about-card:hover {
    border-color: var(--mint);
    background: rgba(0,201,141,.06);
  }
  .about-icon {
    font-size: 1.8rem;
    flex-shrink: 0;
    margin-top: .1rem;
  }
  .about-card h4 {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 1rem;
    color: var(--paper);
    margin-bottom: .35rem;
  }
  .about-card p { font-size: .88rem; color: rgba(247,244,238,.55); line-height: 1.6; }

  /* ── INTERNSHIP ────────────────────────────────── */
  #internship { background: var(--paper); }
  .internship-intro {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    margin-bottom: 4rem;
    align-items: end;
  }
  .internship-desc {
    font-size: 1.05rem;
    color: var(--mid);
    line-height: 1.8;
  }
  .track-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  .track-card {
    background: var(--ink);
    color: var(--paper);
    padding: 2.2rem;
    border-radius: 4px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: transform .25s, box-shadow .25s;
    text-decoration: none;
    display: block;
  }
  .track-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 3px;
    background: var(--electric);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform .3s ease;
  }
  .track-card:hover { transform: translateY(-6px); box-shadow: 0 20px 40px rgba(0,0,0,.18); }
  .track-card:hover::before { transform: scaleX(1); }
  .track-num {
    font-family: var(--font-mono);
    font-size: .72rem;
    color: var(--electric);
    letter-spacing: .1em;
    margin-bottom: 1.2rem;
    opacity: .8;
  }
  .track-title {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 1.15rem;
    margin-bottom: .7rem;
    line-height: 1.25;
  }
  .track-desc { font-size: .85rem; color: rgba(247,244,238,.55); line-height: 1.6; }
  .track-tag {
    display: inline-block;
    margin-top: 1.2rem;
    padding: .3rem .8rem;
    background: rgba(255,77,0,.15);
    color: var(--electric);
    font-family: var(--font-mono);
    font-size: .68rem;
    letter-spacing: .08em;
    text-transform: uppercase;
    border-radius: 2px;
  }

  /* ── PROCESS ───────────────────────────────────── */
  #process { background: #fff; border-top: 1px solid var(--rule); border-bottom: 1px solid var(--rule); }
  .process-header {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    margin-bottom: 4rem;
    align-items: end;
  }
  .process-steps {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    position: relative;
  }
  .process-steps::before {
    content: '';
    position: absolute;
    top: 2rem; left: 4rem; right: 4rem;
    height: 1px;
    background: linear-gradient(to right, var(--electric), var(--mint));
    z-index: 0;
  }
  .process-step {
    padding: 0 1.5rem;
    position: relative;
    z-index: 1;
  }
  .step-bubble {
    width: 4rem; height: 4rem;
    background: var(--electric);
    color: #fff;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1.1rem;
    margin-bottom: 1.5rem;
    box-shadow: 0 0 0 6px var(--paper);
    transition: background .2s, transform .2s;
  }
  .process-step:hover .step-bubble { background: var(--ink); transform: scale(1.08); }
  .step-title {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: .95rem;
    color: var(--ink);
    margin-bottom: .45rem;
  }
  .step-desc { font-size: .83rem; color: var(--mid); line-height: 1.6; }

  /* ── IMPACT ────────────────────────────────────── */
  #impact {
    background: var(--paper);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
  }
  .impact-visual {
    position: relative;
    padding: 3rem;
  }
  .impact-big-num {
    font-family: var(--font-display);
    font-weight: 800;
    font-size: clamp(5rem, 12vw, 11rem);
    line-height: .85;
    color: var(--ink);
    letter-spacing: -.05em;
    position: relative;
  }
  .impact-big-num .frac {
    font-size: .38em;
    vertical-align: super;
    color: var(--electric);
  }
  .impact-caption {
    font-family: var(--font-mono);
    font-size: .75rem;
    letter-spacing: .1em;
    text-transform: uppercase;
    color: var(--mid);
    margin-top: 1rem;
  }
  .impact-bar {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .impact-bar-item { display: flex; flex-direction: column; gap: .35rem; }
  .bar-label {
    display: flex; justify-content: space-between;
    font-family: var(--font-mono);
    font-size: .72rem;
    color: var(--mid);
    letter-spacing: .06em;
    text-transform: uppercase;
  }
  .bar-track {
    height: 4px;
    background: var(--rule);
    border-radius: 2px;
    overflow: hidden;
  }
  .bar-fill {
    height: 100%;
    background: linear-gradient(to right, var(--electric), var(--mint));
    border-radius: 2px;
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 1.2s cubic-bezier(.23,1,.32,1);
  }
  .bar-fill.animated { transform: scaleX(1); }
  .impact-right-text .section-eyebrow { margin-top: 0; }
  .impact-quote {
    margin-top: 2rem;
    border-left: 3px solid var(--electric);
    padding-left: 1.4rem;
    font-size: 1.05rem;
    font-style: italic;
    color: var(--mid);
    line-height: 1.75;
  }
  .impact-quote cite {
    display: block;
    font-style: normal;
    font-family: var(--font-mono);
    font-size: .72rem;
    letter-spacing: .08em;
    text-transform: uppercase;
    color: var(--electric);
    margin-top: .6rem;
  }

  /* ── APPLY / CTA ───────────────────────────────── */
  #apply {
    background: var(--electric);
    color: #fff;
    text-align: center;
    padding: 8rem 4rem;
    position: relative;
    overflow: hidden;
  }
  #apply::before {
    content: 'APPLY';
    position: absolute;
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 22vw;
    color: rgba(255,255,255,.07);
    top: 50%; left: 50%;
    transform: translate(-50%,-50%);
    letter-spacing: -.06em;
    pointer-events: none;
    white-space: nowrap;
  }
  #apply h2 { color: #fff; font-size: clamp(2.4rem, 5vw, 4.5rem); position: relative; }
  #apply h2 em { color: var(--ink); font-style: normal; }
  .apply-sub {
    font-size: 1.08rem;
    color: rgba(255,255,255,.78);
    max-width: 540px;
    margin: 1.4rem auto 2.8rem;
    line-height: 1.75;
    position: relative;
  }
  .btn-white {
    background: #fff;
    color: var(--electric);
    padding: 1rem 2.5rem;
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1rem;
    border: none;
    cursor: pointer;
    text-decoration: none;
    display: inline-block;
    border-radius: 2px;
    letter-spacing: .01em;
    transition: background .2s, color .2s, transform .15s, box-shadow .2s;
    position: relative;
  }
  .btn-white:hover {
    background: var(--ink);
    color: #fff;
    transform: translateY(-3px);
    box-shadow: 0 16px 32px rgba(0,0,0,.22);
  }
  .apply-note {
    font-family: var(--font-mono);
    font-size: .72rem;
    letter-spacing: .1em;
    text-transform: uppercase;
    color: rgba(255,255,255,.55);
    margin-top: 1.4rem;
    position: relative;
  }

  /* ── FOOTER ────────────────────────────────────── */
  footer {
    background: var(--ink);
    color: var(--paper);
    padding: 4rem;
    display: grid;
    grid-template-columns: 1.5fr 1fr 1fr;
    gap: 4rem;
    border-top: 3px solid var(--electric);
  }
  .footer-brand .nav-logo { color: var(--paper); font-size: 1.5rem; display: block; margin-bottom: 1rem; }
  .footer-brand p { font-size: .88rem; color: rgba(247,244,238,.45); line-height: 1.75; max-width: 280px; }
  .footer-col h5 {
    font-family: var(--font-mono);
    font-size: .72rem;
    letter-spacing: .12em;
    text-transform: uppercase;
    color: var(--electric);
    margin-bottom: 1.2rem;
  }
  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: .65rem; }
  .footer-col a {
    font-size: .88rem;
    color: rgba(247,244,238,.5);
    text-decoration: none;
    transition: color .2s;
  }
  .footer-col a:hover { color: var(--paper); }
  .footer-bottom {
    background: var(--ink);
    padding: 1.4rem 4rem;
    border-top: 1px solid rgba(247,244,238,.08);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .footer-bottom p {
    font-family: var(--font-mono);
    font-size: .72rem;
    letter-spacing: .06em;
    color: rgba(247,244,238,.3);
    text-transform: uppercase;
  }
  .footer-bottom a { color: var(--electric); text-decoration: none; }

  /* ── SCROLL REVEAL ─────────────────────────────── */
  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity .7s ease, transform .7s ease;
  }
  .reveal.visible { opacity: 1; transform: none; }

  /* ── MOBILE ────────────────────────────────────── */
  @media (max-width: 900px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .hero { grid-template-columns: 1fr; padding: 6rem 1.5rem 3rem; gap: 3rem; }
    .hero-left { border-right: none; padding-right: 0; border-bottom: 1px solid var(--rule); padding-bottom: 3rem; }
    .hero-right { padding-left: 0; }
    .hero-stats { grid-template-columns: 1fr 1fr; gap: 1rem; }
    section { padding: 4rem 1.5rem; }
    #about { grid-template-columns: 1fr; gap: 3rem; }
    .internship-intro { grid-template-columns: 1fr; gap: 2rem; }
    .track-grid { grid-template-columns: 1fr; }
    .process-header { grid-template-columns: 1fr; gap: 1.5rem; }
    .process-steps { grid-template-columns: 1fr 1fr; gap: 2rem; }
    .process-steps::before { display: none; }
    #impact { grid-template-columns: 1fr; gap: 3rem; }
    footer { grid-template-columns: 1fr; gap: 2rem; }
    .footer-bottom { flex-direction: column; gap: .5rem; text-align: center; }
  }

  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; }
  }
</style>
</head>
<body>

<!-- CURSOR -->
<div class="cursor-dot" id="cursorDot"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">In<span>Amigos</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#internship">Internship</a></li>
    <li><a href="#process">Process</a></li>
    <li><a href="#impact">Impact</a></li>
    <li><a href="#apply" class="nav-cta">Apply Now</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-left">
    <p class="hero-eyebrow">InAmigos Foundation — Internship Program</p>
    <h1>Where <em>students</em> become changemakers</h1>
    <p class="hero-sub">A non-profit foundation empowering the next generation with real-world skills, mentorship, and purpose-driven projects that matter.</p>
    <div class="hero-actions">
      <a href="#apply" class="btn-primary">Apply for Internship</a>
      <a href="#about" class="btn-ghost">Learn More</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-stats">
      <div class="stat-card reveal">
        <div class="stat-num">500<span class="accent">+</span></div>
        <div class="stat-label">Interns Trained</div>
      </div>
      <div class="stat-card reveal" style="transition-delay:.1s">
        <div class="stat-num">30<span class="accent">+</span></div>
        <div class="stat-label">Partner Orgs</div>
      </div>
      <div class="stat-card reveal" style="transition-delay:.2s">
        <div class="stat-num">92<span class="accent">%</span></div>
        <div class="stat-label">Placement Rate</div>
      </div>
      <div class="stat-card reveal" style="transition-delay:.3s">
        <div class="stat-num">6<span class="accent">+</span></div>
        <div class="stat-label">Program Tracks</div>
      </div>
    </div>
  </div>
  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-arrow"></div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-strip" aria-hidden="true">
  <div class="marquee-inner">
    <span class="marquee-item">Education</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Technology</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Social Impact</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Leadership</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Innovation</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Community</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Growth</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Education</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Technology</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Social Impact</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Leadership</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Innovation</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Community</span><span class="marquee-item marquee-dot">✦</span>
    <span class="marquee-item">Growth</span><span class="marquee-item marquee-dot">✦</span>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div>
    <p class="section-eyebrow">Our Foundation</p>
    <h2>Built on<br/><em>friendship.</em><br/>Fueled by purpose.</h2>
    <div class="about-body reveal">
      <p>InAmigos — "In Friends" — was born from a simple belief: young people grow fastest when they're surrounded by a community that believes in them. We're a non-profit connecting ambitious students to opportunities that shape careers and build character.</p>
      <p>Our internship program bridges the gap between academic theory and professional practice, giving participants hands-on experience while making a real difference in underserved communities.</p>
    </div>
  </div>
  <div class="about-right">
    <div class="about-card reveal">
      <div class="about-icon">🎯</div>
      <div>
        <h4>Mission-Driven Projects</h4>
        <p>Every intern works on real initiatives with measurable community impact — not busy work.</p>
      </div>
    </div>
    <div class="about-card reveal" style="transition-delay:.1s">
      <div class="about-icon">🤝</div>
      <div>
        <h4>Mentorship at the Core</h4>
        <p>Paired with experienced professionals who invest in your growth beyond the program.</p>
      </div>
    </div>
    <div class="about-card reveal" style="transition-delay:.2s">
      <div class="about-icon">🌍</div>
      <div>
        <h4>Global Perspective</h4>
        <p>Collaborate across cultures and borders to solve problems with lasting significance.</p>
      </div>
    </div>
    <div class="about-card reveal" style="transition-delay:.3s">
      <div class="about-icon">📜</div>
      <div>
        <h4>Certified Completion</h4>
        <p>Receive a recognized certificate and LinkedIn endorsement upon program completion.</p>
      </div>
    </div>
  </div>
</section>

<!-- INTERNSHIP TRACKS -->
<section id="internship">
  <div class="internship-intro">
    <div>
      <p class="section-eyebrow">Program Tracks</p>
      <h2>Find your<br/><em>domain.</em></h2>
    </div>
    <p class="internship-desc">Six specialized tracks — each designed by industry practitioners — give you deep, focused experience in the field that excites you most. Tracks run 6–12 weeks with flexible remote and hybrid options.</p>
  </div>
  <div class="track-grid">
    <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="track-card reveal">
      <div class="track-num">Track 01</div>
      <div class="track-title">Web & App Development</div>
      <p class="track-desc">Build real-world digital products for NGOs, from responsive websites to mobile applications used in the field.</p>
      <span class="track-tag">Tech</span>
    </a>
    <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="track-card reveal" style="transition-delay:.07s">
      <div class="track-num">Track 02</div>
      <div class="track-title">Digital Marketing</div>
      <p class="track-desc">Drive social campaigns, content strategy, and audience growth for causes that deserve to be heard.</p>
      <span class="track-tag">Creative</span>
    </a>
    <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="track-card reveal" style="transition-delay:.14s">
      <div class="track-num">Track 03</div>
      <div class="track-title">Data & Analytics</div>
      <p class="track-desc">Turn community data into actionable insight — dashboards, reports, and analysis that guide real decisions.</p>
      <span class="track-tag">Data</span>
    </a>
    <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="track-card reveal" style="transition-delay:.21s">
      <div class="track-num">Track 04</div>
      <div class="track-title">Graphic & UI Design</div>
      <p class="track-desc">Craft visual identities, print materials, and user interfaces for programs that serve real communities.</p>
      <span class="track-tag">Design</span>
    </a>
    <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="track-card reveal" style="transition-delay:.28s">
      <div class="track-num">Track 05</div>
      <div class="track-title">Project Management</div>
      <p class="track-desc">Lead cross-functional initiatives from scoping to delivery, building skills that transfer to any industry.</p>
      <span class="track-tag">Operations</span>
    </a>
    <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="track-card reveal" style="transition-delay:.35s">
      <div class="track-num">Track 06</div>
      <div class="track-title">Content & Journalism</div>
      <p class="track-desc">Write, film, and edit stories that amplify underrepresented voices and document community impact.</p>
      <span class="track-tag">Media</span>
    </a>
  </div>
</section>

<!-- PROCESS -->
<section id="process">
  <div class="process-header">
    <div>
      <p class="section-eyebrow">How It Works</p>
      <h2>From<br/><em>application</em><br/>to impact.</h2>
    </div>
    <p style="font-size:1.05rem; color:var(--mid); line-height:1.8;">A straightforward, transparent path from your first click to your final certificate — no gatekeeping, no ambiguity.</p>
  </div>
  <div class="process-steps">
    <div class="process-step reveal">
      <div class="step-bubble">1</div>
      <div class="step-title">Apply Online</div>
      <p class="step-desc">Fill out a short form — your story, your skills, and the track that excites you. Takes 10 minutes.</p>
    </div>
    <div class="process-step reveal" style="transition-delay:.12s">
      <div class="step-bubble">2</div>
      <div class="step-title">Brief Interview</div>
      <p class="step-desc">A 20-minute conversation with a program coordinator — no trick questions, just getting to know you.</p>
    </div>
    <div class="process-step reveal" style="transition-delay:.24s">
      <div class="step-bubble">3</div>
      <div class="step-title">Onboard & Connect</div>
      <p class="step-desc">Meet your mentor, your cohort, and your project brief. Orientation happens your first week.</p>
    </div>
    <div class="process-step reveal" style="transition-delay:.36s">
      <div class="step-bubble">4</div>
      <div class="step-title">Deliver & Graduate</div>
      <p class="step-desc">Present your work, receive your certificate, and join the InAmigos alumni network for life.</p>
    </div>
  </div>
</section>

<!-- IMPACT -->
<section id="impact">
  <div class="impact-visual reveal">
    <div class="impact-big-num">92<span class="frac">%</span></div>
    <div class="impact-caption">intern satisfaction rate · 2023–24 cohort</div>
    <div class="impact-bar">
      <div class="impact-bar-item">
        <div class="bar-label"><span>Job-Ready Skills</span><span>96%</span></div>
        <div class="bar-track"><div class="bar-fill" data-width=".96"></div></div>
      </div>
      <div class="impact-bar-item">
        <div class="bar-label"><span>Would Recommend</span><span>94%</span></div>
        <div class="bar-track"><div class="bar-fill" data-width=".94"></div></div>
      </div>
      <div class="impact-bar-item">
        <div class="bar-label"><span>Placed Within 3 Months</span><span>89%</span></div>
        <div class="bar-track"><div class="bar-fill" data-width=".89"></div></div>
      </div>
    </div>
  </div>
  <div class="impact-right-text reveal" style="transition-delay:.15s">
    <p class="section-eyebrow">Real Impact</p>
    <h2>Numbers that<br/><em>mean something.</em></h2>
    <blockquote class="impact-quote">
      The InAmigos internship gave me more than a line on my résumé — it gave me a reason to show up every day. I built something real, with people who actually cared.
      <cite>— Priya S., 2023 Cohort · Now UX Designer @ Razorpay</cite>
    </blockquote>
    <div style="margin-top:2.4rem;">
      <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="btn-primary">See Alumni Stories</a>
    </div>
  </div>
</section>

<!-- APPLY CTA -->
<section id="apply">
  <h2 class="reveal">Ready to build something <em>real?</em></h2>
  <p class="apply-sub reveal">Applications for the next cohort are open. Seats are limited — we keep each cohort small so every intern gets genuine attention.</p>
  <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener" class="btn-white reveal">Apply Now — It's Free</a>
  <p class="apply-note reveal">No fees · Remote-friendly · Certificate included · Next cohort starts soon</p>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-brand">
    <a href="#" class="nav-logo">In<span style="color:var(--electric)">Amigos</span></a>
    <p>Empowering students to become the professionals communities deserve. A non-profit built on friendship, mentorship, and purpose.</p>
  </div>
  <div class="footer-col">
    <h5>Quick Links</h5>
    <ul>
      <li><a href="#about">About Us</a></li>
      <li><a href="#internship">Internship Tracks</a></li>
      <li><a href="#process">How It Works</a></li>
      <li><a href="#impact">Our Impact</a></li>
    </ul>
  </div>
  <div class="footer-col">
    <h5>Connect</h5>
    <ul>
      <li><a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener">LinkedIn</a></li>
      <li><a href="https://instagram.com" target="_blank" rel="noopener">Instagram</a></li>
      <li><a href="mailto:hello@inamigosfoundation.org">Email Us</a></li>
      <li><a href="#apply">Apply Now</a></li>
    </ul>
  </div>
</footer>
<div class="footer-bottom">
  <p>© 2024 InAmigos Foundation · Non-Profit Organization</p>
  <p>Made with ❤️ for students everywhere · <a href="https://www.linkedin.com/company/inamigos-foundation" target="_blank" rel="noopener">LinkedIn</a></p>
</div>

<script>
  // ── Custom Cursor
  const dot = document.getElementById('cursorDot');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  (function animCursor() {
    dot.style.left = mx + 'px'; dot.style.top = my + 'px';
    rx += (mx - rx) * .13; ry += (my - ry) * .13;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animCursor);
  })();
  document.querySelectorAll('a, button, .track-card, .stat-card').forEach(el => {
    el.addEventListener('mouseenter', () => { ring.style.width = '60px'; ring.style.height = '60px'; ring.style.borderColor = 'var(--mint)'; });
    el.addEventListener('mouseleave', () => { ring.style.width = '36px'; ring.style.height = '36px'; ring.style.borderColor = 'var(--electric)'; });
  });

  // ── Scroll Reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        // Animate bars when impact section reveals
        if (e.target.closest('#impact')) {
          document.querySelectorAll('.bar-fill').forEach(bar => {
            bar.style.transform = `scaleX(${bar.dataset.width})`;
            bar.classList.add('animated');
          });
        }
      }
    });
  }, { threshold: 0.15 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // ── Smooth Nav highlight
  const sections = document.querySelectorAll('section[id]');
  const navLinks = document.querySelectorAll('.nav-links a');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(sec => {
      if (window.scrollY >= sec.offsetTop - 120) current = sec.id;
    });
    navLinks.forEach(a => {
      a.style.color = a.getAttribute('href') === '#' + current ? 'var(--electric)' : '';
    });
  });
</script>
</body>
</html>
