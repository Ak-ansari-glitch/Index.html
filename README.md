<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Don't Click The Husband 😎</title>

<style>
body {
  margin: 0;
  overflow: hidden;
  font-family: 'Comic Sans MS', cursive;
  background: linear-gradient(to bottom right, #ffd6e8, #ffeef5);
  text-align: center;
}

h1 {
  margin-top: 15px;
  color: #ff4081;
  font-size: 24px;
}

#score {
  font-size: 18px;
  margin: 10px;
}

.item {
  position: absolute;
  font-size: 40px;
  cursor: pointer;
  user-select: none;
  animation: floatDown linear forwards;
}

@keyframes floatDown {
  from { transform: translateY(-60px); }
  to { transform: translateY(110vh); }
}

#message {
  position: fixed;
  bottom: 15px;
  width: 100%;
  font-weight: bold;
  color: #d81b60;
}

#proposalScreen {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 192, 203, 0.97);
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 20px;
  text-align: center;
}

#proposalScreen h2 {
  font-size: 26px;
  color: #880e4f;
}

button {
  padding: 12px 25px;
  font-size: 18px;
  border: none;
  border-radius: 25px;
  background: #ff4081;
  color: white;
  margin-top: 20px;
  cursor: pointer;
}

button:hover {
  background: #e91e63;
}
</style>
</head>

<body>

<h1>🚨 Don't Click The Husband 😎</h1>
<div id="score">Score: 0</div>
<div id="message">Only click the ❤️ hearts... NOT your husband 😜</div>

<div id="proposalScreen">
  <h2>💍 SECRET LEVEL UNLOCKED 💍</h2>
  <p>You survived the husband trap 😂</p>
  <p>But now I have a serious question...</p>
  <h2>Will you continue being my wife forever? ❤️</h2>
  <p>(No clicking husband allowed in real life either 😎)</p>
  <button onclick="restartGame()">Say Yes Again 😘</button>
</div>

<script>
let score = 0;
let gameActive = true;
const scoreDisplay = document.getElementById("score");
const message = document.getElementById("message");
const proposalScreen = document.getElementById("proposalScreen");

function createItem() {
  if (!gameActive) return;

  const item = document.createElement("div");
  item.classList.add("item");

  // Random chance: mostly hearts, sometimes husband
  const isHusband = Math.random() < 0.25;

  if (isHusband) {
    item.innerHTML = "😎";
  } else {
    item.innerHTML = "❤️";
  }

  item.style.left = Math.random() * 85 + "vw";
  item.style.animationDuration = (3 + Math.random() * 2) + "s";

  item.onclick = function() {
    if (!gameActive) return;

    if (isHusband) {
      score -= 2;
      message.innerHTML = "WHY WOULD YOU CLICK YOUR HUSBAND?! 😂";
    } else {
      score += 1;
      message.innerHTML = "Good girl 😘 Keep collecting my love!";
    }

    scoreDisplay.innerHTML = "Score: " + score;
    item.remove();

    if (score >= 20) {
      unlockProposal();
    }
  };

  item.addEventListener("animationend", function() {
    if (item.parentNode) {
      item.remove();
    }
  });

  document.body.appendChild(item);
}

function unlockProposal() {
  gameActive = false;
  proposalScreen.style.display = "flex";
}

function restartGame() {
  score = 0;
  scoreDisplay.innerHTML = "Score: 0";
  message.innerHTML = "Only click the ❤️ hearts... NOT your husband 😜";
  proposalScreen.style.display = "none";
  gameActive = true;
}

setInterval(createItem, 700);
</script>

</body>
</html>
