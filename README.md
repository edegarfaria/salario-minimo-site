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
                // Usando a API oficial do governo para pegar o valor do salário mínimo
                const response = await fetch('https://api.bcb.gov.br/dados/serie/bcdata.sgs.1/dados?formato=csv');
                const data = await response.text();

                // Pega o último valor do salário mínimo
                const lines = data.split('\n');
                const lastValue = lines[lines.length - 2]; // Pega a última linha (último valor)
                const salary = lastValue.split(',')[1]; // Extrai o valor do salário

                document.getElementById('salario').innerText = `R$ ${parseFloat(salary).toFixed(2)}`;
            } catch (error) {
                document.getElementById('salario').innerText = 'Erro ao carregar o valor.';
            }
        }

        fetchSalario();
    </script>
</body>
</html>
