<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>From the Star Above the Ocean 💌</title>
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <link href="https://fonts.googleapis.com/css2?family=Nanum+Pen+Script&family=Parisienne&display=swap" rel="stylesheet">
  <style>
    :root {
      --main-bg: #f6ede9;
      --envelope-pastel1: #ffe0ec;
      --envelope-pastel2: #d6f0ff;
      --envelope-pastel3: #fff7d1;
      --envelope-pastel4: #e5ffe2;
      --envelope-pastel5: #f1e0ff;
      --handwriting: 'Nanum Pen Script', 'Parisienne', cursive;
      --title-font: 'Parisienne', cursive;
      --shadow: 0 4px 24px rgba(0,0,0,0.07);
    }
    body {
      margin: 0; padding: 0;
      background: linear-gradient(120deg, #f6ede9 60%, #e5edfb 100%);
      min-height: 100vh;
      font-family: var(--handwriting);
      overflow-x: hidden;
      position: relative;
    }
    .parallax-bg { pointer-events: none; position: fixed; left: 0; top: 0; width: 100vw; height: 100vh; z-index: 1; overflow: hidden;}
    .star { position: absolute; width: 2px; height: 2px; border-radius: 100%; background: #fff8; animation: twinkle 4s infinite linear; opacity: 0.7;}
    @keyframes twinkle { 0% { opacity: .7 } 50% { opacity: 1 } 100% { opacity: .7 }}
    #entrance {
      position: fixed; z-index: 99; background: var(--main-bg); width: 100vw; height: 100vh; top: 0; left: 0;
      display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 24px;
      transition: opacity .9s cubic-bezier(.6,0,.3,1);
    }
    #entrance.hide { opacity: 0; pointer-events: none;}
    .entrance-title {
      font-family: var(--title-font);
      font-size: 2.5rem;
      letter-spacing: .04em;
      color: #b990ca;
      text-shadow: 0 4px 24px #b990ca33;
      margin-bottom: 1rem;
      animation: fadeInDown 2s;
    }
    @keyframes fadeInDown { from { transform: translateY(-50px); opacity: 0 } to   { transform: translateY(0); opacity: 1 }}
    .princess-crown {
      font-size: 3.4rem;
      margin-bottom: 1.3rem;
      filter: drop-shadow(0 3px 15px #dcb8fd44);
      animation: crownPop 1.8s;
      line-height: 1;
      display: block;
    }
    @keyframes crownPop { 0% { transform: scale(0.7) rotate(-30deg); opacity: 0 } 70% { transform: scale(1.1) rotate(5deg); opacity: 1 } 100% { transform: scale(1) rotate(0deg); }}
    #begin-btn {
      font-family: var(--handwriting);
      background: linear-gradient(90deg, #fbb1d1 40%, #c6e6ff 100%);
      color: #573c6b;
      font-size: 1.7rem;
      border: none;
      border-radius: 1.2em;
      padding: 1em 2.5em;
      cursor: pointer;
      box-shadow: 0 2px 16px #c08de833, 0 1.5px 0 #fff;
      transition: all .21s;
      margin-top: 1.5rem;
      animation: fadeIn 2s 1s both;
    }
    #begin-btn:hover { transform: scale(1.04) translateY(-2px); box-shadow: 0 7px 22px #c08de866, 0 2px 0 #fff;}
    @keyframes fadeIn { from { opacity: 0; } to   { opacity: 1; }}
    #gallery {
      padding-top: 60px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 38px;
      max-width: 1350px;
      margin: 0 auto;
      z-index: 10;
      position: relative;
    }
    .envelope-outer { perspective: 900px; background: none; display: flex; align-items: center; justify-content: center; min-height: 230px; min-width: 180px; position: relative;}
    .envelope {
      width: 180px; height: 120px; position: relative; background: none; cursor: pointer;
      transform-style: preserve-3d; transition: transform .3s cubic-bezier(.8,0,.2,1);
      box-shadow: var(--shadow); border-radius: 18px; outline: none;
      z-index: 2;
    }
    .envelope:hover { transform: rotateY(7deg) scale(1.03); z-index: 5; box-shadow: 0 8px 28px #ab90e855, 0 2px 0 #fff;}
    .envelope.opened { pointer-events: none;}
    .envelope-flap {
      position: absolute; width: 100%; height: 60%; background: #fff9fc;
      border-radius: 18px 18px 44px 44px/30px 30px 55px 55px;
      left: 0; top: 0; z-index: 2; transform-origin: top center;
      box-shadow: 0 8px 36px #d1a9c655, 0 2px 0 #fff9;
      transition: transform .72s cubic-bezier(.6,0,.32,1);
    }
    .envelope.opened .envelope-flap { transform: rotateX(-120deg); transition: transform .8s cubic-bezier(.6,0,.32,1); box-shadow: none;}
    .envelope-body { width: 100%; height: 100%; background: var(--envelope-pastel1); border-radius: 0 0 18px 18px/0 0 24px 24px; position: absolute; left: 0; top: 22px; z-index: 1; box-shadow: 0 8px 36px #b5b5d811; overflow: hidden; border: 1.5px solid #fff7; background: repeating-linear-gradient(125deg, #fff9fc 0 12px, #ffe0ec 12px 24px, #fff9fc 24px 40px); transition: background .7s;}
    .envelope-body[data-i="1"] { background: var(--envelope-pastel1);}
    .envelope-body[data-i="2"] { background: var(--envelope-pastel2);}
    .envelope-body[data-i="3"] { background: var(--envelope-pastel3);}
    .envelope-body[data-i="4"] { background: var(--envelope-pastel4);}
    .envelope-body[data-i="5"] { background: var(--envelope-pastel5);}
    .envelope-body[data-i="6"], .envelope-body[data-i="11"], .envelope-body[data-i="16"], .envelope-body[data-i="21"], .envelope-body[data-i="26"], .envelope-body[data-i="31"] { background: var(--envelope-pastel2);}
    .envelope-body[data-i="7"], .envelope-body[data-i="12"], .envelope-body[data-i="17"], .envelope-body[data-i="22"], .envelope-body[data-i="27"] { background: var(--envelope-pastel3);}
    .envelope-body[data-i="8"], .envelope-body[data-i="13"], .envelope-body[data-i="18"], .envelope-body[data-i="23"], .envelope-body[data-i="28"] { background: var(--envelope-pastel4);}
    .envelope-body[data-i="9"], .envelope-body[data-i="14"], .envelope-body[data-i="19"], .envelope-body[data-i="24"], .envelope-body[data-i="29"] { background: var(--envelope-pastel5);}
    .envelope-body[data-i="10"], .envelope-body[data-i="15"], .envelope-body[data-i="20"], .envelope-body[data-i="25"], .envelope-body[data-i="30"] { background: var(--envelope-pastel1);}
    .envelope-paper {
      width: 100%; height: 160px; background: #f9f7ee; position: absolute; left: 0; top: 50px; z-index: 10; border-radius: 12px;
      box-shadow: 0 4px 32px #d0b0b036, 0 1px 0 #fff; border: 1.5px solid #f5e5ff; opacity: 0; pointer-events: none;
      transform: scale(.9) translateY(30px); transition: all .7s cubic-bezier(.5,0,.3,1); padding: 16px 14px 10px 18px;
      font-family: var(--handwriting); font-size: 1.1rem; color: #654c5f;
      background-image: repeating-linear-gradient(120deg, #f9f7ee 0 20px, #fffbe9 20px 32px, #f9f7ee 32px 45px);
      overflow-y: auto; line-height: 1.8; text-shadow: 0 2px 16px #f9f6e988; white-space: pre-line; animation: none;
    }
    .envelope.opened .envelope-paper {
      opacity: 1; pointer-events: auto; transform: scale(1) translateY(-24px);
      transition: all .77s cubic-bezier(.7,0,.2,1); animation: letterUnroll 1.4s both;
    }
    @keyframes letterUnroll { 0% { transform: scale(.85) translateY(100px); opacity: 0; } 50% { opacity: .9; } 100% { transform: scale(1) translateY(-24px); opacity: 1; }}
    .wax-seal { position: absolute; left: 47%; top: 10px; transform: translateX(-50%); width: 36px; height: 36px; z-index: 12; font-size:2.2rem; line-height:1; user-select:none;}
    .mood-anim { pointer-events: none; position: absolute; left: 50%; top: 0; width: 120px; height: 120px; transform: translate(-50%, -50%); z-index: 90; opacity: 0; animation: popMood 1.5s cubic-bezier(.4,0,.2,1);}
    .envelope.opened .mood-anim { opacity: 1; animation: popMood 1.5s cubic-bezier(.4,0,.2,1);}
    @keyframes popMood { 0% { opacity: 0; transform: scale(.7);} 50% { opacity: 1; transform: scale(1.25);} 90% { opacity: 1;} 100% { opacity: 0; transform: scale(0.2);}}
    .flowers-bouquet {
      position: fixed;
      left: 18vw;
      bottom: 0;
      z-index: 50;
      font-size: 3.3rem;
      user-select:none;
      pointer-events: none;
      animation: flowerFloat 10s infinite alternate cubic-bezier(.5,0,.5,1);
      text-shadow: 0 4px 24px #fbb1d1aa;
    }
    @keyframes flowerFloat {
      0% { left: 18vw; bottom: 0; transform: scale(1) rotate(-3deg);}
      25% { left: 42vw; bottom: 2vh; transform: scale(1.12) rotate(3deg);}
      40% { left: 60vw; bottom: 0; transform: scale(0.99) rotate(-1deg);}
      65% { left: 75vw; bottom: 1.7vh; transform: scale(1.11) rotate(2deg);}
      100% { left: 18vw; bottom: 0; transform: scale(1) rotate(-3deg);}
    }
    .envelope-label {
      position: absolute;
      left: 50%; transform: translateX(-50%);
      top: 50%; z-index: 100;
      min-width: 150px; max-width: 170px;
      background: rgba(255,255,255,0.92);
      border-radius: 16px;
      padding: 6px 10px 7px 10px;
      font-family: var(--handwriting);
      font-size: 1.13rem;
      color: #a16bb9;
      letter-spacing: .01em;
      box-shadow: 0 1.5px 14px #d6c2ef41;
      text-shadow: 0 1.5px 4px #fff;
      font-weight: bold;
      pointer-events: none;
      text-align: center;
      transition: opacity .5s, background .2s;
      user-select: none;
      border: 1.5px solid #ede3f7;
      opacity: 1;
    }
    .envelope.opened .envelope-label {
      opacity: 0;
      transition: opacity .5s;
    }
    @media (max-width: 700px) {
      .entrance-title { font-size: 1.7rem; }
      .envelope-outer { min-width: 128px; min-height: 125px;}
      .envelope { width: 98px; height: 67px;}
      .envelope-label { font-size: 0.97rem; min-width: 80px; max-width: 105px;}
      .envelope-paper { font-size: 0.97rem; height: 102px; padding: 7px 6px;}
      #gallery { gap: 16px; padding-top: 20px;}
      .flowers-bouquet { font-size: 2.1rem;}
    }
  </style>
</head>
<body>
  <div class="parallax-bg" id="parallax-bg"></div>
  <div class="flowers-bouquet">💐🌸🌷🌹🌺🌻</div>
  <div id="entrance">
    <span class="princess-crown">👑</span>
    <div class="entrance-title">
      From the <b>Star</b> Above the Ocean<br>
      <span style="font-size:1.4rem;">💖 To my Jaana 💖</span>
    </div>
    <button id="begin-btn">Begin &nbsp;✨</button>
    <div style="font-size:1rem; color:#b188be;">
      <span>31 magical envelopes await you...<br>Each one, a piece of my heart.</span>
    </div>
  </div>
  <main style="z-index:2; position:relative;">
    <div id="gallery"></div>
  </main>
  <script>
    const envelopes = [
      { label: "Open When: You Miss Me", mood: "kiss", text: "My Jaana, every second apart feels like an ocean. When you miss me, remember: I’m thinking of you under the same sky, loving you even more than yesterday. Imagine my arms around you, holding you close—until the moment we meet again." },
      { label: "Open When: You’re Sad", mood: "rain", text: "Sometimes the world feels heavy, and that's okay. Close your eyes, take a deep breath, and remember: your Star is always shining for you. Even on cloudy days, you are my sun. I love every shade of you—your smiles, your tears, your every emotion." },
      { label: "Open When: You Want to Smile", mood: "confetti", text: "Do you know how much your smile lights up my life? Imagine me sending you the world’s biggest, silliest grin. You’re my sunshine—never forget how loved you are, always." },
      { label: "Open When: You Feel Stressed", mood: "rain", text: "Let go of everything for a moment. Inhale deeply and picture me beside you, holding your hand and telling you, ‘We’ll get through anything together.’ I love you beyond words, my hope and my calm." },
      { label: "Open When: You Want a Warm Hug", mood: "kiss", text: "Wrap your arms around yourself. Now imagine it’s me—my embrace, my warmth, my heart beating close to yours. This is my hug, crossing all distance, for you." },
      { label: "Open When: You’re Angry (Even at Me)", mood: "rain", text: "It’s okay to be angry. I’ll always love every part of you, even your stormiest moods. When you’re ready, I’ll listen and hold you—always with patience and so much love." },
      { label: "Open When: You Can’t Sleep", mood: "kiss", text: "Imagine me whispering: ‘It’s okay, my Jaana, just close your eyes and feel my love surround you.’ I’m there with you, even in the silent hours. Goodnight, my love." },
      { label: "Open When: You’re Celebrating", mood: "confetti", text: "Yay! Whatever the reason, I’m cheering for you! You deserve every happiness, every little win, every single joy. I’m so proud of you—always." },
      { label: "Open When: You’re Anxious", mood: "rain", text: "Breathe in. Breathe out. You are safe, you are loved, and you are never alone. Let my words wrap around you like a blanket. Everything will be okay, my hope." },
      { label: "Open When: It’s Your Birthday", mood: "confetti", text: "Happy Birthday, my love! Another year of you—a gift to this world. I wish I could shower you in kisses and cake. Know that I’m celebrating your existence every single day." },
      { label: "Open When: You Doubt Yourself", mood: "kiss", text: "You are more than enough. Strong, beautiful, radiant, and kind. When doubts come, remember: your Star believes in you, endlessly." },
      { label: "Open When: You Need Motivation", mood: "confetti", text: "Whatever you dream of, you can do. You have a universe inside you. I’m always here, your number one supporter, cheering you on through every challenge." },
      { label: "Open When: You Want to Feel Loved", mood: "kiss", text: "You are cherished beyond measure, adored beyond reason, and loved beyond time. Let these words be my arms around your heart. I love you, endlessly." },
      { label: "Open When: You Want to Laugh", mood: "confetti", text: "Knock knock. Who’s there? Star! Star who? Star, who loves you to the moon and back, forever and ever! (Okay, that was cheesy but you smiled, didn’t you?)" },
      { label: "Open When: You Feel Lonely", mood: "rain", text: "Look up at the night sky. Even if we’re apart, we’re looking at the same moon. My love, you are never truly alone—my heart is always with you." },
      { label: "Open When: You’re Tired", mood: "kiss", text: "Rest, my love. You deserve peace, softness, and comfort. If I could, I’d tuck you in and kiss your forehead until you drift into sweet dreams." },
      { label: "Open When: You Want to Remember Us", mood: "confetti", text: "From our first hello to our every memory, every moment with you is my treasure. I’ll spend my life making new memories, side by side with you." },
      { label: "Open When: You Need Hope", mood: "confetti", text: "Remember: storms always pass. There’s always a new dawn, and I’ll always be your light—your hope—through everything." },
      { label: "Open When: You Want to Read My Poem", mood: "kiss", text: "If love were verses, you’d be every line—soft, radiant, brave, divine. My Jaana, my ocean, my hope, my rhyme—loving you always, till the end of time." },
      { label: "Open When: You’re Overthinking", mood: "rain", text: "Pause. Breathe. Let go. Sometimes, the heart knows what the mind can’t explain. Trust yourself, trust us. I trust you, always." },
      { label: "Open When: You Want To Cry", mood: "rain", text: "Let the tears flow. Every drop holds a story, every ache is valid. I love your strong heart and your soft soul. I’ll hold your hand through every storm." },
      { label: "Open When: You Need Forgiveness", mood: "kiss", text: "We all make mistakes. I forgive you, always, for anything. Our love is bigger than any flaw, stronger than any doubt." },
      { label: "Open When: You’re Grateful", mood: "confetti", text: "And I am endlessly grateful for you. Thank you for being my hope, my dream, my greatest miracle." },
      { label: "Open When: You’re Angry At The World", mood: "rain", text: "It’s okay to feel that way. The world is big and tough, but you are stronger. Take your time, come back to yourself. I’m here." },
      { label: "Open When: You’re Proud of Yourself", mood: "confetti", text: "Look at you—growing, shining, glowing. I’m so proud of you. Never forget how wonderful you are." },
      { label: "Open When: You Need a Reason To Keep Going", mood: "confetti", text: "You are my reason. Our love is worth every struggle, every dawn, every heartbeat. We will make it, together." },
      { label: "Open When: You Want to Dream", mood: "confetti", text: "Dream big, my Jaana. Our dreams are the stars above us, guiding us home. I believe in every dream you hold." },
      { label: "Open When: You Want to Feel Safe", mood: "kiss", text: "Imagine my arms around you, shielding you from every worry. You’re safe here, always, in my love." },
      { label: "Open When: You’re Missing Your Family", mood: "rain", text: "Family is forever, and so is my love for you. I’ll always be your home, no matter where we are." },
      { label: "Open When: You Want to Feel Beautiful", mood: "confetti", text: "You are breathtaking. Inside and out. You make the world brighter just by being yourself. Never doubt your beauty." },
      { label: "Open When: You Want to Feel Like a Princess", mood: "confetti", text: "You are my princess, my queen, my everything. I will always cherish you, adore you, and make you feel royal." },
      { label: "Open When: It’s 31st July", mood: "kiss", text: "Our day. One year of love, hope, and magic. Thank you for finding me, for loving me. This is just the beginning of our forever. Happy anniversary, my love." }
    ];
    const moodIcons = { kiss: "💋", rain: "🌧️", confetti: "🎉" };
    const waxSeal = "🕯️";
    const gallery = document.getElementById("gallery");
    envelopes.forEach((env, i) => {
      const el = document.createElement('div');
      el.className = "envelope-outer";
      el.innerHTML = `
        <div class="envelope" tabindex="0" data-i="${i+1}">
          <div class="envelope-flap"></div>
          <div class="envelope-body" data-i="${i+1}"></div>
          <div class="envelope-label">${env.label}</div>
          <div class="envelope-paper"><span>${env.text}</span></div>
          <span class="wax-seal">${waxSeal}</span>
          <div class="mood-anim" style="font-size:3.2rem;">${moodIcons[env.mood]}</div>
        </div>
      `;
      gallery.appendChild(el);
    });
    document.querySelectorAll('.envelope').forEach(env => {
      env.addEventListener('click', function() {
        if (this.classList.contains("opened")) return;
        this.classList.add("opened");
      });
      env.addEventListener('keydown', function(e) {
        if(e.key==="Enter"||e.key===" ") this.click();
      });
    });
    document.getElementById("begin-btn").onclick = function() {
      document.getElementById("entrance").classList.add("hide");
      setTimeout(()=>{document.getElementById("entrance").style.display="none"},900);
    };
    function randomBetween(a,b){return a+Math.random()*(b-a);}
    let parallaxBG = document.getElementById("parallax-bg");
    for(let i=0;i<80;i++){
      let s=document.createElement('div');
      s.className="star";
      s.style.left=randomBetween(1,99)+"vw";
      s.style.top=randomBetween(1,99)+"vh";
      s.style.animationDuration=randomBetween(2,6)+"s";
      parallaxBG.appendChild(s);
    }
    document.querySelectorAll('.envelope').forEach(env=>{
      env.addEventListener('mousemove',function(e){
        const rect = this.getBoundingClientRect();
        const x = (e.clientX - rect.left)/rect.width-.5, y = (e.clientY - rect.top)/rect.height-.5;
        this.style.transform = `rotateY(${x*16}deg) rotateX(${-y*10}deg) scale(1.05)`;
      });
      env.addEventListener('mouseleave',function(e){
        this.style.transform = "";
      });
    });
  </script>
</body>
</html>

