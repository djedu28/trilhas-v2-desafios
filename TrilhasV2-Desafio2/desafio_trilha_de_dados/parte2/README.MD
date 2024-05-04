# 2ª Parte – Aplicação dos conceitos estudados da lógica

**2ª Parte – Aplicação dos conceitos estudados da lógica:**

## 1.  Elabore um algoritmo que contenha uma função chamada “Operacao”, a qual recebe 2 parâmetros e, após as operações, imprima a soma da exponenciação, o resto da divisão do primeiro pelo segundo e a subtração do segundo pelo primeiro.

### Resolução

Para criar o algoritmo/função `Operacao` em JavaScript, segui o processo abaixo. A função recebe dois parâmetros, realiza as operações solicitadas e retorna um objeto contendo os resultados.

```javascript
function Operacao(a, b) {
    // Soma da exponenciação
    const somaExponenciacao = Math.pow(a, b) + Math.pow(b, a);
    // Resto da divisão do primeiro pelo segundo
    const restoDivisao = a % b;
    // Subtração do segundo pelo primeiro
    const subtracao = b - a;

    return {
        somaExponenciacao,
        restoDivisao,
        subtracao
    };
}
```

### Essa função funciona da seguinte maneira:

1. **Soma da exponenciação**: Utiliza a função `Math.pow(a, b)` para calcular a exponenciação de `a` elevado a `b`, e `Math.pow(b, a)` para calcular a exponenciação de `b` elevado a `a`. A soma desses dois resultados é armazenada na variável `somaExponenciacao`. Poderia alternativamente utilizar o operador matemático `**` (potenciação), exemplo: **`a` elevado a `b`** pode ser escrito com `a ** b`.

2. **Resto da divisão do primeiro pelo segundo**: Utiliza o operador de módulo `%` para calcular o resto da divisão de `a` por `b`. Esse resultado é armazenado na variável `restoDivisao`. Uma utilização pratica desse operador é verificar se um numero é par, ou seja, é divisível por 2 com `valor%2==0` (se o resto da divisão por 2 é 0).

3. **Subtração do segundo pelo primeiro**: Subtrai `a` de `b` e armazena o resultado na variável `subtracao`.

Finalmente, a função retorna um objeto contendo os resultados das três operações.

## Utilizando essa função

Você pode utilizar ela em um motor javascript ou rodar ela no navegador usando um arquivo html.

* Para usar essa função é só chamar `Operacao(a, b)` sendo `a` e `b` números.

```js
console.log(Operacao(2, 3))// retorna { somaExponenciacao: 17, restoDivisao: 2, subtracao: 1 }
console.log(Operacao(3, 2))// retorna { somaExponenciacao: 17, restoDivisao: 1, subtracao: -1 }
```

* Para criar um HTML que utilize essa função, você pode seguir o exemplo abaixo. Este exemplo inclui dois campos de entrada para que o usuário possa inserir os valores `a` e `b`, um botão para executar a operação e um elemento para exibir os resultados.

```html
<!DOCTYPE html>
<html lang="pt">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Operação - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 1</title>
</head>

<body>
    <h1>Operação - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 1</h1>
    <h2>
        1. Elabore um algoritmo que contenha uma função chamada “Operacao”, a qual recebe 2 parâmetros e, após as
        operações, imprima a soma da exponenciação, o resto da divisão do primeiro pelo segundo e a subtração do segundo
        pelo primeiro.
    </h2>
    <label> A: <input type="number" id="valorA" placeholder="Digite o valor de A"></label><br/>
    <label> B: <input type="number" id="valorB" placeholder="Digite o valor de B"></label><br/>
    <br/>
    <button onclick="executarOperacao()">Executar Operação</button><br/>
    <div id="resultado"></div>

    <script>
        function Operacao(a, b) {
            const somaExponenciacao = Math.pow(a, b) + Math.pow(b, a);
            const restoDivisao = a % b;
            const subtracao = b - a;

            return {
                somaExponenciacao,
                restoDivisao,
                subtracao
            };
        }

        function executarOperacao() {
            const valorA = document.getElementById('valorA').value;
            const valorB = document.getElementById('valorB').value;

            const resultado = Operacao(valorA, valorB);

            document.getElementById('resultado').innerHTML = `
            <ul>
                <strong>RESULTADO:</strong>
                <li>Soma da exponenciação: ${resultado.somaExponenciacao}</li>
                <li>Resto da divisão do primeiro pelo segundo: ${resultado.restoDivisao}</li>
                <li>Subtração do segundo pelo primeiro: ${resultado.subtracao}</li>
            <ul>
            `;
        }
    </script>
</body>

</html>
```

Neste exemplo, quando o usuário clica no botão "Executar Operação", a função `executarOperacao` é chamada. Esta função obtém os valores dos campos de entrada, executa a função `Operacao` com esses valores e exibe os resultados no elemento com o ID "resultado".

## 2.  Um Banco contratou-lhe para implementar uma operação no seu sistema que aplica a taxa de rendimento sobre o valor aplicado na poupança. Logo, o supervisor de TI pediu para implementar uma função que receba dois parâmetros: “CapitalAplicado” e “TempoDeAplicacao:

   a) Implemente um algoritmo que solicite ao usuário o valor, em dinheiro, aplicado e a quantidade de meses em aplicação, considerando que a taxa de juros, por mês, é de 0,6022\%. Ao final, imprima o valor aplicado inicialmente, a quantidade de meses e o valor final com o acréscimo de juros, em “Template String”, da seguinte forma: **A quantia de R\$[CapitalAplicado] aplicada em [TempoDeAplicacao] meses, rendeu R\$[ValorRendimento] a juros de [TaxaDeJuros].** Caso o valor informado for menor que 0 ou diferente de um número, o algoritmo deve apresentar uma alerta na tela com a seguinte mensagem: “Valor informado inválido! Por favor, informe o valor depositado na poupança”. Em seguida, solicite novamente ao cliente o valor aplicado na poupança e a quantidade de meses, até que o valor válido seja informado.

   b) Faça um algoritmo que, se o capital aplicado for maior ou igual a R\$999,99 e menor ou igual R\$10.000,00 e o tempo de aplicação for maior que 5 meses e menor que 12 meses, a taxa de rendimento deve ser 2\%. O algoritmo deve solicitar ao cliente o valor do capital aplicado e o tempo de aplicação e, após a operação, o programa deve exibir na tela, o valor aplicado, a quantidade de meses em aplicação e o valor de rendimento em R\$, utilizando o “Tamplate string”, da seguinte forma: **A quantia de R\$[CapitalAplicado] aplicada em [TempoDeAplicacao] meses, rendeu R\$[ValorRendimento].** Caso o valor informado for menor que 0 ou diferente de um número, o algoritmo deve apresentar uma alerta na tela com a seguinte mensagem: “Valor informado inválido! Por favor, informe o valor depositado na poupança”. Em seguida, solicite novamente ao cliente o valor aplicado na poupança e a quantidade de meses, até que o valor válido seja informado.

   c) Elabore um algoritmo que se o valor da poupança do cliente for maior que R\$ 50.000,00 e menor ou igual R\$100.000,00 e, se o tempo de aplicação for maior que 12 (meses) e menor ou igual a 24(meses), a taxa de juro de ser 5\%. Caso o tempo de aplicação for maior ou igual a 12 (meses) e menor ou igual a 24 (meses), a taxa de juros deverá ser de 10\%. Por fim, imprima a mensagem na tela, em “Template String” da seguinte forma: “**A poupança de  R\$[CapitalAplicado] aplicada em [TempoDeAplicacao] meses, rendeu R\$[ValorRendimento]**”. Caso o valor informado for menor que 0 ou diferente de um número, o algoritmo deve apresentar uma alerta na tela com a seguinte mensagem: “Valor informado inválido! Por favor, informe o valor depositado na poupança!”. Em seguida, solicite novamente ao cliente o valor aplicado na poupança e a quantidade de meses, até que o valor válido seja informado.

### Resolução de 2. a)

Para resolver o desafio proposto, vamos criar uma função em JavaScript que solicite ao usuário o valor aplicado e a quantidade de meses em aplicação, aplique a taxa de juros de 0,6022% e exiba o resultado. Caso o valor informado seja inválido, o algoritmo deve solicitar novamente os dados até que sejam fornecidos valores válidos.

```html
<!DOCTYPE html>
<html lang="pt">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cálculo de Rendimento - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 2.a)</title>
</head>

<body>
    <h1>Cálculo de Rendimento - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 2.a)</h1>

    <label>
        Capital Aplicado:
        <input type="number" id="capitalAplicado" placeholder="Digite o valor aplicado">
    </label>
    <br>
    <label>
        Tempo de Aplicação (meses):
        <input type="number" id="tempoDeAplicacao" placeholder="Digite o tempo em meses">
    </label>
    <br>
    <button onclick="calcularRendimento()">Calcular Rendimento</button>
    <br>
    <div id="resultado"></div>

    <script>
        function calcularRendimento() {
            const capitalAplicado = document.getElementById('capitalAplicado').value;
            const tempoDeAplicacao = document.getElementById('tempoDeAplicacao').value;

            if (capitalAplicado <= 0) {
                alert("Valor informado inválido! Por favor, informe o valor depositado na poupança.");
                return;
            }
            if (tempoDeAplicacao <= 0) {
                alert("Valor informado inválido! Por favor, informe o tempo em meses da aplicação");
                return;
            }

            const taxaDeJuros = 0.006022; // 0.6022%
            const valorRendimento = capitalAplicado * tempoDeAplicacao * taxaDeJuros;

            document.getElementById('resultado').innerText = `
                A quantia de R\$${capitalAplicado} aplicada em ${tempoDeAplicacao} meses, rendeu R\$${valorRendimento.toFixed(2)} a juros de ${taxaDeJuros * 100}%.
            `;
        }
    </script>
</body>

</html>
```

Neste exemplo, a função `calcularRendimento` é chamada quando o usuário clica no botão "Calcular Rendimento". A função obtém os valores dos campos de entrada, verifica se os valores são válidos (maiores que 0), calcula o rendimento aplicando a taxa de juros ao capital aplicado e ao tempo de aplicação, e exibe o resultado no elemento com o ID "resultado". Se o valor informado for inválido, um alerta é exibido e a função retorna sem realizar o cálculo.

### Resolução de 2. b)

Para resolver o desafio proposto na parte b), vamos ajustar a função `calcularRendimento` para considerar a nova taxa de juros de 2% para capital aplicado entre R$999,99 e R$10.000,00 e tempo de aplicação entre 6 e 11 meses. Caso o valor informado seja inválido, o algoritmo deve solicitar novamente os dados até que sejam fornecidos valores válidos.

```html
<!DOCTYPE html>
<html lang="pt">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cálculo de Rendimento - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 2.b)</title>
</head>

<body>
    <h1>Cálculo de Rendimento - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 2.b)</h1>
    <p>
        Para resolver o desafio proposto, vamos criar uma função em JavaScript que solicite ao usuário o valor aplicado e a
        quantidade de meses em aplicação, aplique a taxa de juros de 0,6022% e exiba o resultado. Caso o valor informado
        seja inválido, o algoritmo deve solicitar novamente os dados até que sejam fornecidos valores válidos.
    </p>

    <label>
        Capital Aplicado:
        <input type="number" id="capitalAplicado" placeholder="Digite o valor aplicado">
    </label>
    <br>
    <label>
        Tempo de Aplicação (meses): 
        <input type="number" id="tempoDeAplicacao" placeholder="Digite o tempo em meses">
    </label>
    <br>
    <button onclick="calcularRendimento()">Calcular Rendimento</button>
    <br>
    <div id="resultado"></div>

    <script>
        function calcularRendimento() {
            const capitalAplicado = document.getElementById('capitalAplicado').value;
            const tempoDeAplicacao = document.getElementById('tempoDeAplicacao').value;

            if (capitalAplicado <= 0) {
                alert("Valor informado inválido! Por favor, informe o valor depositado na poupança.");
                return;
            }
            if (tempoDeAplicacao <= 0) {
                alert("Valor informado inválido! Por favor, informe o tempo em meses da aplicação");
                return;
            }

            let taxaDeJuros = 0.006022; // Taxa padrão de 0.6022%

            // Verifica se o capital aplicado está entre R$999,99 e R$10.000,00 
            // e o tempo de aplicação entre 6 e 11 meses
            if (
                    capitalAplicado >= 999.99   && capitalAplicado  <= 10_000 
                && tempoDeAplicacao >= 6        && tempoDeAplicacao <= 11
            ) {
                taxaDeJuros = 0.02; // 2% ou 2/100
            }

            const valorRendimento = capitalAplicado * tempoDeAplicacao * taxaDeJuros;

            document.getElementById('resultado').innerText = `
                A quantia de R\$${capitalAplicado} aplicada em ${tempoDeAplicacao} meses, rendeu R\$${valorRendimento.toFixed(2)}. A juros de ${taxaDeJuros * 100}%.
            `;
        }
    </script>
</body>

</html>
```

Neste exemplo, a função `calcularRendimento` foi ajustada para verificar se o capital aplicado está entre R$999,99 e R$10.000,00 e o tempo de aplicação entre 6 e 11 meses. Se essas condições forem atendidas, a taxa de juros é ajustada para 2%. A função então calcula o rendimento aplicando a taxa de juros ao capital aplicado e ao tempo de aplicação, e exibe o resultado no elemento com o ID "resultado". Se o valor informado for inválido, um alerta é exibido e a função retorna sem realizar o cálculo.

### Resolução de 2. c)

Para resolver o desafio proposto na parte c), vamos criar uma função em JavaScript que solicite ao usuário o valor aplicado e a quantidade de meses em aplicação, aplique a taxa de juros de acordo com as condições especificadas e exiba o resultado. Caso o valor informado seja inválido, o algoritmo deve solicitar novamente os dados até que sejam fornecidos valores válidos.

As condições são:

i. Condição 1

* se o valor da poupança do cliente for maior que R\$ 50.000,00 e menor ou igual R\$100.000,00 
* e, se o tempo de aplicação for maior que 12 (meses) e menor ou igual a 24(meses),
* então a taxa de juro de ser 5\%. 

ii. Condição 2

* Caso o tempo de aplicação for maior ou igual a 12 (meses) e menor ou igual a 24 (meses), a taxa de juros deverá ser de 10\%.

```html
<!DOCTYPE html>
<html lang="pt">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cálculo de Rendimento - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 2.b)</title>
</head>

<body>
    <h1>Cálculo de Rendimento - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 2.b)</h1>
    <p>
        Para resolver o desafio proposto na parte c), vamos criar uma função em JavaScript que solicite ao usuário o valor
        aplicado e a quantidade de meses em aplicação, aplique a taxa de juros de acordo com as condições especificadas e exiba
        o resultado. Caso o valor informado seja inválido, o algoritmo deve solicitar novamente os dados até que sejam
        fornecidos valores válidos.
    </p>
    <p>As condições são:</p>
    <pre>
        i. Condição 1
        
        * se o valor da poupança do cliente for maior que R\$ 50.000,00 e menor ou igual R\$100.000,00
        * e, se o tempo de aplicação for maior que 12 (meses) e menor ou igual a 24(meses),
        * então a taxa de juro de ser 5\%.
    </pre>
    <pre>
        ii. Condição 2
        
        * Caso o tempo de aplicação for maior ou igual a 12 (meses) e menor ou igual a 24 (meses), 
        a taxa de juros deverá ser de 10\%.
    </pre>
    <label>
        Capital Aplicado: 
        <input type="number" id="capitalAplicado" placeholder="Digite o valor aplicado">
        <span> maior que R$ 50000,00  e menor ou igual a R$100000,00 </span>
    </label>
    <br>
    <label>
        Tempo de Aplicação (meses): 
        <input type="number" id="tempoDeAplicacao" placeholder="Digite o tempo em meses">
        <span> deve estar entre 12 e 24 meses</span>
    </label>
    <br>
    <button onclick="calcularRendimento()">Calcular Rendimento</button>
    <br>
    <div id="resultado"></div>

    <script>
        function calcularRendimento() {
            const capitalAplicado = document.getElementById('capitalAplicado').value;
            const tempoDeAplicacao = document.getElementById('tempoDeAplicacao').value;

            if (capitalAplicado <= 0) {
                alert("Valor informado inválido! Por favor, informe o valor depositado na poupança.");
                return;
            }
            if (tempoDeAplicacao <= 0) {
                alert("Valor informado inválido! Por favor, informe o tempo em meses da aplicação");
                return;
            }

            let taxaDeJuros;

            // Verifica se o capital aplicado está entre R$50.000,00 e R$100.000,00 e o tempo de aplicação entre 12 e 24 meses
            if(capitalAplicado > 50000 && capitalAplicado <= 100000){
                if (tempoDeAplicacao > 12 && tempoDeAplicacao <= 24) {
                    taxaDeJuros = 0.05; // 5%
                } else if (tempoDeAplicacao >= 12 && tempoDeAplicacao <= 24) {
                    taxaDeJuros = 0.10; // 10%
                } else {
                    alert("Valor informado inválido! Por favor, informe o tempo em meses entre 12 e 24 meses");
                    return;
                }
            } else {
                alert("Valor informado inválido! Por favor, informe o valor depositado na poupança entre R$ 50.001,00 e R$ 100.000,00");
                return;
            }

            const valorRendimento = capitalAplicado * tempoDeAplicacao * taxaDeJuros;

            document.getElementById('resultado').innerText = `
                A poupança de R\$${capitalAplicado} aplicada em ${tempoDeAplicacao} meses, rendeu R\$${valorRendimento.toFixed(2)}. A juros de ${taxaDeJuros * 100}%.
            `;
        }
    </script>
</body>

</html>
```

Neste exemplo, a função `calcularRendimento` foi ajustada para verificar se o capital aplicado está entre R$50.000,00 e R$100.000,00 e o tempo de aplicação entre 12 e 24 meses. Se essas condições forem atendidas, a taxa de juros é ajustada para 5% ou 10%, conforme especificado. A função então calcula o rendimento aplicando a taxa de juros ao capital aplicado e ao tempo de aplicação, e exibe o resultado no elemento com o ID "resultado". Se o valor informado for inválido, um alerta é exibido e a função retorna sem realizar o cálculo.

## 3.  O seu primo pretende desenvolver um jogo de acerto para que o filho dele possa brincar, mas como ele não possui o conhecimento em programa, solicitou a sua ajuda, tendo em conta que você havia lhe dito que está fazendo o programa trilhas e aprendendo sobre o algoritmo e lógica de programação. Neste contexto, ele definiu as funcionalidades que gostaria que o jogo tenha:

- O programa deve criar um número secreto e solicitar ao usuário que chute um número entre 20 e 30;
- Se o número secreto for igual ao de chute, o programa deve exibir uma mensagem de acerto;
- Se o número secreto for diferente do número de chute, o programa deve exibir uma mensagem de erro, solicitando novamente um número entre 20 e 30;
- O programa deve oferecer 3 tentativas para o chute e, por fim, exibir uma mensagem de tentativas esgotadas e finalizar.

### Resolução da tarefa 3

Para criar um jogo de adivinhação simples em JavaScript, você pode seguir o exemplo abaixo. Este jogo irá gerar um número secreto entre 20 e 30 e dar ao usuário 3 tentativas para adivinhar o número. Se o usuário acertar, ele receberá uma mensagem de sucesso. Se não, após as 3 tentativas, ele receberá uma mensagem informando que as tentativas esgotaram e qual era o número secreto.

```html
<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jogo de Adivinhação  - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 3</title>
</head>
<body>
    <h1>Jogo de Adivinhação  - 2º desafio trilhasV2.1 - Dados - Parte 2 tarefa 3</title>

    <p>Adivinhe o número secreto entre 20 e 30:</p>
    <input type="number" id="chute" placeholder="Digite seu número entre 20 e 30">
    <button onclick="verificarChute()">Verificar</button>
    <div id="resultado"></div>

    <script>
        const numeroSecreto = Math.floor(Math.random() * 11) + 20; // Gera um número entre 20 e 30
        let tentativas = 3;

        function verificarChute() {
            const chute = document.getElementById('chute').value;
            const resultado = document.getElementById('resultado');

            if (tentativas <= 0) {
                resultado.innerHTML = `Tentativas esgotadas! O número secreto era ${numeroSecreto}.`;
                return;
            }

            if (chute == numeroSecreto) {
                resultado.innerHTML = `Parabéns! Você acertou o número secreto: ${numeroSecreto}.`;
            } else {
                tentativas--;
                resultado.innerHTML = `Errado! Você tem mais ${tentativas} tentativas.`;
            }
        }
    </script>
</body>
</html>
```

Neste exemplo, o jogo começa gerando um número secreto entre 20 e 30. O usuário tem 3 tentativas para adivinhar o número. Cada vez que o usuário clica no botão "Verificar", a função `verificarChute` é chamada. Esta função verifica se o número digitado pelo usuário (`chute`) é igual ao número secreto. Se for, exibe uma mensagem de sucesso. Se não for, decrementa o número de tentativas e exibe uma mensagem informando quantas tentativas restam. Se o usuário esgotar as tentativas sem acertar, exibe uma mensagem informando que as tentativas esgotaram e qual era o número secreto.