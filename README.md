<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salário Mínimo Atual</title>
</head>
<body>
    <h1>Salário Mínimo Atual no Brasil</h1>
    <p>O salário mínimo atual é: <strong id="salario">Carregando...</strong></p>

    <script>
        async function fetchSalario() {
            try {
                const response = await fetch('https://api.hgbrasil.com/finance?key=9db8c7e1&format=json');
                const data = await response.json();
                document.getElementById('salario').innerText = `R$ ${data.results.currencies.BRL.buy.toFixed(2)}`;
            } catch (error) {
                document.getElementById('salario').innerText = 'Erro ao carregar o valor.';
            }
        }

        fetchSalario();
    </script>
</body>
</html>
