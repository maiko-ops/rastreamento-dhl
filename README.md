<form id="rastreamento">
  <input type="text" id="codigo" placeholder="Digite o código DHL" required>
  <button type="submit">Rastrear</button>
</form>
<div id="resultado"></div>

<script>
document.getElementById("rastreamento").addEventListener("submit", function(e) {
  e.preventDefault();
  const codigo = document.getElementById("codigo").value;

  fetch(`https://api-eu.dhl.com/track/shipments?trackingNumber=${codigo}`, {
    method: "GET",
    headers: {
      "DHL-API-Key": "GAWegOrzyTeGp9mXBygDZ9GCIk7Df7rS"
    }
  })
  .then(res => res.json())
  .then(data => {
    const status = data.shipments?.[0]?.status?.status;
    document.getElementById("resultado").innerText =
      "Status atual: " + status;
  });
});
</script>
