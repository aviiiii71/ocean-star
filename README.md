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
  <p>Remember our first movie date? You wore that white dress and I couldn’t take my eyes off you. I felt love blooming right then and there. That’s the kind of love I carry for you—deep, pure, and forever.</p>
</div>
  <div class="envelope sad">
  <h3>Open When You're Feeling Sad 🌧️</h3>
  <p>Remember that time we sat quietly at our lake spot, the world silent except our hearts? Even in your sadness, I am with you. Let my words wrap around you like the hug from that temple lift.</p>
</div>
  <div class="envelope angry">
  <h3>Open When You're Angry 🗯️</h3>
  <p>Maybe you're thinking of when I made you wait, or said something wrong. But love, every fight only makes me want to hold you tighter. Like how we found each other after the tuition drama—I’ll always come back to you.</p>
</div>
  <div class="envelope excited">
  <h3>Open When You're Excited 🌞</h3>
  <p>Like that time we played snooker and laughed till our cheeks hurt—your joy is my joy. Whatever’s making your heart race right now, I’m celebrating it with you from the stars to the ocean.</p>
</div>
  <div class="envelope lonely">
  <h3>Open When You're Feeling Lonely 🌙</h3>
  <p>Close your eyes and think of that night at the rooftop after the vodka sip. Our first kiss—soft, shy, perfect. In your loneliness, remember I’m always just a heartbeat away.</p>
</div>
  <div class="envelope sleepy">
  <h3>Open When You're Sleepy 😴</h3>
  <p>Remember dozing off on my shoulder after go-karting? That peace, that warmth—I wish I could tuck you in every night. Sweet dreams, jaan. I’m hugging you in spirit.</p>
</div>
  <div class="envelope flirty">
  <h3>Open When You're Feeling Flirty 😘</h3>
  <p>Hey beautiful. Remember teasing me at Baskin Robbins with your ice cream smile? That’s the charm that melts me. Come here, I owe you a flying kiss 💋</p>
</div>
  <div class="envelope apology">
  <h3>Open When You Need Forgiveness 🥺</h3>
  <p>If I ever made you feel alone—like that call log day—I’m sorry from my soul. You mean more than any fear or rule. My love, I’ll spend my life making it up to you.</p>
</div>
  <div class="envelope lazy">
  <h3>Open When You're Feeling Lazy ☕</h3>
  <p>Let’s lay down at our lake again, no words, just us. Like that quiet evening when our souls spoke louder than any conversation. You and me, that’s all we need.</p>
</div>
  <div class="envelope special">
  <h3>Open On A Special Day ✨</h3>
  <p>One year. 31 moments. Infinite emotions. From the first scooty ride to this webpage, every second has been you. My Jaana, my forever, my magic. Happy anniversary. 💖</p>
</div>
  <div class="envelope love">
  <h3>Open When You're Missing Me 💌</h3>
  <p>Think of us at that secret lake spot, where time slowed and hearts spoke. Every heartbeat of mine whispers your name when you’re not near. I'm missing you too, Jaana.</p>
</div>
  <div class="envelope sad">
  <h3>Open When You're Overthinking 🎧</h3>
  <p>Remember how we sat on the scooty and just watched the world? Not every answer is needed now. You’re doing more than fine. Let go, and let me love you through it.</p>
</div>
  <div class="envelope apology">
  <h3>Open When We've Had a Fight 💔</h3>
  <p>We’ve had our share of tough moments—like the time we didn’t speak after tuition. But even then, you were all I could think about. I love you more after every storm.</p>
</div>
  <div class="envelope flirty">
  <h3>Open When You Want a Virtual Kiss 😚</h3>
  <p>Come a little closer. Like that day you leaned on me and whispered secrets—I want to press my lips to your forehead and say, 'Forever is ours.'</p>
</div>
  <div class="envelope sleepy">
  <h3>Open When You Can't Sleep 🌌</h3>
  <p>Remember the night under stars after the movie? You laid on my shoulder and my world stopped. If sleep escapes you tonight, let my memory wrap around you softly.</p>
</div>
  <div class="envelope excited">
  <h3>Open When Something Amazing Happens 🎉</h3>
  <p>I can see that sparkle in your eyes, like when we first laughed in the blue city. I’m clapping from miles away. Tell me everything, I want to hear it all!</p>
</div>
  <div class="envelope lonely">
  <h3>Open When You're Far From Home 🏠</h3>
  <p>Whether it’s across town or across the sky, home is in our memories. Like when I said I was your dad to get you out of tuition—wild, but worth it. I’d do anything to be near you.</p>
</div>
  <div class="envelope special">
  <h3>Open When It's Our Anniversary 🎊</h3>
  <p>One year since our souls collided. From scooty rides to secret spots, from laughter to love letters—Jaana, this journey is only beginning. Happy Anniversary, meri jaan.</p>
</div>
  <div class="envelope lazy">
  <h3>Open When It's A Rainy Day 🌧️</h3>
  <p>Rain reminds me of you—refreshing, warm, and full of meaning. I wish we were wrapped in a blanket right now, just watching it fall from our spot at the lake.</p>
</div>
  <div class="envelope apology">
  <h3>Open When I Can’t Be With You 💭</h3>
  <p>On days I can’t be near, remember the galaxy lamp night. You said it looked like our future. You were right. It’s bright, vast, and full of stars—just like my love for you.</p>
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


