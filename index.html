<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>COUNTRYBALLS WAR ONLINE - VM</title>
<script src="https://cdn.jsdelivr.net/npm/peerjs@1.5.2/dist/peerjs.min.js"></script>
<style>
  :root {
    --primary: #4e73df;
    --accent: #7cff4a;
    --panel: rgba(15, 23, 42, 0.85);
  }
  * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
  html, body {
    margin: 0; padding: 0; width: 100%; height: 100%;
    background: #000; overflow: hidden;
    font-family: 'Segoe UI', Arial, sans-serif; color: #fff;
  }

  /* PANTALLA INTRO ESTILO GARENA */
  #introScreen {
    position: absolute; inset: 0; z-index: 1000;
    background: #000;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    opacity: 1; transition: opacity 0.8s ease-out;
    cursor: pointer;
  }
  .intro-logo {
    font-size: 4rem; font-weight: 900; letter-spacing: 4px;
    background: linear-gradient(135deg, #ff0055, #ffcc00, #00ffcc);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    text-shadow: 0 0 20px rgba(255,0,85,0.5);
    animation: zoomIn 1.5s ease-out;
  }
  .intro-sub {
    font-size: 1.2rem; color: #888; letter-spacing: 6px; margin-top: 10px;
    animation: fadeIn 2s ease-out;
  }
  .intro-hint {
    margin-top: 30px; font-size: 0.9rem; color: #666;
  }

  @keyframes zoomIn {
    0% { transform: scale(0.5); opacity: 0; }
    100% { transform: scale(1); opacity: 1; }
  }
  @keyframes fadeIn {
    0% { opacity: 0; }
    100% { opacity: 1; }
  }

  /* CONTENEDOR PRINCIPAL Y PANTALLAS */
  .screen {
    position: absolute; inset: 0; display: none;
    flex-direction: column; align-items: center; justify-content: center;
    background: radial-gradient(circle, #1a202c 0%, #0f172a 100%);
  }
  .screen.active { display: flex; }

  .panel {
    background: var(--panel); border: 2px solid rgba(255,255,255,0.1);
    border-radius: 16px; padding: 24px; width: 90%; max-width: 420px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5); backdrop-filter: blur(10px);
    text-align: center;
  }

  h1 { margin: 0 0 15px; font-size: 1.8rem; text-transform: uppercase; letter-spacing: 2px; }
  
  .btn {
    background: linear-gradient(135deg, #3b82f6, #1d4ed8);
    color: #fff; border: none; padding: 12px 20px; border-radius: 8px;
    font-size: 1rem; font-weight: bold; cursor: pointer; width: 100%;
    margin-top: 10px; transition: transform 0.1s, filter 0.2s;
  }
  .btn:active { transform: scale(0.97); }
  .btn-accent { background: linear-gradient(135deg, #10b981, #047857); }

  input {
    width: 100%; padding: 12px; margin: 8px 0; border-radius: 8px;
    border: 1px solid rgba(255,255,255,0.2); background: rgba(0,0,0,0.3);
    color: #fff; text-align: center; font-size: 1rem; outline: none;
  }

  /* LOBBY / SKIN SELECTOR */
  .skin-preview {
    width: 120px; height: 120px; border-radius: 50%; margin: 15px auto;
    border: 4px solid #fff; box-shadow: 0 0 15px rgba(255,255,255,0.3);
    background-size: cover; background-position: center; transition: transform 0.2s;
  }

  /* JUEGO CANVAS */
  #gameCanvas {
    width: 100%; height: 100%; display: block; background: #111827;
  }
  #uiOverlay {
    position: absolute; top: 10px; left: 10px; right: 10px;
    display: flex; justify-content: space-between; pointer-events: none;
  }
  .hud-box {
    background: rgba(0,0,0,0.6); padding: 8px 15px; border-radius: 8px;
    font-weight: bold; border: 1px solid rgba(255,255,255,0.2);
  }
</style>
</head>
<body>

  <!-- PANTALLA INTRO -->
  <div id="introScreen" onclick="finishIntro()">
    <div class="intro-logo">VM</div>
    <div class="intro-sub">STUDIOS</div>
    <div class="intro-hint">Toca la pantalla para continuar</div>
  </div>

  <!-- PANTALLA LOBBY -->
  <div id="screenLobby" class="screen">
    <div class="panel">
      <h1>Countryballs War</h1>
      <p style="color: #aaa; font-size: 0.9rem;">Elige tu jugador y entra a la batalla</p>
      
      <input type="text" id="nicknameInput" placeholder="Tu Nombre de Jugador" maxlength="12" value="Player1">
      
      <div id="skinPreview" class="skin-preview"></div>
      <button class="btn" onclick="changeSkin()">Cambiar Skin</button>

      <hr style="border-color: rgba(255,255,255,0.1); margin: 15px 0;">

      <button class="btn btn-accent" onclick="startGame()">JUGAR SOLO</button>
    </div>
  </div>

  <!-- PANTALLA JUEGO -->
  <div id="screenGame" class="screen">
    <div id="uiOverlay">
      <div class="hud-box" id="hudName">Jugador</div>
      <div class="hud-box" id="hudScore">Puntos: 0</div>
    </div>
    <canvas id="gameCanvas"></canvas>
  </div>

<script>
  // AUDIO SYNTH
  const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  function playSound(freq, duration) {
    if (audioCtx.state === 'suspended') audioCtx.resume();
    try {
      const osc = audioCtx.createOscillator();
      const gain = audioCtx.createGain();
      osc.type = 'sine';
      osc.frequency.value = freq;
      gain.gain.setValueAtTime(0.1, audioCtx.currentTime);
      gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + duration);
      osc.connect(gain);
      gain.connect(audioCtx.destination);
      osc.start();
      osc.stop(audioCtx.currentTime + duration);
    } catch(e){}
  }

  // CONTROL INTRO
  let introFinished = false;
  function finishIntro() {
    if (introFinished) return;
    introFinished = true;
    playSound(440, 0.2);
    const intro = document.getElementById('introScreen');
    intro.style.opacity = '0';
    setTimeout(() => {
      intro.style.display = 'none';
      showScreen('screenLobby');
    }, 800);
  }

  // Auto-avanzar intro tras 2.5 segundos
  setTimeout(finishIntro, 2500);

  // MANEJO DE PANTALLAS
  const screens = {
    screenLobby: document.getElementById('screenLobby'),
    screenGame: document.getElementById('screenGame')
  };

  function showScreen(name) {
    Object.values(screens).forEach(s => s.classList.remove('active'));
    screens[name].classList.add('active');
  }

  // SKINS Y SELECCION
  const skins = [
    'https://flagcdn.com/w160/ar.png', // Argentina
    'https://flagcdn.com/w160/br.png', // Brasil
    'https://flagcdn.com/w160/mx.png', // México
    'https://flagcdn.com/w160/es.png', // España
    'https://flagcdn.com/w160/us.png'  // EE.UU.
  ];
  let currentSkinIdx = 0;
  const skinPreview = document.getElementById('skinPreview');

  function updateSkinPreview() {
    skinPreview.style.backgroundImage = `url(${skins[currentSkinIdx]})`;
  }
  function changeSkin() {
    currentSkinIdx = (currentSkinIdx + 1) % skins.length;
    updateSkinPreview();
    playSound(600, 0.1);
  }
  updateSkinPreview();

  // BUCLE DE JUEGO BASICO
  let canvas, ctx;
  let player = { x: 100, y: 100, radius: 25, speed: 4 };
  let keys = {};

  function startGame() {
    playSound(800, 0.2);
    showScreen('screenGame');
    canvas = document.getElementById('gameCanvas');
    ctx = canvas.getContext('2d');
    
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    document.getElementById('hudName').innerText = document.getElementById('nicknameInput').value || 'Jugador';

    window.addEventListener('keydown', e => keys[e.key] = true);
    window.addEventListener('keyup', e => keys[e.key] = false);

    requestAnimationFrame(gameLoop);
  }

  function gameLoop() {
    if (keys['ArrowUp'] || keys['w']) player.y -= player.speed;
    if (keys['ArrowDown'] || keys['s']) player.y += player.speed;
    if (keys['ArrowLeft'] || keys['a']) player.x -= player.speed;
    if (keys['ArrowRight'] || keys['d']) player.x += player.speed;

    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Dibujar Jugador
    ctx.beginPath();
    ctx.arc(player.x, player.y, player.radius, 0, Math.PI * 2);
    ctx.fillStyle = '#3b82f6';
    ctx.fill();
    ctx.strokeStyle = '#fff';
    ctx.lineWidth = 3;
    ctx.stroke();

    requestAnimationFrame(gameLoop);
  }
</script>
</body>
</html>
