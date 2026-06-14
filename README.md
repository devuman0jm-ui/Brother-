<!DOCTYPE html>
<html>
<head>
<title>Jithu Hero Quest 💙</title>

<style>
body{
margin:0;
background:black;
color:white;
font-family:Arial;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
text-align:center;
}

.screen{ display:none; }
.active{ display:block; }

button{
margin:10px;
padding:12px 20px;
border:1px solid white;
background:transparent;
color:white;
cursor:pointer;
}

button:hover{
background:white;
color:black;
}

.box{
max-width:600px;
padding:20px;
}

.badge{
color:gold;
font-weight:bold;
}
</style>
</head>

<body>

<!-- 🎬 START -->
<div id="start" class="screen active">
  <div class="box">
    <h1>💙 Jithu Hero Quest</h1>
    <p>A legendary journey for a small hero</p>
    <button onclick="goHub()">START</button>
  </div>
</div>

<!-- 🌍 HUB -->
<div id="hub" class="screen">
  <div class="box">
    <h1>🌍 Hero Base</h1>
    <p id="stats">Coins: 0 | Badge: None</p>

    <button onclick="level1()">🎮 Level 1</button>
    <button onclick="showMessage()">💌 Message</button>
  </div>
</div>

<!-- 🎮 GAME -->
<div id="game" class="screen">
  <div class="box">
    <h2 id="title">Level 1</h2>
    <p id="story">A wild monster appears in the forest!</p>

    <button onclick="choice(1)">⚔️ Fight</button>
    <button onclick="choice(2)">🏃 Run</button>

    <p id="result"></p>

    <button onclick="goHub()">Back</button>
  </div>
</div>

<!-- 💌 MESSAGE -->
<div id="message" class="screen">
  <div class="box">
    <h2>💙 Message for Jithu</h2>
    <p>
      Jithu,<br><br>
      You are a HERO in your own story 💙<br>
      Every level you pass makes you stronger.<br><br>
      Never stop being brave 😊
    </p>

    <button onclick="goHub()">Back</button>
  </div>
</div>

<script>

let coins = 0;
let badge = "None";

/* SCREEN SWITCH */
function show(id){
document.querySelectorAll(".screen").forEach(s=>{
s.classList.remove("active");
});
document.getElementById(id).classList.add("active");
}

function goHub(){
show("hub");
updateStats();
}

function showMessage(){
show("message");
}

function level1(){
show("game");
document.getElementById("title").innerText = "Level 1";
document.getElementById("story").innerText =
"A wild monster appears in the forest!";
}

/* GAME CHOICES */
function choice(n){

if(n===1){
coins += 10;
badge = "Brave Fighter 🛡️";

document.getElementById("result").innerHTML =
"🔥 You defeated the monster! +10 coins";
}

else{
coins += 5;
badge = "Smart Runner 🏃";

document.getElementById("result").innerHTML =
"🏃 You escaped safely! +5 coins";
}

updateStats();

}

/* STATS */
function updateStats(){
document.getElementById("stats").innerHTML =
"Coins: " + coins + " | Badge: " + badge;
}

</script>

</body>
</html>
