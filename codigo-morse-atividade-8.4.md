


## Step 1

Vamos agora programar o segundo micro:bit (M2), que irá receber o código enviado 
pelo primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos pegar o bloco ``||radio:definir grupo do rádio 1||``, na aba 
``||radio:Rádio||``, e colocá-lo dentro do bloco ``||basic:no iniciar||``, igual fizemos 
para o primeiro micro:bit.

```blocks
radio.setGroup(1)
```

## Step 3

Em seguida, vamos adicionar o bloco ``||radio:ao receber rádio receivedNumber||``,
 que pode ser achado na aba 
``||radio:Rádio||``. Esse bloco executa tudo que está dentro dele quando recebe um 
número de outro micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
	
})
radio.setGroup(1)
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
radio.setGroup(1)
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
radio.setGroup(1)
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
radio.setGroup(1)
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

Pronto, agora temos os dois micro:bits configurados e comunicando. Tente enviar uma 
mensagem em Código Morse para um amigo e veja se ele consegue decifrar!







