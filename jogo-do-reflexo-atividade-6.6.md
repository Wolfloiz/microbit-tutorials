```template
let funcionando = false
let inicio = 0
let fim = 0
let comeco_falso = false
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		comeco_falso = false
		funcionando = false
		basic.pause(randint(1000, 3000))
		if (comeco_falso == false) {
				led.plot(randint(0, 4), randint(0, 4))
				inicio = input.runningTime()
				funcionando = true
    }
})
input.onPinPressed(TouchPin.P0, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
            `)
				comeco_falso = true
    }
})
```

## Step 1

Neste tutorial, vamos modificar o jogo para podermos competir com um amigo e ver quem tem o reflexo
mais rápido!

## Step 2

Para incluirmos um segundo jogar, vamos copiar o laço `||input:no pin P0 pressionado||`
(com todo seu conteúdo), e alterar o pino de um dos laços para `||input:P1||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
            `)
				comeco_falso = true
    }
})

input.onPinPressed(TouchPin.P1, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
            `)
				comeco_falso = true
    }
})
```

## Step 3

Agora, para podermos visualizar quem teve o reflexo mais rápido e venceu, precisaremos
modificar os blocos `||basic:mostrar leds||` para alterar o que exibem. Dentro do laço `||input:no pin P0 pressionado||`,
altere o rosto feliz por duas **retas verticais** acesas na esquerda da matriz,
e o rosto triste por um pequeno **X**, também à esquerda da matriz, indicando que se referem ao jogador daquele lado.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            # # . . .
            # # . . .
            # # . . .
            # # . . .
            # # . . .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            # . # . .
            . # . . .
            # . # . .
            . . . . .
            `)
				comeco_falso = true
    }
})
input.onPinPressed(TouchPin.P1, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
            `)
				comeco_falso = true
    }
})
```

## Step 4

Em seguida, dentro do laço `||input:no pin P1 pressionado||` faça o mesmo, substituindo o rosto feliz por duas **retas verticais**
agora na direita da matriz, e o rosto triste por um pequeno **X**, também do lado direito da matriz.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            # # . . .
            # # . . .
            # # . . .
            # # . . .
            # # . . .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            # . # . .
            . # . . .
            # . # . .
            . . . . .
            `)
				comeco_falso = true
    }
})
input.onPinPressed(TouchPin.P1, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            . . . # #
            . . . # #
            . . . # #
            . . . # #
            . . . # #
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {
        basic.showLeds(`
            . . . . .
            . . # . #
            . . . # .
            . . # . #
            . . . . .
            `)
				comeco_falso = true
    }
})
```

## Step 5

Agora podemos competir com outras pessoas e descobrir quem tem o reflexo mais rápido!
