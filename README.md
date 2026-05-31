<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mutunga Willy — Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0a0a0f;
      --bg2: #111118;
      --bg3: #16161f;
      --border: rgba(255,255,255,0.07);
      --border-hover: rgba(255,255,255,0.15);
      --accent: #7df2c1;
      --accent2: #5b8ef0;
      --text: #f0ede8;
      --muted: #7a7886;
      --card-bg: #13131a;
      --font-display: 'Syne', sans-serif;
      --font-body: 'DM Sans', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--font-body);
      font-size: 16px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* ── Noise overlay ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 9999;
      opacity: 0.4;
    }

    /* ── Nav ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.2rem 3rem;
      background: rgba(10,10,15,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo {
      font-family: var(--font-display);
      font-weight: 800;
      font-size: 1.1rem;
      color: var(--text);
      text-decoration: none;
      letter-spacing: -0.02em;
    }

    .nav-logo span { color: var(--accent); }

    .nav-links {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.88rem;
      font-weight: 500;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--text); }

    /* ── Hero ── */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 8rem 3rem 5rem;
      max-width: 1000px;
      margin: 0 auto;
      position: relative;
    }

    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.8rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1.5rem;
      opacity: 0;
      animation: fadeUp 0.7s 0.1s forwards;
    }

    .hero-tag::before {
      content: '';
      display: block;
      width: 24px;
      height: 1px;
      background: var(--accent);
    }

    h1.hero-name {
      font-family: var(--font-display);
      font-size: clamp(3rem, 8vw, 6.5rem);
      font-weight: 800;
      line-height: 1;
      letter-spacing: -0.04em;
      color: var(--text);
      opacity: 0;
      animation: fadeUp 0.8s 0.2s forwards;
    }

    h1.hero-name em {
      font-style: normal;
      color: transparent;
      -webkit-text-stroke: 1px rgba(255,255,255,0.25);
    }

    .hero-sub {
      font-size: 1.15rem;
      color: var(--muted);
      margin-top: 1.5rem;
      max-width: 500px;
      font-weight: 300;
      opacity: 0;
      animation: fadeUp 0.8s 0.35s forwards;
    }

    .hero-ctas {
      display: flex;
      gap: 1rem;
      margin-top: 2.5rem;
      opacity: 0;
      animation: fadeUp 0.8s 0.5s forwards;
    }

    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.75rem 1.75rem;
      background: var(--accent);
      color: #0a0a0f;
      font-family: var(--font-body);
      font-weight: 600;
      font-size: 0.9rem;
      border-radius: 100px;
      text-decoration: none;
      transition: opacity 0.2s, transform 0.2s;
    }

    .btn-primary:hover { opacity: 0.85; transform: translateY(-2px); }

    .btn-ghost {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.75rem 1.75rem;
      background: transparent;
      color: var(--text);
      font-family: var(--font-body);
      font-weight: 500;
      font-size: 0.9rem;
      border: 1px solid var(--border-hover);
      border-radius: 100px;
      text-decoration: none;
      transition: border-color 0.2s, transform 0.2s;
    }

    .btn-ghost:hover { border-color: var(--text); transform: translateY(-2px); }

    /* Floating glow */
    .hero-glow {
      position: absolute;
      top: 20%;
      right: -10%;
      width: 500px;
      height: 500px;
      background: radial-gradient(circle, rgba(125,242,193,0.06) 0%, transparent 70%);
      pointer-events: none;
    }

    /* ── Section layout ── */
    section {
      max-width: 1000px;
      margin: 0 auto;
      padding: 5rem 3rem;
    }

    .section-label {
      font-size: 0.78rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 0.75rem;
    }

    h2.section-title {
      font-family: var(--font-display);
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 800;
      letter-spacing: -0.03em;
      color: var(--text);
      line-height: 1.1;
      margin-bottom: 3rem;
    }

    /* ── About ── */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: start;
    }

    .about-text p {
      color: var(--muted);
      font-weight: 300;
      margin-bottom: 1rem;
      line-height: 1.8;
    }

    .about-text p strong {
      color: var(--text);
      font-weight: 500;
    }

    .about-stats {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
      border-radius: 16px;
      overflow: hidden;
    }

    .stat-cell {
      background: var(--card-bg);
      padding: 1.75rem;
    }

    .stat-cell .num {
      font-family: var(--font-display);
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--accent);
      letter-spacing: -0.03em;
      line-height: 1;
    }

    .stat-cell .label {
      font-size: 0.82rem;
      color: var(--muted);
      margin-top: 0.3rem;
    }

    /* ── Projects ── */
    #projects { background: none; }

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
    }

    .project-card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 2rem;
      transition: border-color 0.25s, transform 0.25s;
      position: relative;
      overflow: hidden;
    }

    .project-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      opacity: 0;
      transition: opacity 0.25s;
    }

    .project-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-4px);
    }

    .project-card:hover::before { opacity: 1; }

    .project-icon {
      width: 44px;
      height: 44px;
      background: rgba(125,242,193,0.08);
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.3rem;
      margin-bottom: 1.25rem;
    }

    .project-card h3 {
      font-family: var(--font-display);
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 0.5rem;
      letter-spacing: -0.01em;
    }

    .project-card p {
      font-size: 0.9rem;
      color: var(--muted);
      font-weight: 300;
      line-height: 1.6;
      margin-bottom: 1.5rem;
    }

    .project-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-bottom: 1.5rem;
    }

    .tag {
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.04em;
      padding: 0.25rem 0.6rem;
      border-radius: 100px;
      background: rgba(255,255,255,0.05);
      color: var(--muted);
      border: 1px solid var(--border);
    }

    .project-link {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      font-size: 0.85rem;
      font-weight: 500;
      color: var(--accent);
      text-decoration: none;
      transition: gap 0.2s;
    }

    .project-link:hover { gap: 0.7rem; }
    .project-link::after { content: '→'; }

    /* ── Skills ── */
    .skills-layout {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
    }

    .skill-group h3 {
      font-family: var(--font-display);
      font-size: 0.85rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 1rem;
    }

    .skill-list {
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
    }

    .skill-item {
      display: flex;
      align-items: center;
      gap: 0.75rem;
    }

    .skill-dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--accent);
      flex-shrink: 0;
    }

    .skill-item span {
      font-size: 0.95rem;
      color: var(--text);
      font-weight: 300;
    }

    /* ── Contact ── */
    #contact {
      border-top: 1px solid var(--border);
    }

    .contact-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: center;
    }

    .contact-text p {
      color: var(--muted);
      font-weight: 300;
      margin-bottom: 2rem;
    }

    .contact-links {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .contact-link {
      display: flex;
      align-items: center;
      gap: 1rem;
      text-decoration: none;
      color: var(--text);
      padding: 1rem 1.25rem;
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 12px;
      transition: border-color 0.2s, transform 0.2s;
      font-size: 0.9rem;
    }

    .contact-link:hover {
      border-color: var(--border-hover);
      transform: translateX(4px);
    }

    .contact-link-icon {
      width: 36px;
      height: 36px;
      border-radius: 8px;
      background: rgba(125,242,193,0.1);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      flex-shrink: 0;
    }

    .contact-link-text small {
      display: block;
      font-size: 0.72rem;
      color: var(--muted);
      letter-spacing: 0.04em;
      text-transform: uppercase;
      margin-bottom: 0.1rem;
    }

    /* ── Footer ── */
    footer {
      border-top: 1px solid var(--border);
      padding: 2rem 3rem;
      text-align: center;
      color: var(--muted);
      font-size: 0.82rem;
    }

    footer span { color: var(--accent); }

    /* ── Divider ── */
    .divider {
      border: none;
      border-top: 1px solid var(--border);
    }

    /* ── Animations ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* ── Scroll reveal ── */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ── Mobile ── */
    @media (max-width: 700px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { gap: 1.5rem; }
      .hero { padding: 7rem 1.5rem 4rem; }
      section { padding: 4rem 1.5rem; }
      .about-grid,
      .skills-layout,
      .contact-inner { grid-template-columns: 1fr; gap: 2rem; }
      .about-stats { grid-template-columns: 1fr 1fr; }
    }
  </style>
</head>
<body>

  <!-- Navigation -->
  <nav>
    <a href="#" class="nav-logo">MW<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- Hero -->
  <div class="hero">
    <div class="hero-glow"></div>
    <p class="hero-tag">Available for Hiring</p>
    <h1 class="hero-name">Mutunga<br><em>Willy</em></h1>
    <p class="hero-sub">CS &amp; Cybersecurity student. Aspiring data analyst. Building things that matter at the intersection of security and data.</p>
    <div class="hero-ctas">
      <a href="#projects" class="btn-primary">View my work</a>
      <a href="#contact" class="btn-ghost">Get in touch</a>
    </div>
  </div>

  <!-- About -->
  <section id="about">
    <p class="section-label reveal">About me</p>
    <h2 class="section-title reveal">Driven by curiosity,<br>grounded in code.</h2>
    <div class="about-grid reveal">
      <div class="about-text">
        <p>I'm <strong>Mutunga Willy</strong>, a Diploma student in Computer Science &amp; Cybersecurity with a genuine passion for data, security, and building useful things.</p>
        <p>I'm actively seeking an <strong>attachment opportunity</strong> where I can contribute meaningfully, sharpen my technical skills, and grow under experienced mentors.</p>
        <p>Whether it's analysing data in Python, securing a network, or crafting a clean database schema — I bring curiosity and care to every project.</p>
      </div>
      <div class="about-stats">
        <div class="stat-cell">
          <div class="num">3+</div>
          <div class="label">Projects completed</div>
        </div>
        <div class="stat-cell">
          <div class="num">2</div>
          <div class="label">Core disciplines</div>
        </div>
        <div class="stat-cell">
          <div class="num">5+</div>
          <div class="label">Technical skills</div>
        </div>
        <div class="stat-cell">
          <div class="num">∞</div>
          <div class="label">Problems to solve</div>
        </div>
      </div>
    </div>
  </section>

  <hr class="divider" style="max-width:1000px; margin:0 auto 0 auto;">

  <!-- Projects -->
  <section id="projects">
    <p class="section-label reveal">What I've built</p>
    <h2 class="section-title reveal">Projects</h2>
    <div class="projects-grid reveal">

      <div class="project-card">
        <div class="project-icon">🛡️</div>
        <h3>Cyber Security Lab Simulation</h3>
        <p>Penetration testing on virtual machines using industry-standard tools to identify and exploit vulnerabilities in a controlled environment.</p>
        <div class="project-tags">
          <span class="tag">Kali Linux</span>
          <span class="tag">Wireshark</span>
          <span class="tag">Pen Testing</span>
        </div>
        <a href="https://github.com/wiley-pixel/cyberlab" target="_blank" class="project-link">View on GitHub</a>
      </div>

      <div class="project-card">
        <div class="project-icon">🗄️</div>
        <h3>Database Management System</h3>
        <p>Designed and implemented a MySQL database for a retail shop to manage sales records, inventory tracking, and basic reporting.</p>
        <div class="project-tags">
          <span class="tag">MySQL</span>
          <span class="tag">SQL</span>
          <span class="tag">Data Modeling</span>
        </div>
        <a href="https://github.com/wiley-pixel/database-project" target="_blank" class="project-link">View on GitHub</a>
      </div>

      <div class="project-card">
        <div class="project-icon">🌐</div>
        <h3>Portfolio Website</h3>
        <p>This portfolio — designed and built from scratch using HTML, CSS, JavaScript and Tailwind to showcase my work and skills.</p>
        <div class="project-tags">
          <span class="tag">HTML/CSS</span>
          <span class="tag">JavaScript</span>
          <span class="tag">Tailwind</span>
        </div>
        <a href="https://mutungawillyportfolio.com" target="_blank" class="project-link">Live Demo</a>
      </div>

    </div>
  </section>

  <hr class="divider" style="max-width:1000px; margin:0 auto;">

  <!-- Skills -->
  <section id="skills">
    <p class="section-label reveal">What I know</p>
    <h2 class="section-title reveal">Technical skills</h2>
    <div class="skills-layout reveal">

      <div class="skill-group">
        <h3>Languages &amp; Data</h3>
        <div class="skill-list">
          <div class="skill-item"><div class="skill-dot"></div><span>Python</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>Java</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>C (basics)</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>MySQL &amp; SQL queries</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>Power BI &amp; Excel</span></div>
        </div>
      </div>

      <div class="skill-group">
        <h3>Security &amp; Networking</h3>
        <div class="skill-list">
          <div class="skill-item"><div class="skill-dot"></div><span>Ethical hacking fundamentals</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>Kali Linux</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>Wireshark &amp; packet analysis</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>Network troubleshooting</span></div>
          <div class="skill-item"><div class="skill-dot"></div><span>System administration basics</span></div>
        </div>
      </div>

    </div>
  </section>

  <hr class="divider" style="max-width:1000px; margin:0 auto;">

  <!-- Contact -->
  <section id="contact">
    <div class="contact-inner">
      <div class="contact-text reveal">
        <p class="section-label">Let's connect</p>
        <h2 class="section-title" style="margin-bottom:1rem;">Open to<br>opportunities.</h2>
        <p>I'm looking for attachment placements where I can contribute, learn, and grow. If you think there's a fit, I'd love to hear from you.</p>
        <a href="mailto:mutungawilly38@gmail.com" class="btn-primary" style="margin-top:0.5rem;">Send me an email</a>
      </div>
      <div class="contact-links reveal">
        <a href="mailto:mutungawilly38@gmail.com" class="contact-link">
          <div class="contact-link-icon">✉️</div>
          <div class="contact-link-text">
            <small>Email</small>
            mutungawilly38@gmail.com
          </div>
        </a>
        <a href="https://linkedin.com/in/yourprofile" target="_blank" class="contact-link">
          <div class="contact-link-icon">💼</div>
          <div class="contact-link-text">
            <small>LinkedIn</small>
            linkedin.com/in/yourprofile
          </div>
        </a>
        <a href="https://github.com/wiley-pixel" target="_blank" class="contact-link">
          <div class="contact-link-icon">🐙</div>
          <div class="contact-link-text">
            <small>GitHub</small>
            github.com/wiley-pixel
          </div>
        </a>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <p>© 2025 <span>Mutunga Willy</span> — Built with care.</p>
  </footer>

  <script>
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach((e, i) => {
        if (e.isIntersecting) {
          setTimeout(() => e.target.classList.add('visible'), i * 80);
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.1 });
    reveals.forEach(el => observer.observe(el));
  </script>
</body>
</html>
