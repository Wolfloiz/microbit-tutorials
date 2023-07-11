```template
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 1

Agora vamos aproveitar o jogo que já criamos e passar a contar quantas vezes
a argola toca no arame. O objetivo é chegar ao outro lado com o mínimo de erros possíveis.

```ghost
    basic.showIcon(IconNames.No)
```

## Step 2

Para isso, vamos criar uma variável chamada `||variables:Erros||` dentro da aba `||variables:Variáveis||`.
Ainda nesta mesma aba `||variables:Variáveis||`, selecione o comando
`||variables:definir Erros para 0||` e o posicione dentro do laço `||basic:no iniciar||`.

```blocks
let Erros = 0
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 3

Agora, dentro do laço `||input:no pin ... pressionado||`, adicione o bloco
`||variables:alterar Erros por 1||`, localizado na aba `||variables:Variáveis||`,
para que toda vez que a argola toque no arame, o erro seja contabilizado. Em seguida, insira o bloco
`||basic:mostrar número 0||` abaixo do anterior, dentro do mesmo laço.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})
```

## Step 4

Por fim, selecione o bloco da variável `||variables:Erros||`, na aba
`||variables:Variáveis||`, e o posicione dentro do bloco
`||basic:mostrar número||`, para que o número exibido seja a quantidade de erros cometidos até então.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(Erros)
})
```

## Step 5

Pronto! Após carregar o programa para o Micro:bit e fazer a montagem dos fios,
argola e arame, já podemos jogar! Tente desafiar um amigo e veja quem chega ao
final com menos erros.
