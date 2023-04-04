


```template
radio.setGroup(1)
radio.setTransmitPower(7)
input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    radio.sendNumber(0)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.AB, function () {
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
    radio.sendNumber(2)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        . . . . .
        . . . . .
        . # # # .
        . . . . .
        . . . . .
        `)
    radio.sendNumber(1)
    basic.pause(100)
    basic.clearScreen()
})

```





## Step 1

O que fizemos até então permite que um dos micro:bits envie o Código Morse e o outro 
receba. Vamos agora fazer algo diferente, para que os dois micro:bits possam enviar e 
receber.

## Step 2

Estamos partindo do código que fizemos antes do micro:bit que apenas envia o código. 
Devemos então acrescentar a parte que faz com que o micro:bit receba informação, 
e mostre o símbolo na tela de acordo com a informação recebida.


## Step 3

Vamos adicionar o bloco ``||radio:ao receber rádio receivedNumber||``,
 que pode ser achado na aba 
``||radio:Rádio||``.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
	
})
```

## Step 4

Agora, dentro do bloco ``||radio:ao receber rádio receivedNumber||`` vamos adicionar 
o laço condicional ``||logic:se-então-senão||``, que está na aba 
``||logic:Lógica||``. Vamos então clicar no símbolo ``||logic:+||`` na extremidade 
inferior esquerda do bloco ``||logic:se-então-senão||`` para adicionar mais uma condição.


```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Step 5

Vamos então adicionar as condições lógicas ao laço ``||logic:se-então-senão||``. As 
estruturas de condição lógica podem ser achadas na aba ``||logic:Lógica||``. A primeira 
condição será ``||logic:receivedNumber = 0||``, e a segunda será 
``||logic:receivedNumber = 1||``. Para pegar a ``||radio:receivedNumber||``, podemos 
arrastá-la do bloco 
``||radio:ao receber rádio receivedNumber||`` para onde quisermos.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
    	
    } else if (receivedNumber == 1) {
    	
    } else {
    	
    }
})
```

## Step 6

Em seguida, vamos utilizar a estrutura condicional para mostrar o símbolo (ponto, traço 
ou seta) na tela, de acordo com o número recebido. Se o número recebido for zero, 
mostraremos o ponto, se for 1, mostraremos o traço, e se não for nenhum dos dois, mostraremos 
a seta.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
    } else {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
    }
})
```

## Step 7

Por fim, vamos adicionar um bloco de  ``||basic:pausa||`` e um de ``||basic:limpar tela||`` 
abaixo do ``||logic:se-então-senão||``, para termos tempo de ver o símbolo na tela, e 
depois apagar o símbolo, para esperarmos o próximo.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
    } else {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
    }
    basic.pause(100)
    basic.clearScreen()
})
radio.setGroup(1)
```





## Step 8

Pronto, agora podemos carregar esse código para dois micro:bits, e nos comunicar 
via código! E então, consegue ter uma conversa com um amigo só em Código Morse? 
Não vale trapacear!!








