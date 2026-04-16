```aura 
<div style={{
  width: '100%', height: '100%',
  background: '#0a0c0f',
  display: 'flex',
  flexDirection: 'column',
  fontFamily: "'Courier New', monospace",
  overflow: 'hidden',
  position: 'relative',
  borderRadius: 12,
  border: '1px solid #1e2d3d',
}}>
  <style>{`
    @keyframes blink { 0%,50%{opacity:1} 51%,100%{opacity:0} }
    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }
    @keyframes glitch {
      0%,89%,100%{opacity:0;transform:translate(0,0)}
      90%{opacity:0.85;transform:translate(-3px,0)}
      92%{opacity:0.6;transform:translate(3px,0)}
      94%{opacity:0.8;transform:translate(-2px,1px)}
      96%{opacity:0}
    }
    @keyframes glitch2 {
      0%,91%,100%{opacity:0;transform:translate(0,0)}
      92%{opacity:0.6;transform:translate(4px,1px)}
      94%{opacity:0.4;transform:translate(-4px,-1px)}
      96%{opacity:0}
    }
    @keyframes rain-fall {
      0%   { transform: translateY(-80px); opacity: 0; }
      10%  { opacity: 1; }
      85%  { opacity: 1; }
      100% { transform: translateY(640px); opacity: 0; }
    }
    #cursor  { animation: blink 0.8s step-end infinite; }
    #dot-g   { animation: pulse 2s ease-in-out infinite; }
    #glitch1 { animation: glitch 6s infinite; }
    #glitch2 { animation: glitch2 6s infinite; }
    .rc0{animation:rain-fall 3.2s linear -0.0s infinite}
    .rc1{animation:rain-fall 2.5s linear -0.6s infinite}
    .rc2{animation:rain-fall 3.9s linear -1.2s infinite}
    .rc3{animation:rain-fall 2.8s linear -0.4s infinite}
    .rc4{animation:rain-fall 3.5s linear -1.8s infinite}
    .rc5{animation:rain-fall 2.6s linear -0.9s infinite}
    .rc6{animation:rain-fall 4.1s linear -0.3s infinite}
    .rc7{animation:rain-fall 3.0s linear -1.5s infinite}
    .rc8{animation:rain-fall 2.7s linear -2.1s infinite}
    .rc9{animation:rain-fall 3.7s linear -0.7s infinite}
    .rc10{animation:rain-fall 2.9s linear -1.1s infinite}
    .rc11{animation:rain-fall 3.4s linear -0.5s infinite}
    .rc12{animation:rain-fall 2.5s linear -2.4s infinite}
    .rc13{animation:rain-fall 4.0s linear -1.0s infinite}
    .rc14{animation:rain-fall 3.1s linear -1.7s infinite}
    .rc15{animation:rain-fall 2.6s linear -0.2s infinite}
    .rc16{animation:rain-fall 3.8s linear -1.3s infinite}
    .rc17{animation:rain-fall 2.4s linear -2.0s infinite}
    .rc18{animation:rain-fall 3.3s linear -0.8s infinite}
    .rc19{animation:rain-fall 4.2s linear -1.6s infinite}
    .rc20{animation:rain-fall 2.8s linear -0.1s infinite}
    .rc21{animation:rain-fall 3.6s linear -1.9s infinite}
    .rc22{animation:rain-fall 2.5s linear -2.3s infinite}
    .rc23{animation:rain-fall 3.0s linear -0.6s infinite}
    .rc24{animation:rain-fall 3.9s linear -1.4s infinite}
    .rc25{animation:rain-fall 2.7s linear -1.0s infinite}
  `}</style>

  {/* Full-canvas SVG — matrix rain + ALL animated elements */}
  <svg width="860" height="620" style={{ position: 'absolute', top: 0, left: 0, pointerEvents: 'none' }}
    xmlns="http://www.w3.org/2000/svg">

    {/* Matrix rain columns — rect-based, no <text> */}
    {[
      {x:30,  cls:'rc0',  op:0.13},{x:62,  cls:'rc1',  op:0.17},{x:94,  cls:'rc2',  op:0.11},
      {x:126, cls:'rc3',  op:0.15},{x:158, cls:'rc4',  op:0.12},{x:190, cls:'rc5',  op:0.18},
      {x:222, cls:'rc6',  op:0.10},{x:254, cls:'rc7',  op:0.16},{x:286, cls:'rc8',  op:0.13},
      {x:318, cls:'rc9',  op:0.14},{x:350, cls:'rc10', op:0.11},{x:382, cls:'rc11', op:0.17},
      {x:414, cls:'rc12', op:0.12},{x:446, cls:'rc13', op:0.15},{x:478, cls:'rc14', op:0.10},
      {x:510, cls:'rc15', op:0.16},{x:542, cls:'rc16', op:0.13},{x:574, cls:'rc17', op:0.18},
      {x:606, cls:'rc18', op:0.11},{x:638, cls:'rc19', op:0.14},{x:670, cls:'rc20', op:0.12},
      {x:702, cls:'rc21', op:0.17},{x:734, cls:'rc22', op:0.10},{x:766, cls:'rc23', op:0.15},
      {x:798, cls:'rc24', op:0.13},{x:830, cls:'rc25', op:0.16},
    ].map(function(col) {
      return (
        <g key={col.x} className={col.cls} style={{ opacity: col.op }}>
          {[0,1,2,3,4].map(function(i) {
            return (
              <rect key={i} x={col.x - 3} y={10 + i * 18}
                width={i === 4 ? 8 : 5} height={i === 4 ? 8 : 3} rx="1"
                fill={i === 4 ? '#afffdf' : '#00ff9d'} opacity={1 - i * 0.15} />
            )
          })}
        </g>
      )
    })}

    {/* Pulsing green dot (top-left traffic light) */}
    <circle id="dot-g" cx="48" cy="40" r="4" fill="#00ff9d" />

    {/* Glitch layers — colored rect slices behind the name text */}
    <g id="glitch1" style={{ opacity: 0 }}>
      <rect x="28" y="78" width="200" height="14" fill="#00bfff" opacity="0.75" />
      <rect x="28" y="96" width="170" height="10" fill="#00bfff" opacity="0.55" />
      <rect x="28" y="110" width="190" height="8"  fill="#00bfff" opacity="0.4" />
    </g>
    <g id="glitch2" style={{ opacity: 0 }}>
      <rect x="31" y="80" width="180" height="12" fill="#ff003c" opacity="0.65" />
      <rect x="28" y="98" width="150" height="9"  fill="#ff003c" opacity="0.45" />
    </g>

    {/* Blinking cursor — positioned at the terminal prompt line */}
    <rect id="cursor" x="258" y="337" width="8" height="13" fill="#00ff9d" />

  </svg>

  {/* Main content layer */}
  <div style={{
    position: 'absolute', top: 0, left: 0, right: 0, bottom: 0,
    display: 'flex', flexDirection: 'column',
  }}>

    {/* Header */}
    <div style={{
      padding: '20px 28px 14px', borderBottom: '1px solid #1e2d3d',
      display: 'flex', flexDirection: 'column',
      background: 'rgba(10,12,15,0.88)',
    }}>
      {/* Traffic lights — dot-g is now in SVG, these two are static */}
      <div style={{ display: 'flex', alignItems: 'center', gap: 7, marginBottom: 10 }}>
        <div style={{ width: 8, height: 8, borderRadius: '50%', background: '#00ff9d' }} />
        <div style={{ width: 8, height: 8, borderRadius: '50%', background: '#ffd700' }} />
        <div style={{ width: 8, height: 8, borderRadius: '50%', background: '#ff003c' }} />
        <span style={{ marginLeft: 8, fontSize: 10, color: '#4a6070', letterSpacing: 2 }}>SYSTEM_ONLINE · NODE: GITHUB/NUll-O7</span>
      </div>

      <div style={{ display: 'flex', marginBottom: 3 }}>
        <span style={{ fontSize: 10, color: '#4a6070', letterSpacing: 2 }}>
          <span style={{ color: '#00ff9d' }}>// </span>IDENTIFIER
        </span>
      </div>

      {/* Name — glitch layers are SVG rects behind this, positioned by coordinates */}
      <div style={{ display: 'flex', position: 'relative' }}>
        <span style={{ fontFamily: 'monospace', fontSize: 42, fontWeight: 900, color: '#00ff9d', letterSpacing: 5, lineHeight: 1 }}>NUll-O7</span>
      </div>

      <div style={{ display: 'flex', gap: 8, marginTop: 8, flexWrap: 'wrap' }}>
        {[
          { label: 'CS UNDERGRAD', color: '#00bfff' },
          { label: 'FULL-STACK',   color: '#00ff9d' },
          { label: 'AI / ML',      color: '#ff003c' },
        ].map(function(b) {
          return (
            <span key={b.label} style={{ fontSize: 10, padding: '3px 10px', border: '1px solid ' + b.color, color: b.color, letterSpacing: 1.5, display: 'flex' }}>{b.label}</span>
          )
        })}
      </div>

      <div style={{ marginTop: 10, fontSize: 11, color: '#4a6070', borderLeft: '2px solid #ff003c', paddingLeft: 12, display: 'flex' }}>
        <span style={{ color: '#ff003c' }}>HTTP 402 —&nbsp;</span>
        <span>Payment Required: currently blocked by a paywall called "rent"</span>
      </div>
    </div>

    {/* Terminal block */}
    <div style={{ padding: '14px 28px', borderBottom: '1px solid #1e2d3d', background: 'rgba(10,12,15,0.88)', display: 'flex' }}>
      <div style={{ background: '#0f1217', border: '1px solid #1e2d3d', display: 'flex', flexDirection: 'column' }}>
        <div style={{ background: '#131820', padding: '6px 14px', borderBottom: '1px solid #1e2d3d', display: 'flex', alignItems: 'center', gap: 6 }}>
          <div style={{ display: 'flex', gap: 5 }}>
            {['#ff5f56','#ffbd2e','#27c93f'].map(function(c, i) {
              return <div key={i} style={{ width: 9, height: 9, borderRadius: '50%', background: c }} />
            })}
          </div>
          <span style={{ fontSize: 10, color: '#4a6070', marginLeft: 8 }}>null07@dev ~ bash</span>
        </div>
        <div style={{ padding: '12px 18px', fontSize: 12, lineHeight: 1.85, display: 'flex', flexDirection: 'column' }}>
          {[
            [{ c:'#00ff9d', t:'> ' }, { c:'#00bfff', t:'cat ' }, { c:'#c8d8e8', t:'profile.json' }],
            [{ c:'#4a6070', t:'  // loading identity matrix...' }],
            [{ c:'#c8d8e8', t:'  ' }, { c:'#ffd700', t:'"name"' }, { c:'#c8d8e8', t:': ' }, { c:'#ffd700', t:'"NUll-O7",' }],
            [{ c:'#c8d8e8', t:'  ' }, { c:'#ffd700', t:'"status"' }, { c:'#c8d8e8', t:': ' }, { c:'#ffd700', t:'"B.Sc. CS · Active",' }],
            [{ c:'#c8d8e8', t:'  ' }, { c:'#ffd700', t:'"experience"' }, { c:'#c8d8e8', t:': ' }, { c:'#ff9d6c', t:'6' }, { c:'#c8d8e8', t:' years,' }],
            [{ c:'#c8d8e8', t:'  ' }, { c:'#ffd700', t:'"CodeChef"' }, { c:'#c8d8e8', t:': ' }, { c:'#ffd700', t:'"3 star"' }, { c:'#c8d8e8', t:', ' }, { c:'#ffd700', t:'"Codeforces"' }, { c:'#c8d8e8', t:': ' }, { c:'#ffd700', t:'"Expert"' }],
          ].map(function(row, ri) {
            return (
              <div key={ri} style={{ display: 'flex' }}>
                {row.map(function(seg, si) {
                  return <span key={si} style={{ color: seg.c }}>{seg.t}</span>
                })}
              </div>
            )
          })}
          {/* Cursor row — the SVG rect cursor overlaps this prompt visually */}
          <div style={{ display: 'flex', alignItems: 'center', marginTop: 2 }}>
            <span style={{ color: '#00ff9d' }}>{'> '}</span>
          </div>
        </div>
      </div>
    </div>

    {/* Stats row */}
    <div style={{ display: 'flex', borderBottom: '1px solid #1e2d3d', background: 'rgba(10,12,15,0.92)' }}>
      {[
        { val: '6+',     label: 'YEARS CODING', color: '#00ff9d' },
        { val: '3 STAR', label: 'CODECHEF',      color: '#00bfff' },
        { val: 'EXPERT', label: 'CODEFORCES',    color: '#a855f7' },
        { val: 'inf',    label: 'CAFFEINE DEBT', color: '#ff003c' },
      ].map(function(s, i) {
        return (
          <div key={i} style={{ flex: 1, padding: '12px', display: 'flex', flexDirection: 'column', alignItems: 'center', borderRight: i < 3 ? '1px solid #1e2d3d' : 'none' }}>
            <span style={{ fontSize: 18, fontWeight: 700, color: s.color, letterSpacing: 2 }}>{s.val}</span>
            <span style={{ fontSize: 9, color: '#4a6070', letterSpacing: 1.5, marginTop: 3 }}>{s.label}</span>
          </div>
        )
      })}
    </div>

    {/* Tech stack */}
    <div style={{ padding: '14px 28px', borderBottom: '1px solid #1e2d3d', display: 'flex', flexDirection: 'column', background: 'rgba(10,12,15,0.88)' }}>
      <div style={{ fontSize: 10, color: '#4a6070', letterSpacing: 3, marginBottom: 12, display: 'flex' }}>TECH STACK</div>
      <div style={{ display: 'flex', gap: 10 }}>
        {[
          { label: '// Frontend',        color: '#00bfff', tags: ['React','Next.js','TypeScript','React Native','Flutter','Electron','Tailwind','Three.js','GSAP'] },
          { label: '// Backend & Infra',  color: '#a855f7', tags: ['Python','Java','Spring Boot','Express.js','PostgreSQL','NoSQL','GitHub Actions','CI/CD'] },
          { label: '// AI / ML',          color: '#ff003c', tags: ['PyTorch','HuggingFace','OpenCV','LangGraph','Pydantic AI','LLM Agents'] },
        ].map(function(group, gi) {
          return (
            <div key={gi} style={{ flex: 1, background: 'rgba(15,18,23,0.95)', border: '1px solid #1e2d3d', borderTop: '2px solid ' + group.color, padding: '10px 10px 8px', display: 'flex', flexDirection: 'column' }}>
              <div style={{ fontSize: 10, color: group.color, letterSpacing: 1.5, marginBottom: 7, fontWeight: 700 }}>{group.label}</div>
              <div style={{ display: 'flex', flexWrap: 'wrap', gap: 4 }}>
                {group.tags.map(function(tag, ti) {
                  return <span key={ti} style={{ fontSize: 10, padding: '2px 7px', background: '#1a2030', color: '#c8d8e8', border: '1px solid #1e2d3d', letterSpacing: 0.5, display: 'flex' }}>{tag}</span>
                })}
              </div>
            </div>
          )
        })}
      </div>
    </div>

    {/* About */}
    <div style={{ padding: '14px 28px 16px', display: 'flex', flexDirection: 'column', background: 'rgba(10,12,15,0.88)' }}>
      <div style={{ fontSize: 10, color: '#4a6070', letterSpacing: 3, marginBottom: 10, display: 'flex' }}>ABOUT.md</div>
      <div style={{ borderLeft: '2px solid #1a2030', paddingLeft: 14, display: 'flex', flexDirection: 'column', gap: 4 }}>
        {[
          ['Engineer with ', '#00ff9d', '6 years', ' in the field — I don\'t just write code, I architect systems that ship.'],
          ['Problem-solving is my native language. ', '#00bfff', 'Logical analysis', ' is my superpower.'],
          ['Built and shipped ', '#00bfff', 'production-grade full-stack apps', ' — clean patterns, efficient microservices, zero to deployed in weeks.'],
          ['', '#ffd700', '3-Star CodeChef · Expert on Codeforces', ' — competitive programming is the gym my brain never skips.'],
          ['Current obsession: ', '#00ff9d', 'multi-model LLM routing', ' and agentic AI workflows that actually work in production.'],
        ].map(function(item, i) {
          return (
            <div key={i} style={{ display: 'flex', alignItems: 'flex-start', gap: 6, fontSize: 11, color: '#90a8bc', lineHeight: 1.65 }}>
              <span style={{ color: '#00ff9d', flexShrink: 0 }}>+</span>
              <div style={{ display: 'flex', flexWrap: 'wrap' }}>
                {item[0] ? <span style={{ color: '#90a8bc' }}>{item[0]}</span> : null}
                <span style={{ color: item[1] }}>{item[2]}</span>
                {item[3] ? <span style={{ color: '#90a8bc' }}>{item[3]}</span> : null}
              </div>
            </div>
          )
        })}
      </div>
    </div>

    {/* Footer */}
    <div style={{ borderTop: '1px solid #1e2d3d', padding: '8px 28px', display: 'flex', justifyContent: 'space-between', alignItems: 'center', background: 'rgba(10,12,15,0.92)' }}>
      <div style={{ display: 'flex', alignItems: 'center', gap: 8 }}>
        <div style={{ width: 6, height: 6, borderRadius: '50%', background: '#00ff9d' }} />
        <span style={{ fontSize: 10, color: '#4a6070' }}>NUll-O7 · GITHUB</span>
      </div>
      <span style={{ fontSize: 10, color: '#4a6070', letterSpacing: 1 }}>OPEN TO COLLAB // LET'S BUILD SOMETHING</span>
    </div>

  </div>
</div>
```

```aura width=860 height=22 link="https://collectioneur.github.io/readme-aura/"
  <div style={{ display: 'flex', justifyContent: 'center', alignItems: 'center', width: '100%', height: '100%', padding: 0, margin: 0 }}>
    <span style={{ fontSize: 12, lineHeight: 1, color: 'rgba(150,140,200,0.55)', fontWeight: 500, letterSpacing: '0.4px' }}>powered by readme-aura</span>
  </div>
```
