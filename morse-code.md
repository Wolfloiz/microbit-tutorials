# Código Morse

## Step 1

Adicione no laço ``||basic:no iniciar||`` dois blocos presentes na aba ``||radio:Rádio||``, são eles: ``||radio:definir grupo do rádio||`` e ``||radio: conjunto de rádio transmite energia 7||``. 
Este último está dentro das opções avançadas da aba ``||radio:Rádio||``, que são exibidas quando clicamos nos três pontos.

```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 2

Devemos determinar quais comandos as placas devem executar quando pressionarmos cada um dos botões durante o envio das mensagens. 
Em todos os quatro casos, ``||Input:botão A||``, ``||Input:botão B||``, ``||Input:botões A+B||`` e ``||Input:agitar||``, estamos usando funções de entrada do Micro:bit, por isso, usaremos os laços presentes na aba ``||Input:Input||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onGesture(Gesture.Shake, function () {
	
})
input.onButtonPressed(Button.AB, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 3

Iniciamos com o laço ``||Input:no botão A pressionado||`` para programarmos o envio de um **PONTO**. Iniciamos com o bloco ``||radio:radio envia número 0||``,
seguido do comando ``||basic:mostrar leds||``, em que desenharemos um ponto acionando os LEDs centrais da matriz. 

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(0)
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
})
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 4

Em seguida, adicionamos uma ``||basic:pausa||`` de meio segundo (**500ms**), para determinar o tempo que os LEDs ficarão acesos. 
Finalizamos com o bloco ``||basic:limpar tela||``, também localizado na aba ``||basic:Básico||``.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(0)
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 5

Seguindo para a programação do ``||Input:botão B||``, vamos construir a mesma lógica, apenas alterando o número enviado para **1** e os LEDs que estarão acesos na matriz para formar um **TRAÇO**. 
Podemos duplicar os blocos do laço do ``||Input:botão A||`` e realizar tais alterações.

```blocks
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(0)
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(1)
    basic.showLeds(`
        . . . . .
        . . . . .
        . # # # .
        . . . . .
        . . . . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 6

Para os ``||Input:botões A+B||``, devemos enviar um número diferente dos anteriores para sinalizar que estamos passando para a próxima palavra. 
Neste caso, vamos exibir uma **seta para direita** na matriz de LEDs. Duplique os blocos do laço ao lado, altere o número para **2** e desenhe a seta.

```blocks
input.onButtonPressed(Button.AB, function () {
    radio.sendNumber(2)
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
```
## Step 7

Chegamos ao laço agitar em que precisamos exibir um sinal de erro na matriz de LEDs, como um **X**. Além disso, devemos enviar um novo número (**3**) para que o outro Micro:bit também entenda esse comando 
e informe ao seu usuário que a palavra deve ser desconsiderada.

```blocks
input.onGesture(Gesture.Shake, function () {
    radio.sendNumber(3)
    basic.showLeds(`
        # . . . #
        . # . # .
        . . # . .
        . # . # .
        # . . . #
        `)
    basic.pause(500)
    basic.clearScreen()
})
```

## Step 8

Neste ponto, programamos tudo o que os Micro:bits precisam executar para enviar os sinais para o outro. 
Entretanto, ainda precisamos considerar o caso em que eles estão recebendo essas mensagens. Por isso, vamos adicionar o laço ``||Radio:ao receber rádio||`` ``||variables:receivedNumber||`` presente na aba ``||Radio:Rádio||``.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
	
})
```

## Step 9

O Micro:bit só executará as instruções dentro deste laço quando receber um número via ``||Radio:Rádio||``. Portanto, vamos incluir estruturas lógicas ``||Logic:se-então-senão||`` para testar cada um dos casos de números recebidos.
Adicione o segundo bloco localizado na aba ``||Logic:Lógica||`` e clique **três** vezes no sinal de adição para criar mais casos a serem avaliados pelo Micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (true) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Step 10

Agora, devemos criar os testes lógicos que serão realizados dentro de cada ``||Logic:se-então||``.
Para isso, usaremos o ``||Logic:comparador||`` em cada caso para avaliar se o número recebido ``||variables:receivedNumber||`` é igual a **0**, **1**, **2**, ou **3** respectivamente. 
Para inserir o bloco ``||variables:receivedNumber||`` no ``||Logic:comparador||`` basta clicar sobre ele e arrastá-lo até o espaço circular.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
    	
    } else if (receivedNumber == 1) {
    	
    } else if (receivedNumber == 2) {
    	
    } else if (receivedNumber == 3) {
    	
    } else {
    	
    }
})
```

## Step 11

Por fim, basta inserir os símbolos que devem ser mostrados em cada caso, o **PONTO**, **TRAÇO**, **SETA DIREITA** e **X** com a ``||basic:pausa||`` de meio segundo (**500ms**) e o ``||basic:limpar tela||``,
garantindo que eles apareçam por um tempo e despois sumam para o usuário perceber a mudança de símbolo.

 Para o **PONTO** (``||variables:receivedNumber||``** = 0**):

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
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 1) {
    	
    } else if (receivedNumber == 2) {
    	
    } else if (receivedNumber == 3) {
    	
    } else {
    	
    }
})
```

## Step 12

Para o **TRAÇO** (``||variables:receivedNumber||``** = 1**):

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
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 2) {
    	
    } else if (receivedNumber == 3) {
    	
    } else {
    	
    }
})
```

## Step 13

Para o **SETA PARA DIREITA** (``||variables:receivedNumber||``** = 2**):

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
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 2) {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 3) {
    	
    } else {
    	
    }
})
```

## Step 14

Para o **X** (``||variables:receivedNumber||``** = 3**):

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
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 2) {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 3) {
        basic.showLeds(`
            # . . . #
            . # . # .
            . . # . .
            . # . # .
            # . . . #
            `)
        basic.pause(500)
        basic.clearScreen()
    } else {
    	
    }
})
```

## Step 15

Na última parte, dentro do senão, vamos apenas ``||basic:limpar a tela||``, pois o Micro:bit não estará recebendo nenhum dos números que estabelecemos como códigos.

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
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 2) {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 3) {
        basic.showLeds(`
            # . . . #
            . # . # .
            . . # . .
            . # . # .
            # . . . #
            `)
        basic.pause(500)
        basic.clearScreen()
    } else {
        basic.clearScreen()
    }
})
```

## Step 16

Desse modo, finalizamos o programa que permite que o Micro:bit envie ou receba as mensagens codificadas em Morse. 
Teste um pouco no simulador e transfira o código para duas placas para ver o funcionamento na prática.

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
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 2) {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
        basic.pause(500)
        basic.clearScreen()
    } else if (receivedNumber == 3) {
        basic.showLeds(`
            # . . . #
            . # . # .
            . . # . .
            . # . # .
            # . . . #
            `)
        basic.pause(500)
        basic.clearScreen()
    } else {
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(0)
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
input.onGesture(Gesture.Shake, function () {
    radio.sendNumber(3)
    basic.showLeds(`
        # . . . #
        . # . # .
        . . # . .
        . # . # .
        # . . . #
        `)
    basic.pause(500)
    basic.clearScreen()
})
input.onButtonPressed(Button.AB, function () {
    radio.sendNumber(2)
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(1)
    basic.showLeds(`
        . . . . .
        . . . . .
        . # # # .
        . . . . .
        . . . . .
        `)
    basic.pause(500)
    basic.clearScreen()
})
radio.setGroup(1)
radio.setTransmitPower(7)

```