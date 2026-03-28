<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Awais Sajid — GitHub Profile Preview</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Oxanium:wght@300;400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --g: #00ff88;
    --c: #00d4ff;
    --p: #a78bfa;
    --r: #ff6b6b;
    --bg: #060b14;
    --bg2: #0d1525;
    --bg3: #111d2e;
    --glass: rgba(13, 21, 37, 0.65);
    --border: rgba(0, 255, 136, 0.15);
    --border2: rgba(0, 212, 255, 0.12);
    --text: #e2e8f0;
    --muted: #64748b;
  }

  body {
    background: var(--bg);
    font-family: 'Oxanium', sans-serif;
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* AMBIENT BACKGROUND ORBS */
  body::before {
    content: '';
    position: fixed;
    top: -200px; left: -200px;
    width: 700px; height: 700px;
    background: radial-gradient(circle, rgba(0,255,136,0.06) 0%, transparent 70%);
    pointer-events: none; z-index: 0;
  }
  body::after {
    content: '';
    position: fixed;
    bottom: -200px; right: -200px;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(0,212,255,0.06) 0%, transparent 70%);
    pointer-events: none; z-index: 0;
  }

  .page { max-width: 860px; margin: 0 auto; padding: 0 24px 80px; position: relative; z-index: 1; }

  /* ── DOME HEADER ── */
  .dome-header {
    position: relative;
    text-align: center;
    padding: 70px 40px 50px;
    margin-bottom: 48px;
    overflow: hidden;
  }

  .dome-shell {
    position: absolute;
    inset: 0;
    border-radius: 0 0 50% 50% / 0 0 80px 80px;
    background: linear-gradient(180deg,
      rgba(0,255,136,0.04) 0%,
      rgba(0,212,255,0.03) 40%,
      transparent 100%);
    border: 1px solid rgba(0,255,136,0.1);
    border-top: none;
  }

  .dome-shell::before {
    content: '';
    position: absolute;
    top: 0; left: 50%; transform: translateX(-50%);
    width: 80%; height: 1px;
    background: linear-gradient(90deg, transparent, var(--g), var(--c), transparent);
  }

  .dome-shell::after {
    content: '';
    position: absolute;
    bottom: -1px; left: 10%; right: 10%;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(0,212,255,0.3), transparent);
  }

  /* Scanline texture */
  .dome-scan {
    position: absolute; inset: 0;
    background: repeating-linear-gradient(0deg,
      transparent,
      transparent 3px,
      rgba(0,255,136,0.012) 3px,
      rgba(0,255,136,0.012) 4px
    );
    border-radius: inherit;
    pointer-events: none;
  }

  /* Corner brackets */
  .dome-corner { position: absolute; width: 20px; height: 20px; }
  .dome-corner.tl { top: 16px; left: 16px; border-top: 1.5px solid var(--g); border-left: 1.5px solid var(--g); }
  .dome-corner.tr { top: 16px; right: 16px; border-top: 1.5px solid var(--g); border-right: 1.5px solid var(--g); }
  .dome-corner.bl { bottom: 24px; left: 16px; border-bottom: 1.5px solid var(--c); border-left: 1.5px solid var(--c); }
  .dome-corner.br { bottom: 24px; right: 16px; border-bottom: 1.5px solid var(--c); border-right: 1.5px solid var(--c); }

  .status-dot {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px; color: var(--g);
    letter-spacing: 2px; text-transform: uppercase;
    margin-bottom: 20px;
  }
  .status-dot::before {
    content: '';
    width: 8px; height: 8px; border-radius: 50%;
    background: var(--g);
    box-shadow: 0 0 8px var(--g);
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }

  .hero-name {
    font-size: clamp(42px, 8vw, 72px);
    font-weight: 800;
    letter-spacing: -1px;
    line-height: 1;
    background: linear-gradient(135deg, #ffffff 0%, var(--g) 50%, var(--c) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 12px;
  }

  .hero-title {
    font-size: 15px;
    font-weight: 300;
    color: var(--c);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 28px;
  }

  .hero-badges {
    display: flex; flex-wrap: wrap; gap: 10px;
    justify-content: center;
  }

  .badge {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 5px 14px;
    font-size: 11px; font-weight: 600;
    letter-spacing: 1px; text-transform: uppercase;
    font-family: 'Share Tech Mono', monospace;
    border-radius: 3px;
    border: 1px solid;
    position: relative;
    overflow: hidden;
  }
  .badge::before {
    content: '';
    position: absolute; inset: 0;
    background: currentColor;
    opacity: 0.07;
  }
  .badge.green { color: var(--g); border-color: rgba(0,255,136,0.3); }
  .badge.cyan  { color: var(--c); border-color: rgba(0,212,255,0.3); }
  .badge.purple{ color: var(--p); border-color: rgba(167,139,250,0.3); }
  .badge.red   { color: var(--r); border-color: rgba(255,107,107,0.3); }

  /* ── SECTION HEADER ── */
  .section-label {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 20px;
  }
  .section-label .cmd {
    font-family: 'Share Tech Mono', monospace;
    font-size: 13px; color: var(--g);
  }
  .section-label .cmd span { color: var(--c); }
  .section-label::after {
    content: '';
    flex: 1; height: 1px;
    background: linear-gradient(90deg, rgba(0,255,136,0.2), transparent);
  }

  /* ── GLASS PANEL ── */
  .glass {
    background: var(--glass);
    border: 1px solid var(--border);
    border-radius: 12px;
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    padding: 24px;
    position: relative;
    overflow: hidden;
  }
  .glass::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--g), var(--c), transparent);
    opacity: 0.4;
  }

  /* ── TWO COLUMN LAYOUT ── */
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 24px; }
  .three-col { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 16px; margin-bottom: 24px; }

  /* ── TERMINAL BLOCK ── */
  .terminal {
    background: rgba(6, 11, 20, 0.8);
    border: 1px solid rgba(0,255,136,0.1);
    border-radius: 8px;
    padding: 20px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 12px;
    line-height: 1.8;
  }
  .terminal .prompt { color: var(--g); }
  .terminal .key    { color: var(--c); }
  .terminal .val    { color: var(--text); }
  .terminal .comment{ color: var(--muted); }

  /* ── STAT CARDS ── */
  .stat-card {
    background: rgba(0,255,136,0.04);
    border: 1px solid rgba(0,255,136,0.12);
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, border-color 0.2s;
  }
  .stat-card:hover { transform: translateY(-3px); border-color: rgba(0,255,136,0.3); }
  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--g), var(--c));
    opacity: 0.5;
  }
  .stat-num  { font-size: 32px; font-weight: 800; color: var(--g); line-height: 1; margin-bottom: 6px; }
  .stat-lbl  { font-size: 10px; letter-spacing: 2px; text-transform: uppercase; color: var(--muted); font-family: 'Share Tech Mono', monospace; }

  /* ── SKILL ROWS ── */
  .skill-row {
    display: flex; align-items: center; gap: 14px;
    padding: 12px 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
  }
  .skill-row:last-child { border-bottom: none; }
  .skill-icon { font-size: 16px; width: 28px; text-align: center; }
  .skill-name { font-size: 12px; font-weight: 600; min-width: 140px; color: var(--c); letter-spacing: 1px; text-transform: uppercase; font-family: 'Share Tech Mono', monospace; }
  .skill-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-size: 10px; padding: 3px 8px;
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.15);
    border-radius: 3px; color: var(--c);
    font-family: 'Share Tech Mono', monospace;
    letter-spacing: 0.5px;
  }
  .tag.green { background: rgba(0,255,136,0.08); border-color: rgba(0,255,136,0.15); color: var(--g); }
  .tag.purple{ background: rgba(167,139,250,0.08); border-color: rgba(167,139,250,0.15); color: var(--p); }
  .tag.amber { background: rgba(251,191,36,0.08); border-color: rgba(251,191,36,0.15); color: #fbbf24; }

  /* ── REPO CARDS ── */
  .repo-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-bottom: 24px; }

  .repo-card {
    background: rgba(13, 21, 37, 0.8);
    border: 1px solid rgba(0,212,255,0.1);
    border-radius: 10px;
    padding: 18px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.2s, transform 0.2s;
    cursor: pointer;
  }
  .repo-card:hover { border-color: rgba(0,255,136,0.3); transform: translateY(-2px); }
  .repo-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; height: 2px;
    background: linear-gradient(90deg, var(--g), var(--c));
  }

  .repo-icon { font-size: 20px; margin-bottom: 10px; }
  .repo-name { font-size: 13px; font-weight: 700; color: #fff; margin-bottom: 6px; font-family: 'Share Tech Mono', monospace; }
  .repo-desc { font-size: 11px; color: var(--muted); line-height: 1.5; margin-bottom: 12px; }
  .repo-meta { display: flex; gap: 12px; align-items: center; }
  .repo-lang { display: flex; align-items: center; gap: 5px; font-size: 10px; color: var(--muted); font-family: 'Share Tech Mono', monospace; }
  .lang-dot { width: 10px; height: 10px; border-radius: 50%; }
  .repo-stars { font-size: 10px; color: var(--muted); font-family: 'Share Tech Mono', monospace; }

  /* ── ACTIVITY DOME ── */
  .activity-dome {
    position: relative;
    padding: 30px 24px 20px;
    margin-bottom: 24px;
    background: rgba(6,11,20,0.7);
    border: 1px solid rgba(0,255,136,0.1);
    border-radius: 10px 10px 50% 50% / 10px 10px 30px 30px;
    overflow: hidden;
  }
  .activity-dome::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent 5%, var(--g) 30%, var(--c) 70%, transparent 95%);
  }

  /* activity graph mock */
  .contrib-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 2px;
  }
  .contrib-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    background: rgba(0,255,136,0.06);
  }
  .contrib-cell.l1 { background: rgba(0,255,136,0.2); }
  .contrib-cell.l2 { background: rgba(0,255,136,0.4); }
  .contrib-cell.l3 { background: rgba(0,255,136,0.65); }
  .contrib-cell.l4 { background: rgba(0,255,136,0.9); }

  /* ── CONNECT SECTION ── */
  .connect-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 12px; }
  .connect-card {
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    padding: 18px 10px;
    background: rgba(13,21,37,0.8);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 10px;
    text-decoration: none;
    transition: border-color 0.2s, transform 0.2s;
    cursor: pointer;
  }
  .connect-card:hover { border-color: rgba(0,255,136,0.3); transform: translateY(-3px); }
  .connect-icon { font-size: 22px; }
  .connect-name { font-size: 9px; letter-spacing: 1.5px; text-transform: uppercase; color: var(--muted); font-family: 'Share Tech Mono', monospace; }

  /* ── FOOTER DOME ── */
  .footer-dome {
    text-align: center;
    padding: 40px 24px 30px;
    position: relative;
    overflow: hidden;
    margin-top: 48px;
  }
  .footer-dome-shell {
    position: absolute; inset: 0;
    border-radius: 50% 50% 0 0 / 60px 60px 0 0;
    background: linear-gradient(0deg, rgba(0,255,136,0.03), transparent);
    border: 1px solid rgba(0,212,255,0.1);
    border-bottom: none;
  }
  .footer-dome-shell::after {
    content: '';
    position: absolute; bottom: 0; left: 10%; right: 10%; height: 1px;
    background: linear-gradient(90deg, transparent, rgba(0,212,255,0.2), transparent);
  }
  .footer-text {
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    position: relative;
  }
  .footer-text span { color: var(--g); }

  /* ── DIVIDER ── */
  .divider { height: 1px; background: linear-gradient(90deg, transparent, rgba(0,255,136,0.15), rgba(0,212,255,0.15), transparent); margin: 32px 0; }

  /* STATS ROW */
  .stats-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; margin-bottom: 24px; }

  /* ACHIEVEMENT TABLE */
  .ach-table { width: 100%; border-collapse: collapse; }
  .ach-table tr { border-bottom: 1px solid rgba(255,255,255,0.04); }
  .ach-table tr:last-child { border-bottom: none; }
  .ach-table td { padding: 11px 8px; font-size: 13px; vertical-align: middle; }
  .ach-icon { font-size: 18px; width: 36px; }
  .ach-title { font-weight: 600; color: #fff; }
  .ach-detail { color: var(--muted); font-size: 12px; }

  /* TYPEWRITER */
  .typewriter { display: inline-block; overflow: hidden; white-space: nowrap; border-right: 2px solid var(--g); animation: type 3s steps(40, end) infinite alternate, blink 0.7s step-end infinite; }
  @keyframes type { from { width: 0; } to { width: 100%; } }
  @keyframes blink { 50% { border-color: transparent; } }
</style>
</head>
<body>
<div class="page">

  <!-- ══ DOME HEADER ══ -->
  <header class="dome-header">
    <div class="dome-shell"></div>
    <div class="dome-scan"></div>
    <div class="dome-corner tl"></div>
    <div class="dome-corner tr"></div>
    <div class="dome-corner bl"></div>
    <div class="dome-corner br"></div>

    <div class="status-dot">System Online · Islamabad, PK</div>
    <div class="hero-name">Awais Sajid</div>
    <div class="hero-title">Security Engineer · Threat Hunter · Detection Architect</div>
    <div class="hero-badges">
      <span class="badge green">⬡ Secure Networks</span>
      <span class="badge cyan">⬡ 2+ Yrs Experience</span>
      <span class="badge purple">⬡ MITRE ATT&CK</span>
      <span class="badge red">⬡ Open to Relocation</span>
    </div>
  </header>

  <!-- ══ ABOUT ══ -->
  <div class="section-label"><span class="cmd">$ <span>whoami</span></span></div>
  <div class="two-col" style="margin-bottom:24px">
    <div class="glass">
      <div class="terminal">
        <div><span class="prompt">▶ </span><span class="key">name</span><span class="val">        : Awais Sajid</span></div>
        <div><span class="prompt">▶ </span><span class="key">role</span><span class="val">        : Security Engineer</span></div>
        <div><span class="prompt">▶ </span><span class="key">company</span><span class="val">     : Secure Networks</span></div>
        <div><span class="prompt">▶ </span><span class="key">since</span><span class="val">       : Sep 2024</span></div>
        <div><span class="prompt">▶ </span><span class="key">location</span><span class="val">    : Islamabad, PK 🇵🇰</span></div>
        <div><span class="prompt">▶ </span><span class="key">degree</span><span class="val">      : B.S. Cyber Security</span></div>
        <div><span class="prompt">▶ </span><span class="key">university</span><span class="val">  : NUCES (2019–2023)</span></div>
        <div><span class="comment"># Available: UAE · KSA · Qatar · Malaysia · Remote</span></div>
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:14px">
      <div class="stats-row" style="display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:0">
        <div class="stat-card"><div class="stat-num">2+</div><div class="stat-lbl">Yrs Experience</div></div>
        <div class="stat-card"><div class="stat-num">3</div><div class="stat-lbl">Certifications</div></div>
        <div class="stat-card"><div class="stat-num">5+</div><div class="stat-lbl">Security Tools</div></div>
        <div class="stat-card"><div class="stat-num">100+</div><div class="stat-lbl">TryHackMe Rooms</div></div>
      </div>
    </div>
  </div>

  <!-- ══ SKILLS ══ -->
  <div class="section-label"><span class="cmd">$ <span>skills</span> --list-all</span></div>
  <div class="glass" style="margin-bottom:24px">
    <div class="skill-row">
      <span class="skill-icon">🔴</span>
      <span class="skill-name">SIEM / XDR</span>
      <div class="skill-tags">
        <span class="tag green">Wazuh</span>
        <span class="tag green">Trend Micro XDR</span>
        <span class="tag green">Vision One</span>
        <span class="tag green">Deep Security</span>
      </div>
    </div>
    <div class="skill-row">
      <span class="skill-icon">🟠</span>
      <span class="skill-name">Network Sec</span>
      <div class="skill-tags">
        <span class="tag">Palo Alto NGFW</span>
        <span class="tag">Infoblox BloxOne</span>
        <span class="tag">Threat Defense</span>
      </div>
    </div>
    <div class="skill-row">
      <span class="skill-icon">🟡</span>
      <span class="skill-name">Frameworks</span>
      <div class="skill-tags">
        <span class="tag purple">MITRE ATT&CK</span>
        <span class="tag purple">D3FEND</span>
        <span class="tag purple">Sigma Rules</span>
        <span class="tag purple">YARA</span>
      </div>
    </div>
    <div class="skill-row">
      <span class="skill-icon">🟢</span>
      <span class="skill-name">Compliance</span>
      <div class="skill-tags">
        <span class="tag amber">ISO 27001</span>
        <span class="tag amber">PCI-DSS</span>
        <span class="tag amber">SSAE-18</span>
      </div>
    </div>
    <div class="skill-row">
      <span class="skill-icon">🔵</span>
      <span class="skill-name">Scripting</span>
      <div class="skill-tags">
        <span class="tag">Python</span>
        <span class="tag">Bash</span>
        <span class="tag">PowerShell</span>
        <span class="tag">C++</span>
      </div>
    </div>
  </div>

  <!-- ══ REPOS ══ -->
  <div class="section-label"><span class="cmd">$ <span>git</span> log --pinned</span></div>
  <div class="repo-grid">
    <div class="repo-card">
      <div class="repo-icon">🔬</div>
      <div class="repo-name">[ YOUR-REPO-1 ]</div>
      <div class="repo-desc">Pin your repos on GitHub → github.com/asajid03 → Customize your pins</div>
      <div class="repo-meta">
        <div class="repo-lang"><span class="lang-dot" style="background:#3572A5"></span>Python</div>
        <div class="repo-stars">★ –</div>
      </div>
    </div>
    <div class="repo-card">
      <div class="repo-icon">🛡️</div>
      <div class="repo-name">[ YOUR-REPO-2 ]</div>
      <div class="repo-desc">Auto-rendered via github-readme-stats pin cards once repo names are set</div>
      <div class="repo-meta">
        <div class="repo-lang"><span class="lang-dot" style="background:#4EAA25"></span>Bash</div>
        <div class="repo-stars">★ –</div>
      </div>
    </div>
    <div class="repo-card">
      <div class="repo-icon">🧠</div>
      <div class="repo-name">[ YOUR-REPO-3 ]</div>
      <div class="repo-desc">Share your actual pinned repo names and I'll update the cards instantly</div>
      <div class="repo-meta">
        <div class="repo-lang"><span class="lang-dot" style="background:#f34b7d"></span>C++</div>
        <div class="repo-stars">★ –</div>
      </div>
    </div>
    <div class="repo-card">
      <div class="repo-icon">⛓️</div>
      <div class="repo-name">[ YOUR-REPO-4 ]</div>
      <div class="repo-desc">All stats, language, fork &amp; star counts auto-update from GitHub API</div>
      <div class="repo-meta">
        <div class="repo-lang"><span class="lang-dot" style="background:#f1e05a"></span>JavaScript</div>
        <div class="repo-stars">★ –</div>
      </div>
    </div>
  </div>

  <!-- ══ STATS DASHBOARD ══ -->
  <div class="section-label"><span class="cmd">$ <span>stats</span> --dashboard</span></div>
  <div class="activity-dome" style="margin-bottom:24px">
    <div style="font-size:11px;color:var(--muted);font-family:'Share Tech Mono',monospace;letter-spacing:2px;margin-bottom:14px;text-transform:uppercase">◈ Contribution Activity — asajid03</div>
    <div class="contrib-grid" id="grid"></div>
    <div style="font-size:10px;color:var(--muted);font-family:'Share Tech Mono',monospace;margin-top:10px;display:flex;gap:12px;justify-content:flex-end;align-items:center">
      <span>Less</span>
      <span style="display:flex;gap:3px">
        <span style="width:10px;height:10px;border-radius:2px;background:rgba(0,255,136,0.06);display:inline-block"></span>
        <span style="width:10px;height:10px;border-radius:2px;background:rgba(0,255,136,0.2);display:inline-block"></span>
        <span style="width:10px;height:10px;border-radius:2px;background:rgba(0,255,136,0.45);display:inline-block"></span>
        <span style="width:10px;height:10px;border-radius:2px;background:rgba(0,255,136,0.9);display:inline-block"></span>
      </span>
      <span>More</span>
    </div>
  </div>

  <!-- ══ ACHIEVEMENTS ══ -->
  <div class="section-label"><span class="cmd">$ <span>cat</span> achievements.log</span></div>
  <div class="glass" style="margin-bottom:24px">
    <table class="ach-table">
      <tr><td class="ach-icon">🥈</td><td><div class="ach-title">Runner-Up — Cyber Quiz Competition</div><div class="ach-detail">NESCON National Conference</div></td></tr>
      <tr><td class="ach-icon">🌐</td><td><div class="ach-title">Head of Cybersecurity</div><div class="ach-detail">Google Developer Student Club — NUCES Islamabad</div></td></tr>
      <tr><td class="ach-icon">🎓</td><td><div class="ach-title">National Merit Scholarship</div><div class="ach-detail">Nationwide — 8th Class</div></td></tr>
      <tr><td class="ach-icon">🔬</td><td><div class="ach-title">ML-Based Intrusion Detection System</div><div class="ach-detail">Academic Research Project</div></td></tr>
      <tr><td class="ach-icon">⛓️</td><td><div class="ach-title">Blockchain-Based Lottery System</div><div class="ach-detail">Academic Project — Smart Contracts</div></td></tr>
      <tr><td class="ach-icon">🔐</td><td><div class="ach-title">Lightweight TLS Secure Communication</div><div class="ach-detail">Protocol Implementation</div></td></tr>
    </table>
  </div>

  <!-- ══ CONNECT ══ -->
  <div class="section-label"><span class="cmd">$ <span>netstat</span> -connect</span></div>
  <div class="connect-grid">
    <a class="connect-card" href="https://linkedin.com/in/awais-sajid" target="_blank">
      <span class="connect-icon">💼</span>
      <span class="connect-name" style="color:#0a66c2">LinkedIn</span>
    </a>
    <a class="connect-card" href="mailto:awaissajid92260@gmail.com">
      <span class="connect-icon">📧</span>
      <span class="connect-name" style="color:#ea4335">Gmail</span>
    </a>
    <a class="connect-card" href="https://github.com/asajid03" target="_blank">
      <span class="connect-icon">🐙</span>
      <span class="connect-name" style="color:#fff">GitHub</span>
    </a>
    <a class="connect-card" href="https://tryhackme.com/p/asajid03" target="_blank">
      <span class="connect-icon">🎯</span>
      <span class="connect-name" style="color:#88cc14">TryHackMe</span>
    </a>
    <a class="connect-card" href="https://app.letsdefend.io/user/asajid03" target="_blank">
      <span class="connect-icon">🛡️</span>
      <span class="connect-name" style="color:#00aaff">LetsDefend</span>
    </a>
  </div>

  <!-- ══ FOOTER DOME ══ -->
  <div class="footer-dome">
    <div class="footer-dome-shell"></div>
    <div class="footer-text"><span>Defend.</span> &nbsp;·&nbsp; <span>Detect.</span> &nbsp;·&nbsp; <span>Respond.</span></div>
    <div style="font-family:'Share Tech Mono',monospace;font-size:10px;color:var(--muted);margin-top:10px;letter-spacing:2px">// asajid03 · 2026 · Made with ☕ &amp; too much caffeine</div>
  </div>

</div>

<script>
  // Generate contribution grid
  const grid = document.getElementById('grid');
  const levels = [0,0,0,0,0,1,1,2,2,3,4];
  for(let i = 0; i < 52*7; i++){
    const cell = document.createElement('div');
    cell.className = 'contrib-cell';
    const r = Math.random();
    if(r > 0.85){ const l = levels[Math.floor(Math.random()*levels.length)]; if(l) cell.classList.add('l'+l); }
    grid.appendChild(cell);
  }
</script>
</body>
</html>
