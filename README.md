<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ahmed Gaber — Backend Developer</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0e0d;
    --bg2: #0f1512;
    --bg3: #141c19;
    --card: #111916;
    --border: #1e2b26;
    --border2: #243530;
    --accent: #1D9E75;
    --accent2: #0f6e56;
    --accent3: #5DCAA5;
    --accent-dim: #1D9E7520;
    --text: #e8f2ee;
    --text2: #8ba89e;
    --text3: #4d6b62;
    --red: #e2554a;
    --blue: #378add;
    --amber: #ef9f27;
    --purple: #7f77dd;
    --mono: 'JetBrains Mono', monospace;
    --display: 'Syne', sans-serif;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--mono);
    font-size: 14px;
    line-height: 1.7;
    min-height: 100vh;
  }

  /* GRID BACKGROUND */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 40px 40px;
    opacity: 0.35;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 100px;
  }

  /* HEADER */
  .header {
    margin-bottom: 60px;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards;
  }

  .header-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 24px;
    flex-wrap: wrap;
    margin-bottom: 32px;
  }

  .header-label {
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--accent);
    font-weight: 500;
    margin-bottom: 10px;
    text-transform: uppercase;
  }

  .name {
    font-family: var(--display);
    font-size: clamp(42px, 8vw, 72px);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -2px;
    color: var(--text);
    margin-bottom: 14px;
  }

  .name span {
    color: var(--accent);
  }

  .tagline {
    font-size: 13px;
    color: var(--text2);
    max-width: 460px;
    line-height: 1.8;
  }

  .header-links {
    display: flex;
    flex-direction: column;
    gap: 8px;
    align-items: flex-end;
    flex-shrink: 0;
  }

  .link-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: var(--text2);
    text-decoration: none;
    transition: color 0.2s;
  }
  .link-item:hover { color: var(--accent3); }
  .link-item .dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--border2);
    flex-shrink: 0;
  }
  .link-item:hover .dot { background: var(--accent); }

  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 24px;
  }

  .badge {
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 2px;
    border: 1px solid;
    font-weight: 500;
    letter-spacing: 0.5px;
  }
  .badge-green { border-color: var(--accent2); color: var(--accent3); background: var(--accent-dim); }
  .badge-blue { border-color: #185fa5; color: #85b7eb; background: #042c5320; }
  .badge-red { border-color: #993c1d; color: #f0997b; background: #4a1b0c20; }
  .badge-amber { border-color: #854f0b; color: #ef9f27; background: #41240220; }
  .badge-purple { border-color: #534ab7; color: #afa9ec; background: #26215c20; }

  /* STATS */
  .stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 4px;
    margin-bottom: 60px;
    overflow: hidden;
    opacity: 0;
    animation: fadeUp 0.7s ease 0.1s forwards;
  }

  .stat {
    background: var(--card);
    padding: 20px 24px;
    text-align: center;
  }

  .stat-num {
    font-family: var(--display);
    font-size: 28px;
    font-weight: 700;
    color: var(--accent3);
    line-height: 1;
    margin-bottom: 6px;
  }

  .stat-label {
    font-size: 11px;
    color: var(--text3);
    letter-spacing: 0.5px;
  }

  /* SECTIONS */
  .section {
    margin-bottom: 56px;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards;
  }

  .section:nth-child(3) { animation-delay: 0.15s; }
  .section:nth-child(4) { animation-delay: 0.2s; }
  .section:nth-child(5) { animation-delay: 0.25s; }
  .section:nth-child(6) { animation-delay: 0.3s; }
  .section:nth-child(7) { animation-delay: 0.35s; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 24px;
  }

  .section-title {
    font-family: var(--display);
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* PROJECT CARDS */
  .projects-grid {
    display: grid;
    gap: 12px;
  }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 24px 28px;
    transition: border-color 0.2s, background 0.2s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: var(--accent);
    opacity: 0;
    transition: opacity 0.2s;
  }

  .project-card:hover {
    border-color: var(--border2);
    background: var(--bg3);
  }

  .project-card:hover::before { opacity: 1; }

  .project-top {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 16px;
    margin-bottom: 10px;
    flex-wrap: wrap;
  }

  .project-name {
    font-family: var(--display);
    font-size: 17px;
    font-weight: 700;
    color: var(--text);
  }

  .project-type {
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 2px;
    letter-spacing: 1px;
    text-transform: uppercase;
    flex-shrink: 0;
  }

  .type-oss { background: #26215c40; color: var(--purple); border: 1px solid #534ab750; }
  .type-pypi { background: #04342c40; color: var(--accent3); border: 1px solid var(--accent2); }
  .type-api { background: #042c5340; color: var(--blue); border: 1px solid #185fa5; }
  .type-realtime { background: #4a1b0c40; color: #f0997b; border: 1px solid #993c1d; }

  .project-links-row {
    display: flex;
    gap: 10px;
    margin-bottom: 14px;
  }

  .plink {
    font-size: 11px;
    color: var(--text3);
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 4px;
    transition: color 0.2s;
  }
  .plink:hover { color: var(--accent3); }
  .plink::before { content: '↗'; font-size: 10px; }

  .project-desc {
    font-size: 12.5px;
    color: var(--text2);
    line-height: 1.75;
    margin-bottom: 16px;
  }

  /* METRICS TABLE */
  .metrics-table {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 3px;
    overflow: hidden;
    margin-bottom: 16px;
    font-size: 12px;
  }

  .metrics-table table {
    width: 100%;
    border-collapse: collapse;
  }

  .metrics-table th {
    text-align: left;
    padding: 7px 14px;
    font-size: 10px;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--text3);
    background: var(--bg);
    border-bottom: 1px solid var(--border);
    font-weight: 500;
  }

  .metrics-table td {
    padding: 7px 14px;
    border-bottom: 1px solid var(--border);
    color: var(--text2);
  }

  .metrics-table tr:last-child td { border-bottom: none; }

  .metric-after {
    color: var(--accent3);
    font-weight: 500;
  }

  .stack-row {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .pill {
    font-size: 10px;
    padding: 3px 9px;
    border-radius: 2px;
    border: 1px solid var(--border);
    color: var(--text3);
    letter-spacing: 0.3px;
    transition: border-color 0.2s, color 0.2s;
  }

  .project-card:hover .pill {
    border-color: var(--border2);
    color: var(--text2);
  }

  /* SKILLS */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
  }

  .skill-group {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 18px 20px;
  }

  .skill-group-title {
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 12px;
    font-weight: 500;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .stag {
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 2px;
    background: var(--bg2);
    border: 1px solid var(--border);
    color: var(--text2);
  }

  /* EXPERIENCE */
  .exp-list { display: flex; flex-direction: column; gap: 2px; }

  .exp-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 20px 24px;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 0 20px;
    position: relative;
  }

  .exp-indicator {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 4px;
  }

  .exp-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    border: 2px solid var(--accent);
    background: var(--bg);
    flex-shrink: 0;
  }

  .exp-line {
    width: 1px;
    flex: 1;
    background: var(--border);
    margin-top: 6px;
  }

  .exp-title {
    font-family: var(--display);
    font-size: 15px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 3px;
    display: flex;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
  }

  .exp-badge {
    font-size: 10px;
    padding: 2px 8px;
    background: #41240240;
    color: var(--amber);
    border: 1px solid #854f0b;
    border-radius: 2px;
    letter-spacing: 0.5px;
  }

  .exp-org {
    font-size: 11px;
    color: var(--text3);
    margin-bottom: 10px;
    letter-spacing: 0.5px;
  }

  .exp-points {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  .exp-points li {
    font-size: 12.5px;
    color: var(--text2);
    display: flex;
    gap: 8px;
    align-items: flex-start;
  }

  .exp-points li::before {
    content: '›';
    color: var(--accent);
    flex-shrink: 0;
    margin-top: 1px;
  }

  /* CONTACT */
  .contact-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
  }

  .contact-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 16px 18px;
    display: flex;
    align-items: center;
    gap: 12px;
    transition: border-color 0.2s;
    text-decoration: none;
  }

  .contact-item:hover { border-color: var(--accent2); }

  .contact-icon {
    font-size: 18px;
    color: var(--accent);
    flex-shrink: 0;
  }

  .contact-label {
    font-size: 10px;
    color: var(--text3);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 2px;
  }

  .contact-value {
    font-size: 12px;
    color: var(--text2);
  }

  /* FOOTER */
  .footer {
    margin-top: 80px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;
  }

  .footer-left {
    font-size: 11px;
    color: var(--text3);
  }

  .footer-left span { color: var(--accent); }

  .footer-right {
    font-size: 11px;
    color: var(--text3);
    letter-spacing: 1px;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 3px; }

  @media (max-width: 600px) {
    .stats { grid-template-columns: repeat(2, 1fr); }
    .skills-grid { grid-template-columns: 1fr; }
    .contact-grid { grid-template-columns: 1fr; }
    .header-top { flex-direction: column; }
    .header-links { align-items: flex-start; }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- HEADER -->
  <header class="header">
    <div class="header-top">
      <div>
        <div class="header-label">// backend engineer</div>
        <div class="name">Ahmed<br><span>Gaber</span></div>
        <p class="tagline">Building scalable, production-ready systems with Python and Django. Focused on async architectures, caching strategies, and real-time applications.</p>
        <div class="badges">
          <span class="badge badge-green">Python · Django · DRF</span>
          <span class="badge badge-red">Redis · Celery</span>
          <span class="badge badge-blue">PostgreSQL</span>
          <span class="badge badge-amber">Docker · AWS EC2</span>
          <span class="badge badge-purple">WebSockets</span>
        </div>
      </div>
      <div class="header-links">
        <a href="mailto:ahmed.gaber.dev@gmail.com" class="link-item">
          <span class="dot"></span> ahmed.gaber.dev@gmail.com
        </a>
        <a href="https://www.linkedin.com/in/ahmed-gaber-509b88359" class="link-item">
          <span class="dot"></span> linkedin.com/in/ahmed-gaber
        </a>
        <a href="https://codekat123.github.io/portfolio/" class="link-item">
          <span class="dot"></span> portfolio
        </a>
        <a href="https://leetcode.com/u/codekat123/" class="link-item">
          <span class="dot"></span> leetcode / codekat123
        </a>
        <span class="link-item">
          <span class="dot"></span> Sharkia / Cairo, Egypt
        </span>
      </div>
    </div>
  </header>

  <!-- STATS -->
  <div class="stats">
    <div class="stat">
      <div class="stat-num">4</div>
      <div class="stat-label">Projects shipped</div>
    </div>
    <div class="stat">
      <div class="stat-num">2</div>
      <div class="stat-label">Open source contributions</div>
    </div>
    <div class="stat">
      <div class="stat-num">~50%</div>
      <div class="stat-label">Avg. latency reduction</div>
    </div>
    <div class="stat">
      <div class="stat-num">1</div>
      <div class="stat-label">PyPI package published</div>
    </div>
  </div>

  <!-- PROJECTS -->
  <section class="section">
    <div class="section-header">
      <div class="section-title">Projects</div>
      <div class="section-line"></div>
    </div>
    <div class="projects-grid">

      <!-- E-Commerce -->
      <div class="project-card">
        <div class="project-top">
          <div class="project-name">E-Commerce REST API</div>
          <span class="project-type type-api">REST API</span>
        </div>
        <div class="project-links-row">
          <a href="#" class="plink">Live Demo</a>
          <a href="#" class="plink">GitHub</a>
        </div>
        <p class="project-desc">
          Full-featured e-commerce backend with 25+ endpoints covering products, cart, orders, wallet, and user management. JWT auth with custom user model and role-based access control. Stripe payments with webhook handling. Secured with HTTPS via Let's Encrypt, served behind NGINX, deployed on AWS EC2.
        </p>
        <div class="metrics-table">
          <table>
            <thead>
              <tr>
                <th>Optimization</th>
                <th>Before</th>
                <th>After</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Endpoint response time</td>
                <td>baseline</td>
                <td class="metric-after">~50% faster (Redis cache)</td>
              </tr>
              <tr>
                <td>API blocking time (tasks)</td>
                <td>~2s</td>
                <td class="metric-after">&lt;200ms (Celery offload)</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="stack-row">
          <span class="pill">Django</span><span class="pill">DRF</span><span class="pill">PostgreSQL</span><span class="pill">Redis</span><span class="pill">Celery</span><span class="pill">JWT</span><span class="pill">Docker</span><span class="pill">AWS EC2</span><span class="pill">Stripe</span><span class="pill">NGINX</span>
        </div>
      </div>

      <!-- WhatsApp Clone -->
      <div class="project-card">
        <div class="project-top">
          <div class="project-name">WhatsApp Clone — Real-Time Chat</div>
          <span class="project-type type-realtime">Real-Time</span>
        </div>
        <div class="project-links-row">
          <a href="#" class="plink">Live Demo</a>
          <a href="#" class="plink">GitHub</a>
        </div>
        <p class="project-desc">
          Real-time group chat application with OTP-based authentication, JWT session authorization, and persistent WebSocket connections for low-latency message delivery. Group chat system with admin/user role-based permissions. Containerized with Docker and documented via Swagger/OpenAPI.
        </p>
        <div class="stack-row">
          <span class="pill">Django Channels</span><span class="pill">WebSockets</span><span class="pill">PostgreSQL</span><span class="pill">JWT</span><span class="pill">Docker</span><span class="pill">Swagger</span><span class="pill">OTP Auth</span>
        </div>
      </div>

      <!-- Publisher Stats -->
      <div class="project-card">
        <div class="project-top">
          <div class="project-name">Publisher Statistics Service</div>
          <span class="project-type type-oss">Open Source</span>
        </div>
        <div class="project-links-row">
          <a href="#" class="plink">Contribution</a>
        </div>
        <p class="project-desc">
          Contributed a scalable statistics endpoint for aggregated publisher data to an open-source Django project. Implemented event-driven cache invalidation via Django signals, and an async processing pipeline with Celery Beat for scheduled background tasks. Includes unit tests for caching, data correctness, and access control.
        </p>
        <div class="metrics-table">
          <table>
            <thead>
              <tr>
                <th>Metric</th>
                <th>Before</th>
                <th>After</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Average response time</td>
                <td>~400ms</td>
                <td class="metric-after">~120ms (Redis caching)</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="stack-row">
          <span class="pill">Django Ninja</span><span class="pill">Redis</span><span class="pill">Celery Beat</span><span class="pill">PostgreSQL</span><span class="pill">Django Signals</span><span class="pill">Unit Tests</span>
        </div>
      </div>

      <!-- django-api-profiler -->
      <div class="project-card">
        <div class="project-top">
          <div class="project-name">django-api-profiler</div>
          <span class="project-type type-pypi">PyPI Package</span>
        </div>
        <div class="project-links-row">
          <a href="#" class="plink">Live Demo</a>
          <a href="#" class="plink">GitHub</a>
          <a href="#" class="plink">PyPI</a>
        </div>
        <p class="project-desc">
          A reusable Django observability and monitoring package published on PyPI. Middleware-based request instrumentation, SQL query tracking, and N+1 query detection. Async metric ingestion via Celery/Redis with automatic sync fallback. Endpoint aggregation with p95 latency and error-rate analytics. Ships with admin dashboards, automated tests, and CI/CD workflows.
        </p>
        <div class="stack-row">
          <span class="pill">Django</span><span class="pill">Middleware</span><span class="pill">Redis</span><span class="pill">Celery</span><span class="pill">N+1 Detection</span><span class="pill">CI/CD</span><span class="pill">PyPI</span><span class="pill">Swagger</span>
        </div>
      </div>

    </div>
  </section>

  <!-- SKILLS -->
  <section class="section">
    <div class="section-header">
      <div class="section-title">Tech Stack</div>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-group">
        <div class="skill-group-title">Backend & APIs</div>
        <div class="skill-tags">
          <span class="stag">Django</span>
          <span class="stag">DRF</span>
          <span class="stag">Celery</span>
          <span class="stag">Django Channels</span>
          <span class="stag">WebSockets</span>
          <span class="stag">JWT</span>
          <span class="stag">REST Design</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Databases & Caching</div>
        <div class="skill-tags">
          <span class="stag">PostgreSQL</span>
          <span class="stag">Redis</span>
          <span class="stag">MySQL</span>
          <span class="stag">MongoDB</span>
          <span class="stag">SQLite</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">DevOps & Tooling</div>
        <div class="skill-tags">
          <span class="stag">Docker</span>
          <span class="stag">AWS EC2</span>
          <span class="stag">NGINX</span>
          <span class="stag">Linux</span>
          <span class="stag">Git</span>
          <span class="stag">Postman</span>
          <span class="stag">Swagger</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Languages & Concepts</div>
        <div class="skill-tags">
          <span class="stag">Python</span>
          <span class="stag">C</span>
          <span class="stag">C++</span>
          <span class="stag">OOP</span>
          <span class="stag">Design Patterns</span>
          <span class="stag">SOLID</span>
          <span class="stag">Clean Architecture</span>
        </div>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section class="section">
    <div class="section-header">
      <div class="section-title">Experience</div>
      <div class="section-line"></div>
    </div>
    <div class="exp-list">

      <div class="exp-card">
        <div class="exp-indicator">
          <div class="exp-dot"></div>
          <div class="exp-line"></div>
        </div>
        <div>
          <div class="exp-title">
            CIS Team MU — Django Backend Circle
            <span class="exp-badge">⭐ Top Member</span>
          </div>
          <div class="exp-org">// Backend Circle Member · Mansoura University</div>
          <ul class="exp-points">
            <li>Recognized as Top Member for outstanding performance and dedication</li>
            <li>Built and debugged production-grade APIs with the backend team</li>
            <li>Applied clean architecture principles across collaborative projects</li>
          </ul>
        </div>
      </div>

      <div class="exp-card">
        <div class="exp-indicator">
          <div class="exp-dot" style="border-color: var(--blue);"></div>
        </div>
        <div>
          <div class="exp-title">DIGITOPIA — AI & Software Competition</div>
          <div class="exp-org">// MCIT · Ministry of Communications & Information Technology</div>
          <ul class="exp-points">
            <li>Collaborated with cross-functional teams in a high-pressure competitive environment</li>
            <li>Delivered results under tight deadlines and shared objectives</li>
          </ul>
        </div>
      </div>

    </div>
  </section>

  <!-- CONTACT -->
  <section class="section">
    <div class="section-header">
      <div class="section-title">Contact</div>
      <div class="section-line"></div>
    </div>
    <div class="contact-grid">
      <a href="mailto:ahmed.gaber.dev@gmail.com" class="contact-item">
        <span class="contact-icon">✉</span>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-value">ahmed.gaber.dev@gmail.com</div>
        </div>
      </a>
      <a href="tel:+201004968716" class="contact-item">
        <span class="contact-icon">✆</span>
        <div>
          <div class="contact-label">Phone</div>
          <div class="contact-value">+201004968716</div>
        </div>
      </a>
      <span class="contact-item">
        <span class="contact-icon">⌖</span>
        <div>
          <div class="contact-label">Location</div>
          <div class="contact-value">Sharkia / Cairo, Egypt</div>
        </div>
      </span>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer">
    <div class="footer-left">
      Built by <span>Ahmed Gaber</span> · Backend Developer
    </div>
    <div class="footer-right">Python · Django · DRF</div>
  </footer>

</div>
</body>
</html>
