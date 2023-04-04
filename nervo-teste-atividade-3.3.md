

```template
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 1

Vamos agora pegar o jogo que já criamos, e vamos contar quantas vezes 
a argola toca no arame, para podermos competir com amigos e ver quem 
chega ao final com menos falhas.

```ghost
    basic.showIcon(IconNames.No)
```

## Step 2

Para contar quantas vezes a argola toca no arame, vamos criar uma variável 
chamada ``||variables:Erros||`` dentro da aba ``||variables:Variáveis||``. 
Ainda dentro da aba ``||variables:Variáveis||`` vamos pegar o bloco 
``||variables:definir Erros para 0||`` e colocar ele dentro do bloco 
``||basic:no iniciar||``. 


```blocks
let Erros = 0
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 3

Agora, dentro do bloco ``||input:no pin ... pressionado||``, vamos colocar o bloco 
``||variables:alterar Erros por 1||``, que está na aba 
``||variables:Variáveis||`` 
 para que toda vez que a argola toque  
no arame, o erro seja contado. Vamos também colocar o bloco 
``||basic:mostrar número 0||``, logo abaixo.


```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(0)
})
```


## Step 4

Por fim, vamos pegar o bloco da variável ``||variables:Erros||``, na aba 
``||variables:Variáveis||``, e colocar ele dentro do bloco 
``||basic:mostrar número||``, para mostrarmos quantos erros temos até então.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
    Erros += 1
    basic.showNumber(Erros)
})
```


## Step 5
Pronto! Após carregar o programa para o micro:bit e fazer a montagem dos fios, 
argola e arame, já podemos jogar! Tente desafiar um amigo e veja quem chega ao 
final com menos erros.