

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

Vamos agora modificar o jogo para, ao invés de testar o reflexo somente do dedo, 
testarmos o reflexo do braço todo. Para fazer isso, primeiro devemos fazer a montagem 
do "tabuleiro".

## Step 2

O funcionamento do jogo continuará sendo o mesmo, quando apertarmos o botão B, vai 
começar uma contagem regressiva e o jogo começa. A mudança vai ser que agora, ao invés 
de apertarmos o botão A quando o LED aparecer, vamos ter que apertar o pino P0.

## Step 3

Para fazer essa mudança, vamos primeiro adicionar o bloco 
``||input:no pin P0 pressionado||``. Agora basta pegar todos os blocos que estão dentro 
do bloco ``||input:no botão A pressionado||`` e passar para o bloco ``||input:no pin P0 pressionado||``. 
Em seguida, deletamos o bloco ``||input:no botão A pressionado||``.

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

Agora podemos testar o reflexo do braço todo. E então, qual reflexo é melhor? O do 
seu dedo ou o do braço todo?








