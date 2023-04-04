

## Step 1
Vamos agora fazer um jogo chamado nervo teste. Ele consiste em passar 
uma argola por um caminho, sem encostar a argola no arame.


## Step 2

Primeiro, vamos adicionar o bloco  ``||input:no pin ... pressionado||``, que está 
na aba  ``||input:input||``. Vamos escolher o ``||input:pin 0 (P0)||``.

```blocks
input.onPinPressed(TouchPin.P0, function () {
	
})

```

## Step 3

Vamos agora colocar um ícone X, usando o bloco ``||basic:mostrar ícone||``, 
que pode ser encontrado na aba ``||basic:Básico||``, para mostrar que a 
argola encostou no arame.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.No)
})
```

## Step 4

O próximo passo é contar quantas vezes 
a argola toca no arame, para podermos competir com amigos e ver quem 
chega ao final com menos falhas.

## Step 5

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

## Step 6
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

## Step 7

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

## Step 8

A única coisa que falta agora, é colocar um botão para recomeçar o jogo. 
Esse botão deve resetar a quantidade de Erros, para um novo jogador poder 
jogar.

## Step 9
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

## Step 10

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

## Step 11
Pronto! Após carregar o programa para o micro:bit e fazer a montagem dos fios, 
argola e arame, já podemos jogar! Tente competir com seus colegas e veja quem 
consegue chegar ao final com menos erros.