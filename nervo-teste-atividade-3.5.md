## Step 1

Vamos criar um jogo chamado nervo teste para testarmos nossa concentação e coordenação motora.
Ele consiste em passar uma argola por um arame, sem encostar encostar um no outro durante o trajeto.

## Step 2

Primeiro, vamos adicionar o laço `||input:no pin ... pressionado||`, localizado  
na aba `||input:input||`. Selecione o `||input:pin 0 (P0)||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {

})

```

## Step 3

Agora, vamos exibir o ícone X, usando o bloco `||basic:mostrar ícone||`,
que pode ser encontrado na aba `||basic:Básico||`, para informar que a
argola encostou no arame.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 4

O próximo passo é contar quantas vezes a argola toca no arame. Para isso, vamos criar uma variável
chamada `||variables:Erros||` dentro da aba `||variables:Variáveis||`.
Ainda nesta aba, selecione o bloco `||variables:definir Erros para 0||` e o posicione dentro do laço
`||basic:no iniciar||`.

```blocks
let Erros = 0
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 5

Agora, dentro do laço `||input:no pin ... pressionado||`, vamos adicionar o comando
`||variables:alterar Erros por 1||`, localizado na aba `||variables:Variáveis||`
para que toda vez que a argola toque no arame, o erro seja contabilizado. Também vamos inserir o bloco
`||basic:mostrar número 0||`, logo abaixo do anterior, ainda no mesmo laço.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})
```

## Step 6

Em seguida, vamos pegar o bloco da variável `||variables:Erros||`, na aba
`||variables:Variáveis||`, e colocá-lo dentro do bloco
`||basic:mostrar número||`, para exibirmos quantos erros temos até então.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(Erros)
})
```

## Step 7

Só nos resta adicionar um botão para recomeçar o jogo para termos o projeto completo.
Esse botão deve resetar a quantidade de Erros, para que um novo jogador possa jogar.

## Step 8

Na aba `||input:Input||`, adicione o laço `||input:no botão ... pressionado||` ao programa.

```blocks
input.onButtonPressed(Button.A, function () {

})
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})

Erros = 0
```

## Step 9

Por fim, vamos pegar o bloco `||variables:definir Erros para 0||` na aba
`||variables:Variáveis||`, e colocá-lo dentro do laço `||input:no botão ... pressionado||`, para
zerar o número de erros toda vez que o botão A for apertado.

```blocks
input.onButtonPressed(Button.A, function () {
    Erros = 0
})
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})

Erros = 0
```

## Step 10

Pronto! Após carregar o programa para o micro:bit e fazer a montagem dos fios,
argola e arame, já podemos jogar! Agora que temos um botão de reiniciar. Veja quantas
tentativas você gasta para chegar ao final sem encostar no arame!!
