<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Banyu Game Center</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

body{
    font-family:Arial,sans-serif;
    min-height:100vh;
    color:white;
    background:
    radial-gradient(circle at 20% 10%,#4c1d95,transparent 35%),
    radial-gradient(circle at 80% 90%,#0369a1,transparent 35%),
    #020617;
    overflow-x:hidden;
}

header{
    text-align:center;
    padding:35px 15px;
}

.logo{
    font-size:60px;
    animation:pulse 2s infinite;
}

h1{
    font-size:42px;
    background:linear-gradient(90deg,#22d3ee,#a78bfa,#f472b6,#22d3ee);
    background-size:300%;
    -webkit-background-clip:text;
    color:transparent;
    animation:fusing 4s linear infinite;
}

.subtitle{
    color:#cbd5e1;
    margin:10px 0;
}

.developer{
    display:inline-block;
    padding:8px 18px;
    margin-top:10px;
    border:1px solid #38bdf8;
    border-radius:30px;
    box-shadow:0 0 20px #0ea5e9;
    color:#7dd3fc;
}

.topbar{
    width:92%;
    max-width:1100px;
    margin:auto;
    display:flex;
    justify-content:space-between;
    gap:10px;
    flex-wrap:wrap;
}

.topButton{
    border:1px solid #38bdf8;
    background:rgba(255,255,255,.08);
    color:white;
    padding:11px 18px;
    border-radius:12px;
    cursor:pointer;
}

.score{
    padding:11px 18px;
    border-radius:12px;
    background:rgba(34,197,94,.15);
    border:1px solid #22c55e;
}

.container{
    width:92%;
    max-width:1100px;
    margin:auto;
}

.games{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:20px;
    margin-top:25px;
}

.card{
    position:relative;
    overflow:hidden;
    padding:25px 20px;
    text-align:center;
    border-radius:22px;
    background:rgba(255,255,255,.07);
    border:1px solid rgba(255,255,255,.15);
    backdrop-filter:blur(12px);
    transition:.3s;
}

.card::before{
    content:"";
    position:absolute;
    width:180px;
    height:180px;
    top:-100px;
    left:-100px;
    background:linear-gradient(
        45deg,
        #00eaff,
        #8b5cf6,
        #ff00cc,
        #00eaff
    );
    background-size:300%;
    filter:blur(35px);
    opacity:.5;
    animation:fusing 4s linear infinite;
}

.card:hover{
    transform:translateY(-8px) scale(1.03);
    box-shadow:
    0 0 15px #22d3ee,
    0 0 35px #8b5cf6;
}

.icon{
    position:relative;
    font-size:50px;
    margin-bottom:10px;
}

.card h2,
.card p,
.card button{
    position:relative;
}

.card p{
    color:#cbd5e1;
    min-height:42px;
    margin:8px 0 18px;
}

.play{
    width:100%;
    padding:13px;
    border:0;
    border-radius:12px;
    color:white;
    font-weight:bold;
    cursor:pointer;
    background:linear-gradient(90deg,#2563eb,#7c3aed,#db2777);
    background-size:200%;
    animation:gradient 3s infinite;
}

.play:hover{
    box-shadow:0 0 20px #a78bfa;
}

#gameArea{
    display:none;
    margin:30px auto;
    padding:30px;
    max-width:650px;
    text-align:center;
    border-radius:25px;
    background:rgba(0,0,0,.4);
    border:1px solid rgba(255,255,255,.2);
    box-shadow:0 0 35px rgba(59,130,246,.25);
}

#gameTitle{
    font-size:32px;
    margin-bottom:15px;
}

input{
    width:90%;
    max-width:350px;
    padding:14px;
    margin:10px;
    border:0;
    border-radius:12px;
    text-align:center;
    font-size:17px;
}

.gameBtn{
    padding:13px 25px;
    border:0;
    border-radius:12px;
    background:#22c55e;
    color:white;
    font-weight:bold;
    cursor:pointer;
    margin:7px;
}

.gameBtn:hover{
    box-shadow:0 0 20px #22c55e;
}

.back{
    background:#ef4444;
}

#result{
    margin:20px 0;
    min-height:30px;
    font-size:20px;
}

footer{
    text-align:center;
    color:#94a3b8;
    margin:50px 0 25px;
}

@keyframes fusing{
    0%{background-position:0% 50%}
    50%{background-position:100% 50%}
    100%{background-position:0% 50%}
}

@keyframes gradient{
    0%{background-position:0%}
    50%{background-position:100%}
    100%{background-position:0%}
}

@keyframes pulse{
    0%,100%{transform:scale(1)}
    50%{transform:scale(1.12)}
}
</style>
</head>

<body>

<header>

<div class="logo">🎮</div>

<h1>BANYU GAME CENTER</h1>

<p class="subtitle">
🔥 Banyak Game • 🔊 Banyak Suara • 🏆 Banyak Tantangan
</p>

<div class="developer">
⚡ GAME DIBUAT OLEH DEVELOPER BANYU ⚡
</div>

</header>

<div class="topbar">

<button class="topButton" onclick="toggleSound()">
🔊 <span id="soundText">Suara ON</span>
</button>

<div class="score">
🏆 Skor: <span id="score">0</span>
</div>

</div>

<div class="container">

<div class="games">

<!-- 1 -->

<div class="card">
<div class="icon">🎯</div>
<h2>Tebak Angka</h2>
<p>Tebak angka rahasia 1 sampai 100.</p>
<button class="play" onclick="openGame('angka')">🔥 MAIN</button>
</div>

<!-- 2 -->

<div class="card">
<div class="icon">🧠</div>
<h2>Quiz</h2>
<p>Uji pengetahuanmu dengan pertanyaan.</p>
<button class="play" onclick="openGame('quiz')">🔥 MAIN</button>
</div>

<!-- 3 -->

<div class="card">
<div class="icon">🌎</div>
<h2>Tebak Negara</h2>
<p>Tebak negara berdasarkan petunjuk.</p>
<button class="play" onclick="openGame('negara')">🔥 MAIN</button>
</div>

<!-- 4 -->

<div class="card">
<div class="icon">🐾</div>
<h2>Tebak Hewan</h2>
<p>Tebak hewan dari ciri-cirinya.</p>
<button class="play" onclick="openGame('hewan')">🔥 MAIN</button>
</div>

<!-- 5 -->

<div class="card">
<div class="icon">➗</div>
<h2>Matematika</h2>
<p>Perkalian dan pembagian cepat.</p>
<button class="play" onclick="openGame('math')">🔥 MAIN</button>
</div>

<!-- 6 -->

<div class="card">
<div class="icon">🧩</div>
<h2>Tebak Benda</h2>
<p>Tebak benda dari petunjuk.</p>
<button class="play" onclick="openGame('benda')">🔥 MAIN</button>
</div>

<!-- 7 -->

<div class="card">
<div class="icon">⚡</div>
<h2>Reaksi Cepat</h2>
<p>Uji kecepatan reaksimu.</p>
<button class="play" onclick="openGame('reaksi')">🔥 MAIN</button>
</div>

<!-- 8 -->

<div class="card">
<div class="icon">🔢</div>
<h2>Hitung Cepat</h2>
<p>Selesaikan soal matematika.</p>
<button class="play" onclick="openGame('hitung')">🔥 MAIN</button>
</div>

<!-- 9 -->

<div class="card">
<div class="icon">🪙</div>
<h2>Tebak Koin</h2>
<p>Pilih gambar atau angka.</p>
<button class="play" onclick="openGame('koin')">🔥 MAIN</button>
</div>

<!-- 10 -->

<div class="card">
<div class="icon">✊</div>
<h2>Batu Gunting Kertas</h2>
<p>Lawan komputer!</p>
<button class="play" onclick="openGame('rps')">🔥 MAIN</button>
</div>

<!-- 11 -->

<div class="card">
<div class="icon">🧠</div>
<h2>Memory Game</h2>
<p>Ingat pasangan emoji.</p>
<button class="play" onclick="openGame('memory')">🔥 MAIN</button>
</div>

</div>

<div id="gameArea">

<h2 id="gameTitle"></h2>

<div id="gameContent"></div>

<button class="gameBtn back" onclick="closeGame()">
⬅ KEMBALI
</button>

</div>

</div>

<footer>
© 2026 Banyu Game Center<br>
Dibuat oleh <b>Developer Banyu</b>
</footer>


<script>

/* =========================
   SISTEM SUARA
========================= */

let soundOn=true;
let audioContext;

function sound(type){

    if(!soundOn) return;

    if(!audioContext){
        audioContext=new
        (window.AudioContext||window.webkitAudioContext)();
    }

    const oscillator=audioContext.createOscillator();
    const gain=audioContext.createGain();

    oscillator.connect(gain);
    gain.connect(audioContext.destination);

    if(type==="click"){
        oscillator.frequency.value=500;
    }

    if(type==="win"){
        oscillator.frequency.value=800;
    }

    if(type==="wrong"){
        oscillator.frequency.value=180;
    }

    oscillator.start();

    gain.gain.setValueAtTime(.12,audioContext.currentTime);

    gain.gain.exponentialRampToValueAtTime(
        .001,
        audioContext.currentTime+.25
    );

    oscillator.stop(audioContext.currentTime+.25);
}

function toggleSound(){

    soundOn=!soundOn;

    document.getElementById("soundText").innerText=
    soundOn ? "Suara ON":"Suara OFF";

}


/* =========================
   SCORE
========================= */

let score=0;

function addScore(points){

    score+=points;

    document.getElementById("score")
    .innerText=score;

}


/* =========================
   OPEN GAME
========================= */

function openGame(game){

    sound("click");

    document.querySelector(".games")
    .style.display="none";

    document.getElementById("gameArea")
    .style.display="block";

    if(game==="angka") angka();
    if(game==="quiz") quiz();
    if(game==="negara") negara();
    if(game==="hewan") hewan();
    if(game==="math") math();
    if(game==="benda") benda();
    if(game==="reaksi") reaksi();
    if(game==="hitung") hitung();
    if(game==="koin") koin();
    if(game==="rps") rps();
    if(game==="memory") memory();

}


/* =========================
   CLOSE
========================= */

function closeGame(){

    sound("click");

    document.querySelector(".games")
    .style.display="grid";

    document.getElementById("gameArea")
    .style.display="none";

}


/* =========================
   TEBAK ANGKA
========================= */

let secretNumber;

function angka(){

    secretNumber=Math.floor(Math.random()*100)+1;

    document.getElementById("gameTitle")
    .innerText="🎯 Tebak Angka";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Tebak angka 1 sampai 100!</p>

    <input id="answer"
    type="number"
    placeholder="Masukkan angka">

    <br>

    <button class="gameBtn"
    onclick="checkAngka()">
    TEBAK
    </button>

    <p id="result"></p>

    `;

}

function checkAngka(){

    let value=Number(
        document.getElementById("answer").value
    );

    if(value===secretNumber){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🎉 BENAR! +10 POIN";

    }

    else{

        sound("wrong");

        document.getElementById("result")
        .innerText=value<secretNumber
        ?"⬆️ Terlalu kecil!"
        :"⬇️ Terlalu besar!";

    }

}


/* =========================
   QUIZ
========================= */

function quiz(){

    document.getElementById("gameTitle")
    .innerText="🧠 Quiz";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Planet yang kita tinggali adalah?</p>

    <input id="answer"
    placeholder="Jawaban">

    <br>

    <button class="gameBtn"
    onclick="checkQuiz()">
    JAWAB
    </button>

    <p id="result"></p>

    `;

}

function checkQuiz(){

    let a=document.getElementById("answer")
    .value.toLowerCase();

    if(a==="bumi"){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🎉 BENAR! +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText="❌ Salah!";

    }

}


/* =========================
   NEGARA
========================= */

function negara(){

    document.getElementById("gameTitle")
    .innerText="🌎 Tebak Negara";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Aku memiliki Menara Eiffel. Negara apakah aku?</p>

    <input id="answer"
    placeholder="Jawaban">

    <br>

    <button class="gameBtn"
    onclick="checkNegara()">
    JAWAB
    </button>

    <p id="result"></p>

    `;

}

function checkNegara(){

    let a=document.getElementById("answer")
    .value.toLowerCase();

    if(a==="prancis"||a==="perancis"){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🎉 BENAR! +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText="❌ Salah!";

    }

}


/* =========================
   HEWAN
========================= */

function hewan(){

    document.getElementById("gameTitle")
    .innerText="🐾 Tebak Hewan";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Aku memiliki belalai panjang. Aku siapa?</p>

    <input id="answer"
    placeholder="Jawaban">

    <br>

    <button class="gameBtn"
    onclick="checkHewan()">
    JAWAB
    </button>

    <p id="result"></p>

    `;

}

function checkHewan(){

    let a=document.getElementById("answer")
    .value.toLowerCase();

    if(a==="gajah"){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🎉 BENAR! +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText="❌ Salah!";

    }

}


/* =========================
   MATEMATIKA
========================= */

function math(){

    let a=Math.floor(Math.random()*10)+1;
    let b=Math.floor(Math.random()*10)+1;

    let correct=a*b;

    document.getElementById("gameTitle")
    .innerText="➗ Matematika";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>${a} × ${b} = ?</p>

    <input id="answer"
    type="number"
    placeholder="Jawaban">

    <br>

    <button class="gameBtn"
    onclick="checkMath(${correct})">
    JAWAB
    </button>

    <p id="result"></p>

    `;

}

function checkMath(correct){

    let a=Number(
        document.getElementById("answer").value
    );

    if(a===correct){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🎉 BENAR! +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText="❌ Salah!";

    }

}


/* =========================
   BENDA
========================= */

function benda(){

    document.getElementById("gameTitle")
    .innerText="🧩 Tebak Benda";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Aku digunakan untuk melihat waktu dan punya jarum.</p>

    <input id="answer"
    placeholder="Jawaban">

    <br>

    <button class="gameBtn"
    onclick="checkBenda()">
    JAWAB
    </button>

    <p id="result"></p>

    `;

}

function checkBenda(){

    let a=document.getElementById("answer")
    .value.toLowerCase();

    if(a==="jam"){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🎉 BENAR! +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText="❌ Salah!";

    }

}


/* =========================
   REAKSI CEPAT
========================= */

function reaksi(){

    document.getElementById("gameTitle")
    .innerText="⚡ Reaksi Cepat";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Klik MULAI lalu tunggu tombol muncul!</p>

    <button class="gameBtn"
    onclick="reactionStart()">
    MULAI
    </button>

    <p id="result"></p>

    `;

}

function reactionStart(){

    sound("click");

    document.getElementById("gameContent")
    .innerHTML=`
    <h2>TUNGGU...</h2>
    `;

    let delay=Math.random()*3000+1000;

    setTimeout(()=>{

        window.reactionTime=Date.now();

        document.getElementById("gameContent")
        .innerHTML=`

        <button class="gameBtn"
        onclick="reactionEnd()">
        ⚡ KLIK SEKARANG!
        </button>

        `;

    },delay);

}

function reactionEnd(){

    let time=Date.now()-window.reactionTime;

    sound("win");

    let points=Math.max(
        1,
        Math.floor(1000/time*20)
    );

    addScore(points);

    document.getElementById("gameContent")
    .innerHTML=`

    <h2>⚡ ${time} ms</h2>

    <p>+${points} POIN!</p>

    <button class="gameBtn"
    onclick="reaksi()">
    COBA LAGI
    </button>

    `;

}


/* =========================
   HITUNG CEPAT
========================= */

function hitung(){

    let a=Math.floor(Math.random()*30)+1;
    let b=Math.floor(Math.random()*30)+1;

    let correct=a+b;

    document.getElementById("gameTitle")
    .innerText="🔢 Hitung Cepat";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>${a} + ${b} = ?</p>

    <input id="answer"
    type="number"
    placeholder="Jawaban">

    <br>

    <button class="gameBtn"
    onclick="checkHitung(${correct})">
    JAWAB
    </button>

    <p id="result"></p>

    `;

}

function checkHitung(correct){

    let a=Number(
        document.getElementById("answer").value
    );

    if(a===correct){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText="🔥 BENAR! +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText="❌ Salah!";

    }

}


/* =========================
   TEBAK KOIN
========================= */

function koin(){

    document.getElementById("gameTitle")
    .innerText="🪙 Tebak Koin";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Pilih: ANGKA atau GAMBAR?</p>

    <button class="gameBtn"
    onclick="coin('angka')">
    🔢 ANGKA
    </button>

    <button class="gameBtn"
    onclick="coin('gambar')">
    🪙 GAMBAR
    </button>

    <p id="result"></p>

    `;

}

function coin(choice){

    let result=Math.random()<.5
    ?"angka"
    :"gambar";

    if(choice===result){

        sound("win");
        addScore(10);

        document.getElementById("result")
        .innerText=
        "🎉 BENAR! Hasilnya "+result+" +10";

    }else{

        sound("wrong");

        document.getElementById("result")
        .innerText=
        "❌ Salah! Hasilnya "+result;

    }

}


/* =========================
   BATU GUNTING KERTAS
========================= */

function rps(){

    document.getElementById("gameTitle")
    .innerText="✊ Batu Gunting Kertas";

    document.getElementById("gameContent")
    .innerHTML=`

    <p>Pilih senjatamu!</p>

    <button class="gameBtn"
    onclick="playRPS('batu')">
    🪨 BATU
    </button>

    <button class="gameBtn"
    onclick="playRPS('gunting')">
    ✂️ GUNTING
    </button>

    <button class="gameBtn"
    onclick="playRPS('kertas')">
    📄 KERTAS
    </button>

    <p id="result"></p>

    `;

}

function playRPS(player){

    let choices=["batu","gunting","kertas"];

    let computer=
    choices[Math.floor(Math.random()*3)];

    let result="";

    if(player===computer){

        result="🤝 SERI!";

    }else if(

        (player==="batu"&&computer==="gunting")||
        (player==="gunting"&&computer==="kertas")||
        (player==="kertas"&&computer==="batu")

    ){

        result="🎉 KAMU MENANG! +10";

        sound("win");
        addScore(10);

    }else{

        result="❌ KAMU KALAH!";

        sound("wrong");

    }

    document.getElementById("result")
    .innerText=
    result+" Komputer: "+computer;

}


/* =========================
   MEMORY GAME
========================= */

let memoryCards=[];
let firstCard=null;
let lock=false;

function memory(){

    memoryCards=[
        "🍎","🍎",
        "🐱","🐱",
        "🚗","🚗",
        "⚽","⚽",
        "⭐","⭐",
        "🔥","🔥"
    ];

    memoryCards.sort(()=>Math.random()-.5);

    document.getElementById("gameTitle")
    .innerText="🧠 Memory Game";

    let html=`

    <p>Cari pasangan emoji yang sama!</p>

    <div style="
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:10px;
    max-width:400px;
    margin:20px auto;
    ">`;

    memoryCards.forEach((card,index)=>{

        html+=`

        <button
        id="card${index}"
        class="gameBtn"
        style="height:70px;font-size:25px"
        onclick="flipCard(${index})">
        ❓
        </button>

        `;

    });

    html+=`</div><p id="result"></p>`;

    document.getElementById("gameContent")
    .innerHTML=html;

    firstCard=null;
    lock=false;

}

function flipCard(index){

    if(lock) return;

    let button=document.getElementById("card"+index);

    if(button.innerText!=="❓") return;

    button.innerText=memoryCards[index];

    if(firstCard===null){

        firstCard=index;

    }else{

        let second=index;

        lock=true;

        if(memoryCards[firstCard]===memoryCards[second]){

            sound("win");
            addScore(20);

            document.getElementById("result")
            .innerText="🎉 Pasangan ditemukan! +20";

            firstCard=null;
            lock=false;

        }else{

            sound("wrong");

            setTimeout(()=>{

                document.getElementById("card"+firstCard)
                .innerText="❓";

                document.getElementById("card"+second)
                .innerText="❓";

                firstCard=null;
                lock=false;

            },700);

        }

    }

}

</script>

</body>
</html>
