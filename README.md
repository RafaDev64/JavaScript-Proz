# JavaScript - Proz
Exercícios realizados durante a disciplina 'Linguagem de Programação', ministrada no curso de _Desenvolvimento de Sistemas_ da Escola Proz

<hr>

### **Variáveis, Operadores Aritméticos, Concatenação, Relacionais e Lógicos - parte 1**

**Q1.** Crie um programa cujo objetivo é inserir seus dados pessoais (nome, idade, gênero e cidade) e armazenar em cada variável determinada e depois exibidos na tela.


<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dados Pessoais</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        label {
            display: block;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Insira seus dados pessoais</h1>
    <form id="dadosForm">
        <label for="nome">Nome:</label>
        <input type="text" id="nome" required>
        <label for="idade">Idade:</label>
        <input type="number" id="idade" required>
        <label for="genero">Gênero:</label>
        <select id="genero" required>
            <option value="">Selecione</option>
            <option value="Masculino">Masculino</option>
            <option value="Feminino">Feminino</option>
            <option value="Outro">Outro</option>
        </select>
        <label for="cidade">Cidade:</label>
        <input type="text" id="cidade" required>
        <button type="submit">Enviar</button>
    </form>
    <h2>Dados Inseridos:</h2>
    <div id="resultado"></div>
    <script>
        document.getElementById('dadosForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Impede o envio do formulário
            // Coletando os dados do formulário
            const nome = document.getElementById('nome').value;
            const idade = document.getElementById('idade').value;
            const genero = document.getElementById('genero').value;
            const cidade = document.getElementById('cidade').value;
            // Exibindo os dados na tela
            const resultadoDiv = document.getElementById('resultado');
            resultadoDiv.innerHTML = `
                <p><strong>Nome:</strong> ${nome}</p>
                <p><strong>Idade:</strong> ${idade}</p>
                <p><strong>Gênero:</strong> ${genero}</p>
                <p><strong>Cidade:</strong> ${cidade}</p>
            ;
        });
    </script>
</body>
</html>


**Q2.** Dado o cálculo 12 x 3 + 4 - 8 / 2 % 3, qual o resultado segundo a precedência de operadores?
```
//Adicionar parênteses só para confirmar 
var calculo =  (12 * 3) + 4 - (8 / 2) % 3

document.write(" O resultado da expressão 12 * 3 + 4 - 8 / 2 % 3 é: " + calculo)
```



**Q3.** Crie um programa que utilize os métodos de Strings, onde o usuário envia uma frase e o programa exibe as informações dessa frase (tamanho, letra maiúscula, letra minúscula, substring e index).
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Informações da Frase</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .result {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Informações da Frase</h1>
    <label for="frase">Digite uma frase:</label><br>
    <input type="text" id="frase" placeholder="Digite sua frase aqui"><br><br>
    <label for="substring">Digite uma substring para verificar:</label><br>
    <input type="text" id="substring" placeholder="Substring"><br><br>
    <label for="caractere">Digite um caractere para encontrar o índice:</label><br>
    <input type="text" id="caractere" placeholder="Caractere" maxlength="1"><br><br>    
    <button onclick="analisarFrase()">Analisar Frase</button>   
    <div class="result" id="result"></div>
   <script>
        function analisarFrase() {
            const frase = document.getElementById('frase').value;
            const substring = document.getElementById('substring').value;
            const caractere = document.getElementById('caractere').value;
           const tamanho = frase.length;
            // Contagem de letras maiúsculas e minúsculas
            const maiusculas = frase.split('').filter(c => c === c.toUpperCase() && c !== ' ').length;
            const minusculas = frase.split('').filter(c => c === c.toLowerCase() && c !== ' ').length;
            // Verificação da substring
            const substringEncontrada = frase.includes(substring) ? "encontrada" : "não encontrada";
            // Índice do caractere
            const indice = frase.indexOf(caractere);
            const indiceMensagem = indice !== -1 ? `O índice do caractere '${caractere}' é: ${indice}` : `O caractere '${caractere}' não está presente na frase.`;
            // Exibir resultados
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `
                <p>Tamanho da frase: ${tamanho} caracteres</p>
                <p>Letras maiúsculas: ${maiusculas}</p>
                <p>Letras minúsculas: ${minusculas}</p>
                <p>A substring '${substring}' foi ${substringEncontrada} na frase.</p>
                <p>${indiceMensagem}</p>
            `;
        }
    </script>
</body>
</html>

### **Variáveis, Operadores Aritméticos, Concatenação, Relacionais e Lógicos - parte 2**

**Q1.** Crie um programa que peça ao usuário para inserir dois números. Verifique se eles são iguais e exiba uma mensagem indicando o resultado.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Verificação de Números</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .result {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Verificação de Números</h1>
    <label for="numero1">Digite o primeiro número:</label><br>
    <input type="number" id="numero1" placeholder="Primeiro número"><br><br>  
    <label for="numero2">Digite o segundo número:</label><br>
    <input type="number" id="numero2" placeholder="Segundo número"><br><br>    
    <button onclick="verificarNumeros()">Verificar</button>    
    <div class="result" id="result"></div>
    <script>
        function verificarNumeros() {
            const numero1 = parseFloat(document.getElementById('numero1').value);
            const numero2 = parseFloat(document.getElementById('numero2').value);
            const resultDiv = document.getElementById('result');
            // Verifica se os números são iguais
            if (numero1 === numero2) {
                resultDiv.innerHTML = "<p>Os números são iguais.</p>";
            } else {
                resultDiv.innerHTML = "<p>Os números são diferentes.</p>";
            }
        }
    </script>
</body>
</html>

**Q2.** Crie um programa que peça ao usuário para inserir dois números. Verifique se eles são pares e exiba uma mensagem indicando o resultado.


<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Verificador de Números Pares</title>
    <script>
        function verificarNumeros() {            
            const numero1 = parseInt(document.getElementById('numero1').value);
            const numero2 = parseInt(document.getElementById('numero2').value);
            let mensagem = '';
            // Verifica se números são pares
            if (numero1 % 2 === 0 && numero2 % 2 === 0) {
                mensagem = 'Ambos os numeros são pares.';
            } else if (numero1 % 2 === 0) {
                mensagem = 'O primeiro número é par e o segundo número é ímpar.';
            } else if (numero2 % 2 === 0) {
                mensagem = 'O primeiro número é ímpar e o segundo número é par.';
            } else {
                mensagem = 'Ambos os números são ímpares.';
            }
            // mensagem
            document.getElementById('resultado').innerText = mensagem;
        }
    </script>
</head>
<body>
    <h1>Verificador de Números Pares</h1>
    <label for="numero1">Insira o primeiro número:</label>
    <input type="number" id="numero1"><br><br>
    <label for="numero2">Insira o segundo número:</label>
    <input type="number" id="numero2"><br><br>
    <button onclick="verificarNumeros()">Verificar</button>
    <h2 id="resultado"></h2>
</body>
</html>


**Q3.** Crie um programa que peça ao usuário para inserir dois números. Verifique se eles são ímpares e exiba uma mensagem indicando o resultado.
```

```

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Verificador de Números Ímpares</title>
    <script>
        function verificarImpar() {
            var num1 = parseInt(document.getElementById("numero1").value);
            var num2 = parseInt(document.getElementById("numero2").value);
            var resultado = "";          
            if (num1 % 2 !== 0 && num2 % 2 !== 0) {
                resultado = "Ambos os números são ímpares.";
            } else if (num1 % 2 !== 0) {
                resultado = "O primeiro número é ímpar e o segundo é par.";
            } else if (num2 % 2 !== 0) {
                resultado = "O segundo número é ímpar e o primeiro é par.";
            } else {
                resultado = "Ambos os números são pares.";
            }
            //  resultado
            document.getElementById("resultado").innerText = resultado;
        }
    </script>
</head>
<body>
    <h1>Verificador de Números Ímpares</h1>
    <label for="numero1">Digite o primeiro número:</label>
    <input type="number" id="numero1"><br><br>
    <label for="numero2">Digite o segundo número:</label>
    <input type="number" id="numero2"><br><br>
    <button onclick="verificarImpar()">Verificar</button>
    <h2 id="resultado"></h2>
</body>
</html>

**Q4.** Crie um aplicativo que calcule o Índice de Massa Corporal (IMC) de uma pessoa. Peça o peso e a altura, e calcule o IMC usando a fórmula: IMC = peso / (altura * altura). E por fim, indique, de acordo com o resultado, se a pessoa está: 
* Abaixo do normal
* Normal
* Sobrepeso
* Obesidade grau I
* Obesidade grau II
* Obesidade grau III
```

```

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de IMC</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            justify-content: center;
            align-items: center;
            margin: 40px;
            padding: 40px;
            border: 1px solid #0c0101;
            border-radius: 10px;
            max-width: 400px;
        }
        input[type="number"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #0c0101;
            border-radius: 5px;
        }
        button {
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .resultado {
            margin-top: 20px;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <h1>Calculadora de IMC</h1>
    <label for="peso">Peso (kg):</label>
    <input type="number" id="peso" placeholder="Digite seu peso" required>
    <label for="altura">Altura (m):</label>
    <input type="number" step="0.01" id="altura" placeholder="Digite sua altura" required>    
    <button onclick="calcularIMC()">Calcular IMC</button>
    <div class="resultado" id="resultado"></div>
    <script>
        function calcularIMC() {
            const peso = parseFloat(document.getElementById('peso').value);
            const altura = parseFloat(document.getElementById('altura').value);
            const resultadoDiv = document.getElementById('resultado');
            if (!peso || !altura) {
                resultadoDiv.innerHTML = "Por favor, insira valores válidos.";
                return;
            }
            const imc = peso / (altura * altura);
            let classificacao;
            if (imc < 18.5) {
                classificacao = "Abaixo do normal";
            } else if (imc < 24.9) {
                classificacao = "Normal";
            } else if (imc < 29.9) {
                classificacao = "Sobrepeso";
            } else if (imc < 34.9) {
                classificacao = "Obesidade grau I";
            } else if (imc < 39.9) {
                classificacao = "Obesidade grau II";
            } else {
                classificacao = "Obesidade grau III";
            }
            resultadoDiv.innerHTML = `Seu IMC é: ${imc.toFixed(2)}<br>Classificação: ${classificacao}`;
        }
    </script>

</body>
</html>


**Q5.** Desenvolva um jogo interativo de pedra, papel e tesoura onde o usuário pode competir contra o computador. Dica: utilize o método de Matemática random para criar um número aleatório.
```

```

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pedra, Papel e Tesoura</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
        }
        .container {
            text-align: center;
            background: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .choice-button {
            margin: 10px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: #007bff;
            color: white;
            transition: background-color 0.3s;
        }
        .choice-button:hover {
            background-color: #0056b3;
        }
        .resultado {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
        }
        #reset {
            margin-top: 20px;
            padding: 10px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 10px;
            background-color: #28a745;
            color: white;
            display: none; 
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Pedra, Papel e Tesoura</h1>
        <div class="choices">
            <button class="choice-button" onclick="jogar('pedra')">Pedra</button>
            <button class="choice-button" onclick="jogar('papel')">Papel</button>
            <button class="choice-button" onclick="jogar('tesoura')">Tesoura</button>
        </div>
        <div id="resultado" class="resultado"></div>
        <button id="reset" onclick="resetar()">Jogar Novamente</button>
    </div>
    <script>
        function jogar(usuarioEscolha) {
            const opcoes = ['pedra', 'papel', 'tesoura'];
            const computadorEscolha = opcoes[Math.floor(Math.random() * opcoes.length)];
            let resultado = '';
            if (usuarioEscolha === computadorEscolha) {
                resultado = `Empate! Ambos escolheram ${usuarioEscolha}.`;
            } else if (
                (usuarioEscolha === 'pedra' && computadorEscolha === 'tesoura') ||
                (usuarioEscolha === 'papel' && computadorEscolha === 'pedra') ||
                (usuarioEscolha === 'tesoura' && computadorEscolha === 'papel')
            ) {
                resultado = `Você ganhou! ${usuarioEscolha} vence ${computadorEscolha}.`;
            } else {
                resultado = `Você perdeu! ${computadorEscolha} vence ${usuarioEscolha}.`;
            }
            document.getElementById('resultado').innerText = resultado;
            document.getElementById('reset').style.display = 'inline'; 
        }
        function resetar() {
            document.getElementById('resultado').innerText = '';
            document.getElementById('reset').style.display = 'none'; 
        }
    </script>
</body>
</html>



### **Funções**




**Q1.** Para um site de e-commerce, desenvolva um programa com uma função que calcula o preço total com base na quantidade de produtos inserida pelo usuário. A entrada é recebida como uma string e precisa ser convertida em um número inteiro antes de ser multiplicada pelo preço unitário.
`<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cálculo de Preço Total</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input[type="number"] {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            margin-bottom: 10px;
        }
        button {
            padding: 10px;
            font-size: 16px;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>Cálculo de Preço Total</h1>
    <label for="quantidade">Digite a quantidade de produtos:</label>
    <input type="number" id="quantidade" placeholder="Quantidade" />
    <label for="precoUnitario">Digite o preço unitário do produto:</label>
    <input type="number" id="precoUnitario" placeholder="Preço Unitário" step="0.01" />
    <button onclick="calcularPrecoTotal()">Calcular Preço Total</button>
    <div class="result" id="result"></div>
    <script>
        function calcularPrecoTotal() {
            const quantidade = document.getElementById('quantidade').value;
            const precoUnitario = document.getElementById('precoUnitario').value;
            const resultDiv = document.getElementById('result');
            // Converte a quantidade e o preço unitário para números inteiros e flutuantes
            const quantidadeNumerica = parseInt(quantidade);
            const precoUnitarioNumerico = parseFloat(precoUnitario);
           // Verifica se os valores são válidos
            if (isNaN(quantidadeNumerica) || isNaN(precoUnitarioNumerico) || quantidadeNumerica < 0 || precoUnitarioNumerico < 0) {
                resultDiv.innerHTML = "<p style='color: red;'>Por favor, insira valores válidos.</p>";
                return;
            }
            // Calcula o preço total
            const precoTotal = quantidadeNumerica * precoUnitarioNumerico;
          // Exibe o resultado
            resultDiv.innerHTML = `<p>O preço total é: R$ ${precoTotal.toFixed(2)}</p>`;
        }
    </script>
</body>
</html>



**Q2.** Desenvolva um programa para aplicar descontos aplicativo que ajuda os usuários a rastrear seus gastos. Como parte deste aplicativo, os usuários podem inserir o preço de um produto, o valor do desconto e o aplicativo calcula o valor total após aplicar um desconto.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Desconto</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .result {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Calculadora de Desconto</h1>
    <label for="preco">Digite o preço do produto:</label><br>
    <input type="number" id="preco" placeholder="Preço do produto" step="0.01"><br><br>
    <label for="desconto">Digite o valor do desconto (em %):</label><br>
    <input type="number" id="desconto" placeholder="Desconto (%)" step="0.01"><br><br>   
    <button onclick="calcularDesconto()">Calcular</button>  
    <div class="result" id="result"></div>
    <script>
        function calcularDesconto() {
            const preco = parseFloat(document.getElementById('preco').value);
            const desconto = parseFloat(document.getElementById('desconto').value);
            const resultDiv = document.getElementById('result');
            // Verifica se os valores são válidos
            if (isNaN(preco) || isNaN(desconto) || preco < 0 || desconto < 0) {
                resultDiv.innerHTML = "<p style='color: red;'>Por favor, insira valores válidos.</p>";
                return;
            }
            // Calcula o valor do desconto
            const valorDesconto = (desconto / 100) * preco;
            // Calcula o preço final após aplicar o desconto
            const precoFinal = preco - valorDesconto;
            // Exibe o resultado
            resultDiv.innerHTML = `
                <p>O valor do desconto é: R$ ${valorDesconto.toFixed(2)}</p>
                <p>O preço final após aplicar o desconto é: R$ ${precoFinal.toFixed(2)}</p>
            `;
        }
    </script>
</body>
</html>




**Q3.** Desenvolva uma calculadora.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Simples</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            font-size: 18px;
        }
        button {
            padding: 10px;
            font-size: 18px;
            margin: 5px;
        }
        .result {
            margin-top: 20px;
            font-size: 20px;
        }
    </style>
</head>
<body>
    <h1>Calculadora Simples</h1>
    <input type="text" id="num1" placeholder="Digite o primeiro número" />
    <input type="text" id="num2" placeholder="Digite o segundo número" />
    <div>
        <button onclick="calcular('+')">Adicionar</button>
        <button onclick="calcular('-')">Subtrair</button>
        <button onclick="calcular('*')">Multiplicar</button>
        <button onclick="calcular('/')">Dividir</button>
    </div>    
    <div class="result" id="result"></div>
    <script>
        function calcular(operacao) {
            const num1 = parseFloat(document.getElementById('num1').value);
            const num2 = parseFloat(document.getElementById('num2').value);
            const resultDiv = document.getElementById('result');
            let resultado;
            // Verifica se os números são válidos
            if (isNaN(num1) || isNaN(num2)) {
                resultDiv.innerHTML = "<p style='color: red;'>Por favor, insira números válidos.</p>";
                return;
            }
            // Realiza a operação
            switch (operacao) {
                case '+':
                    resultado = num1 + num2;
                    break;
                case '-':
                    resultado = num1 - num2;
                    break;
                case '*':
                    resultado = num1 * num2;
                    break;
                case '/':
                    if (num2 === 0) {
                        resultDiv.innerHTML = "<p style='color: red;'>Erro: Divisão por zero não é permitida.</p>";
                        return;
                    }
                    resultado = num1 / num2;
                    break;
                default:
                    resultDiv.innerHTML = "<p style='color: red;'>Operação inválida.</p>";
                    return;
            }
           // Exibe o resultado
          resultDiv.innerHTML = `<p>Resultado: ${resultado}</p>`;
        }
    </script>
</body>
</html>

### Laços de Repetição + Datas + POO - Programação Orientada a Objetos

**Q1.** Desenvolva um programa que informa a tabuada de um número inserido pelo usuário.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tabuada</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input[type="number"] {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            margin-bottom: 10px;
        }
        button {
            padding: 10px;
            font-size: 16px;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>Tabuada</h1>
    <input type="number" id="numero" placeholder="Digite um número" />
    <button onclick="mostrarTabuada()">Mostrar Tabuada</button>
    <div class="result" id="result"></div>
    <script>
        function mostrarTabuada() {
            const numero = parseInt(document.getElementById('numero').value);
            const resultDiv = document.getElementById('result');
            // Verifica se o número é válido
            if (isNaN(numero)) {
                resultDiv.innerHTML = "<p style='color: red;'>Por favor, insira um número válido.</p>";
                return;
            }
            // Gera a tabuada
            let tabuada = `<h2>Tabuada do ${numero}:</h2>`;
            for (let i = 1; i <= 10; i++) {
                tabuada += `<p>${numero} x ${i} = ${numero * i}</p>`;
            }
            // Exibe a tabuada
            resultDiv.innerHTML = tabuada;
        }
    </script>
</body>
</html>




**Q2.** Conforme com o que você aprendeu sobre manipulação de datas, faça as contas: quantos dias se passaram da data do seu nascimento até o dia de hoje?

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cálculo de Dias desde o Nascimento</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input[type="date"] {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            margin-bottom: 10px;
        }
        button {
            padding: 10px;
            font-size: 16px;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>Cálculo de Dias desde o Nascimento</h1>
    <label for="dataNascimento">Digite sua data de nascimento:</label>
    <input type="date" id="dataNascimento" />
    <button onclick="calcularDias()">Calcular Dias</button>
        <div class="result" id="result"></div>
    <script>
        function calcularDias() {
            const dataNascimentoInput = document.getElementById('dataNascimento').value;
            const resultDiv = document.getElementById('result');
          // Verifica se a data de nascimento foi inserida
            if (!dataNascimentoInput) {
               resultDiv.innerHTML = "<p style='color: red;'>Por favor, insira sua data de nascimento.</p>";
                return;
            }
            // Converte a data de nascimento para um objeto Date
            const dataNascimento = new Date(dataNascimentoInput);
            const dataAtual = new Date();
            // Calcula a diferença em milissegundos
            const diferenca = dataAtual - dataNascimento;
     // Converte a diferença de milissegundos para dias
            const diasPassados = Math.floor(diferenca / (1000 * 60 * 60 * 24));
            // Exibe o resultado
            resultDiv.innerHTML = `<p>Se passaram ${diasPassados} dias desde a sua data de nascimento até hoje.</p>`;
        }
    </script>
</body>
</html>


**Q3.** Utilizando a programação Orientada a Objetos, monte um modelo de construção de um sistema de uma das empresas abaixo: 
* Netflix

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mini Netflix</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #141414;
            color: #ffffff;
        }
        h1 {
            text-align: center;
            margin: 20px 0;
            color: #e50914;
        }
        .container {
            max-width: 800px;
            margin: auto;
            background: #222;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }
        .content {
            margin-bottom: 20px;
        }
        .content h2 {
            margin: 10px 0;
            color: #e50914;
        }
        button {
            padding: 10px;
            margin: 5px;
            cursor: pointer;
            background-color: #e50914;
            border: none;
            border-radius: 5px;
            color: white;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #f40612;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
            background: #333;
            padding: 10px;
            border-radius: 5px;
        }
        .content div {
            margin: 10px 0;
            padding: 10px;
            background: #333;
            border-radius: 5px;
        }
        .content h3 {
            margin: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Mini Netflix</h1>
        <div class="content">
            <h2>Assinatura</h2>
            <button onclick="assinar('Básico', 19.90)">Assinar Plano Básico - R$ 19,90</button>
            <button onclick="assinar('Premium', 39.90)">Assinar Plano Premium - R$ 39,90</button>
        </div>
        <div class="content">
            <h2>Filmes e Séries</h2>
            <div>
                <h3>A Origem</h3>
                <button onclick="adicionarConteudo('A Origem')">Adicionar à Biblioteca</button>
            </div>
            <div>
                <h3>Stranger Things</h3>
                <button onclick="adicionarConteudo('Stranger Things')">Adicionar à Biblioteca</button>
            </div>
        </div>
        <div class="result" id="result"></div>
    </div>
    <script>
        let biblioteca = [];
        let planoAssinado = null;
        function assinar(plano, preco) {
            planoAssinado = plano;
            document.getElementById('result').innerHTML = `Você assinou o plano: ${plano} por R$ ${preco.toFixed(2)}`;
        }
        function adicionarConteudo(conteudo) {
            if (!planoAssinado) {
                alert("Você precisa assinar um plano primeiro!");
                return;
            }
            biblioteca.push(conteudo);
            document.getElementById('result').innerHTML += `<p>${conteudo} foi adicionado à sua biblioteca.</p>`;
        }
    </script>
</body>
</html>
