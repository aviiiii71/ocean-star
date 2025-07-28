<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>For My Jaana 💌</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display&family=Dancing+Script&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #fff8f4;
      font-family: 'Playfair Display', serif;
      overflow-x: hidden;
      position: relative;
    }

    .cat-container {
      position: fixed;
      bottom: 20px;
      left: 20px;
      z-index: 0;
      opacity: 0.5;
      animation: float 6s ease-in-out infinite;
    }

    .cat-container img {
      width: 160px;
      height: auto;
      filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));
    }

    @keyframes float {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-15px); }
      100% { transform: translateY(0px); }
    }

    .entrance {
      position: fixed;
      width: 100%;
      height: 100vh;
      background: linear-gradient(to bottom right, #fbd3e9, #bbd2c5);
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      z-index: 10;
      transition: opacity 1s ease;
    }

    .entrance h1 {
      font-family: 'Dancing Script', cursive;
      font-size: 2.5rem;
      color: #5a2a54;
      margin-bottom: 20px;
    }

    .entrance button {
      padding: 12px 24px;
      font-size: 1rem;
      border: none;
      border-radius: 8px;
      background: #fff;
      color: #5a2a54;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      transition: background 0.3s ease;
    }

    .entrance button:hover {
      background: #ffe5f1;
    }

    .container {
      display: none;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
      padding: 40px;
      position: relative;
      z-index: 1;
    }

    .envelope-wrapper {
      perspective: 1200px;
    }

    .envelope {
      width: 280px;
      height: 180px;
      position: relative;
      transform-style: preserve-3d;
      transition: transform 1s;
      cursor: pointer;
    }

    .envelope.open {
      transform: rotateY(180deg);
    }

    .envelope-front, .envelope-back {
      position: absolute;
      width: 100%;
      height: 100%;
      border-radius: 12px;
      backface-visibility: hidden;
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
    }

    .envelope-front {
      background: linear-gradient(to bottom right, #fbd3e9, #bbd2c5);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.4rem;
      font-weight: bold;
      color: #5a2a54;
      font-family: 'Dancing Script', cursive;
      padding: 10px;
      text-align: center;
    }

    .envelope-back {
      background: #fff;
      transform: rotateY(180deg);
      padding: 20px;
      font-size: 1rem;
      color: #333;
      line-height: 1.6;
      border: 2px solid #f7cce3;
      box-sizing: border-box;
    }

    .envelope-back p {
      margin: 0;
      font-family: 'Playfair Display', serif;
    }

    @media (max-width: 768px) {
      .container {
        flex-direction: column;
        align-items: center;
      }

      .cat-container {
        bottom: 10px;
        left: 50%;
        transform: translateX(-50%);
      }
    }
  </style>
</head>
<body>

<!-- Floating Persian Cat -->
<div class="cat-container">
  <img src="https://i.ibb.co/qmKPnPr/blue-cat.png" alt="Cute Persian Cat">
</div>

<!-- Entrance Screen -->
<div class="entrance" id="entrance">
  <h1>For My Jaana 💌</h1>
  <button onclick="startExperience()">Tap to Begin</button>
</div>

<!-- Envelope Container -->
<div class="container" id="envelopes">

  <!-- Envelope 1 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You miss me</div>
      <div class="envelope-back">
        <p>Jaana, when you're missing me, just remember: my arms miss you more. I carry the scent of your kurta, the warmth of our first date, and every moment with you in my heartbeat. I am always close, even when we’re far.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 2 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You're sad</div>
      <div class="envelope-back">
        <p>When you're sad, I wish I could hold your hand and wipe away your tears. You are not alone. Your star above the ocean is still watching, still shining, still loving. This pain will pass, but my love won't.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 3 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You're stressed</div>
      <div class="envelope-back">
        <p>Take a deep breath, my love. Close your eyes and imagine my hands holding your cheeks gently. You’ve faced so much already, and you've made it through. I’m proud of you. Always.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 4 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You feel alone</div>
      <div class="envelope-back">
        <p>Aloneness is just an illusion. In every room you enter, my love follows. Even when I’m not beside you, my thoughts stay wrapped around you like a soft whisper. You are never truly alone, Jaana.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 5 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You need strength</div>
      <div class="envelope-back">
        <p>Look how far you’ve come, my brave girl. You have survived every battle. If ever you doubt yourself, know this — I believe in you more than I’ve ever believed in anything. You are my warrior wrapped in softness.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 6 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You're angry at me</div>
      <div class="envelope-back">
        <p>If I ever hurt you, I’m deeply sorry. Never was it out of lack of love, only the ache of not being near you. I’ll always want to understand you more, love you better, and hold you through every storm.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 7 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You're remembering us</div>
      <div class="envelope-back">
        <p>Our first kiss watching <em>Laila Majnu</em>, our first beer on that rooftop, the smell of your kurta — it all lives in me. Those days weren’t just memories, they were magic. And they’ll return, stronger and brighter.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 8 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You can't sleep</div>
      <div class="envelope-back">
        <p>Close your eyes, Jaana. Imagine my heartbeat as your lullaby. My fingers tracing your back, my nose in your hair. You're safe. You’re loved. I’m right here, whispering: “Sleep tight, meri jaan.”</p>
      </div>
    </div>
  </div>

  <!-- Envelope 9 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You need to smile</div>
      <div class="envelope-back">
        <p>Remember that goofy face I made on the rooftop? Or when I wanted to buy the whole store for you? 😄 Jaana, your smile is the most powerful light I’ve known. Let me bring it back, again and again.</p>
      </div>
    </div>
  </div>

  <!-- Envelope 10 -->
  <div class="envelope-wrapper" onclick="this.querySelector('.envelope').classList.toggle('open')">
    <div class="envelope">
      <div class="envelope-front">You need love</div>
      <div class="envelope-back">
        <p>This is where my words end and my heart speaks. You are my only jaan. The ocean may be wide, the night may be long — but your star still shines, always waiting, always yours. 💖</p>
      </div>
    </div>
  </div>
</div>

<script>
  function startExperience() {
    const entrance = document.getElementById('entrance');
    const envelopes = document.getElementById('envelopes');
    entrance.style.opacity = '0';
    setTimeout(() => {
      entrance.style.display = 'none';
      envelopes.style.display = 'flex';
    }, 1000);
  }
</script>

</body>
</html>
