<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Eddie Turya — Full-Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #060810;
    --surface: #0d1120;
    --surface2: #131929;
    --accent: #00e5ff;
    --accent2: #7b61ff;
    --accent3: #ff6b35;
    --text: #e8eaf0;
    --muted: #6b7280;
    --glow: 0 0 40px rgba(0,229,255,0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom Cursor */
  .cursor {
    position: fixed;
    width: 12px; height: 12px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s ease;
    mix-blend-mode: difference;
  }
  .cursor-trail {
    position: fixed;
    width: 36px; height: 36px;
    border: 1px solid rgba(0,229,255,0.4);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.15s ease;
  }

  /* Background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.025) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.025) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* Floating orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(100px);
    pointer-events: none;
    z-index: 0;
    animation: float 12s ease-in-out infinite;
  }
  .orb1 { width: 500px; height: 500px; background: rgba(0,229,255,0.06); top: -150px; right: -100px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: rgba(123,97,255,0.07); bottom: 20%; left: -100px; animation-delay: -4s; }
  .orb3 { width: 300px; height: 300px; background: rgba(255,107,53,0.05); bottom: -100px; right: 20%; animation-delay: -8s; }

  @keyframes float {
    0%, 100% { transform: translateY(0px) scale(1); }
    50% { transform: translateY(-30px) scale(1.05); }
  }

  /* Layout */
  main { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 24px 80px; }

  /* ─── HERO ─── */
  .hero {
    padding: 100px 0 60px;
    position: relative;
  }

  .hero-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.2s;
  }

  .hero-name {
    font-size: clamp(52px, 10vw, 88px);
    font-weight: 800;
    line-height: 0.95;
    margin: 16px 0;
    background: linear-gradient(135deg, #ffffff 0%, var(--accent) 50%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.4s;
  }

  .hero-role {
    font-family: 'JetBrains Mono', monospace;
    font-size: 16px;
    color: var(--muted);
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.6s;
  }
  .hero-role span { color: var(--accent2); }

  .hero-desc {
    font-size: 18px;
    line-height: 1.7;
    color: #9ba3af;
    max-width: 560px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.8s;
  }

  .hero-badges {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 36px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 1s;
  }
  .badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 6px 14px;
    border-radius: 4px;
    border: 1px solid rgba(0,229,255,0.2);
    background: rgba(0,229,255,0.05);
    color: var(--accent);
    letter-spacing: 1px;
    transition: all 0.2s ease;
  }
  .badge:hover { background: rgba(0,229,255,0.12); border-color: var(--accent); transform: translateY(-2px); }
  .badge.v { color: var(--accent2); border-color: rgba(123,97,255,0.3); background: rgba(123,97,255,0.06); }
  .badge.v:hover { background: rgba(123,97,255,0.14); border-color: var(--accent2); }
  .badge.o { color: var(--accent3); border-color: rgba(255,107,53,0.3); background: rgba(255,107,53,0.06); }

  /* Typing animation */
  .type-wrap {
    font-family: 'JetBrains Mono', monospace;
    font-size: 14px;
    color: var(--accent);
    margin-top: 24px;
    height: 22px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 1.1s;
  }
  .type-cursor { animation: blink 1s step-end infinite; }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  /* ─── SECTION ─── */
  section { margin-top: 80px; opacity: 0; animation: fadeUp 0.7s ease forwards; }
  section:nth-child(2) { animation-delay: 0.1s; }
  section:nth-child(3) { animation-delay: 0.2s; }
  section:nth-child(4) { animation-delay: 0.3s; }
  section:nth-child(5) { animation-delay: 0.4s; }
  section:nth-child(6) { animation-delay: 0.5s; }

  .section-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .section-title {
    font-size: 32px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 32px;
    position: relative;
    display: inline-block;
  }
  .section-title::after {
    content: '';
    position: absolute;
    bottom: -8px; left: 0;
    width: 40px; height: 2px;
    background: linear-gradient(90deg, var(--accent), transparent);
  }

  /* ─── INFO CARD ─── */
  .info-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
  }
  .info-card {
    background: var(--surface);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 12px;
    padding: 20px;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }
  .info-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .info-card:hover { transform: translateY(-4px); border-color: rgba(0,229,255,0.2); box-shadow: var(--glow); }
  .info-card:hover::before { opacity: 1; }
  .info-icon { font-size: 24px; margin-bottom: 10px; }
  .info-label { font-family: 'JetBrains Mono', monospace; font-size: 10px; color: var(--muted); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 6px; }
  .info-value { font-size: 15px; font-weight: 600; color: var(--text); }

  /* ─── SKILLS ─── */
  .skill-category { margin-bottom: 32px; }
  .skill-cat-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent2);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 14px;
  }
  .skill-pills { display: flex; flex-wrap: wrap; gap: 10px; }
  .skill-pill {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    padding: 8px 16px;
    border-radius: 6px;
    background: var(--surface2);
    border: 1px solid rgba(255,255,255,0.07);
    color: #c8cdd6;
    transition: all 0.2s ease;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .skill-pill:hover { background: rgba(0,229,255,0.08); border-color: rgba(0,229,255,0.3); color: var(--accent); transform: scale(1.04); }
  .skill-pill .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent); opacity: 0.6; }

  /* ─── PROJECTS ─── */
  .project-grid { display: grid; gap: 20px; }
  .project-card {
    background: var(--surface);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 14px;
    padding: 28px;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }
  .project-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(0,229,255,0.03) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .project-card:hover { transform: translateY(-6px); border-color: rgba(0,229,255,0.25); box-shadow: 0 20px 60px rgba(0,0,0,0.4), var(--glow); }
  .project-card:hover::after { opacity: 1; }

  .project-header { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 14px; gap: 16px; }
  .project-emoji { font-size: 28px; }
  .project-links { display: flex; gap: 10px; }
  .project-link {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 5px 12px;
    border-radius: 4px;
    border: 1px solid rgba(0,229,255,0.25);
    color: var(--accent);
    text-decoration: none;
    transition: all 0.2s;
  }
  .project-link:hover { background: rgba(0,229,255,0.1); }
  .project-title { font-size: 20px; font-weight: 700; color: #fff; margin-bottom: 10px; }
  .project-desc { font-size: 14px; line-height: 1.65; color: #8a93a2; margin-bottom: 18px; }
  .project-stack { display: flex; flex-wrap: wrap; gap: 8px; }
  .stack-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 4px 10px;
    border-radius: 4px;
    background: rgba(123,97,255,0.1);
    border: 1px solid rgba(123,97,255,0.2);
    color: #a78bfa;
  }

  /* ─── STATS ─── */
  .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 16px; }
  .stat-card {
    background: var(--surface);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 12px;
    padding: 24px 20px;
    text-align: center;
    transition: all 0.3s ease;
  }
  .stat-card:hover { transform: translateY(-4px); border-color: rgba(0,229,255,0.2); }
  .stat-number { font-size: 36px; font-weight: 800; background: linear-gradient(135deg, var(--accent), var(--accent2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .stat-label { font-family: 'JetBrains Mono', monospace; font-size: 11px; color: var(--muted); letter-spacing: 1px; margin-top: 6px; }

  /* ─── GITHUB EMBED ─── */
  .github-cards { display: flex; flex-wrap: wrap; gap: 16px; justify-content: center; }
  .github-cards img { border-radius: 10px; max-width: 100%; height: auto; }

  /* ─── CONTACT ─── */
  .contact-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 14px; }
  .contact-card {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 18px 20px;
    background: var(--surface);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 12px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.3s ease;
    cursor: none;
  }
  .contact-card:hover { transform: translateY(-4px); border-color: rgba(0,229,255,0.3); box-shadow: var(--glow); background: rgba(0,229,255,0.04); }
  .contact-icon { font-size: 22px; }
  .contact-info-label { font-family: 'JetBrains Mono', monospace; font-size: 10px; color: var(--muted); letter-spacing: 1px; }
  .contact-info-value { font-size: 14px; font-weight: 600; margin-top: 2px; }

  /* ─── DIVIDER ─── */
  .divider {
    border: none;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.08), transparent);
    margin: 0;
  }

  /* ─── FOOTER ─── */
  footer {
    text-align: center;
    padding: 40px 0;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    position: relative;
    z-index: 1;
  }
  footer span { color: var(--accent); }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: rgba(0,229,255,0.3); border-radius: 2px; }

  /* Nav dot indicator */
  .nav-dots {
    position: fixed;
    right: 24px;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    flex-direction: column;
    gap: 10px;
    z-index: 100;
  }
  .nav-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: rgba(255,255,255,0.2);
    transition: all 0.3s ease;
    cursor: none;
  }
  .nav-dot.active { background: var(--accent); box-shadow: 0 0 10px var(--accent); transform: scale(1.5); }

  @media (max-width: 600px) {
    .nav-dots { display: none; }
    .hero-name { font-size: 48px; }
  }
</style>
</head>
<body>

<!-- Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="cursorTrail"></div>

<!-- Background orbs -->
<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<!-- Side nav dots -->
<div class="nav-dots">
  <div class="nav-dot active"></div>
  <div class="nav-dot"></div>
  <div class="nav-dot"></div>
  <div class="nav-dot"></div>
  <div class="nav-dot"></div>
</div>

<main>

  <!-- ── HERO ── -->
  <div class="hero">
    <div class="hero-tag">// Available for work · Tanzania 🇹🇿</div>
    <h1 class="hero-name">Eddie<br>Turya</h1>
    <div class="hero-role">
      <span>Full-Stack Developer</span> · App Innovator · Digital Architect
    </div>
    <p class="hero-desc">
      Crafting premium, scalable software solutions that live at the intersection of elegant code and meaningful user experience. From fintech platforms to cross-platform mobile apps — I build things that matter.
    </p>
    <div class="type-wrap">
      &gt; <span id="typeText"></span><span class="type-cursor">_</span>
    </div>
    <div class="hero-badges">
      <span class="badge">Python</span>
      <span class="badge">JavaScript</span>
      <span class="badge">Flutter</span>
      <span class="badge v">React</span>
      <span class="badge v">Node.js</span>
      <span class="badge v">Kotlin</span>
      <span class="badge o">Open to Collaborate</span>
    </div>
  </div>

  <hr class="divider" />

  <!-- ── ABOUT ── -->
  <section>
    <div class="section-label">01 / Profile</div>
    <h2 class="section-title">About Me</h2>
    <div class="info-grid">
      <div class="info-card">
        <div class="info-icon">🌍</div>
        <div class="info-label">Location</div>
        <div class="info-value">Dar es Salaam, Tanzania</div>
      </div>
      <div class="info-card">
        <div class="info-icon">🎯</div>
        <div class="info-label">Focus</div>
        <div class="info-value">Web · Mobile · Fintech</div>
      </div>
      <div class="info-card">
        <div class="info-icon">🌱</div>
        <div class="info-label">Currently Learning</div>
        <div class="info-value">Advanced Flutter & React Native</div>
      </div>
      <div class="info-card">
        <div class="info-icon">⚡</div>
        <div class="info-label">Passion Projects</div>
        <div class="info-value">Blockchain · Open Source</div>
      </div>
      <div class="info-card">
        <div class="info-icon">💼</div>
        <div class="info-label">Status</div>
        <div class="info-value" style="color:#4ade80">● Available for Hire</div>
      </div>
      <div class="info-card">
        <div class="info-icon">🏆</div>
        <div class="info-label">Experience</div>
        <div class="info-value">Full-Stack · Enterprise Grade</div>
      </div>
    </div>
  </section>

  <hr class="divider" />

  <!-- ── TECH ── -->
  <section>
    <div class="section-label">02 / Skills</div>
    <h2 class="section-title">Tech Arsenal</h2>

    <div class="skill-category">
      <div class="skill-cat-title">// Languages</div>
      <div class="skill-pills">
        <div class="skill-pill"><span class="dot"></span>Python</div>
        <div class="skill-pill"><span class="dot"></span>JavaScript</div>
        <div class="skill-pill"><span class="dot"></span>TypeScript</div>
        <div class="skill-pill"><span class="dot"></span>Java</div>
        <div class="skill-pill"><span class="dot"></span>Kotlin</div>
        <div class="skill-pill"><span class="dot"></span>PHP</div>
        <div class="skill-pill"><span class="dot"></span>Dart</div>
      </div>
    </div>

    <div class="skill-category">
      <div class="skill-cat-title">// Frameworks & Tools</div>
      <div class="skill-pills">
        <div class="skill-pill"><span class="dot"></span>React.js</div>
        <div class="skill-pill"><span class="dot"></span>Node.js</div>
        <div class="skill-pill"><span class="dot"></span>Flutter</div>
        <div class="skill-pill"><span class="dot"></span>Next.js</div>
        <div class="skill-pill"><span class="dot"></span>Django</div>
        <div class="skill-pill"><span class="dot"></span>Express.js</div>
        <div class="skill-pill"><span class="dot"></span>React Native</div>
      </div>
    </div>

    <div class="skill-category">
      <div class="skill-cat-title">// Databases & DevOps</div>
      <div class="skill-pills">
        <div class="skill-pill"><span class="dot"></span>MySQL</div>
        <div class="skill-pill"><span class="dot"></span>PostgreSQL</div>
        <div class="skill-pill"><span class="dot"></span>MongoDB</div>
        <div class="skill-pill"><span class="dot"></span>Firebase</div>
        <div class="skill-pill"><span class="dot"></span>Docker</div>
        <div class="skill-pill"><span class="dot"></span>Git</div>
        <div class="skill-pill"><span class="dot"></span>Linux</div>
      </div>
    </div>
  </section>

  <hr class="divider" />

  <!-- ── PROJECTS ── -->
  <section>
    <div class="section-label">03 / Work</div>
    <h2 class="section-title">Featured Projects</h2>
    <div class="project-grid">

      <div class="project-card">
        <div class="project-header">
          <div class="project-emoji">🖥️</div>
          <div class="project-links">
            <a class="project-link" href="https://github.com/Eddie-Turya/Portfolio">GitHub ↗</a>
          </div>
        </div>
        <div class="project-title">Portfolio Website</div>
        <div class="project-desc">
          A sleek, fully-responsive personal showcase featuring smooth animations, project gallery, and integrated contact. Built for performance and lasting first impressions.
        </div>
        <div class="project-stack">
          <span class="stack-tag">React.js</span>
          <span class="stack-tag">CSS3</span>
          <span class="stack-tag">JavaScript</span>
          <span class="stack-tag">Responsive</span>
        </div>
      </div>

      <div class="project-card">
        <div class="project-header">
          <div class="project-emoji">📅</div>
          <div class="project-links">
            <a class="project-link" href="https://github.com/Eddie-Turya/newbook">GitHub ↗</a>
          </div>
        </div>
        <div class="project-title">Smart Booking System</div>
        <div class="project-desc">
          Full-stack booking platform with JWT authentication, role-based access control, real-time availability, and integrated payment gateway. Production-ready architecture.
        </div>
        <div class="project-stack">
          <span class="stack-tag">Node.js</span>
          <span class="stack-tag">PHP</span>
          <span class="stack-tag">MySQL</span>
          <span class="stack-tag">JWT</span>
          <span class="stack-tag">Payment API</span>
        </div>
      </div>

    </div>
  </section>

  <hr class="divider" />

  <!-- ── STATS ── -->
  <section>
    <div class="section-label">04 / Metrics</div>
    <h2 class="section-title">By the Numbers</h2>

    <div class="stats-grid" style="margin-bottom:32px">
      <div class="stat-card">
        <div class="stat-number">7+</div>
        <div class="stat-label">Languages</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">15+</div>
        <div class="stat-label">Frameworks</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">2+</div>
        <div class="stat-label">Years Coding</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">∞</div>
        <div class="stat-label">Curiosity</div>
      </div>
    </div>

    <div class="github-cards">
      <img src="https://github-readme-stats.vercel.app/api?username=Eddie-Turya&show_icons=true&theme=midnight-purple&hide_border=true&bg_color=0d1120&title_color=00e5ff&icon_color=7b61ff&text_color=c9d1d9&rank_icon=github" height="160" alt="GitHub Stats" />
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=Eddie-Turya&theme=midnight-purple&hide_border=true&background=0d1120&stroke=7b61ff&ring=00e5ff&fire=ff6b35&currStreakLabel=00e5ff" height="160" alt="Streak Stats" />
    </div>
    <br>
    <div style="text-align:center">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Eddie-Turya&layout=compact&theme=midnight-purple&hide_border=true&bg_color=0d1120&title_color=00e5ff&text_color=c9d1d9&langs_count=8" height="155" alt="Top Languages" />
    </div>
  </section>

  <hr class="divider" />

  <!-- ── CONTACT ── -->
  <section>
    <div class="section-label">05 / Connect</div>
    <h2 class="section-title">Let's Build Together</h2>
    <p style="color:#8a93a2;font-size:15px;margin-bottom:28px;line-height:1.7">
      Whether you have a project in mind, a collaboration idea, or just want to talk tech — I'm always open to a good conversation.
    </p>
    <div class="contact-grid">
      <a class="contact-card" href="https://wa.me/255627492719">
        <div class="contact-icon">💬</div>
        <div>
          <div class="contact-info-label">WhatsApp</div>
          <div class="contact-info-value">+255 627 492 719</div>
        </div>
      </a>
      <a class="contact-card" href="mailto:graphereddy@gmail.com">
        <div class="contact-icon">✉️</div>
        <div>
          <div class="contact-info-label">Email</div>
          <div class="contact-info-value">graphereddy@gmail.com</div>
        </div>
      </a>
      <a class="contact-card" href="https://github.com/Eddie-Turya">
        <div class="contact-icon">🐙</div>
        <div>
          <div class="contact-info-label">GitHub</div>
          <div class="contact-info-value">@Eddie-Turya</div>
        </div>
      </a>
      <a class="contact-card" href="https://twitter.com/EdwinTurya">
        <div class="contact-icon">🐦</div>
        <div>
          <div class="contact-info-label">Twitter / X</div>
          <div class="contact-info-value">@EdwinTurya</div>
        </div>
      </a>
      <a class="contact-card" href="https://www.linkedin.com/in/yourprofile">
        <div class="contact-icon">💼</div>
        <div>
          <div class="contact-info-label">LinkedIn</div>
          <div class="contact-info-value">Eddie Turya</div>
        </div>
      </a>
    </div>
  </section>

</main>

<footer>
  <p>Crafted with <span>♥</span> by <span>Eddie Turya</span> · Tanzania 🇹🇿 · <span>2025</span></p>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const trail = document.getElementById('cursorTrail');
  let trailX = 0, trailY = 0;

  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX - 6 + 'px';
    cursor.style.top = e.clientY - 6 + 'px';
    setTimeout(() => {
      trail.style.left = e.clientX - 18 + 'px';
      trail.style.top = e.clientY - 18 + 'px';
    }, 60);
  });

  document.querySelectorAll('a, button, .project-card, .info-card, .stat-card, .contact-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'scale(2.5)';
      trail.style.transform = 'scale(1.4)';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'scale(1)';
      trail.style.transform = 'scale(1)';
    });
  });

  // Typing animation
  const phrases = [
    'Building web apps that scale.',
    'Engineering mobile experiences.',
    'Passionate about clean code.',
    'Open to exciting opportunities.',
    'Let\'s ship something great.'
  ];
  let pi = 0, ci = 0, deleting = false;
  const typeEl = document.getElementById('typeText');

  function type() {
    const current = phrases[pi];
    if (!deleting) {
      typeEl.textContent = current.slice(0, ++ci);
      if (ci === current.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      typeEl.textContent = current.slice(0, --ci);
      if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
    }
    setTimeout(type, deleting ? 40 : 70);
  }
  setTimeout(type, 1400);

  // Intersection observer for nav dots
  const sections = document.querySelectorAll('section');
  const dots = document.querySelectorAll('.nav-dot');
  const allTargets = [document.querySelector('.hero'), ...sections];

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const idx = [...allTargets].indexOf(entry.target);
        dots.forEach((d, i) => d.classList.toggle('active', i === idx));
      }
    });
  }, { threshold: 0.4 });

  allTargets.forEach(t => t && observer.observe(t));
</script>
</body>
</html>
