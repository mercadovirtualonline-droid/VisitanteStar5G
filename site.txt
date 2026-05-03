VisitanteStar5G/
│
├── index.html
├── style.css
├── script.js
└── assets/
    └── background.jpg
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
    font-size:28px;
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
    background:gold;
    transition: width 1s;
}

button {
    padding:12px 20px;
    margin:10px;
    border:none;
    border-radius:8px;
    font-size:16px;
    cursor:pointer;
}

.insta {
    background:#E1306C;
    color:white;
}

.wifi {
    background:gold;
    color:black;
}

.wifi:disabled {
    background:gray;
}

.footer {
    margin-top:20px;
    font-size:12px;
    opacity:0.7;
}
let tempo = 5;
let progresso = 0;

const contador = document.getElementById("contador");
const barra = document.getElementById("progress");
const botaoWifi = document.getElementById("btnWifi");

function abrirInstagram() {
    window.open("https://www.instagram.com/star.festaseeventos", "_blank");

    iniciarContagem();
}

function iniciarContagem() {
    const intervalo = setInterval(() => {

        tempo--;
        progresso += 20;

        barra.style.width = progresso + "%";
        contador.innerText = "Aguarde " + tempo + "s...";

        if (tempo <= 0) {
            clearInterval(intervalo);

            contador.innerText = "Acesso liberado!";
            botaoWifi.disabled = false;
            botaoWifi.innerText = "✔ Liberar Wi-Fi";
        }

    }, 1000);
}

function liberarWifi() {
    // ESSENCIAL PARA INTELBRAS
    window.location.href = "http://login.intelbras/ok.html";
}
