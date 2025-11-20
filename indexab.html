<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1" />
<title>Jumping — Singe $JUMP</title>
<style>
  html,body{height:100%;margin:0;background:#87ceeb;touch-action:none;-webkit-tap-highlight-color:transparent}
  #game{display:block;margin:0 auto;background:#7ec850;border-radius:10px;max-width:900px;width:100%;height:60vh;box-shadow:0 10px 30px rgba(0,0,0,0.25)}
  #ui{font-family:Inter,system-ui,Arial;color:#222;text-align:center;margin-top:10px}
  .btn{display:inline-block;background:#fff;padding:8px 14px;border-radius:8px;box-shadow:0 3px 8px rgba(0,0,0,.15);cursor:pointer}
  #instructions{font-size:14px;color:#fff;margin-top:8px}
</style>
</head>
<body>
<canvas id="game"></canvas>
<div id="ui">
  <div style="display:flex;justify-content:space-between;max-width:900px;margin:8px auto;">
    <div class="btn" id="playBtn">TAP POUR JOUER</div>
    <div style="font-weight:700">Score: <span id="score">0</span></div>
  </div>
  <div id="instructions">Tape l'écran ou clique pour faire SAUTER le singe 🐵. Évite les obstacles !</div>
</div>

<script>
(() => {
  const canvas = document.getElementById('game');
  const ctx = canvas.getContext('2d');
  const scoreEl = document.getElementById('score');
  const playBtn = document.getElementById('playBtn');

  // Responsive canvas
  function resize(){
    canvas.width = Math.min(window.innerWidth,900);
    canvas.height = Math.max(320, Math.floor(window.innerHeight * 0.60));
  }
  window.addEventListener('resize', resize);
  resize();

  // Game variables
  let running = false;
  let score = 0;
  let speed = 3;
  let gravity = 0.9;
  let obstacles = [];
  let frame = 0;
  let best = 0;

  // Player (singe)
  const player = {
    x: 80,
    y: canvas.height - 120,
    w: 60,
    h: 60,
    vy: 0,
    jumping: false,
    draw(){
      // body
      ctx.save();
      ctx.translate(this.x + this.w/2, this.y + this.h/2);
      // draw simple monkey with emoji-like face
      ctx.fillStyle = '#8B5A2B';
      ctx.beginPath();
      ctx.ellipse(0, 0, this.w/2, this.h/2, 0, 0, Math.PI*2);
      ctx.fill();
      // face patch
      ctx.fillStyle = '#F2D6B3';
      ctx.beginPath();
      ctx.ellipse(-2, 4, this.w/3.2, this.h/3.2, 0, 0, Math.PI*2);
      ctx.fill();
      // eyes
      ctx.fillStyle = '#111';
      ctx.beginPath(); ctx.arc(-14, -2, 4, 0, Math.PI*2); ctx.fill();
      ctx.beginPath(); ctx.arc(6, -2, 4, 0, Math.PI*2); ctx.fill();
      // smile
      ctx.strokeStyle = '#5a2d0a'; ctx.lineWidth = 2;
      ctx.beginPath(); ctx.arc(-3, 10, 10, 0, Math.PI); ctx.stroke();
      ctx.restore();
    },
    update(){
      this.vy += gravity;
      this.y += this.vy;
      // ground collision
      const ground = canvas.height - 60;
      if(this.y + this.h > ground){
        this.y = ground - this.h;
        this.vy = 0;
        this.jumping = false;
      }
    },
    jump(){
      if(!this.jumping){
        this.vy = -16;
        this.jumping = true;
      }
    }
  };

  // Obstacle generator
  function spawnObstacle(){
    const h = 30 + Math.random()*60;
    const w = 20 + Math.random()*30;
    const y = canvas.height - 60 - h;
    obstacles.push({
      x: canvas.width + 10,
      y,
      w, h
    });
  }

  // Reset
  function reset(){
    obstacles = [];
    score = 0;
    speed = 3;
    frame = 0;
    running = true;
  }

  // Game loop
  function loop(){
    if(!running) return;
    frame++;
    ctx.clearRect(0,0,canvas.width,canvas.height);

    // background ground
    ctx.fillStyle = '#6b8e23';
    ctx.fillRect(0, canvas.height - 60, canvas.width, 60);

    // spawn obstacles every ~90 frames (faster with score)
    if(frame % Math.max(60, Math.floor(120 - score/5)) === 0){
      spawnObstacle();
    }

    // update obstacles
    for(let i = obstacles.length-1; i >= 0; i--){
      obstacles[i].x -= speed;
      // draw
      ctx.fillStyle = '#46311a';
      roundRect(ctx, obstacles[i].x, obstacles[i].y, obstacles[i].w, obstacles[i].h, 6, true, false);
      // collision
      if(collide(player, obstacles[i])){
        running = false;
        playBtn.innerText = 'REJOUER';
        best = Math.max(best, score);
        // show game over overlay
        gameOver();
      }
      // remove off-screen
      if(obstacles[i].x + obstacles[i].w < -50) obstacles.splice(i,1);
    }

    // update player
    player.update();
    player.draw();

    // score and speed
    if(frame % 6 === 0) { score++; scoreEl.innerText = score; }
    speed = 3 + Math.min(6, Math.floor(score/30));

    requestAnimationFrame(loop);
  }

  function collide(a, b){
    return a.x < b.x + b.w &&
           a.x + a.w > b.x &&
           a.y < b.y + b.h &&
           a.y + a.h > b.y;
  }

  function roundRect(ctx, x, y, w, h, r, fill, stroke){
    if (typeof stroke === 'undefined') stroke = true;
    if (typeof r === 'undefined') r = 5;
    ctx.beginPath();
    ctx.moveTo(x + r, y);
    ctx.arcTo(x + w, y, x + w, y + h, r);
    ctx.arcTo(x + w, y + h, x, y + h, r);
    ctx.arcTo(x, y + h, x, y, r);
    ctx.arcTo(x, y, x + w, y, r);
    ctx.closePath();
    if(fill) ctx.fill();
    if(stroke) ctx.stroke();
  }

  // Input
  function tapHandler(e){
    e.preventDefault();
    if(!running){
      reset();
      loop();
    }
    player.jump();
  }
  canvas.addEventListener('touchstart', tapHandler, {passive:false});
  canvas.addEventListener('mousedown', tapHandler);

  playBtn.addEventListener('click', () => {
    if(!running){
      reset();
      loop();
    } else {
      player.jump();
    }
  });

  // Game over overlay
  function gameOver(){
    // small modal
    ctx.fillStyle = 'rgba(0,0,0,0.45)';
    ctx.fillRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle = '#fff';
    ctx.textAlign = 'center';
    ctx.font = '28px sans-serif';
    ctx.fillText('Game Over 🐵', canvas.width/2, canvas.height/2 - 10);
    ctx.font = '18px sans-serif';
    ctx.fillText('Score: ' + score + '  •  Best: ' + best, canvas.width/2, canvas.height/2 + 20);

    // send score to embedding app (optional)
    try {
      // If your game is inside Telegram's webview, it can receive postMessage or Telegram.WebApp methods.
      // We'll try to postMessage to parent — you can catch it on your bot server if proxied.
      window.parent.postMessage({type:'jumping_score', score}, '*');
    } catch(e){}
  }

  // expose for debugging
  window.JUMPING = { getScore: ()=>score, getBest: ()=>best };

  // first frame draw (idle monkey)
  ctx.fillStyle = '#6b8e23';
  ctx.fillRect(0, canvas.height - 60, canvas.width, 60);
  player.draw();
})();
</script>
</body>
</html>
