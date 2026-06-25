<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GitHub Profile README — Tech Console</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600;700&family=Inter:wght@300;400;500;600;700&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg-base: #0a0a0f;
    --bg-surface: #0f0f1a;
    --bg-card: #12121e;
    --bg-card-hover: #161624;
    --red-core: #ff2244;
    --red-glow: rgba(255,34,68,0.18);
    --red-dim: rgba(255,34,68,0.08);
    --red-border: rgba(255,34,68,0.35);
    --red-bright: #ff4466;
    --text-primary: #f0f0ff;
    --text-secondary: #8888bb;
    --text-muted: #44446a;
    --grid-line: rgba(255,34,68,0.06);
    --scan: rgba(255,34,68,0.03);
  }

  body {
    background: var(--bg-base);
    color: var(--text-primary);
    font-family: 'Inter', system-ui, sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── grid bg ── */
  body::before {
    content: '';
    position: fixed; inset: 0; z-index: 0;
    background-image:
      linear-gradient(var(--grid-line) 1px, transparent 1px),
      linear-gradient(90deg, var(--grid-line) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
  }

  /* scanline */
  body::after {
    content: '';
    position: fixed; inset: 0; z-index: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 3px,
      var(--scan) 3px,
      var(--scan) 4px
    );
    pointer-events: none;
  }

  .wrapper {
    position: relative; z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 2rem 1.5rem 4rem;
  }

  /* ──────────────── HEADER ──────────────── */
  .header {
    border: 1px solid var(--red-border);
    background: var(--bg-card);
    border-radius: 12px;
    padding: 2.5rem 2rem;
    margin-bottom: 1.25rem;
    position: relative;
    overflow: hidden;
    box-shadow: 0 0 40px var(--red-glow), inset 0 0 80px rgba(255,34,68,0.03);
    animation: fadeSlideDown 0.7s ease both;
  }

  .header::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--red-core), transparent);
    animation: scanH 3s linear infinite;
  }

  @keyframes scanH {
    0% { opacity: 0.4; } 50% { opacity: 1; } 100% { opacity: 0.4; }
  }

  .header-inner {
    display: flex;
    align-items: center;
    gap: 2rem;
    flex-wrap: wrap;
  }

  /* ── pixel robot mascot ── */
  .mascot {
    flex-shrink: 0;
    width: 100px;
    animation: floatMascot 3.5s ease-in-out infinite;
  }

  @keyframes floatMascot {
    0%, 100% { transform: translateY(0px); }
    50% { transform: translateY(-8px); }
  }

  .header-text { flex: 1; min-width: 200px; }

  .system-badge {
    display: inline-flex; align-items: center; gap: 6px;
    background: var(--red-dim);
    border: 1px solid var(--red-border);
    border-radius: 4px;
    padding: 3px 10px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    color: var(--red-bright);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin-bottom: 0.75rem;
  }

  .system-badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--red-core);
    box-shadow: 0 0 6px var(--red-core);
    animation: pulse 1.4s ease-in-out infinite;
  }

  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }

  .typing-wrap {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.9rem;
    color: var(--text-primary);
    font-weight: 500;
    margin-bottom: 0.6rem;
    min-height: 1.4em;
  }

  .typing-wrap .cursor {
    display: inline-block;
    width: 2px; height: 1em;
    background: var(--red-core);
    vertical-align: middle;
    animation: blink 0.9s step-end infinite;
    margin-left: 2px;
    box-shadow: 0 0 8px var(--red-core);
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  .header-sub {
    font-size: 0.78rem;
    color: var(--text-secondary);
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 0.04em;
  }

  /* ──────────────── GRID LAYOUT ──────────────── */
  .grid-two {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.25rem;
    margin-bottom: 1.25rem;
    animation: fadeUp 0.7s 0.2s ease both;
  }

  @media (max-width: 640px) {
    .grid-two { grid-template-columns: 1fr; }
  }

  /* ──────────────── CARD ──────────────── */
  .card {
    background: var(--bg-card);
    border: 1px solid var(--red-border);
    border-radius: 10px;
    padding: 1.5rem;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, box-shadow 0.3s, background 0.3s;
  }

  .card:hover {
    border-color: rgba(255,34,68,0.65);
    box-shadow: 0 0 28px var(--red-glow);
    background: var(--bg-card-hover);
  }

  .card-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--red-bright);
    margin-bottom: 0.9rem;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .card-label::before {
    content: '';
    display: block;
    width: 16px; height: 1px;
    background: var(--red-core);
    box-shadow: 0 0 6px var(--red-core);
  }

  .card-title {
    font-size: 0.75rem;
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 0.5rem;
    letter-spacing: 0.02em;
  }

  /* ──────────────── TECH STACK ──────────────── */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
    gap: 0.75rem;
    margin-top: 0.5rem;
  }

  .tech-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5px;
    cursor: default;
  }

  .tech-icon {
    width: 44px; height: 44px;
    border: 1px solid var(--red-border);
    border-radius: 8px;
    background: var(--red-dim);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
    animation: floatIcon var(--d, 3s) var(--delay, 0s) ease-in-out infinite;
  }

  .tech-item:hover .tech-icon {
    transform: translateY(-4px) scale(1.1);
    box-shadow: 0 0 18px var(--red-glow);
    border-color: var(--red-core);
  }

  @keyframes floatIcon {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-5px); }
  }

  .tech-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: 9px;
    color: var(--text-secondary);
    text-align: center;
    letter-spacing: 0.04em;
  }

  /* highlight featured */
  .tech-item.featured .tech-icon {
    border-color: var(--red-core);
    background: rgba(255,34,68,0.14);
    box-shadow: 0 0 12px var(--red-glow);
  }

  .tech-item.featured .tech-name {
    color: var(--red-bright);
  }

  /* ──────────────── BIO ──────────────── */
  .bio-text {
    font-size: 0.8rem;
    line-height: 1.75;
    color: var(--text-secondary);
  }

  .bio-text strong {
    color: var(--text-primary);
    font-weight: 600;
  }

  .bio-highlight {
    display: inline-block;
    background: var(--red-dim);
    border-left: 2px solid var(--red-core);
    padding: 0.6rem 0.8rem;
    margin: 0.75rem 0 0;
    border-radius: 0 4px 4px 0;
    font-size: 0.75rem;
    font-family: 'JetBrains Mono', monospace;
    color: var(--red-bright);
    width: 100%;
  }

  /* ──────────────── ANALYTICS ROW ──────────────── */
  .analytics-row {
    animation: fadeUp 0.7s 0.4s ease both;
    margin-bottom: 1.25rem;
  }

  .analytics-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--red-bright);
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 1rem;
  }

  .analytics-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--red-border), transparent);
  }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }

  @media (max-width: 600px) { .stats-grid { grid-template-columns: 1fr; } }

  .stat-card {
    background: var(--bg-card);
    border: 1px solid var(--red-border);
    border-radius: 10px;
    padding: 1.25rem;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: box-shadow 0.3s, transform 0.3s;
    animation: fadeIn 0.6s calc(0.5s + var(--i,0) * 0.12s) ease both;
  }

  .stat-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 32px var(--red-glow);
  }

  .stat-card::after {
    content: '';
    position: absolute; bottom: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--red-core), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .stat-card:hover::after { opacity: 1; }

  .stat-number {
    font-family: 'JetBrains Mono', monospace;
    font-size: 2rem;
    font-weight: 700;
    color: var(--text-primary);
    line-height: 1;
    margin-bottom: 0.25rem;
    text-shadow: 0 0 20px rgba(255,255,255,0.12);
  }

  .stat-number span { color: var(--red-bright); }

  .stat-label {
    font-size: 0.68rem;
    color: var(--text-secondary);
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }

  .stat-sub {
    font-size: 0.65rem;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
  }

  /* ──────────────── STREAK ──────────────── */
  .streak-bar {
    display: flex;
    gap: 3px;
    flex-wrap: wrap;
    margin-top: 0.6rem;
  }

  .streak-cell {
    width: 11px; height: 11px;
    border-radius: 2px;
    background: var(--bg-surface);
    border: 1px solid var(--red-border);
    transition: background 0.2s, box-shadow 0.2s;
  }

  .streak-cell.active {
    background: var(--red-core);
    border-color: var(--red-core);
    box-shadow: 0 0 4px var(--red-core);
  }

  .streak-cell.mid {
    background: rgba(255,34,68,0.4);
    border-color: rgba(255,34,68,0.5);
  }

  .streak-cell:hover {
    transform: scale(1.3);
    box-shadow: 0 0 8px var(--red-core);
  }

  /* ──────────────── LANGUAGES CHART ──────────────── */
  .lang-chart { margin-top: 0.5rem; }

  .lang-bar-row {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    margin-bottom: 0.5rem;
    animation: fadeIn 0.5s ease both;
  }

  .lang-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    color: var(--text-secondary);
    width: 80px;
    flex-shrink: 0;
    text-align: right;
  }

  .lang-track {
    flex: 1;
    height: 8px;
    background: var(--bg-surface);
    border-radius: 99px;
    overflow: hidden;
    border: 1px solid rgba(255,34,68,0.12);
  }

  .lang-fill {
    height: 100%;
    border-radius: 99px;
    background: linear-gradient(90deg, var(--red-core), var(--red-bright));
    box-shadow: 0 0 6px var(--red-glow);
    transform-origin: left;
    animation: growBar 1s calc(var(--delay,0s)) cubic-bezier(0.23,1,0.32,1) both;
  }

  @keyframes growBar {
    from { transform: scaleX(0); }
    to { transform: scaleX(1); }
  }

  .lang-fill.alt { background: linear-gradient(90deg, #662233, var(--red-core)); }
  .lang-fill.dim { background: rgba(255,34,68,0.35); box-shadow: none; }

  .lang-pct {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    color: var(--red-bright);
    width: 36px;
    flex-shrink: 0;
  }

  /* ──────────────── VISITOR COUNTER ──────────────── */
  .visitor-count {
    font-family: 'JetBrains Mono', monospace;
    font-size: 2.4rem;
    font-weight: 700;
    color: var(--red-bright);
    text-shadow: 0 0 24px rgba(255,34,68,0.5);
    letter-spacing: 0.08em;
    line-height: 1;
    margin-bottom: 0.25rem;
    animation: countUp 1.5s ease both;
  }

  @keyframes countUp {
    from { opacity: 0; transform: translateY(6px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ──────────────── FOOTER ROW ──────────────── */
  .footer-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.25rem;
    animation: fadeUp 0.7s 0.6s ease both;
  }

  @media (max-width: 600px) { .footer-row { grid-template-columns: 1fr; } }

  /* ──────────────── SOCIAL STRIP ──────────────── */
  .social-strip {
    display: flex; gap: 0.5rem; flex-wrap: wrap; margin-top: 0.75rem;
  }

  .social-btn {
    display: inline-flex; align-items: center; gap: 5px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    border: 1px solid var(--red-border);
    background: var(--red-dim);
    color: var(--red-bright);
    padding: 4px 10px;
    border-radius: 4px;
    text-decoration: none;
    transition: background 0.2s, box-shadow 0.2s;
    cursor: pointer;
  }

  .social-btn:hover {
    background: rgba(255,34,68,0.18);
    box-shadow: 0 0 10px var(--red-glow);
  }

  /* ──────────────── STATUS BAR ──────────────── */
  .status-bar {
    margin-top: 1.25rem;
    border: 1px solid var(--red-border);
    background: var(--bg-card);
    border-radius: 8px;
    padding: 0.6rem 1rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
    animation: fadeUp 0.7s 0.8s ease both;
  }

  .status-item {
    display: flex; align-items: center; gap: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    color: var(--text-muted);
  }

  .status-item .dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--red-core);
    box-shadow: 0 0 6px var(--red-core);
  }

  .status-item .dot.green {
    background: #22cc66;
    box-shadow: 0 0 6px rgba(34,204,102,0.6);
  }

  .status-spacer { flex: 1; }

  .status-right {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    color: var(--red-bright);
    letter-spacing: 0.06em;
  }

  /* ──────────────── ANIMATIONS ──────────────── */
  @keyframes fadeSlideDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  /* corner accents */
  .card-corner {
    position: absolute;
    width: 10px; height: 10px;
    border-color: var(--red-core);
    border-style: solid;
    opacity: 0.5;
  }

  .card-corner.tl { top: 6px; left: 6px; border-width: 1px 0 0 1px; }
  .card-corner.br { bottom: 6px; right: 6px; border-width: 0 1px 1px 0; }

</style>
</head>
<body>
<div class="wrapper">

  <!-- ═══════════════ HEADER ═══════════════ -->
  <div class="header">
    <div class="card-corner tl"></div>
    <div class="card-corner br"></div>
    <div class="header-inner">

      <!-- pixel robot SVG -->
      <div class="mascot">
        <svg viewBox="0 0 100 120" xmlns="http://www.w3.org/2000/svg" style="width:100%;height:auto">
          <!-- antenna -->
          <rect x="47" y="4" width="6" height="14" fill="#ff2244" rx="2"/>
          <circle cx="50" cy="3" r="4" fill="#ff4466" style="filter:drop-shadow(0 0 4px #ff2244)"/>
          <!-- head -->
          <rect x="22" y="16" width="56" height="44" rx="8" fill="#161624" stroke="#ff2244" stroke-width="1.5"/>
          <!-- eyes -->
          <rect x="32" y="26" width="14" height="10" rx="3" fill="#ff2244" style="filter:drop-shadow(0 0 5px #ff2244)"/>
          <rect x="54" y="26" width="14" height="10" rx="3" fill="#ff2244" style="filter:drop-shadow(0 0 5px #ff2244)"/>
          <!-- eye pupils animate -->
          <rect x="37" y="29" width="5" height="5" rx="1.5" fill="#fff" style="animation:blink 3s 1s step-end infinite"/>
          <rect x="59" y="29" width="5" height="5" rx="1.5" fill="#fff" style="animation:blink 3s 1s step-end infinite"/>
          <!-- mouth -->
          <rect x="34" y="44" width="32" height="7" rx="3.5" fill="#0a0a0f" stroke="#ff2244" stroke-width="1"/>
          <rect x="37" y="46" width="5" height="3" rx="1" fill="#ff2244"/>
          <rect x="45" y="46" width="5" height="3" rx="1" fill="#ff2244"/>
          <rect x="53" y="46" width="5" height="3" rx="1" fill="#ff2244"/>
          <!-- body -->
          <rect x="28" y="62" width="44" height="36" rx="6" fill="#12121e" stroke="#ff2244" stroke-width="1.5"/>
          <!-- chest panel -->
          <rect x="35" y="68" width="30" height="20" rx="4" fill="#0a0a0f" stroke="rgba(255,34,68,0.4)" stroke-width="1"/>
          <!-- chest leds -->
          <circle cx="43" cy="75" r="3" fill="#ff2244" style="animation:pulse 1.4s 0s ease-in-out infinite"/>
          <circle cx="50" cy="75" r="3" fill="#ff2244" style="animation:pulse 1.4s 0.3s ease-in-out infinite"/>
          <circle cx="57" cy="75" r="3" fill="#ff2244" style="animation:pulse 1.4s 0.6s ease-in-out infinite"/>
          <rect x="40" y="82" width="20" height="3" rx="1.5" fill="rgba(255,34,68,0.3)" stroke="rgba(255,34,68,0.5)" stroke-width="0.5"/>
          <!-- arms -->
          <rect x="8" y="64" width="18" height="28" rx="6" fill="#12121e" stroke="#ff2244" stroke-width="1.5"/>
          <rect x="74" y="64" width="18" height="28" rx="6" fill="#12121e" stroke="#ff2244" stroke-width="1.5"/>
          <!-- hands -->
          <rect x="10" y="91" width="14" height="8" rx="4" fill="#161624" stroke="rgba(255,34,68,0.5)" stroke-width="1"/>
          <rect x="76" y="91" width="14" height="8" rx="4" fill="#161624" stroke="rgba(255,34,68,0.5)" stroke-width="1"/>
          <!-- legs -->
          <rect x="34" y="98" width="14" height="18" rx="4" fill="#12121e" stroke="#ff2244" stroke-width="1.5"/>
          <rect x="52" y="98" width="14" height="18" rx="4" fill="#12121e" stroke="#ff2244" stroke-width="1.5"/>
          <!-- feet -->
          <rect x="30" y="112" width="22" height="8" rx="4" fill="#161624" stroke="rgba(255,34,68,0.5)" stroke-width="1"/>
          <rect x="48" y="112" width="22" height="8" rx="4" fill="#161624" stroke="rgba(255,34,68,0.5)" stroke-width="1"/>
        </svg>
      </div>

      <div class="header-text">
        <div class="system-badge">SYS — ONLINE</div>
        <div class="typing-wrap">
          <span id="typed-text"></span><span class="cursor"></span>
        </div>
        <div class="header-sub">[ frontend_arch &nbsp;·&nbsp; ui_ux_specialist &nbsp;·&nbsp; systems_analyst ]</div>
        <div class="social-strip" style="margin-top:1rem">
          <a class="social-btn" href="#">⌂ Portfolio</a>
          <a class="social-btn" href="#">⎋ LinkedIn</a>
          <a class="social-btn" href="#">✉ Contact</a>
          <a class="social-btn" href="#">◈ GitHub</a>
        </div>
      </div>
    </div>
  </div>

  <!-- ═══════════════ TECH + BIO ═══════════════ -->
  <div class="grid-two">

    <!-- tech stack -->
    <div class="card">
      <div class="card-corner tl"></div>
      <div class="card-corner br"></div>
      <div class="card-label">MODULE_01 — TECH STACK</div>
      <div class="tech-grid">
        <div class="tech-item featured" style="--delay:0s;--d:3s">
          <div class="tech-icon">🎨</div>
          <div class="tech-name">Figma</div>
        </div>
        <div class="tech-item featured" style="--delay:0.2s;--d:3.4s">
          <div class="tech-icon">▲</div>
          <div class="tech-name">Next.js</div>
        </div>
        <div class="tech-item featured" style="--delay:0.4s;--d:3.2s">
          <div class="tech-icon">⬡</div>
          <div class="tech-name">Node.js</div>
        </div>
        <div class="tech-item featured" style="--delay:0.6s;--d:3.6s">
          <div class="tech-icon">🐬</div>
          <div class="tech-name">MySQL</div>
        </div>
        <div class="tech-item" style="--delay:0.1s;--d:4s">
          <div class="tech-icon">⚛</div>
          <div class="tech-name">React</div>
        </div>
        <div class="tech-item" style="--delay:0.3s;--d:3.8s">
          <div class="tech-icon">🟦</div>
          <div class="tech-name">TypeScript</div>
        </div>
        <div class="tech-item" style="--delay:0.5s;--d:3.3s">
          <div class="tech-icon">🎯</div>
          <div class="tech-name">Tailwind</div>
        </div>
        <div class="tech-item" style="--delay:0.7s;--d:3.7s">
          <div class="tech-icon">🐙</div>
          <div class="tech-name">Git</div>
        </div>
      </div>
      <div style="margin-top:0.8rem; padding-top:0.8rem; border-top: 1px solid rgba(255,34,68,0.1);">
        <div style="font-family:'JetBrains Mono',monospace;font-size:0.65rem;color:var(--text-muted);">
          <span style="color:var(--red-bright)">★</span> highlighted = daily drivers
        </div>
      </div>
    </div>

    <!-- bio -->
    <div class="card">
      <div class="card-corner tl"></div>
      <div class="card-corner br"></div>
      <div class="card-label">MODULE_02 — PROFILE</div>
      <div class="bio-text">
        Hey — I'm an <strong>aspiring software engineer</strong> who believes the best interfaces feel <strong>inevitable</strong>: intuitive before you read a word, fast before you feel the wait.
        <br><br>
        My work lives at the crossroads of <strong>frontend architecture</strong> and <strong>user experience design</strong>. I obsess over component systems, information hierarchy, and the micro-decisions that separate a good UI from a great one.
        <br><br>
        Outside of shipping features, I'm drawn to <strong>structured systems analysis</strong> — mapping data flows, identifying bottlenecks, and turning complexity into clarity.
      </div>
      <div class="bio-highlight">
        &gt; currently: building things that scale, learning things that don't expire
      </div>
      <div style="margin-top:1rem">
        <div class="card-label" style="margin-bottom:0.5rem">INTERESTS</div>
        <div style="display:flex;flex-wrap:wrap;gap:5px">
          <span style="font-family:'JetBrains Mono',monospace;font-size:0.65rem;background:var(--red-dim);border:1px solid var(--red-border);color:var(--red-bright);padding:3px 8px;border-radius:3px">UI Architecture</span>
          <span style="font-family:'JetBrains Mono',monospace;font-size:0.65rem;background:var(--red-dim);border:1px solid var(--red-border);color:var(--red-bright);padding:3px 8px;border-radius:3px">Systems Design</span>
          <span style="font-family:'JetBrains Mono',monospace;font-size:0.65rem;background:var(--red-dim);border:1px solid var(--red-border);color:var(--red-bright);padding:3px 8px;border-radius:3px">UX Research</span>
          <span style="font-family:'JetBrains Mono',monospace;font-size:0.65rem;background:var(--red-dim);border:1px solid var(--red-border);color:var(--red-bright);padding:3px 8px;border-radius:3px">Data Modeling</span>
          <span style="font-family:'JetBrains Mono',monospace;font-size:0.65rem;background:var(--red-dim);border:1px solid var(--red-border);color:var(--red-bright);padding:3px 8px;border-radius:3px">Open Source</span>
        </div>
      </div>
    </div>
  </div>

  <!-- ═══════════════ ANALYTICS ═══════════════ -->
  <div class="analytics-row">
    <div class="analytics-label">ANALYTICS DASHBOARD — LIVE METRICS</div>

    <div class="stats-grid">

      <!-- commits -->
      <div class="stat-card" style="--i:0">
        <div class="card-corner tl"></div>
        <div class="card-corner br"></div>
        <div class="card-label" style="justify-content:center;margin-bottom:0.75rem">COMMIT STREAK</div>
        <div class="stat-number">47<span>d</span></div>
        <div class="stat-label">current streak</div>
        <div class="streak-bar" id="streakBar"></div>
        <div class="stat-sub" style="margin-top:0.5rem">longest: 91 days</div>
      </div>

      <!-- visitors -->
      <div class="stat-card" style="--i:1">
        <div class="card-corner tl"></div>
        <div class="card-corner br"></div>
        <div class="card-label" style="justify-content:center;margin-bottom:0.75rem">PROFILE VIEWS</div>
        <div class="visitor-count" id="visitorCount">0</div>
        <div class="stat-label">total visitors</div>
        <div style="margin-top:0.6rem;display:flex;justify-content:center;gap:1rem">
          <div style="text-align:center">
            <div style="font-family:'JetBrains Mono',monospace;font-size:1rem;font-weight:700;color:var(--text-primary)">+24</div>
            <div class="stat-sub">today</div>
          </div>
          <div style="width:1px;background:var(--red-border)"></div>
          <div style="text-align:center">
            <div style="font-family:'JetBrains Mono',monospace;font-size:1rem;font-weight:700;color:var(--text-primary)">+186</div>
            <div class="stat-sub">this week</div>
          </div>
        </div>
        <div style="margin-top:0.75rem;height:30px;position:relative;overflow:hidden">
          <canvas id="sparkline" width="220" height="30" style="width:100%;height:100%"></canvas>
        </div>
      </div>

      <!-- github stats -->
      <div class="stat-card" style="--i:2">
        <div class="card-corner tl"></div>
        <div class="card-corner br"></div>
        <div class="card-label" style="justify-content:center;margin-bottom:0.75rem">GITHUB STATS</div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:0.5rem">
          <div style="text-align:center;padding:0.5rem;background:var(--red-dim);border:1px solid var(--red-border);border-radius:6px">
            <div style="font-family:'JetBrains Mono',monospace;font-size:1.3rem;font-weight:700;color:var(--text-primary)">842</div>
            <div class="stat-sub">commits</div>
          </div>
          <div style="text-align:center;padding:0.5rem;background:var(--red-dim);border:1px solid var(--red-border);border-radius:6px">
            <div style="font-family:'JetBrains Mono',monospace;font-size:1.3rem;font-weight:700;color:var(--text-primary)">34</div>
            <div class="stat-sub">repos</div>
          </div>
          <div style="text-align:center;padding:0.5rem;background:var(--red-dim);border:1px solid var(--red-border);border-radius:6px">
            <div style="font-family:'JetBrains Mono',monospace;font-size:1.3rem;font-weight:700;color:var(--text-primary)">127</div>
            <div class="stat-sub">stars</div>
          </div>
          <div style="text-align:center;padding:0.5rem;background:var(--red-dim);border:1px solid var(--red-border);border-radius:6px">
            <div style="font-family:'JetBrains Mono',monospace;font-size:1.3rem;font-weight:700;color:var(--text-primary)">18</div>
            <div class="stat-sub">PRs</div>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- ═══════════════ LANGUAGES + ACTIVITY ═══════════════ -->
  <div class="footer-row">

    <!-- languages -->
    <div class="card">
      <div class="card-corner tl"></div>
      <div class="card-corner br"></div>
      <div class="card-label">MODULE_03 — LANGUAGES</div>
      <div class="lang-chart">
        <div class="lang-bar-row">
          <div class="lang-name">JavaScript</div>
          <div class="lang-track"><div class="lang-fill" style="width:38%;--delay:0.5s"></div></div>
          <div class="lang-pct">38%</div>
        </div>
        <div class="lang-bar-row">
          <div class="lang-name">TypeScript</div>
          <div class="lang-track"><div class="lang-fill" style="width:28%;--delay:0.65s"></div></div>
          <div class="lang-pct">28%</div>
        </div>
        <div class="lang-bar-row">
          <div class="lang-name">CSS</div>
          <div class="lang-track"><div class="lang-fill alt" style="width:18%;--delay:0.8s"></div></div>
          <div class="lang-pct">18%</div>
        </div>
        <div class="lang-bar-row">
          <div class="lang-name">HTML</div>
          <div class="lang-track"><div class="lang-fill dim" style="width:10%;--delay:0.95s"></div></div>
          <div class="lang-pct">10%</div>
        </div>
        <div class="lang-bar-row">
          <div class="lang-name">SQL</div>
          <div class="lang-track"><div class="lang-fill dim" style="width:6%;--delay:1.1s"></div></div>
          <div class="lang-pct">6%</div>
        </div>
      </div>

      <!-- mini donut vis -->
      <div style="margin-top:1rem;display:flex;justify-content:center">
        <svg viewBox="0 0 120 60" style="width:100%;max-width:220px">
          <!-- donut arcs (decorative) -->
          <circle cx="60" cy="60" r="44" fill="none" stroke="rgba(255,34,68,0.1)" stroke-width="12"/>
          <circle cx="60" cy="60" r="44" fill="none" stroke="#ff2244" stroke-width="12"
            stroke-dasharray="104 172" stroke-dashoffset="-43" stroke-linecap="round"
            style="filter:drop-shadow(0 0 4px rgba(255,34,68,0.6))"/>
          <circle cx="60" cy="60" r="44" fill="none" stroke="rgba(255,34,68,0.5)" stroke-width="12"
            stroke-dasharray="77 172" stroke-dashoffset="-147" stroke-linecap="round"/>
          <circle cx="60" cy="60" r="44" fill="none" stroke="rgba(255,34,68,0.25)" stroke-width="12"
            stroke-dasharray="49 172" stroke-dashoffset="-224" stroke-linecap="round"/>
        </svg>
      </div>
    </div>

    <!-- activity feed -->
    <div class="card">
      <div class="card-corner tl"></div>
      <div class="card-corner br"></div>
      <div class="card-label">MODULE_04 — RECENT ACTIVITY</div>
      <div id="activityFeed" style="display:flex;flex-direction:column;gap:0.6rem"></div>
    </div>

  </div>

  <!-- ═══════════════ STATUS BAR ═══════════════ -->
  <div class="status-bar">
    <div class="status-item"><span class="dot green"></span>SYSTEM ONLINE</div>
    <div class="status-item"><span class="dot"></span>OPEN TO OPPORTUNITIES</div>
    <div class="status-item"><span class="dot"></span>AVAILABLE FOR COLLAB</div>
    <div class="status-spacer"></div>
    <div class="status-right" id="statusTime">──</div>
  </div>

</div><!-- /wrapper -->

<script>
/* typing animation */
const msg = 'System initialized: Aspiring Software Engineer & UI/UX Specialist online.';
let i = 0;
const el = document.getElementById('typed-text');
function type() {
  if (i <= msg.length) {
    el.textContent = msg.slice(0, i);
    i++;
    setTimeout(type, i === 1 ? 600 : 36 + Math.random() * 24);
  }
}
setTimeout(type, 900);

/* streak cells */
const streak = document.getElementById('streakBar');
const pattern = [1,1,1,0,1,1,1,1,0,1,1,1,1,1,0,1,1,1,1,1,1,1,0,1,1,1,1,1,1,1,1,1,1,1,0,1,1,1,1,1,1,1,1,1,1,1,1,1];
pattern.forEach((v, idx) => {
  const c = document.createElement('div');
  c.className = 'streak-cell' + (v && idx >= pattern.length - 47 ? ' active' : v ? ' mid' : '');
  streak.appendChild(c);
});

/* visitor counter */
const vc = document.getElementById('visitorCount');
let count = 0, target = 3847;
const step = Math.ceil(target / 60);
const counter = setInterval(() => {
  count = Math.min(count + step, target);
  vc.textContent = count.toLocaleString();
  if (count >= target) clearInterval(counter);
}, 25);

/* sparkline */
function drawSparkline() {
  const canvas = document.getElementById('sparkline');
  const ctx = canvas.getContext('2d');
  const data = [12,8,19,24,14,30,22,28,20,35,24,38,31,42,28,36,44,38,48,44,52,40,58,52,62];
  const w = canvas.width, h = canvas.height;
  const max = Math.max(...data), min = Math.min(...data);
  const scaleY = v => h - ((v - min) / (max - min)) * (h * 0.85) - h * 0.08;
  const scaleX = i => (i / (data.length - 1)) * w;

  ctx.clearRect(0, 0, w, h);
  ctx.beginPath();
  ctx.moveTo(scaleX(0), scaleY(data[0]));
  for (let j = 1; j < data.length; j++) {
    const cx = (scaleX(j - 1) + scaleX(j)) / 2;
    ctx.bezierCurveTo(cx, scaleY(data[j-1]), cx, scaleY(data[j]), scaleX(j), scaleY(data[j]));
  }
  const grad = ctx.createLinearGradient(0, 0, w, 0);
  grad.addColorStop(0, 'rgba(255,34,68,0.3)');
  grad.addColorStop(1, '#ff2244');
  ctx.strokeStyle = grad;
  ctx.lineWidth = 1.5;
  ctx.stroke();

  // fill
  ctx.lineTo(w, h); ctx.lineTo(0, h); ctx.closePath();
  const fillGrad = ctx.createLinearGradient(0, 0, 0, h);
  fillGrad.addColorStop(0, 'rgba(255,34,68,0.15)');
  fillGrad.addColorStop(1, 'rgba(255,34,68,0)');
  ctx.fillStyle = fillGrad;
  ctx.fill();
}
setTimeout(drawSparkline, 200);

/* activity feed */
const activities = [
  { type: 'commit', icon: '◈', text: 'feat: redesign dashboard layout', repo: 'portfolio-v3', time: '2h ago' },
  { type: 'push',   icon: '↑', text: 'fix: mobile nav overflow bug', repo: 'nextjs-ecom', time: '5h ago' },
  { type: 'pr',     icon: '⎇', text: 'PR merged: auth flow refactor', repo: 'node-api', time: '1d ago' },
  { type: 'star',   icon: '★', text: 'starred shadcn/ui', repo: null, time: '2d ago' },
  { type: 'commit', icon: '◈', text: 'chore: update MySQL schema', repo: 'db-layer', time: '3d ago' },
];

const feed = document.getElementById('activityFeed');
activities.forEach((a, idx) => {
  const item = document.createElement('div');
  item.style.cssText = `display:flex;align-items:flex-start;gap:8px;padding:8px;background:var(--red-dim);border:1px solid rgba(255,34,68,0.15);border-radius:6px;animation:fadeIn 0.4s ${0.8 + idx*0.1}s ease both;opacity:0;transition:border-color 0.2s,background 0.2s;cursor:default`;
  item.onmouseenter = () => { item.style.borderColor = 'rgba(255,34,68,0.4)'; item.style.background = 'rgba(255,34,68,0.12)'; };
  item.onmouseleave = () => { item.style.borderColor = 'rgba(255,34,68,0.15)'; item.style.background = 'var(--red-dim)'; };

  item.innerHTML = `
    <span style="font-family:'JetBrains Mono',monospace;font-size:0.8rem;color:var(--red-bright);flex-shrink:0;margin-top:1px">${a.icon}</span>
    <div style="flex:1;min-width:0">
      <div style="font-family:'JetBrains Mono',monospace;font-size:0.68rem;color:var(--text-primary);white-space:nowrap;overflow:hidden;text-overflow:ellipsis">${a.text}</div>
      <div style="font-family:'JetBrains Mono',monospace;font-size:0.6rem;color:var(--text-muted);margin-top:2px">${a.repo ? `<span style="color:var(--red-bright)">${a.repo}</span> · ` : ''}${a.time}</div>
    </div>
  `;
  feed.appendChild(item);
});

/* live clock */
function updateTime() {
  const now = new Date();
  const t = now.toLocaleTimeString('en-GB', { hour12: false });
  document.getElementById('statusTime').textContent = `UTC ${t} | v2.4.1`;
}
updateTime();
setInterval(updateTime, 1000);
</script>
</body>
</html>
