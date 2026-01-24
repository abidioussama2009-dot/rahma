# rahma[Untitled-1.html](https://github.com/user-attachments/files/24840234/Untitled-1.html)
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Rahma 💖 Universe of Love</title>
    <style>
      html,
      body {
        margin: 0;
        padding: 0;
        height: 100%;
        overflow: hidden;
        font-family: "Comic Sans MS", cursive, sans-serif;
        background: radial-gradient(circle at center, #120012, #450045);
        cursor: url("https://i.ibb.co/0sY9M4x/cursor-heart.png"), auto;
      }

      .card {
        position: relative;
        z-index: 2;
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(15px);
        border-radius: 40px;
        padding: 60px 80px;
        text-align: center;
        box-shadow: 0 0 60px #ff4d88;
        animation: heartbeat 3s infinite;
      }

      @keyframes heartbeat {
        0%,
        100% {
          transform: scale(1);
        }
        50% {
          transform: scale(1.05);
        }
      }

      h1 {
        font-size: 70px;
        color: #fff;
        text-shadow: 0 0 20px #ff4d88, 0 0 40px #ff1f6d;
        margin-bottom: 15px;
      }

      #message {
        font-size: 28px;
        color: #ffd6e8;
        margin-bottom: 35px;
        min-height: 40px;
      }

      button {
        padding: 20px 60px;
        font-size: 24px;
        border: none;
        border-radius: 50px;
        background: linear-gradient(45deg, #ff006a, #ffb347);
        color: white;
        cursor: pointer;
        box-shadow: 0 0 30px #ff4d88;
        transition: transform 0.2s, box-shadow 0.2s;
      }

      button:hover {
        transform: scale(1.2) rotate(-3deg);
        box-shadow: 0 0 50px #ff7ab8;
      }

      .kiss {
        position: absolute;
        font-size: 50px;
        pointer-events: none;
        animation: floatRandom 1s ease-out forwards;
      }

      @keyframes floatRandom {
        0% {
          opacity: 1;
          transform: scale(1) translate(0, 0);
        }
        50% {
          transform: scale(1.2) translate(0, -20px);
        }
        100% {
          opacity: 0;
          transform: scale(1.4) translate(0, -50px);
        }
      }

      #counter {
        margin-top: 15px;
        color: #fff;
        font-size: 20px;
      }

      .heart {
        position: absolute;
        pointer-events: none;
        animation: floatUp 5s linear forwards;
        z-index: 9999;
      }

      @keyframes floatUp {
        0% {
          transform: translateY(0) scale(0.5);
          opacity: 1;
        }
        100% {
          transform: translateY(-200px) scale(1.5);
          opacity: 0;
        }
      }

      canvas {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 1;
      }
    </style>
  </head>
  <body>
    <canvas id="bg"></canvas>

    <div class="card" id="card">
      <h1>Rahma 💖</h1>
      <div id="message"></div>
      <button onclick="sendKiss()">Send Magical Kiss 💋</button>
      <div id="counter">Kisses sent: 0</div>
    </div>

    <audio
      id="kissSound"
      src="https://www.soundjay.com/human/kiss-1.mp3"
    ></audio>

    <script>
      let kisses = 0;
      const messageText = "I LOVE YOU RAHMA 💕🌌";
      let messageIndex = 0;

      // Typewriter message
      function typeMessage() {
        const msg = document.getElementById("message");
        if (messageIndex < messageText.length) {
          msg.innerHTML += messageText[messageIndex++];
          setTimeout(typeMessage, 150);
        }
      }
      typeMessage();

      // Send kiss
      function sendKiss() {
        const card = document.getElementById("card");
        const counter = document.getElementById("counter");
        const audio = document.getElementById("kissSound");

        audio.currentTime = 0;
        audio.play();

        for (let i = 0; i < 10; i++) {
          const kiss = document.createElement("div");
          kiss.className = "kiss";
          kiss.innerHTML = "💋💖";

          const rect = card.getBoundingClientRect();
          const x = Math.random() * (rect.width - 50);
          const y = Math.random() * (rect.height - 50);
          kiss.style.left = x + "px";
          kiss.style.top = y + "px";

          card.appendChild(kiss);
          setTimeout(() => kiss.remove(), 1000);
        }

        const rect = card.getBoundingClientRect();
        for (let i = 0; i < 30; i++) {
          createHeart(rect.left + rect.width / 2, rect.top + rect.height / 2);
        }

        kisses++;
        counter.innerHTML = "Kisses sent: " + kisses;
      }

      // Floating hearts
      function createHeart(x, y) {
        const heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = Math.random() < 0.5 ? "❤️" : "💖";
        heart.style.left = x + "px";
        heart.style.top = y + "px";
        heart.style.fontSize = 20 + Math.random() * 20 + "px";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 5000);
      }

      // ✅ MODIFIED PART: heart ALWAYS appears when mouse moves
      document.addEventListener("mousemove", (e) => {
        createHeart(e.clientX, e.clientY);
      });

      // Background animation (unchanged)
      const canvas = document.getElementById("bg");
      const ctx = canvas.getContext("2d");
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;

      let stars = [],
        shootingStars = [],
        fireworks = [];

      function initStars() {
        stars = [];
        for (let i = 0; i < 300; i++) {
          stars.push({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            r: Math.random() * 1.5,
            dx: (Math.random() - 0.5) * 0.1,
            dy: (Math.random() - 0.5) * 0.1,
          });
        }
      }

      function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        for (let s of stars) {
          ctx.beginPath();
          ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
          ctx.fillStyle = "#fff";
          ctx.fill();
          s.x += s.dx;
          s.y += s.dy;
          if (s.x < 0) s.x = canvas.width;
          if (s.x > canvas.width) s.x = 0;
          if (s.y < 0) s.y = canvas.height;
          if (s.y > canvas.height) s.y = 0;
        }

        requestAnimationFrame(animate);
      }

      initStars();
      animate();
      window.addEventListener("resize", () => {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        initStars();
      });
    </script>
  </body>
</html>
