<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Your Name — GitHub Dashboard</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&family=Sora:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css" />
  <style>
    :root {
      --bg: #0d0f14;
      --bg2: #13161e;
      --bg3: #1a1d27;
      --border: rgba(255,255,255,0.07);
      --border2: rgba(255,255,255,0.13);
      --text: #e8eaf0;
      --text2: #8b8fa8;
      --text3: #555870;
      --accent: #6ee7b7;
      --accent2: #818cf8;
      --accent3: #f472b6;
      --green: #4ade80;
      --yellow: #facc15;
      --orange: #fb923c;
      --red: #f87171;
      --teal: #22d3ee;
      --purple: #a78bfa;
      --c-html: #4ade80;
      --c-js: #facc15;
      --c-angular: #f87171;
      --c-python: #818cf8;
      --c-nodejs: #6ee7b7;
      --c-php: #fb923c;
      --c-mysql: #f472b6;
      --c-git: #94a3b8;
      --radius: 12px;
      --radius-sm: 8px;
      --font-mono: 'JetBrains Mono', monospace;
      --font-sans: 'Sora', sans-serif;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--font-sans);
      min-height: 100vh;
      line-height: 1.6;
    }

    .page {
      max-width: 900px;
      margin: 0 auto;
      padding: 3rem 1.5rem 4rem;
    }

    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(110,231,183,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(110,231,183,0.03) 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      z-index: 0;
    }
    .page { position: relative; z-index: 1; }

    .card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.5rem;
      transition: border-color 0.2s;
    }
    .card:hover { border-color: var(--border2); }

    .section-label {
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--accent);
      letter-spacing: 0.12em;
      text-transform: uppercase;
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 1.25rem;
    }
    .section-label::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    .hero {
      display: grid;
      grid-template-columns: auto 1fr;
      gap: 2rem;
      align-items: center;
      margin-bottom: 2rem;
      padding: 2rem;
    }

    .avatar-wrap { position: relative; }
    .avatar {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background: var(--bg3);
      border: 2px solid var(--border2);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 32px;
      font-weight: 600;
      color: var(--accent);
      font-family: var(--font-mono);
      position: relative;
      z-index: 1;
    }
    .avatar-ring {
      position: absolute;
      inset: -6px;
      border-radius: 50%;
      border: 1px dashed var(--accent);
      opacity: 0.4;
      animation: spin 12s linear infinite;
    }
    .avatar-dot {
      position: absolute;
      bottom: 4px;
      right: 4px;
      width: 14px;
      height: 14px;
      border-radius: 50%;
      background: var(--green);
      border: 2px solid var(--bg2);
      z-index: 2;
    }
    @keyframes spin { to { transform: rotate(360deg); } }

    .hero-name { font-size: 28px; font-weight: 600; color: var(--text); }
    .hero-tag {
      font-family: var(--font-mono);
      font-size: 13px;
      color: var(--accent2);
      margin-top: 4px;
    }
    .hero-loc {
      font-size: 13px;
      color: var(--text3);
      margin-top: 6px;
      display: flex;
      align-items: center;
      gap: 4px;
    }

    .typing-line {
      font-family: var(--font-mono);
      font-size: 13px;
      color: var(--text2);
      margin-top: 10px;
      min-height: 20px;
    }
    .cursor {
      display: inline-block;
      width: 2px;
      height: 13px;
      background: var(--accent);
      vertical-align: middle;
      animation: blink 0.8s step-end infinite;
    }
    @keyframes blink { 50% { opacity: 0; } }

    .badges {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 14px;
    }
    .badge {
      font-family: var(--font-mono);
      font-size: 11px;
      padding: 4px 12px;
      border-radius: 99px;
      border: 1px solid var(--border2);
      color: var(--text2);
      background: var(--bg3);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 5px;
      transition: border-color 0.2s, color 0.2s;
    }
    .badge:hover { border-color: var(--accent); color: var(--accent); }

    .stats-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 12px;
      margin-bottom: 2rem;
    }
    .stat-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.25rem 1rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .stat-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
    }
    .stat-card.s1::before { background: var(--accent); }
    .stat-card.s2::before { background: var(--accent2); }
    .stat-card.s3::before { background: var(--accent3); }
    .stat-card.s4::before { background: var(--yellow); }
    .stat-num {
      font-family: var(--font-mono);
      font-size: 28px;
      font-weight: 600;
      color: var(--text);
    }
    .stat-label {
      font-size: 11px;
      color: var(--text3);
      margin-top: 4px;
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    .two-col {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem;
      margin-bottom: 2rem;
    }

    .skill-row { margin-bottom: 12px; }
    .skill-meta {
      display: flex;
      justify-content: space-between;
      font-family: var(--font-mono);
      font-size: 12px;
      color: var(--text2);
      margin-bottom: 5px;
    }
    .skill-pct { color: var(--text3); }
    .skill-track {
      height: 4px;
      background: var(--bg3);
      border-radius: 99px;
      overflow: hidden;
    }
    .skill-bar {
      height: 100%;
      border-radius: 99px;
      width: 0;
      transition: width 1.4s cubic-bezier(0.4,0,0.2,1);
    }

    .donut-wrap { display: flex; flex-direction: column; gap: 1rem; }
    .donut-canvas-wrap {
      position: relative;
      width: 140px;
      height: 140px;
      margin: 0 auto;
    }
    .donut-center {
      position: absolute;
      inset: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    .donut-center-num {
      font-family: var(--font-mono);
      font-size: 20px;
      font-weight: 600;
      color: var(--text);
    }
    .donut-center-lbl { font-size: 10px; color: var(--text3); }
    .lang-legend { display: flex; flex-direction: column; gap: 6px; }
    .lang-row {
      display: flex;
      align-items: center;
      gap: 8px;
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text2);
    }
    .lang-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
    .lang-pct { margin-left: auto; color: var(--text3); }

    .activity-section { margin-bottom: 2rem; }
    .activity-grid {
      display: grid;
      grid-template-columns: repeat(26, 1fr);
      gap: 3px;
    }
    .act-cell {
      aspect-ratio: 1;
      border-radius: 2px;
      background: var(--bg3);
      transition: transform 0.1s, opacity 0.1s;
      cursor: default;
    }
    .act-cell:hover { transform: scale(1.5); opacity: 0.9; }
    .act-1 { background: #14532d; }
    .act-2 { background: #16a34a; }
    .act-3 { background: #4ade80; }
    .act-4 { background: #86efac; }
    .legend-row {
      display: flex;
      align-items: center;
      gap: 5px;
      justify-content: flex-end;
      margin-top: 8px;
    }
    .legend-cell { width: 10px; height: 10px; border-radius: 2px; }
    .legend-txt { font-family: var(--font-mono); font-size: 10px; color: var(--text3); }

    .streak-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
    }
    .streak-card {
      background: var(--bg3);
      border-radius: var(--radius-sm);
      padding: 1rem;
      text-align: center;
      border: 1px solid var(--border);
    }
    .streak-num {
      font-family: var(--font-mono);
      font-size: 22px;
      font-weight: 600;
      color: var(--text);
    }
    .streak-lbl { font-size: 11px; color: var(--text3); margin-top: 3px; }

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 1rem;
      margin-bottom: 2rem;
    }
    .proj-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1.25rem;
      display: flex;
      flex-direction: column;
      gap: 10px;
      transition: border-color 0.2s, transform 0.2s;
    }
    .proj-card:hover { border-color: var(--border2); transform: translateY(-2px); }
    .proj-top { display: flex; align-items: center; gap: 10px; }
    .proj-icon {
      width: 34px; height: 34px;
      border-radius: var(--radius-sm);
      display: flex; align-items: center; justify-content: center;
      font-size: 16px; flex-shrink: 0;
    }
    .proj-name { font-size: 14px; font-weight: 500; color: var(--text); }
    .proj-desc { font-size: 12px; color: var(--text2); line-height: 1.6; }
    .proj-tags { display: flex; flex-wrap: wrap; gap: 5px; }
    .proj-tag {
      font-family: var(--font-mono);
      font-size: 10px;
      padding: 2px 8px;
      border-radius: 99px;
      border: 1px solid var(--border2);
      color: var(--text3);
    }
    .proj-footer {
      display: flex;
      gap: 12px;
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text3);
      margin-top: auto;
    }
    .proj-footer span { display: flex; align-items: center; gap: 3px; }

    .cert-list { display: flex; flex-direction: column; gap: 10px; margin-bottom: 2rem; }
    .cert-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 1rem 1.25rem;
      display: flex;
      align-items: center;
      gap: 14px;
      transition: border-color 0.2s;
    }
    .cert-card:hover { border-color: var(--border2); }
    .cert-icon {
      width: 38px; height: 38px;
      border-radius: var(--radius-sm);
      display: flex; align-items: center; justify-content: center;
      font-size: 18px; flex-shrink: 0;
    }
    .cert-name { font-size: 13px; font-weight: 500; color: var(--text); }
    .cert-issuer { font-size: 11px; color: var(--text3); margin-top: 2px; }
    .cert-year {
      margin-left: auto;
      font-family: var(--font-mono);
      font-size: 11px;
      padding: 3px 10px;
      border-radius: 99px;
      border: 1px solid var(--border2);
      color: var(--text3);
      white-space: nowrap;
    }

    .footer {
      text-align: center;
      font-family: var(--font-mono);
      font-size: 11px;
      color: var(--text3);
      margin-top: 3rem;
      padding-top: 1.5rem;
      border-top: 1px solid var(--border);
    }

    @media (max-width: 640px) {
      .hero { grid-template-columns: 1fr; text-align: center; }
      .badges { justify-content: center; }
      .stats-grid { grid-template-columns: repeat(2, 1fr); }
      .two-col { grid-template-columns: 1fr; }
      .projects-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
<div class="page">

  <!-- HERO -->
  <div class="card hero">
    <div class="avatar-wrap">
      <div class="avatar">YN</div>
      <div class="avatar-ring"></div>
      <div class="avatar-dot"></div>
    </div>
    <div class="hero-info">
      <div class="hero-name">Your Name Here</div>
      <div class="hero-tag">// Full Stack Developer & CS Student</div>
      <div class="hero-loc"><i class="ti ti-map-pin"></i> Your City, India</div>
      <div class="typing-line"><span id="typing-text"></span><span class="cursor"></span></div>
      <div class="badges">
        <a href="https://github.com/username" class="badge" target="_blank"><i class="ti ti-brand-github"></i> github/username</a>
        <a href="https://linkedin.com/in/username" class="badge" target="_blank"><i class="ti ti-brand-linkedin"></i> linkedin/username</a>
        <a href="mailto:your@email.com" class="badge"><i class="ti ti-mail"></i> your@email.com</a>
        <a href="https://x.com/yourhandle" class="badge" target="_blank"><i class="ti ti-brand-twitter"></i> @yourhandle</a>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-grid">
    <div class="stat-card s1"><div class="stat-num" id="repos-count">0</div><div class="stat-label">Repositories</div></div>
    <div class="stat-card s2"><div class="stat-num" id="commit-count">0</div><div class="stat-label">Commits this year</div></div>
    <div class="stat-card s3"><div class="stat-num" id="streak-count">0</div><div class="stat-label">Day streak</div></div>
    <div class="stat-card s4"><div class="stat-num" id="stars-count">0</div><div class="stat-label">Total stars</div></div>
  </div>

  <!-- SKILLS + DONUT -->
  <div class="two-col">
    <div class="card">
      <div class="section-label"><i class="ti ti-code"></i> Tech skills</div>
      <div class="skill-row"><div class="skill-meta"><span>HTML / CSS</span><span class="skill-pct">90%</span></div><div class="skill-track"><div class="skill-bar" data-width="90%" style="background:var(--c-html)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>JavaScript</span><span class="skill-pct">80%</span></div><div class="skill-track"><div class="skill-bar" data-width="80%" style="background:var(--c-js)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>Angular</span><span class="skill-pct">72%</span></div><div class="skill-track"><div class="skill-bar" data-width="72%" style="background:var(--c-angular)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>Python</span><span class="skill-pct">75%</span></div><div class="skill-track"><div class="skill-bar" data-width="75%" style="background:var(--c-python)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>Node.js</span><span class="skill-pct">68%</span></div><div class="skill-track"><div class="skill-bar" data-width="68%" style="background:var(--c-nodejs)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>PHP</span><span class="skill-pct">60%</span></div><div class="skill-track"><div class="skill-bar" data-width="60%" style="background:var(--c-php)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>MySQL</span><span class="skill-pct">65%</span></div><div class="skill-track"><div class="skill-bar" data-width="65%" style="background:var(--c-mysql)"></div></div></div>
      <div class="skill-row"><div class="skill-meta"><span>Git / GitHub</span><span class="skill-pct">78%</span></div><div class="skill-track"><div class="skill-bar" data-width="78%" style="background:var(--c-git)"></div></div></div>
    </div>

    <div class="card">
      <div class="section-label"><i class="ti ti-chart-donut"></i> Language split</div>
      <div class="donut-wrap">
        <div class="donut-canvas-wrap">
          <canvas id="donut-canvas" width="140" height="140"></canvas>
          <div class="donut-center">
            <div class="donut-center-num">5</div>
            <div class="donut-center-lbl">languages</div>
          </div>
        </div>
        <div class="lang-legend">
          <div class="lang-row"><div class="lang-dot" style="background:var(--c-html)"></div>HTML/CSS<span class="lang-pct">34%</span></div>
          <div class="lang-row"><div class="lang-dot" style="background:var(--c-js)"></div>JavaScript<span class="lang-pct">28%</span></div>
          <div class="lang-row"><div class="lang-dot" style="background:var(--c-python)"></div>Python<span class="lang-pct">18%</span></div>
          <div class="lang-row"><div class="lang-dot" style="background:var(--c-angular)"></div>Angular/TS<span class="lang-pct">12%</span></div>
          <div class="lang-row"><div class="lang-dot" style="background:var(--c-php)"></div>PHP<span class="lang-pct">8%</span></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ACTIVITY GRID -->
  <div class="card activity-section">
    <div class="section-label"><i class="ti ti-chart-dots"></i> Contribution activity · last 26 weeks</div>
    <div class="activity-grid" id="activity-grid"></div>
    <div class="legend-row">
      <span class="legend-txt">less</span>
      <div class="legend-cell" style="background:var(--bg3)"></div>
      <div class="legend-cell" style="background:#14532d"></div>
      <div class="legend-cell" style="background:#16a34a"></div>
      <div class="legend-cell" style="background:#4ade80"></div>
      <div class="legend-cell" style="background:#86efac"></div>
      <span class="legend-txt">more</span>
    </div>
  </div>

  <!-- STREAK -->
  <div class="card" style="margin-top:1.5rem; margin-bottom:2rem;">
    <div class="section-label"><i class="ti ti-flame"></i> Streak stats</div>
    <div class="streak-grid">
      <div class="streak-card"><div class="streak-num" style="color:var(--accent)">45</div><div class="streak-lbl">Current streak</div></div>
      <div class="streak-card"><div class="streak-num" style="color:var(--accent2)">82</div><div class="streak-lbl">Longest streak</div></div>
      <div class="streak-card"><div class="streak-num" style="color:var(--accent3)">210</div><div class="streak-lbl">Total active days</div></div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section-label" style="margin-bottom:1rem;"><i class="ti ti-layout-grid"></i> Projects</div>
  <div class="projects-grid">

    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-icon" style="background:rgba(74,222,128,0.1);color:var(--green)"><i class="ti ti-world"></i></div>
        <div class="proj-name">Project Name 1</div>
      </div>
      <div class="proj-desc">Short description of this project. Replace with your own.</div>
      <div class="proj-tags">
        <span class="proj-tag">HTML/CSS</span>
        <span class="proj-tag">JavaScript</span>
        <span class="proj-tag">Node.js</span>
      </div>
      <div class="proj-footer">
        <span><i class="ti ti-star"></i> 0</span>
        <span><i class="ti ti-git-fork"></i> 0</span>
        <span style="color:var(--c-js)"><i class="ti ti-circle-filled"></i> JavaScript</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-icon" style="background:rgba(129,140,248,0.1);color:var(--purple)"><i class="ti ti-server"></i></div>
        <div class="proj-name">Project Name 2</div>
      </div>
      <div class="proj-desc">Short description of this project. Replace with your own.</div>
      <div class="proj-tags">
        <span class="proj-tag">Python</span>
        <span class="proj-tag">MySQL</span>
        <span class="proj-tag">REST API</span>
      </div>
      <div class="proj-footer">
        <span><i class="ti ti-star"></i> 0</span>
        <span><i class="ti ti-git-fork"></i> 0</span>
        <span style="color:var(--c-python)"><i class="ti ti-circle-filled"></i> Python</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-icon" style="background:rgba(248,113,113,0.1);color:var(--red)"><i class="ti ti-device-mobile"></i></div>
        <div class="proj-name">Project Name 3</div>
      </div>
      <div class="proj-desc">Short description of this project. Replace with your own.</div>
      <div class="proj-tags">
        <span class="proj-tag">Angular</span>
        <span class="proj-tag">PHP</span>
        <span class="proj-tag">MySQL</span>
      </div>
      <div class="proj-footer">
        <span><i class="ti ti-star"></i> 0</span>
        <span><i class="ti ti-git-fork"></i> 0</span>
        <span style="color:var(--c-angular)"><i class="ti ti-circle-filled"></i> Angular</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-icon" style="background:rgba(110,231,183,0.1);color:var(--accent)"><i class="ti ti-database"></i></div>
        <div class="proj-name">Project Name 4</div>
      </div>
      <div class="proj-desc">Short description of this project. Replace with your own.</div>
      <div class="proj-tags">
        <span class="proj-tag">Node.js</span>
        <span class="proj-tag">MySQL</span>
        <span class="proj-tag">Git</span>
      </div>
      <div class="proj-footer">
        <span><i class="ti ti-star"></i> 0</span>
        <span><i class="ti ti-git-fork"></i> 0</span>
        <span style="color:var(--c-nodejs)"><i class="ti ti-circle-filled"></i> Node.js</span>
      </div>
    </div>

  </div>

  <!-- CERTIFICATIONS -->
  <div class="section-label" style="margin-bottom:1rem;"><i class="ti ti-certificate"></i> Certifications</div>
  <div class="cert-list">

    <div class="cert-card">
      <div class="cert-icon" style="background:rgba(34,211,238,0.1);color:var(--teal)"><i class="ti ti-shield-check"></i></div>
      <div>
        <div class="cert-name">Certification Name 1</div>
        <div class="cert-issuer">Issuer — e.g. Coursera / Google</div>
      </div>
      <span class="cert-year">2024</span>
    </div>

    <div class="cert-card">
      <div class="cert-icon" style="background:rgba(129,140,248,0.1);color:var(--accent2)"><i class="ti ti-code"></i></div>
      <div>
        <div class="cert-name">Certification Name 2</div>
        <div class="cert-issuer">Issuer — e.g. freeCodeCamp / IBM</div>
      </div>
      <span class="cert-year">2024</span>
    </div>

    <div class="cert-card">
      <div class="cert-icon" style="background:rgba(74,222,128,0.1);color:var(--green)"><i class="ti ti-brand-python"></i></div>
      <div>
        <div class="cert-name">Certification Name 3</div>
        <div class="cert-issuer">Issuer — e.g. Microsoft / AWS</div>
      </div>
      <span class="cert-year">2025</span>
    </div>

    <div class="cert-card">
      <div class="cert-icon" style="background:rgba(250,204,21,0.1);color:var(--yellow)"><i class="ti ti-trophy"></i></div>
      <div>
        <div class="cert-name">Certification Name 4</div>
        <div class="cert-issuer">Issuer — e.g. Oracle / Meta</div>
      </div>
      <span class="cert-year">2025</span>
    </div>

  </div>

  <!-- FOOTER -->
  <div class="footer">
    crafted by <span style="color:var(--accent)">Your Name</span> · open to opportunities · 2025
  </div>

</div>
<script>
  /* ── Typing animation ── */
  const typingLines = [
    "Building the web, one commit at a time.",
    "Student by day, coder by night.",
    "Passionate about full stack development.",
    "Always learning, always shipping."
  ];
  let li = 0, ci = 0, deleting = false;
  const el = document.getElementById('typing-text');
  function typeLoop() {
    const line = typingLines[li];
    if (!deleting) {
      el.textContent = line.slice(0, ++ci);
      if (ci === line.length) { deleting = true; setTimeout(typeLoop, 1800); return; }
    } else {
      el.textContent = line.slice(0, --ci);
      if (ci === 0) { deleting = false; li = (li + 1) % typingLines.length; }
    }
    setTimeout(typeLoop, deleting ? 35 : 65);
  }
  typeLoop();

  /* ── Counters ── */
  function animateCount(id, target) {
    const el = document.getElementById(id);
    let v = 0;
    const step = Math.ceil(target / 60);
    const t = setInterval(() => { v = Math.min(v + step, target); el.textContent = v; if (v >= target) clearInterval(t); }, 20);
  }
  animateCount('repos-count',  18);
  animateCount('commit-count', 342);
  animateCount('streak-count', 45);
  animateCount('stars-count',  12);

  /* ── Skill bars ── */
  setTimeout(() => {
    document.querySelectorAll('.skill-bar').forEach(b => { b.style.width = b.dataset.width; });
  }, 300);

  /* ── Activity grid ── */
  const levels = [
    0,0,0,1,0,1,2,0,1,1,2,3,1,2,0,3,2,1,4,2,3,1,2,4,3,2,
    1,0,2,1,3,2,0,1,2,3,1,4,2,1,3,2,1,0,3,2,4,3,1,2,
    0,0,1,2,1,0,2,1,3,2,1,2,3,4,2,1,3,2,0,1,2,3,1,2,
    3,2,4,1,2,0,1,2,3,2,1,4,2,3,1,2,3,0,1,2,4,3,2,1,
    2,3,1,0,2,1,3,2,1,0,2,3,4,2,1,3,0,1,2,1,3,2,4,1,
    2,0,1,2,3,1,2,4,3,2,1,2,3,1,4,2,3,0,1,2,3,2,1,4,
    0,0,1,2,0,1,2,0,1,1,2,3,1,0,0,3,2,1,4,2,3,1,0,4,3,2
  ];
  const grid = document.getElementById('activity-grid');
  levels.slice(0, 182).forEach(l => {
    const d = document.createElement('div');
    d.className = 'act-cell' + (l ? ' act-' + l : '');
    grid.appendChild(d);
  });

  /* ── Donut chart ── */
  setTimeout(() => {
    const canvas = document.getElementById('donut-canvas');
    const ctx = canvas.getContext('2d');
    const style = getComputedStyle(document.documentElement);
    const segments = [
      { pct: 34, color: style.getPropertyValue('--c-html').trim() },
      { pct: 28, color: style.getPropertyValue('--c-js').trim() },
      { pct: 18, color: style.getPropertyValue('--c-python').trim() },
      { pct: 12, color: style.getPropertyValue('--c-angular').trim() },
      { pct: 8,  color: style.getPropertyValue('--c-php').trim() }
    ];
    const cx = 70, cy = 70, r = 62, inner = 38;
    const total = segments.reduce((s, x) => s + x.pct, 0);
    let drawn = 0;
    function drawFrame() {
      ctx.clearRect(0, 0, 140, 140);
      let sa = -Math.PI / 2;
      const progress = Math.min(drawn / 100, 1);
      segments.forEach(seg => {
        const sweep = (seg.pct / total) * Math.PI * 2 * progress;
        const gap = 0.04;
        ctx.beginPath();
        ctx.moveTo(cx + Math.cos(sa + gap) * inner, cy + Math.sin(sa + gap) * inner);
        ctx.arc(cx, cy, r, sa + gap, sa + sweep - gap);
        ctx.arc(cx, cy, inner, sa + sweep - gap, sa + gap, true);
        ctx.closePath();
        ctx.fillStyle = seg.color;
        ctx.fill();
        sa += sweep;
      });
      drawn += 3;
      if (drawn <= 100) requestAnimationFrame(drawFrame);
    }
    drawFrame();
  }, 500);
</script>
</body>
</html>