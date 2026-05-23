<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Addio al nubilato di Valentina 💍</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=DM+Sans:wght@400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --pink: #d4537e; --pink-light: #fbeaf0; --pink-dark: #72243e;
      --gold: #ef9f27; --gold-light: #faeeda;
      --teal: #1d9e75; --teal-light: #e1f5ee;
      --purple: #7f77dd; --purple-light: #eeedfe;
      --blue: #378add; --blue-light: #e6f1fb;
      --text: #1a1a1a; --text-muted: #6b6b6b;
      --border: rgba(0,0,0,0.1);
      --radius: 16px;
      --c0: #d4537e; --c0l: #fbeaf0; --c0d: #72243e;
      --c1: #7f77dd; --c1l: #eeedfe; --c1d: #3c3489;
      --c2: #1d9e75; --c2l: #e1f5ee; --c2d: #0f6e56;
    }
    body { font-family: "DM Sans", sans-serif; color: var(--text); min-height: 100vh; background: linear-gradient(135deg, #72243e 0%, #3c1a2e 50%, #0f3028 100%); }

    .ribbon { text-align: center; padding: 1.6rem 1rem 1rem; color: white; }
    .ribbon h1 { font-family: "Playfair Display", serif; font-size: clamp(20px,5vw,30px); font-weight: 700; text-shadow: 0 2px 8px rgba(0,0,0,0.4); }
    .ribbon p { font-size: 13px; opacity: 0.85; margin-top: 4px; }

    .container { max-width: 560px; margin: 0 auto; padding: 1rem 1rem 3rem; }
    .screen { display: none; }
    .screen.active { display: block; }

    .card { background: rgba(255,255,255,0.12); border-radius: var(--radius); border: 1px solid rgba(255,255,255,0.2); box-shadow: 0 4px 24px rgba(0,0,0,0.2); }

    .setup-intro { text-align: center; padding: 0.4rem 0 1rem; color: white; }
    .setup-intro h2 { font-family: "Playfair Display", serif; font-size: 20px; margin-bottom: 5px; }
    .setup-intro p { font-size: 13px; opacity: 0.85; }

    .teams-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 10px; }
    .tsc { background: rgba(255,255,255,0.12); border-radius: var(--radius); border: 2px solid rgba(255,255,255,0.2); padding: 12px 10px; }
    .tsc.c0 { border-color: var(--c0); } .tsc.c1 { border-color: var(--c1); } .tsc.c2 { border-color: var(--c2); }
    .tsc-label { font-size: 12px; font-weight: 500; margin-bottom: 8px; display: flex; align-items: center; gap: 5px; color: white; }
    .dot { width: 9px; height: 9px; border-radius: 50%; flex-shrink: 0; }
    .d0 { background: var(--c0); } .d1 { background: var(--c1); } .d2 { background: var(--c2); }
    .fl { font-size: 11px; color: rgba(255,255,255,0.7); text-transform: uppercase; letter-spacing: 0.4px; margin: 7px 0 3px; }
    input[type="text"], textarea {
      width: 100%; padding: 7px 9px; border: 1.5px solid rgba(255,255,255,0.3); border-radius: 9px;
      font-family: "DM Sans", sans-serif; font-size: 13px; color: white;
      background: rgba(255,255,255,0.15); outline: none; transition: border-color 0.2s;
    }
    input[type="text"]:focus, textarea:focus { border-color: var(--pink); }
    textarea { resize: vertical; min-height: 70px; }
    input::placeholder, textarea::placeholder { color: rgba(255,255,255,0.4); }

    .btn {
      display: inline-flex; align-items: center; justify-content: center; gap: 8px;
      padding: 12px 22px; border-radius: 50px; font-family: "DM Sans", sans-serif;
      font-size: 14px; font-weight: 500; cursor: pointer; border: none; transition: transform 0.15s, opacity 0.15s;
    }
    .btn:active { transform: scale(0.97); }
    .btn-primary { background: linear-gradient(135deg, var(--pink), var(--pink-dark)); color: white; width: 100%; margin-top: 12px; box-shadow: 0 4px 14px rgba(212,83,126,0.45); }
    .btn-teal { background: linear-gradient(135deg, var(--teal), #085041); color: white; width: 100%; box-shadow: 0 4px 14px rgba(29,158,117,0.35); }
    .btn-skip { background: rgba(255,255,255,0.15); color: white; border: 1.5px solid rgba(255,255,255,0.3); flex: 1; }
    .btn-done { background: linear-gradient(135deg, var(--teal), #085041); color: white; flex: 1; }
    .btn-fail { background: rgba(255,255,255,0.1); color: #ff8a8a; border: 1.5px solid rgba(255,107,107,0.4); flex: 1; }

    .home-title { font-family: "Playfair Display", serif; font-size: 20px; text-align: center; margin: 0.5rem 0 0.3rem; color: white; text-shadow: 0 2px 6px rgba(0,0,0,0.4); }
    .home-sub { font-size: 13px; color: rgba(255,255,255,0.75); text-align: center; margin-bottom: 1rem; }

    .live-scores { display: grid; grid-template-columns: repeat(3,1fr); gap: 8px; margin-bottom: 1rem; }
    .ls-card { border-radius: 12px; padding: 10px 8px; text-align: center; border: 2px solid transparent; background: rgba(255,255,255,0.12); }
    .ls-card.c0 { border-color: var(--c0); } .ls-card.c1 { border-color: var(--c1); } .ls-card.c2 { border-color: var(--c2); }
    .ls-name { font-size: 11px; font-weight: 500; margin-bottom: 2px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; color: white; }
    .ls-pts { font-size: 20px; font-weight: 500; color: white; }
    .ls-fin { font-size: 10px; color: rgba(255,255,255,0.6); margin-top: 2px; }

    .team-pick-btn {
      display: flex; align-items: center; justify-content: space-between;
      width: 100%; padding: 14px 18px; border-radius: 14px; border: 2px solid rgba(255,255,255,0.2);
      font-family: "DM Sans", sans-serif; font-size: 15px; font-weight: 500; cursor: pointer;
      margin-bottom: 10px; background: rgba(255,255,255,0.12); color: white; transition: all 0.15s;
    }
    .team-pick-btn.c0 { border-color: var(--c0); }
    .team-pick-btn.c1 { border-color: var(--c1); }
    .team-pick-btn.c2 { border-color: var(--c2); }
    .team-pick-btn.finished { opacity: 0.45; cursor: default; pointer-events: none; }
    .tpb-cap { font-size: 12px; font-weight: 400; opacity: 0.7; }

    .game-header { display: flex; align-items: center; gap: 10px; margin-bottom: 1rem; }
    .team-pill { display: flex; align-items: center; gap: 6px; padding: 5px 12px; border-radius: 50px; font-size: 13px; font-weight: 500; color: white; background: rgba(255,255,255,0.15); }
    .team-score-inline { margin-left: auto; font-size: 13px; font-weight: 500; color: rgba(255,255,255,0.9); }

    .progress-bar-wrap { background: rgba(255,255,255,0.15); border-radius: 50px; height: 5px; margin-bottom: 5px; overflow: hidden; }
    .progress-bar-fill { height: 100%; border-radius: 50px; transition: width 0.4s ease; }
    .fill0 { background: linear-gradient(90deg, var(--c0), var(--pink-dark)); }
    .fill1 { background: linear-gradient(90deg, var(--c1), #3c3489); }
    .fill2 { background: linear-gradient(90deg, var(--c2), #085041); }
    .progress-label { font-size: 12px; color: rgba(255,255,255,0.6); text-align: right; margin-bottom: 0.8rem; }

    .challenge-card { padding: 1.4rem; margin-bottom: 0.8rem; }
    .challenge-top { display: flex; align-items: center; gap: 8px; margin-bottom: 12px; }
    .cat-badge { font-size: 11px; font-weight: 500; padding: 4px 12px; border-radius: 50px; color: white; }
    .cat-pink { background: rgba(212,83,126,0.5); }
    .cat-purple { background: rgba(127,119,221,0.5); }
    .cat-teal { background: rgba(29,158,117,0.5); }
    .cat-gold { background: rgba(239,159,39,0.5); }
    .cat-blue { background: rgba(55,138,221,0.5); }
    .pts-label { margin-left: auto; font-size: 13px; font-weight: 500; color: #ffd97d; }
    .challenge-text { font-family: "Playfair Display", serif; font-size: clamp(16px,4vw,20px); line-height: 1.55; color: white; margin-bottom: 1.2rem; white-space: pre-line; }

    .timer-idle { text-align: center; }
    .timer-idle p { font-size: 14px; color: rgba(255,255,255,0.8); margin-bottom: 6px; }
    .timer-duration { font-size: 15px; font-weight: 600; color: #ffd97d; margin-bottom: 10px; }
    .timer-display { text-align: center; font-family: "Playfair Display", serif; font-size: 56px; font-weight: 700; letter-spacing: -1px; margin-bottom: 8px; color: white; transition: color 0.3s; }
    .timer-display.urgent { color: #ff6b6b; }
    .timer-bar-wrap { background: rgba(255,255,255,0.15); border-radius: 50px; height: 8px; overflow: hidden; margin-bottom: 12px; }
    .timer-bar-fill { height: 100%; border-radius: 50px; transition: width 0.5s linear, background 0.3s; }
    .action-row { display: flex; gap: 10px; }

    .team-done-wrap { text-align: center; padding: 2rem 1rem; color: white; }
    .team-done-wrap h2 { font-family: "Playfair Display", serif; font-size: 22px; margin-bottom: 6px; }
    .big-score-card { border-radius: var(--radius); padding: 1.5rem; text-align: center; margin-bottom: 1rem; background: rgba(255,255,255,0.12); border: 2px solid rgba(255,255,255,0.2); }
    .big-score-card.c0 { border-color: var(--c0); } .big-score-card.c1 { border-color: var(--c1); } .big-score-card.c2 { border-color: var(--c2); }
    .big-score { font-family: "Playfair Display", serif; font-size: 56px; font-weight: 700; color: white; }
    .finish-time { font-size: 14px; color: rgba(255,255,255,0.7); margin-top: 4px; }

    .trophy { font-size: 44px; text-align: center; margin: 1rem 0 0.3rem; }
    .winner-title { font-family: "Playfair Display", serif; font-size: 24px; font-weight: 700; text-align: center; color: white; margin-bottom: 3px; }
    .winner-sub { font-size: 13px; color: rgba(255,255,255,0.75); text-align: center; margin-bottom: 1rem; }
    .winner-banner { border-radius: var(--radius); padding: 1.1rem; text-align: center; margin-bottom: 1rem; background: rgba(255,255,255,0.12); }
    .winner-banner.c0 { border: 2px solid var(--c0); } .winner-banner.c1 { border: 2px solid var(--c1); } .winner-banner.c2 { border: 2px solid var(--c2); }
    .wb-label { font-size: 12px; font-weight: 500; margin-bottom: 3px; color: rgba(255,255,255,0.8); }
    .wb-name { font-family: "Playfair Display", serif; font-size: 22px; font-weight: 700; color: white; }
    .wb-detail { font-size: 12px; margin-top: 2px; color: rgba(255,255,255,0.7); }
    .final-card { background: rgba(255,255,255,0.12); border-radius: var(--radius); overflow: hidden; margin-bottom: 1.2rem; border: 1px solid rgba(255,255,255,0.2); }
    .final-row { display: flex; align-items: center; padding: 12px 16px; border-bottom: 1px solid rgba(255,255,255,0.1); gap: 10px; }
    .final-row:last-child { border-bottom: none; }
    .rank-circle { width: 28px; height: 28px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 12px; font-weight: 500; flex-shrink: 0; background: rgba(255,255,255,0.2); color: white; }
    .r0 { background: rgba(239,159,39,0.5); } .r1 { background: rgba(255,255,255,0.2); } .r2 { background: rgba(255,120,80,0.4); }
    .fdot { width: 9px; height: 9px; border-radius: 50%; flex-shrink: 0; }
    .final-info { flex: 1; }
    .final-tname { font-size: 14px; font-weight: 500; color: white; }
    .final-meta { font-size: 11px; color: rgba(255,255,255,0.6); }
    .final-pts { font-size: 15px; font-weight: 500; color: white; }

    .music-btn {
      position: fixed; bottom: 20px; right: 16px; z-index: 100;
      width: 44px; height: 44px; border-radius: 50%;
      background: rgba(255,255,255,0.2); border: 1.5px solid rgba(255,255,255,0.4);
      display: flex; align-items: center; justify-content: center;
      cursor: pointer; font-size: 20px; box-shadow: 0 2px 12px rgba(0,0,0,0.2);
    }

    @media(max-width: 400px) { .teams-grid { grid-template-columns: 1fr; } }
  </style>
</head>
<body>

<div class="ribbon">
  <h1>&#128141; Addio al nubilato di Valentina</h1>
  <p>Tre squadre, sfide a tempo &mdash; vince chi fa pi&ugrave; punti!</p>
</div>

<div class="container">

  <div id="setup" class="screen active">
    <div class="setup-intro">
      <h2>Crea le 3 squadre</h2>
      <p>Nome squadra, capitana e partecipanti</p>
    </div>
    <div class="teams-grid">
      <div class="tsc c0">
        <div class="tsc-label"><span class="dot d0"></span>Squadra 1</div>
        <div class="fl">Nome</div><input type="text" id="tn0" placeholder="Le Rose" />
        <div class="fl">Capitana</div><input type="text" id="tc0" placeholder="Nome" />
        <div class="fl">Altre</div><textarea id="tm0" placeholder="Sara&#10;Giulia"></textarea>
      </div>
      <div class="tsc c1">
        <div class="tsc-label"><span class="dot d1"></span>Squadra 2</div>
        <div class="fl">Nome</div><input type="text" id="tn1" placeholder="Le Stelle" />
        <div class="fl">Capitana</div><input type="text" id="tc1" placeholder="Nome" />
        <div class="fl">Altre</div><textarea id="tm1" placeholder="Marta&#10;Lucia"></textarea>
      </div>
      <div class="tsc c2">
        <div class="tsc-label"><span class="dot d2"></span>Squadra 3</div>
        <div class="fl">Nome</div><input type="text" id="tn2" placeholder="Le Cuori" />
        <div class="fl">Capitana</div><input type="text" id="tc2" placeholder="Nome" />
        <div class="fl">Altre</div><textarea id="tm2" placeholder="Anna&#10;Chiara"></textarea>
      </div>
    </div>
    <button class="btn btn-primary" onclick="startGame()">Inizia il gioco &#8594;</button>
  </div>

  <div id="home" class="screen">
    <div class="live-scores" id="live-scores"></div>
    <h2 class="home-title">Seleziona la tua squadra</h2>
    <p class="home-sub">Ogni squadra gioca dal proprio telefono</p>
    <div id="team-pick-list"></div>
  </div>

  <div id="game" class="screen">
    <div class="game-header">
      <div class="team-pill" id="g-pill"></div>
      <div class="team-score-inline" id="g-score"></div>
    </div>
    <div class="progress-bar-wrap"><div class="progress-bar-fill" id="g-prog-fill"></div></div>
    <div class="progress-label" id="g-prog-label"></div>
    <div class="challenge-card card">
      <div class="challenge-top">
        <span class="cat-badge" id="g-cat"></span>
        <span class="pts-label" id="g-pts"></span>
      </div>
      <p class="challenge-text" id="g-text"></p>
      <div id="timer-idle" class="timer-idle">
        <p>Pronta? Premi per accettare la sfida e far partire il timer!</p>
        <p class="timer-duration" id="timer-duration-label"></p>
        <button class="btn btn-teal" onclick="acceptChallenge()">&#9203; Accetta e inizia il timer</button>
      </div>
      <div id="timer-running" style="display:none">
        <div class="timer-display" id="timer-display">0:00</div>
        <div class="timer-bar-wrap"><div class="timer-bar-fill" id="timer-bar"></div></div>
        <div class="action-row">
          <button class="btn btn-done" onclick="completeChallenge()">&#10003; Completata!</button>
          <button class="btn btn-fail" onclick="failChallenge()">&#10007; Non riuscita</button>
        </div>
      </div>
    </div>
    <div style="display:flex;gap:10px;margin-top:0.5rem;">
      <button class="btn btn-skip" onclick="prevChallenge()">&#8592; Indietro</button>
      <button class="btn btn-skip" onclick="skipChallenge()">&#8617; Salta</button>
    </div>
  </div>

  <div id="teamdone" class="screen">
    <div class="team-done-wrap">
      <div style="font-size:40px;margin-bottom:8px">&#127882;</div>
      <h2>Sfide completate!</h2>
      <p style="color:rgba(255,255,255,0.8);margin-bottom:1.5rem">Hai finito tutte le sfide!</p>
      <div class="big-score-card" id="td-card">
        <div class="big-score" id="td-score"></div>
        <div class="finish-time" id="td-time"></div>
      </div>
      <button class="btn btn-primary" onclick="goHome()">&#8592; Torna alla home</button>
    </div>
  </div>

  <div id="final" class="screen">
    <div class="trophy">&#127942;</div>
    <h2 class="winner-title">Gioco finito!</h2>
    <p class="winner-sub">Classifica finale</p>
    <div id="f-winner-banner"></div>
    <div class="final-card" id="f-scores"></div>
    <button class="btn btn-primary" onclick="resetAll()">Gioca ancora!</button>
  </div>

</div>

<div class="music-btn" id="music-btn" onclick="toggleMusic()">&#127925;</div>
<audio id="bg-music" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<script>
var COLORS = ["c0","c1","c2"];
var CDOTS = ["#d4537e","#7f77dd","#1d9e75"];
var musicPlaying = false;

var challenges = [
  {text:"Fai un imitazione della Vale davanti al gruppo!", cat:"Sposa", catCls:"cat-pink", pts:100, time:300},
  {text:"Chiedete a due ragazzi di autografare il braccio di due partecipanti del gruppo", cat:"Social", catCls:"cat-purple", pts:150, time:600},
  {text:"Raggruppa tre sconosciuti e racconta loro un ricordo divertente con Valentina", cat:"Social", catCls:"cat-purple", pts:200, time:600},
  {text:"Ballate con un twerk folle per 1 minuto e 30 secondi in un posto scelto dalle squadre avversarie!", cat:"Coraggio", catCls:"cat-teal", pts:150, time:120},
  {text:"Chiama un amico single di Luca e chiedigli se puoi sederti accanto a lui in chiesa perche hai il trauma dell abbandono", cat:"Coraggio", catCls:"cat-teal", pts:200, time:300},
  {text:"La sposa sceglie una canzone: tutto il gruppo deve cantare il ritornello a squarciagola!", cat:"Sposa", catCls:"cat-pink", pts:250, time:120},
  {text:"Due componenti del gruppo fingono di essere influencer e si scattano foto in pose assurde per 5 minuti", cat:"Divertimento", catCls:"cat-gold", pts:150, time:300},
  {text:"Convinci tre sconosciuti a dedicare un augurio POETICO alla Vale", cat:"Social", catCls:"cat-purple", pts:200, time:600},
  {text:"Trova qualcosa di blu e usalo come accessorio per 5 minuti", cat:"Creativita", catCls:"cat-blue", pts:150, time:300},
  {text:"Fai un selfie con tre ragazzi con le facce piu brutte e buffe possibili e taggali su Instagram", cat:"Social", catCls:"cat-purple", pts:200, time:600},
  {text:"Abbracciate tre sconosciuti!", cat:"Coraggio", catCls:"cat-teal", pts:200, time:300},
  {text:"Scorri la lista contatti WhatsApp e chiama il primo su cui punti il dito a caso. Parla in cinese per 2 minuti senza che riattacchi", cat:"Coraggio", catCls:"cat-teal", pts:250, time:120},
  {text:"Simulate una lezione di Zumba insieme a tutto il gruppo per 3 minuti!", cat:"Divertimento", catCls:"cat-gold", pts:200, time:180},
  {text:"Quiz sulla Vale\n1) A quanti anni ha dato il primo bacio?\n2) Qual e il crush piu brutto che ha avuto?\n3) Qual e il desiderio piu perverso della Vale?", cat:"Quiz Vale", catCls:"cat-pink", pts:150, time:120},
  {text:"Chiedi a tre ragazzi di posare con la Vale per una foto in pose da bodybuilder", cat:"Social", catCls:"cat-purple", pts:300, time:600},
  {text:"Chiama la mamma o il papa di una del gruppo e digli che al momento non puo parlare... anche se hai chiamato tu!", cat:"Coraggio", catCls:"cat-teal", pts:200, time:180},
  {text:"Tutto il gruppo simula l urlo della Vale all unisono, piu fedele possibile!", cat:"Sposa", catCls:"cat-pink", pts:200, time:60},
  {text:"Cerca su Instagram un vecchio crush della Vale, mandagli un selfie del gruppo con la Vale in DM e scrivigli: La Vale si sposa, grazie per aver partecipato!", cat:"Sposa", catCls:"cat-pink", pts:100, time:120},
  {text:"Quiz su Luca\n1) Qual e il nome della sua prima fidanzata?\n2) Qual e la cosa che piu lo fa arrabbiare della Vale?\n3) Quanti tatuaggi ha?", cat:"Quiz Luca", catCls:"cat-blue", pts:150, time:120},
  {text:"Chiedete al DJ di fare un augurio alla sposa al microfono!", cat:"Missione Epica", catCls:"cat-gold", pts:500, time:600}
];

function shuffle(a){ return a.slice().sort(function(){ return Math.random()-0.5; }); }
function showScreen(id){ var all=document.querySelectorAll(".screen"); for(var i=0;i<all.length;i++) all[i].classList.remove("active"); document.getElementById(id).classList.add("active"); }

function toggleMusic(){
  var audio=document.getElementById("bg-music");
  var btn=document.getElementById("music-btn");
  if(musicPlaying){ audio.pause(); btn.style.opacity="0.5"; musicPlaying=false; }
  else { audio.play().catch(function(){}); btn.style.opacity="1"; musicPlaying=true; }
}
document.addEventListener("click", function startM(){
  if(!musicPlaying){ document.getElementById("bg-music").play().then(function(){ musicPlaying=true; }).catch(function(){}); }
  document.removeEventListener("click", startM);
}, {once:true});

var teams=[], activeTeam=null, timerInterval=null, timerLeft=0, currentChallengeTime=120, gameStartTime=null;

function startGame(){
  teams=[];
  for(var i=0;i<3;i++){
    var name=document.getElementById("tn"+i).value.trim()||"Squadra "+(i+1);
    var cap=document.getElementById("tc"+i).value.trim()||"Capitana";
    teams.push({name:name,cap:cap,cls:COLORS[i],score:0,shuffled:shuffle(challenges),idx:0,finishTime:null});
  }
  gameStartTime=Date.now();
  showScreen("home"); renderHome();
}

function renderHome(){
  var ls="";
  for(var i=0;i<teams.length;i++){
    var t=teams[i];
    var fin=t.finishTime?"Finita":t.idx>0?t.idx+"/"+t.shuffled.length:"Non iniziata";
    ls+="<div class='ls-card "+t.cls+"'><div class='ls-name'>"+t.name+"</div><div class='ls-pts'>"+t.score+"</div><div class='ls-fin'>"+fin+"</div></div>";
  }
  document.getElementById("live-scores").innerHTML=ls;
  var pl="";
  for(var i=0;i<teams.length;i++){
    var t=teams[i];
    var done=t.finishTime!==null;
    var right=done?"Completata":t.idx>0?t.idx+"/"+t.shuffled.length+" sfide":"Inizia";
    pl+="<button class='team-pick-btn "+t.cls+(done?" finished":"")+"' onclick='selectTeam("+i+")'>"
      +"<div><div style='font-size:16px;font-weight:500'>"+t.name+"</div><div class='tpb-cap'>cap. "+t.cap+"</div></div>"
      +"<span style='font-size:13px'>"+right+"</span></button>";
  }
  document.getElementById("team-pick-list").innerHTML=pl;
  var allDone=true; for(var i=0;i<teams.length;i++) if(!teams[i].finishTime) allDone=false;
  if(allDone) showFinal();
}

function selectTeam(i){ activeTeam=i; clearTimer(); renderChallenge(); showScreen("game"); }
function goHome(){ clearTimer(); activeTeam=null; renderHome(); showScreen("home"); }

function renderChallenge(){
  var t=teams[activeTeam];
  if(t.idx>=t.shuffled.length){ teamFinished(); return; }
  var c=t.shuffled[t.idx];
  var pct=Math.round((t.idx/t.shuffled.length)*100);
  var pill=document.getElementById("g-pill");
  pill.className="team-pill";
  pill.innerHTML="<span class='dot d"+activeTeam+"'></span>"+t.name;
  document.getElementById("g-score").textContent=t.score+" pt";
  var fill=document.getElementById("g-prog-fill");
  fill.className="progress-bar-fill fill"+activeTeam;
  fill.style.width=pct+"%";
  document.getElementById("g-prog-label").textContent="Sfida "+(t.idx+1)+" di "+t.shuffled.length;
  document.getElementById("g-cat").textContent=c.cat;
  document.getElementById("g-cat").className="cat-badge "+c.catCls;
  document.getElementById("g-pts").textContent="* "+c.pts+" punti";
  document.getElementById("g-text").textContent=c.text;
  clearTimer();
  document.getElementById("timer-idle").style.display="block";
  document.getElementById("timer-running").style.display="none";
  var m=Math.floor(c.time/60), s=c.time%60;
  document.getElementById("timer-duration-label").textContent="Tempo: "+(s>0?m+"m "+s+"s":m+" min");
}

function acceptChallenge(){
  var t=teams[activeTeam];
  currentChallengeTime=t.shuffled[t.idx].time||120;
  document.getElementById("timer-idle").style.display="none";
  document.getElementById("timer-running").style.display="block";
  timerLeft=currentChallengeTime;
  updateTimerUI();
  timerInterval=setInterval(function(){
    timerLeft--; updateTimerUI();
    if(timerLeft<=0){ clearTimer(); failChallenge(); }
  },1000);
}

function updateTimerUI(){
  var m=Math.floor(timerLeft/60), s=timerLeft%60;
  var disp=document.getElementById("timer-display");
  disp.textContent=m+":"+(s<10?"0":"")+s;
  disp.className="timer-display"+(timerLeft<=15?" urgent":"");
  var pct=(timerLeft/currentChallengeTime)*100;
  var bar=document.getElementById("timer-bar");
  bar.style.width=pct+"%";
  bar.style.background=timerLeft<=15?"#e24b4a":timerLeft<=(currentChallengeTime*0.25)?"#ef9f27":"#1d9e75";
}

function clearTimer(){ if(timerInterval){ clearInterval(timerInterval); timerInterval=null; } }

function completeChallenge(){ clearTimer(); var t=teams[activeTeam]; t.score+=t.shuffled[t.idx].pts; t.idx++; renderChallenge(); }
function failChallenge(){ clearTimer(); teams[activeTeam].idx++; renderChallenge(); }
function skipChallenge(){ clearTimer(); teams[activeTeam].idx++; renderChallenge(); }
function prevChallenge(){ clearTimer(); var t=teams[activeTeam]; if(t.idx>0) t.idx--; renderChallenge(); }

function teamFinished(){
  clearTimer();
  var t=teams[activeTeam];
  t.finishTime=Date.now();
  var elapsed=Math.round((t.finishTime-gameStartTime)/1000);
  var m=Math.floor(elapsed/60), s=elapsed%60;
  document.getElementById("td-card").className="big-score-card "+t.cls;
  document.getElementById("td-score").textContent=t.score+" pt";
  document.getElementById("td-time").textContent="Tempo totale: "+m+"m "+s+"s";
  showScreen("teamdone");
  var allDone=true; for(var i=0;i<teams.length;i++) if(!teams[i].finishTime) allDone=false;
  if(allDone) setTimeout(function(){ showFinal(); },1800);
}

function showFinal(){
  showScreen("final");
  var ranked=[];
  for(var i=0;i<teams.length;i++) ranked.push({t:teams[i],i:i});
  ranked.sort(function(a,b){
    if(b.t.score!==a.t.score) return b.t.score-a.t.score;
    if(a.t.finishTime&&b.t.finishTime) return a.t.finishTime-b.t.finishTime;
    if(a.t.finishTime) return -1; if(b.t.finishTime) return 1; return 0;
  });
  var w=ranked[0].t, wi=ranked[0].i;
  document.getElementById("f-winner-banner").innerHTML=
    "<div class='winner-banner "+COLORS[wi]+"'>"
    +"<div class='wb-label'>Squadra vincitrice!</div>"
    +"<div class='wb-name'>"+w.name+"</div>"
    +"<div class='wb-detail'>cap. "+w.cap+" - "+w.score+" punti</div></div>";
  var rcls=["r0","r1","r2"], html="";
  for(var pos=0;pos<ranked.length;pos++){
    var t=ranked[pos].t, ri=ranked[pos].i;
    var elapsed=t.finishTime?Math.round((t.finishTime-gameStartTime)/1000):null;
    var timeStr=elapsed?Math.floor(elapsed/60)+"m "+(elapsed%60)+"s":"---";
    html+="<div class='final-row'>"
      +"<div class='rank-circle "+rcls[pos]+"'>"+(pos+1)+"</div>"
      +"<div class='fdot' style='background:"+CDOTS[ri]+"'></div>"
      +"<div class='final-info'><div class='final-tname'>"+t.name+"</div><div class='final-meta'>cap. "+t.cap+" - "+timeStr+"</div></div>"
      +"<span class='final-pts'>"+t.score+" pt</span></div>";
  }
  document.getElementById("f-scores").innerHTML=html;
}

function resetAll(){
  var ids=["tn0","tn1","tn2","tc0","tc1","tc2","tm0","tm1","tm2"];
  for(var i=0;i<ids.length;i++) document.getElementById(ids[i]).value="";
  showScreen("setup");
}
</script>
</body>
</html>
