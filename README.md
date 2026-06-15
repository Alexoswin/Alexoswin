<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Oswin Alex — AI Systems Engineer</title>
<style>
  :root{
    --bg:#05050a;
    --bg2:#0b0b18;
    --accent:#8B5CF6;
    --accent2:#22D3EE;
    --accent3:#F472B6;
    --text:#E5E7EB;
    --muted:#9CA3AF;
    --card:rgba(255,255,255,0.04);
    --border:rgba(255,255,255,0.08);
  }

  *{ box-sizing:border-box; margin:0; padding:0; }

  html,body{
    background:var(--bg);
    color:var(--text);
    font-family:'Space Mono','Courier New',monospace;
    overflow-x:hidden;
    scroll-behavior:smooth;
  }

  /* === STAR FIELD BACKGROUND === */
  #stars-canvas{
    position:fixed;
    top:0; left:0;
    width:100%; height:100%;
    z-index:0;
    pointer-events:none;
  }

  .grid-overlay{
    position:fixed;
    top:0; left:0; width:100%; height:100%;
    background-image:
      linear-gradient(rgba(139,92,246,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(139,92,246,0.04) 1px, transparent 1px);
    background-size:48px 48px;
    z-index:0;
    pointer-events:none;
    mask-image: radial-gradient(circle at 50% 30%, rgba(0,0,0,0.9), transparent 70%);
  }

  .page{
    position:relative;
    z-index:1;
    max-width:1100px;
    margin:0 auto;
    padding:60px 24px 100px;
  }

  /* === HERO === */
  .hero{
    text-align:center;
    padding:60px 20px;
    perspective:1000px;
  }

  .hero-title{
    font-size:clamp(2.4rem, 7vw, 4.5rem);
    font-weight:800;
    letter-spacing:4px;
    background:linear-gradient(135deg,var(--accent2),var(--accent),var(--accent3));
    background-size:300% 300%;
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
    animation:gradientShift 6s ease infinite, floatUp 6s ease-in-out infinite;
    transform-style:preserve-3d;
    text-shadow:0 0 40px rgba(139,92,246,0.25);
  }

  @keyframes gradientShift{
    0%,100%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
  }

  @keyframes floatUp{
    0%,100%{transform:translateY(0) rotateX(0deg);}
    50%{transform:translateY(-10px) rotateX(4deg);}
  }

  .hero-subtitle{
    margin-top:18px;
    font-size:clamp(0.9rem, 2.5vw, 1.2rem);
    color:var(--accent2);
    letter-spacing:1px;
    min-height:30px;
  }

  .typed-cursor{
    display:inline-block;
    width:2px;
    background:var(--accent2);
    margin-left:4px;
    animation:blink 0.8s steps(1) infinite;
  }
  @keyframes blink{ 50%{opacity:0;} }

  .badges{
    margin-top:32px;
    display:flex;
    flex-wrap:wrap;
    gap:14px;
    justify-content:center;
  }

  .badge{
    display:inline-flex;
    align-items:center;
    gap:8px;
    padding:10px 22px;
    border-radius:999px;
    border:1px solid var(--border);
    background:var(--card);
    color:var(--text);
    text-decoration:none;
    font-size:0.85rem;
    font-weight:700;
    letter-spacing:0.5px;
    backdrop-filter:blur(8px);
    transform-style:preserve-3d;
    transition:transform 0.35s ease, box-shadow 0.35s ease, border-color 0.35s ease;
  }

  .badge:hover{
    transform:translateY(-6px) rotateX(8deg) scale(1.05);
    border-color:var(--accent);
    box-shadow:0 12px 30px -8px rgba(139,92,246,0.55);
  }

  /* === SECTION HEADERS === */
  .section{
    margin-top:90px;
  }

  .section-title{
    text-align:center;
    font-size:clamp(1.4rem, 4vw, 2.2rem);
    letter-spacing:6px;
    text-transform:uppercase;
    font-weight:800;
    color:var(--text);
    position:relative;
    margin-bottom:50px;
  }

  .section-title::before{
    content:'';
    position:absolute;
    left:50%;
    bottom:-16px;
    transform:translateX(-50%);
    width:80px;
    height:3px;
    background:linear-gradient(90deg,var(--accent2),var(--accent3));
    border-radius:3px;
    box-shadow:0 0 18px rgba(139,92,246,0.7);
  }

  .section-title .icon{
    display:inline-block;
    animation:spin3d 6s linear infinite;
    transform-style:preserve-3d;
  }

  @keyframes spin3d{
    0%{transform:rotateY(0deg);}
    100%{transform:rotateY(360deg);}
  }

  /* === STATUS / TERMINAL CARD === */
  .terminal{
    background:linear-gradient(145deg, rgba(139,92,246,0.08), rgba(34,211,238,0.05));
    border:1px solid var(--border);
    border-radius:16px;
    padding:30px clamp(16px,4vw,40px);
    max-width:640px;
    margin:0 auto;
    position:relative;
    transform-style:preserve-3d;
    transition:transform 0.5s ease, box-shadow 0.5s ease;
    box-shadow:0 20px 60px -25px rgba(139,92,246,0.4);
  }

  .terminal:hover{
    transform:rotateX(4deg) rotateY(-4deg) translateY(-6px);
    box-shadow:0 30px 80px -20px rgba(139,92,246,0.55);
  }

  .terminal-dots{
    display:flex;
    gap:8px;
    margin-bottom:18px;
  }
  .dot{ width:12px; height:12px; border-radius:50%; }
  .dot.red{background:#ef4444;}
  .dot.yellow{background:#f59e0b;}
  .dot.green{background:#22c55e;}

  .terminal pre{
    white-space:pre-wrap;
    font-size:0.85rem;
    line-height:1.7;
    color:var(--muted);
  }
  .terminal .hl{ color:var(--accent2); font-weight:700; }
  .terminal .ok{ color:#22c55e; }

  .bar{
    display:inline-block;
    height:10px;
    border-radius:5px;
    background:linear-gradient(90deg,var(--accent2),var(--accent));
    box-shadow:0 0 10px rgba(34,211,238,0.5);
    vertical-align:middle;
  }
  .bar-track{
    display:inline-block;
    width:160px;
    height:10px;
    background:rgba(255,255,255,0.06);
    border-radius:5px;
    overflow:hidden;
    vertical-align:middle;
    margin-left:8px;
  }

  /* === MISSION GRID (3D TILT CARDS) === */
  .mission-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(220px, 1fr));
    gap:22px;
  }

  .tilt-card{
    background:var(--card);
    border:1px solid var(--border);
    border-radius:16px;
    padding:28px 20px;
    text-align:center;
    backdrop-filter:blur(10px);
    transform-style:preserve-3d;
    transition:transform 0.15s ease, box-shadow 0.3s ease, border-color 0.3s ease;
    cursor:pointer;
    position:relative;
    overflow:hidden;
  }

  .tilt-card::before{
    content:'';
    position:absolute;
    top:-50%; left:-50%;
    width:200%; height:200%;
    background:radial-gradient(circle, rgba(139,92,246,0.18), transparent 60%);
    opacity:0;
    transition:opacity 0.4s ease;
    pointer-events:none;
  }

  .tilt-card:hover::before{ opacity:1; }

  .tilt-card:hover{
    border-color:var(--accent);
    box-shadow:0 25px 50px -20px rgba(139,92,246,0.5);
  }

  .tilt-card .emoji{
    font-size:2.4rem;
    display:inline-block;
    margin-bottom:14px;
    transform:translateZ(20px);
    filter:drop-shadow(0 8px 12px rgba(139,92,246,0.4));
  }

  .tilt-card h3{
    font-size:1rem;
    letter-spacing:1px;
    font-weight:700;
    transform:translateZ(15px);
  }

  /* === TECH ARSENAL === */
  .arsenal{
    display:flex;
    flex-direction:column;
    gap:34px;
  }

  .arsenal-row h4{
    text-align:center;
    color:var(--accent2);
    letter-spacing:3px;
    text-transform:uppercase;
    font-size:0.85rem;
    margin-bottom:18px;
  }

  .icon-track{
    display:flex;
    flex-wrap:wrap;
    justify-content:center;
    gap:16px;
  }

  .icon-chip{
    width:64px; height:64px;
    border-radius:16px;
    background:var(--card);
    border:1px solid var(--border);
    display:flex;
    align-items:center;
    justify-content:center;
    transform-style:preserve-3d;
    transition:transform 0.4s ease, box-shadow 0.4s ease, border-color 0.4s ease;
    animation:floatChip 5s ease-in-out infinite;
  }
  .icon-chip img{ width:34px; height:34px; }

  .icon-chip:hover{
    transform:translateY(-10px) rotateY(20deg) scale(1.15);
    border-color:var(--accent2);
    box-shadow:0 18px 35px -12px rgba(34,211,238,0.5);
  }

  @keyframes floatChip{
    0%,100%{ transform:translateY(0); }
    50%{ transform:translateY(-6px); }
  }
  .icon-chip:nth-child(2n){ animation-delay:0.6s; }
  .icon-chip:nth-child(3n){ animation-delay:1.2s; }

  /* === ACHIEVEMENTS === */
  .achievements{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(220px,1fr));
    gap:20px;
  }

  .ach-card{
    background:linear-gradient(160deg, rgba(34,211,238,0.07), rgba(139,92,246,0.05));
    border:1px solid var(--border);
    border-radius:14px;
    padding:22px;
    display:flex;
    align-items:center;
    gap:14px;
    transform-style:preserve-3d;
    transition:transform 0.35s ease, box-shadow 0.35s ease;
  }

  .ach-card:hover{
    transform:perspective(600px) rotateX(6deg) translateY(-5px);
    box-shadow:0 18px 40px -18px rgba(34,211,238,0.45);
  }

  .ach-card .trophy{ font-size:1.8rem; }
  .ach-card span{ font-weight:700; font-size:0.9rem; letter-spacing:0.5px; }

  .ach-card.full{ grid-column:1 / -1; justify-content:center; text-align:center; }

  /* === GITHUB STATS === */
  .stats-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(300px,1fr));
    gap:20px;
  }

  .stats-grid img{
    width:100%;
    border-radius:14px;
    border:1px solid var(--border);
    display:block;
    transition:transform 0.4s ease, box-shadow 0.4s ease;
  }

  .stats-grid img:hover{
    transform:scale(1.02) translateY(-4px);
    box-shadow:0 20px 50px -22px rgba(139,92,246,0.5);
  }

  .full-row img{
    width:100%;
    border-radius:14px;
    border:1px solid var(--border);
    margin-top:20px;
  }

  /* === OPEN SOURCE CARD === */
  .oss-card{
    max-width:700px;
    margin:0 auto;
    background:var(--card);
    border:1px solid var(--border);
    border-radius:18px;
    padding:36px;
    text-align:center;
    position:relative;
    overflow:hidden;
    transform-style:preserve-3d;
    transition:transform 0.4s ease, box-shadow 0.4s ease;
  }

  .oss-card:hover{
    transform:rotateX(3deg) rotateY(-3deg);
    box-shadow:0 25px 60px -22px rgba(244,114,182,0.4);
  }

  .oss-card::after{
    content:'';
    position:absolute;
    inset:0;
    background:linear-gradient(135deg, transparent, rgba(244,114,182,0.08), transparent);
    transform:translateX(-100%);
    animation:shine 5s ease-in-out infinite;
  }

  @keyframes shine{
    0%,100%{ transform:translateX(-100%); }
    50%{ transform:translateX(100%); }
  }

  .oss-card h3{
    color:var(--accent3);
    letter-spacing:2px;
    margin-bottom:6px;
    font-size:1.1rem;
  }

  .oss-card .pr-tag{
    display:inline-block;
    margin:14px 0;
    padding:6px 16px;
    border-radius:999px;
    border:1px solid var(--accent3);
    color:var(--accent3);
    font-weight:700;
    font-size:0.8rem;
  }

  .oss-card p{
    color:var(--muted);
    font-size:0.9rem;
    line-height:1.6;
    margin-bottom:18px;
  }

  .pill-row{
    display:flex;
    flex-wrap:wrap;
    gap:10px;
    justify-content:center;
  }

  .pill{
    padding:8px 16px;
    border-radius:999px;
    font-size:0.75rem;
    font-weight:700;
    letter-spacing:0.5px;
    border:1px solid var(--border);
  }
  .pill.green{ color:#22c55e; border-color:#22c55e44; }
  .pill.blue{ color:var(--accent2); border-color:#22D3EE44; }
  .pill.purple{ color:var(--accent); border-color:#8B5CF644; }

  /* === FOOTER / CONNECT === */
  .connect{
    text-align:center;
  }

  .connect-row{
    display:flex;
    flex-wrap:wrap;
    justify-content:center;
    gap:14px;
    margin-bottom:40px;
  }

  .connect-row img{
    border-radius:10px;
    transition:transform 0.3s ease;
  }
  .connect-row img:hover{ transform:translateY(-4px) scale(1.05); }

  footer-wave{ display:block; }

  .footer-wave{
    width:100%;
    margin-top:60px;
    border-radius:14px;
  }

  /* === SCROLL REVEAL === */
  .reveal{
    opacity:0;
    transform:translateY(40px);
    transition:opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible{
    opacity:1;
    transform:translateY(0);
  }

  @media (max-width:600px){
    .hero{ padding:40px 10px; }
    .section{ margin-top:60px; }
  }
</style>
</head>
<body>

<canvas id="stars-canvas"></canvas>
<div class="grid-overlay"></div>

<div class="page">

  <!-- HERO -->
  <section class="hero">
    <h1 class="hero-title">OSWIN ALEX</h1>
    <div class="hero-subtitle" id="typed-text">&nbsp;</div>
    <div class="badges">
      <a class="badge" href="https://oswinalex.site" target="_blank">🌐 Portfolio</a>
      <a class="badge" href="https://linkedin.com/in/oswin-alex" target="_blank">💼 LinkedIn</a>
      <a class="badge" href="mailto:oswinalex1@gmail.com">✉️ Gmail</a>
      <a class="badge" href="https://github.com/Alexoswin" target="_blank">🐙 GitHub</a>
    </div>
  </section>

  <!-- STATUS TERMINAL -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">🧠</span> AI Command Center</h2>
    <div class="terminal">
      <div class="terminal-dots">
        <div class="dot red"></div><div class="dot yellow"></div><div class="dot green"></div>
      </div>
      <pre><span class="ok">STATUS: ONLINE</span>

Name      : <span class="hl">Oswin Alex</span>
Role      : Software Engineer @ mple.ai
Location  : Mumbai, India

Specialization
──────────────────────
► Agentic AI
► NestJS Architecture
► WebSocket Systems
► Analytics Pipelines
► AI Avatars

System Health
──────────────────────
AI Systems   <span class="bar-track"><span class="bar" style="width:100%"></span></span> 100%
Backend      <span class="bar-track"><span class="bar" style="width:95%"></span></span>  95%
DevOps       <span class="bar-track"><span class="bar" style="width:90%"></span></span>  90%
Frontend     <span class="bar-track"><span class="bar" style="width:80%"></span></span>  80%
Sleep        <span class="bar-track"><span class="bar" style="width:10%"></span></span>  10%</pre>
    </div>
  </section>

  <!-- CURRENT MISSION -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">🚀</span> Current Mission</h2>
    <div class="mission-grid">
      <div class="tilt-card"><div class="emoji">🧠</div><h3>Agentic AI Systems</h3></div>
      <div class="tilt-card"><div class="emoji">⚡</div><h3>AI Roleplay Engines</h3></div>
      <div class="tilt-card"><div class="emoji">🎭</div><h3>AI Avatar Experiences</h3></div>
      <div class="tilt-card"><div class="emoji">🌐</div><h3>Real-Time WebSocket Platforms</h3></div>
      <div class="tilt-card"><div class="emoji">📊</div><h3>Learning Analytics Pipelines</h3></div>
      <div class="tilt-card"><div class="emoji">☁️</div><h3>Scalable Cloud Architectures</h3></div>
    </div>
  </section>

  <!-- TECH ARSENAL -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">⚔️</span> Tech Arsenal</h2>
    <div class="arsenal">
      <div class="arsenal-row">
        <h4>Languages</h4>
        <div class="icon-track">
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=typescript" alt="TypeScript"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=javascript" alt="JavaScript"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=python" alt="Python"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=java" alt="Java"/></div>
        </div>
      </div>
      <div class="arsenal-row">
        <h4>Backend</h4>
        <div class="icon-track">
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=nestjs" alt="NestJS"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=nodejs" alt="Node.js"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=express" alt="Express"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=mongodb" alt="MongoDB"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=mysql" alt="MySQL"/></div>
        </div>
      </div>
      <div class="arsenal-row">
        <h4>Frontend</h4>
        <div class="icon-track">
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=nextjs" alt="Next.js"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=react" alt="React"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=tailwind" alt="Tailwind"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=flutter" alt="Flutter"/></div>
        </div>
      </div>
      <div class="arsenal-row">
        <h4>Cloud &amp; DevOps</h4>
        <div class="icon-track">
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=aws" alt="AWS"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=docker" alt="Docker"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=jenkins" alt="Jenkins"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=githubactions" alt="GitHub Actions"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=git" alt="Git"/></div>
          <div class="icon-chip"><img src="https://skillicons.dev/icons?i=linux" alt="Linux"/></div>
        </div>
      </div>
    </div>
  </section>

  <!-- ACHIEVEMENTS -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">🏆</span> Achievements</h2>
    <div class="achievements">
      <div class="ach-card"><div class="trophy">🥇</div><span>Smart India Hackathon Winner</span></div>
      <div class="ach-card"><div class="trophy">🏆</div><span>Innovex 2025 Champion</span></div>
      <div class="ach-card"><div class="trophy">☁️</div><span>AWS Certified</span></div>
      <div class="ach-card"><div class="trophy">🔧</div><span>Frappe OSS Contributor</span></div>
      <div class="ach-card full"><div class="trophy">🚀</div><span>Software Engineer @ mple.ai</span></div>
    </div>
  </section>

  <!-- GITHUB DASHBOARD -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">📊</span> GitHub Dashboard</h2>
    <div class="stats-grid">
      <img src="https://github-readme-stats.vercel.app/api?username=Alexoswin&show_icons=true&theme=midnight-purple&hide_border=true&count_private=true" alt="GitHub Stats"/>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Alexoswin&layout=compact&theme=midnight-purple&hide_border=true" alt="Top Languages"/>
    </div>
    <div class="full-row">
      <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=Alexoswin&theme=tokyonight" alt="Profile Summary"/>
    </div>
  </section>

  <!-- CONTRIBUTION ACTIVITY -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">🔥</span> Contribution Activity</h2>
    <img class="full-row" src="https://github-readme-activity-graph.vercel.app/graph?username=Alexoswin&theme=tokyo-night&hide_border=true&area=true" alt="Activity Graph" style="margin-top:0;"/>
  </section>

  <!-- SNAKE -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">🐍</span> Contribution Snake</h2>
    <img class="full-row" src="https://raw.githubusercontent.com/Alexoswin/Alexoswin/output/github-contribution-grid-snake-dark.svg" alt="Snake" style="margin-top:0;"/>
  </section>

  <!-- OPEN SOURCE -->
  <section class="section reveal">
    <h2 class="section-title"><span class="icon">🔓</span> Open Source Impact</h2>
    <div class="oss-card">
      <h3>FRAPPE FRAMEWORK CONTRIBUTOR</h3>
      <div class="pr-tag">PR #36145</div>
      <p>Fixed a production OAuth2 refresh token validation issue causing 403 Forbidden responses under guest context.</p>
      <div class="pill-row">
        <span class="pill green">RFC6749 Compliant</span>
        <span class="pill blue">Test Coverage Added</span>
        <span class="pill purple">Open Source Contributor</span>
      </div>
    </div>
  </section>

  <!-- CONNECT -->
  <section class="section reveal connect">
    <h2 class="section-title"><span class="icon">📡</span> Connect</h2>
    <div class="connect-row">
      <img src="https://komarev.com/ghpvc/?username=Alexoswin&style=for-the-badge&color=8B5CF6" alt="Profile Views"/>
      <img src="https://img.shields.io/github/followers/Alexoswin?style=for-the-badge&color=8B5CF6" alt="Followers"/>
      <img src="https://img.shields.io/github/stars/Alexoswin?style=for-the-badge&color=8B5CF6" alt="Stars"/>
    </div>
    <img class="footer-wave" src="https://capsule-render.vercel.app/api?type=waving&height=120&section=footer&color=gradient&customColorList=12,20,24" alt="footer"/>
  </section>

</div>

<script>
  /* ===== STARFIELD WITH PARALLAX 3D MOTION ===== */
  const canvas = document.getElementById('stars-canvas');
  const ctx = canvas.getContext('2d');
  let stars = [];

  function resize(){
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    initStars();
  }

  function initStars(){
    stars = [];
    const count = Math.floor((canvas.width * canvas.height) / 6000);
    for(let i=0;i<count;i++){
      stars.push({
        x: Math.random()*canvas.width,
        y: Math.random()*canvas.height,
        z: Math.random()*1 + 0.2,
        r: Math.random()*1.4 + 0.3,
        tw: Math.random()*Math.PI*2
      });
    }
  }

  let mouseX = 0, mouseY = 0;
  window.addEventListener('mousemove', (e)=>{
    mouseX = (e.clientX / window.innerWidth - 0.5);
    mouseY = (e.clientY / window.innerHeight - 0.5);
  });

  function draw(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    const t = Date.now()*0.001;
    for(const s of stars){
      const parallaxX = mouseX * 30 * s.z;
      const parallaxY = mouseY * 30 * s.z;
      const twinkle = 0.5 + 0.5*Math.sin(t*1.5 + s.tw);
      ctx.beginPath();
      ctx.arc(s.x + parallaxX, s.y + parallaxY, s.r * s.z, 0, Math.PI*2);
      ctx.fillStyle = `rgba(180,160,255,${0.25 + twinkle*0.55})`;
      ctx.fill();
    }
    requestAnimationFrame(draw);
  }

  window.addEventListener('resize', resize);
  resize();
  draw();

  /* ===== TYPING EFFECT ===== */
  const phrases = [
    "Building Agentic AI Platforms",
    "Real-Time WebSocket Architectures",
    "NestJS Backend Engineering",
    "AI Roleplay and Avatar Systems",
    "Open Source Contributor"
  ];
  const typedEl = document.getElementById('typed-text');
  let phraseIndex = 0, charIndex = 0, deleting = false;

  function typeLoop(){
    const current = phrases[phraseIndex];
    if(!deleting){
      charIndex++;
      typedEl.innerHTML = current.substring(0, charIndex) + '<span class="typed-cursor">&nbsp;</span>';
      if(charIndex === current.length){
        deleting = true;
        setTimeout(typeLoop, 1400);
        return;
      }
    } else {
      charIndex--;
      typedEl.innerHTML = current.substring(0, charIndex) + '<span class="typed-cursor">&nbsp;</span>';
      if(charIndex === 0){
        deleting = false;
        phraseIndex = (phraseIndex + 1) % phrases.length;
      }
    }
    setTimeout(typeLoop, deleting ? 35 : 55);
  }
  typeLoop();

  /* ===== 3D TILT ON CARDS (mouse-follow) ===== */
  document.querySelectorAll('.tilt-card').forEach(card=>{
    card.addEventListener('mousemove', (e)=>{
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      const rotateX = ((y / rect.height) - 0.5) * -18;
      const rotateY = ((x / rect.width) - 0.5) * 18;
      card.style.transform = `perspective(700px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateY(-6px) scale(1.03)`;
    });
    card.addEventListener('mouseleave', ()=>{
      card.style.transform = 'perspective(700px) rotateX(0) rotateY(0) translateY(0) scale(1)';
    });
  });

  /* ===== SCROLL REVEAL ===== */
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
      if(entry.isIntersecting){
        entry.target.classList.add('visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });
  reveals.forEach(el=>observer.observe(el));
</script>

</body>
</html>
