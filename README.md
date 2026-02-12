<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ismail Sirsikar — Full-Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;700;800&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #050508;
    --surface: #0d0d14;
    --card: #111120;
    --border: rgba(120,100,255,0.15);
    --accent1: #7b5cf0;
    --accent2: #00e5ff;
    --accent3: #ff4d8d;
    --accent4: #39ff9a;
    --text: #e8e8f0;
    --muted: #6a6a8a;
    --glow1: rgba(123,92,240,0.3);
    --glow2: rgba(0,229,255,0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Serif Display', serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 10px; height: 10px;
    background: var(--accent2);
    border-radius: 50%;
    position: fixed; pointer-events: none; z-index: 9999;
    transition: transform 0.1s ease, opacity 0.1s;
    mix-blend-mode: difference;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid var(--accent1);
    border-radius: 50%;
    position: fixed; pointer-events: none; z-index: 9998;
    transition: transform 0.25s ease;
    mix-blend-mode: difference;
  }

  /* Grid noise overlay */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(123,92,240,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(123,92,240,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none; z-index: 0;
  }

  /* Ambient blobs */
  .blob {
    position: fixed; border-radius: 50%; filter: blur(100px);
    pointer-events: none; z-index: 0; animation: drift 20s infinite alternate ease-in-out;
  }
  .blob1 { width: 600px; height: 600px; background: var(--glow1); top: -200px; left: -150px; }
  .blob2 { width: 500px; height: 500px; background: var(--glow2); bottom: -150px; right: -100px; animation-delay: -10s; }
  .blob3 { width: 300px; height: 300px; background: rgba(255,77,141,0.1); top: 50%; left: 40%; animation-delay: -5s; }

  @keyframes drift {
    from { transform: translate(0,0) scale(1); }
    to   { transform: translate(40px, 30px) scale(1.1); }
  }

  /* Layout */
  .wrapper {
    max-width: 860px; margin: 0 auto;
    padding: 60px 32px 120px;
    position: relative; z-index: 1;
  }

  /* ── HEADER ── */
  header {
    position: relative; margin-bottom: 80px;
  }

  .header-tag {
    font-family: 'Space Mono', monospace;
    font-size: 11px; letter-spacing: 4px;
    color: var(--accent4); text-transform: uppercase;
    margin-bottom: 20px; opacity: 0;
    animation: fadeUp 0.6s 0.1s forwards;
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 8vw, 92px);
    font-weight: 800; line-height: 0.92;
    letter-spacing: -3px;
    opacity: 0; animation: fadeUp 0.7s 0.2s forwards;
  }

  h1 .first { color: var(--text); }
  h1 .last {
    display: block;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .subtitle {
    font-family: 'Space Mono', monospace;
    font-size: 13px; line-height: 1.9;
    color: var(--muted); margin-top: 28px;
    max-width: 480px; border-left: 2px solid var(--accent1);
    padding-left: 16px; opacity: 0;
    animation: fadeUp 0.7s 0.4s forwards;
  }

  .subtitle em { color: var(--accent2); font-style: normal; }

  /* glitch effect on name */
  .glitch {
    position: relative; display: inline-block;
  }
  .glitch::before, .glitch::after {
    content: attr(data-text);
    position: absolute; top: 0; left: 0; width: 100%; height: 100%;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .glitch::before {
    animation: glitch1 4s infinite; left: 2px;
    clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
  }
  .glitch::after {
    animation: glitch2 4s infinite; left: -2px;
    clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
  }
  @keyframes glitch1 {
    0%,95%  { opacity: 0; transform: translateX(0); }
    96%     { opacity: 0.8; transform: translateX(-3px); }
    97%     { opacity: 0; }
    98%     { opacity: 0.6; transform: translateX(3px); }
    99%,100%{ opacity: 0; }
  }
  @keyframes glitch2 {
    0%,92%  { opacity: 0; }
    93%     { opacity: 0.7; transform: translateX(2px); }
    94%     { opacity: 0; }
    95%     { opacity: 0.5; transform: translateX(-4px); }
    96%,100%{ opacity: 0; }
  }

  /* Status badge */
  .status {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: 'Space Mono', monospace; font-size: 11px;
    color: var(--accent4); border: 1px solid rgba(57,255,154,0.3);
    padding: 6px 14px; border-radius: 100px;
    margin-top: 28px; opacity: 0;
    animation: fadeUp 0.7s 0.55s forwards;
  }
  .status-dot {
    width: 7px; height: 7px; border-radius: 50%;
    background: var(--accent4);
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%,100% { box-shadow: 0 0 0 0 rgba(57,255,154,0.6); }
    50%     { box-shadow: 0 0 0 6px rgba(57,255,154,0); }
  }

  /* ── DIVIDER ── */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent1), var(--accent2), transparent);
    margin: 48px 0; opacity: 0.4;
  }

  /* ── SECTION LABEL ── */
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px; letter-spacing: 5px;
    color: var(--accent1); text-transform: uppercase;
    margin-bottom: 24px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::after {
    content: ''; flex: 1; height: 1px;
    background: var(--border);
  }

  /* ── TECH GRID ── */
  .tech-section { margin-bottom: 72px; }

  .tech-categories {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
  }

  .tech-cat {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px; padding: 20px 22px;
    position: relative; overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
    opacity: 0; animation: fadeUp 0.6s forwards;
  }
  .tech-cat:hover {
    border-color: rgba(123,92,240,0.5);
    transform: translateY(-3px);
  }
  .tech-cat::before {
    content: ''; position: absolute;
    top: 0; left: 0; right: 0; height: 2px;
  }
  .tech-cat.cat-backend::before  { background: linear-gradient(90deg, var(--accent1), transparent); }
  .tech-cat.cat-frontend::before { background: linear-gradient(90deg, var(--accent2), transparent); }
  .tech-cat.cat-mobile::before   { background: linear-gradient(90deg, var(--accent3), transparent); }
  .tech-cat.cat-cloud::before    { background: linear-gradient(90deg, var(--accent4), transparent); }
  .tech-cat.cat-db::before       { background: linear-gradient(90deg, #ff9a3c, transparent); }
  .tech-cat.cat-tools::before    { background: linear-gradient(90deg, #c084fc, transparent); }

  .cat-title {
    font-family: 'Space Mono', monospace;
    font-size: 10px; letter-spacing: 3px;
    text-transform: uppercase; margin-bottom: 14px;
  }
  .cat-backend  .cat-title { color: var(--accent1); }
  .cat-frontend .cat-title { color: var(--accent2); }
  .cat-mobile   .cat-title { color: var(--accent3); }
  .cat-cloud    .cat-title { color: var(--accent4); }
  .cat-db       .cat-title { color: #ff9a3c; }
  .cat-tools    .cat-title { color: #c084fc; }

  .tech-pills {
    display: flex; flex-wrap: wrap; gap: 7px;
  }
  .pill {
    font-family: 'Space Mono', monospace;
    font-size: 10px; padding: 4px 10px;
    border-radius: 6px; color: var(--text);
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.08);
    transition: background 0.2s, border-color 0.2s;
  }
  .pill:hover {
    background: rgba(123,92,240,0.2);
    border-color: rgba(123,92,240,0.4);
  }

  /* stagger delays for tech cards */
  .tech-cat:nth-child(1) { animation-delay: 0.1s; }
  .tech-cat:nth-child(2) { animation-delay: 0.18s; }
  .tech-cat:nth-child(3) { animation-delay: 0.26s; }
  .tech-cat:nth-child(4) { animation-delay: 0.34s; }
  .tech-cat:nth-child(5) { animation-delay: 0.42s; }
  .tech-cat:nth-child(6) { animation-delay: 0.5s; }

  /* ── STATS ── */
  .stats-section { margin-bottom: 72px; }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }

  .stat-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 28px 24px;
    text-align: center; position: relative; overflow: hidden;
    opacity: 0; animation: fadeUp 0.6s forwards;
    transition: transform 0.3s, border-color 0.3s;
  }
  .stat-card:hover {
    transform: translateY(-4px);
    border-color: rgba(123,92,240,0.4);
  }
  .stat-card::after {
    content: '';
    position: absolute; bottom: 0; left: 0; right: 0; height: 60px;
    background: linear-gradient(to top, var(--glow1), transparent);
    opacity: 0.3;
  }

  .stat-number {
    font-family: 'Syne', sans-serif;
    font-size: 48px; font-weight: 800;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text; line-height: 1;
    margin-bottom: 8px;
  }
  .stat-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px; letter-spacing: 3px;
    color: var(--muted); text-transform: uppercase;
  }

  .stat-card:nth-child(1) { animation-delay: 0.1s; }
  .stat-card:nth-child(2) { animation-delay: 0.2s; }
  .stat-card:nth-child(3) { animation-delay: 0.3s; }

  /* ── SOCIALS ── */
  .socials-section { margin-bottom: 72px; }

  .socials-row {
    display: flex; gap: 12px; flex-wrap: wrap;
  }

  .social-link {
    display: inline-flex; align-items: center; gap: 10px;
    font-family: 'Space Mono', monospace; font-size: 11px;
    color: var(--text); text-decoration: none;
    background: var(--card); border: 1px solid var(--border);
    padding: 10px 18px; border-radius: 100px;
    transition: all 0.3s; position: relative; overflow: hidden;
    opacity: 0; animation: fadeUp 0.6s forwards;
  }
  .social-link::before {
    content: ''; position: absolute; inset: 0;
    background: var(--accent1); opacity: 0;
    transition: opacity 0.3s;
  }
  .social-link:hover { border-color: var(--accent1); color: #fff; transform: translateY(-2px); }
  .social-link:hover::before { opacity: 0.15; }

  .social-link span { position: relative; z-index: 1; }
  .social-icon { font-size: 15px; position: relative; z-index: 1; }

  .social-link:nth-child(1) { animation-delay: 0.1s; }
  .social-link:nth-child(2) { animation-delay: 0.18s; }
  .social-link:nth-child(3) { animation-delay: 0.26s; }
  .social-link:nth-child(4) { animation-delay: 0.34s; }

  /* ── GITHUB STATS EMBED ── */
  .github-section { margin-bottom: 72px; }

  .github-cards {
    display: grid; gap: 16px;
    grid-template-columns: 1fr 1fr;
  }
  .github-card-wide { grid-column: 1/-1; }

  .github-img-wrap {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
    opacity: 0; animation: fadeUp 0.7s forwards;
  }
  .github-img-wrap:hover {
    border-color: rgba(123,92,240,0.5); transform: translateY(-3px);
  }
  .github-img-wrap img { width: 100%; display: block; }

  .github-img-wrap:nth-child(1) { animation-delay: 0.1s; }
  .github-img-wrap:nth-child(2) { animation-delay: 0.2s; }
  .github-img-wrap:nth-child(3) { animation-delay: 0.3s; }

  /* ── FOOTER ── */
  footer {
    text-align: center; padding-top: 48px;
    border-top: 1px solid var(--border);
  }

  .footer-text {
    font-family: 'Space Mono', monospace;
    font-size: 10px; letter-spacing: 3px;
    color: var(--muted); text-transform: uppercase;
  }
  .footer-text em {
    color: var(--accent1); font-style: normal;
  }

  .visitor-badge {
    display: inline-flex; align-items: center; gap: 8px;
    margin-top: 16px; font-family: 'Space Mono', monospace;
    font-size: 10px; color: var(--muted);
  }
  .visitor-count {
    font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700;
    color: var(--accent2);
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Scan line effect */
  body::after {
    content: '';
    position: fixed; inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.04) 2px,
      rgba(0,0,0,0.04) 4px
    );
    pointer-events: none; z-index: 0;
  }

  /* Responsive */
  @media (max-width: 600px) {
    .stats-grid { grid-template-columns: 1fr 1fr; }
    .github-cards { grid-template-columns: 1fr; }
    .github-card-wide { grid-column: auto; }
    h1 { font-size: 48px; }
  }

  /* Terminal blink cursor */
  .blink { animation: blink 1s step-end infinite; }
  @keyframes blink { 0%,100%{opacity:1;} 50%{opacity:0;} }

  /* Animated counter */
  .count-up { display: inline-block; }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<div class="blob blob1"></div>
<div class="blob blob2"></div>
<div class="blob blob3"></div>

<div class="wrapper">

  <!-- ── HEADER ── -->
  <header>
    <p class="header-tag">&#x2f;&#x2f; full-stack engineer — available for work</p>
    <h1>
      <span class="first">Ismail</span>
      <span class="last glitch" data-text="Sirsikar">Sirsikar</span>
    </h1>
    <p class="subtitle">
      Architecting <em>scalable systems</em> &amp; <em>beautiful interfaces</em><br>
      .NET · React · Node.js · Azure · AWS<br>
      Clean code. Zero compromise.<span class="blink">_</span>
    </p>
    <div class="status">
      <span class="status-dot"></span>
      Open to exciting opportunities
    </div>
  </header>

  <!-- ── STATS ── -->
  <section class="stats-section">
    <div class="section-label">At a Glance</div>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-number count-up" data-target="5">0</div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div class="stat-card">
        <div class="stat-number count-up" data-target="15">0</div>
        <div class="stat-label">Technologies</div>
      </div>
      <div class="stat-card">
        <div class="stat-number" style="font-size:32px;">∞</div>
        <div class="stat-label">Lines of Coffee</div>
      </div>
    </div>
  </section>

  <!-- ── TECH STACK ── -->
  <section class="tech-section">
    <div class="section-label">Tech Stack</div>
    <div class="tech-categories">
      <div class="tech-cat cat-backend">
        <div class="cat-title">⬡ Backend</div>
        <div class="tech-pills">
          <span class="pill">C#</span>
          <span class="pill">.NET Core</span>
          <span class="pill">ASP.NET MVC</span>
          <span class="pill">Web API</span>
          <span class="pill">Node.js</span>
          <span class="pill">PHP</span>
          <span class="pill">Python</span>
        </div>
      </div>
      <div class="tech-cat cat-frontend">
        <div class="cat-title">◈ Frontend</div>
        <div class="tech-pills">
          <span class="pill">React</span>
          <span class="pill">Next.js</span>
          <span class="pill">Angular</span>
          <span class="pill">TypeScript</span>
          <span class="pill">HTML5</span>
          <span class="pill">CSS3</span>
          <span class="pill">Bootstrap</span>
          <span class="pill">Chart.js</span>
        </div>
      </div>
      <div class="tech-cat cat-mobile">
        <div class="cat-title">◎ Mobile</div>
        <div class="tech-pills">
          <span class="pill">React Native</span>
          <span class="pill">Socket.io</span>
          <span class="pill">REST APIs</span>
        </div>
      </div>
      <div class="tech-cat cat-cloud">
        <div class="cat-title">◌ Cloud & Infra</div>
        <div class="tech-pills">
          <span class="pill">Azure</span>
          <span class="pill">AWS</span>
          <span class="pill">Microservices</span>
          <span class="pill">Apache</span>
        </div>
      </div>
      <div class="tech-cat cat-db">
        <div class="cat-title">◧ Databases</div>
        <div class="tech-pills">
          <span class="pill">SQL Server</span>
          <span class="pill">MySQL</span>
          <span class="pill">Entity Framework</span>
        </div>
      </div>
      <div class="tech-cat cat-tools">
        <div class="cat-title">⬢ Tools</div>
        <div class="tech-pills">
          <span class="pill">GitHub</span>
          <span class="pill">Swagger</span>
          <span class="pill">Postman</span>
          <span class="pill">Docker</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ── GITHUB STATS ── -->
  <section class="github-section">
    <div class="section-label">GitHub Activity</div>
    <div class="github-cards">
      <div class="github-img-wrap">
        <img src="https://github-readme-stats.vercel.app/api?username=Ismailsirsikar&theme=tokyonight&hide_border=true&include_all_commits=false&count_private=false&bg_color=0d0d14&title_color=7b5cf0&text_color=e8e8f0&icon_color=00e5ff" alt="GitHub Stats" loading="lazy"/>
      </div>
      <div class="github-img-wrap">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Ismailsirsikar&theme=tokyonight&hide_border=true&include_all_commits=false&count_private=false&layout=compact&bg_color=0d0d14&title_color=7b5cf0&text_color=e8e8f0" alt="Top Languages" loading="lazy"/>
      </div>
      <div class="github-img-wrap github-card-wide">
        <img src="https://nirzak-streak-stats.vercel.app/?user=Ismailsirsikar&theme=tokyonight&hide_border=true&background=0d0d14&stroke=7b5cf0&ring=00e5ff&fire=ff4d8d&currStreakLabel=e8e8f0&sideLabels=e8e8f0&dates=6a6a8a&sideNums=7b5cf0&currStreakNum=00e5ff" alt="Streak Stats" loading="lazy"/>
      </div>
    </div>
  </section>

  <!-- ── SOCIALS ── -->
  <section class="socials-section">
    <div class="section-label">Connect</div>
    <div class="socials-row">
      <a class="social-link" href="https://linkedin.com/in/Ismailsirsikar" target="_blank">
        <span class="social-icon">in</span>
        <span>LinkedIn</span>
      </a>
      <a class="social-link" href="https://facebook.com/Ismailsirsikar" target="_blank">
        <span class="social-icon">f</span>
        <span>Facebook</span>
      </a>
      <a class="social-link" href="https://instagram.com/Sirsikarismail" target="_blank">
        <span class="social-icon">ig</span>
        <span>Instagram</span>
      </a>
      <a class="social-link" href="mailto:ismailsirsikar7@gmail.com" target="_blank">
        <span class="social-icon">✉</span>
        <span>ismailsirsikar7@gmail.com</span>
      </a>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ── FOOTER ── -->
  <footer>
    <p class="footer-text">
      crafted with <em>precision</em> · powered by <em>caffeine</em> · driven by <em>clean code</em>
    </p>
    <div class="visitor-badge">
      <span>PROFILE VIEWS</span>
      <img src="https://visitcount.itsvg.in/api?id=Ismailsirsikar&icon=0&color=7" alt="visitor count" height="16" style="border-radius:4px;"/>
    </div>
  </footer>

</div>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  (function animate() {
    cursor.style.left = (mx - 5) + 'px';
    cursor.style.top  = (my - 5) + 'px';
    rx += (mx - rx - 18) * 0.12;
    ry += (my - ry - 18) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top  = ry + 'px';
    requestAnimationFrame(animate);
  })();

  // Count-up animation
  document.querySelectorAll('.count-up').forEach(el => {
    const target = +el.dataset.target;
    let start = null;
    const duration = 1800;
    const obs = new IntersectionObserver(entries => {
      if (!entries[0].isIntersecting) return;
      obs.disconnect();
      function step(ts) {
        if (!start) start = ts;
        const progress = Math.min((ts - start) / duration, 1);
        const ease = 1 - Math.pow(1 - progress, 3);
        el.textContent = Math.floor(ease * target) + '+';
        if (progress < 1) requestAnimationFrame(step);
        else el.textContent = target + '+';
      }
      requestAnimationFrame(step);
    }, { threshold: 0.5 });
    obs.observe(el);
  });
</script>
</body>
</html>
