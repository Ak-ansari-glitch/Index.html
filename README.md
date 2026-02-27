<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Love Kausar 💖</title>
<style>
  body {
    font-family: 'Comic Sans MS', cursive, sans-serif;
    background: #ffe6f0;
    text-align: center;
    color: #ff3366;
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }
  h1 { font-size: 2em; margin-top: 20px; }
  .game-container { padding: 20px; position: relative; height: 100vh; }
  button {
    background-color: #ff6699;
    border: none;
    padding: 15px 30px;
    margin: 10px;
    font-size: 1em;
    color: white;
    border-radius: 10px;
    cursor: pointer;
  }
  button:hover { background-color: #ff3366; }
  .hidden { display: none; }
  .gift-box {
    width: 150px; height: 150px;
    margin: 50px auto;
    background: url('https://i.imgur.com/TqgqTLO.png') no-repeat center/cover;
    cursor: pointer;
    animation: bounce 1s infinite;
  }
  @keyframes bounce {
    0%,100% { transform: translateY(0);}
    50% { transform: translateY(-20px);}
  }
  .ring { font-size: 2em; color: gold; margin-top: 20px; }
  .heart, .rose {
    position: absolute;
    border-radius: 50%;
    cursor: pointer;
  }
  .heart {
    width: 50px; height: 50px;
    background: red;
    animation: float 3s ease-in-out infinite;
  }
  .rose {
    width: 40px; height: 40px;
    background: pink;
    animation: float 4s ease-in-out infinite;
  }
  @keyframes float {
    0% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-20px) rotate(10deg); }
    100% { transform: translateY(0) rotate(0deg); }
  }
</style>
</head>
<body>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For My Love Kausar 💖</title>
<style>
  body {
    font-family: 'Comic Sans MS', cursive, sans-serif;
    background: #ffe6f0;
    text-align: center;
    color: #ff3366;
    margin: 0;
    padding: 0;
  }
  h1 { font-size: 2em; margin-top: 20px; }
  .game-container { padding: 20px; }
  button {
    background-color: #ff6699;
    border: none;
    padding: 15px 30px;
    margin: 10px;
    font-size: 1em;
    color: white;
    border-radius: 10px;
    cursor: pointer;
  }
  button:hover { background-color: #ff3366; }
  .hidden { display: none; }
  .gift-box {
    width: 150px; height: 150px;
    margin: 50px auto;
    background: url('https://i.imgur.com/TqgqTLO.png') no-repeat center/cover;
    cursor: pointer;
    animation: bounce 1s infinite;
  }
  @keyframes bounce {
    0%,100% { transform: translateY(0);}
    50% { transform: translateY(-20px);}
  }
  .ring { font-size: 2em; color: gold; margin-top: 20px; }
</style>
</head>
<body>

<h1>💖 For My Love, Kausar 💖</h1>
<div class="game-container" id="game-container">

  <!-- Level 1: Funny Romantic Questions -->
  <div id="level1">
    <h2>Level 1: Fun & Romantic Questions</h2>
    <p id="question"></p>
    <button onclick="answer('yes')">Yes</button>
    <button onclick="answer('no')">No</button>
  </div>

  <!-- Level 2: Love Trap Game 1 -->
  <div id="level2" class="hidden">
    <h2>Level 2: Catch the Heart 💘</h2>
    <p>Click on the moving heart to catch it!</p>
    <div id="heart" style="width:50px;height:50px;background:red;border-radius:50%;position:absolute;top:100px;left:50px;cursor:pointer;"></div>
  </div>

  <!-- Level 3: Love Trap Game 2 -->
  <div id="level3" class="hidden">
    <h2>Level 3: Swipe the Roses 🌹</h2>
    <p>Swipe/click on all the roses to collect them!</p>
    <div id="roses"></div>
  </div>

  <!-- Level 4: Final Love Trap Game -->
  <div id="level4" class="hidden">
    <h2>Final Level: Open the Gift Box 🎁</h2>
    <p>Click the gift box to reveal your surprise!</p>
    <div class="gift-box" id="gift-box"></div>
    <div id="surprise" class="hidden">
      <p class="ring">💍</p>
      <p>My love, Kausar Qureshi 💖, I love you forever!</p>
    </div>
  </div>

</div>

<script>
  // Level 1: Questions
  const questions = [
    "Do you love me more than chocolate?",
    "Will you marry me someday? 😘",
    "Am I your favorite human?",
    "Do you want to go on endless adventures together?",
    "Should we have endless cuddles tonight?"
  ];
  let currentQuestion = 0;
  const questionEl = document.getElementById('question');

  function showQuestion() {
    questionEl.innerText = questions[currentQuestion];
  }
  function answer(ans) {
    currentQuestion++;
    if(currentQuestion < questions.length) {
      showQuestion();
    } else {
      // Move to Level 2
      document.getElementById('level1').classList.add('hidden');
      document.getElementById('level2').classList.remove('hidden');
      startHeartGame();
    }
  }
  showQuestion();

  // Level 2: Catch the Heart
  const heart = document.getElementById('heart');
  let heartCaught = false;

  function moveHeart() {
    const x = Math.random() * (window.innerWidth - 50);
    const y = Math.random() * (window.innerHeight - 150);
    heart.style.left = x + 'px';
    heart.style.top = y + 'px';
  }
  heart.addEventListener('click', () => {
    heartCaught = true;
    document.getElementById('level2').classList.add('hidden');
    document.getElementById('level3').classList.remove('hidden');
    startRoseGame();
  });

  function startHeartGame() {
    setInterval(moveHeart, 1000);
  }

  // Level 3: Swipe Roses
  const rosesContainer = document.getElementById('roses');
  let roseCount = 0;
  function startRoseGame() {
    for(let i=0;i<5;i++) {
      const rose = document.createElement('div');
      rose.style.width='40px';
      rose.style.height='40px';
      rose.style.background='pink';
      rose.style.borderRadius='50%';
      rose.style.position='absolute';
      rose.style.top=Math.random()*(window.innerHeight-150)+'px';
      rose.style.left=Math.random()*(window.innerWidth-50)+'px';
      rose.style.cursor='pointer';
      rose.addEventListener('click', () => {
        rose.remove();
        roseCount++;
        if(roseCount===5) {
          document.getElementById('level3').classList.add('hidden');
          document.getElementById('level4').classList.remove('hidden');
        }
      });
      rosesContainer.appendChild(rose);
    }
  }

  // Level 4: Gift Box
  const giftBox = document.getElementById('gift-box');
  const surprise = document.getElementById('surprise');
  giftBox.addEventListener('click', () => {
    giftBox.style.display='none';
    surprise.classList.remove('hidden');
  });

</script>
</body>
</html>

<h1>💖 For My Love, Kausar 💖</h1>
<div class="game-container" id="game-container">

  <!-- Level 1: Questions -->
  <div id="level1">
    <h2>Level 1: Fun & Romantic Questions</h2>
    <p id="question"></p>
    <button onclick="answer('yes')">Yes</button>
    <button onclick="answer('no')">No</button>
  </div>

  <!-- Level 2: Love Trap Game 1 -->
  <div id="level2" class="hidden">
    <h2>Level 2: Catch the Heart 💘</h2>
    <p>Tap on the moving heart to catch it!</p>
  </div>

  <!-- Level 3: Love Trap Game 2 -->
  <div id="level3" class="hidden">
    <h2>Level 3: Swipe the Roses 🌹</h2>
    <p>Tap or swipe all the roses to collect them!</p>
  </div>

  <!-- Level 4: Final Love Trap Game -->
  <div id="level4" class="hidden">
    <h2>Final Level: Open the Gift Box 🎁</h2>
    <p>Tap the gift box to reveal your surprise!</p>
    <div class="gift-box" id="gift-box"></div>
    <div id="surprise" class="hidden">
      <p class="ring">💍</p>
      <p>My love, Kausar Qureshi 💖, I love you forever!</p>
    </div>
  </div>

</div>

<script>
  // Level 1: Questions
  const questions = [
    "Do you love me more than chocolate?",
    "Will you marry me someday? 😘",
    "Am I your favorite human?",
    "Do you want to go on endless adventures together?",
    "Should we have endless cuddles tonight?"
  ];
  let currentQuestion = 0;
  const questionEl = document.getElementById('question');

  function showQuestion() {
    questionEl.innerText = questions[currentQuestion];
  }
  function answer(ans) {
    currentQuestion++;
    if(currentQuestion < questions.length) {
      showQuestion();
    } else {
      // Move to Level 2
      document.getElementById('level1').classList.add('hidden');
      document.getElementById('level2').classList.remove('hidden');
      startHeartGame();
    }
  }
  showQuestion();

  // Level 2: Animated Heart
  const gameContainer = document.getElementById('game-container');
  let heartCaught = false;
  let heartEl;

  function startHeartGame() {
    heartEl = document.createElement('div');
    heartEl.classList.add('heart');
    setHeartPosition();
    gameContainer.appendChild(heartEl);

    heartEl.addEventListener('click', () => {
      heartCaught = true;
      heartEl.remove();
      document.getElementById('level2').classList.add('hidden');
      document.getElementById('level3').classList.remove('hidden');
      startRoseGame();
    });

    setInterval(() => {
      if(!heartCaught) setHeartPosition();
    }, 1200);
  }

  function setHeartPosition() {
    const x = Math.random() * (window.innerWidth - 50);
    const y = Math.random() * (window.innerHeight - 200);
    heartEl.style.left = x + 'px';
    heartEl.style.top = y + 'px';
  }

  // Level 3: Animated Roses with Tap/Swipe
  let roseCount = 0;
  const roseTotal = 5;
  const roses = [];

  function startRoseGame() {
    for(let i=0; i<roseTotal; i++){
      const rose = document.createElement('div');
      rose.classList.add('rose');
      rose.style.top = Math.random()*(window.innerHeight-150)+'px';
      rose.style.left = Math.random()*(window.innerWidth-50)+'px';
      gameContainer.appendChild(rose);
      roses.push(rose);

      // Tap / click
      rose.addEventListener('click', () => collectRose(rose));
      
      // Swipe gesture for mobile
      let touchStartX, touchStartY;
      rose.addEventListener('touchstart', (e) => {
        touchStartX = e.touches[0].clientX;
        touchStartY = e.touches[0].clientY;
      });
      rose.addEventListener('touchend', (e) => {
        const dx = e.changedTouches[0].clientX - touchStartX;
        const dy = e.changedTouches[0].clientY - touchStartY;
        if(Math.abs(dx) > 10 || Math.abs(dy) > 10){
          collectRose(rose);
        }
      });
    }
  }

  function collectRose(rose) {
    rose.remove();
    roseCount++;
    if(roseCount === roseTotal){
      document.getElementById('level3').classList.add('hidden');
      document.getElementById('level4').classList.remove('hidden');
    }
  }

  // Level 4: Gift Box
  const giftBox = document.getElementById('gift-box');
  const surprise = document.getElementById('surprise');
  giftBox.addEventListener('click', () => {
    giftBox.style.display='none';
    surprise.classList.remove('hidden');
  });
</script>
</body>
</html>
