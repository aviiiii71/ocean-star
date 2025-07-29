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
<div class="welcome">
  <h1>From the Star Above the Ocean ❤️</h1>
  <button class="begin-btn" onclick="startStory()">Begin</button>
</div>

<div class="envelopes" id="envelopes">
  <div class="envelope love">
    <h3>Open When You're Feeling Loved 💖</h3>
    <p>You are the heart of my every heartbeat. You're deeply loved, forever and always.</p>
  </div>
  <div class="envelope sad">
    <h3>Open When You're Feeling Sad 🌧️</h3>
    <p>Let the sadness fall away like rain. My arms are always here, even in silence.</p>
  </div>
  <div class="envelope angry">
    <h3>Open When You're Angry 🗯️</h3>
    <p>Take a deep breath. I'm not here to fight—I'm here to understand and love you through it.</p>
  </div>
  <div class="envelope excited">
    <h3>Open When You're Excited 🌞</h3>
    <p>I can feel your glow from miles away! Celebrate everything—you make moments magical.</p>
  </div>
  <div class="envelope lonely">
    <h3>Open When You're Feeling Lonely 🌙</h3>
    <p>Close your eyes—I’m right there beside you. My love fills the space between us.</p>
  </div>
  <div class="envelope sleepy">
    <h3>Open When You're Sleepy 😴</h3>
    <p>Goodnight, my dream. I hope your sleep is as soft and warm as your hug.</p>
  </div>
  <div class="envelope flirty">
    <h3>Open When You're Feeling Flirty 😘</h3>
    <p>Hey you, gorgeous. Just thinking about you makes my heart race. Mwah!</p>
  </div>
  <div class="envelope apology">
    <h3>Open When You Need Forgiveness 🥺</h3>
    <p>No mistake can undo my love. Let's heal together, hand in hand, heart to heart.</p>
  </div>
  <div class="envelope lazy">
    <h3>Open When You're Feeling Lazy ☕</h3>
    <p>Let's do nothing together sometime. Even silence with you feels like music.</p>
  </div>
  <div class="envelope special">
    <h3>Open On A Special Day ✨</h3>
    <p>This day matters because you're in it. Here's to a memory worth holding forever.</p>
  </div>
  <div class="envelope love">
    <h3>Open When You're Missing Me 💌</h3>
    <p>Each second apart only brings us closer. My soul reaches out to you, always.</p>
  </div>
  <div class="envelope sad">
    <h3>Open When You're Overthinking 🎧</h3>
    <p>Quiet your mind, love. You don’t have to figure it all out now. Just breathe.</p>
  </div>
  <div class="envelope apology">
    <h3>Open When We've Had a Fight 💔</h3>
    <p>Our love is stronger than any disagreement. I'm here, willing, and loving you still.</p>
  </div>
  <div class="envelope flirty">
    <h3>Open When You Want a Virtual Kiss 😚</h3>
    <p>*mwah!* You’re irresistibly cute and mine forever.</p>
  </div>
  <div class="envelope sleepy">
    <h3>Open When You Can't Sleep 🌌</h3>
    <p>Count the stars, not your worries. I'm in your dreams tonight.</p>
  </div>
  <div class="envelope excited">
    <h3>Open When Something Amazing Happens 🎉</h3>
    <p>I knew you'd shine. Tell me everything—I want to celebrate your joy.</p>
  </div>
  <div class="envelope lonely">
    <h3>Open When You're Far From Home 🏠</h3>
    <p>No matter where you are, you're never alone. My love surrounds you.</p>
  </div>
  <div class="envelope special">
    <h3>Open When It's Our Anniversary 🎊</h3>
    <p>From the day we met, you’ve made the world brighter. Here's to forever.</p>
  </div>
  <div class="envelope lazy">
    <h3>Open When It's A Rainy Day 🌧️</h3>
    <p>Let’s curl up with memories and love letters. You and me, cozy forever.</p>
  </div>
  <div class="envelope apology">
    <h3>Open When I Can’t Be With You 💭</h3>
    <p>If I could fly to you right now, I would. But till then, this note is my hug.</p>
  </div>
  <div class="envelope love">
    <h3>Open When You're Feeling Beautiful 💅</h3>
    <p>You are a walking poem—gorgeous in every way. Never forget that.</p>
  </div>
  <div class="envelope excited">
    <h3>Open When You Want to Dance 💃</h3>
    <p>Turn the volume up. Let’s dance like we’re silly kids in love!</p>
  </div>
  <div class="envelope flirty">
    <h3>Open When You Need Butterflies 🦋</h3>
    <p>Thinking about our first hug, first kiss, first “I love you”… chills!</p>
  </div>
  <div class="envelope sleepy">
    <h3>Open When It's Midnight 🌙</h3>
    <p>Stars above, heart within. I’m lying awake loving you.</p>
  </div>
  <div class="envelope lonely">
    <h3>Open When You Miss My Voice 📞</h3>
    <p>Imagine this: I whisper your name, soft and slow… I love you.</p>
  </div>
  <div class="envelope love">
    <h3>Open When You're Feeling Lucky 🍀</h3>
    <p>We're not just lucky—we're fated. My heart was always yours.</p>
  </div>
  <div class="envelope special">
    <h3>Open When You're Proud of Yourself 🏆</h3>
    <p>YES! You did it, love. I knew you would. I’m bursting with pride.</p>
  </div>
  <div class="envelope sleepy">
    <h3>Open When You Want A Bedtime Story 📖</h3>
    <p>Once upon a time, you fell in love. And every day since, it’s grown deeper.</p>
  </div>
  <div class="envelope sad">
    <h3>Open When You Feel Insecure 🪞</h3>
    <p>Look into the mirror and see the soul I adore. You’re enough. Always.</p>
  </div>
  <div class="envelope flirty">
    <h3>Open When You Need Spice 🌶️</h3>
    <p>Warning: this letter contains kisses, flirty winks, and thoughts of you in my arms.</p>
  </div>
  <div class="envelope love">
    <h3>Open When You're Grateful 🙏</h3>
    <p>Let’s be thankful together—for fate, for love, for this beautiful journey.</p>
  </div>
</div>

<img class="cat" src="https://i.imgur.com/XLQ7WDX.gif" alt="Walking Persian Cat" />

<audio autoplay loop>
  <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>

<script>
  function startStory() {
    document.querySelector('.welcome').style.display = 'none';
    document.getElementById('envelopes').style.display = 'grid';
  }
</script>
</body>
</html>

