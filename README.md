<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>From the star above the ocean</title>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <!-- Canvas-Confetti CDN -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
  <style>
    /*------------------------------------*
      ROOT & VARIABLES
    *------------------------------------*/
    :root {
      --color-primary: #d6336c;
      --color-secondary: #fdeef4;
      --color-accent: #e6a1b8;
      --transition-speed: 0.7s;
      --shadow-light: rgba(0,0,0,0.15);
    }
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    html, body {
      width: 100%;
      height: 100%;
      overflow: auto;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(180deg, var(--color-secondary), #fff5f8);
    }

    /*------------------------------------*
      NAVIGATION & LAYOUT
    *------------------------------------*/
    #navbar {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 1rem;
      z-index: 1000;
    }
    .nav-btn {
      padding: 0.5rem 1rem;
      background: rgba(255,255,255,0.6);
      backdrop-filter: blur(10px);
      border-radius: 20px;
      border: 2px solid var(--color-accent);
      cursor: pointer;
      font-family: 'Playfair Display', serif;
      font-weight: 600;
      color: var(--color-primary);
      transition: background var(--transition-speed);
    }
    .nav-btn.active, .nav-btn:hover {
      background: rgba(255,255,255,0.9);
    }

    /*------------------------------------*
      PARALLAX BACKGROUND LAYERS (5 LAYERS)
    *------------------------------------*/
    .parallax-layer {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-size: cover;
      background-attachment: fixed;
      will-change: transform;
    }
    #layer1 { background-image: url('layer1.png'); z-index: 1; opacity: 0.6; }
    #layer2 { background-image: url('layer2.png'); z-index: 2; opacity: 0.5; }
    #layer3 { background-image: url('layer3.png'); z-index: 3; opacity: 0.4; }
    #layer4 { background-image: url('layer4.png'); z-index: 4; opacity: 0.3; }
    #layer5 { background-image: url('layer5.png'); z-index: 5; opacity: 0.2; }

    /*------------------------------------*
      CANVAS SPARKLES
    *------------------------------------*/
    #sparkleCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 10;
    }

    /*------------------------------------*
      INTRO SCREEN
    *------------------------------------*/
    #intro {
      position: relative;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      backdrop-filter: blur(5px);
      z-index: 100;
    }
    #intro h1 {
      font-family: 'Dancing Script', cursive;
      font-size: 4rem;
      color: var(--color-primary);
      text-shadow: 3px 3px 6px var(--shadow-light);
    }
    #intro button {
      margin-top: 1rem;
      font-family: 'Playfair Display', serif;
      font-size: 1.2rem;
      padding: 1rem 2rem;
      border: none;
      border-radius: 30px;
      background: var(--color-primary);
      color: #fff;
      cursor: pointer;
      box-shadow: 0 4px 12px var(--shadow-light);
      transition: transform 0.2s;
    }
    #intro button:hover {
      transform: scale(1.05);
    }

    /*------------------------------------*
      LETTERS SECTION
    *------------------------------------*/
    #lettersSection {
      display: none;
      position: relative;
      padding: 4rem 2rem;
      overflow-y: auto;
      z-index: 100;
    }
    .envelope-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
    }
    .envelope {
      perspective: 1200px;
      cursor: pointer;
      position: relative;
      height: 0;
      padding-bottom: 60%;
      transform-style: preserve-3d;
      will-change: transform;
      transition: transform 0.2s ease;
    }
    .envelope:hover {
      box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    }
    .flap, .body {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 12px;
    }
    .flap {
      background: linear-gradient(135deg, var(--color-accent), var(--color-secondary));
      border: 2px solid var(--color-primary);
      transform-origin: top;
      transition: transform var(--transition-speed) ease;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      z-index: 2;
    }
    .flap .label {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      color: var(--color-primary);
    }
    .flap .open-text {
      font-family: 'Poppins', sans-serif;
      font-size: 0.85rem;
      color: var(--color-accent);
      margin-top: 0.2rem;
    }
    .body {
      background: #fff;
      top: 0;
      left: 0;
      transform: rotateX(0deg);
      border: 2px solid var(--color-accent);
      z-index: 1;
    }
    .letter {
      position: absolute;
      bottom: 0;
      left: 5%;
      width: 90%;
      height: 90%;
      background: #fff;
      border-radius: 8px;
      padding: 1rem;
      box-shadow: 0 4px 12px var(--shadow-light);
      transform: translateY(120%);
      transition: transform var(--transition-speed) ease var(--transition-speed);
      overflow: auto;
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      line-height: 1.6;
      color: #333;
      white-space: pre-wrap;
    }
    .envelope.open .flap {
      transform: rotateX(-180deg);
    }
    .envelope.open .letter {
      transform: translateY(0);
    }

    /*------------------------------------*
      JOURNAL SECTION
    *------------------------------------*/
    #journalSection {
      display: none;
      position: relative;
      padding: 3rem 2rem;
      color: #333;
      z-index: 100;
    }
    #journalSection h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2.5rem;
      margin-bottom: 1rem;
      text-align: center;
    }
    #journalSection textarea {
      width: 100%;
      height: 200px;
      border: 2px solid var(--color-accent);
      border-radius: 10px;
      padding: 1rem;
      font-family: 'Poppins', sans-serif;
      font-size: 1rem;
      resize: vertical;
    }
    #journalSection button {
      margin-top: 0.5rem;
      font-family: 'Playfair Display', serif;
      padding: 0.6rem 1.2rem;
      background: var(--color-primary);
      color: #fff;
      border: none;
      border-radius: 20px;
      cursor: pointer;
    }
    #entriesList {
      margin-top: 2rem;
      max-height: 300px;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
    .entry {
      background: #fff;
      border-left: 4px solid var(--color-primary);
      padding: 0.8rem;
      border-radius: 6px;
      font-family: 'Poppins', sans-serif;
      font-size: 0.95rem;
      line-height: 1.4;
    }

    /*------------------------------------*
      AUDIO & CAT
    *------------------------------------*/
    #audioControl {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 50px;
      height: 50px;
      background: rgba(255,255,255,0.8);
      border-radius: 50%;
      display: flex;
      align-items: center;justify-content: center;
      cursor: pointer;
      z-index: 100;
    }
    #audioControl img { width: 24px; height: 24px; }
    #cat {
      position: absolute;
      bottom: 5%;
      left: 5%;
      width: 140px;
      transition: transform 5s ease-in-out;
      z-index: 50;
    }

    /*------------------------------------*
      SCROLLBAR STYLING
    *------------------------------------*/
    ::-webkit-scrollbar { width: 12px; }
    ::-webkit-scrollbar-track { background: rgba(0,0,0,0.05); }
    ::-webkit-scrollbar-thumb { background: rgba(0,0,0,0.1); border-radius: 6px; }
  </style>
</head>
<body>
  <!-- Parallax Layers -->
  <div id="layer1" class="parallax-layer"></div>
  <div id="layer2" class="parallax-layer"></div>
  <div id="layer3" class="parallax-layer"></div>
  <div id="layer4" class="parallax-layer"></div>
  <div id="layer5" class="parallax-layer"></div>

  <!-- Navigation -->
  <div id="navbar">
    <div class="nav-btn active" data-target="intro">Home</div>
    <div class="nav-btn" data-target="lettersSection">Letters</div>
    <div class="nav-btn" data-target="journalSection">Journal</div>
  </div>

  <!-- Sparkle Canvas -->
  <canvas id="sparkleCanvas"></canvas>

  <!-- Intro Screen -->
  <div id="intro">
    <h1>From the star above the ocean ❤️</h1>
    <button id="beginBtn">Begin</button>
  </div>

  <!-- Letters Section -->
  <section id="lettersSection">
    <div class="envelope-container"></div>
  </section>

  <!-- Journal Section -->
  <section id="journalSection">
    <h2>Your Safe Place</h2>
    <textarea id="journalInput" placeholder="Write your thoughts..."></textarea>
    <button id="saveEntryBtn">Save Entry</button>
    <div id="entriesList"></div>
  </section>

  <!-- Audio Control -->
  <div id="audioControl"><img id="audioIcon" src="audio_on.png" alt="Audio Toggle"></div>
  <audio id="bgMusic" src="music.mp3" loop></audio>

  <!-- Persian Cat -->
  <img id="cat" src="persian_cat.png" alt="Persian Cat">

  <script>
    // Utility selectors
    const $ = s => document.querySelector(s);
    const $$ = s => Array.from(document.querySelectorAll(s));

    // Sparkle Canvas Setup
    const canvas = $('#sparkleCanvas');
    const ctx = canvas.getContext('2d');
    let sparkles = [];
    function resizeCanvas() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();
    class Sparkle { constructor() { this.reset(); } reset() { this.x= Math.random()*canvas.width; this.y= Math.random()*canvas.height; this.alpha=1; this.size=1+Math.random()*2; } update() { this.y -=0.5; this.alpha -=0.01; if(this.alpha<=0) this.reset(); } draw() { ctx.globalAlpha=this.alpha; ctx.fillStyle='#fff'; ctx.fillRect(this.x,this.y,this.size,this.size); }}
    for(let i=0;i<200;i++) sparkles.push(new Sparkle());
    function animateSparkles() { ctx.clearRect(0,0,canvas.width,canvas.height); sparkles.forEach(s=>{ s.update(); s.draw(); }); requestAnimationFrame(animateSparkles); }
    animateSparkles();

    // Parallax on Letters Scroll
    const scrollContainer = $('#lettersSection');
    scrollContainer.addEventListener('scroll',()=>{
      const y=scrollContainer.scrollTop;
      [1,2,3,4,5].forEach(i=>{
        document.getElementById('layer'+i).style.transform=`translateY(${y*0.2*i}px)`;
      });
    });

    // Envelope Data
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

    // 3D Tilt Handlers
    function applyTilt(el,e){ const r=el.getBoundingClientRect(),x=e.clientX-(r.left+r.width/2),y=e.clientY-(r.top+r.height/2),rx=(y/r.height)*15,ry=-(x/r.width)*15; el.style.transform=`rotateX(${rx}deg) rotateY(${ry}deg)`; }
    function resetTilt(el){ el.style.transform='rotateX(0) rotateY(0)'; }

    // Confetti
    function triggerConfetti(el){ const r=el.getBoundingClientRect(); confetti({ particleCount:80, spread:70, origin:{ x:(r.left+r.width/2)/window.innerWidth, y:(r.top+r.height/2)/window.innerHeight } }); }

    // Particles
    function spawnParticles(el){ const container=document.createElement('div'); container.style.position='absolute'; container.style.top='0'; container.style.left='0'; el.append(container); for(let i=0;i<10;i++){ const p=document.createElement('span'); p.textContent='❤️'; p.style.position='absolute'; p.style.left=`${50+Math.random()*50}%`; p.style.top=`${50+Math.random()*50}%`; p.style.opacity=1; p.style.transition='transform 2s ease, opacity 2s'; container.append(p); setTimeout(()=>{ p.style.transform=`translateY(-100px) scale(1.5)`; p.style.opacity=0; },50); setTimeout(()=>p.remove(),2050); } }

    // Flying Kiss
    function spawnKiss(el){ const kiss=document.createElement('div'); kiss.textContent='💋'; kiss.style.position='absolute'; const r=el.getBoundingClientRect(); kiss.style.left=`${r.left+r.width/2}px`; kiss.style.top=`${r.top}px`; kiss.style.fontSize='2rem'; document.body.append(kiss); setTimeout(()=>{ kiss.style.transition='transform 1.2s, opacity 1.2s'; kiss.style.transform='translateY(-140px) scale(1.6)'; kiss.style.opacity=0; },50); setTimeout(()=>kiss.remove(),1250); }

    // Typing Effect
    function typeMessage(el,text,speed){ let i=0; el.innerHTML=''; const c=document.createElement('span'); c.className='cursor'; el.append(c); (function t(){ if(i<text.length){ el.innerHTML=el.innerHTML.replace(c.outerHTML,'')+(text[i]==='\n'?'<br>':text[i]); el.append(c); i++; setTimeout(t,speed);} else c.remove(); })(); }

    // Initialize Letters
    function initLetters(){ const container=$('.envelope-container'); container.innerHTML=''; envelopesData.forEach(env=>{ const el=document.createElement('div'); el.className='envelope'; el.innerHTML=`<div class="flap"><div class="label">${env.icon} ${env.label}</div><div class="open-text">Open When</div></div><div class="body"><div class="letter"><div class="message"></div></div></div>`; container.append(el); el.addEventListener('mousemove',e=>applyTilt(el,e)); el.addEventListener('mouseleave',()=>resetTilt(el)); el.addEventListener('click',()=>{ if(el.classList.contains('open'))return; el.classList.add('open'); typeMessage(el.querySelector('.message'),env.message,40); triggerConfetti(el); spawnParticles(el); spawnKiss(el); }); }); }

    // Journal
    function loadEntries(){ const list=$('#entriesList'); list.innerHTML=''; const entries=JSON.parse(localStorage.getItem('journalEntries')||'[]'); entries.reverse().forEach(e=>{ const d=document.createElement('div'); d.className='entry'; d.textContent=e; list.append(d);} ); }
    $('#saveEntryBtn').addEventListener('click',()=>{ const t=$('#journalInput'); const v=t.value.trim(); if(!v)return; const arr=JSON.parse(localStorage.getItem('journalEntries')||'[]'); arr.push(v); localStorage.setItem('journalEntries',JSON.stringify(arr)); t.value=''; loadEntries(); });

    // Audio Control
    function initAudio(){ const music=$('#bgMusic'), icon=$('#audioIcon'); $('#audioControl').addEventListener('click',()=>{ if(music.paused){ music.play(); icon.src='audio_on.png'; }else{ music.pause(); icon.src='audio_off.png'; }}); music.play().catch(()=>{}); }

    // Cat Roam
    function roamCat(){ const cat=$('#cat'); const x=Math.random()*(window.innerWidth-cat.clientWidth), y=Math.random()*(window.innerHeight-cat.clientHeight-50); cat.style.transform=`translate(${x}px,${y}px)`;} setInterval(roamCat,6000);

    // Begin Experience
    $('#beginBtn').addEventListener('click',()=>{ $('#intro').style.display='none'; initLetters(); setTimeout(()=>$('.nav-btn[data-target="lettersSection"]').click(),100); initAudio(); roamCat(); loadEntries(); });
  </script>
</body>
</html>

