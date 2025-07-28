<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For You 💌</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: linear-gradient(to bottom right, #ffe6f0, #f9f0ff);
      font-family: 'Segoe UI', sans-serif;
      overflow: hidden;
    }

    #entrance {
      position: fixed;
      inset: 0;
      background: linear-gradient(135deg, #ffd6e0, #e6e6ff);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      z-index: 9999;
    }

    #entrance h1 {
      font-size: 3em;
      color: #cc3366;
      margin-bottom: 20px;
    }

    #entrance button {
      padding: 15px 30px;
      font-size: 1.2em;
      border: none;
      background-color: #ff6699;
      color: white;
      border-radius: 30px;
      cursor: pointer;
      box-shadow: 0 5px 10px rgba(0,0,0,0.2);
    }

    #mainContent {
      display: none;
    }

    h1 {
      text-align: center;
      margin-top: 40px;
      font-size: 2.5em;
      color: #cc3366;
    }

    .envelope-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 30px;
      gap: 40px;
    }

    .envelope-container {
      position: relative;
      width: 280px;
      height: 220px;
      cursor: pointer;
      perspective: 1000px;
    }

    .envelope {
      position: relative;
      width: 100%;
      height: 100%;
      background: #ff99aa;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      overflow: hidden;
      transition: transform 0.8s ease;
    }

    .envelope-label {
      position: absolute;
      top: 12px;
      left: 0;
      width: 100%;
      text-align: center;
      font-size: 18px;
      font-weight: bold;
      color: #cc3366;
      z-index: 3;
      background: #ffccd5;
      padding: 6px 0;
    }

    .envelope:before {
      content: "";
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 50%;
      background: #ffccd5;
      transform: rotateX(0deg);
      transform-origin: top;
      transition: transform 1s ease;
      z-index: 2;
    }

    .envelope.open:before {
      transform: rotateX(-140deg);
    }

    .message {
      opacity: 0;
      padding: 40px 25px 25px 25px;
      background: #fff;
      height: 100%;
      font-size: 16px;
      line-height: 1.8;
      color: #333;
      overflow: hidden;
      z-index: 1;
      position: relative;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
    }

    .envelope.open .message {
      animation: typewriter 3s steps(80, end) 1 forwards;
    }

    @keyframes typewriter {
      from { opacity: 1; width: 0; }
      to { opacity: 1; width: 100%; }
    }

    .sparkles {
      position: fixed;
      top: 0;
      left: 0;
      pointer-events: none;
      width: 100vw;
      height: 100vh;
      z-index: 999;
    }

    .sparkle {
      position: absolute;
      width: 8px;
      height: 8px;
      background: pink;
      border-radius: 50%;
      animation: sparkle 2s infinite;
    }

    @keyframes sparkle {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(100px) scale(0); opacity: 0; }
    }

    .cat {
      position: fixed;
      bottom: 10px;
      left: -200px;
      width: 150px;
      animation: catWalk 20s linear infinite;
      z-index: 5;
    }

    @keyframes catWalk {
      0% { left: -200px; }
      50% { left: 100vw; }
      100% { left: -200px; }
    }

    audio {
      display: none;
    }
  </style>
</head>
<body>
  <!-- Remaining HTML will follow here -->
