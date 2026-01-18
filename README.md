<!DOCTYPE html>
<html lang="hu">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Saját Magyar Nemzetünk Közössége</title>
<style>
body{margin:0;font-family:Arial,sans-serif;background:#f2f2f2;color:#000;}
header{background:#1e1e1e;color:white;padding:20px;text-align:center;}
nav{padding:10px;text-align:center;background:#333;position:sticky;top:0;z-index:100;}
nav button{
  margin:0 4px;
  padding:6px 10px;
  background:#4752c4;
  color:white;
  border:none;
  border-radius:5px;
  cursor:pointer;
  font-size:14px;
}
nav button:hover{background:#3b41a0;}
section{
  position:absolute;
  top:120px; left:0; right:0;
  opacity:0;
  visibility:hidden;
  transition:opacity 0.4s ease, visibility 0.4s;
  padding:20px;
  max-width:900px;
  margin:auto;
}
section.active{
  opacity:1;
  visibility:visible;
}
.card{
  background:white;
  padding:15px;
  border-radius:10px;
  margin-bottom:20px;
}
button.main-btn{
  padding:6px 12px;
  font-size:14px;
  background:#5865F2;
  color:white;
  border:none;
  border-radius:5px;
  cursor:pointer;
  transition: background 0.3s;
  margin-top:10px;
}
button.main-btn:hover{background:#4752c4;}
input,textarea{width:100%;padding:10px;margin:6px 0;}
.termekek-container{display:flex;gap:15px;flex-wrap:wrap;}
.termek{flex:1;min-width:250px;border:1px solid #ddd;border-radius:10px;padding:15px;}
.termek ul{font-size:14px;}
.termek p, .termek h3{margin:5px 0;}
footer{background:#1e1e1e;color:white;text-align:center;padding:20px;margin-top:100px;}
</style>
</head>
<body>

<header>
<h1>Saját Magyar Nemzetünk Közössége</h1>
<p>Magyar közösség • Discord • Összetartás 🇭🇺</p>
</header>

<nav>
<button onclick="showSection('fo')">Főoldal</button>
<button onclick="showSection('tulaj')">Tulajdonosok</button>
<button onclick="showSection('rolunk')">Rólunk</button>
<button onclick="showSection('szabalyozat')">Szabályzat</button>
<button onclick="showSection('termekek')">Termékeink</button>
<button onclick="showSection('velemenyek')">Vélemények</button>
<button onclick="showSection('egyebek')">Egyebek</button>
<button onclick="showSection('csatlakozas')">Csatlakozás</button>
</nav>

<!-- FŐOLDAL -->
<section id="fo" class="card active">
<h2>Üdvözlünk a Saját Magyar Nemzetünk Közösségében!</h2>
<p>Ez a közösség magyar fiataloknak szól, ahol játszhatunk, beszélgethetünk és normális hangulat van.</p>
</section>

<!-- Tulajdonosok -->
<section id="tulaj" class="card">
<h2>👑 Tulajdonosok</h2>
<p><b>Alapító / fő irányítás:</b> Beni</p>
<p><b>Tulaj / Fejlesztő a szerver:</b> Áron</p>
<p><b>Admin / Közösség:</b> Bence</p>
</section>

<!-- Rólunk -->
<section id="rolunk" class="card">
<h2>📖 Rólunk</h2>
<p>A Saját Magyar Nemzetünk Közössége egy összetartó magyar Discord közösség, ahol tisztelet, jó hangulat és baráti beszélgetések vannak. Célunk, hogy minden tag jól érezze magát, és biztonságos közegben lehessen része a közösségnek.</p>
</section>

<!-- Szabályzat -->
<section id="szabalyozat" class="card">
<h2>📜 Szabályzat</h2>
<ul>
<li>Tisztelet minden tag felé</li>
<li>Spam és reklám tilos</li>
<li>Kamu fiókok tiltva</li>
<li>Rasszista vagy sértő tartalom = tiltás</li>
<li>Admin döntése végleges</li>
</ul>
</section>

<!-- Termékeink -->
<section id="termekek" class="card">
<h2>🛒 Termékeink</h2>
<div class="termekek-container">
  <div class="termek">
    <img src="matrica.png" alt="SMNK matrica">
    <h3>🇭🇺 Saját Magyar Nemzetünk – Matrica</h3>
    <p>Prémium kinézetű matrica a közösséghez. Laptopra, telefonra, füzetre vagy bárhová.</p>
    <ul>
      <li>✔ Magyar közösségi dizájn</li>
      <li>✔ Tartós matrica</li>
      <li>✔ Limitált darab</li>
    </ul>
    <p><b>Tulaj / Fejlesztő a szerver:</b> Áron</p>
    <button class="main-btn" onclick="window.open('https://discord.gg/ppdCdak8X')">Vásárlás / Discord</button>
  </div>
</div>
</section>

<!-- Vélemények -->
<section id="velemenyek" class="card">
<h2>⭐ Vélemények</h2>
<input id="name" placeholder="Neved">
<textarea id="msg" placeholder="Írd ide a véleményed"></textarea>
<button class="main-btn" onclick="sendMsg()">Küldés</button>
<div id="msgs"></div>
</section>

<!-- Egyebek -->
<section id="egyebek" class="card">
<h2>ℹ️ Egyebek</h2>
<p>A közösség folyamatosan fejlődik. Eventek, rangok, újdonságok várhatók. Kövess minket a Discordon további infókért!</p>
</section>

<!-- Csatlakozás -->
<section id="csatlakozas" class="card">
<h2>🤝 Csatlakozás a Discordra</h2>
<p>Csatlakozz a közösséghez, és légy részese a magyar Discord közösségnek!</p>
<button class="main-btn" onclick="window.open('https://discord.gg/ppdCdak8X')">Discordhoz csatlakozás</button>
</section>

<footer>
<p>© Saját Magyar Nemzetünk Közössége</p>
</footer>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.2/firebase-app.js";
import { getDatabase, ref, push, onChildAdded } from "https://www.gstatic.com/firebasejs/9.22.2/firebase-database.js";

const firebaseConfig = {
  apiKey: "IDE_A_TE_ADATOD",
  authDomain: "IDE_A_TE_ADATOD",
  databaseURL: "IDE_A_TE_ADATOD",
  projectId: "IDE_A_TE_ADATOD",
  storageBucket: "IDE_A_TE_ADATOD",
  messagingSenderId: "IDE_A_TE_ADATOD",
  appId: "IDE_A_TE_ADATOD"
};

const app = initializeApp(firebaseConfig);
const db = getDatabase(app);
const msgsRef = ref(db, "messages");

function sendMsg(){
  const name = document.getElementById("name").value;
  const msg = document.getElementById("msg").value;
  if(name && msg){
    push(msgsRef, { name, msg });
    document.getElementById("name").value = "";
    document.getElementById("msg").value = "";
  }
}

onChildAdded(msgsRef, (data) => {
  const msgsDiv = document.getElementById("msgs");
  const item = document.createElement("div");
  item.textContent = data.val().name + ": " + data.val().msg;
  msgsDiv.appendChild(item);
});

// SPA funkció: absolute + opacity
function showSection(id){
  const sections = document.querySelectorAll('section');
  sections.forEach(s => s.classList.remove('active'));
  const sec = document.getElementById(id);
  if(sec) sec.classList.add('active');
}
</script>

</body>
</html>