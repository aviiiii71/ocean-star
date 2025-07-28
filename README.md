<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>For You, My Love 💌</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Dancing Script', cursive;
      background: linear-gradient(to bottom right, #ffe6f0, #e6f7ff);
      overflow-x: hidden;
    }

    .entrance {
      position: fixed;
      width: 100%;
      height: 100%;
      background: #fff;
      z-index: 10;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      animation: fadeIn 1s ease-in-out;
    }

    .entrance button {
      font-size: 24px;
      padding: 12px 24px;
      border: none;
      background: #ff99cc;
      color: white;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    h1 {
      color: #cc3366;
      margin-bottom: 20px;
    }

    .container {
      padding: 60px 20px;
      display: none;
    }

    .envelopes {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
    }

    .envelope {
      width: 200px;
      height: 140px;
      position: relative;
      cursor: pointer;
      perspective: 1000px;
    }

    .flap {
      position: absolute;
      top: 0;
      left: 0;
      width: 0;
      height: 0;
      border-left: 100px solid transparent;
      border-right: 100px solid transparent;
      border-bottom: 70px solid #ffb6c1;
      transform-origin: top;
      transition: transform 0.6s ease;
      z-index: 2;
    }

    .body {
      position: absolute;
      top: 35px;
      width: 200px;
      height: 105px;
      background: #fff0f5;
      border: 2px solid #ffb6c1;
      border-radius: 0 0 10px 10px;
      z-index: 1;
      overflow: hidden;
      text-align: center;
      padding: 10px;
      box-sizing: border-box;
      font-size: 14px;
    }

    .envelope.open .flap {
      transform: rotateX(-160deg);
    }

    .kiss {
      position: absolute;
      top: 50%;
      left: 50%;
      font-size: 28px;
      transform: translate(-50%, -50%) scale(0);
      animation: kissPop 1s forwards;
      z-index: 10;
    }

    .sparkle {
      position: absolute;
      width: 6px;
      height: 6px;
      background: gold;
      border-radius: 50%;
      animation: sparkleAnim 1.5s ease-out forwards;
      pointer-events: none;
      z-index: 5;
      opacity: 0.8;
      box-shadow: 0 0 6px 2px gold;
    }

    @keyframes sparkleAnim {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-60px) scale(0.2); opacity: 0; }
    }

    @keyframes kissPop {
      0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
      50% { transform: translate(-50%, -80%) scale(1.5); opacity: 1; }
      100% { transform: translate(-50%, -120%) scale(0.5); opacity: 0; }
    }

    @keyframes fadeIn {
      from { opacity: 0 }
      to { opacity: 1 }
    }

    .cat {
      position: absolute;
      bottom: 0;
      left: -200px;
      width: 120px;
      animation: moveCat 20s linear infinite;
      z-index: 1;
    }

    @keyframes moveCat {
      0% { left: -200px; transform: scaleX(1); }
      50% { left: 100%; transform: scaleX(1); }
      51% { transform: scaleX(-1); }
      100% { left: -200px; transform: scaleX(-1); }
    }

    .message-title {
      font-size: 18px;
      color: #cc3366;
      font-weight: bold;
      margin-bottom: 10px;
    }

    .message-text {
      font-size: 14px;
      color: #444;
      white-space: pre-wrap;
      min-height: 40px;
    }

    @media(max-width: 600px) {
      .envelope {
        transform: scale(0.9);
      }
    }
  </style>
</head>
<body>

  <div class="entrance">
    <h1>💌 For My Jaana</h1>
    <p style="font-size:18px;color:#888;margin-bottom:30px;">A collection of letters, just for your heart</p>
    <button onclick="startExperience()">Tap to Begin</button>
  </div>

  <div class="container">
    <h1>Open When...</h1>
    <div class="envelopes" id="envelopes"></div>
  </div>

  <img src="https://i.ibb.co/yRgy03k/blue-persian-cat.png" class="cat" alt="cat" />

  <script>
    const messages = [
      { title: "You miss me", text: "Jaana, when you miss me, just know I miss you more. Close your eyes and feel my warmth." },
      { title: "You're sad", text: "I'm holding your heart gently from afar. Cry if you must, but never forget my love surrounds you." },
      { title: "You're stressed", text: "Take a breath. Let go. You're strong, soft, and seen. I’m so proud of your soul." },
      { title: "You're alone", text: "You're not alone. My love is a quiet presence holding you always, even in silence." },
      { title: "You need strength", text: "You are made of galaxies and fire. Remember who you are, my warrior queen." },
      { title: "You're angry at me", text: "I’m sorry if I hurt you. It was never from lack of love — only distance and ache." },
      { title: "You remember us", text: "Rooftops. Our kiss. That cafe. Every second lives in me. You’re still my magic." },
      { title: "You can't sleep", text: "Imagine my arms wrapped around you. My fingers on your back. Sleep now, meri jaan." },
      { title: "You need to smile", text: "Your smile is heaven. Let this silly message or memory bring it back. 😊" },
      { title: "You need love", text: "This is it. The whole of my love, wrapped in words and stars. Yours. Forever." }
    ];

    function startExperience() {
      document.querySelector('.entrance').style.display = 'none';
      document.querySelector('.container').style.display = 'block';
    }

    function typeWriter(text, el, i = 0) {
      if (i < text.length) {
        el.innerHTML += text.charAt(i);
        setTimeout(() => typeWriter(text, el, i + 1), 35);
      }
    }

    const envelopeContainer = document.getElementById('envelopes');

    messages.forEach((msg, index) => {
      const envelope = document.createElement('div');
      envelope.className = 'envelope';
      envelope.innerHTML = `
        <div class="flap"></div>
        <div class="body">
          <div class="message-title">${msg.title}</div>
          <div class="message-text" id="msg-${index}"></div>
        </div>`;
      envelope.addEventListener('click', () => {
        if (!envelope.classList.contains('open')) {
          envelope.classList.add('open');
          const textEl = document.getElementById(`msg-${index}`);
          typeWriter(msg.text, textEl);

          const kiss = document.createElement('div');
          kiss.className = 'kiss';
          kiss.innerHTML = '💋';
          envelope.appendChild(kiss);
          setTimeout(() => kiss.remove(), 2000);

          for (let i = 0; i < 8; i++) {
            const sparkle = document.createElement('div');
            sparkle.className = 'sparkle';
            sparkle.style.left = `${Math.random() * 100}%`;
            sparkle.style.top = `${Math.random() * 100}%`;
            envelope.appendChild(sparkle);
            setTimeout(() => sparkle.remove(), 1500);
          }
        }
      });
      envelopeContainer.appendChild(envelope);
    });
  </script>

</body>
</html>
