<!DOCTYPE html>
<html>
<head>
<title>Jithu Adventure Quest 🌍</title>

<style>
body{
margin:0;
background:#000;
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
margin:8px;
padding:12px 18px;
border:1px solid white;
background:transparent;
color:white;
cursor:pointer;
transition:0.3s;
}

button:hover{
background:white;
color:black;
}

.box{
max-width:650px;
padding:20px;
}

.stat{
position:fixed;
top:10px;
left:10px;
font-size:14px;
color:#aaa;
}
</style>
</head>

<body>

<div class="stat" id="stats">❤️ HP: 100 | 💰 Coins: 0 | ⚔️ Level: 1</div>

<!-- 🌍 START -->
<div id="start" class="screen active">
  <div class="box">
    <h1>🌍 Jithu Adventure Quest</h1>
    <p>A dangerous journey begins...</p>
    <button onclick="start()">START</button>
  </div>
</div>

<!-- 🗺️ MAP -->
<div id="map" class="screen">
  <div class="box">
    <h2>🗺️ Choose Your Path</h2>

    <button onclick="forest()">🌲 Forest</button>
    <button onclick="cave()">🕳️ Cave</button>
    <button onclick="lake()">🌊 Lake</button>
    <button onclick="boss()">👹 Final Boss</button>
  </div>
</div>

<!-- 🎮 GAME -->
<div id="game" class="screen">
  <div class="box">
    <h2 id="title">Area</h2>
    <p id="story">Story</p>

    <button onclick="fight()">⚔️ Fight</button>
    <button onclick="run()">🏃 Run</button>

    <p id="result"></p>

    <button onclick="goMap()">⬅ Back to Map</button>
  </div>
</div>

<!-- 🏆 END -->
<div id="end" class="screen">
  <div class="box">
    <h1>🏆 ADVENTURE COMPLETE</h1>
    <p id="final"></p>
    <button onclick="restart()">Play Again</button>
  </div>
</div>

<script>

let hp = 100;
let coins = 0;
let level = 1;
let currentArea = "";

/* SCREEN CONTROL */
function show(id){
document.querySelectorAll(".screen").forEach(s=>{
s.classList.remove("active");
});
document.getElementById(id).classList.add("active");
}

/* START */
function start(){
show("map");
}

/* AREAS */
function forest(){
currentArea="Forest";
startArea("🌲 A wild wolf appears in the forest!");
}

function cave(){
currentArea="Cave";
startArea("🕳️ A dark monster is hiding in the cave!");
}

function lake(){
currentArea="Lake";
startArea("🌊 A water beast rises from the lake!");
}

function boss(){
currentArea="Boss";
startArea("👹 FINAL BOSS: Shadow King appears!");
}

/* START AREA */
function startArea(text){
show("game");
document.getElementById("title").innerText = currentArea;
document.getElementById("story").innerText = text;
document.getElementById("result").innerText = "";
}

/* FIGHT */
function fight(){

if(currentArea==="Boss"){
hp -= 40;
coins += 50;
level += 2;
endGame();
return;
}

hp -= 20;
coins += 10;
level++;

document.getElementById("result").innerText =
"⚔️ You fought bravely! +coins earned";
updateStats();
}

/* RUN */
function run(){
hp -= 5;
document.getElementById("result").innerText =
"🏃 You escaped safely!";
updateStats();
}

/* MAP */
function goMap(){
show("map");
}

/* UPDATE */
function updateStats(){
document.getElementById("stats").innerText =
`❤️ HP: ${hp} | 💰 Coins: ${coins} | ⚔️ Level: ${level}`;
}

/* END */
function endGame(){
show("end");
document.getElementById("final").innerHTML =
`Coins: ${coins}<br>Level: ${level}<br>HP: ${hp}`;
}

/* RESTART */
function restart(){
hp=100;
coins=0;
level=1;
show("map");
updateStats();
}

</script>

</body>
</html>
