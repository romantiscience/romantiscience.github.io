<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Jesse Young — Portfolio (Offline)</title>
  <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;700&display=swap" rel="stylesheet">
  <style>
  :root{--bg:#fbfbfb;--panel:#fff;--line:#0b0b0b;--muted:#666;--accent:#00a6a0}
  *{box-sizing:border-box}html,body{height:100%}body{margin:20px;background:var(--bg);font-family:"IBM Plex Mono",monospace;color:var(--line);display:flex;align-items:center;justify-content:center}
  .shell{width:min(1180px,96vw);background:linear-gradient(180deg,var(--panel),#fff);border:2px solid var(--line);border-radius:10px;padding:18px}
  header{display:flex;align-items:flex-end;gap:18px;margin-bottom:12px}
  .title{font-size:clamp(28px,5vw,48px);font-weight:700;letter-spacing:1px}
  nav{margin-left:auto;display:flex;gap:10px;flex-wrap:wrap}
  .tab{background:transparent;border:2px solid var(--line);padding:8px 12px;border-radius:8px;cursor:pointer;font-size:13px;min-width:78px;text-align:center}
  .tab.active{background:var(--line);color:var(--panel)}
  main{display:flex;gap:18px;min-height:56vh}
  .content{flex:2.2;background:var(--panel);border-radius:10px;padding:20px;overflow:auto;min-width:360px}
  .graphics{flex:1;min-width:320px;max-width:480px;border-radius:10px;background:var(--panel);display:flex;align-items:center;justify-content:center;padding:14px;border-left:2px solid rgba(0,0,0,0.04)}
  .render-wrap{width:92%;height:86%;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg,#fff,#fbfbfb);border-radius:8px;border:1px dashed rgba(0,0,0,0.04)}
  canvas{width:86%;height:86%;max-width:720px;max-height:560px;display:block}
  footer{margin-top:12px;display:flex;justify-content:space-between;color:var(--muted);font-size:13px;padding-top:10px}
  @media (max-width:980px){main{flex-direction:column}.graphics{width:100%;max-width:none;min-width:unset}canvas{width:96%;height:260px}}
  </style>
</head>
<body>
  <div class="shell">
    <header>
      <div class="title">JESSE YOUNG</div>
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
      <section class="content" id="contentArea" tabindex="0" aria-live="polite"></section>
      <aside class="graphics" aria-hidden="false">
        <div class="render-wrap">
          <canvas id="threeCanvas" aria-hidden="true"></canvas>
        </div>
      </aside>
    </main>
    <footer>
      <div>typewriter · synth · geometric — wireframe edition</div>
      <div>Jesse Young — portfolio</div>
    </footer>
  </div>

<script src="three.min.js"></script>
<script>
// Minimal bootstrap script: uses local three.min.js and local font file.
(function(){
  const canvas = document.getElementById('threeCanvas');
  const contentArea = document.getElementById('contentArea');
  const tabs = Array.from(document.querySelectorAll('.tab'));
  const CONTENT = {
    bio:{title:'BIO', lines:['Jesse Young — writer / translator / designer','I make compact signal-objects.']},
    design:{title:'DESIGN', lines:['Selected interactive work — interfaces and type experiments.']},
    text:{title:'TEXT', lines:['Poems, short forms, translations.']},
    audio:{title:'AUDIO', lines:['Recordings and sound experiments.']},
    video:{title:'VIDEO', lines:['Short films and moving-image work.']},
    contact:{title:'CONTACT', lines:['Email: jesse.young@example.com']}
  };
  let active='bio';
  function renderContent(k){
    const sec=CONTENT[k]; contentArea.innerHTML=''; const h=document.createElement('h2'); h.textContent=sec.title; contentArea.appendChild(h); sec.lines.forEach(l=>{const p=document.createElement('p');p.textContent=l;contentArea.appendChild(p);});
  }
  renderContent(active);

  // if THREE not available, fallback 2D
  function startFallback(){ const ctx=canvas.getContext('2d'); let t=0; function draw(now){ t=now/1000; const rect=canvas.getBoundingClientRect(); const dpr=Math.max(1,window.devicePixelRatio||1); canvas.width=Math.floor(rect.width*dpr); canvas.height=Math.floor(rect.height*dpr); ctx.save(); ctx.scale(dpr,dpr); ctx.clearRect(0,0,rect.width,rect.height); ctx.fillStyle='#fff'; ctx.fillRect(0,0,rect.width,rect.height); ctx.strokeStyle='#0b0b0b'; ctx.lineWidth=1.6; ctx.beginPath(); ctx.arc(rect.width/2, rect.height/2, Math.min(rect.width,rect.height)*0.18, 0, Math.PI*2); ctx.stroke(); ctx.restore(); requestAnimationFrame(draw);} requestAnimationFrame(draw); }

  // safe Three init
  async function initThreeSafe(){
    if (typeof THREE === 'undefined'){ console.warn('three missing -> starting fallback'); startFallback(); return; }
    try{
      const renderer = new THREE.WebGLRenderer({canvas:canvas,antialias:true,alpha:true});
      const rect = canvas.getBoundingClientRect(); const dpr=Math.max(1,window.devicePixelRatio||1); canvas.width=Math.floor(rect.width*dpr); canvas.height=Math.floor(rect.height*dpr); renderer.setSize(canvas.width, canvas.height, false); renderer.setPixelRatio(dpr);
      const scene = new THREE.Scene();
      const camera = new THREE.PerspectiveCamera(45, rect.width/Math.max(1,rect.height), 0.1, 100); camera.position.set(0,0,4);
      const root = new THREE.Group(); scene.add(root);
      const amb = new THREE.AmbientLight(0xffffff,0.9); scene.add(amb);
      const pl = new THREE.PointLight(0xffffff,0.8); pl.position.set(5,5,5); scene.add(pl);

      let current=null;
      function dispose(g){ if(!g) return; g.traverse(o=>{ if(o.geometry){ try{o.geometry.dispose();}catch(e){} } if(o.material){ try{ if(Array.isArray(o.material)) o.material.forEach(m=>m.dispose()); else o.material.dispose(); }catch(e){} } }); }
      function makeWire(geom){ return new THREE.LineSegments(new THREE.WireframeGeometry(geom), new THREE.LineBasicMaterial({color:0x0b0b0b})); }

      function createFor(tab){
        switch(tab){
          case 'bio': { const g=new THREE.Group(); g.add(makeWire(new THREE.SphereGeometry(1, 24,24))); return g;}
          case 'design': { const g=new THREE.Group(); g.add(makeWire(new THREE.BoxGeometry(1.4,1.4,1.4))); return g;}
          case 'text': { const g=new THREE.Group(); const leg=new THREE.LineSegments(new THREE.WireframeGeometry(new THREE.BoxGeometry(0.14,1.6,0.12)), new THREE.LineBasicMaterial({color:0x0b0b0b})); const leg2=leg.clone(); leg.position.set(-0.34,0,0); leg2.position.set(0.34,0,0); g.add(leg,leg2); return g;}
          case 'audio': { const g=new THREE.Group(); const pts=128; const pos=new Float32Array(pts*3); for(let i=0;i<pts;i++){ const x=(i/(pts-1))*4-2; pos[i*3]=x; pos[i*3+1]=0; pos[i*3+2]=0;} const geom=new THREE.BufferGeometry(); geom.setAttribute('position', new THREE.BufferAttribute(pos,3)); const line=new THREE.Line(geom, new THREE.LineBasicMaterial({color:0x0b0b0b})); g.add(line); g.userData._lineGeom=geom; return g;}
          case 'video': { const g=new THREE.Group(); g.add(makeWire(new THREE.BoxGeometry(2.0,1.2,0.06))); return g;}
          case 'contact': { const g=new THREE.Group(); g.add(makeWire(new THREE.OctahedronGeometry(1.1,0))); return g;}
        }
      }

      function swap(tab){
        if (current){ root.remove(current); dispose(current); current=null; }
        current = createFor(tab);
        current.scale.set(0.9,0.9,0.9);
        root.add(current);
      }

      // simple pointer interactivity
      let target={x:0,y:0};
      canvas.addEventListener('pointermove', (e)=>{ const r=canvas.getBoundingClientRect(); const nx=((e.clientX-r.left)/r.width)*2-1; const ny=((e.clientY-r.top)/r.height)*2-1; target.x=nx*0.7; target.y=-ny*0.4; });

      function animate(now=0){
        requestAnimationFrame(animate);
        const t = now/1000;
        if (current){
          current.rotation.x += (target.y - current.rotation.x) * 0.08;
          current.rotation.y += (target.x - current.rotation.y) * 0.08;
          // per-type small anims
          if (current.userData && current.userData._lineGeom){
            const arr = current.userData._lineGeom.attributes.position.array;
            const pts = arr.length/3;
            for(let i=0;i<pts;i++){ const x = arr[i*3]; arr[i*3+1]=Math.sin((x*3.5)+t*3 + i*0.09)*0.22; }
            current.userData._lineGeom.attributes.position.needsUpdate = true;
          } else {
            current.rotation.y += 0.005;
          }
        }
        renderer.render(scene,camera);
      }

      swap(active);
      animate();

      // public swap
      window.__swapThree = swap;
    }catch(e){
      console.warn('three init error',e);
      startFallback();
    }
  }

  // Attempt to init three (local file). If not present, fallback to 2D.
  try{
    if (typeof THREE === 'undefined') throw new Error('THREE missing');
    initThreeSafe = initThreeSafe || null;
    // call our init (safe)
    initThreeSafe && initThreeSafe();
  }catch(e){
    // if THREE is undefined try to load local script dynamically then attempt init
    const s = document.createElement('script');
    s.src = 'three.min.js';
    s.onload = function(){ if (typeof THREE !== 'undefined'){ try{ initThreeSafe(); }catch(e){ console.warn(e); startFallback(); } } else { console.warn('three loaded but THREE undefined'); startFallback(); } };
    s.onerror = function(){ console.warn('three.js load failed'); startFallback(); };
    document.head.appendChild(s);
  }

  // wiring tabs to swap visuals + update content
  tabs.forEach(btn => btn.addEventListener('click', () => {
    tabs.forEach(t=>t.classList.remove('active')); btn.classList.add('active');
    const tab = btn.dataset.tab;
    active = tab;
    renderContent(tab);
    // if three available and swap function is exposed use it
    if (typeof window.__swapThree === 'function'){
      window.__swapThree(tab);
    }
  }));
})();
</script>
</body>
</html>
