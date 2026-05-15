<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ashmit Singh — MERN Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0a0a;
    --surface: #111111;
    --border: #1f1f1f;
    --accent: #00ff87;
    --accent2: #60efff;
    --text: #e8e8e8;
    --muted: #555;
    --mono: 'Space Mono', monospace;
    --sans: 'Syne', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grain overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: 0.4;
  }

  .wrapper {
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    border: 1px solid var(--border);
    padding: 52px 48px 44px;
    margin-bottom: 2px;
    background: linear-gradient(135deg, #0e0e0e 0%, #111 100%);
    overflow: hidden;
    animation: fadeUp .7s ease both;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -80px; right: -80px;
    width: 320px; height: 320px;
    background: radial-gradient(circle, rgba(0,255,135,.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-tag {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .18em;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 18px;
  }

  .hero-tag::before { content: '> '; opacity: .5; }

  .hero h1 {
    font-family: var(--sans);
    font-size: clamp(2.4rem, 6vw, 3.8rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -.02em;
    margin-bottom: 6px;
  }

  .hero h1 span {
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--muted);
    margin-bottom: 28px;
  }

  .hero-sub em { color: var(--accent2); font-style: normal; }

  .hero-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .pill {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .06em;
    padding: 6px 14px;
    border: 1px solid var(--border);
    color: #888;
    transition: all .2s;
  }

  .pill:hover { border-color: var(--accent); color: var(--accent); }

  /* ── SECTION SHELL ── */
  .section {
    border: 1px solid var(--border);
    border-top: none;
    padding: 36px 48px;
    animation: fadeUp .7s ease both;
  }

  .section + .section { border-top: none; }

  .section-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .2em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── ABOUT ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }

  .about-card {
    border: 1px solid var(--border);
    padding: 20px 22px;
    background: #0d0d0d;
    transition: border-color .2s;
  }

  .about-card:hover { border-color: #2a2a2a; }

  .about-card-icon {
    font-size: 22px;
    margin-bottom: 10px;
  }

  .about-card-title {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: .15em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 6px;
  }

  .about-card-val {
    font-size: 14px;
    font-weight: 600;
    line-height: 1.5;
    color: #ccc;
  }

  .about-card-val small { display: block; font-size: 12px; color: #555; font-weight: 400; margin-top: 2px; }

  /* ── SKILLS GRID ── */
  .skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .04em;
    padding: 8px 14px;
    border: 1px solid var(--border);
    color: #999;
    background: #0d0d0d;
    transition: all .2s;
    cursor: default;
  }

  .skill-badge:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(0,255,135,.04);
    transform: translateY(-2px);
  }

  .skill-badge img {
    width: 14px;
    height: 14px;
    filter: grayscale(1) brightness(1.5);
    transition: filter .2s;
  }

  .skill-badge:hover img { filter: none; }

  /* ── STATS ── */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .stat-img-wrap {
    border: 1px solid var(--border);
    background: #0d0d0d;
    padding: 16px;
    text-align: center;
    transition: border-color .25s;
  }

  .stat-img-wrap:hover { border-color: #2e2e2e; }
  .stat-img-wrap img { width: 100%; max-width: 400px; display: block; margin: 0 auto; min-height: 120px; }
  .stat-img-wrap img.errored {
    display: none;
  }
  .stat-placeholder {
    display: none;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    text-align: center;
    padding: 32px 16px;
    letter-spacing: .08em;
  }
  .stat-placeholder span { color: var(--accent); }

  /* ── CONNECT ── */
  .connect-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .connect-link {
    display: inline-flex;
    align-items: center;
    gap: 9px;
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .06em;
    padding: 10px 18px;
    border: 1px solid var(--border);
    color: #888;
    text-decoration: none;
    background: #0d0d0d;
    transition: all .2s;
  }

  .connect-link:hover {
    color: var(--accent2);
    border-color: var(--accent2);
    background: rgba(96,239,255,.04);
    transform: translateY(-2px);
  }

  .connect-link img {
    width: 14px; height: 14px;
    filter: grayscale(1) brightness(2);
    transition: filter .2s;
  }

  .connect-link:hover img { filter: none brightness(1); }

  /* ── FOOTER BAR ── */
  .footer-bar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 12px;
    border: 1px solid var(--border);
    border-top: none;
    padding: 20px 48px;
    background: #0d0d0d;
    animation: fadeUp .7s ease both;
  }

  .footer-left {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
  }

  .resume-btn {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .1em;
    text-transform: uppercase;
    padding: 10px 22px;
    border: 1px solid var(--accent);
    color: var(--accent);
    text-decoration: none;
    background: transparent;
    transition: all .2s;
  }

  .resume-btn:hover {
    background: var(--accent);
    color: #000;
  }

  /* ── CURSOR LINE ── */
  .cursor-blink {
    display: inline-block;
    width: 2px; height: 1em;
    background: var(--accent);
    margin-left: 4px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0; }
  }

  /* stagger children */
  .section:nth-child(2) { animation-delay: .08s; }
  .section:nth-child(3) { animation-delay: .16s; }
  .section:nth-child(4) { animation-delay: .24s; }
  .section:nth-child(5) { animation-delay: .32s; }
  .footer-bar { animation-delay: .4s; }

  @media (max-width: 600px) {
    .hero { padding: 32px 24px; }
    .section { padding: 28px 24px; }
    .about-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: 1fr; }
    .footer-bar { padding: 20px 24px; }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-tag">mern full stack developer</div>
    <h1>Ashmit<br/><span>Singh</span><span class="cursor-blink"></span></h1>
    <p class="hero-sub">B.Tech IT '25 &nbsp;·&nbsp; Intern @ <em>Mojija E-Commerce Pvt. Ltd.</em></p>
    <div class="hero-pills">
      <span class="pill">Scalable Apps</span>
      <span class="pill">Role-Based Auth</span>
      <span class="pill">Real-Time APIs</span>
      <span class="pill">REST Architecture</span>
    </div>
  </div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-label">About</div>
    <div class="about-grid">
      <div class="about-card">
        <div class="about-card-icon">🎓</div>
        <div class="about-card-title">Education</div>
        <div class="about-card-val">B.Tech Information Technology<small>Batch of 2025</small></div>
      </div>
      <div class="about-card">
        <div class="about-card-icon">💼</div>
        <div class="about-card-title">Current Role</div>
        <div class="about-card-val">MERN Stack Intern<small>Mojija E-Commerce Pvt. Ltd.</small></div>
      </div>
      <div class="about-card">
        <div class="about-card-icon">🚀</div>
        <div class="about-card-title">Projects</div>
        <div class="about-card-val">Book Store Web App<small>+ Enterprise RBAC App · Weather App</small></div>
      </div>
      <div class="about-card">
        <div class="about-card-icon">🧩</div>
        <div class="about-card-title">Past Experience</div>
        <div class="about-card-val">Codsoft · Oxo Journey Pvt. Ltd.<small>Web Dev Intern · WordPress Dev</small></div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="section-label">Tech Stack</div>
    <div class="skills-grid">
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/html5/E34F26" alt=""/>HTML</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/css3/1572B6" alt=""/>CSS</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/javascript/F7DF1E" alt=""/>JavaScript</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/react/61DAFB" alt=""/>React</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/bootstrap/7952B3" alt=""/>Bootstrap</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/tailwindcss/06B6D4" alt=""/>Tailwind CSS</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/daisyui/5A0EF8" alt=""/>DaisyUI</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/threedotjs/ffffff" alt=""/>Three.js</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/nodedotjs/339933" alt=""/>Node.js</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/nodemon/76D04B" alt=""/>Nodemon</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/mysql/4479A1" alt=""/>MySQL</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/mongodb/47A248" alt=""/>MongoDB</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/git/F05032" alt=""/>Git</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/github/ffffff" alt=""/>GitHub</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/postman/FF6C37" alt=""/>Postman</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/wordpress/21759B" alt=""/>WordPress</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/figma/F24E1E" alt=""/>Figma</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/canva/00C4CC" alt=""/>Canva</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/render/46E3B7" alt=""/>Render</span>
      <span class="skill-badge"><img src="https://cdn.simpleicons.org/vercel/ffffff" alt=""/>Vercel</span>
    </div>
  </div>

  <!-- GITHUB STATS -->
  <div class="section">
    <div class="section-label">GitHub Stats</div>
    <div class="stats-row">
      <div class="stat-img-wrap" id="stats-wrap">
        <img src="https://github-readme-stats.vercel.app/api?username=Ashmit8736&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d0d0d&title_color=00ff87&icon_color=60efff&text_color=aaaaaa" alt="GitHub Stats"
          onerror="this.classList.add('errored'); this.nextElementSibling.style.display='block'"/>
        <div class="stat-placeholder">📊 GitHub Stats · <span>Ashmit8736</span><br/>Loads in browser</div>
      </div>
      <div class="stat-img-wrap" id="streak-wrap">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ashmit8736&theme=github-dark&hide_border=true&background=0d0d0d&ring=00ff87&fire=60efff&currStreakLabel=00ff87" alt="Streak Stats"
          onerror="this.classList.add('errored'); this.nextElementSibling.style.display='block'"/>
        <div class="stat-placeholder">🔥 Streak Stats · <span>Ashmit8736</span><br/>Loads in browser</div>
      </div>
    </div>
  </div>

  <!-- ACTIVITY GRAPH -->
  <div class="section">
    <div class="section-label">Contribution Activity</div>
    <div class="stat-img-wrap">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=Ashmit8736&theme=github-dark&hide_border=true&bg_color=0d0d0d&color=00ff87&line=60efff&point=ffffff" alt="Activity Graph"
        style="max-width:100%; min-height:120px"
        onerror="this.classList.add('errored'); this.nextElementSibling.style.display='block'"/>
      <div class="stat-placeholder">📈 Contribution Graph · <span>Ashmit8736</span><br/>Loads in browser</div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-label">Connect</div>
    <div class="connect-grid">
      <a class="connect-link" href="https://www.linkedin.com/in/ashmit8736" target="_blank">
        <img src="https://cdn.simpleicons.org/linkedin/0A66C2" alt=""/>LinkedIn
      </a>
      <a class="connect-link" href="mailto:ashmit8736@gmail.com">
        <img src="https://cdn.simpleicons.org/gmail/EA4335" alt=""/>Email
      </a>
      <a class="connect-link" href="https://x.com/Ashmitsingh8736" target="_blank">
        <img src="https://cdn.simpleicons.org/x/ffffff" alt=""/>X / Twitter
      </a>
      <a class="connect-link" href="https://www.instagram.com/mr_singh_____ji" target="_blank">
        <img src="https://cdn.simpleicons.org/instagram/E4405F" alt=""/>Instagram
      </a>
      <a class="connect-link" href="https://www.facebook.com/rajputashmit8736" target="_blank">
        <img src="https://cdn.simpleicons.org/facebook/1877F2" alt=""/>Facebook
      </a>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer-bar">
    <span class="footer-left">
      <img src="https://komarev.com/ghpvc/?username=Ashmit8736&color=00ff87&style=flat-square&label=visitors" alt="Visitor Count" style="vertical-align:middle"/>
    </span>
    <a class="resume-btn" href="your-link-here" target="_blank">↓ Resume</a>
  </div>

</div>
</body>
</html>
