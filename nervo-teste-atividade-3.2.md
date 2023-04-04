

```template
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.Happy)
})
```

## Step 1

Com base no último programa que fizemos, vamos agora fazer um jogo chamado 
nervo teste. Ele consiste em passar uma argola por um caminho, sem encostar 
a argola no arame. Para isso, vamos trocar o ícone do bloco ``||basic:mostrar ícone||`` 
para um X, para mostrar que a argola encostou no arame.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```


## Step 2
Pronto! Após carregar o programa para o micro:bit e fazer a montagem dos fios, 
argola e arame, já podemos jogar! Veja se consegue chegar ao final sem errar!!!