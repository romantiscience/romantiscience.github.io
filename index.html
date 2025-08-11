<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Jesse Young — Interactive Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=VT323&display=swap" rel="stylesheet">
  <style>
    body { margin:0; background:black; color:white; font-family:"VT323", monospace; display:flex; flex-direction:column; height:100vh; }
    header { padding:20px; display:flex; flex-direction:column; border-bottom:2px solid white; }
    .title { font-size:4rem; color:cyan; margin-bottom:10px; }
    nav { display:flex; gap:15px; flex-wrap:wrap; }
    nav button { background:transparent; color:white; border:2px solid white; padding:5px 10px; cursor:pointer; font-size:1.2rem; transition:all 0.2s; }
    nav button:hover, nav button.active { background:cyan; color:black; border-color:cyan; }
    main { flex:1; display:flex; }
    .content { flex:1; padding:20px; font-size:1.2rem; }
    .graphics { flex:1; position:relative; }
    canvas { width:100%; height:100%; display:block; }
  </style>
</head>
<body>
  <header>
    <div class="title">JESSE YOUNG</div>
    <nav>
      <button class="tab active" data-tab="bio">BIO</button>
      <button class="tab" data-tab="design">DESIGN</button>
      <button class="tab" data-tab="articles">ARTICLES</button>
      <button class="tab" data-tab="translation">TRANSLATION</button>
      <button class="tab" data-tab="poetry">POETRY</button>
      <button class="tab" data-tab="audio">AUDIO</button>
      <button class="tab" data-tab="contact">CONTACT</button>
    </nav>
  </header>
  <main>
    <div class="content" id="contentArea"></div>
    <div class="graphics"><canvas id="threeCanvas"></canvas></div>
  </main>

<script src="https://unpkg.com/three@0.156.0/build/three.min.js"></script>
<script>
const content = {
  bio: "I make compact signal-objects: essays, kinetic poems, interfaces, and translations.",
  design: "Selected interactive work.",
  articles: "Essays & shorter pieces.",
  translation: "Selected translations.",
  poetry: "Kinetic lines & micro-forms.",
  audio: "Selected recordings.",
  contact: "Email: jesse.young@example.com"
};

let scene, camera, renderer, mesh, clock;
const canvas = document.getElementById('threeCanvas');
let font;

function init(){
  scene = new THREE.Scene();
  camera = new THREE.PerspectiveCamera(45, canvas.clientWidth/canvas.clientHeight, 0.1, 100);
  camera.position.z = 5;
  clock = new THREE.Clock();
  const light = new THREE.PointLight(0xffffff, 1);
  light.position.set(5,5,5);
  scene.add(light);
  renderer = new THREE.WebGLRenderer({canvas, antialias:true, alpha:true});
  renderer.setSize(canvas.clientWidth, canvas.clientHeight);
  window.addEventListener('resize', onResize);
  changeShape('bio');
  animate();
}

function createShape(tab){
  switch(tab){
    case 'bio': return new THREE.SphereGeometry(1, 16, 16);
    case 'design': return new THREE.BoxGeometry(1.5, 1.5, 1.5);
    case 'articles': return new THREE.CylinderGeometry(0.8, 0.8, 2, 16);
    case 'translation': return new THREE.TorusKnotGeometry(0.7, 0.2, 64, 16);
    case 'poetry': return new THREE.TextGeometry('A', {font: font, size: 1, height: 0.05});
    case 'audio': return makeWaveGeometry();
    case 'contact': return new THREE.IcosahedronGeometry(1.2, 0);
  }
}

function makeWaveGeometry(){
  const points = [];
  for(let i=0;i<50;i++){
    points.push(new THREE.Vector3((i/5)-5, Math.sin(i*0.3), 0));
  }
  const curve = new THREE.CatmullRomCurve3(points);
  return new THREE.TubeGeometry(curve, 100, 0.05, 8, false);
}

function changeShape(tab){
  if(mesh){ scene.remove(mesh); mesh.geometry.dispose(); mesh.material.dispose(); }
  const geometry = createShape(tab);
  const material = new THREE.MeshBasicMaterial({color:0x00ffff, wireframe:true});
  mesh = new THREE.Mesh(geometry, material);
  mesh.rotationSpeed = (tab==='audio')?0.05:0.01;
  scene.add(mesh);
}

function animate(){
  requestAnimationFrame(animate);
  const delta = clock.getDelta();
  if(mesh){
    mesh.rotation.x += mesh.rotationSpeed || 0.01;
    mesh.rotation.y += mesh.rotationSpeed || 0.01;
    if(mesh.geometry.type==='TextGeometry'){
      const scale = 1 + Math.sin(clock.elapsedTime*2)*0.1;
      mesh.scale.set(scale, scale, scale);
    }
  }
  renderer.render(scene, camera);
}

function onResize(){
  camera.aspect = canvas.clientWidth/canvas.clientHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(canvas.clientWidth, canvas.clientHeight);
}

new THREE.FontLoader().load('https://threejs.org/examples/fonts/helvetiker_regular.typeface.json', f=>{
  font = f;
  init();
});

document.querySelectorAll('.tab').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
    btn.classList.add('active');
    const tab = btn.dataset.tab;
    document.getElementById('contentArea').textContent = content[tab];
    changeShape(tab);
  });
});

document.getElementById('contentArea').textContent = content['bio'];
</script>
</body>
</html>
