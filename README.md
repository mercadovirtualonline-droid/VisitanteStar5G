VisitanteStar5G/
│
├── index.html
├── style.css
├── script.js
└── assets/
    └── background.jpg


assets/background.jpg
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Star Festas Wi-Fi</title>

<link rel="stylesheet" href="style.css">
</head>

<body>

<div class="overlay">

    <div class="logo">⭐ Star Festas & Eventos</div>

    <div class="sub">
        Siga nosso Instagram para acessar o Wi-Fi
    </div>

    <div class="progress-container">
        <div id="progress" class="progress"></div>
    </div>

    <p id="contador">Preparando acesso...</p>

    <button class="insta" onclick="abrirInstagram()">
        📲 Abrir Instagram
    </button>

    <button id="btnWifi" class="wifi" disabled onclick="liberarWifi()">
        🔒 Liberar Wi-Fi
    </button>

    <div class="footer">
        Conecte • Curta • Compartilhe
    </div>

</div>

<script src="script.js"></script>

</body>
</html>
body {
    margin:0;
    font-family: 'Segoe UI', sans-serif;
    color:white;
    text-align:center;

    background: url('assets/background.jpg') no-repeat center center/cover;
}

.overlay {
    backdrop-filter: blur(6px);
    background: rgba(0,0,0,0.6);
    height:100vh;

    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    padding:20px;
}

.logo {
    font-size:32px;
    font-weight:bold;
    margin-bottom:10px;

    text-shadow: 0 0 10px gold;
    animation: glow 2s infinite alternate;
}

@keyframes glow {
    from { text-shadow: 0 0 5px gold; }
    to { text-shadow: 0 0 20px #FFD700; }
}

.sub {
    margin-bottom:20px;
    font-size:16px;
    opacity:0.9;
}

.progress-container {
    width:90%;
    max-width:320px;
    height:12px;
    background:#222;
    border-radius:20px;
    overflow:hidden;
    margin-bottom:15px;
}

.progress {
    height:100%;
    width:0%;
    background: linear-gradient(90deg,#833AB4,#FD1D1D,#FCAF45);
    transition: width 0.5s;
}

button {
    width:90%;
    max-width:320px;
    padding:15px;
    border:none;
    border-radius:12px;
    font-size:16px;
    font-weight:bold;
    margin-top:10px;
}

.insta {
    background: linear-gradient(45deg,#833AB4,#FD1D1D,#FCAF45);
}

.wifi {
    background: gray;
}

.footer {
    margin-top:20px;
    font-size:12px;
    opacity:0.6;
}
let tempo = 8;
let total = 8;

let contador = document.getElementById("contador");
let progress = document.getElementById("progress");
let btnWifi = document.getElementById("btnWifi");

let linkInsta = "https://www.instagram.com/star.festaseeventos";

// abrir Instagram
function abrirInstagram(){
    window.open(linkInsta, "_blank");
}

// liberar Wi-Fi (compatibilidade geral)
function liberarWifi(){
    window.location.href = "http://1.1.1.1";

    setTimeout(()=>{
        window.location.href = "http://192.168.0.1";
    },2000);

    setTimeout(()=>{
        window.location.href = "http://192.168.1.1";
    },4000);
}

// tentativa automática (pode ser bloqueada)
setTimeout(()=>{
    window.open(linkInsta, "_blank");
},3000);

// contador + barra
let intervalo = setInterval(()=>{

    tempo--;

    let progresso = ((total - tempo) / total) * 100;
    progress.style.width = progresso + "%";

    contador.innerHTML = "Aguarde " + tempo + " segundos...";

    if(tempo <= 0){
        clearInterval(intervalo);

        contador.innerHTML = "✅ Agora você pode liberar o Wi-Fi";

        btnWifi.disabled = false;
        btnWifi.style.background = "#00c853";
    }

},1000);
<img width="720" height="1600" alt="Screenshot_20260501-100312" src="https://github.com/user-attachments/assets/0189a60d-b961-4724-8a62-1488a446f480" />
