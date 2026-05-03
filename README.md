<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Abram ❤️ Hanii — Forever & Always</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Great+Vibes&display=swap" rel="stylesheet">
<style>
  :root {
    --rose: #f9a8c4;
    --blush: #fce4ec;
    --gold: #f5c842;
    --gold-light: #fff3b0;
    --lavender: #d8b4fe;
    --deep-purple: #6b21a8;
    --deep-rose: #be185d;
    --bg-dark: #0d0408;
    --bg-mid: #1a0a14;
    --text-light: #fef3f8;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg-dark);
    color: var(--text-light);
    font-family: 'Cormorant Garamond', serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  #cursor {
    position: fixed;
    width: 20px; height: 20px;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s;
  }
  #cursor::after {
    content: '♥';
    font-size: 18px;
    color: var(--rose);
    filter: drop-shadow(0 0 6px var(--rose));
  }

  .cursor-trail {
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    font-size: 12px;
    color: var(--gold);
    opacity: 0;
    animation: trailFade 1s ease forwards;
  }

  @keyframes trailFade {
    0% { opacity: 0.8; transform: translate(-50%,-50%) scale(1); }
    100% { opacity: 0; transform: translate(-50%,-70%) scale(0.3); }
  }

  /* CANVAS */
  #heroCanvas {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: 0;
    pointer-events: none;
  }

  /* MUSIC TOGGLE */
  #musicBtn {
    position: fixed;
    top: 24px; right: 24px;
    z-index: 1000;
    background: rgba(249,168,196,0.15);
    border: 1px solid rgba(249,168,196,0.4);
    border-radius: 50px;
    padding: 10px 20px;
    color: var(--rose);
    font-family: 'Cormorant Garamond', serif;
    font-size: 14px;
    cursor: pointer;
    backdrop-filter: blur(10px);
    transition: all 0.3s;
    display: flex; align-items: center; gap: 8px;
  }
  #musicBtn:hover {
    background: rgba(249,168,196,0.3);
    box-shadow: 0 0 20px rgba(249,168,196,0.4);
  }
  #musicBtn .note { font-size: 18px; animation: noteFloat 2s ease-in-out infinite; }
  @keyframes noteFloat { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-4px)} }

  /* SECTIONS */
  section {
    position: relative;
    z-index: 10;
  }

  /* HERO */
  #hero {
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 40px;
  }

  .hero-names {
    font-family: 'Great Vibes', cursive;
    font-size: clamp(4rem, 10vw, 9rem);
    background: linear-gradient(135deg, var(--rose), var(--gold), var(--lavender), var(--rose));
    background-size: 300% 300%;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: gradientShift 4s ease infinite, heroFadeIn 2s ease forwards;
    text-shadow: none;
    filter: drop-shadow(0 0 30px rgba(249,168,196,0.5));
    opacity: 0;
  }

  @keyframes gradientShift {
    0%,100%{background-position:0% 50%}
    50%{background-position:100% 50%}
  }

  @keyframes heroFadeIn {
    0%{opacity:0;transform:translateY(30px)}
    100%{opacity:1;transform:translateY(0)}
  }

  .hero-subtitle {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: clamp(1.2rem, 3vw, 2rem);
    color: var(--gold-light);
    margin-top: 16px;
    letter-spacing: 0.3em;
    opacity: 0;
    animation: heroFadeIn 2s ease 0.8s forwards;
  }

  .hero-scroll {
    position: absolute;
    bottom: 40px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    opacity: 0;
    animation: heroFadeIn 2s ease 2s forwards;
  }
  .hero-scroll span { font-size: 12px; letter-spacing: 0.3em; color: var(--rose); opacity: 0.7; }
  .scroll-arrow {
    width: 2px; height: 40px;
    background: linear-gradient(to bottom, var(--rose), transparent);
    animation: scrollPulse 2s ease-in-out infinite;
  }
  @keyframes scrollPulse { 0%,100%{opacity:1;transform:scaleY(1)} 50%{opacity:0.4;transform:scaleY(0.6)} }

  /* DIVIDER */
  .divider {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    padding: 40px 0;
    opacity: 0.6;
  }
  .divider-line { width: 100px; height: 1px; background: linear-gradient(to right, transparent, var(--rose)); }
  .divider-line.right { background: linear-gradient(to left, transparent, var(--rose)); }
  .divider-heart { color: var(--gold); font-size: 20px; animation: heartbeat 1.5s ease-in-out infinite; }
  @keyframes heartbeat { 0%,100%{transform:scale(1)} 50%{transform:scale(1.3)} }

  /* LOVE STORY */
  #story {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 100px 40px;
    background: linear-gradient(180deg, transparent, rgba(107,33,168,0.05), transparent);
  }

  .story-inner {
    max-width: 780px;
    text-align: center;
  }

  .section-label {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 14px;
    letter-spacing: 0.4em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 20px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.8s ease;
  }
  .section-label.visible { opacity: 1; transform: translateY(0); }

  .section-title {
    font-family: 'Great Vibes', cursive;
    font-size: clamp(3rem, 7vw, 5.5rem);
    color: var(--rose);
    filter: drop-shadow(0 0 20px rgba(249,168,196,0.4));
    margin-bottom: 40px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.8s ease 0.2s;
  }
  .section-title.visible { opacity: 1; transform: translateY(0); }

  #typewriter {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.1rem, 2.5vw, 1.5rem);
    line-height: 2;
    color: rgba(254,243,248,0.85);
    font-style: italic;
    min-height: 200px;
    opacity: 0;
    transition: opacity 0.5s;
  }
  #typewriter.visible { opacity: 1; }
  #cursor-blink {
    display: inline-block;
    width: 2px;
    height: 1.2em;
    background: var(--rose);
    animation: blink 1s step-end infinite;
    vertical-align: middle;
    margin-left: 2px;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* MEMORIES */
  #memories {
    min-height: 100vh;
    padding: 100px 40px;
    overflow: hidden;
    background: linear-gradient(180deg, transparent, rgba(249,168,196,0.03), transparent);
  }

  .memories-header { text-align: center; margin-bottom: 80px; }

  .frames-container {
    position: relative;
    width: 100%;
    height: 600px;
    perspective: 1000px;
  }

  .photo-frame {
    position: absolute;
    background: linear-gradient(135deg, rgba(249,168,196,0.1), rgba(216,180,254,0.1));
    border: 1px solid rgba(249,168,196,0.3);
    border-radius: 12px;
    padding: 20px;
    backdrop-filter: blur(10px);
    box-shadow: 0 8px 32px rgba(249,168,196,0.1), inset 0 1px 0 rgba(255,255,255,0.1);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: transform 0.3s, box-shadow 0.3s;
  }

  .photo-frame:hover {
    box-shadow: 0 20px 60px rgba(249,168,196,0.3), 0 0 40px rgba(245,200,66,0.2);
    z-index: 10;
  }

  .frame-emoji { font-size: 3rem; margin-bottom: 12px; }
  .frame-caption {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 14px;
    color: var(--rose);
    text-align: center;
    line-height: 1.5;
  }

  /* TIMELINE */
  #timeline {
    padding: 100px 40px;
    max-width: 900px;
    margin: 0 auto;
  }

  .timeline-track {
    position: relative;
    padding-left: 60px;
    margin-top: 60px;
  }

  .timeline-line {
    position: absolute;
    left: 20px;
    top: 0; bottom: 0;
    width: 2px;
    background: linear-gradient(to bottom, var(--rose), var(--lavender), var(--gold));
    box-shadow: 0 0 10px rgba(249,168,196,0.5);
  }

  .timeline-item {
    position: relative;
    margin-bottom: 60px;
    opacity: 0;
    transform: translateX(-20px);
    transition: all 0.7s ease;
  }
  .timeline-item.visible { opacity: 1; transform: translateX(0); }

  .timeline-dot {
    position: absolute;
    left: -48px;
    top: 8px;
    width: 16px; height: 16px;
    border-radius: 50%;
    background: var(--rose);
    box-shadow: 0 0 15px rgba(249,168,196,0.8);
    animation: dotPulse 2s ease-in-out infinite;
  }
  @keyframes dotPulse { 0%,100%{box-shadow:0 0 10px rgba(249,168,196,0.8)} 50%{box-shadow:0 0 25px rgba(249,168,196,1), 0 0 50px rgba(249,168,196,0.4)} }

  .timeline-date {
    font-size: 12px;
    letter-spacing: 0.3em;
    color: var(--gold);
    margin-bottom: 8px;
    text-transform: uppercase;
  }

  .timeline-text {
    font-size: clamp(1rem, 2vw, 1.25rem);
    line-height: 1.8;
    color: rgba(254,243,248,0.85);
    font-style: italic;
  }

  /* SECRET MESSAGE */
  #secret {
    min-height: 70vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 100px 40px;
    text-align: center;
  }

  #secretHeart {
    width: 120px; height: 120px;
    background: radial-gradient(circle, var(--deep-rose), var(--bg-dark));
    clip-path: polygon(50% 80%, 0% 35%, 25% 0%, 50% 20%, 75% 0%, 100% 35%);
    cursor: pointer;
    transition: all 0.4s;
    animation: secretPulse 2s ease-in-out infinite;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 40px;
    filter: drop-shadow(0 0 20px rgba(190,24,93,0.6));
  }

  /* Heart shape using unicode */
  .big-heart-btn {
    font-size: 100px;
    cursor: pointer;
    transition: all 0.4s;
    animation: secretPulse 2s ease-in-out infinite;
    display: block;
    margin-bottom: 20px;
    filter: drop-shadow(0 0 20px rgba(249,168,196,0.6));
    user-select: none;
  }
  .big-heart-btn:hover {
    transform: scale(1.15);
    filter: drop-shadow(0 0 40px rgba(249,168,196,1));
  }

  @keyframes secretPulse {
    0%,100%{transform:scale(1)} 50%{transform:scale(1.08)}
  }

  .secret-hint {
    font-size: 14px;
    letter-spacing: 0.3em;
    color: var(--rose);
    opacity: 0.7;
    text-transform: uppercase;
    margin-bottom: 40px;
  }

  #secretMessage {
    max-width: 640px;
    display: none;
    flex-direction: column;
    align-items: center;
    gap: 20px;
  }
  #secretMessage.revealed {
    display: flex;
    animation: secretReveal 1s ease forwards;
  }
  @keyframes secretReveal {
    0%{opacity:0;transform:scale(0.8) translateY(20px)}
    100%{opacity:1;transform:scale(1) translateY(0)}
  }

  .message-card {
    background: linear-gradient(135deg, rgba(249,168,196,0.08), rgba(216,180,254,0.08));
    border: 1px solid rgba(249,168,196,0.25);
    border-radius: 20px;
    padding: 40px;
    text-align: center;
    box-shadow: 0 0 60px rgba(249,168,196,0.1), inset 0 1px 0 rgba(255,255,255,0.05);
  }

  .message-text {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: clamp(1.1rem, 2.5vw, 1.5rem);
    line-height: 2;
    color: rgba(254,243,248,0.9);
  }

  .message-signature {
    font-family: 'Great Vibes', cursive;
    font-size: clamp(2rem, 5vw, 3.5rem);
    color: var(--rose);
    filter: drop-shadow(0 0 15px rgba(249,168,196,0.5));
    margin-top: 20px;
  }

  /* PROMISE */
  #promise {
    min-height: 80vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 100px 40px;
    text-align: center;
    background: radial-gradient(ellipse at center, rgba(107,33,168,0.08) 0%, transparent 70%);
  }

  .promise-text {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: clamp(1.5rem, 4vw, 3rem);
    line-height: 1.7;
    max-width: 820px;
    background: linear-gradient(135deg, var(--text-light), var(--rose), var(--gold-light));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    transform: translateY(30px);
    transition: all 1s ease;
  }
  .promise-text.visible { opacity: 1; transform: translateY(0); }

  .promise-glow {
    margin-top: 60px;
    width: 200px; height: 200px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(249,168,196,0.2), transparent);
    animation: glowPulse 3s ease-in-out infinite;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 80px;
  }
  @keyframes glowPulse {
    0%,100%{box-shadow:0 0 30px rgba(249,168,196,0.3)} 
    50%{box-shadow:0 0 80px rgba(249,168,196,0.6), 0 0 150px rgba(245,200,66,0.2)}
  }

  /* FOOTER */
  footer {
    padding: 80px 40px;
    text-align: center;
    position: relative;
    z-index: 10;
  }

  .footer-names {
    font-family: 'Great Vibes', cursive;
    font-size: clamp(2.5rem, 6vw, 5rem);
    color: var(--rose);
    opacity: 0.6;
    filter: drop-shadow(0 0 20px rgba(249,168,196,0.3));
  }

  .footer-sub {
    font-size: 13px;
    letter-spacing: 0.4em;
    color: rgba(254,243,248,0.3);
    margin-top: 20px;
    text-transform: uppercase;
  }

  /* SPARKLE */
  .sparkle {
    position: fixed;
    pointer-events: none;
    z-index: 9997;
    font-size: 16px;
    animation: sparkleAnim 0.8s ease forwards;
  }
  @keyframes sparkleAnim {
    0%{opacity:1;transform:translate(-50%,-50%) scale(0)}
    50%{opacity:1;transform:translate(-50%,-50%) scale(1.5)}
    100%{opacity:0;transform:translate(-50%,-120%) scale(0.5)}
  }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    .frames-container { height: auto; display: flex; flex-wrap: wrap; gap: 20px; }
    .photo-frame { position: relative !important; left: auto !important; top: auto !important; transform: none !important; width: calc(50% - 10px) !important; min-height: 150px; }
  }
</style>
</head>
<body>

<canvas id="heroCanvas"></canvas>
<div id="cursor"></div>

<button id="musicBtn" onclick="toggleMusic()">
  <span class="note">♪</span>
  <span id="musicLabel">Play Music</span>
</button>

<!-- HERO -->
<section id="hero">
  <div class="hero-names">Abram ❤️ Hanii</div>
  <div class="hero-subtitle">Forever & Always</div>
  <div class="hero-scroll">
    <span>Scroll to explore</span>
    <div class="scroll-arrow"></div>
  </div>
</section>

<!-- LOVE STORY -->
<section id="story">
  <div class="story-inner">
    <div class="section-label" data-reveal>— A Love Story —</div>
    <div class="section-title" data-reveal>Our Beginning</div>
    <div id="typewriter"></div>
  </div>
</section>

<div class="divider">
  <div class="divider-line"></div>
  <span class="divider-heart">♥</span>
  <div class="divider-line right"></div>
</div>

<!-- MEMORIES -->
<section id="memories">
  <div class="memories-header">
    <div class="section-label" data-reveal>— Captured in Time —</div>
    <div class="section-title" data-reveal>Our Memories</div>
  </div>
  <div class="frames-container" id="framesContainer"></div>
</section>

<div class="divider">
  <div class="divider-line"></div>
  <span class="divider-heart">♥</span>
  <div class="divider-line right"></div>
</div>

<!-- TIMELINE -->
<section id="timeline">
  <div style="text-align:center">
    <div class="section-label" data-reveal>— The Journey —</div>
    <div class="section-title" data-reveal>Special Moments</div>
  </div>
  <div class="timeline-track">
    <div class="timeline-line"></div>
    <div id="timelineItems"></div>
  </div>
</section>

<div class="divider">
  <div class="divider-line"></div>
  <span class="divider-heart">♥</span>
  <div class="divider-line right"></div>
</div>

<!-- SECRET MESSAGE -->
<section id="secret">
  <div class="section-label" data-reveal>— For Your Eyes Only —</div>
  <div class="section-title" data-reveal>A Secret For Hanii</div>
  <span class="big-heart-btn" id="secretHeartBtn" onclick="revealSecret(this)">💗</span>
  <p class="secret-hint">Click the heart to reveal...</p>
  <div id="secretMessage">
    <div class="message-card">
      <div class="message-text">
        My dearest Hanii,<br><br>
        From the very first moment I saw you, something shifted inside me — like the universe had finally decided to be kind. Every laugh we share, every quiet moment, every glance that says more than words ever could — it all means the world to me.<br><br>
        You are my favorite thought in every morning and my warmest feeling every night. In you, I found not just love, but a home — a feeling of belonging I never knew I was searching for.<br><br>
        I promise to hold your hand through every season, to be your safe place in every storm, and to love you in ways that grow deeper with every passing day.
      </div>
      <div class="message-signature">Always yours, Abram ♥</div>
    </div>
  </div>
</section>

<div class="divider">
  <div class="divider-line"></div>
  <span class="divider-heart">♥</span>
  <div class="divider-line right"></div>
</div>

<!-- PROMISE -->
<section id="promise">
  <div class="section-label" data-reveal>— My Vow —</div>
  <div class="promise-text" data-reveal>
    "I will always be with you, Hanii.<br>
    Through every sunrise and every storm,<br>
    through laughter and through tears —<br>
    you are the reason I believe in forever."
  </div>
  <div class="promise-glow">💫</div>
</section>

<footer>
  <div class="footer-names">Abram & Hanii</div>
  <div class="footer-sub">Written in the stars ✦ Forever & Always</div>
</footer>

<script>
// ─────────────────────────────────
// CUSTOM CURSOR
// ─────────────────────────────────
const cursor = document.getElementById('cursor');
const trails = ['♥', '✦', '·', '♡', '✿'];
let lastTrail = 0;

document.addEventListener('mousemove', (e) => {
  cursor.style.left = e.clientX + 'px';
  cursor.style.top = e.clientY + 'px';

  const now = Date.now();
  if (now - lastTrail > 120) {
    lastTrail = now;
    const t = document.createElement('div');
    t.className = 'cursor-trail';
    t.textContent = trails[Math.floor(Math.random() * trails.length)];
    t.style.left = e.clientX + 'px';
    t.style.top = e.clientY + 'px';
    t.style.color = Math.random() > 0.5 ? '#f9a8c4' : '#f5c842';
    document.body.appendChild(t);
    setTimeout(() => t.remove(), 1000);
  }
});

// ─────────────────────────────────
// CANVAS — floating hearts + particles
// ─────────────────────────────────
const canvas = document.getElementById('heroCanvas');
const ctx = canvas.getContext('2d');
let W, H, particles = [], hearts = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

// Particles
for (let i = 0; i < 120; i++) {
  particles.push({
    x: Math.random() * W, y: Math.random() * H,
    vx: (Math.random() - 0.5) * 0.3,
    vy: -Math.random() * 0.4 - 0.1,
    r: Math.random() * 2 + 0.5,
    alpha: Math.random() * 0.5 + 0.1,
    color: Math.random() > 0.5 ? '#f9a8c4' : '#f5c842'
  });
}

// Hearts
function createHeart(x, y, size, speed) {
  return {
    x: x ?? Math.random() * W,
    y: y ?? H + 20,
    size: size ?? Math.random() * 14 + 6,
    vx: (Math.random() - 0.5) * 0.5,
    vy: speed ?? -(Math.random() * 0.8 + 0.3),
    alpha: Math.random() * 0.4 + 0.15,
    wobble: Math.random() * Math.PI * 2,
    wobbleSpeed: (Math.random() - 0.5) * 0.03,
    rotation: (Math.random() - 0.5) * 0.3
  };
}

for (let i = 0; i < 25; i++) {
  hearts.push(createHeart(Math.random() * W, Math.random() * H));
}

function drawHeart(ctx, x, y, size, alpha, rotation) {
  ctx.save();
  ctx.translate(x, y);
  ctx.rotate(rotation);
  ctx.globalAlpha = alpha;
  ctx.fillStyle = '#f9a8c4';
  ctx.shadowBlur = 15;
  ctx.shadowColor = '#f9a8c4';
  ctx.beginPath();
  const s = size / 2;
  ctx.moveTo(0, s * 0.4);
  ctx.bezierCurveTo(-s * 1.2, -s * 0.5, -s * 2, s * 0.6, 0, s * 1.5);
  ctx.bezierCurveTo(s * 2, s * 0.6, s * 1.2, -s * 0.5, 0, s * 0.4);
  ctx.fill();
  ctx.restore();
}

function animate() {
  ctx.clearRect(0, 0, W, H);

  // Particles
  for (let p of particles) {
    ctx.save();
    ctx.globalAlpha = p.alpha;
    ctx.fillStyle = p.color;
    ctx.shadowBlur = 8;
    ctx.shadowColor = p.color;
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fill();
    ctx.restore();
    p.x += p.vx; p.y += p.vy;
    if (p.y < -5) { p.y = H + 5; p.x = Math.random() * W; }
    if (p.x < 0 || p.x > W) p.vx *= -1;
  }

  // Hearts
  for (let h of hearts) {
    h.wobble += h.wobbleSpeed;
    h.x += h.vx + Math.sin(h.wobble) * 0.3;
    h.y += h.vy;
    if (h.y < -30) {
      h.y = H + 20;
      h.x = Math.random() * W;
      h.alpha = Math.random() * 0.4 + 0.1;
    }
    drawHeart(ctx, h.x, h.y, h.size, h.alpha, h.rotation);
  }

  requestAnimationFrame(animate);
}
animate();

// Click sparkles
document.addEventListener('click', (e) => {
  for (let i = 0; i < 8; i++) {
    const spark = document.createElement('div');
    spark.className = 'sparkle';
    const icons = ['✦','♥','✿','★','·','♡'];
    spark.textContent = icons[Math.floor(Math.random() * icons.length)];
    spark.style.left = (e.clientX + (Math.random()-0.5)*60) + 'px';
    spark.style.top = (e.clientY + (Math.random()-0.5)*60) + 'px';
    spark.style.color = Math.random()>0.5 ? '#f9a8c4' : '#f5c842';
    spark.style.animationDuration = (Math.random()*0.5+0.5) + 's';
    document.body.appendChild(spark);
    setTimeout(() => spark.remove(), 900);
  }
});

// ─────────────────────────────────
// SCROLL REVEAL
// ─────────────────────────────────
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('visible');
  });
}, { threshold: 0.2 });

document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el));

// Promise text
const promiseObs = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.3 });
document.querySelectorAll('.promise-text').forEach(el => promiseObs.observe(el));

// ─────────────────────────────────
// TYPEWRITER
// ─────────────────────────────────
const storyText = `There are moments in life so quietly perfect that you don't realize they're changing you — until you look back and see the person you've become. For Abram, one of those moments was meeting Hanii.

It wasn't dramatic. It was soft — like the first light of morning slipping through curtains, warm and unhurried. And somehow, from that gentleness, grew the most beautiful love he had ever known.

Hanii became his favorite chapter in a story he never expected to write — the reason he smiles at his phone, the name that plays on repeat in his quietest thoughts, the person who makes ordinary moments feel like magic.`;

const typeEl = document.getElementById('typewriter');
let typeStarted = false;

const typeObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting && !typeStarted) {
      typeStarted = true;
      typeEl.classList.add('visible');
      startTyping();
    }
  });
}, { threshold: 0.3 });
typeObs.observe(typeEl);

function startTyping() {
  let i = 0;
  const cursorEl = document.createElement('span');
  cursorEl.id = 'cursor-blink';
  typeEl.appendChild(cursorEl);

  const interval = setInterval(() => {
    if (i < storyText.length) {
      const ch = storyText[i];
      if (ch === '\n') {
        cursorEl.before(document.createElement('br'));
        if (storyText[i+1] === '\n') {
          cursorEl.before(document.createElement('br'));
          i++;
        }
      } else {
        const span = document.createElement('span');
        span.textContent = ch;
        cursorEl.before(span);
      }
      i++;
    } else {
      clearInterval(interval);
      setTimeout(() => cursorEl.remove(), 2000);
    }
  }, 28);
}

// ─────────────────────────────────
// MEMORIES FRAMES
// ─────────────────────────────────
const memories = [
  { emoji: '🌅', caption: 'The morning we decided\nto be together', top: '5%', left: '5%', w: 180, h: 200, delay: 0 },
  { emoji: '☕', caption: 'Coffee & conversations\nthat lasted forever', top: '10%', left: '30%', w: 160, h: 180, delay: 0.5 },
  { emoji: '🌙', caption: 'Late nights and\nsoft laughter', top: '2%', left: '55%', w: 195, h: 210, delay: 1 },
  { emoji: '🌸', caption: 'Spring walks and\nshared dreams', top: '40%', left: '10%', w: 175, h: 190, delay: 1.5 },
  { emoji: '🎵', caption: 'The song that became\nours forever', top: '45%', left: '38%', w: 185, h: 200, delay: 2 },
  { emoji: '✨', caption: 'Every moment with you\nfelt like magic', top: '38%', left: '65%', w: 170, h: 185, delay: 2.5 },
];

const fc = document.getElementById('framesContainer');
memories.forEach((m, i) => {
  const div = document.createElement('div');
  div.className = 'photo-frame';
  div.style.cssText = `top:${m.top};left:${m.left};width:${m.w}px;min-height:${m.h}px;transition-delay:${m.delay}s;`;
  div.innerHTML = `<div class="frame-emoji">${m.emoji}</div><div class="frame-caption">${m.caption}</div>`;

  // Gentle float
  let angle = Math.random() * Math.PI * 2;
  const speed = 0.003 + Math.random() * 0.002;
  const ampX = 5 + Math.random() * 8;
  const ampY = 4 + Math.random() * 6;
  const baseTop = parseFloat(m.top);
  const baseLeft = parseFloat(m.left);

  function floatFrame() {
    angle += speed;
    div.style.transform = `translate(${Math.sin(angle)*ampX}px, ${Math.cos(angle)*ampY}px) rotate(${Math.sin(angle)*1.5}deg)`;
    requestAnimationFrame(floatFrame);
  }
  floatFrame();

  fc.appendChild(div);
});

// ─────────────────────────────────
// TIMELINE
// ─────────────────────────────────
const moments = [
  { date: 'The First Meeting', text: 'Two souls crossed paths in the most unexpected way — and the world quietly rearranged itself.' },
  { date: 'First Conversation', text: 'Words flowed like they had always known each other. Hours passed like minutes.' },
  { date: 'The First Smile', text: 'Hanii smiled, and Abram knew — something had permanently changed inside him.' },
  { date: 'Our First Adventure', text: 'A simple walk turned into a map of memories neither wanted to forget.' },
  { date: 'I Love You', text: 'Three words that changed everything. Spoken softly, felt deeply, meant entirely.' },
  { date: 'Forever Begins', text: 'No longer two separate stories — one beautiful chapter, written together.' },
];

const tl = document.getElementById('timelineItems');
moments.forEach((m, i) => {
  const div = document.createElement('div');
  div.className = 'timeline-item';
  div.setAttribute('data-reveal', '');
  div.innerHTML = `
    <div class="timeline-dot"></div>
    <div class="timeline-date">${m.date}</div>
    <div class="timeline-text">${m.text}</div>
  `;
  div.style.transitionDelay = (i * 0.15) + 's';
  observer.observe(div);
  tl.appendChild(div);
});

// ─────────────────────────────────
// SECRET REVEAL
// ─────────────────────────────────
let secretRevealed = false;
function revealSecret(btn) {
  if (secretRevealed) return;
  secretRevealed = true;
  btn.style.animation = 'none';
  btn.style.transform = 'scale(1.4)';
  btn.style.filter = 'drop-shadow(0 0 60px rgba(249,168,196,1))';

  // Heart explosion
  for (let i = 0; i < 20; i++) {
    setTimeout(() => {
      const rect = btn.getBoundingClientRect();
      const spark = document.createElement('div');
      spark.className = 'sparkle';
      spark.textContent = '♥';
      spark.style.left = (rect.left + rect.width/2 + (Math.random()-0.5)*120) + 'px';
      spark.style.top = (rect.top + rect.height/2 + (Math.random()-0.5)*120) + 'px';
      spark.style.color = Math.random()>0.5 ? '#f9a8c4' : '#d8b4fe';
      spark.style.fontSize = (Math.random()*20+12) + 'px';
      document.body.appendChild(spark);
      setTimeout(() => spark.remove(), 900);
    }, i * 60);
  }

  setTimeout(() => {
    btn.style.display = 'none';
    document.querySelector('.secret-hint').style.display = 'none';
    document.getElementById('secretMessage').classList.add('revealed');
  }, 800);
}

// ─────────────────────────────────
// MUSIC
// ─────────────────────────────────
let audioCtx = null, musicPlaying = false;
let oscillators = [];

function createRomanticTone() {
  audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  const master = audioCtx.createGain();
  master.gain.setValueAtTime(0.06, audioCtx.currentTime);
  master.connect(audioCtx.destination);

  // Simple ambient chord
  const freqs = [261.63, 329.63, 392.00, 523.25, 659.25];
  const osc = freqs.map(f => {
    const o = audioCtx.createOscillator();
    const g = audioCtx.createGain();
    o.type = 'sine';
    o.frequency.setValueAtTime(f, audioCtx.currentTime);
    g.gain.setValueAtTime(0.015, audioCtx.currentTime);
    o.connect(g);
    g.connect(master);
    o.start();
    return { o, g };
  });

  // Gentle melody
  const melodyFreqs = [523.25, 587.33, 659.25, 783.99, 880, 783.99, 659.25, 587.33];
  let noteIdx = 0;
  function playNote() {
    if (!musicPlaying) return;
    const o = audioCtx.createOscillator();
    const g = audioCtx.createGain();
    o.type = 'sine';
    o.frequency.setValueAtTime(melodyFreqs[noteIdx % melodyFreqs.length], audioCtx.currentTime);
    g.gain.setValueAtTime(0.035, audioCtx.currentTime);
    g.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 1.8);
    o.connect(g);
    g.connect(master);
    o.start();
    o.stop(audioCtx.currentTime + 2);
    noteIdx++;
    setTimeout(playNote, 1400);
  }
  playNote();

  oscillators = osc;
}

function toggleMusic() {
  if (!musicPlaying) {
    musicPlaying = true;
    createRomanticTone();
    document.getElementById('musicLabel').textContent = 'Pause Music';
    document.querySelector('#musicBtn .note').style.animation = 'noteFloat 0.5s ease-in-out infinite';
  } else {
    musicPlaying = false;
    if (audioCtx) { audioCtx.close(); audioCtx = null; oscillators = []; }
    document.getElementById('musicLabel').textContent = 'Play Music';
  }
}
</script>
</body>
</html>
