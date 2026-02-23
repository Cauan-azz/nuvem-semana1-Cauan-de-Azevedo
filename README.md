# nuvem-semana1-Cauan-de-Azevedo
<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Semana 1 - Hello Cloud</title>
<link rel="stylesheet" href="style.css" />
</head>
<body>
<main class="container">
<h1>Hello Cloud (Semana 1)</h1>
<p>Aluno(a): <span class="muted">[Cauan de Azevedo]</span></p>
<section class="card">
<h2>Checklist</h2>
<ul>
<li>Repositorio criado no GitHub</li>
<li>Arquivos: index.html, style.css, script.js</li>
<li>GitHub Pages ativado</li>
</ul>
</section>
<section class="card">
<h2>Status</h2>
<p id="status" class="muted">Carregando...</p>
<p class="muted">Horario local: <span id="clock">--:--</span></p>
</section>
<section class="card">
<h2>(Opcional) Teste de API publica</h2>
<p class="muted">Se quiser, clique no botao para testar fetch.</p>
<button id="btn">Testar API</button>
<pre id="api" class="code"></pre>
</section>
<footer class="muted">
Publicado com GitHub Pages.
</footer>
</main>
<script src="script.js"></script>
</body>
</html>
C2) Criar style.css
Clique em Add file -> Create new file. Nome: style.css. Cole e comite.
:root {
font-family: system-ui, Arial, sans-serif;
}
body {
margin: 0;
background: #f6f7fb;
color: #111;
}
.container {
max-width: 900px;
margin: 0 auto;
padding: 24px;
}
h1 {
margin: 0 0 8px 0;

Página 3

}
.card {
background: #fff;
border: 1px solid #e6e6e6;
border-radius: 12px;
padding: 16px;
margin: 14px 0;
}
.muted {
color: #555;
}
button {
padding: 10px 12px;
border-radius: 10px;
border: 1px solid #ddd;
cursor: pointer;
background: #fff;
}
button:hover {
background: #f0f0f0;
}
.code {
background: #0f172a;
color: #e2e8f0;
padding: 12px;
border-radius: 10px;
overflow-x: auto;
}
C3) Criar script.js
Clique em Add file -> Create new file. Nome: script.js. Cole e comite.
const statusEl = document.getElementById("status");
const clockEl = document.getElementById("clock");
const btn = document.getElementById("btn");
const apiEl = document.getElementById("api");
function tick() {
const now = new Date();
clockEl.textContent = now.toLocaleTimeString("pt-BR");
}
setInterval(tick, 1000);
tick();
statusEl.textContent = "Site carregado com sucesso. (Sem Node, sem instalacao.)";
btn.addEventListener("click", async () => {
apiEl.textContent = "Consultando API...";
try {
const resp = await fetch("https://api.agify.io?name=rafael");
if (!resp.ok) throw new Error("HTTP " + resp.status);
const data = await resp.json();
apiEl.textContent = JSON.stringify(data, null, 2);
} catch (err) {
apiEl.textContent = "Erro no fetch: " + err.message;
}
