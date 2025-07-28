<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Open When – For Jaana</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom right, #dbcdf0, #d0f0ef);
      font-family: 'Segoe UI', cursive;
      overflow-x: hidden;
    }

    h1 {
      text-align: center;
      color: #a84877;
      padding: 20px;
      font-size: 2em;
    }

    .envelope-grid {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 20px;
      justify-items: center;
      padding: 30px;
    }

    .envelope {
      width: 100px;
      height: 70px;
      background: #fcdada;
      border: 2px solid #efb0c9;
      border-radius: 6px;
      position: relative;
      cursor: pointer;
      transition: transform 0.3s;
    }

    .envelope:hover {
      transform: scale(1.1);
    }

    .envelope::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background:
        linear-gradient(135deg, transparent 50%, #efb0c9 50%),
        linear-gradient(-135deg, transparent 50%, #efb0c9 50%);
      background-repeat: no-repeat;
      background-size: 50% 50%;
      background-position: top left, top right;
    }

    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.7);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 10;
    }

    .modal-content {
      background: #fff0f5;
      padding: 20px;
      border-radius: 15px;
      max-width: 600px;
      max-height: 80vh;
      overflow-y: auto;
      font-size: 1.1em;
      box-shadow: 0 4px 20px rgba(0,0,0,0.2);
      position: relative;
    }

    .close {
      position: absolute;
      top: 8px;
      right: 12px;
      font-size: 24px;
      cursor: pointer;
    }

    .cat {
      width: 120px;
      position: absolute;
      bottom: 0;
      left: -150px;
      animation: walk 30s linear infinite;
    }

    @keyframes walk {
      0% { left: -150px; }
      50% { left: 100%; transform: scaleX(1); }
      50.1% { transform: scaleX(-1); }
      100% { left: -150px; transform: scaleX(-1); }
    }
  </style>
</head>
<body>

  <h1>💌 Click an Envelope, Jaana 💌</h1>

  <div class="envelope-grid">
    <div class="envelope" data-id="0" title="Open When You're Sad"></div>
    <div class="envelope" data-id="1" title="About Distance & Pain"></div>
    <!-- Add more envelopes if needed -->
  </div>

  <img src="https://i.imgur.com/L6kVl5I.png" alt="Cat" class="cat">

  <div class="modal" id="modal">
    <div class="modal-content">
      <span class="close" onclick="closeModal()">&times;</span>
      <div id="letterText"></div>
    </div>
  </div>

  <script>
    const letters = [
      `My Jaana, My Shining Star,<br><br>
      If your heart feels heavy today, I want this letter to hold it for a while.
      You always try to be strong — but even the stars deserve to rest.
      On days when your eyes are teary and the world feels too loud,
      I hope you remember that you’re never truly alone...<br><br>
      (more of your message here)
      `,

      `Jaana, Please Read With Your Heart<br><br>
      I know this is not easy. For either of us.
      The distance. The changes. The fights. The ache. The helplessness...
      But still, with all of that, we are here.
      Breathing, hoping, holding on to the tiny pieces of what we believe in.
      You matter. This matters...<br><br>
      (more of your message here)
      `
    ];

    const envelopes = document.querySelectorAll('.envelope');
    const modal = document.getElementById('modal');
    const letterText = document.getElementById('letterText');

    envelopes.forEach(env => {
      env.addEventListener('click', () => {
        const id = env.getAttribute('data-id');
        letterText.innerHTML = letters[id];
        modal.style.display = 'flex';
      });
    });

    function closeModal() {
      modal.style.display = 'none';
    }
  </script>

</body>
</html>

