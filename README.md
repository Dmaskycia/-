<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Calculadora de Atrasos 0,5 %</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    * {
      box-sizing: border-box;
    }

    html, body {
      height: 100%;
      margin: 0;
      padding: 0;
      font-family: "Segoe UI", Roboto, sans-serif;
      background: #f4f4f4;
      color: #333;
    }

    body {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }

    .container {
      background: #ffffff;
      max-width: 500px;
      width: 100%;
      padding: 25px 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      border-left: 10px solid #cc0000;
      box-sizing: border-box;
      margin: 20px;
    }

    h1 {
      color: #cc0000;
      font-size: 20px;
      margin-bottom: 15px;
    }

    p {
      font-size: 14px;
      margin-bottom: 15px;
    }

    label {
      font-weight: bold;
      display: block;
      margin-bottom: 5px;
    }

    input {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 16px;
      margin-bottom: 15px;
    }

    button {
      background-color: #cc0000;
      color: white;
      border: none;
      padding: 12px;
      width: 100%;
      font-size: 16px;
      border-radius: 6px;
      cursor: pointer;
    }

    button:hover {
      background-color: #a00000;
    }

    .resultado {
      background: #fdf3f3;
      border-left: 5px solid #cc0000;
      margin-top: 25px;
      padding: 15px 20px;
      border-radius: 8px;
      font-size: 15px;
    }

    .resaltado {
      font-size: 1.3em;
      font-weight: bold;
      color: #cc0000;
    }

    .footer {
      text-align: center;
      margin: 15px auto 20px auto;
      font-size: 12px;
      color: #777;
      width: 100%;
      max-width: 500px;
      padding: 0 15px;
    }

    @media (max-height: 650px) {
      body {
        align-items: flex-start;
        padding-top: 10px;
      }
    }

    @media (max-width: 480px) {
      .container {
        margin: 10px;
        padding: 20px 15px;
      }

      h1 {
        font-size: 18px;
      }

      .resaltado {
        font-size: 1.1em;
      }
    }
  </style>
</head>
<body>

<div class="container">
  <h1>🧮 Calculadora de Atrasos 0,5 % desde 1 enero 2024</h1>
  <p>Introduce el importe bruto mensual completo de tu nómina (incluye base, destino, específico...)<br><strong>SIMULACRO ORIENTATIVO</strong></p>

  <label for="nomina">Nómina mensual bruta (€):</label>
  <input type="number" id="nomina" placeholder="Ejemplo: 2150.00" step="0.01">

  <button onclick="calcular()">Calcular atrasos</button>

  <div id="resultado" class="resultado" style="display:none;"></div>
</div>

<div class="footer">
  CCOO FSC Región de Murcia · Elaboración propia
</div>

<script>
function calcular() {
  const nomina = parseFloat(document.getElementById('nomina').value);
  if (isNaN(nomina) || nomina <= 0) {
    alert("Introduce una cifra válida.");
    return;
  }

  const subidaMensual = nomina * 0.005;

  const hoy = new Date();
  const añoActual = hoy.getFullYear();
  const mesActual = hoy.getMonth() + 1;

  const meses2024 = 12;
  const meses2025 = (añoActual === 2025) ? mesActual : (añoActual > 2025 ? 12 : 0);
  const totalMensualidades = meses2024 + meses2025;

  let pagasExtras = 2; // junio y diciembre 2024
  if (añoActual > 2025 || (añoActual === 2025 && mesActual >= 6)) {
    pagasExtras += 1;
  }

  const atrasosMensuales = subidaMensual * totalMensualidades;
  const atrasosExtras = subidaMensual * pagasExtras;
  const atrasosTotales = atrasosMensuales + atrasosExtras;

  const resultado = document.getElementById("resultado");
  resultado.style.display = "block";
  resultado.innerHTML = `
    <strong>📈 Subida mensual (0,5 %):</strong> ${subidaMensual.toFixed(2)} €<br><br>
    <strong>🗓️ Meses con atrasos:</strong> ${totalMensualidades} → <strong>${atrasosMensuales.toFixed(2)} €</strong><br>
    <strong>🎁 Pagas extra incluidas:</strong> ${pagasExtras} → <strong>${atrasosExtras.toFixed(2)} €</strong><br><br>
    <span class="resaltado">💰 Total atrasos a percibir: ${atrasosTotales.toFixed(2)} €</span>
  `;
}
</script>

</body>
</html>
