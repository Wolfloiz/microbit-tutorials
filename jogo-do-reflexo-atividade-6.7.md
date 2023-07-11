## Step 1

Neste tutorial, vamos fazer um jogo para podermos competir com um amigo e ver quem tem o reflexo
mais rápido!

## Step 2

Primeiramente, crie uma variável chamada `||variables:funcionando||`, na aba
`||variables:Variáveis||`. Em seguida, adicione o bloco `||variables:definir funcionando para||` dentro do laço `||basic:no iniciar||`.
Vamos definir essa variável como `||logic:falso||`, que pode ser encontrado na aba `||logic:Lógica||`.

```blocks
let funcionando = false
```

## Step 3

Acesse a aba `||input:Input||` e inclua o laço
`||input:no botão A pressionado||`. Altere de `||input:botão A||`
para `||input:botão B||`.

```blocks
let funcionando = false
input.onButtonPressed(Button.B, function () {
})
```

## Step 4

Feito isso, dentro do laço `||input:no botão B pressionado||`, vamos adicionar u
m bloco de
`||basic:pausa||` com **2000ms**. Logo abaixo, vamos inserir o bloco
`||led:plotar x y||`,
que se encontra na aba `||led:led||`.

```blocks
let funcionando = 0
funcionando = false
input.onButtonPressed(Button.B, function () {
basic.pause(2000)
led.plot(0, 0)
})
```

## Step 5

Nos campos dos valores **x** e **y**, vamos colocar dois blocos `||math:escolher aleatório 0 até 10||` que se encontram na aba `||math:Matemática||`.
Altere os valores dos campos para **0** e **4**.
Abaixo deste comando, vamos redefinir a variável `||variables:funcionando||` para
`||logic:verdadeiro||`, que também se encontra na aba `||logic:Lógica||`.

```blocks
let funcionando = 0
funcionando = false
input.onButtonPressed(Button.B, function () {
basic.pause(2000)
led.plot(randint(0, 4), randint(0, 4))
funcionando = true
})
```

## Step 6

Para fazer a contagem regressiva, vamos inserir 3 blocos `||basic:mostrar número||`
dentro do laço `||input:no botão B pressionado||`, antes de todos os outros que adicionamos no passo anterior.
Então, vamos mostrar os números **3**, **2** e **1**, nesta ordem. Abaixo destes três blocos, adicionamos um bloco `||basic:limpar tela||`,
localizado na aba `||basic:Básico||`.

```blocks
let funcionando = 0
funcionando = false
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(2000)
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
```

## Step 7

Porém, o jogo ainda está muito previsível. Para torná-lo mais desafiador, vamos incluir
um valor de pausa aleatório para não sabermos exatamente quando o LED irá acender.
Para isso, só devemos substituir o número **2000** dentro do bloco `||basic:pausa||` pelo bloco `||math:aleatório entre 1000 e 3000||`,
localizado na aba `||math:Matemática||`. Lembre-se de alterar o valores dentro deste comando para **1000** e **3000**.

```blocks
let funcionando = 0
funcionando = false
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
```

## Step 8

Em seguida, crie as variáveis `||variables:início||` e `||variables:fim||`.

## Step 9

Agora, dentro do laço `||input:no botão B pressionado||` e abaixo do bloco
`||led:plotar x y||`, adicione o bloco `||variables:definir início para 0||`.
Em seguida, defina `||variables:início||` como sendo igual ao tempo que o Micro:bit está
funcionando, usando o bloco `||input:tempo de execução (ms)||`, que se encontra na aba
`||input:Input-> mais||`.

```blocks

input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		início = input.runningTime()
		funcionando = true
})
```

## Step 10

Agora vamos fazer a parte interativa do jogo. Vá até a aba `||input:Input||` e adicione o laço `||input:no pin P0 pressionado||` ao código.
Dentro desse laço, vamos incluir um bloco `||basic:limpar tela||`, situado em `||basic:Básico||`, e a estrutura condicional `||logic:se-então-senão||` localizada em `||logic:Lógica||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.clearScreen()
    if (true) {

    } else {

    }
})
```

## Step 11

Vamos verificar se, quando pressionamos o botão, o jogo estava em andamento ou não.
Para isso, vamos substituir o bloco `||logic:verdadeiro||` pela variável `||variables:funcionando||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {
     basic.clearScreen()
    if (funcionando) {

    } else {

    }
})
```

## Step 12

Feito isso, dentro do laço `||input:no botão A pressionado||`, dentro do
`||logic:se-então-senão||` (entre o **se ... então** e o **senão**),
adicione o bloco `||variables:definir fim para 0||`. Defina `||variables:fim||` como sendo igual ao tempo que o Micro:bit está
funcionando, usando o bloco `||input:tempo de execução (ms)||`, que se encontra na aba
`||input:Input-> mais||`

```blocks
input.onPinPressed(TouchPin.P0, function () {
		basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()

    } else {

    }
})
```

## Step 13

Em seguida, inclua uma `||basic:pausa||` de um segundo (**1000ms**), logo abaixo de
`||variables:definir fim para||`.
Então utilize um bloco `||basic:mostrar número||`, abaixo da pausa, para mostrar quanto tempo levamos. O número exibido será uma operação matemática de
`||math:subtração||`, que pode ser encontrada na aba `||math:Matemática||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {
		basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()

				basic.pause(1000)
        basic.showNumber(0-0)
    } else {

    }
})
```

## Step 14

Dentro dos campos da operação, preencha com as varíaveis `||math:fim - inicio||`, localizadas na aba `||variables:Variáveis||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {
		basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()

				basic.pause(1000)
        basic.showNumber(fim-início)
    } else {

    }
})
```

## Step 15

Para incluirmos o segundo jogar, vamos copiar o laço `||input:no pin P0 pressionado||`
(com todo seu conteúdo), e alterar o pino de um dos laços para `||input:P1||`.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()

				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {


    }
})

input.onPinPressed(TouchPin.P1, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()

				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {


    }
})
```

## Step 16

Agora, para podermos visualizar quem teve o reflexo mais rápido e venceu,
usaremos o bloco `||basic:mostrar leds||`
que se encontra na aba `||basic:Básico||`. Dentro do laço `||input:no pin P0 pressionado||`,
adicione esse bloco acima da pausa
de **1000ms** desenhando
duas **retas verticais** acesas na esquerda da matriz, e outro bloco `||basic:mostrar leds||`
dentro do laço `||logic:senão||`, desenhando um pequeno **X**, também à esquerda da
matriz, indicando que se referem ao jogador daquele lado.

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

    }
})
input.onPinPressed(TouchPin.P1, function () {
    basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()

				basic.pause(1000)
        basic.showNumber(fim-inicio)
    } else {


    }
})
```

## Step 17

Em seguida, dentro do laço `||input:no pin P1 pressionado||` faça o mesmo, desenhando **retas verticais**
agora na direita da matriz, e o pequeno **X**, também do lado direito da matriz.

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
    }
})
```

## Step 18

Agora podemos competir com outras pessoas e descobrir quem tem o reflexo mais rápido!
