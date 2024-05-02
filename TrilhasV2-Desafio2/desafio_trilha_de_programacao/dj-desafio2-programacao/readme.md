# No layout apresentado no FIGMA existe um prolema de acessibilidade

## PROBLEMA

    Quando o input é preenchido a informação do que é solicitado no input 
    é perdida, pois o placeholder some, e não existe um label planejado
    no design apresentado no FIGMA. 

## CASO DE TESTE

    Quando é preenchido o campo "Nome Completo", a informação que indica
    que aquele input é do nome completo some da tela.

## SOLUÇÃO DE ACESSIBILIDADE PARA QUANDO O INPUT FOR PREENCHIDO

    Adicionar um evento em todos os inputs, para que quando o input for 
    preenchido aparecer o label do mesmo, e para não ficar informação 
    duplicada em tela, quando o input é vazio, o label é oculto em tela, 
    pois o placeHolder assume o papel de label

### Codigo css

```css
.input-container label {
    position: absolute; 
    top: 0rem;
    display: none;
}
.input-container[displayLabel="true"] {
    padding-top: 1rem;
}
.input-container[displayLabel="true"] label {
    display: block;
}
```

### Codigo JS

1. buscar todos os inputs em tela
2. percorrer com forEach todos os inputs em tela encontrados no passo anterior
3. Adicionar um evento onInput em todos os inputs.
   Esse evento onInput verifica se a value do input é vazia
   e baseada nessa informação ativa/desativa a label

```js
Array(...document.getElementsByTagName("input"))
    .forEach(element_input => {
        element_input.oninput = ({ target }) => {
            console.log(target.value)
            if (target.value) {
                console.log("ativando", target.name)
                target.parentElement.setAttribute("displayLabel", true)
            } else {
                console.log("desativando", target.name)
                target.parentElement.setAttribute("displayLabel", false)
            }
        }
    })
```
