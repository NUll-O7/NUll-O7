

```aura width=860 height=200 link="https://collectioneur.github.io/readme-aura/"
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
@import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Space+Mono:wght@400;700&display=swap');

:root {
  --bg: #0a0c0f;
  --bg2: #0f1217;
  --accent: #00ff9d;
  --accent2: #00bfff;
  --accent3: #ff003c;
  --dim: #1a2030;
  --border: #1e2d3d;
  --text: #c8d8e8;
  --muted: #4a6070;
  --mono: 'Share Tech Mono', 'Space Mono', monospace;
  --display: 'Orbitron', monospace;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: var(--bg);
  font-family: var(--mono);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

.card {
  width: 100%;
  max-width: 820px;
  margin: 0 auto;
  padding: 0;
  position: relative;
  background: var(--bg);
}

/* Scanline overlay */
.card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,255,157,0.015) 2px, rgba(0,255,157,0.015) 4px);
  pointer-events: none;
  z-index: 100;
}

/* ---- HEADER ---- */
.header {
  padding: 28px 32px 20px;
  border-bottom: 1px solid var(--border);
  position: relative;
  overflow: hidden;
}

.header-grid {
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: start;
  gap: 16px;
}

.status-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 14px;
  font-size: 11px;
  color: var(--muted);
}

.dot { width: 8px; height: 8px; border-radius: 50%; }
.dot.green { background: #00ff9d; box-shadow: 0 0 6px #00ff9d; animation: pulse 2s ease-in-out infinite; }
.dot.yellow { background: #ffd700; }
.dot.red { background: #ff003c; }

@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.4} }

.name-block { position: relative; }

.name-label {
  font-size: 11px;
  color: var(--muted);
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 4px;
}

.name-label::before { content: '// '; color: var(--accent); }

.name {
  font-family: var(--display);
  font-size: 42px;
  font-weight: 900;
  color: var(--accent);
  letter-spacing: 4px;
  line-height: 1;
  position: relative;
  display: inline-block;
}

.name .glitch-layer {
  position: absolute;
  top: 0; left: 0;
  color: var(--accent2);
  opacity: 0;
  clip-path: inset(0 0 100% 0);
  animation: glitch 6s infinite;
}

.name .glitch-layer2 {
  position: absolute;
  top: 0; left: 0;
  color: var(--accent3);
  opacity: 0;
  clip-path: inset(100% 0 0 0);
  animation: glitch2 6s infinite;
}

@keyframes glitch {
  0%,89%,100% { opacity:0; transform: none; clip-path: inset(0 0 100% 0); }
  90% { opacity:.8; transform: translate(-3px,0); clip-path: inset(20% 0 60% 0); }
  92% { opacity:.6; transform: translate(3px,0); clip-path: inset(60% 0 20% 0); }
  94% { opacity:.8; transform: translate(-2px,0); clip-path: inset(40% 0 40% 0); }
  96% { opacity:0; }
}

@keyframes glitch2 {
  0%,91%,100% { opacity:0; transform: none; }
  92% { opacity:.6; transform: translate(4px,1px); clip-path: inset(50% 0 30% 0); }
  94% { opacity:.4; transform: translate(-4px,-1px); clip-path: inset(30% 0 50% 0); }
  96% { opacity:0; }
}

.title-row {
  margin-top: 8px;
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

.badge {
  font-size: 10px;
  padding: 3px 10px;
  border: 1px solid;
  letter-spacing: 1.5px;
  text-transform: uppercase;
}

.badge.blue { color: var(--accent2); border-color: var(--accent2); }
.badge.green { color: var(--accent); border-color: var(--accent); }
.badge.red { color: var(--accent3); border-color: var(--accent3); }

.tagline {
  margin-top: 14px;
  font-size: 12px;
  color: var(--muted);
  letter-spacing: .5px;
  border-left: 2px solid var(--accent3);
  padding-left: 12px;
  font-style: italic;
}

.tagline span { color: var(--accent3); font-style: normal; }

/* corner decoration */
.corner-tl, .corner-br {
  position: absolute;
  width: 20px; height: 20px;
  pointer-events: none;
}
.corner-tl { top: 12px; right: 28px; border-top: 2px solid var(--accent); border-right: 2px solid var(--accent); }
.corner-br { bottom: 12px; right: 28px; border-bottom: 2px solid var(--muted); border-left: 2px solid var(--muted); }

/* ---- TERMINAL ---- */
.terminal-section {
  padding: 20px 32px;
  border-bottom: 1px solid var(--border);
}

.terminal {
  background: var(--bg2);
  border: 1px solid var(--border);
  border-radius: 4px;
  overflow: hidden;
}

.terminal-bar {
  background: #131820;
  padding: 8px 14px;
  display: flex;
  align-items: center;
  gap: 8px;
  border-bottom: 1px solid var(--border);
}

.terminal-bar .dots { display:flex; gap:5px; }
.terminal-bar .dots span { width:10px; height:10px; border-radius:50%; }
.terminal-bar .dots span:nth-child(1) { background:#ff5f56; }
.terminal-bar .dots span:nth-child(2) { background:#ffbd2e; }
.terminal-bar .dots span:nth-child(3) { background:#27c93f; }
.terminal-bar .title { font-size:11px; color: var(--muted); margin-left: 8px; }

.terminal-body {
  padding: 16px 20px;
  font-size: 12.5px;
  line-height: 1.9;
}

.line { display: flex; gap: 8px; }
.prompt { color: var(--accent); flex-shrink: 0; }
.cmd { color: var(--text); }
.kw { color: var(--accent2); }
.str { color: #ffd700; }
.num { color: #ff9d6c; }
.comment { color: var(--muted); }

.cursor {
  display: inline-block;
  width: 8px; height: 14px;
  background: var(--accent);
  animation: blink .8s step-end infinite;
  vertical-align: -2px;
  margin-left: 2px;
}
@keyframes blink { 0%,50%{ opacity:1 } 51%,100%{ opacity:0 } }

/* ---- SKILLS ---- */
.skills-section {
  padding: 20px 32px;
  border-bottom: 1px solid var(--border);
}

.section-header {
  font-size: 10px;
  color: var(--muted);
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 16px;
  display: flex;
  align-items: center;
  gap: 10px;
}

.section-header::after {
  content: '';
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--border), transparent);
}

.skill-groups {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

.skill-group {
  background: var(--bg2);
  border: 1px solid var(--border);
  border-top: 2px solid;
  padding: 14px 14px 12px;
  border-radius: 2px;
  position: relative;
  transition: border-color .2s;
}

.skill-group:nth-child(1) { border-top-color: var(--accent2); }
.skill-group:nth-child(2) { border-top-color: #a855f7; }
.skill-group:nth-child(3) { border-top-color: var(--accent3); }

.skill-group:hover { background: #141b24; }

.sg-label {
  font-size: 10px;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 10px;
  font-weight: 700;
}

.skill-group:nth-child(1) .sg-label { color: var(--accent2); }
.skill-group:nth-child(2) .sg-label { color: #a855f7; }
.skill-group:nth-child(3) .sg-label { color: var(--accent3); }

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
}

.tag {
  font-size: 10px;
  padding: 2px 8px;
  background: var(--dim);
  color: var(--text);
  border: 1px solid var(--border);
  letter-spacing: .5px;
  cursor: default;
  transition: all .15s;
  white-space: nowrap;
}

.tag:hover { background: var(--border); color: #fff; }

/* ---- STATS ROW ---- */
.stats-section {
  padding: 18px 32px;
  border-bottom: 1px solid var(--border);
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  background: var(--border);
}

.stat {
  background: var(--bg);
  padding: 14px 16px;
  text-align: center;
}

.stat-val {
  font-family: var(--display);
  font-size: 22px;
  font-weight: 700;
  color: var(--accent);
  letter-spacing: 2px;
  display: block;
}

.stat-val.blue { color: var(--accent2); }
.stat-val.purple { color: #a855f7; }
.stat-val.red { color: var(--accent3); }

.stat-key {
  font-size: 10px;
  color: var(--muted);
  letter-spacing: 1.5px;
  text-transform: uppercase;
  margin-top: 3px;
  display: block;
}

/* ---- BIO ---- */
.bio-section {
  padding: 20px 32px 28px;
}

.bio-text {
  font-size: 12px;
  line-height: 1.9;
  color: #90a8bc;
  border-left: 2px solid var(--dim);
  padding-left: 16px;
}

.bio-text .hl { color: var(--accent); }
.bio-text .hl2 { color: var(--accent2); }
.bio-text .hl3 { color: #ffd700; }

.bio-bullets {
  margin-top: 10px;
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 5px;
  font-size: 12px;
  color: #90a8bc;
  border-left: 2px solid var(--dim);
  padding-left: 16px;
}

.bio-bullets li::before {
  content: '▸ ';
  color: var(--accent);
}

/* ---- FOOTER ---- */
.footer {
  border-top: 1px solid var(--border);
  padding: 12px 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 10px;
  color: var(--muted);
}

.footer-left { display: flex; align-items: center; gap: 8px; }
.footer .blip { width: 6px; height: 6px; background: var(--accent); border-radius: 50%; animation: pulse 1.5s ease-in-out infinite; }

/* animated border-scan on hover for skill groups */
@keyframes scan-h {
  0%   { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.skill-group::after {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent 0%, rgba(255,255,255,.4) 50%, transparent 100%);
  transform: translateX(-100%);
  opacity: 0;
  transition: opacity .2s;
}

.skill-group:hover::after {
  opacity: 1;
  animation: scan-h .6s ease-out forwards;
}

/* Responsive */
@media (max-width: 600px) {
  .skill-groups { grid-template-columns: 1fr; }
  .stats-section { grid-template-columns: repeat(2,1fr); }
  .name { font-size: 28px; }
}
</style>
</head>
<body>
<div class="card">

  <!-- HEADER -->
  <div class="header">
    <div class="corner-tl"></div>
    <div class="corner-br"></div>
    <div class="status-bar">
      <div class="dot green"></div>
      <div class="dot yellow"></div>
      <div class="dot red"></div>
      <span style="margin-left:6px">SYSTEM_ONLINE</span>
      <span>•</span>
      <span>NODE: GITHUB/NUll-O7</span>
    </div>
    <div class="header-grid">
      <div class="name-block">
        <div class="name-label">IDENTIFIER</div>
        <div class="name">
          NUll-O7
          <span class="glitch-layer">NUll-O7</span>
          <span class="glitch-layer2">NUll-O7</span>
        </div>
        <div class="title-row">
          <span class="badge blue">CS UNDERGRAD</span>
          <span class="badge green">FULL-STACK</span>
          <span class="badge red">AI/ML</span>
        </div>
        <div class="tagline">
          <span>HTTP 402 —</span> Payment Required: currently blocked by a paywall called "rent"
        </div>
      </div>
    </div>
  </div>

  <!-- TERMINAL -->
  <div class="terminal-section">
    <div class="terminal">
      <div class="terminal-bar">
        <div class="dots"><span></span><span></span><span></span></div>
        <span class="title">null07@dev ~ bash</span>
      </div>
      <div class="terminal-body">
        <div class="line"><span class="prompt">❯</span><span class="cmd"><span class="kw">cat</span> profile.json</span></div>
        <div class="line" style="margin-left:16px"><span class="comment">// loading identity matrix...</span></div>
        <div class="line" style="margin-left:16px; margin-top:4px">
          <span class="str">"name"</span><span class="cmd">: </span><span class="str">"NUll-O7"</span><span class="cmd">,</span>
        </div>
        <div class="line" style="margin-left:16px">
          <span class="str">"status"</span><span class="cmd">: </span><span class="str">"B.Sc. CS · Active"</span><span class="cmd">,</span>
        </div>
        <div class="line" style="margin-left:16px">
          <span class="str">"experience"</span><span class="cmd">: </span><span class="num">6</span><span class="cmd"> years,</span>
        </div>
        <div class="line" style="margin-left:16px">
          <span class="str">"ratings"</span><span class="cmd">: { </span><span class="str">"CodeChef"</span><span class="cmd">: </span><span class="str">"★★★"</span><span class="cmd">, </span><span class="str">"Codeforces"</span><span class="cmd">: </span><span class="str">"Expert"</span><span class="cmd"> }</span>
        </div>
        <div class="line" style="margin-top:8px"><span class="prompt">❯</span><span class="cursor"></span></div>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-section">
    <div class="stat">
      <span class="stat-val">6+</span>
      <span class="stat-key">YEARS CODING</span>
    </div>
    <div class="stat">
      <span class="stat-val blue">★★★</span>
      <span class="stat-key">CODECHEF</span>
    </div>
    <div class="stat">
      <span class="stat-val purple">EXPERT</span>
      <span class="stat-key">CODEFORCES</span>
    </div>
    <div class="stat">
      <span class="stat-val red">∞</span>
      <span class="stat-key">CAFFEINE DEBT</span>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="skills-section">
    <div class="section-header">TECH STACK</div>
    <div class="skill-groups">
      <!-- Frontend -->
      <div class="skill-group">
        <div class="sg-label">// Frontend</div>
        <div class="skill-tags">
          <span class="tag">React</span>
          <span class="tag">Next.js</span>
          <span class="tag">TypeScript</span>
          <span class="tag">JavaScript</span>
          <span class="tag">React Native</span>
          <span class="tag">Flutter</span>
          <span class="tag">Electron</span>
          <span class="tag">HTML/CSS</span>
          <span class="tag">Tailwind</span>
          <span class="tag">shadcn/ui</span>
          <span class="tag">DaisyUI</span>
          <span class="tag">Chakra UI</span>
          <span class="tag">Recharts</span>
          <span class="tag">Three.js</span>
          <span class="tag">R3F</span>
          <span class="tag">GSAP</span>
          <span class="tag">Motion</span>
          <span class="tag">Anime.js</span>
        </div>
      </div>
      <!-- Backend -->
      <div class="skill-group">
        <div class="sg-label">// Backend & Infra</div>
        <div class="skill-tags">
          <span class="tag">Python</span>
          <span class="tag">Java</span>
          <span class="tag">Spring Boot</span>
          <span class="tag">Express.js</span>
          <span class="tag">Node.js</span>
          <span class="tag">PostgreSQL</span>
          <span class="tag">SQL</span>
          <span class="tag">NoSQL</span>
          <span class="tag">REST APIs</span>
          <span class="tag">Microservices</span>
          <span class="tag">Git</span>
          <span class="tag">GitHub</span>
          <span class="tag">GitHub Actions</span>
          <span class="tag">CI/CD</span>
        </div>
      </div>
      <!-- AI/ML -->
      <div class="skill-group">
        <div class="sg-label">// AI / ML</div>
        <div class="skill-tags">
          <span class="tag">PyTorch</span>
          <span class="tag">HuggingFace</span>
          <span class="tag">OpenCV</span>
          <span class="tag">LangGraph</span>
          <span class="tag">Pydantic AI</span>
          <span class="tag">Multi-model Routing</span>
          <span class="tag">LLM Agents</span>
          <span class="tag">Computer Vision</span>
          <span class="tag">Agentic Workflows</span>
        </div>
      </div>
    </div>
  </div>

  <!-- BIO -->
  <div class="bio-section">
    <div class="section-header">ABOUT.md</div>
    <div class="bio-text">
      Engineer with <span class="hl">6 years</span> in the field — I don't just write code, I architect systems that ship.
    </div>
    <ul class="bio-bullets" style="margin-top:10px">
      <li>Problem-solving is my native language. Logical analysis is my superpower.</li>
      <li>Built and shipped multiple <span class="hl2">production-grade full-stack apps</span> from zero to deployed in weeks — clean design patterns, efficient microservices, no shortcuts on architecture.</li>
      <li><span class="hl3">★★★ CodeChef</span> · <span class="hl3">Expert on Codeforces</span> — competitive programming is the gym session my brain never skips.</li>
      <li>Fluent across the stack: from <span class="hl">pixel-perfect UIs</span> to <span class="hl2">distributed backends</span> to <span class="hl">agentic AI pipelines</span>.</li>
      <li>Current obsession: multi-model LLM routing and building AI workflows that actually work in production.</li>
    </ul>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-left">
      <div class="blip"></div>
      <span>NUll-O7 · GITHUB</span>
    </div>
    <span>OPEN TO COLLAB // LET'S BUILD SOMETHING CURSED</span>
  </div>

</div>
</body>
</html>
```

```aura width=860 height=22 link="https://collectioneur.github.io/readme-aura/"
  <div style={{ display: 'flex', justifyContent: 'center', alignItems: 'center', width: '100%', height: '100%', padding: 0, margin: 0 }}>
    <span style={{ fontSize: 12, lineHeight: 1, color: 'rgba(150,140,200,0.55)', fontWeight: 500, letterSpacing: '0.4px' }}>powered by readme-aura</span>
  </div>
```
