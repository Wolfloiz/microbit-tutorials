

```template
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})

Erros = 0
```

## Step 1

A única coisa que falta agora, é colocar um botão para recomeçar o jogo. 
Esse botão deve resetar a quantidade de Erros, para um novo jogador poder 
jogar.


## Step 2

Na aba ``||input:Input||``, vamos pegar o bloco 
``||input:no botão ... pressionado||``.



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

Por fim, vamos pegar o bloco ``||variables:definir Erros para 0||`` na aba 
``||variables:Variáveis||``, e colocar ele dentro do bloco ``||input:no botão ... pressionado||``, para 
zerar o número de erros toda vez que o botão for apertado.


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
argola e arame, já podemos jogar! Agora que temos um botão de reset, veja quantas 
tentativas você gasta para chegar no final sem errar nenhuma vez!!