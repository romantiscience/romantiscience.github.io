<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Jesse Young — Wireframe Portfolio (typewriter / synth-gadget)</title>

  <!-- Typewriter + mono for UI -->
  <link href="https://fonts.googleapis.com/css2?family=Special+Elite&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">

  <style>
    /* ---------------------------
       A clean white / black-lines UI
       typewriter typography + synth gadget accents
       --------------------------- */
    :root{
      --bg: #f7f7f7;      /* page bg (off-white) */
      --panel: #ffffff;   /* panels */
      --line: #0b0b0b;    /* black line color */
      --muted: #666;
      --accent: #00a6a0;  /* subtle cyan accent */
      --gap: 18px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:20px;
      background:var(--bg);
      font-family: "Space Mono", monospace;
      color:var(--line);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:center;
      justify-content:center;
    }

    .shell{
      width: min(1180px,96vw);
      background:linear-gradient(180deg, var(--panel), #fbfbfb);
      border: 2px solid var(--line);
      border-radius: 10px;
      padding: 18px;
      box-shadow: 0 10px 30px rgba(11,11,11,0.04);
    }

    header{
      display:flex;
      align-items:flex-end;
      gap:var(--gap);
      margin-bottom:12px;
    }

    /* big typewriter title (left) */
    .title {
      font-family: "Special Elite", "Space Mono", monospace;
      font-size: clamp(28px, 5.2vw, 48px);
      color:var(--line);
      letter-spacing:1px;
      margin:0;
      padding-right:18px;
      border-right:2px solid rgba(11,11,11,0.06);
    }

    /* tidy tabs area (right) */
    nav {
      margin-left:auto;
      display:flex;
      gap:10px;
      align-items:center;
      padding-left:18px;
    }
    .tab {
      background:transparent;
      border: 2px solid var(--line);
      color:var(--line);
      padding:8px 12px;
      border-radius:8px;
      cursor:pointer;
      font-size:13px;
      transition: all 180ms ease;
      min-width:78px;
      text-align:center;
    }
    .tab.active{
      background:var(--line);
      color:var(--panel);
      box-shadow: 0 6px 0 rgba(0,0,0,0.04) inset;
    }

    main{
      display:flex;
      gap:18px;
      align-items:stretch;
      min-height:60vh;
    }

    /* Content (left) should take most of the width */
    .content{
      flex: 2.2;                 /* larger than graphics */
      background:var(--panel);
      border:2px solid rgba(11,11,11,0.04);
      border-radius:10px;
      padding:20px;
      overflow:auto;
      box-shadow: 0 6px 18px rgba(11,11,11,0.03);
      min-width:420px;
    }
    .content h2{ font-family:"Space Mono"; margin-top:0; color:var(--line); }
    .meta {
      display:flex;
      gap:10px;
      align-items:center;
      color:var(--muted);
      font-size:13px;
      margin-bottom:12px;
    }

    /* Graphics column smaller and centered */
    .graphics {
      flex: 1;                 /* smaller than content */
      min-width:360px;
      max-width:480px;
      background:var(--panel);
      border:2px solid rgba(11,11,11,0.04);
      border-radius:10px;
      display:flex;
      align-items:center;
      justify-content:center;
      position:relative;
      padding:14px;
      box-shadow: 0 6px 18px rgba(11,11,11,0.03);
    }

    /* center canvas inside and control size */
    .render-wrap {
      width: 92%;
      height: calc(100% - 10px);
      display:flex;
      align-items:center;
      justify-content:center;
      background:linear-gradient(180deg, #ffffff, #fbfbfb);
      border: 1px dashed rgba(11,11,11,0.03);
      border-radius:8px;
      position:relative;
    }

    canvas { display:block; width: 86%; height: 86%; max-width:720px; max-height:560px; }

    /* small synth-esque knobs for visual flavor (pure CSS) */
    .knobs {
      position:absolute;
      right:12px;
      bottom:12px;
      display:flex;
      gap:10px;
      align-items:center;
    }
    .knob{
      width:34px;height:34px;border-radius:6px;border:2px solid var(--line);display:flex;align-items:center;justify-content:center;font-size:12px;color:var(--line);
      background:linear-gradient(180deg,#fff,#f1f1f1);
      box-shadow: 0 1px 0 rgba(0,0,0,0.03);
    }

    footer{
      margin-top:12px;
      display:flex;
      justify-content:space-between;
      color:var(--muted);
      font-size:13px;
      padding-top:10px;
    }

    /* responsive */
    @media (max-width:980px){
      main{flex-direction:column}
      .graphics{width:100%;min-width:unset;max-width:none}
      canvas{width:96%;height:260px;max-height:none}
    }
  </style>
</head>
<body>
  <div class="shell">
    <header>
      <h1 class="title">JESSE YOUNG</h1>
      <nav role="tablist" aria-label="Primary tabs">
        <button class="tab active" data-tab="bio">BIO</button>
        <button class="tab" data-tab="design">DESIGN</button>
        <button class="tab" data-tab="text">TEXT</button>
        <button class="tab" data-tab="audio">AUDIO</button>
        <button class="tab" data-tab="video">VIDEO</button>
        <button class="tab" data-tab="contact">CONTACT</button>
      </nav>
    </header>

    <main>
      <section class="content" id="contentArea" tabindex="0" aria-live="polite">
        <!-- filled by JS -->
      </section>

      <aside class="graphics" aria-hidden="false">
        <div class="render-wrap">
          <canvas id="threeCanvas" aria-hidden="true"></canvas>
        </div>
        <div class="knobs" aria-hidden="true">
          <div class="knob">VOL</div>
          <div class="knob">TUNE</div>
          <div class="knob">CLK</div>
        </div>
      </aside>
    </main>

    <footer>
      <div>typewriter · synth · geometric — wireframe edition</div>
      <div>Jesse Young — portfolio</div>
    </footer>
  </div>

  <script>
  /* =============================
     Robust loader + deferred init
     - Prefer local "three.min.js" if present
     - Fallback to CDN if not
     - Fallback 2D animation if both fail
     ============================= */

  const TAB_ORDER = ['bio','design','text','audio','video','contact'];
  const tabs = Array.from(document.querySelectorAll('.tab'));
  const contentArea = document.getElementById('contentArea');
  const canvas = document.getElementById('threeCanvas');
  const renderWrap = document.querySelector('.render-wrap');

  const CONTENT = {
    bio: {title:'BIO', lines:['Jesse Young — writer / translator / designer','I make compact signal-objects: essays, kinetic poems, interfaces, and translations.']},
    design: {title:'DESIGN', lines:['Selected interactive work — interfaces, tiny games, type experiments.']},
    text: {title:'TEXT', lines:['Poems, flash fiction, translations, notes.']},
    audio: {title:'AUDIO', lines:['Recordings and sound experiments.']},
    video: {title:'VIDEO', lines:['Short films and moving-image work.']},
    contact: {title:'CONTACT', lines:['Email: jesse.young@example.com']}
  };

  let activeTab = 'bio';

  function renderContent(k){
    const sec = CONTENT[k];
    contentArea.innerHTML = '';
    const h = document.createElement('h2'); h.textContent = sec.title; contentArea.appendChild(h);
    sec.lines.forEach(l => { const p = document.createElement('p'); p.textContent = l; contentArea.appendChild(p); });
  }

  // robust script loader
  function loadThreeScript(localName='three.min.js', cdnUrl='https://unpkg.com/three@0.156.0/build/three.min.js', timeout=7000){
    return new Promise((resolve, reject) => {
      if (typeof THREE !== 'undefined') return resolve(window.THREE);

      // try local first
      function tryLoad(src) {
        return new Promise((res, rej) => {
          const s = document.createElement('script');
          s.src = src;
          s.async = true;
          s.onload = () => res(window.THREE);
          s.onerror = () => rej(new Error('script load failed: ' + src));
          document.head.appendChild(s);
        });
      }

      // attempt local -> CDN -> reject
      tryLoad(localName).then(resolve).catch(() => {
        tryLoad(cdnUrl).then(resolve).catch(() => {
          // final fallback: reject after timeout
          setTimeout(() => reject(new Error('three failed to load from local or CDN')), timeout);
        });
      });
    });
  }

  /* 2D fallback drawing (clean lines on paper) */
  let fallbackRAF = null;
  function startFallback2D(){
    stopThree();
    const ctx = canvas.getContext('2d');
    function sizeCanvas() {
      const rect = canvas.getBoundingClientRect();
      const dpr = Math.max(1, window.devicePixelRatio || 1);
      canvas.width = Math.floor(rect.width * dpr);
      canvas.height = Math.floor(rect.height * dpr);
    }
    sizeCanvas();
    let t = 0;
    function draw(now){
      t = now/1000;
      sizeCanvas();
      const rect = canvas.getBoundingClientRect();
      const w = rect.width, h = rect.height;
      ctx.save();
      ctx.scale(window.devicePixelRatio, window.devicePixelRatio);
      ctx.clearRect(0,0,canvas.width,canvas.height);
      // paper bg
      ctx.fillStyle = '#fff';
      ctx.fillRect(0,0,w,h);

      ctx.strokeStyle = '#0b0b0b';
      ctx.lineWidth = 1.6;

      // simple moving shapes per tab (wireframe feel)
      if (activeTab === 'bio'){
        const cx = w/2, cy = h/2, R = Math.min(w,h)*0.18;
        ctx.beginPath();
        for (let i=0;i<24;i++){ const a = i*(Math.PI*2/24) + t*0.25; const r = R*(0.75 + 0.2*Math.sin(t + i)); ctx.lineTo(cx + Math.cos(a)*r, cy + Math.sin(a)*r); }
        ctx.closePath(); ctx.stroke();
      } else if (activeTab === 'text'){
        ctx.save();
        ctx.translate(w/2, h/2);
        const s = 1 + Math.sin(t*2)*0.06;
        ctx.font = `${Math.floor(Math.min(w,h)*0.28*s)}px "Special Elite", monospace`;
        ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
        ctx.strokeText('A', 0, 0);
        ctx.restore();
      } else if (activeTab === 'audio'){
        ctx.beginPath(); const mid = h/2;
        for (let x=0;x<w;x+=6){ const n = x / w; const y = mid + Math.sin(n*12 + t*4)* (h*0.07); if (x===0) ctx.moveTo(x,y); else ctx.lineTo(x,y); }
        ctx.stroke();
      } else if (activeTab === 'video'){
        const pad = 18; const rw = w - pad*2, rh = h - pad*2;
        ctx.strokeRect(pad,pad,rw,rh);
        // play triangle pulsing
        ctx.beginPath();
        const px = w/2 - 18, py = h/2;
        ctx.moveTo(px, py-24); ctx.lineTo(px, py+24); ctx.lineTo(px+36, py); ctx.closePath();
        ctx.stroke();
      } else {
        // design/contact default geometric
        ctx.beginPath();
        const cx=w/2, cy=h/2, R=Math.min(w,h)*0.14;
        for(let i=0;i<6;i++){ const a=(i/6)*Math.PI*2 + t*0.4; ctx.lineTo(cx+Math.cos(a)*R, cy+Math.sin(a)*R); }
        ctx.closePath(); ctx.stroke();
      }

      ctx.restore();
      fallbackRAF = requestAnimationFrame(draw);
    }
    fallbackRAF = requestAnimationFrame(draw);
  }
  function stopFallback2D(){ if (fallbackRAF) cancelAnimationFrame(fallbackRAF); fallbackRAF = null; }

  /* ---------- Three.js 3D system ---------- */
  let renderer = null, scene = null, camera = null, root = null, currentGroup = null;
  let mouse = {x:0,y:0};
  let targetRot = {x:0,y:0};

  function setCanvasAndDPR(){
    const rect = canvas.getBoundingClientRect();
    const dpr = Math.max(1, window.devicePixelRatio || 1);
    canvas.width = Math.max(1, Math.floor(rect.width * dpr));
    canvas.height = Math.max(1, Math.floor(rect.height * dpr));
    canvas.style.width = rect.width + 'px';
    canvas.style.height = rect.height + 'px';
    if (renderer) renderer.setPixelRatio(dpr);
  }

  function initThree(){
    if (typeof THREE === 'undefined') {
      console.warn('THREE not present — switching to 2D fallback');
      startFallback2D();
      return;
    }
    stopFallback2D();

    // renderer
    renderer = new THREE.WebGLRenderer({canvas: canvas, antialias:true, alpha:true});
    renderer.setClearColor(0xffffff, 1); // white background (paper)
    setCanvasAndDPR();

    // scene & camera
    scene = new THREE.Scene();
    camera = new THREE.PerspectiveCamera(45, canvas.clientWidth / Math.max(1, canvas.clientHeight), 0.1, 100);
    camera.position.set(0,0,4);

    root = new THREE.Group();
    scene.add(root);

    // subtle light (wireframe materials don't need lights but keep ambience)
    const amb = new THREE.AmbientLight(0xffffff, 0.8); scene.add(amb);
    const pl = new THREE.PointLight(0xffffff, 0.8); pl.position.set(5,5,5); scene.add(pl);

    // pointer interactions -> rotations
    canvas.addEventListener('pointermove', (e) => {
      const rect = canvas.getBoundingClientRect();
      const nx = ((e.clientX - rect.left) / rect.width) * 2 - 1;
      const ny = ((e.clientY - rect.top) / rect.height) * 2 - 1;
      targetRot.y = nx * 0.7;
      targetRot.x = -ny * 0.4;
    });
    canvas.addEventListener('pointerdown', () => {
      if (!currentGroup) return;
      currentGroup.scale.set(1.06,1.06,1.06);
      setTimeout(()=>{ if (currentGroup) currentGroup.scale.set(1,1,1); }, 220);
    });
    canvas.addEventListener('wheel', (e)=> {
      if (!camera) return;
      camera.position.z += e.deltaY * 0.003;
      camera.position.z = Math.min(Math.max(camera.position.z, 2.0), 10);
    }, {passive:true});

    window.addEventListener('resize', () => {
      setCanvasAndDPR();
      if (camera) { camera.aspect = canvas.clientWidth / Math.max(1, canvas.clientHeight); camera.updateProjectionMatrix(); }
      if (renderer) renderer.setSize(canvas.width, canvas.height, false);
    });

    // initial tab
    changeVisual(activeTab);

    // animate
    requestAnimationFrame(animate);
  }

  function disposeGroup(g){
    if (!g) return;
    g.traverse(o => {
      if (o.geometry) { try{ o.geometry.dispose(); } catch(e){} }
      if (o.material) { try{ Array.isArray(o.material) ? o.material.forEach(m=>m.dispose()) : o.material.dispose(); } catch(e){} }
    });
  }

  // create wire materials (black lines)
  function lineOnly(geom, color=0x0b0b0b, opacity=1){
    return new THREE.LineSegments(new THREE.WireframeGeometry(geom), new THREE.LineBasicMaterial({color, transparent: opacity<1, opacity}));
  }

  // Build wireframe groups for each tab ------------------------------------------------
  function makeBio(){
    const g = new THREE.Group();
    const sph = lineOnly(new THREE.SphereGeometry(1.0, 24, 24));
    g.add(sph);
    const rings = lineOnly(new THREE.TorusGeometry(1.3, 0.02, 8, 64), 0x0b0b0b, 0.7);
    rings.rotation.x = 0.5;
    g.add(rings);
    g.userData.animate = (t) => { sph.rotation.y = 0.05*t; rings.rotation.z = 0.12*t; };
    return g;
  }

  function makeDesign(){
    const g = new THREE.Group();
    const outer = lineOnly(new THREE.BoxGeometry(1.5,1.5,1.5));
    const inner = lineOnly(new THREE.BoxGeometry(0.9,0.9,0.9));
    inner.position.set(0.3,-0.2,0.2);
    g.add(outer); g.add(inner);
    g.userData.animate = (t)=>{ outer.rotation.x = 0.02*t; outer.rotation.y = 0.03*t; inner.rotation.y = -0.04*t; };
    return g;
  }

  function makeText(){
    // build a simple wireframe 'A' using box pieces (no font files required)
    const g = new THREE.Group();
    const legGeo = new THREE.BoxGeometry(0.14,1.6,0.12);
    const crossGeo = new THREE.BoxGeometry(0.76,0.12,0.12);
    const left = lineOnly(legGeo); left.position.set(-0.34,0,0); left.rotation.z = 0.26; g.add(left);
    const right = lineOnly(legGeo); right.position.set(0.34,0,0); right.rotation.z = -0.26; g.add(right);
    const cross = lineOnly(crossGeo); cross.position.set(0,-0.04,0); g.add(cross);
    g.userData.animate = (t) => { const s = 1 + Math.sin(t*1.8)*0.07; g.scale.set(s,s,s); g.rotation.y = 0.03*t; };
    return g;
  }

  function makeAudio(){
    const g = new THREE.Group();
    const pts = 256;
    const positions = new Float32Array(pts*3);
    for(let i=0;i<pts;i++){ const x = (i/(pts-1))*4 - 2; positions[i*3]=x; positions[i*3+1]=0; positions[i*3+2]=0; }
    const geom = new THREE.BufferGeometry(); geom.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    const line = new THREE.Line(geom, new THREE.LineBasicMaterial({color:0x0b0b0b, linewidth:2}));
    g.add(line);
    g.userData.animate = (t) => {
      const arr = geom.attributes.position.array;
      for(let i=0;i<pts;i++){
        const x = arr[i*3];
        arr[i*3+1] = Math.sin((x*3.5)+ t*3 + i*0.11) * 0.28 * (1 + 0.2*Math.sin(t*0.8 + i*0.05));
      }
      geom.attributes.position.needsUpdate = true;
      line.rotation.y = 0.06*t;
      g.rotation.x = 0.02*t;
    };
    return g;
  }

  function makeVideo(){
    const g = new THREE.Group();
    // outer frame
    const frame = lineOnly(new THREE.BoxGeometry(2.0,1.2,0.06));
    g.add(frame);
    // play triangle (wire): create triangle geometry
    const triGeo = new THREE.BufferGeometry();
    const vertices = new Float32Array([
      -0.2, -0.25, 0.1,
      -0.2,  0.25, 0.1,
       0.35, 0.0, 0.1,
      -0.2, -0.25, 0.1
    ]);
    triGeo.setAttribute('position', new THREE.BufferAttribute(vertices, 3));
    const tri = new THREE.Line(triGeo, new THREE.LineBasicMaterial({color:0x0b0b0b}));
    g.add(tri);
    g.userData.animate = (t)=> { frame.rotation.y = 0.03*t; tri.rotation.y = 0.05*t; tri.scale.set(1+0.06*Math.sin(t*2),1+0.06*Math.sin(t*2),1); };
    return g;
  }

  function makeContact(){
    const g = new THREE.Group();
    const poly = lineOnly(new THREE.OctahedronGeometry(1.1, 0));
    g.add(poly);
    g.userData.animate = (t)=> { poly.rotation.x = 0.03*t; poly.rotation.y = -0.025*t; };
    return g;
  }

  function createForTab(k){
    switch(k){
      case 'bio': return makeBio();
      case 'design': return makeDesign();
      case 'text': return makeText();
      case 'audio': return makeAudio();
      case 'video': return makeVideo();
      case 'contact': return makeContact();
      default: return makeContact();
    }
  }

  function changeVisual(k){
    activeTab = k;
    renderContent(k);
    if (!root){
      // three not yet initialized, nothing to swap — content will be shown by fallback or when three initializes
      return;
    }
    if (currentGroup){ root.remove(currentGroup); disposeGroup(currentGroup); currentGroup = null; }
    currentGroup = createForTab(k);
    currentGroup.position.set(0,0,0);
    // center and scale to fit nicely
    currentGroup.scale.set(0.9,0.9,0.9);
    root.add(currentGroup);
  }

  /* animation loop */
  function animate(now=0){
    if (!renderer || !scene || !camera) return;
    requestAnimationFrame(animate);
    const t = now / 1000;
    // smooth rotation interpolation
    if (currentGroup){
      currentGroup.rotation.x += (targetRot.x - currentGroup.rotation.x) * 0.08;
      currentGroup.rotation.y += (targetRot.y - currentGroup.rotation.y) * 0.08;
      if (currentGroup.userData && typeof currentGroup.userData.animate === 'function'){
        currentGroup.userData.animate(t);
      }
    }
    renderer.render(scene, camera);
  }

  function stopThree(){
    try{ if (renderer) { renderer.dispose(); renderer.forceContextLoss && renderer.forceContextLoss(); } }catch(e){}
    renderer = null; scene = null; camera = null; root = null; currentGroup = null;
  }

  /* Wiring: tab clicks */
  tabs.forEach(btn => btn.addEventListener('click', async () => {
    tabs.forEach(t => t.classList.remove('active')); btn.classList.add('active');
    const tab = btn.dataset.tab;
    activeTab = tab;
    renderContent(tab);
    try {
      if (typeof THREE === 'undefined' || !renderer) {
        // attempt load + init, then change visual
        await loadThreeScript();
        if (!renderer) initThree();
        changeVisual(tab);
      } else {
        changeVisual(tab);
      }
    } catch (e) {
      console.warn('three failed to load — using fallback 2D', e);
      startFallback2D();
    }
  }));

  // initial render
  renderContent(activeTab);

  /* Boot: try to load three quickly; otherwise fall back and keep trying in background */
  (async function boot(){
    try {
      await loadThreeScript();
      initThree();
      changeVisual(activeTab);

      // smoke test: ensure all tabs can create geometry (non-invasive)
      try {
        for (const k of TAB_ORDER){
          const g = createForTab(k);
          console.assert(!!g, 'smoke: geometry missing for ' + k);
          // clean up
          disposeGroup(g);
        }
        console.log('SMOKE: geometry checks passed');
      } catch (e) { console.warn('SMOKE checks error', e); }

    } catch (err) {
      console.warn('quick load failed, using 2D fallback for now', err);
      startFallback2D();
      // background retry (longer)
      try { await loadThreeScript(undefined, undefined, 10000); initThree(); changeVisual(activeTab); } catch(e){ console.warn('background three load failed', e); }
    }
  })();

  </script>
</body>
</html>
