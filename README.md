ludrien valks and rudson emile website
<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<title>Human Time Calculator + Games</title>
<style>
body { font-family: Arial; text-align:center; background:#f5f5f5; }
.container { background:white; padding:20px; margin:20px auto; width:320px; border-radius:10px; box-shadow:0 4px 10px rgba(0,0,0,0.1);} 
button { margin:5px; padding:10px; border:none; border-radius:6px; cursor:pointer; }
#time { font-size:2em; }
.grid { display:grid; grid-template-columns:repeat(3,80px); gap:5px; justify-content:center; }
.cell { width:80px; height:80px; font-size:2em; background:#eee; display:flex; align-items:center; justify-content:center; cursor:pointer; }
</style>
</head>
<body><h1>Human Time Calculator</h1><div class="container">
<input type="number" id="people" placeholder="Number of people"><br>
<div id="time">00:00</div>
<button onclick="startTimer()">Start</button>
<button onclick="stopTimer()">Stop</button>
<div id="result"></div>
</div><div class="container">
<h2>Rock Paper Scissors</h2>
<button onclick="playRPS('rock')">Rock</button>
<button onclick="playRPS('paper')">Paper</button>
<button onclick="playRPS('scissors')">Scissors</button>
<div id="rpsResult"></div>
</div><div class="container">
<h2>Tic Tac Toe</h2>
<div class="grid" id="board"></div>
<div id="tttResult"></div>
<button onclick="resetGame()">Reset</button>
</div><script>
// TIMER
let startTime, interval;
function startTimer(){
 startTime = Date.now();
 interval = setInterval(()=>{
  let diff = Date.now()-startTime;
  let s = Math.floor(diff/1000);
  let m = Math.floor(s/60);
  s = s%60;
  document.getElementById('time').innerText = `${m.toString().padStart(2,'0')}:${s.toString().padStart(2,'0')}`;
 },1000);
}
function stopTimer(){
 clearInterval(interval);
 let mins = (Date.now()-startTime)/60000;
 let people = document.getElementById('people').value;
 let wasted = mins * people;
 document.getElementById('result').innerText = `Wasted: ${wasted.toFixed(2)} minutes`;
}

// RPS
function playRPS(player){
 let choices=['rock','paper','scissors'];
 let ai = choices[Math.floor(Math.random()*3)];
 let result='';
 if(player===ai) result='Draw';
 else if((player==='rock'&&ai==='scissors')||(player==='paper'&&ai==='rock')||(player==='scissors'&&ai==='paper')) result='You win';
 else result='You lose';
 document.getElementById('rpsResult').innerText = `You: ${player} | AI: ${ai} → ${result}`;
}

// TIC TAC TOE
let board = Array(9).fill('');
let current='X';
const boardDiv=document.getElementById('board');

function renderBoard(){
 boardDiv.innerHTML='';
 board.forEach((cell,i)=>{
  let div=document.createElement('div');
  div.className='cell';
  div.innerText=cell;
  div.onclick=()=>move(i);
  boardDiv.appendChild(div);
 });
}

function move(i){
 if(board[i]||checkWin()) return;
 board[i]=current;
 current=current==='X'?'O':'X';
 renderBoard();
 let winner=checkWin();
 if(winner) document.getElementById('tttResult').innerText=winner+' wins';
}

function checkWin(){
 const wins=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
 for(let w of wins){
  if(board[w[0]] && board[w[0]]===board[w[1]] && board[w[1]]===board[w[2]]) return board[w[0]];
 }
 return null;
}

function resetGame(){
 board=Array(9).fill('');
 current='X';
 document.getElementById('tttResult').innerText='';
 renderBoard();
}

renderBoard();
</script></body>
</html>

On Tue, Apr 21, 2026, 2:30 PM lanox valk <ludrien2009@gmail.com> wrote:
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Human Time Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin-top: 50px;
      background: #f5f5f5;
    }

    h1 {
      font-size: 2.5em;
    }

    .container {
      background: white;
      padding: 30px;
      border-radius: 12px;
      width: 300px;
      margin: auto;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }

    input {
      padding: 10px;
      font-size: 1em;
      width: 80%;
      margin-bottom: 15px;
    }

    button {
      padding: 10px 15px;
      margin: 5px;
      font-size: 1em;
      cursor: pointer;
      border: none;
      border-radius: 8px;
    }

    .start { background: #4CAF50; color: white; }
    .stop { background: #f44336; color: white; }

    #time {
      font-size: 2em;
      margin: 15px 0;
    }

    #result {
      margin-top: 20px;
      font-size: 1.2em;
      font-weight: bold;
    }
  </style>
</head>
      document.getElementById("result").innerText =
        `Total human time wasted: ${wasted.toFixed(2)} minutes`;
    }
  </script>

</body>
</html>
