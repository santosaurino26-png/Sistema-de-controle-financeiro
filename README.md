<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Controle Financeiro</title>

<style>
body{
    font-family: Arial, sans-serif;
    max-width: 500px;
    margin: 20px auto;
    padding: 20px;
    background: #0f172a;
    color: white;
}

h1{
    text-align: center;
    color: #00bfff;
}

input, select{
    width: 100%;
    padding: 12px;
    margin-top: 10px;
    border: 2px solid #00bfff;
    border-radius: 8px;
    background: #1e293b;
    color: white;
    box-sizing: border-box;
}

button{
    width: 100%;
    padding: 12px;
    margin-top: 10px;
    border: none;
    border-radius: 8px;
    background: #22c55e;
    color: white;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
}

button:hover{
    background: #16a34a;
}

h2{
    background: #c2b280;
    color: #111;
    padding: 10px;
    border-radius: 8px;
    text-align: center;
}

ul{
    padding: 0;
}

li{
    list-style: none;
    background: #ef4444;
    color: white;
    margin-top: 10px;
    padding: 12px;
    border-radius: 8px;
    border-left: 6px solid #00bfff;
    font-weight: bold;
}
</style>
</head>
<body>

<h1>ðŸ’° Controle Financeiro</h1>

<input type="number" id="saldoInicial" placeholder="Digite seu saldo inicial">
<button onclick="definirSaldo()">Definir Saldo Inicial</button>

<h2>Saldo Atual: R$ <span id="saldo">0.00</span></h2>

<input type="text" id="descricao" placeholder="DescriÃ§Ã£o">

<select id="tipo">
    <option value="receita">ðŸ’µ Receita</option>
    <option value="despesa">ðŸ’¸ Despesa</option>
</select>

<input type="number" id="valor" placeholder="Valor">

<button onclick="adicionar()">Adicionar MovimentaÃ§Ã£o</button>

<ul id="lista"></ul>

<script>
let saldo = 0;

function definirSaldo() {
    const valorInicial = Number(document.getElementById("saldoInicial").value);

    if (isNaN(valorInicial)) {
        alert("Digite um valor vÃ¡lido!");
        return;
    }

    saldo = valorInicial;
    document.getElementById("saldo").textContent = saldo.toFixed(2);
}

function adicionar() {
    const descricao = document.getElementById("descricao").value;
    let valor = Number(document.getElementById("valor").value);
    const tipo = document.getElementById("tipo").value;

    if (descricao === "" || isNaN(valor) || valor <= 0) {
        alert("Preencha os campos corretamente!");
        return;
    }

    if (tipo === "despesa") {
        valor = -valor;
    }

    saldo += valor;
    document.getElementById("saldo").textContent = saldo.toFixed(2);

    const item = document.createElement("li");

    item.textContent =
        `${tipo === "receita" ? "ðŸ’µ Receita" : "ðŸ’¸ Despesa"} | ${descricao} | R$ ${Math.abs(valor).toFixed(2)}`;

    document.getElementById("lista").appendChild(item);

    document.getElementById("descricao").value = "";
    document.getElementById("valor").value = "";
}
</script>

</body>
</html>