<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mazen Al-Azhary — Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0c10;
    --surface: #111419;
    --card: #161b22;
    --border: #21262d;
    --accent: #58a6ff;
    --accent2: #3fb950;
    --accent3: #f78166;
    --accent4: #d2a8ff;
    --text: #e6edf3;
    --muted: #8b949e;
    --mono: 'Space Mono', monospace;
    --sans: 'DM Sans', sans-serif;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    padding: 40px 20px;
  }

  /* Background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(88,166,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(88,166,255,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    max-width: 820px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  /* ── HERO ── */
  .hero {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 36px 36px 28px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 220px; height: 220px;
    background: radial-gradient(circle, rgba(88,166,255,0.15) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-top {
    display: flex;
    align-items: flex-start;
    gap: 20px;
    flex-wrap: wrap;
  }
  .avatar {
    width: 72px; height: 72px;
    border-radius: 50%;
    border: 2px solid var(--accent);
    background: linear-gradient(135deg, #1f3a5f, #2d5a27);
    display: flex; align-items: center; justify-content: center;
    font-family: var(--mono);
    font-size: 22px;
    color: var(--accent);
    flex-shrink: 0;
    box-shadow: 0 0 24px rgba(88,166,255,0.25);
  }
  .hero-text h1 {
    font-family: var(--mono);
    font-size: 22px;
    color: var(--text);
    letter-spacing: -0.5px;
  }
  .hero-text h1 span { color: var(--accent); }
  .hero-text .tagline {
    color: var(--muted);
    font-size: 13px;
    margin-top: 5px;
    font-family: var(--mono);
  }
  .badge-row {
    display: flex; gap: 8px; flex-wrap: wrap; margin-top: 12px;
  }
  .badge {
    background: rgba(88,166,255,0.1);
    border: 1px solid rgba(88,166,255,0.25);
    color: var(--accent);
    font-size: 11px;
    font-family: var(--mono);
    padding: 3px 10px;
    border-radius: 20px;
    letter-spacing: 0.3px;
  }
  .badge.green { background: rgba(63,185,80,0.1); border-color: rgba(63,185,80,0.25); color: var(--accent2); }
  .badge.purple { background: rgba(210,168,255,0.1); border-color: rgba(210,168,255,0.25); color: var(--accent4); }

  .hero-links {
    display: flex; gap: 12px; flex-wrap: wrap; margin-top: 18px;
  }
  .link-pill {
    display: flex; align-items: center; gap: 6px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 6px 12px;
    font-size: 12px;
    font-family: var(--mono);
    color: var(--muted);
    text-decoration: none;
    transition: all 0.2s;
  }
  .link-pill:hover { border-color: var(--accent); color: var(--accent); }
  .link-pill .dot {
    width: 7px; height: 7px; border-radius: 50%;
    background: currentColor; opacity: 0.7;
  }

  /* ── TWO-COL ── */
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
  @media(max-width: 600px){ .two-col { grid-template-columns: 1fr; } }

  /* ── CARD ── */
  .panel {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 22px 24px;
  }
  .panel-title {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1.5px;
    margin-bottom: 16px;
    display: flex; align-items: center; gap: 8px;
  }
  .panel-title::after {
    content: '';
    flex: 1; height: 1px; background: var(--border);
  }

  /* ── STAT BARS ── */
  .stat-item { margin-bottom: 14px; }
  .stat-item:last-child { margin-bottom: 0; }
  .stat-label {
    display: flex; justify-content: space-between;
    font-size: 12px; margin-bottom: 6px;
  }
  .stat-name { font-family: var(--mono); color: var(--text); }
  .stat-pct { font-family: var(--mono); color: var(--muted); font-size: 11px; }
  .bar-track {
    height: 5px; background: var(--border); border-radius: 99px; overflow: hidden;
  }
  .bar-fill {
    height: 100%; border-radius: 99px;
    animation: growBar 1.2s cubic-bezier(.4,0,.2,1) both;
  }
  @keyframes growBar { from { width: 0 !important; } }

  /* ── CONTRIBUTION HEATMAP ── */
  .heatmap-grid {
    display: grid;
    grid-template-columns: repeat(26, 1fr);
    gap: 3px;
    margin-top: 4px;
  }
  .heatmap-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    background: var(--border);
  }
  .h1 { background: #0e4429; }
  .h2 { background: #006d32; }
  .h3 { background: #26a641; }
  .h4 { background: #39d353; }
  .heatmap-legend {
    display: flex; align-items: center; gap: 5px;
    margin-top: 8px; justify-content: flex-end;
    font-size: 10px; color: var(--muted); font-family: var(--mono);
  }
  .heatmap-legend span {
    width: 10px; height: 10px; border-radius: 2px; display: inline-block;
  }

  /* ── STREAK ── */
  .streak-display {
    display: flex; gap: 12px; justify-content: space-around;
    margin-top: 4px;
  }
  .streak-box {
    text-align: center;
    padding: 14px 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    flex: 1;
  }
  .streak-num {
    font-family: var(--mono);
    font-size: 26px;
    font-weight: 700;
    line-height: 1;
    margin-bottom: 4px;
  }
  .streak-label { font-size: 10px; color: var(--muted); font-family: var(--mono); text-transform: uppercase; letter-spacing: 0.8px; }

  /* ── SKILLS GRID ── */
  .skills-grid {
    display: flex; flex-wrap: wrap; gap: 8px;
  }
  .skill-chip {
    display: flex; align-items: center; gap: 6px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 5px 10px;
    font-size: 12px;
    font-family: var(--mono);
    color: var(--muted);
    transition: all 0.2s;
    cursor: default;
  }
  .skill-chip:hover { border-color: var(--accent); color: var(--text); transform: translateY(-1px); }
  .skill-chip .icon { font-size: 15px; }

  /* ── SOCIAL ── */
  .social-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .social-item {
    display: flex; align-items: center; gap: 10px;
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 8px; padding: 10px 14px;
    text-decoration: none; color: var(--muted);
    font-size: 12px; font-family: var(--mono);
    transition: all 0.2s;
  }
  .social-item:hover { border-color: var(--accent); color: var(--accent); }
  .social-icon { font-size: 18px; }
  .social-meta { display: flex; flex-direction: column; gap: 1px; }
  .social-platform { font-size: 10px; color: var(--muted); }
  .social-handle { color: inherit; }

  /* ── CURRENTLY LEARNING ── */
  .learning-pills { display: flex; gap: 8px; flex-wrap: wrap; }
  .learn-pill {
    background: rgba(63,185,80,0.08);
    border: 1px solid rgba(63,185,80,0.2);
    border-radius: 6px;
    padding: 6px 14px;
    font-size: 12px; font-family: var(--mono);
    color: var(--accent2);
    display: flex; align-items: center; gap: 6px;
  }
  .learn-pill::before { content: '▶'; font-size: 8px; opacity: 0.6; }

  /* fade-in */
  .panel, .hero { animation: fadeUp 0.5s ease both; }
  .panel:nth-child(1) { animation-delay: 0.05s; }
  .panel:nth-child(2) { animation-delay: 0.1s; }
  @keyframes fadeUp { from { opacity:0; transform: translateY(12px); } to { opacity:1; transform: none; } }
</style>
</head>
<body>
<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-top">
      <div class="avatar">MA</div>
      <div class="hero-text">
        <h1>Hi 👋 I'm <span>Mazen Al-Azhary</span></h1>
        <div class="tagline">// Undergraduate Computer & Communication Engineer</div>
        <div class="badge-row">
          <span class="badge">Open to Work</span>
          <span class="badge green">🌱 Learning React & Node.js</span>
          <span class="badge purple">⚡ Competitive Programmer</span>
        </div>
      </div>
    </div>
    <div class="hero-links">
      <a class="link-pill" href="https://mazen-azhary.github.io/My_Portfolio/" target="_blank"><span class="dot"></span> Portfolio</a>
      <a class="link-pill" href="https://www.linkedin.com/in/mazen-al-azhary-b5808424b/" target="_blank"><span class="dot"></span> LinkedIn</a>
      <a class="link-pill" href="https://drive.google.com/file/d/1kkj3bXUawkyzM2I23yY-PFR4D_Fvrdr_/view?usp=sharing" target="_blank"><span class="dot"></span> Resume</a>
    </div>
  </div>

  <!-- TOP LANGUAGES + STREAK -->
  <div class="two-col">

    <div class="panel">
      <div class="panel-title">Top Languages</div>
      <div id="lang-bars">
        <!-- filled by JS -->
      </div>
    </div>

    <div class="panel">
      <div class="panel-title">Coding Activity</div>
      <div class="streak-display">
        <div class="streak-box">
          <div class="streak-num" style="color:var(--accent)">42</div>
          <div class="streak-label">Total Repos</div>
        </div>
        <div class="streak-box">
          <div class="streak-num" style="color:var(--accent2)">318</div>
          <div class="streak-label">Contributions</div>
        </div>
        <div class="streak-box">
          <div class="streak-num" style="color:var(--accent4)">14</div>
          <div class="streak-label">Day Streak</div>
        </div>
      </div>
    </div>

  </div>

  <!-- CONTRIBUTION HEATMAP -->
  <div class="panel">
    <div class="panel-title">Contribution Graph — Last 6 Months</div>
    <div class="heatmap-grid" id="heatmap"></div>
    <div class="heatmap-legend">
      Less <span style="background:var(--border)"></span>
      <span class="h1"></span><span class="h2"></span><span class="h3"></span><span class="h4"></span> More
    </div>
  </div>

  <!-- SKILLS -->
  <div class="panel">
    <div class="panel-title">Languages &amp; Tools</div>
    <div class="skills-grid" id="skills-grid"></div>
  </div>

  <!-- CURRENTLY LEARNING + SOCIALS -->
  <div class="two-col">

    <div class="panel">
      <div class="panel-title">Currently Learning</div>
      <div class="learning-pills">
        <span class="learn-pill">React</span>
        <span class="learn-pill">Node.js</span>
        <span class="learn-pill">GraphQL</span>
        <span class="learn-pill">Kubernetes</span>
        <span class="learn-pill">Kafka</span>
        <span class="learn-pill">Designing Data-Intensive Apps</span>
      </div>
    </div>

    <div class="panel">
      <div class="panel-title">Connect</div>
      <div class="social-grid">
        <a class="social-item" href="https://github.com/Mazen-Azhary" target="_blank">
          <span class="social-icon">⌥</span>
          <div class="social-meta">
            <span class="social-platform">GitHub</span>
            <span class="social-handle">Mazen-Azhary</span>
          </div>
        </a>
        <a class="social-item" href="https://codeforces.com/profile/Mazen_Azhary" target="_blank">
          <span class="social-icon">⚔</span>
          <div class="social-meta">
            <span class="social-platform">Codeforces</span>
            <span class="social-handle">Mazen_Azhary</span>
          </div>
        </a>
        <a class="social-item" href="https://linkedin.com/in/mazen-al-azhary-b5808424b" target="_blank">
          <span class="social-icon">◈</span>
          <div class="social-meta">
            <span class="social-platform">LinkedIn</span>
            <span class="social-handle">Mazen Al Azhary</span>
          </div>
        </a>
        <a class="social-item" href="https://leetcode.com/Mazen-Azhary" target="_blank">
          <span class="social-icon">◎</span>
          <div class="social-meta">
            <span class="social-platform">LeetCode</span>
            <span class="social-handle">Mazen-Azhary</span>
          </div>
        </a>
      </div>
    </div>

  </div>

</div>

<script>
  // ── LANGUAGE BARS ──
  const langs = [
    { name: 'C / C++',     pct: 35, color: '#58a6ff' },
    { name: 'Python',      pct: 25, color: '#d2a8ff' },
    { name: 'JavaScript',  pct: 20, color: '#f0db4f' },
    { name: 'TypeScript',  pct: 10, color: '#3178c6' },
    { name: 'Java',        pct: 6,  color: '#f78166' },
    { name: 'PHP',         pct: 4,  color: '#b0b3f0' },
  ];
  const langBars = document.getElementById('lang-bars');
  langs.forEach(l => {
    langBars.innerHTML += `
      <div class="stat-item">
        <div class="stat-label">
          <span class="stat-name">${l.name}</span>
          <span class="stat-pct">${l.pct}%</span>
        </div>
        <div class="bar-track">
          <div class="bar-fill" style="width:${l.pct}%;background:${l.color}"></div>
        </div>
      </div>`;
  });

  // ── HEATMAP ──
  const levels = [0,0,0,1,1,2,2,3,3,4,2,1,0,0,1,2,3,4,3,2,1,0,0,1,2,3];
  const weeks = 26;
  const days = 7;
  const heatmap = document.getElementById('heatmap');
  // Build columns (weeks) of 7 days
  for(let w=0;w<weeks;w++){
    for(let d=0;d<days;d++){
      const r = Math.random();
      let cls = 'heatmap-cell';
      if(r > 0.65) cls += ' h4';
      else if(r > 0.45) cls += ' h3';
      else if(r > 0.3) cls += ' h2';
      else if(r > 0.18) cls += ' h1';
      heatmap.innerHTML += `<div class="${cls}"></div>`;
    }
  }

  // ── SKILLS ──
  const skills = [
    {icon:'🔵', name:'C'},
    {icon:'🔷', name:'C++'},
    {icon:'🐍', name:'Python'},
    {icon:'☕', name:'Java'},
    {icon:'🟨', name:'JavaScript'},
    {icon:'🔷', name:'TypeScript'},
    {icon:'⚛️', name:'React'},
    {icon:'🟢', name:'Node.js'},
    {icon:'🐘', name:'PHP'},
    {icon:'🌐', name:'HTML5'},
    {icon:'🎨', name:'CSS3'},
    {icon:'💨', name:'Tailwind'},
    {icon:'🔺', name:'GraphQL'},
    {icon:'🗂️', name:'Git'},
    {icon:'🐧', name:'Linux'},
    {icon:'🐳', name:'Kubernetes'},
    {icon:'📨', name:'Kafka'},
    {icon:'🧪', name:'Selenium'},
    {icon:'🎮', name:'Unity'},
    {icon:'🖥️', name:'Qt'},
    {icon:'🔌', name:'Arduino'},
    {icon:'📬', name:'Postman'},
    {icon:'🐳', name:'Docker'},
  ];
  const grid = document.getElementById('skills-grid');
  skills.forEach(s => {
    grid.innerHTML += `<div class="skill-chip"><span class="icon">${s.icon}</span>${s.name}</div>`;
  });
</script>
</body>
</html>
