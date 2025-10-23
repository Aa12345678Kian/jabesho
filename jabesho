<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎁 بازی جعبه شانس</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #f3f4f6;
      text-align: center;
      direction: rtl;
      padding: 20px;
    }
    h2 {
      color: #333;
    }
    .game-container {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin: 40px 0;
    }
    .box {
      width: 100px;
      height: 100px;
      background-color: #0088cc;
      border-radius: 15px;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      font-size: 18px;
      cursor: pointer;
      transition: transform 0.3s ease;
    }
    .box.opened {
      background-color: #10b981;
      cursor: default;
    }
    .hidden-text {
      display: none;
    }
    button {
      background-color: #ef4444;
      color: white;
      border: none;
      border-radius: 10px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #dc2626;
    }
    @keyframes shuffle {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-40px); }
      50% { transform: translateX(40px); }
      75% { transform: translateX(-20px); }
    }
  </style>
</head>
<body>

  <h2>🎁 بازی جعبه شانس</h2>
  <p>دکمه شروع رو بزن تا جعبه‌ها جابه‌جا بشن، بعد یکی رو انتخاب کن!</p>

  <div class="game-container" id="game">
    <div class="box" data-result="دوباره امتحان کن 🔁">?</div>
    <div class="box" data-result="پوچ 😅">?</div>
    <div class="box" data-result="پوچ 😅">?</div>
  </div>

  <button id="startBtn">شروع بازی 🎮</button>
  <button id="resetBtn" style="display:none;">بازی دوباره 🔁</button>

  <h3 id="resultText"></h3>

  <script>
    const boxes = document.querySelectorAll('.box');
    const startBtn = document.getElementById('startBtn');
    const resetBtn = document.getElementById('resetBtn');
    const resultText = document.getElementById('resultText');
    const game = document.getElementById('game');

    let shuffling = false;

    function shuffleBoxes() {
      shuffling = true;
      resultText.textContent = '';
      boxes.forEach(box => box.classList.remove('opened'));
      game.style.pointerEvents = 'none';
      boxes.forEach(box => box.style.animation = 'shuffle 1s ease-in-out infinite');
      
      setTimeout(() => {
        boxes.forEach(box => box.style.animation = '');
        const order = [0, 1, 2].sort(() => Math.random() - 0.5);
        game.innerHTML = '';
        order.forEach(i => game.appendChild(boxes[i]));
        game.style.pointerEvents = 'auto';
        shuffling = false;
      }, 3000);
    }

    function openBox(e) {
      if (shuffling) return;
      const box = e.target;
      if (box.classList.contains('opened')) return;

      const result = box.dataset.result;
      box.textContent = result;
      box.classList.add('opened');
      resultText.textContent = `نتیجه: ${result}`;
      startBtn.style.display = 'none';
      resetBtn.style.display = 'inline-block';
      game.style.pointerEvents = 'none';
    }

    function resetGame() {
      boxes.forEach(box => {
        box.textContent = '?';
        box.classList.remove('opened');
      });
      resultText.textContent = '';
      startBtn.style.display = 'inline-block';
      resetBtn.style.display = 'none';
    }

    startBtn.addEventListener('click', shuffleBoxes);
    boxes.forEach(box => box.addEventListener('click', openBox));
    resetBtn.addEventListener('click', resetGame);
  </script>

</body>
</html>
