# ocean-star
private page for my shimmers 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>For Jaana — Memories & Love</title>
<style>
  body {
    background: linear-gradient(135deg, #fceabb, #f8b500);
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0; padding: 0;
    color: #333;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  header {
    background: #ff6f61;
    color: white;
    padding: 40px 20px;
    text-align: center;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }
  header h1 {
    margin: 0;
    font-size: 3rem;
    letter-spacing: 2px;
    text-transform: uppercase;
  }
  header p {
    margin-top: 10px;
    font-size: 1.2rem;
    font-style: italic;
  }
  main {
    flex: 1;
    padding: 40px 20px;
    display: flex;
    justify-content: center;
  }
  .ad-container {
    background: white;
    max-width: 600px;
    padding: 30px 40px;
    border-radius: 20px;
    box-shadow: 0 8px 15px rgba(255,111,97,0.3);
    text-align: center;
    animation: fadeIn 1.5s ease forwards;
  }
  .ad-container h2 {
    font-size: 2rem;
    margin-bottom: 20px;
    color: #ff6f61;
  }
  .ad-container p {
    font-size: 1.1rem;
    line-height: 1.5;
    margin-bottom: 30px;
    color: #555;
  }
  .btn-open {
    background: #ff6f61;
    color: white;
    border: none;
    padding: 15px 35px;
    font-size: 1.2rem;
    border-radius: 50px;
    cursor: pointer;
    transition: background 0.3s ease;
    box-shadow: 0 6px 12px rgba(255,111,97,0.5);
    text-transform: uppercase;
    letter-spacing: 1.5px;
  }
  .btn-open:hover {
    background: #e65a4c;
  }
  @keyframes fadeIn {
    from {opacity: 0; transform: translateY(30px);}
    to {opacity: 1; transform: translateY(0);}
  }
  footer {
    background: #ff6f61;
    color: white;
    padding: 15px 0;
    text-align: center;
    font-size: 0.9rem;
    letter-spacing: 0.5px;
  }
</style>
</head>
<body>

<header>
  <h1>For Jaana</h1>
  <p>Your Star Shining Above the Ocean</p>
</header>

<main>
  <div class="ad-container">
    <h2>Open When You Need Me</h2>
    <p>Discover beautiful letters crafted with love — for moments when you miss me, feel stressed, or need a little comfort. Click the button below to open your special envelopes and let my words reach your heart.</p>
    <button class="btn-open" onclick="window.location.href='envelopes.html'">Open Your Envelopes</button>
  </div>
</main>

<footer>
  &copy; 2025 Your Star Above the Ocean — Made with ❤️
</footer>

</body>
</html>
