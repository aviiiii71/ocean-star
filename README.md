<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>For You, My Love ❤️</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&family=Quicksand&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Quicksand', sans-serif;
      background: linear-gradient(to bottom right, #ffe6f0, #e6f7ff);
      overflow-x: hidden;
      position: relative;
    }

    .entrance {
      position: fixed;
      width: 100%;
      height: 100vh;
      background: #fff;
      z-index: 1000;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
    }

    .entrance button {
      font-size: 24px;
      padding: 14px 30px;
      background: #ff69b4;
      color: white;
      border: none;
      border-radius: 12px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      cursor: pointer;
      transition: background 0.3s;
    }
    .entrance button:hover {
      background: #ff1493;
    }

    .container {
      padding: 40px 10px;
      display: none;
      max-width: 1200px;
      margin: auto;
    }

    h1 {
      text-align: center;
      font-family: 'Dancing Script', cursive;
      font-size: 36px;
      color: #cc3366;
      margin-bottom: 40px;
    }

    .envelopes {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 30px;
      justify-content: center;
    }

    .envelope {
      perspective: 1200px;
      position: relative;
      cursor: pointer;
    }

    .flap {
      width: 100%;
      height: 0;
      padding-bottom: 60%;
      background: linear-gradient(to top right, #ffc0cb, #fff0f5);
      border-radius: 10px 10px 0 0;
      transform-origin: top;
      transition: transform 0.7s;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    .body {
      background: #fff;
      padding: 20px;
      border-radius: 0 0 15px 15px;
      border: 2px solid #ffb6c1;
      margin-top: -6px;
      overflow: hidden;
      min-height: 120px;
      text-align: center;
    }

    .envelope.open .flap {
      transform: rotateX(-160deg);
    }

    .message-title {
      font-size: 18px;
      font-weight: bold;
      color: #d63384;
      margin-bottom: 8px;
    }

    .message-text {
      font-size: 15px;
      color: #333;
      white-space: pre-wrap;
      min-height: 60px;
    }

    .kiss, .sparkle {
      position: absolute;
      pointer-events: none;
      animation: floatUp 1.5s ease-out forwards;
    }

    .kiss {
      font-size: 28px;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      opacity: 0;
    }

    .sparkle {
      width: 8px;
      height: 8px;
      background: gold;
      border-radius: 50%;
      opacity: 0.9;
      box-shadow: 0 0 6px 2px gold;
    }

    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-60px); opacity: 0; }
    }

    .cat {
      position: fixed;
      bottom: 0;
      left: -160px;
      width: 130px;
      animation: catWalk 25s linear infinite;
    }

    @keyframes catWalk {
      0% { left: -160px; transform: scaleX(1); }
      50% { left: 100vw; transform: scaleX(1); }
      50.1% { transform: scaleX(-1); }
      100% { left: -160px; transform: scaleX(-1); }
    }
  </style>
</head>
<body>

  <div class="entrance">
    <h1>My Letters to You ✨</h1>
    <p style="font-size:18px;color:#777;margin-bottom:30px;">Click to begin opening my heart</p>
    <button onclick="startExperience()">Start the Journey</button>
  </div>

  <div class="container">
    <h1>Choose a Letter to Open ✨</h1>
    <div class="envelopes" id="envelopes"></div>
  </div>

  <img src="https://i.ibb.co/yRgy03k/blue-persian-cat.png" class="cat" alt="cat">

  <script>
    const messages = [
      { title: "You miss me", text: "I miss you more, Jaana. Let this letter be my hug." },
      { title: "You're sad", text: "You're allowed to cry, but never forget: I love you deeply." },
      { title: "You're stressed", text: "Take this letter as your calm breath. I'm holding you." },
      { title: "You feel alone", text: "You're never alone. My soul is right beside yours." },
      { title: "You need strength", text: "You are strong and beautiful. You always rise." },
      { title: "You're angry at me", text: "I'm sorry. I'm here. I love you more than my ego." },
      { title: "You remember us", text: "Every moment with you is inked in my heart." },
      { title: "You can't sleep", text: "Close your eyes. I'm humming to you from afar." },
      { title: "You need to smile", text: "Smile, baby. It makes the stars blush." },
      { title: "You need love", text: "This message is soaked in all my love for you." }
    ];

    function startExperience() {
      document.querySelector('.entrance').style.display = 'none';
      document.querySelector('.container').style.display = 'block';
    }

    function typeWriter(text, element, i = 0) {
      if (i < text.length) {
        element.innerHTML += text.charAt(i);
        setTimeout(() => typeWriter(text, element, i + 1), 35);
      }
    }

    const container = document.getElementById('envelopes');
    messages.forEach((msg, idx) => {
      const env = document.createElement('div');
      env.className = 'envelope';
      env.innerHTML = `
        <div class="flap"></div>
        <div class="body">
          <div class="message-title">${msg.title}</div>
          <div class="message-text" id="msg-${idx}"></div>
        </div>`;
      env.addEventListener('click', () => {
        if (!env.classList.contains('open')) {
          env.classList.add('open');
          const el = document.getElementById(`msg-${idx}`);
          typeWriter(msg.text, el);
          
          const kiss = document.createElement('div');
          kiss.className = 'kiss';
          kiss.innerHTML = '💋';
          env.appendChild(kiss);
          kiss.style.top = '30%';
          kiss.style.left = '50%';
          kiss.style.opacity = 1;

          for (let i = 0; i < 7; i++) {
            const sp = document.createElement('div');
            sp.className = 'sparkle';
            sp.style.left = `${Math.random() * 90 + 5}%`;
            sp.style.top = `${Math.random() * 80 + 10}%`;
            env.appendChild(sp);
            setTimeout(() => sp.remove(), 1500);
          }
          setTimeout(() => kiss.remove(), 1500);
        }
      });
      container.appendChild(env);
    });
  </script>

</body>
</html>
