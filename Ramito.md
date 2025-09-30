<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title> Para mi morenito</title>
  <style>
    body {
      background: #fff9f4;
      font-family: 'Arial', sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
    }
    h1 {
      font-size: 1.3em;
      margin-top: 20px;
      color: #444;
    }
    canvas {
      margin-top: 30px;
    }
    #mensaje {
      margin: 20px auto;
      font-size: 20px;
      font-weight: bold;
      color: #333;
      width: 80%;
      line-height: 1.4em;
    }
  </style>
</head>
<body>
  <h1> Recuerda que estas en mi corazoncito 💕</h1>
  <canvas id="ramito" width="400" height="400"></canvas>
  <div id="mensaje"></div>

  <script>
    // --- Dibujo del ramo con carritos ---
    const canvas = document.getElementById("ramito");
    const ctx = canvas.getContext("2d");

    const centerX = 200;
    const centerY = 150;
    const radius = 100;
    const count = 7;

    function drawCar(x, y, color) {
      // carrocería
      ctx.fillStyle = color;
      ctx.fillRect(x - 25, y - 12, 50, 24);
      // cabina
      ctx.fillStyle = color;
      ctx.fillRect(x - 10, y - 22, 20, 15);
      // ventana
      ctx.fillStyle = "white";
      ctx.fillRect(x - 8, y - 20, 16, 11);
      // ruedas
      ctx.fillStyle = "black";
      ctx.beginPath(); ctx.arc(x - 18, y + 12, 6, 0, 2 * Math.PI); ctx.fill();
      ctx.beginPath(); ctx.arc(x + 18, y + 12, 6, 0, 2 * Math.PI); ctx.fill();
    }

    // tallos
    ctx.strokeStyle = "green";
    ctx.lineWidth = 6;
    for (let i = 0; i < count; i++) {
      let angle = Math.PI/2.5 + (i - (count-1)/2) * 0.3;
      ctx.beginPath();
      ctx.moveTo(centerX, centerY);
      ctx.lineTo(centerX + radius*1.2*Math.cos(angle), centerY + radius*1.6*Math.sin(angle));
      ctx.stroke();
    }

    // cinta
    ctx.fillStyle = "deeppink";
    ctx.fillRect(centerX - 50, centerY + 80, 100, 30);

    // colores llamativos estilo Hot Wheels
    const colors = ["red","orange","yellow","limegreen","blue","purple","brown"];
    for (let i = 0; i < count; i++) {
      let angle = Math.PI/2.6 + (i - (count-1)/2) * 0.35;
      let x = centerX + radius*Math.cos(angle);
      let y = centerY + radius*Math.sin(angle);
      drawCar(x, y, colors[i % colors.length]);
    }

    // --- Texto tipo máquina de escribir ---
    const mensaje = , Espero que este dellito te haga muy feliz mi negrito;
    const mensajeDiv = document.getElementById("mensaje");

    let i = 0;
    function typeWriter() {
      if (i < mensaje.length) {
        mensajeDiv.textContent += mensaje.charAt(i);
        i++;
        setTimeout(typeWriter, 50); // velocidad (ms por letra)
      }
    }
    typeWriter();
  </script>
</body>
</html>
