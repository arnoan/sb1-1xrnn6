<script>
  import { onMount } from 'svelte';

  let canvas;
  let ctx;
  let balloonX = 0;
  let balloonY = 0;
  let balloonSpeed = 1;

  onMount(() => {
    ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = 400;
    animate();
  });

  function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawSky();
    drawBalloon();
    moveBalloon();
    requestAnimationFrame(animate);
  }

  function drawSky() {
    let gradient = ctx.createLinearGradient(0, 0, 0, canvas.height);
    gradient.addColorStop(0, "#87CEEB");
    gradient.addColorStop(1, "#E0F6FF");
    ctx.fillStyle = gradient;
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    // Draw clouds
    ctx.fillStyle = "rgba(255, 255, 255, 0.7)";
    drawCloud(100, 50, 70);
    drawCloud(300, 100, 60);
    drawCloud(500, 30, 80);
  }

  function drawCloud(x, y, size) {
    ctx.beginPath();
    ctx.arc(x, y, size * 0.4, 0, Math.PI * 2);
    ctx.arc(x + size * 0.3, y - size * 0.2, size * 0.3, 0, Math.PI * 2);
    ctx.arc(x + size * 0.6, y, size * 0.4, 0, Math.PI * 2);
    ctx.fill();
  }

  function drawBalloon() {
    // Balloon basket
    ctx.fillStyle = "#8B4513";
    ctx.fillRect(balloonX + 40, balloonY + 120, 40, 30);

    // Balloon
    ctx.beginPath();
    ctx.moveTo(balloonX + 60, balloonY + 120);
    ctx.quadraticCurveTo(balloonX + 60, balloonY, balloonX + 10, balloonY + 50);
    ctx.quadraticCurveTo(balloonX - 60, balloonY + 50, balloonX - 10, balloonY + 120);
    ctx.quadraticCurveTo(balloonX + 25, balloonY + 140, balloonX + 60, balloonY + 120);
    ctx.fillStyle = "#FF6347";
    ctx.fill();

    // Balloon stripes
    ctx.beginPath();
    ctx.moveTo(balloonX + 30, balloonY + 50);
    ctx.lineTo(balloonX + 30, balloonY + 120);
    ctx.moveTo(balloonX, balloonY + 40);
    ctx.lineTo(balloonX, balloonY + 120);
    ctx.moveTo(balloonX - 30, balloonY + 50);
    ctx.lineTo(balloonX - 30, balloonY + 120);
    ctx.strokeStyle = "#FF4500";
    ctx.lineWidth = 2;
    ctx.stroke();
  }

  function moveBalloon() {
    balloonX += balloonSpeed;
    balloonY = 50 + Math.sin(balloonX * 0.02) * 20;

    if (balloonX > canvas.width + 100) {
      balloonX = -100;
    }
  }
</script>

<main>
  <h1>Experimental: Hot Air Balloon Adventure</h1>
  <p>Watch the mesmerizing journey of our hot air balloon across a beautiful sky!</p>
  <canvas bind:this={canvas}></canvas>
  <div class="info">
    <h2>About This Experiment</h2>
    <p>This page showcases an animated hot air balloon using HTML5 Canvas and Svelte. The balloon gracefully floats across a dynamically generated sky with clouds, creating a serene and captivating visual experience.</p>
    <h3>Technical Details:</h3>
    <ul>
      <li>Canvas-based animation</li>
      <li>Dynamic sky gradient</li>
      <li>Procedurally generated clouds</li>
      <li>Smooth balloon movement with subtle vertical oscillation</li>
    </ul>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
  }

  h1 {
    color: #ff3e00;
    font-size: 2.5em;
    margin-bottom: 0.5em;
  }

  canvas {
    border: 1px solid #ccc;
    max-width: 100%;
  }

  .info {
    max-width: 600px;
    margin: 2em auto;
    text-align: left;
    background-color: #f9f9f9;
    padding: 1em;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }

  h2, h3 {
    color: #40b3ff;
  }

  ul {
    padding-left: 1.5em;
  }
</style>