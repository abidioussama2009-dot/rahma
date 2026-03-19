[Untitled-2.html](https://github.com/user-attachments/files/26117398/Untitled-2.html)
<!DOCTYPE html>
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>For My Love 💖</title>

    <style>
      body {
        margin: 0;
        padding: 0;
        font-family: Arial, sans-serif;
        color: white;
        text-align: center;
        overflow: hidden;
        background: linear-gradient(135deg, #ff4da6, #330033);
        animation: gradientShift 10s ease infinite;
      }

      @keyframes gradientShift {
        0% {
          background: linear-gradient(135deg, #ff4da6, #330033);
        }
        25% {
          background: linear-gradient(135deg, #ff66cc, #330066);
        }
        50% {
          background: linear-gradient(135deg, #ff99dd, #660033);
        }
        75% {
          background: linear-gradient(135deg, #ff4da6, #660066);
        }
        100% {
          background: linear-gradient(135deg, #ff4da6, #330033);
        }
      }

      .container {
        position: relative;
        z-index: 2;
        margin-top: 50px;
      }

      #message {
        display: none;
        font-size: 22px;
        max-width: 700px;
        margin: 30px auto;
        line-height: 1.6;
        animation: fadeIn 1s forwards;
        text-shadow: 0 0 20px #ff99dd, 0 0 40px #ff66cc;
      }

      @keyframes fadeIn {
        from {
          opacity: 0;
          transform: translateY(20px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      button {
        padding: 15px 35px;
        font-size: 20px;
        border: none;
        border-radius: 30px;
        margin: 15px;
        cursor: pointer;
        transition: 0.3s;
      }

      button:hover {
        transform: scale(1.1);
      }

      #yesBtn {
        background: #00ff99;
        color: black;
      }
      #noBtn {
        background: #ff3333;
        color: white;
      }
      #fireworkBtn {
        background: #ffcc33;
        color: black;
      }

      .kiss {
        position: absolute;
        font-size: 20px;
        pointer-events: none;
        animation: floatUp 2s linear forwards;
      }

      @keyframes floatUp {
        0% {
          opacity: 1;
          transform: translateY(0);
        }
        100% {
          opacity: 0;
          transform: translateY(-80px);
        }
      }

      .heart {
        position: absolute;
        font-size: 25px;
        animation: floatHeart 4s linear forwards;
      }

      @keyframes floatHeart {
        0% {
          opacity: 1;
          transform: translateY(0) rotate(0deg);
        }
        100% {
          opacity: 0;
          transform: translateY(-400px) rotate(360deg);
        }
      }

      .firework {
        position: absolute;
        width: 8px;
        height: 8px;
        border-radius: 50%;
        pointer-events: none;
      }
    </style>
  </head>

  <body>
    <div class="container" id="container">
      <h1>💖 Do You Love Me? 💖</h1>

      <button id="yesBtn" onclick="showMessage()">YES 💕</button>
      <button id="noBtn" onclick="clickNo()">NO 💔</button>

      <div id="message">
        My beautiful Rahma 💖<br /><br />
        From the first moment I saw you, I knew you were special. Your smile
        lights up my world brighter than the sun. Your eyes shine like stars in
        the night sky. You are the most beautiful girl I have ever seen, not
        only outside but inside too. <br /><br />
        Your kindness, your laugh, your energy — everything about you is perfect
        to me. I feel lucky every single day to have you in my life. I hope we
        continue making memories, smiling together, supporting each other, and
        growing stronger in love. 💕<br /><br />
        Happy Birthday my love 🎂💖
        <br />
        <button id="fireworkBtn" onclick="fireworks()">Fireworks 🎆</button>
      </div>
    </div>

    <script>
      document.addEventListener("mousemove", function (e) {
        let kiss = document.createElement("div");
        kiss.className = "kiss";
        kiss.innerHTML = "💋";
        kiss.style.left = e.pageX + "px";
        kiss.style.top = e.pageY + "px";
        document.body.appendChild(kiss);
        setTimeout(() => kiss.remove(), 2000);
      });

      function loveExplosion() {
        for (let i = 0; i < 25; i++) {
          let heart = document.createElement("div");
          heart.className = "heart";
          heart.innerHTML = "💖";
          heart.style.left = Math.random() * window.innerWidth + "px";
          heart.style.top = Math.random() * window.innerHeight + "px";
          document.body.appendChild(heart);
          setTimeout(() => heart.remove(), 4000);
        }
      }

      function showMessage() {
        const container = document.getElementById("container");
        const message = document.getElementById("message");
        container.innerHTML = "";
        container.appendChild(message);
        message.style.display = "block";
        loveExplosion();
      }

      let noClicks = 0;
      function clickNo() {
        noClicks++;
        const yesBtn = document.getElementById("yesBtn");
        let currentScale =
          parseFloat(yesBtn.style.transform.replace(/[^0-9.]/g, "")) || 1;
        currentScale += 0.15;
        yesBtn.style.transform = `scale(${currentScale})`;
        loveExplosion();
        if (noClicks >= 7) {
          const noBtn = document.getElementById("noBtn");
          noBtn.innerText = "YES 💕";
          noBtn.style.background = "#00ff99";
        }
      }

      function fireworks() {
        for (let i = 0; i < 30; i++) {
          let fire = document.createElement("div");
          fire.className = "firework";
          fire.style.background = `hsl(${Math.random() * 360}, 100%, 50%)`;

          let startX = Math.random() * window.innerWidth;
          let startY = Math.random() * window.innerHeight;
          fire.style.left = startX + "px";
          fire.style.top = startY + "px";
          document.body.appendChild(fire);
          let angle = Math.random() * 2 * Math.PI;
          let distance = 50 + Math.random() * 150;
          let x = distance * Math.cos(angle);
          let y = distance * Math.sin(angle);

          fire.animate(
            [
              { transform: `translate(0,0) scale(1)`, opacity: 1 },
              { transform: `translate(${x}px, ${y}px) scale(1.5)`, opacity: 0 },
            ],
            {
              duration: 1000 + Math.random() * 1000,
              easing: "ease-out",
            }
          );

          setTimeout(() => fire.remove(), 2000);
        }
      }
    </script>
  </body>
</html>
