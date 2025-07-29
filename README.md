<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>From the Star Above the Ocean</title>
  <link href="https://fonts.googleapis.com/css2?family=Sacramento&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Sacramento', cursive;
      background: linear-gradient(to bottom, #fdeff9, #ec38bc);
      overflow-x: hidden;
    }

    .welcome {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      background-image: url('https://i.imgur.com/47F6yJ1.png');
      background-size: cover;
      background-position: center;
    }

    .welcome h1 {
      font-size: 3em;
      color: #fff;
      text-shadow: 2px 2px 4px #000;
      margin-bottom: 20px;
    }

    .begin-btn {
      font-size: 1.5em;
      padding: 10px 30px;
      background-color: #ff8fa3;
      border: none;
      border-radius: 25px;
      color: white;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .begin-btn:hover {
      background-color: #ec38bc;
    }

    .envelopes {
      display: none;
      padding: 30px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      background: #fff0f5;
    }

    .envelope {
      background: #fff;
      border-radius: 20px;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
      padding: 20px;
      text-align: center;
      position: relative;
      animation: penWrite 2s ease forwards;
      opacity: 0;
    }

    .envelope h3 {
      font-size: 1.3em;
      color: #333;
    }

    .envelope p {
      font-size: 1.1em;
      color: #555;
      white-space: pre-wrap;
      border-right: 2px solid #000;
      animation: typing 4s steps(40) 1 forwards;
      overflow: hidden;
    }

    /* Mood Animations */
    .love     { animation: flyingKiss 2s ease-out forwards; }
    .sad      { animation: raindropFade 3s ease-out forwards; }
    .angry    { animation: shakeAngry 0.6s ease-in-out infinite; }
    .excited  { animation: glowPulse 2s ease-in-out infinite; }
    .lonely   { animation: floatLonely 4s ease-in-out infinite; }
    .sleepy   { animation: sleepyFade 3s ease-out forwards; }
    .flirty   { animation: popBounce 2s ease-out forwards; }
    .apology  { animation: slowFadeIn 3s ease forwards; }
    .lazy     { animation: lazyDrift 5s ease-in-out infinite; }
    .special  { animation: goldenGlow 2s ease-in-out infinite; }

    @keyframes typing {
      0% { width: 0; }
      100% { width: 100%; opacity: 1; }
    }

    @keyframes penWrite {
      0% { opacity: 0; transform: scale(0.8); }
      100% { opacity: 1; transform: scale(1); }
    }

    @keyframes flyingKiss {
      0% { transform: scale(0.8) rotate(-5deg); opacity: 0; }
      50% { transform: scale(1.05) rotate(2deg); }
      100% { transform: scale(1) rotate(0deg); opacity: 1; }
    }

    @keyframes raindropFade {
      0% { transform: translateY(-20px); opacity: 0; }
      50% { opacity: 0.5; }
      100% { transform: translateY(0); opacity: 1; }
    }

    @keyframes shakeAngry {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-5px); }
      50% { transform: translateX(5px); }
      75% { transform: translateX(-5px); }
    }

    @keyframes glowPulse {
      0%, 100% { box-shadow: 0 0 10px #ff5ec4; }
      50% { box-shadow: 0 0 30px #ff1493; }
    }

    @keyframes floatLonely {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-15px); }
    }

    @keyframes sleepyFade {
      0% { opacity: 0; }
      100% { opacity: 0.6; }
    }

    @keyframes popBounce {
      0% { transform: scale(0.5); opacity: 0; }
      50% { transform: scale(1.2); opacity: 1; }
      100% { transform: scale(1); }
    }

    @keyframes slowFadeIn {
      0% { opacity: 0; }
      100% { opacity: 1; }
    }

    @keyframes lazyDrift {
      0%, 100% { transform: translateX(0); }
      50% { transform: translateX(10px); }
    }

    @keyframes goldenGlow {
      0%, 100% { box-shadow: 0 0 10px gold; }
      50% { box-shadow: 0 0 30px gold; }
    }

    .cat {
      position: fixed;
      bottom: 20px;
      left: 0;
      height: 100px;
      animation: walkCat 15s linear infinite;
    }

    @keyframes walkCat {
      0% { left: -120px; }
      100% { left: 100%; }
    }
  </style>
</head>
<body>
<!-- Envelope and script code to be added in the next part -->
</body>
</html>

