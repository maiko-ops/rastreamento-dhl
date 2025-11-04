<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Rastreamento DHL Simples</title>
</head>
<body>

    <h1>Rastreamento de Encomendas DHL</h1>
    
    <input type="text" id="dhl-tracking-number" placeholder="Insira o número de rastreamento (Ex: 8350214880)">
    <button onclick="trackShipment()">Rastrear</button>
    
    <hr>
    
    <h2>Resultados do Rastreamento</h2>
    <div id="tracking-results">
        <p>Aguardando número de rastreamento...</p>
    </div>

    <script src="tracking.js"></script> 
    
</body>
</html>
