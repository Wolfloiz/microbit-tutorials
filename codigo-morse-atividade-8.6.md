


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





## Step 1

E se apertarmos um botão errado por acidente? Precisamos avisar a pessoa que estamos 
comunicando que erramos, e começar a escrever a palavra denovo! Mas como fazemos isso?


## Step 2

Da mesma forma que podemos escolher enviar ponto, traço ou próxima palavra, vamos agora 
enviar uma informação que significa reiniciar palavra. Vamos começar adicionando o bloco 
``||input:em agitar||``. Toda vez que quisermos reiniciar a palavra, vamos ter que agitar 
o micro:bit.

```blocks
input.onGesture(Gesture.Shake, function () {
	
})
```

## Step 3

Vamos então colocar no bloco ``||input:em agitar||`` os mesmos blocos que estão dentro de 
``||input:no botão A pressionado||``, podemos fazer isso copiando e colando, para facilitar.


```blocks
input.onGesture(Gesture.Shake, function () {
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
```

## Step 4

Vamos agora mudar tanto o símbolo mostrado quanto o número enviado ao agitarmos o micro:bit. 
Dentro do bloco ``||input:em agitar||``, vamos modificar o bloco ``||basic:mostrar leds||`` 
para mostrar um X. E no bloco ``||radio:rádio envia número 0||``, vamos trocar o número zero 
pelo número 3.

```blocks
input.onGesture(Gesture.Shake, function () {
	basic.showLeds(`
        # . . . #
        . # . # .
        . . # . .
        . # . # .
        # . . . #
        `)
    radio.sendNumber(3)
    basic.pause(100)
    basic.clearScreen()
})
```

## Step 5

Agora já terminamos a parte de enviar a mensagem de reiniciar palavra. Falta modificar a 
parte de receber essa informação.


## Step 6

No bloco ``||logic:se-então-senão||`` vamos então clicar no símbolo ``||logic:+||`` 
na extremidade inferior, de modo a acrescentar uma condição.

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
    } else if (false) {
    	
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
```

## Step 7

No laço novo que acabou de ser criado, vamos colocar a condição 
``||logic:receivedNumber = 3||``. Por fim, vamos adicionar dentro desse laço o bloco 
``||basic:mostrar leds||`` e desenhar um X.


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
    } else if (receivedNumber == 3) {
        basic.showLeds(`
            # . . . #
            . # . # .
            . . # . .
            . # . # .
            # . . . #
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
```


## Step 8

Pronto, agora podemos carregar esse código para dois micro:bits, e nos comunicar 
via código! Se errar, não se esqueça de agitar o micro:bit e recomeçar a palavra.
 E então, consegue ter uma conversa com um amigo só em Código Morse? 
Não vale trapacear!!









