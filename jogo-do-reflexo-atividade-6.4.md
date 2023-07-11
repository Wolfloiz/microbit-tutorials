```template
let funcionando = false
let inicio = 0
let fim = 0
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		inicio = input.runningTime()
		funcionando = true
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
    }
})
```

## Step 1

Nesta atividade, vamos incluir uma funcionalidade para identificar que o botão foi pressionado antes do LED acender,
chamada "Começo Falso".

## Step 2

Primeiramente, crie uma variável `||variables:comeco_falso||`.

## Step 3

Agora, dentro do laço `||input:no botão B pressionado||` e abaixo do bloco `||basic:limpar tela||`,
adicione o bloco `||variables:definir comeco_falso para falso||`.

```blocks
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		comeco_falso = false
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		inicio = input.runningTime()
		funcionando = true
})
```

## Step 4

Em seguida, ainda dentro do laço `||input:no botão B pressionado||` e abaixo da
`||basic:pausa||`, insira um laço `||logic:se-então||`, localizado na aba `||logic:Lógica||`.

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showNumber(3)
    basic.showNumber(2)
    basic.showNumber(1)
    basic.clearScreen()
    comeco_falso = false
    funcionando = false
    basic.pause(randint(1000, 3000))
    if (true) {

    }
    led.plot(randint(0, 4), randint(0, 4))
    inicio = input.runningTime()
    funcionando = true
})
```

## Step 5

Dentro do campo triangular **verdadeiro** insira a um comparador `||logic:0=0 ||` localizado na aba `||logic:Lógica||`.
Na comparação, verifique se a variável `||logic:comeco_falso = falso||`.
O bloco triangular `||logic:falso||` também pode ser encontrado na aba `||logic:Lógica||`.

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showNumber(3)
    basic.showNumber(2)
    basic.showNumber(1)
    basic.clearScreen()
    comeco_falso = false
    funcionando = false
    basic.pause(randint(1000, 3000))
    if (comeco_falso == false) {

    }
    led.plot(randint(0, 4), randint(0, 4))
    inicio = input.runningTime()
    funcionando = true
})
```

## Step 6

Feito isso, mova os blocos `||led:plotar x y||`, `||variables:definir inicio||` e
`||variables:definir funcionando||` para dentro do laço `||logic:se-então||`.

```blocks
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
```

## Step 7

Por fim, adicione um bloco `||variables:definir comeco_falso para||` `||logic:verdadeiro||`,
dentro do laço `||logic:se-então-senão||`, abaixo do rosto triste presente no laço `||input:no botão A pressionado||`.

```blocks
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

## Step 8

Pronto! Na próxima atividade vamos deixar de usar os botões e pasaremos a usar os pinos do Micro:bit
como entrada para nosso jogo. Assim, vamos conseguir construir um "botão" maior que podemos tocar mais rapidamente
como papel alumínio, por exemplo.

```blocks
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
