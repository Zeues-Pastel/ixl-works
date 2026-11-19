# ixl-works
gaming unblocked school website

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>IXL-WORKS | Gaming Universe</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
  background:#050510;
  color:white;
  font-family:Arial,sans-serif;
  min-height:100vh;
  background-image:
    radial-gradient(ellipse at 20% 10%,#29104c 0%,transparent 40%),
    radial-gradient(ellipse at 85% 75%,#111c48 0%,transparent 40%);
}

header{
  padding:20px 6%;
  background:#080812ee;
  border-bottom:1px solid #59358b;
  display:flex;
  justify-content:space-between;
  align-items:center;
  position:sticky;
  top:0;
  z-index:5;
}

.logo{
  font-size:27px;
  font-weight:bold;
  color:#c49aff;
  letter-spacing:2px;
}

header a{
  color:white;
  text-decoration:none;
  margin-left:18px;
}

.hero{text-align:center;padding:65px 15px 35px}

.hero h1{
  font-size:clamp(42px,8vw,75px);
  color:#c49aff;
  text-shadow:0 0 25px #974cff;
}

.hero p{color:#c1b3d5;margin:15px}

.search{
  margin-top:15px;
  width:min(450px,90%);
  padding:14px;
  border-radius:30px;
  border:1px solid #9a62db;
  background:#121020;
  color:white;
  font-size:16px;
  outline:none;
}

.container{padding:20px 6% 60px}

h2{color:#c49aff;margin:25px 0 20px}

.categories{
  display:flex;
  flex-wrap:wrap;
  gap:10px;
  margin-bottom:25px;
}

button{
  cursor:pointer;
  border:1px solid #7547a9;
  background:#19132c;
  color:white;
  border-radius:12px;
  padding:12px 17px;
}

button:hover,.active{
  background:#743ac0;
  box-shadow:0 0 12px #7137b0;
}

.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(190px,1fr));
  gap:17px;
}

.card{
  background:linear-gradient(145deg,#19132c,#0d0c19);
  border:1px solid #382553;
  padding:23px;
  border-radius:17px;
  transition:.2s;
}

.card:hover{
  transform:translateY(-5px);
  border-color:#bd8aff;
  box-shadow:0 0 20px #6734a5;
}

.card .emoji{font-size:43px}
.card h3{margin:12px 0;color:#d5b9ff}
.card p{color:#aaa0ba;font-size:14px;min-height:36px}
.card button{width:100%;margin-top:16px}

#gameScreen{
  display:none;
  background:#100e20;
  border:1px solid #7042a6;
  border-radius:18px;
  padding:25px;
  margin-top:30px;
  text-align:center;
}

#gameScreen h2{margin:5px 0 20px}

#gameArea{
  margin:20px auto;
  max-width:500px;
}

.game-button{
  background:#7541b8;
  margin:5px;
}

.cells{
  display:grid;
  grid-template-columns:repeat(3,90px);
  justify-content:center;
  gap:7px;
}

.cell{
  height:90px;
  font-size:35px;
  background:#211638;
}

.memory-grid{
  display:grid;
  grid-template-columns:repeat(4,65px);
  justify-content:center;
  gap:8px;
}

.memory-card{
  height:65px;
  font-size:25px;
  padding:5px;
}

#snakeCanvas{
  background:#090e19;
  border:2px solid #8b55c9;
  max-width:100%;
}

.target{
  position:absolute;
  width:48px;
  height:48px;
  border-radius:50%;
  background:#ff4b90;
  padding:0;
}

#targetArea{
  height:260px;
  background:#080817;
  border:1px solid #503276;
  position:relative;
  overflow:hidden;
  margin:15px auto;
  max-width:450px;
  border-radius:12px;
}

.hidden{display:none!important}

footer{
  text-align:center;
  border-top:1px solid #382553;
  padding:30px;
  color:#9988b2;
}

@media(max-width:550px){
  header{flex-direction:column;gap:15px}
  .cells{grid-template-columns:repeat(3,75px)}
  .cell{height:75px}
}
</style>
</head>

<body>

<header>
  <div class="logo">✦ IXL-WORKS</div>
  <nav>
    <a href="#home">Home</a>
    <a href="#games">Games</a>
  </nav>
</header>

<section class="hero" id="home">
  <h1>IXL-WORKS</h1>
  <p>🌌 Welcome to your gaming universe.</p>
  <p>Choose a game and start playing!</p>
  <input class="search" id="search"
    placeholder="🔎 Search games...">
</section>

<main class="container" id="games">

<h2>🎮 Game Library</h2>

<div class="categories">
  <button class="active" onclick="filterGames('all',this)">All Games</button>
  <button onclick="filterGames('arcade',this)">Arcade</button>
  <button onclick="filterGames('puzzle',this)">Puzzle</button>
  <button onclick="filterGames('strategy',this)">Strategy</button>
</div>

<div class="grid" id="gameGrid">

  <div class="card" data-type="arcade">
    <div class="emoji">🐍</div>
    <h3>Snake</h3>
    <p>Eat food and grow your snake. Don't hit yourself!</p>
    <button onclick="startGame('snake')">PLAY NOW</button>
  </div>

  <div class="card" data-type="strategy">
    <div class="emoji">❌</div>
    <h3>Tic-Tac-Toe</h3>
    <p>Play against a friend. Get three in a row!</p>
    <button onclick="startGame('tic')">PLAY NOW</button>
  </div>

  <div class="card" data-type="puzzle">
    <div class="emoji">🧠</div>
    <h3>Memory Match</h3>
    <p>Find matching pairs and test your memory.</p>
    <button onclick="startGame('memory')">PLAY NOW</button>
  </div>

  <div class="card" data-type="arcade">
    <div class="emoji">🎯</div>
    <h3>Target Rush</h3>
    <p>Click as many targets as possible in 20 seconds!</p>
    <button onclick="startGame('target')">PLAY NOW</button>
  </div>

</div>

<section id="gameScreen">
  <h2 id="gameTitle">Game</h2>
  <p id="gameInfo">Have fun!</p>
  <div id="gameArea"></div>
  <button onclick="stopGame()">← BACK TO GAMES</button>
</section>

</main>

<footer>
  <h3 style="color:#bd91ff">✦ IXL-WORKS ✦</h3>
  <p style="margin-top:10px">Your universe. Your games. Your rules.</p>
  <p style="margin-top:12px;font-size:12px">© 2026 IXL-WORKS</p>
</footer>

<script>
let currentGame=null;
let timers=[];
let snakeInterval=null;

function timer(fn,ms){
  let id=setTimeout(fn,ms);
  timers.push(id);
  return id;
}

function interval(fn,ms){
  let id=setInterval(fn,ms);
  timers.push(id);
  return id;
}

function clearTimers(){
  timers.forEach(clearTimeout);
  timers=[];
}

function stopGame(){
  clearTimers();
  if(snakeInterval) clearInterval(snakeInterval);
  snakeInterval=null;
  currentGame=null;
  document.getElementById("gameScreen").style.display="none";
  document.getElementById("gameGrid").style.display="grid";
}

function startGame(game){
  stopGame();
  currentGame=game;
  document.getElementById("gameGrid").style.display="none";
  document.getElementById("gameScreen").style.display="block";
  document.getElementById("gameScreen").scrollIntoView({behavior:"smooth"});
  const area=document.getElementById("gameArea");
  const title=document.getElementById("gameTitle");
  const info=document.getElementById("gameInfo");

  if(game==="snake"){
    title.textContent="🐍 Snake";
    info.textContent="Use the arrow keys to move!";
    playSnake(area,info);
  }

  if(game==="tic"){
    title.textContent="❌ Tic-Tac-Toe";
    playTic(area,info);
  }

  if(game==="memory"){
    title.textContent="🧠 Memory Match";
    playMemory(area,info);
  }

  if(game==="target"){
    title.textContent="🎯 Target Rush";
    playTarget(area,info);
  }
}

function filterGames(type,button){
  document.querySelectorAll(".categories button")
    .forEach(b=>b.classList.remove("active"));
  button.classList.add("active");

  document.querySelectorAll(".card").forEach(card=>{
    card.classList.toggle("hidden",
      type!=="all" && card.dataset.type!==type);
  });
}

document.getElementById("search").addEventListener("input",e=>{
  const q=e.target.value.toLowerCase();
  document.querySelectorAll(".card").forEach(card=>{
    card.classList.toggle("hidden",
      !card.innerText.toLowerCase().includes(q));
  });
});

// TIC TAC TOE

function playTic(area,info){
  let board=Array(9).fill("");
  let turn="X";
  const wins=[
    [0,1,2],[3,4,5],[6,7,8],
    [0,3,6],[1,4,7],[2,5,8],
    [0,4,8],[2,4,6]
  ];

  area.innerHTML='<div class="cells">'+
    board.map((_,i)=>`<button class="cell" data-i="${i}"></button>`).join("")+
    '</div><br><button class="game-button" id="reset">RESTART</button>';

  function render(){
    area.querySelectorAll(".cell").forEach((b,i)=>{
      b.textContent=board[i];
    });
  }

  function check(){
    if(wins.some(w=>w.every(i=>board[i]===turn))){
      info.textContent=turn+" WINS! 🎉";
      return true;
    }
    if(board.every(Boolean)){
      info.textContent="It's a draw!";
      return true;
    }
    return false;
  }

  area.querySelectorAll(".cell").forEach(b=>{
    b.onclick=()=>{
      let i=Number(b.dataset.i);
      if(board[i] || check())return;
      board[i]=turn;
      render();
      if(!check()){
        turn=turn==="X"?"O":"X";
        info.textContent=turn+"'s turn";
      }
    };
  });

  area.querySelector("#reset").onclick=()=>{
    board.fill("");
    turn="X";
    info.textContent="X's turn";
    render();
  };
}

// MEMORY MATCH

function playMemory(area,info){
  const symbols=["🚀","🌟","🎮","👾","💎","🔥","🪐","🎯"];
  let cards=[...symbols,...symbols].sort(()=>Math.random()-.5);
  let first=null;
  let locked=false;
  let matched=0;

  area.innerHTML='<div class="memory-grid">'+
    cards.map((_,i)=>`<button class="memory-card" data-i="${i}">?</button>`).join("")+
    '</div><br><button class="game-button" id="resetMemory">RESTART</button>';

  const buttons=[...area.querySelectorAll(".memory-card")];

  buttons.forEach((b,i)=>{
    b.onclick=()=>{
      if(locked || b.textContent!=="?")return;
      b.textContent=cards[i];

      if(first===null){
        first={button:b,index:i};
        return;
      }

      locked=true;
      if(cards[first.index]===cards[i]){
        matched+=2;
        first=null;
        locked=false;
        info.textContent="Great match! ⭐ "+matched+"/16";
        if(matched===16)info.textContent="YOU WON! 🏆";
      }else{
        let old=first.button;
        first=null;
        timer(()=>{
          old.textContent="?";
          b.textContent="?";
          locked=false;
        },750);
      }
    };
  });

  area.querySelector("#resetMemory").onclick=()=>{
    startGame("memory");
  };
}

// TARGET RUSH

function playTarget(area,info){
  let score=0;
  let time=20;
  let ended=false;

  area.innerHTML=`
    <p>Score: <span id="score">0</span></p>
    <p>Time: <span id="time">20</span>s</p>
    <div id="targetArea">
      <button class="target" id="target">🎯</button>
    </div>
    <button class="game-button" id="startTarget">START GAME</button>
  `;

  const target=area.querySelector("#target");
  const zone=area.querySelector("#targetArea");

  target.hidden=true;

  function move(){
    target.style.left=Math.random()*(zone.clientWidth-48)+"px";
    target.style.top=Math.random()*(zone.clientHeight-48)+"px";
  }

  area.querySelector("#startTarget").onclick=()=>{
    score=0;
    time=20;
    ended=false;
    area.querySelector("#score").textContent=score;
    area.querySelector("#time").textContent=time;
    target.hidden=false;
    move();

    interval(()=>{
      if(ended)return;
      time--;
      area.querySelector("#time").textContent=time;
      if(time<=0){
        ended=true;
        target.hidden=true;
        info.textContent="TIME UP! Your score: "+score+" 🏆";
      }
    },1000);
  };

  target.onclick=()=>{
    if(ended || target.hidden)return;
    score++;
    area.querySelector("#score").textContent=score;
    move();
  };
}

// SNAKE

function playSnake(area,info){
  area.innerHTML=`
    <p>Score: <span id="snakeScore">0</span></p>
    <canvas id="snakeCanvas" width="320" height="320"></canvas>
    <p style="margin:12px">Arrow keys or WASD to move</p>
    <button class="game-button" id="snakeStart">START / RESTART</button>
    <div style="margin-top:12px">
      <button onclick="changeDirection(0,-1)">⬆️</button><br>
      <button onclick="changeDirection(-1,0)">⬅️</button>
      <button onclick="changeDirection(0,1)">⬇️</button>
      <button onclick="changeDirection(1,0)">➡️</button>
    </div>
  `;

  const canvas=area.querySelector("#snakeCanvas");
  const ctx=canvas.getContext("2d");
  let snake,food,dx,dy,score,running=false;

  function reset(){
    if(snakeInterval)clearInterval(snakeInterval);
    snakeInterval=null;
    snake=[{x:8,y:8},{x:7,y:8},{x:6,y:8}];
    dx=1;dy=0;score=0;running=true;
    food={x:14,y:10};
    area.querySelector("#snakeScore").textContent=score;
    draw();
    snakeInterval=setInterval(tick,130);
  }

  function draw(){
    ctx.fillStyle="#090e19";
    ctx.fillRect(0,0,320,320);
    ctx.fillStyle="#ff4b8a";
    ctx.fillRect(food.x*16,food.y*16,15,15);
    snake.forEach((s,i)=>{
      ctx.fillStyle=i===0?"#c49aff":"#7b54b5";
      ctx.fillRect(s.x*16,s.y*16,15,15);
    });
  }

  function tick(){
    let head={x:snake[0].x+dx,y:snake[0].y+dy};
    if(head.x<0||head.y<0||head.x>=20||head.y>=20||
       snake.some(s=>s.x===head.x&&s.y===head.y)){
      running=false;
      clearInterval(snakeInterval);
      snakeInterval=null;
      info.textContent="GAME OVER! Score: "+score;
      return;
    }

    snake.unshift(head);

    if(head.x===food.x&&head.y===food.y){
      score++;
      area.querySelector("#snakeScore").textContent=score;
      do{
        food={x:Math.floor(Math.random()*20),y:Math.floor(Math.random()*20)};
      }while(snake.some(s=>s.x===food.x&&s.y===food.y));
    }else{
      snake.pop();
    }
    draw();
  }

  area.querySelector("#snakeStart").onclick=reset;
  window.changeDirection=(x,y)=>{
    if(!running)return;
    if(x===-dx&&y===-dy)return;
    dx=x;dy=y;
  };

  window.onkeydown=e=>{
    if(currentGame!=="snake")return;
    const keys={
      ArrowUp:[0,-1],w:[0,-1],
      ArrowDown:[0,1],s:[0,1],
      ArrowLeft:[-1,0],a:[-1,0],
      ArrowRight:[1,0],d:[1,0]
    };
    let dir=keys[e.key];
    if(dir){
      e.preventDefault();
      changeDirection(...dir);
    }
  };

  reset();
}
</script>
</body>
</html>
