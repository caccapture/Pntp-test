<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>PNTP Analyzer</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 400px;
      margin: 100px auto;
      background: white;
      padding: 2rem;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      border-radius: 8px;
    }
    h2 {
      text-align: center;
      color: #007BFF;
    }
    input[type="text"],
    input[type="password"],
    input[type="url"] {
      width: 100%;
      padding: 0.8rem;
      margin: 1rem 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      width: 100%;
      padding: 0.8rem;
      background: #007BFF;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background: #0056b3;
    }
    .hidden {
      display: none;
    }
    .result {
      margin-top: 1rem;
      background: #e9f5ff;
      padding: 1rem;
      border-left: 4px solid #007BFF;
      border-radius: 4px;
    }
  </style>
</head>
<body>

<div class="container" id="login-page">
  <h2>Login</h2>
  <input type="text" id="username" placeholder="Usuário" />
  <input type="password" id="password" placeholder="Senha" />
  <button onclick="login()">Entrar</button>
</div>

<div class="container hidden" id="analyzer-page">
  <h2>Analisar Site</h2>
  <input type="url" id="site-url" placeholder="Cole o link do site aqui" />
  <button onclick="analisar()">Analisar</button>
  <div class="result hidden" id="resultado">
    <strong>Resultado:</strong><br>
    Conformidade PNTP: <span id="percentual">...</span><br>
    - Item 1.1 ✅<br>
    - Item 1.2 ✅<br>
    - Item 1.3 ❌<br>
    - Item 2.1 ❌<br>
    - Item 2.3 ✅
  </div>
</div>

<script>
  function login() {
    const usuario = document.getElementById("username").value;
    const senha = document.getElementById("password").value;

    // Validação simples (ex: admin / 123)
    if (usuario === "admin" && senha === "123") {
      document.getElementById("login-page").classList.add("hidden");
      document.getElementById("analyzer-page").classList.remove("hidden");
    } else {
      alert("Usuário ou senha inválidos.");
    }
  }

  function analisar() {
    const url = document.getElementById("site-url").value;
    if (!url || !url.startsWith("http")) {
      alert("Por favor, insira uma URL válida.");
      return;
    }

    // Simulação de análise
    const resultado = document.getElementById("resultado");
    const percentual = Math.floor(Math.random() * 40 + 60); // entre 60 e 100
    document.getElementById("percentual").innerText = percentual + "%";
    resultado.classList.remove("hidden");
  }
</script>

</body>
</html>
