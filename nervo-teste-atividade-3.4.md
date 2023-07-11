```template
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})

Erros = 0
```

## Step 1

Só nos resta adicionar um botão para recomeçar o jogo para termos o projeto completo.
Esse botão deve resetar a quantidade de Erros, para que um novo jogador possa jogar.

## Step 2

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

## Step 3

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

## Step 4

Pronto! Após carregar o programa para o micro:bit e fazer a montagem dos fios,
argola e arame, já podemos jogar! Agora que temos um botão de reiniciar. Veja quantas
tentativas você gasta para chegar ao final sem encostar no arame!!
