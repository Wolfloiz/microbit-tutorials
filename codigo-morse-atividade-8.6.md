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
radio.setGroup(255)
```

## Step 1

E se apertarmos um botão errado por acidente? Precisamos avisar a pessoa que estamos
nos comunicando que erramos, e então, começar a escrever a palavra novamente! Mas como fazemos isso?

## Step 2

Da mesma forma que podemos escolher enviar um ponto, traço ou próxima palavra, também podemos enviar uma informação que significa reiniciar palavra. Para isso, vamos começar adicionando o laço
`||input:em agitar||`, localizado na categoria `||input:input||`.
Assim, sempre que quisermos reiniciar a palavra, vamos precisar agitar o micro:bit.

```blocks
input.onGesture(Gesture.Shake, function () {

})
```

## Step 3

Em seguida, coloque os mesmos blocos que estão dentro de `||input:no botão A pressionado||`, dentro também do laço `||input:em agitar||`.
Para facilitar, podemos fazer isso copiando e colando todo o laço, ou duplicando os blocos.

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

Agora, vamos mudar tanto o símbolo exibido, quanto o número enviado ao agitarmos o micro:bit.
Dentro do laço `||input:em agitar||`, modificamos o bloco `||basic:mostrar leds||`
para exibir um **X**. Já no bloco `||radio:rádio envia número 0||`, vamos trocar o número **0** pelo número **3**.

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

Assim, já terminamos a parte de enviar a mensagem para reiniciar a palavra. Porém, ainda falta modificar a
parte de receber essa informação.

## Step 6

No laço `||logic:se-então-senão||` vamos clicar no símbolo `||logic:+||`
que fica na extremidade inferior do bloco para acrescentar uma condição.

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

Neste laço condicional que acabou de ser criado, vamos incluir a condição
`||logic:receivedNumber = 3||`. Por fim, dentro do `||logic:então||` desse laço, adicionamos o bloco
`||basic:mostrar leds||` e desenhamos um **X**.

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

Pronto, agora podemos carregar esse programa para os dois micro:bits, e nos comunicar
via Código Morse! E então, consegue ter uma conversa com um amigo só em Código Morse?
Se errar, não se esqueça de agitar o micro:bit e recomeçar a palavra.
