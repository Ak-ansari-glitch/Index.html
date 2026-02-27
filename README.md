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
  h1 { font-size: 2em; margin-top: 15px; }
  h2 { font-size: 1.5em; margin: 10px 0; }
  .game-container { padding: 10px; }
  button {
    background-color: #ff6699;
    border: none;
    padding: 12px 25px;
    margin: 5px;
    font-size: 1em;
    color: white;
    border-radius: 10px;
    cursor: pointer;
  }
  button:hover { background-color: #ff3366; }
  .hidden { display: none; }
  .gift-box {
    width: 120px; height: 120px;
    margin: 30px auto;
    background: url('https://i.imgur.com/TqgqTLO.png') no-repeat center/cover;
    cursor: pointer;
    animation: bounce 1s infinite;
  }
  @keyframes bounce {
    0%,100% { transform: translateY(0);}
    50% { transform: translateY(-15px);}
  }
  .ring { font-size: 2em; color: gold; margin-top: 10px; }
  .puzzle-letter {
    display: inline-block;
    padding: 10px;
    margin: 3px;
    background: #ff99cc;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1.2em;
    color: white;
  }
  .memory-card {
    width: 60px; height: 60px;
    display: inline-block;
    margin: 5px;
    background: pink;
    border-radius: 8px;
    cursor: pointer;
    vertical-align: top;
    font-size: 1.5em;
    line-height: 60px;
    color: white;
  }
  #heart { width:40px; height:40px; border-radius:50%; position:absolute; background:red; cursor:pointer; }
  #roses div { width:35px; height:35px; border-radius:50%; position:absolute; background:pink; cursor:pointer; }
</style>
</head>
<body>

<h1>💖 For My Love, Kausar 💖</h1>
<div class="game-container" id="game-container">

  <!-- Level 1 -->
  <div id="level1">
    <h2>Level 1: Fun & Romantic Questions</h2>
    <p id="question"></p>
    <button onclick="answer('yes')">Yes</button>
    <button onclick="answer('no')">No</button>
  </div>

  <!-- Level 2 -->
  <div id="level2" class="hidden">
    <h2>Level 2: Catch the Heart 💘</h2>
    <p>Tap the moving heart!</p>
    <div id="heart"></div>
  </div>

  <!-- Level 3 -->
  <div id="level3" class="hidden">
    <h2>Level 3: Swipe the Roses 🌹</h2>
    <p>Tap all roses!</p>
    <div id="roses"></div>
  </div>

  <!-- Level 4 -->
  <div id="level4" class="hidden">
    <h2>Level 4: Puzzle of Love 💌</h2>
    <p>Rearrange the letters to form "LOVE"</p>
    <div id="puzzle"></div>
  </div>

  <!-- Level 5 -->
  <div id="level5" class="hidden">
    <h2>Level 5: Memory Match 💖</h2>
    <p>Find all matching hearts!</p>
    <div id="memory"></div>
  </div>

  <!-- Level 6 -->
  <div id="level6" class="hidden">
    <h2>Final Level: Open the Gift Box 🎁</h2>
    <p>Tap the gift box to reveal your surprise!</p>
    <div class="gift-box" id="gift-box"></div>
    <div id="surprise" class="hidden">
      <p class="ring">💍</p>
      <p>My love, Kausar Qureshi 💖, I love you forever!</p>
      <p id="love-letter">
        Dear Kausar,<br>
        Every moment with you is a treasure. Thank you for being my sunshine and my heart.<br>
        I promise to make you smile every day, forever and always.<br>
        Yours truly, 💕
      </p>
    </div>
  </div>

</div>

<script>
  // Level 1
  const questions = [
    "Do you love me more than chocolate?",
    "Will you marry me someday? 😘",
    "Am I your favorite human?",
    "Do you want to go on endless adventures together?",
    "Should we have endless cuddles tonight?"
  ];
  let currentQuestion=0;
  const questionEl=document.getElementById('question');
  function showQuestion(){ questionEl.innerText=questions[currentQuestion]; }
  function answer(ans){
    currentQuestion++;
    if(currentQuestion<questions.length) showQuestion();
    else { document.getElementById('level1').classList.add('hidden'); document.getElementById('level2').classList.remove('hidden'); startHeartGame(); }
  }
  showQuestion();

  // Level 2
  const heart=document.getElementById('heart');
  function moveHeart(){
    heart.style.left = Math.random()*(window.innerWidth-40)+'px';
    heart.style.top = Math.random()*(window.innerHeight-150)+'px';
  }
  heart.addEventListener('click', ()=>{
    document.getElementById('level2').classList.add('hidden');
    document.getElementById('level3').classList.remove('hidden');
    startRoseGame();
  });
  setInterval(moveHeart,800);

  // Level 3
  const rosesContainer=document.getElementById('roses');
  let roseCount=0;
  function startRoseGame(){
    for(let i=0;i<5;i++){
      const rose=document.createElement('div');
      rose.style.top=Math.random()*(window.innerHeight-150)+'px';
      rose.style.left=Math.random()*(window.innerWidth-50)+'px';
      rose.addEventListener('click',()=>{
        rose.remove(); roseCount++;
        if(roseCount===5){
          document.getElementById('level3').classList.add('hidden');
          document.getElementById('level4').classList.remove('hidden');
          startPuzzleGame();
        }
      });
      rosesContainer.appendChild(rose);
    }
  }

  // Level 4
  const puzzleContainer=document.getElementById('puzzle');
  const puzzleWord="LOVE".split('');
  let selectedLetters=[];
  function startPuzzleGame(){
    const shuffled=puzzleWord.sort(()=>Math.random()-0.5);
    shuffled.forEach(letter=>{
      const span=document.createElement('span');
      span.className='puzzle-letter';
      span.innerText=letter;
      span.addEventListener('click',()=>{
        selectedLetters.push(letter);
        span.style.visibility='hidden';
        if(selectedLetters.join('')===puzzleWord.join('')){
          document.getElementById('level4').classList.add('hidden');
          document.getElementById('level5').classList.remove('hidden');
          startMemoryGame();
        }
      });
      puzzleContainer.appendChild(span);
    });
  }

  // Level 5
  const memoryContainer=document.getElementById('memory');
  let memoryCards=['💖','💖','🌹','🌹','💌','💌'];
  let firstCard=null, secondCard=null;
  function startMemoryGame(){
    memoryCards.sort(()=>Math.random()-0.5).forEach(symbol=>{
      const card=document.createElement('div');
      card.className='memory-card';
      card.dataset.symbol=symbol;
      card.innerText='';
      card.addEventListener('click',()=>{
        if(card.innerText==='' && !secondCard){
          card.innerText=symbol;
          if(!firstCard) firstCard=card;
          else secondCard=card;
          if(firstCard && secondCard){
            if(firstCard.dataset.symbol===secondCard.dataset.symbol){ firstCard=null; secondCard=null; }
            else { setTimeout(()=>{ firstCard.innerText=''; secondCard.innerText=''; firstCard=null; secondCard=null; },500); }
          }
        }
        if(document.querySelectorAll('.memory-card:empty').length===0){
          document.getElementById('level5').classList.add('hidden');
          document.getElementById('level6').classList.remove('hidden');
        }
      });
      memoryContainer.appendChild(card);
    });
  }

  // Level 6
  const giftBox=document.getElementById('gift-box');
  const surprise=document.getElementById('surprise');
  giftBox.addEventListener('click',()=>{ giftBox.style.display='none'; surprise.classList.remove('hidden'); });
</script>

</body>
</html>
