# FEEDBACK 

<https://github.com/djedu28/trilhas-v2-desafios/blob/desafio2_trilha_de_dados/TrilhasV2-Desafio2/desafio_trilha_de_dados/FEEDBACK.MD>

Os desafios de lógica precisam ser revisados antes de publicar.

* no desafio 1 tinha gaps nos testes de lógica dos ranges de valores, até brinquei com isso na resolução dizendo que o funcionário não receberia o aumento. 
* Porem o erro dessa vez, na tarefa 2.c) da parte 2 não possuía lógica:

## NO INPUT FORNECIDO PELO DESAFIO DIZIA

> c) Elabore um algoritmo que se o valor da poupança do cliente for maior que R\$ 50.000,00 e menor ou igual R\$100.000,00 e, se o tempo de aplicação for maior que 12 (meses) e menor ou igual a 24(meses), a taxa de juro de ser 5\%. Caso o tempo de aplicação for maior ou igual a 12 (meses) e menor ou igual a 24 (meses), a taxa de juros deverá ser de 10\%. ...

### OU SEJA, as condições são:

``capitalAplicado` > 50000 && `capitalAplicado` <= 100000`

até ai tudo bem, mas na parte que do range de tempo fica duplicado de +12 a 24.

1. MAIOR a 12 (meses) e menor ou igual a 24 (meses)
2. MAIOR OU IGUAL a 12 (meses) e menor ou igual a 24 (meses)

No formato que foi construído o texto/logica o que acontece é:

se o `CapitalAplicado` for atendido, então cai na condição do `CapitalAplicado` + `TempoDeAplicacao`
e como não foi dito "**caso contrario** para o `CapitalAplicado`" então o teste do `TempoDeAplicacao` é reaplicado dentro o teste da condição `CapitalAplicado`+`TempoDeAplicacao`, ai que vem o problema.

No fluxo que o `CapitalAplicado` é atendido, é colocando a taxa de 5% quando `12 < TempoDeAplicacao <= 24`, logo após é testado o `12 <= TempoDeAplicacao <= 24`, que atualiza a taxa para 10%, pois a primeira condição do `TempoDeAplicacao` está contida no tempo da segunda condição.

Resultado, a aplicação da taxa de 5% nunca será usada, e não foi especificado o que acontece quando a condição do `CapitalAplicado` não é atendida.

```js
 if(capitalAplicado > 50000 && capitalAplicado <= 100000){
    if (tempoDeAplicacao > 12 && tempoDeAplicacao <= 24) {
        taxaDeJuros = 0.05; // 5%
    }
    if (tempoDeAplicacao >= 12 && tempoDeAplicacao <= 24) {
        taxaDeJuros = 0.10; // 10%
    } else {
        alert("Valor informado inválido! Por favor, informe o tempo em meses entre 12 e 24 meses");
        return;
    }
} else {
    alert("Valor informado inválido! Por favor, informe o valor depositado na poupança entre R$ 50.001,00 e R$ 100.000,00");
    return;
}
```
