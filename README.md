<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Happy Birthday Bhai!</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      background-color: #e0f7fa;
      margin: 0;
      overflow: hidden;
      position: relative;
    }

    .background-text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 80px;
      font-weight: bold;
      color: rgba(33, 150, 243, 0.1);
      z-index: 0;
      white-space: nowrap;
      pointer-events: none;
    }

    .container {
      position: relative;
      z-index: 1;
      margin-top: 50px;
      background: white;
      padding: 30px;
      width: 80%;
      max-width: 600px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      margin-left: auto;
      margin-right: auto;
      animation: popUp 0.8s ease;
    }

    @keyframes popUp {
      0% { transform: scale(0.8); opacity: 0; }
      100% { transform: scale(1); opacity: 1; }
    }

    .message-box {
      font-size: 18px;
      line-height: 1.6;
      color: #444;
    }

    .btn {
      padding: 12px 24px;
      margin: 10px;
      border: none;
      cursor: pointer;
      font-size: 16px;
      border-radius: 8px;
      transition: transform 0.3s;
    }

    .btn:hover {
      transform: scale(1.05);
    }

    .btn-hello {
      background-color: #4CAF50;
      color: white;
    }

    .btn-no {
      background-color: #f44336;
      color: white;
    }

    .btn-next, .btn-restart {
      background-color: #008CBA;
      color: white;
    }

    .emoji-burst {
      position: absolute;
      font-size: 24px;
      animation: burst 1s ease-out forwards;
      pointer-events: none;
    }

    @keyframes burst {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-150px) scale(1.5); opacity: 0; }
    }
  </style>
</head>
<body>

  <div class="background-text">Happy Birthday Chhote Bhai!</div>

  <div class="container" id="greeting">
    <h2>Hey there!</h2>
    <button class="btn btn-hello" onclick="startMessage()">Say Hello</button>
    <button class="btn btn-no" onclick="notInterested()">Not Interested to Talk</button>
  </div>

  <div class="container" id="message" style="display: none;">
    <h2>🎉 Happy Birthday Chhote Bhai! 🎂🎈</h2>
    <p id="message-content" class="message-box"></p>
    <button class="btn btn-next" onclick="nextMessage(this)">Next 🎈</button>
    <button class="btn btn-restart" onclick="restart(this)" style="display: none;">Back to Begin 🔁</button>
  </div>

  <script>
    const messages = [
      "Happy Birthday to the coolest Chhote Bhai! 🧁🎉",
      "From the day we met, you’ve been like the little brother I never knew I needed.",
      "You bring so much fun, madness, and joy into life — like a walking meme machine 🤪.",
      "Your goofy energy, loyal heart, and infinite chatter make every day brighter.",
      "May you always stay happy, keep shining, and never lose that spark that makes you YOU.",
      "Even when you're annoying (which is often 😆), I wouldn’t trade you for anything!",
      "Loads of love, hugs, and crazy wishes your way. Happy Birthday, Bhai! 🎈🎂🫶"
    ];

    let index = 0;

    function startMessage() {
      document.getElementById("greeting").style.display = "none";
      document.getElementById("message").style.display = "block";
      showMessage();
    }

    function showMessage() {
      const content = document.getElementById("message-content");
      content.innerHTML = messages[index];

      const restartBtn = document.querySelector('.btn-restart');
      const nextBtn = document.querySelector('.btn-next');

      if (index === messages.length - 1) {
        restartBtn.style.display = "inline-block";
        nextBtn.style.display = "none";
      } else {
        restartBtn.style.display = "none";
        nextBtn.style.display = "inline-block";
      }
    }

    function nextMessage(btn) {
      if (index < messages.length - 1) {
        index++;
        showMessage();
        createBurst(btn);
      }
    }

    function restart(btn) {
      index = 0;
      showMessage();
      createBurst(btn);
    }

    function notInterested() {
      const response = confirm("C'mon yaar, don’t ignore me! 🙃");
      if (response) {
        location.reload();
      }
    }

    function createBurst(btn) {
      const emojis = ['🎂','🎈','✨','🎉','🫶'];
      for (let i = 0; i < 5; i++) {
        const burst = document.createElement('span');
        burst.className = 'emoji-burst';
        burst.textContent = emojis[Math.floor(Math.random() * emojis.length)];
        burst.style.left = Math.random() * 100 + '%';
        burst.style.top = '-10px';
        btn.appendChild(burst);
        setTimeout(() => burst.remove(), 1000);
      }
    }
  </script>
</body>
</html>



