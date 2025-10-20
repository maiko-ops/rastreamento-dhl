<!DOCTYPE html>
<html>
<head>
  <title>Rastreamento DHL</title>
  <meta charset="UTF-8">
</head>
<body>
  <h1>Rastreie sua encomenda DHL</h1>
  <form id="rastreamento">
    <input type="text" id="codigo" placeholder="Digite o código de rastreio" required>
    <button type="submit">Rastrear</button>
  </form>
  <div id="resultado"></div>

  <script>
    document.getElementById("rastreamento").addEventListener("submit", function(e) {
      e.preventDefault();
      const codigo = document.getElementById("codigo").value;

      fetch("https://api.trackingmore.com/v2/trackings/post", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "Trackingmore-Api-Key": "SUA_API_KEY_AQUI"
        },
        body: JSON.stringify({
          tracking_number: codigo,
          carrier_code: "dhl"
        })
      })
      .then(res => res.json())
      .then(data => {
        if (data.meta.code === 200) {
          document.getElementById("resultado").innerText =
            "Status atual: " + data.data.tracking_info.status;
        } else {
          document.getElementById("resultado").innerText =
            "Erro: " + data.meta.message;
        }
      })
      .catch(err => {
        document.getElementById("resultado").innerText =
          "Erro ao conectar com a API.";
      });
    });
  </script>
</body>
</html>
