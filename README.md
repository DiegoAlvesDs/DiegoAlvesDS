<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#07040e">
  <title>Diego Alves — System Online</title>
  <style>
    :root { --cyan:#00f5ff; --pink:#ff007a; --yellow:#f7e600; --ink:#07040e; --panel:rgba(18,8,31,.78); --line:rgba(0,245,255,.3); --text:#f7f1ff; --muted:#b9aac7; }
    * { box-sizing:border-box; }
    html { scroll-behavior:smooth; }
    body { margin:0; color:var(--text); background:var(--ink); font-family:Inter,Segoe UI,Arial,sans-serif; overflow-x:hidden; }
    #city { position:fixed; inset:0; width:100%; height:100%; opacity:.42; z-index:-2; }
    .noise { position:fixed; inset:0; pointer-events:none; z-index:3; opacity:.04; background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.95' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.6'/%3E%3C/svg%3E"); }
    .wrap { width:min(1120px,calc(100% - 40px)); margin:auto; }
    nav { display:flex; justify-content:space-between; align-items:center; padding:22px 0; border-bottom:1px solid var(--line); font:700 12px/1 "Courier New",monospace; letter-spacing:.13em; }
    nav a { color:var(--cyan); text-decoration:none; } .status { color:var(--yellow); }
    header { min-height:76vh; display:grid; align-items:center; padding:54px 0 80px; }
    .eyebrow { color:var(--cyan); font:700 13px "Courier New",monospace; letter-spacing:.18em; }
    h1 { margin:16px 0; max-width:850px; font-size:clamp(50px,10vw,112px); line-height:.87; letter-spacing:-.065em; text-transform:uppercase; text-shadow:4px 0 var(--pink),-2px 0 var(--cyan); }
    h1 span { color:var(--cyan); } .lead { max-width:620px; color:var(--muted); font-size:clamp(17px,2.3vw,21px); line-height:1.65; }
    .actions { display:flex; gap:12px; flex-wrap:wrap; margin-top:30px; }
    .btn { padding:14px 19px; border:1px solid var(--cyan); color:var(--cyan); background:rgba(0,245,255,.06); text-decoration:none; font:700 12px "Courier New",monospace; letter-spacing:.08em; transition:.2s; }
    .btn:hover { color:var(--ink); background:var(--cyan); box-shadow:0 0 28px var(--cyan); transform:translateY(-2px); }
    .btn.pink { border-color:var(--pink); color:var(--pink); background:rgba(255,0,122,.08); } .btn.pink:hover { color:white; background:var(--pink); box-shadow:0 0 28px var(--pink); }
    section { padding:82px 0; border-top:1px solid var(--line); }
    .label { color:var(--pink); font:700 12px "Courier New",monospace; letter-spacing:.14em; } h2 { font-size:clamp(31px,5vw,56px); margin:10px 0 30px; letter-spacing:-.045em; }
    .grid { display:grid; grid-template-columns:repeat(12,1fr); gap:16px; }
    .card { grid-column:span 4; min-height:190px; padding:24px; border:1px solid rgba(255,255,255,.14); background:linear-gradient(145deg,rgba(30,12,50,.82),var(--panel)); position:relative; overflow:hidden; }
    .card:before { content:""; position:absolute; top:0; left:0; height:2px; width:100%; background:linear-gradient(90deg,var(--cyan),var(--pink)); }
    .card h3 { margin:11px 0 10px; font-size:21px; } .card p { margin:0; color:var(--muted); line-height:1.55; }
    .code { color:var(--cyan); font:700 11px "Courier New",monospace; letter-spacing:.1em; }
    .project { grid-column:span 6; padding:30px; border:1px solid var(--line); background:rgba(8,4,17,.7); min-height:305px; display:flex; flex-direction:column; }
    .project:nth-child(2) { border-color:rgba(255,0,122,.4); } .project h3 { font-size:31px; margin:15px 0 12px; } .project p { color:var(--muted); line-height:1.65; max-width:460px; }
    .tags { margin-top:auto; display:flex; flex-wrap:wrap; gap:8px; } .tag { border:1px solid rgba(247,241,255,.23); padding:6px 8px; color:#ded0ef; font:11px "Courier New",monospace; }
    .meter { display:grid; grid-template-columns:160px 1fr 48px; gap:14px; align-items:center; padding:14px 0; border-bottom:1px solid rgba(255,255,255,.1); font:700 13px "Courier New",monospace; }
    .bar { height:8px; background:#21132e; overflow:hidden; } .bar i { display:block; height:100%; background:linear-gradient(90deg,var(--cyan),var(--pink)); box-shadow:0 0 15px var(--cyan); }
    .terminal { background:#050208; border:1px solid var(--pink); padding:22px; color:#d9c8eb; font:15px/1.75 "Courier New",monospace; box-shadow:0 0 42px rgba(255,0,122,.08); } .terminal b { color:var(--cyan); } .terminal em { color:var(--yellow); font-style:normal; }
    footer { padding:45px 0 60px; text-align:center; color:var(--muted); font:12px "Courier New",monospace; border-top:1px solid var(--line); }
    @media(max-width:720px) { .card,.project { grid-column:span 12; } .meter { grid-template-columns:1fr 42px; } .meter .bar { grid-row:2; grid-column:span 2; } nav { font-size:10px; } }
  </style>
</head>
<body>
  <canvas id="city"></canvas><div class="noise"></div>
  <div class="wrap">
    <nav><span>DA//NET_2077</span><span class="status">● SYSTEM ONLINE</span><a href="https://github.com/DiegoAlvesDs">GITHUB ↗</a></nav>
    <header>
      <div>
        <div class="eyebrow">// DEVELOPER IN PROGRESS · BRAZIL</div>
        <h1>DIEGO<br><span>ALVES</span></h1>
        <p class="lead">Transformando curiosidade em código, ideias em experiências e projetos em próximos níveis.</p>
        <div class="actions"><a class="btn" href="https://github.com/DiegoAlvesDs?tab=repositories">[ ACCESS PROJECTS ]</a><a class="btn pink" href="#archive">[ EXPLORE ARCHIVE ]</a></div>
      </div>
    </header>
    <section>
      <div class="label">// IDENTITY PACKET</div><h2>Construindo em público.<br>Aprendendo sem pausa.</h2>
      <div class="grid">
        <article class="card"><div class="code">NODE_01</div><h3>Web</h3><p>Interfaces responsivas e experiências que nascem direto no navegador.</p></article>
        <article class="card"><div class="code">NODE_02</div><h3>Games</h3><p>Lógica, interação e sistemas que transformam uma ideia em jogo.</p></article>
        <article class="card"><div class="code">NODE_03</div><h3>Python</h3><p>Uma base sólida para aprender, criar e compartilhar conhecimento.</p></article>
      </div>
    </section>
    <section id="archive">
      <div class="label">// PROJECT ARCHIVE</div><h2>Experiências em construção.</h2>
      <div class="grid">
        <article class="project"><div class="code">PROJECT_001 · PLAYABLE</div><h3>🐍 Python Snake</h3><p>O clássico Snake, reimaginado como uma experiência web com desafio, evolução e personalidade.</p><div class="tags"><span class="tag">JAVASCRIPT</span><span class="tag">HTML</span><span class="tag">CSS</span><span class="tag">CANVAS</span></div></article>
        <article class="project"><div class="code">PROJECT_002 · LEARNING</div><h3>📚 Curso de Python</h3><p>Um curso autoral pensado para tornar programação simples, prática e possível para quem está começando.</p><div class="tags"><span class="tag">HTML</span><span class="tag">CSS</span><span class="tag">EDUCATION</span></div></article>
      </div>
    </section>
    <section>
      <div class="label">// SKILL MATRIX</div><h2>Carregando novos poderes.</h2>
      <div class="meter"><span>PYTHON</span><div class="bar"><i style="width:80%"></i></div><span>80%</span></div>
      <div class="meter"><span>HTML / CSS</span><div class="bar"><i style="width:85%"></i></div><span>85%</span></div>
      <div class="meter"><span>JAVASCRIPT</span><div class="bar"><i style="width:65%"></i></div><span>65%</span></div>
      <div class="meter"><span>GAME LOGIC</span><div class="bar"><i style="width:60%"></i></div><span>60%</span></div>
    </section>
    <section>
      <div class="label">// CURRENT MISSION</div><h2>Não preciso saber tudo.<br>Preciso continuar.</h2>
      <div class="terminal"><b>diego@build-station:~$</b> status<br><em>MISSION:</em> explorar, criar e evoluir projetos reais<br><em>NEXT_UPGRADE:</em> framework web + projeto full-stack<br><em>SIGNAL:</em> forte, constante, em construção<span id="cursor">_</span></div>
    </section>
  </div>
  <footer>© DIEGO ALVES // BUILT WITH CURIOSITY, CODE &amp; NEON</footer>
  <script>
    const c=document.getElementById('city'),x=c.getContext('2d');
    function draw(){c.width=innerWidth;c.height=innerHeight;const w=c.width,h=c.height; x.fillStyle='#07040e';x.fillRect(0,0,w,h); for(let i=0;i<110;i++){const sx=Math.random()*w,sy=Math.random()*h*.72,r=Math.random()*1.5;x.fillStyle=i%3?'#00f5ff':'#ff007a';x.globalAlpha=Math.random()*.8;x.fillRect(sx,sy,r,r)} x.globalAlpha=1; let px=0;while(px<w){const bw=35+Math.random()*100,bh=60+Math.random()*Math.min(330,h*.38),by=h-bh;let g=x.createLinearGradient(px,by,px,h);g.addColorStop(0,'#1a0930');g.addColorStop(1,'#050208');x.fillStyle=g;x.fillRect(px,by,bw,bh);for(let yy=by+14;yy<h-12;yy+=18)for(let xx=px+10;xx<px+bw-8;xx+=17)if(Math.random()>.45){x.fillStyle=Math.random()>.45?'rgba(0,245,255,.45)':'rgba(255,0,122,.42)';x.fillRect(xx,yy,4,6)}px+=bw+4} let g=x.createLinearGradient(0,h*.65,0,h);g.addColorStop(0,'transparent');g.addColorStop(1,'rgba(255,0,122,.12)');x.fillStyle=g;x.fillRect(0,h*.65,w,h*.35)}
    draw(); addEventListener('resize',draw); setInterval(()=>document.getElementById('cursor').style.opacity=document.getElementById('cursor').style.opacity==='0'?'1':'0',530);
  </script>
</body>
</html>
