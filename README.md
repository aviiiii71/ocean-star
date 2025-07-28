<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For You 💌</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom right, #ffe6f0, #f9f0ff);
      font-family: 'Segoe UI', sans-serif;
      overflow-x: hidden;
    }

    h1 {
      text-align: center;
      margin-top: 40px;
      font-size: 2.5em;
      color: #cc3366;
    }

    .envelope-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 30px;
      gap: 30px;
    }

    .envelope-container {
      position: relative;
      width: 200px;
      height: 140px;
      cursor: pointer;
      perspective: 1000px;
    }

    .envelope {
      position: relative;
      width: 100%;
      height: 100%;
      background: #ff99aa;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      overflow: hidden;
      transition: transform 0.8s ease;
    }

    .envelope:before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 50%;
      background: #ffccd5;
      transform: rotateX(0deg);
      transform-origin: top;
      transition: transform 1s ease;
      z-index: 2;
    }

    .envelope.open:before {
      transform: rotateX(-140deg);
    }

    .message {
      opacity: 0;
      padding: 15px;
      background: #fff;
      height: 100%;
      font-size: 14px;
      line-height: 1.5;
      color: #333;
      overflow: hidden;
      z-index: 1;
      position: relative;
      border-radius: 10px;
    }

    .envelope.open .message {
      animation: typewriter 3s steps(80, end) 1 forwards;
    }

    @keyframes typewriter {
      from { opacity: 1; width: 0; }
      to { opacity: 1; width: 100%; }
    }

    .sparkles {
      position: fixed;
      top: 0;
      left: 0;
      pointer-events: none;
      width: 100vw;
      height: 100vh;
      z-index: 999;
    }

    .sparkle {
      position: absolute;
      width: 8px;
      height: 8px;
      background: pink;
      border-radius: 50%;
      animation: sparkle 2s infinite;
    }

    @keyframes sparkle {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(100px) scale(0); opacity: 0; }
    }

    .cat {
      position: fixed;
      bottom: 10px;
      left: -200px;
      width: 150px;
      animation: catWalk 20s linear infinite;
      z-index: 5;
    }

    @keyframes catWalk {
      0% { left: -200px; }
      50% { left: 100vw; }
      100% { left: -200px; }
    }

    audio {
      display: none;
    }
  </style>
</head>
<body>
  <h1>Open When... 💌</h1>

  <div class="envelope-grid">
    <div class="envelope-container" onclick="openEnvelope(this, 0)">
      <div class="envelope">
        <div class="message">When you're missing me, know this: I miss you more, I feel you more, I love you more than words can say. 💖</div>
      </div>
    </div>
    <div class="envelope-container" onclick="openEnvelope(this, 1)">
      <div class="envelope">
        <div class="message">When you're sad, remember my hugs are wrapped in this message. You are my sunshine, even on cloudy days. 🌧️☀️</div>
      </div>
    </div>
    <div class="envelope-container" onclick="openEnvelope(this, 2)">
      <div class="envelope">
        <div class="message">When you're scared, feel my arms holding you from afar. You are never alone, jaan. 🌙</div>
      </div>
    </div>
    <!-- Add more envelopes here similarly -->
  </div>

  <div class="sparkles" id="sparkles"></div>
  <img src="https://cdn.pixabay.com/photo/2023/04/09/21/21/cat-7911825_1280.png" class="cat" />
  <audio autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2023/03/15/audio_51e3c989d3.mp3?filename=romantic-piano-144998.mp3" type="audio/mpeg" />
  </audio>

  <script>
    function openEnvelope(el, i) {
      if (el.classList.contains('opened')) return;
      el.classList.add('opened');
      const env = el.querySelector('.envelope');
      env.classList.add('open');
      createKiss(env);
    }

    function createKiss(parent) {
      const kiss = document.createElement('div');
      kiss.innerHTML = '💋';
      kiss.style.position = 'absolute';
      kiss.style.fontSize = '24px';
      kiss.style.left = '50%';
      kiss.style.top = '50%';
      kiss.style.transform = 'translate(-50%, -50%)';
      kiss.style.opacity = '0';
      kiss.style.transition = 'all 2s ease';
      parent.appendChild(kiss);
      setTimeout(() => {
        kiss.style.top = '-50px';
        kiss.style.opacity = '1';
      }, 10);
      setTimeout(() => parent.removeChild(kiss), 3000);
    }

    function generateSparkles() {
      const sparkleArea = document.getElementById('sparkles');
      for (let i = 0; i < 40; i++) {
        const s = document.createElement('div');
        s.className = 'sparkle';
        s.style.left = Math.random() * 100 + 'vw';
        s.style.top = Math.random() * 100 + 'vh';
        s.style.animationDelay = (Math.random() * 3) + 's';
        sparkleArea.appendChild(s);
      }
    }

    generateSparkles();
  </script>
</body>
</html>
