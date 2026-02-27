<!DOCTYPE html>
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ultimate Wife Challenge 💖</title>
<style>
/* Basic styling */
body {
  margin: 0;
  overflow: hidden;
  font-family: Arial, sans-serif;
  background: linear-gradient(to bottom right, #ffd6e8, #ffeef5);
  text-align: center;
  touch-action: manipulation;
}
h1 { margin-top: 10px; color: #ff4081; font-size: 22px; }
#topBar { display: flex; justify-content: space-around; font-weight: bold; margin: 5px; }
.item { position: absolute; font-size: 40px; cursor: pointer; user-select:none; animation: floatDown linear forwards; }

/* Falling animation */
@keyframes floatDown { from { transform: translateY(-60px); } to { transform: translateY(110vh); } }

/* Proposal & Love Letter Screens */
#proposalScreen, #loveLetter {
  display: none;
  position: fixed;
  inset: 0;
  background: radial-gradient(circle, #ffb6c1, #ff69b4);
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: white;
  text-align: center;
  overflow: auto;
  padding: 20px;
}

/* Ring Box */
.ring-box {
  position: relative;
  width: 120px;
  height: 100px;
  margin: 20px auto;
  cursor: pointer;
  perspective: 1000px;
}
.lid { width: 120px; height: 50px; background: #e91e63; border-radius: 10px 10px 0 0; position: absolute; top:0; transform-origin: bottom; transition: transform 1s ease; }
.base { width: 120px; height: 50px; background: #ad1457; border-radius: 0 0 10px 10px; position: absolute; bottom:0; }
.ring {
  position: absolute;
  font-size: 40px;
  top: -20px;
  left: 50%;
  transform: translateX(-50%) scale(0);
  transition: transform 1s ease 0.5s;
  animation: sparkle 1.5s infinite alternate;
}
@keyframes sparkle { from { text-shadow: 0 0 5px white, 0 0 10px white; } to { text-shadow: 0 0 20px yellow, 0 0 30px white; } }
.ring-box.open .lid { transform: rotateX(-120deg); }
.ring-box.open .ring { transform: translateX(-50%) scale(1.3); }

/* Fireworks */
.firework { position:absolute; font-size:25px; animation: explode 1s ease-out forwards; }
@keyframes explode { from { transform: scale(0); opacity:1;} to { transform: scale(3); opacity:0;} }

/* Falling roses */
.rose { position:absolute; font-size:24px; pointer-events:none; animation: fall 5s linear forwards; }
@keyframes fall { from { transform: translateY(-50px) rotate(0deg);} to { transform: translateY(110vh) rotate(360deg);} }

/* Glowing I Love You */
#loveLetter h1 { font-size:32px; font-weight:bold; text-shadow: 0 0 10px red,0 0 20px yellow; animation: glow 1.5s ease-in-out infinite alternate; }
@keyframes glow { 0% { text-shadow:0 0 5px #fff,0 0 10px #ff0;} 100% { text-shadow:0 0 20px #ff69b4,0 0 40px #fff;} }

/* Love Letter Text */
#loveLetter p { max-width: 90%; margin: 15px auto; font-size:18px; line-height:1.6; }

/* Buttons */
button { padding:12px 25px; font-size:18px; border:none; border-radius:25px; background:white; color:#e91e63; margin:10px; cursor:pointer; position: relative; touch-action: manipulation; }
</style>
</head>

<body>
<h1>💖 Ultimate Wife Challenge 💖</h1>
<div id="topBar">
  <div id="score">Score: 0</div>
  <div id="lives">Lives: ❤️❤️❤️</div>
  <div id="level">Level: 1</div>
</div>

<!-- Proposal Screen -->
<div id="proposalScreen">
  <h2>🎉 YOU WON MY HEART 🎉</h2>
  <h2>My Love Kausar Qureshi 💖</h2>

  <div class="ring-box" onclick="openRingBox()">
    <div class="lid"></div>
    <div class="base"><div class="ring">💍</div></div>
  </div>

  <h2 id="finalText" style="display:none;">Will you stay mine forever? ❤️</h2>
  <div id="buttons" style="display:none;">
    <button onclick="showLoveLetter()">YES 😘</button>
    <button id="noBtn">NO 😜</button>
  </div>
</div>

<!-- Love Letter Screen -->
<div id="loveLetter">
  <h1>I Love You ❤️</h1>
  <h2>To My Love Kausar Qureshi 💌</h2>
  <p>
  From the moment we met, you changed my world forever.<br>
  Every smile of yours is my happiness.<br>
  Every moment with you is my treasure.<br>
  Through good memories and bad memories,<br>
  I choose you again and again.<br>
  Not just today. Not just tomorrow. But forever.<br>
  You are my heart, my peace, my home.<br>
  I promise to stand with you, laugh with you, and grow old with you.<br>
  I love you endlessly. ❤️
  </p>
  <button onclick="location.reload()">Play Again 😘</button>
</div>

<script>
// Game Variables
let score = 0, lives = 3, level = 1, levelThreshold = 15, gameActive = true, spawnInterval;
const scoreDisplay = document.getElementById("score");
const livesDisplay = document.getElementById("lives");
const levelDisplay = document.getElementById("level");
const proposalScreen = document.getElementById("proposalScreen");
const loveLetter = document.getElementById("loveLetter");
const noBtn = document.getElementById("noBtn");

// Update UI
function updateUI() {
  if(score<0) score=0;
  scoreDisplay.textContent="Score: "+score;
  livesDisplay.textContent="Lives: "+ "❤️".repeat(lives);
  levelDisplay.textContent="Level: "+level;
}

// Create Floating Items
function createItem(){
  if(!gameActive) return;
  const item=document.createElement("div"); item.className="item";
  const r=Math.random(); let type;
  if(r<0.4){ type="heart"; item.textContent="❤️"; }
  else if(r<0.6){ type="bad"; item.textContent="😎"; }
  else if(r<0.75){ type="sleep"; item.textContent="😴"; }
  else if(r<0.9){ type="shop"; item.textContent="🛍️"; }
  else{ type="bomb"; item.textContent="💣"; }

  item.style.left=Math.random()*85+"vw"; 
  item.style.animationDuration=Math.max(1.5,3-level*0.4)+"s";

  item.addEventListener("pointerdown",function(e){
    e.preventDefault(); if(!gameActive) return;
    if(type==="heart") score++;
    else if(type==="shop") score-=3;
    else lives--;
    updateUI(); item.remove();
    if(lives<=0){ alert("😂 Husband Wins!"); location.reload();}
    if(score>=levelThreshold){ level++; levelThreshold+=15; clearInterval(spawnInterval); spawnInterval=setInterval(createItem, Math.max(300,800-level*100)); updateUI();}
    if(level===4) winGame();
  });
  item.addEventListener("animationend",()=>item.remove());
  document.body.appendChild(item);
}

// Win Game
function winGame(){
  gameActive=false;
  clearInterval(spawnInterval);
  proposalScreen.style.display="flex";
  startFireworks();
}

// Fireworks
function startFireworks(){
  setInterval(()=>{
    const f=document.createElement("div"); f.className="firework"; f.textContent="✨";
    f.style.left=Math.random()*100+"vw"; f.style.top=Math.random()*100+"vh";
    proposalScreen.appendChild(f); setTimeout(()=>f.remove(),1000);
  },300);
}

// Ring Box
function openRingBox(){
  document.querySelector(".ring-box").classList.add("open");
  setTimeout(()=>{
    document.getElementById("finalText").style.display="block";
    document.getElementById("buttons").style.display="block";
  },1200);
}
  
// Show Love Letter & Start Rose Petals
function showLoveLetter(){
  proposalScreen.style.display="none";
  loveLetter.style.display="flex";
  startPetals();
}

// Funny NO Button
noBtn.addEventListener("mouseover", moveNoButton);
noBtn.addEventListener("touchstart", moveNoButton);
function moveNoButton(){
  noBtn.style.position="absolute";
  noBtn.style.left=Math.random()*80+"%";
  noBtn.style.top=Math.random()*80+"%";
}

// Falling rose petals
function startPetals(){
  setInterval(()=>{
    const rose=document.createElement("div"); rose.className="rose"; rose.textContent="🌹";
    rose.style.left=Math.random()*100+"vw"; rose.style.fontSize=(15+Math.random()*20)+"px";
    loveLetter.appendChild(rose);
    setTimeout(()=>rose.remove(),5000);
  },300);
}

// Start game
updateUI(); spawnInterval=setInterval(createItem,800);
</script>
</body>
</html>
