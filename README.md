<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Open When... 💌</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #fff1f5, #fef6f9);
      overflow-x: hidden;
    }

    .entrance {
      position: fixed;
      z-index: 999;
      background: linear-gradient(to right, #ffdde1, #ee9ca7);
      width: 100%;
      height: 100vh;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      text-align: center;
    }

    .entrance h1 {
      font-size: 3em;
      margin-bottom: 10px;
    }

    .entrance button {
      padding: 15px 30px;
      font-size: 1.2em;
      background: white;
      color: #cc3366;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.3s;
    }

    .entrance button:hover {
      background: #ffe6ec;
    }

    .container {
      display: none;
      padding: 30px 20px 80px;
      text-align: center;
    }

    .container h1 {
      font-size: 2.5em;
      color: #cc3366;
    }

    .subtitle {
      font-style: italic;
      margin-bottom: 40px;
      color: #555;
    }

    .envelopes {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 25px;
    }

    .envelope {
      width: 200px;
      height: 150px;
      position: relative;
      perspective: 1000px;
      cursor: pointer;
    }

    .envelope-inner {
      width: 100%;
      height: 100%;
      position: relative;
      transition: transform 1s;
      transform-style: preserve-3d;
    }

    .envelope.opened .envelope-inner {
      transform: rotateX(180deg);
    }

    .front, .back {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
      box-sizing: border-box;
      font-size: 15px;
    }

    .front {
      background: #f9b3c2;
      color: white;
      font-weight: bold;
    }

    .back {
      background: white;
      transform: rotateX(180deg);
      color: #333;
      line-height: 1.4;
      overflow-y: auto;
    }

    /* Cat animation */
    .cat {
      position: fixed;
      width: 100px;
      bottom: 20px;
      left: -120px;
      z-index: 1;
      animation: moveCat 20s linear infinite;
    }

    @keyframes moveCat {
      0% { left: -120px; transform: scaleX(1); }
      50% { left: calc(100% + 120px); transform: scaleX(1); }
      50.01% { transform: scaleX(-1); }
      100% { left: -120px; transform: scaleX(-1); }
    }

    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: pink;
      border-radius: 50%;
      animation: floatHeart 5s infinite ease-in-out;
      z-index: 0;
    }

    @keyframes floatHeart {
      0% {
        opacity: 0;
        transform: translateY(0) scale(1);
      }
      25% {
        opacity: 1;
        transform: translateY(-50px) scale(1.2);
      }
      100% {
        opacity: 0;
        transform: translateY(-200px) scale(0.8);
      }
    }

    @media (max-width: 600px) {
      .envelope {
        width: 90%;
        height: 140px;
      }

      .cat {
        width: 70px;
      }
    }
  </style>
</head>
<body>

  <!-- Entrance screen -->
  <div class="entrance" id="entrance">
    <h1>Hi Jaana 💖</h1>
    <p>Tap below to open the envelopes of my heart</p>
    <button onclick="enterLove()">Open Love Letters 💌</button>
  </div>

  <!-- Main content -->
  <div class="container" id="container">
    <h1>Open When...</h1>
    <p class="subtitle">Click any envelope to read my heart 💌</p>

    <div class="envelopes">
      <!-- Repeat for 10 envelopes -->
      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You miss me</div>
          <div class="back">When you're missing me, remember: my arms miss you more. I’m always with you, Jaana.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You're sad</div>
          <div class="back">If you're sad, I wish I could hold you. My love is a blanket you can always wrap in.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You're stressed</div>
          <div class="back">Close your eyes. Breathe. Let my voice guide you. You’ve got this, meri jaan.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You feel alone</div>
          <div class="back">Even when you're alone, my love surrounds you. Always with you, in every breath.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You need strength</div>
          <div class="back">You are my strong girl. My warrior. You carry galaxies in your soul.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You're angry at me</div>
          <div class="back">If I hurt you, I am sorry. Never out of lack of love — only out of longing. Please forgive me.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You're remembering us</div>
          <div class="back">Our memories are not in the past. They are alive — and waiting to bloom again.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You can't sleep</div>
          <div class="back">Pretend my chest is your pillow. My heartbeat is your lullaby. Sleep, meri jaan.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You need to smile</div>
          <div class="back">Remember my silly faces? You laughed. You glowed. That light is still inside you.</div>
        </div>
      </div>

      <div class="envelope" onclick="this.classList.toggle('opened')">
        <div class="envelope-inner">
          <div class="front">You need love</div>
          <div class="back">This is it. My soul, poured into every word. You are my forever, my jaan.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Floating Cat -->
  <img src="https://i.imgur.com/HRzA6Cz.png" alt="Persian Cat" class="cat" />

  <!-- Floating hearts -->
  <script>
    function enterLove() {
      document.getElementById('entrance').style.display = 'none';
      document.getElementById('container').style.display = 'block';
    }

    // Generate floating hearts
    for (let i = 0; i < 30; i++) {
      let heart = document.createElement("div");
      heart.classList.add("heart");
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.top = Math.random() * 100 + "vh";
      heart.style.animationDuration = (3 + Math.random() * 2) + "s";
      document.body.appendChild(heart);
    }
  </script>
</body>
</html>
