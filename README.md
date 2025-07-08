<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Calculadora de Atrasos 0,5â€¯%</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: "Segoe UI", Roboto, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 20px;
      color: #333;
    }

    .container {
      background: #fff;
      max-width: 500px;
      margin: auto;
      padding: 30px 25px;
      border-radius: 10px;
      box-shadow: 0 0 12px rgba(0, 0, 0, 0.1);
      border-left: 10px solid #cc0000;
    }

    h1 {
      color: #cc0000;
      font-size: 24px;
      margin-bottom: 15px;
    }

    p {
      font-size: 15px;
      margin-bottom: 20px;
    }

    label {
      font-weight: bold;
      display: block;
      margin-bottom: 6px;
      margin-top: 12px;
    }

    input {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 16px;
      margin-bottom: 10px;
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
      margin-top: 10px;
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
      margin-top: 30px;
      font-size: 12px;
      color: #777;
    }
  </style>
</head>
<body>

<div class="container">
  <h1>ðŸ§® Calculadora de Atrasos 0,5â€¯% desde el 1 enero 2024.
  </h1>
  <p>Introduce el importe bruto mensual completo de tu nÃ³mina (incluyendo base, destino, especÃ­fico...)  SIMULACRO ORIENTATIVO</p>

  <label for="nomina">NÃ³mina mensual bruta (â‚¬):</label>
  <input type="number" id="nomina" placeholder="Ejemplo: 2150.00" step="0.01">

  <button onclick="calcular()">Calcular atrasos</button>

  <div id="resultado" class="resultado" style="display:none;"></div>
</div>

<div class="footer">
  CCOO FSC RegiÃ³n de Murcia Â· ElaboraciÃ³n propia
</div>

<script>
function calcular() {
  const nomina = parseFloat(document.getElementById('nomina').value);
  if (isNaN(nomina) || nomina <= 0) {
    alert("Introduce una cifra vÃ¡lida.");
    return;
  }

  const subidaMensual = nomina * 0.005;

  const hoy = new Date();
  const aÃ±oActual = hoy.getFullYear();
  const mesActual = hoy.getMonth() + 1;

  const meses2024 = 12;
  const meses2025 = (aÃ±oActual === 2025) ? mesActual : (aÃ±oActual > 2025 ? 12 : 0);
  const totalMensualidades = meses2024 + meses2025;

  let pagasExtras = 2; // junio y diciembre 2024
  if (aÃ±oActual > 2025 || (aÃ±oActual === 2025 && mesActual >= 6)) {
    pagasExtras += 1;
  }

  const atrasosMensuales = subidaMensual * totalMensualidades;
  const atrasosExtras = subidaMensual * pagasExtras;
  const atrasosTotales = atrasosMensuales + atrasosExtras;

  const resultado = document.getElementById("resultado");
  resultado.style.display = "block";
  resultado.innerHTML = `
    <strong>ðŸ“ˆ Subida mensual (0,5â€¯%):</strong> ${subidaMensual.toFixed(2)}â€¯â‚¬<br><br>
    <strong>ðŸ—“ï¸ Meses con atrasos:</strong> ${totalMensualidades} â†’ <strong>${atrasosMensuales.toFixed(2)}â€¯â‚¬</strong><br>
    <strong>ðŸŽ Pagas extra incluidas:</strong> ${pagasExtras} â†’ <strong>${atrasosExtras.toFixed(2)}â€¯â‚¬</strong><br><br>
    <span class="resaltado">ðŸ’° Total atrasos a percibir: ${atrasosTotales.toFixed(2)}â€¯â‚¬</span>
  `;
}
</script>

</body>
</html>
