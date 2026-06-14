<!DOCTYPE html>
<html>
<head>
<title>Jithu RPG</title>

<style>
body{
margin:0;
background:#0b0b0f;
font-family:Arial;
color:white;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

/* MOBILE SCREEN */
.phone{
width:360px;
height:640px;
background:#111;
border-radius:25px;
box-shadow:0 0 30px rgba(0,0,0,0.8);
overflow:hidden;
position:relative;
}

/* TOP BAR */
.top{
background:#1c1c2a;
padding:10px;
display:flex;
justify-content:space-between;
font-size:14px;
}

/* CONTENT */
.screen{
display:none;
padding:15px;
}

.active{
display:block;
}

/* CARDS */
.card{
background:#222;
padding:15px;
border-radius:12px;
margin:10px 0;
cursor:pointer;
transition:0.3s;
}

.card:hover{
background:#333;
transform:scale(1.02);
}

/* BUTTON */
button{
margin-top:10px;
padding:10px;
width:100%;
border:none;
border-radius:10px;
background:#ffcc00;
color:black;
font-weight:bold;
cursor:pointer;
}

/* BOTTOM NAV */
.nav{
position:absolute;
bottom:0;
width:100%;
display:flex;
background:#1c1c2a;
}

.nav button{
flex:1;
border:none;
padding:10px;
background:transparent;
color:white;
font-size:12px;
}

.nav button:hover{
background:#333;
}
</style>
</head>

<body>

<div class="phone">

<!-- TOP -->
<div class="top">
<div>💙 JITHU RPG</div>
<div id="stats">❤️100 💰0 ⚔️1</div>
</div>

<!-- HOME -->
<div id="home" class="screen active">
  <h3>🌍 Mission Hub</h3>

  <div class="card" onclick="startMission('Forest','🐺 Wolf appears in forest!')">
    🌲 Forest
  </div>

  <div class="card" onclick="startMission('Cave','🕳️ Dark monster inside cave!')">
    🕳️ Cave
  </div>

  <div class="card" onclick="startMission('Lake','🌊 Water beast rises!')">
    🌊 Lake
  </div>

  <div class="card" onclick="boss()">
    👹 Boss Fight
  </div>
</div>

<!-- BATTLE -->
<div id="battle" class="screen">
  <h3 id="title">Battle</h3>
  <p id="story">Enemy appears</p>

  <button onclick="attack()">⚔️ ATTACK</button>
  <button onclick="run()">🏃 RUN</button>

  <p id="result"></p>
</div>

<!-- END -->
<div id="end" class="screen">
  <h3>🏆 Mission Complete</h3>
  <p id="final"></p>
  <button onclick="restart()">Play Again</button>
</div>

<!-- NAV -->
<div class="nav">
  <button onclick="go('home')">🏠 Home</button>
  <button onclick="go('battle')">⚔️ Battle</button>
</div>

</div>

<script>

let hp = 100;
let coins = 0;
let lvl = 1;
let enemy = "";

/* SCREEN SWITCH */
function go(id){
document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
document.getElementById(id).classList.add('active');
update();
}

/* START MISSION */
function startMission(name,text){
enemy=name;
go('battle');
document.getElementById("title").innerText=name;
document.getElementById("story").innerText=text;
document.getElementById("result").innerText="";
}

/* BOSS */
function boss(){
enemy="Boss";
go('battle');
document.getElementById("title").innerText="👹 Shadow King";
document.getElementById("story").innerText="Final Boss appears!";
}

/* ATTACK */
function attack(){

if(enemy==="Boss"){
hp -= 30;
coins += 50;
lvl += 2;
endGame();
return;
}

hp -= 15;
coins += 10;
lvl++;

document.getElementById("result").innerText="⚔️ Hit enemy!";
update();
}

/* RUN */
function run(){
hp -= 5;
document.getElementById("result").innerText="🏃 Escaped!";
update();
}

/* END */
function endGame(){
go('end');
document.getElementById("final").innerHTML =
`Coins: ${coins}<br>Level: ${lvl}<br>HP: ${hp}`;
}

/* RESTART */
function restart(){
hp=100; coins=0; lvl=1;
go('home');
}

/* UPDATE STATS */
function update(){
document.getElementById("stats").innerText =
`❤️${hp} 💰${coins} ⚔️${lvl}`;
}

</script>

</body>
</html>
