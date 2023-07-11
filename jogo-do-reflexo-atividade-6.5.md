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
input.onButtonPressed(Button.A, function () {
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

Vamos modificar o jogo para que usarmos um tabuleiro com "placas" que podemos tocar para testar o nosso reflexo.
Para fazer isso, primeiro devemos fazer a montagem do circuito. Apesar de programarmos apenas para um jogador neste tutorial,
o tabuleiro que será construído já comporta dois jogadores, pois este será nosso próximo desafio.

## Step 2

O funcionamento do jogo continuará sendo o mesmo, quando pressionarmos o botão B, uma contagem
regressiva vai se iniciar e, em seguida, o jogo começa. A única mudança é que, agora, vamos ter que tocar a placa conectada ao pino P0,
não mais o `||input:Botão A||` do Micro:bit.

## Step 3

Para fazer essa mudança, primeiramente, adicione o laço `||input:no pin P0 pressionado||`.
Feito isso, passe todos os blocos que estão dentro do laço `||input:no botão A pressionado||` para o laço `||input:no pin P0 pressionado||` que acabou de adicionar.
Em seguida, delete o laço `||input:no botão A pressionado||`.

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
```

## Step 4

Desse modo, conseguimos testar o reflexo tocando na placa do tabuleiro. E então, qual você consegue ser mais rápido?
Pressionando o botão do Micro:bit ou a placa?
