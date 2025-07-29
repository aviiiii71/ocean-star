<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>From the star above the ocean</title>
  <!-- Google Font for handwritten effect -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    /*------------------------------------*
      ROOT VARIABLES AND GLOBAL RESET
    *------------------------------------*/
    :root {
      --primary-color: #d6336c;
      --secondary-color: #fdeef4;
      --accent-color: #e6a1b8;
      --bg-gradient-start: #f8c8dc;
      --bg-gradient-end: #fdeef4;
      --envelope-gradient-start: #ffe1e8;
      --envelope-gradient-end: #ffedef;
      --font-handwriting: 'Dancing Script', cursive;
      --font-sans: 'Poppins', sans-serif;
      --transition-duration: 0.8s;
      --drop-shadow: 0 8px 16px rgba(0,0,0,0.15);
    }
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    html, body {
      width: 100%;
      height: 100%;
      overflow: hidden;
      background: #fff5f8;
      font-family: var(--font-sans);
      color: #333;
    }

    /*------------------------------------*
      INTRO SCREEN STYLES
    *------------------------------------*/
    #intro {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      background: linear-gradient(135deg, var(--bg-gradient-start), var(--bg-gradient-end));
      z-index: 10;
    }
    #intro h1 {
      font-family: var(--font-handwriting);
      font-size: 3rem;
      color: var(--primary-color);
      text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
      margin-bottom: 1rem;
    }
    #intro button {
      font-family: var(--font-sans);
      font-size: 1.2rem;
      padding: 1rem 2rem;
      border: none;
      border-radius: 30px;
      background: var(--primary-color);
      color: #fff;
      cursor: pointer;
      box-shadow: 0 6px 12px rgba(0,0,0,0.25);
      transition: transform 0.2s;
    }
    #intro button:hover {
      transform: scale(1.05);
    }

    /*------------------------------------*
      ENVELOPE GRID CONTAINER
    *------------------------------------*/
    #envelopes {
      display: none;
      position: relative;
      width: 100%; height: 100%;
      padding: 2rem;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: flex-start;
      gap: 1.5rem;
      overflow-y: auto;
    }
    /* Custom scrollbar for envelopes container */
    #envelopes::-webkit-scrollbar {
      width: 10px;
    }
    #envelopes::-webkit-scrollbar-track {
      background: rgba(0,0,0,0.05);
      border-radius: 5px;
    }
    #envelopes::-webkit-scrollbar-thumb {
      background: rgba(0,0,0,0.1);
      border-radius: 5px;
    }

    /*------------------------------------*
      ENVELOPE COMPONENT STYLES
    *------------------------------------*/
    .envelope {
      width: 260px;
      height: 160px;
      perspective: 1000px;
      position: relative;
      cursor: pointer;
      filter: drop-shadow(var(--drop-shadow));
    }
    .envelope .flap,
    .envelope .body {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 12px;
    }
    /* Flap styles */
    .envelope .flap {
      background: linear-gradient(135deg, var(--envelope-gradient-start), var(--envelope-gradient-end));
      border: 2px solid var(--accent-color);
      transform-origin: top;
      transition: transform var(--transition-duration) ease;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding-top: 1rem;
    }
    .flap .label {
      font-family: var(--font-handwriting);
      font-size: 1.2rem;
      color: var(--primary-color);
    }
    .flap .open-text {
      font-family: var(--font-sans);
      font-size: 0.85rem;
      color: var(--secondary-color);
      margin-top: 0.25rem;
    }
    /* Body styles */
    .envelope .body {
      background: linear-gradient(135deg, #fff, #fafafa);
      border: 2px solid var(--accent-color);
      transform: rotateX(0deg);
    }

    /* Letter inside envelope */
    .envelope .letter {
      position: absolute;
      bottom: 0;
      left: 5%;
      width: 90%;
      height: 90%;
      background: #fff;
      border-radius: 8px;
      padding: 1rem;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      transform: translateY(120%);
      transition: transform var(--transition-duration) ease var(--transition-duration);
      overflow: auto;
    }
    .letter .message {
      font-family: var(--font-sans);
      font-size: 0.95rem;
      line-height: 1.6;
      color: #444;
      white-space: pre-wrap;
    }
    /* Cursor styling for typing effect */
    .letter .cursor {
      display: inline-block;
      background: #444;
      width: 2px;
      animation: blink 0.6s steps(1) infinite;
      margin-left: 2px;
    }
    @keyframes blink {
      0%, 100% { opacity: 1; }
      50% { opacity: 0; }
    }

    /* Open state animations */
    .envelope.open .flap {
      transform: rotateX(-180deg);
    }
    .envelope.open .letter {
      transform: translateY(0);
    }

    /*------------------------------------*
      BACKGROUND & CAT ANIMATIONS
    *------------------------------------*/
    body {
      background: #fff5f8;
      overflow: hidden;
      animation: bgPulse 10s ease-in-out infinite;
    }
    @keyframes bgPulse {
      0%, 100% { background: #fff5f8; }
      50% { background: #fdeef4; }
    }
    #cat {
      position: absolute;
      bottom: 5%;
      left: 5%;
      width: 120px;
      transition: transform 4s ease-in-out;
    }
    /*------------------------------------*
      FLYING KISS & PARTICLE EFFECTS
    *------------------------------------*/
    .kiss {
      position: absolute;
      font-size: 2rem;
      opacity: 0;
      animation: flykiss 1.5s ease-out forwards;
      pointer-events: none;
    }
    @keyframes flykiss {
      0%   { transform: translateY(0) scale(1); opacity: 1; }
      50%  { transform: translateY(-80px) scale(1.3); opacity: 0.8; }
      100% { transform: translateY(-140px) scale(1.6); opacity: 0; }
    }
    /* Heart particle container */
    #particles {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
    }
    .particle {
      position: absolute;
      font-size: 0.8rem;
      color: var(--primary-color);
      opacity: 0;
      animation: floatUp 4s ease-out forwards;
    }
    @keyframes floatUp {
      0%   { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-200px) scale(1.5); opacity: 0; }
    }

    /*------------------------------------*
      AUDIO CONTROLS & PRELOADER
    *------------------------------------*/
    #audioControl {
      position: fixed;
      top: 20px;
      right: 20px;
      background: rgba(255,255,255,0.8);
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      cursor: pointer;
      z-index: 100;
    }
    #audioControl img {
      width: 24px;
      height: 24px;
    }

    #preloader {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #fff;
      z-index: 200;
      transition: opacity 0.5s;
    }
    #preloader.hidden {
      opacity: 0;
      pointer-events: none;
    }
    .spinner {
      border: 6px solid #f3f3f3;
      border-top: 6px solid var(--primary-color);
      border-radius: 50%;
      width: 60px;
      height: 60px;
      animation: spin 1s linear infinite;
    }
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
  </style>
</head>
<body>
  <!-- Preloader Screen -->
  <div id="preloader">
    <div class="spinner"></div>
  </div>

  <!-- Intro Screen -->
  <div id="intro">
    <h1>From the star above the ocean ❤️</h1>
    <button id="beginBtn">Begin</button>
  </div>

  <!-- Envelope Grid -->
  <div id="envelopes"></div>

  <!-- Particle Container -->
  <div id="particles"></div>

  <!-- Audio Control -->
  <div id="audioControl">
    <img src="audio_on.png" alt="Toggle Music" id="audioIcon">
  </div>

  <!-- Background Music -->
  <audio id="bgMusic" src="music.mp3" loop></audio>

  <!-- Persian Cat -->
  <img id="cat" src="persian_cat.png" alt="Persian Cat">

  <script>
    /*------------------------------------*
      PRELOADER LOGIC
    *------------------------------------*/
    window.addEventListener('load', () => {
      const preloader = document.getElementById('preloader');
      setTimeout(() => {
        preloader.classList.add('hidden');
      }, 800);
    });

    /*------------------------------------*
      ENVELOPE DATA STRUCTURE
    *------------------------------------*/
    const envelopesData = [
      { icon: "❤️", label: "Love Reminder", message: `My dearest Jaana,

Every moment with you feels like the star above the ocean guiding me home. I love you beyond words.

Forever yours,
Abhinav` },
      { icon: "💌", label: "Miss Me", message: `My sweet Jaana,

When distance tugs at our hearts, remember that I carry you with me in every beat. I miss you more than the ocean misses the moon.

All my love,
Abhinav` },
      { icon: "🌧️", label: "Bad Day", message: `Hey love,

I know today has been tough. Here’s a gentle hug to remind you that you’re never alone—I'm always here for you.

Love,
Your safe harbor` },
      { icon: "🏅", label: "Proud of You", message: `My brave Jaana,

I see your strength and all you've accomplished. You make me so proud every single day.

Keep shining,
Abhinav` },
      { icon: "💪", label: "Encouragement", message: `Beloved Jaana,

Whenever doubts arise, remember how far you've come and how brightly you shine. You can conquer anything.

Cheering for you,
Abhinav` },
      { icon: "🌍", label: "Apart", message: `Sweetheart,

Though miles separate us, my heart is tethered to yours. Soon we'll be together again—hold on to that thought.

Yours always,
Abhinav` },
      { icon: "🎉", label: "Anniversary", message: `Happy Anniversary, my love!

Today marks another chapter in our story. Thank you for being my star above the ocean.

Forever & always,
Abhinav` },
      { icon: "🎂", label: "Birthday", message: `To my beautiful Jaana,

Happy Birthday! May your day be as radiant as your smile and filled with love.

All my love,
Abhinav` },
      { icon: "😂", label: "Need a Laugh", message: `Dearest J,

Here’s a silly joke: Why did the star go to school? To get a little brighter! Keep smiling, angel.

😘,
Abhinav` },
      { icon: "😰", label: "Stressed", message: `My calm in the storm,

Close your eyes, take a deep breath, and imagine my arms around you. Everything will be okay.

Lovingly,
Abhinav` },
      { icon: "🏆", label: "Achieved a Goal", message: `Champion,

Congratulations on your achievement! I’m so proud of you and all your hard work.

Cheers to you,
Abhinav` },
      { icon: "🤗", label: "Lonely", message: `My heart,

Whenever loneliness creeps in, know that you are cherished beyond measure. I’m with you in spirit.

Always yours,
Abhinav` },
      { icon: "🔮", label: "Future", message: `My dreamer,

I can’t wait for all our tomorrows—hand in hand, heart to heart. The best is yet to come.

Love,
Abhinav` },
      { icon: "✨", label: "Inspiration", message: `My muse,

Your grace, passion, and kindness inspire me daily. Keep being the incredible you.

With admiration,
Abhinav` },
      { icon: "🤔", label: "Worried About Me", message: `Dear Jaana,

Your care warms my soul. Rest assured, I’m safe and thinking of you every moment.

Forever devoted,
Abhinav` },
      { icon: "😴", label: "Sleepy", message: `Goodnight, love,

May your dreams be sweet and filled with our happiest memories. Sleep tight.

Yours in every dream,
Abhinav` },
      { icon: "🎊", label: "Holiday", message: `My joyful Jaana,

Wishing you a holiday filled with laughter, warmth, and love. Can’t wait to celebrate together.

Love always,
Abhinav` },
      { icon: "😊", label: "Smile", message: `My sunshine,

Here’s a reminder: your smile lights up my world. I hope this little note made yours bloom.

😘,
Abhinav` },
      { icon: "😥", label: "Anxious", message: `My darling,

Take a moment to breathe. You have all the strength you need, and I believe in you completely.

Love,
Abhinav` },
      { icon: "🤗", label: "Comfort", message: `Sweet Jaana,

Imagine my arms wrapped around you, holding you close. You are safe, loved, and never alone.

Always,
Abhinav` },
      { icon: "🙏", label: "Grateful", message: `My gratitude,

Thank you for being you—kind, beautiful, amazing. I’m endlessly thankful for our love.

Yours,
Abhinav` },
      { icon: "💃", label: "Dance", message: `My rhythm,

Put on our song, spin around, and dance like nobody’s watching. I’ll be right there with you in spirit.

❤️,
Abhinav` },
      { icon: "🎈", label: "Excited", message: `My spark,

Your excitement is contagious. I can’t wait to see your joy light up the room.

With excitement too,
Abhinav` },
      { icon: "📸", label: "Nostalgic", message: `My memory keeper,

Remember our first date by the ocean? I treasure that night endlessly. Here’s to making more memories.

Love,
Abhinav` },
      { icon: "😘", label: "Kiss", message: `My sweet,

Closing your eyes? Imagine my softest kiss pressed to your forehead, sealing my love for you.

😘,
Abhinav` },
      { icon: "🌙", label: "Not There", message: `My heart,

Even when I’m not by your side, you are never far from my thoughts. Feel my love reaching you now.

Always,
Abhinav` },
      { icon: "☮️", label: "Peace", message: `My tranquility,

Let your mind rest in the calm of our love. You deserve serenity and all the quiet joy it brings.

Yours in peace,
Abhinav` },
      { icon: "😪", label: "Tired", message: `My darling,

Rest your weary soul. I’ll be here when you wake, ready to hold you tight.

Sweet dreams,
Abhinav` },
      { icon: "🌹", label: "First Date", message: `My dearest,

That magical evening under the stars by the ocean—my heart knew then what it knows now: you are my forever.

Love always,
Abhinav` },
      { icon: "✈️", label: "Next Adventure", message: `My partner in crime,

Dreaming of our next adventure—whether near or far, every journey is brighter with you.

Let’s go,
Abhinav` },
      { icon: "💖", label: "Just Because", message: `My everything,

No reason needed—just a little note to say I love you more each day.

Always,
Abhinav` }
    ];

    /*------------------------------------*
      RENDER ENVELOPES INTO DOM
    *------------------------------------*/
    function createEnvelopes() {
      const container = document.getElementById('envelopes');
      envelopesData.forEach(env => {
        const envelope = document.createElement('div');
        envelope.className = 'envelope';
        
        const flap = document.createElement('div');
        flap.className = 'flap';
        flap.innerHTML = `<div class="label">${env.icon} ${env.label}</div><div class="open-text">Open When</div>`;
        
        const body = document.createElement('div');
        body.className = 'body';

        const letter = document.createElement('div');
        letter.className = 'letter';

        const msg = document.createElement('div');
        msg.className = 'message';
        letter.appendChild(msg);

        body.appendChild(letter);
        envelope.append(flap, body);
        container.append(envelope);

        envelope.addEventListener('click', () => openEnvelope(envelope, env.message));
      });
    }

    /*------------------------------------*
      OPEN ENVELOPE & TYPING EFFECT
    *------------------------------------*/
    function openEnvelope(el, text) {
      if (el.classList.contains('open')) return;
      el.classList.add('open');
      typeMessage(el.querySelector('.message'), text, 40, () => {
        spawnParticles(el);
      });
      spawnKiss(el);
    }

    function typeMessage(container, text, speed, callback) {
      let idx = 0;
      container.innerHTML = '';
      const cursor = document.createElement('span');
      cursor.className = 'cursor';
      cursor.innerHTML = '&nbsp;';
      container.append(cursor);
      
      function type() {
        if (idx < text.length) {
          const char = text[idx++];
          if (char === '\n') container.innerHTML = container.innerHTML.replace(cursor.outerHTML, '') + '<br>';
          else container.innerHTML = container.innerHTML.replace(cursor.outerHTML, '') + char;
          container.append(cursor);
          setTimeout(type, speed);
        } else {
          cursor.remove();
          if (callback) callback();
        }
      }
      type();
    }

    /*------------------------------------*
      FLYING KISS EFFECT
    *------------------------------------*/
    function spawnKiss(el) {
      const kiss = document.createElement('span');
      kiss.className = 'kiss';
      kiss.textContent = '💋';
      const { left, top, width } = el.getBoundingClientRect();
      kiss.style.left = `${left + width/2}px`;
      kiss.style.top = `${top}px`;
      document.body.append(kiss);
      setTimeout(() => kiss.remove(), 1500);
    }

    /*------------------------------------*
      PARTICLE BURST EFFECT
    *------------------------------------*/
    function spawnParticles(el) {
      const container = document.getElementById('particles');
      for (let i = 0; i < 8; i++) {
        const p = document.createElement('span');
        p.className = 'particle';
        p.textContent = '❤️';
        const { left, top, width, height } = el.getBoundingClientRect();
        p.style.left = `${left + width/2}px`;
        p.style.top = `${top + height/2}px`;
        p.style.animationDelay = `${Math.random() * 0.3}s`;
        container.append(p);
        setTimeout(() => p.remove(), 4000);
      }
    }

    /*------------------------------------*
      CAT ROAMING ANIMATION
    *------------------------------------*/
    function roamCat() {
      const cat = document.getElementById('cat');
      const x = Math.random() * (window.innerWidth - cat.clientWidth);
      const y = Math.random() * (window.innerHeight - cat.clientHeight - 50);
      cat.style.transform = `translate(${x}px, ${y}px)`;
    }
    setInterval(roamCat, 6000);

    /*------------------------------------*
      AUDIO CONTROL TOGGLE
    *------------------------------------*/
    function setupAudioControl() {
      const music = document.getElementById('bgMusic');
      const control = document.getElementById('audioControl');
      const icon = document.getElementById('audioIcon');
      control.addEventListener('click', () => {
        if (music.paused) { music.play(); icon.src = 'audio_on.png'; }
        else { music.pause(); icon.src = 'audio_off.png'; }
      });
    }

    /*------------------------------------*
      INITIALIZATION
    *------------------------------------*/
    document.getElementById('beginBtn').addEventListener('click', () => {
      document.getElementById('intro').style.display = 'none';
      document.getElementById('envelopes').style.display = 'flex';
      document.getElementById('bgMusic').play().catch(()=>{});
      roamCat();
      createEnvelopes();
      setupAudioControl();
    });
  </script>
</body>
</html>
