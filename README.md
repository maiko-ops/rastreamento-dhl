<form id="rastreamento">
  <input type="text" id="codigo" placeholder="Digite o código DHL" required>
  <button type="submit">Rastrear</button>
</form>
<div id="resultado"></div>

<script>
document.getElementById("rastreamento").addEventListener("submit", function(e) {
  e.preventDefault();
  const codigo = document.getElementById("codigo").value;

  fetch("https://api.aftership.com/v4/trackings", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "aftership-api-key": "SUA_API_KEY"
    },
    body: JSON.stringify({
      tracking: {
        tracking_number: codigo,
        slug: "dhl"
      }
    })
  })
  .then(res => res.json())
  .then(data => {
    if (data.data) {
      document.getElementById("resultado").innerText =
        "Rastreamento iniciado. Você receberá atualizações por e-mail.";
    } else {
      document.getElementById("resultado").innerText =
        "Erro: " + data.meta.message;
    }
  });
});
</script>
