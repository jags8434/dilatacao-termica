<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simulador de Dilatação Térmica</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input {
            padding: 8px;
            width: 200px;
        }
        button {
            padding: 10px 15px;
            margin-top: 10px;
        }
        .resultado {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <h1>Simulador de Dilatação Térmica</h1>

    <label for="comprimento">Comprimento inicial (m):</label>
    <input type="number" id="comprimento" step="any" aria-label="Comprimento inicial em metros">

    <label for="coeficiente">Coeficiente de dilatação (1/°C):</label>
    <input type="number" id="coeficiente" step="any" aria-label="Coeficiente de dilatação em 1/°C">

    <label for="temp_inicial">Temperatura inicial (°C):</label>
    <input type="number" id="temp_inicial" step="any" aria-label="Temperatura inicial em graus Celsius">

    <label for="temp_final">Temperatura final (°C):</label>
    <input type="number" id="temp_final" step="any" aria-label="Temperatura final em graus Celsius">

    <button onclick="calcularDilatacao()">Calcular</button>

    <div class="resultado" id="resultado"></div>
    <div class="resultado" id="resultado_final"></div>

    <script>
        function calcularDilatacao() {
            const comprimentoInicial = parseFloat(document.getElementById('comprimento').value);
            const coeficienteDilatacao = parseFloat(document.getElementById('coeficiente').value);
            const tempInicial = parseFloat(document.getElementById('temp_inicial').value);
            const tempFinal = parseFloat(document.getElementById('temp_final').value);

            // Validação dos inputs
            if (isNaN(comprimentoInicial) || isNaN(coeficienteDilatacao) || isNaN(tempInicial) || isNaN(tempFinal)) {
                alert("Por favor, insira valores numéricos válidos.");
                return;
            }

            if (comprimentoInicial < 0 || coeficienteDilatacao < 0 || tempInicial > tempFinal) {
                alert("Por favor, insira valores positivos e assegure-se de que a temperatura inicial seja menor que a final.");
                return;
            }

            const deltaTemp = tempFinal - tempInicial;
            const deltaComprimento = comprimentoInicial * coeficienteDilatacao * deltaTemp;
            const novoComprimento = comprimentoInicial + deltaComprimento;

            document.getElementById('resultado').innerText = `Variação no comprimento: ${deltaComprimento.toFixed(4)} m`;
            document.getElementById('resultado_final').innerText = `Novo comprimento: ${novoComprimento.toFixed(4)} m`;
        }
    </script>

</body>
</html>
