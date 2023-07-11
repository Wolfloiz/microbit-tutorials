## Step 1

Vamos fazer um programa para testar nosso reflexo. Este jogo consiste em pressionar um botão
assim que qualquer LED do Micro:bit acender.

## Step 2

Primeiramente, crie uma variável chamada `||variables:funcionando||`, na aba
`||variables:Variáveis||`. Em seguida, adicione o bloco `||variables:definir funcionando para||` dentro do laço `||basic:no iniciar||`.
Vamos definir essa variável como `||logic:falso||`, que pode ser encontrado na aba `||logic:Lógica||`.

```blocks
let funcionando = false
```

## Step 3

Feito isso, dentro do laço `||basic:no iniciar||`, vamos adicionar um bloco de
`||basic:pausa||` com **2000ms**. Logo abaixo, vamos inserir o bloco `||led:plotar x y||`,
que se encontra na aba `||led:led||`.

```blocks
let funcionando = 0
funcionando = false
basic.pause(2000)
led.plot(0, 0)
```

## Step 4

Nos campos dos valores **x** e **y**, vamos colocar dois blocos `||math:escolher aleatório 0 até 10||` que se encontram na aba `||math:Matemática||`.
Altere os valores dos campos para **0** e **4**.
Abaixo deste comando, vamos redefinir a variável `||variables:funcionando||` para
`||logic:verdadeiro||`, que também se encontra na aba `||logic:Lógica||`.

```blocks
let funcionando = 0
funcionando = false
basic.pause(2000)
led.plot(randint(0, 4), randint(0, 4))
funcionando = true
```

## Step 5

Agora vamos fazer a parte interativa do jogo. Vá até a aba `||input:Input||` e adicione o laço `||input:no botão A pressionado||` ao código.
Dentro desse laço, vamos incluir um bloco `||basic:limpar tela||`, situado em `||basic:Básico||`, e a estrutura condicional `||logic:se-então-senão||` localizada em `||logic:Lógica||`.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    if (true) {

    } else {

    }
})
```

## Step 6

Vamos verificar se, quando pressionamos o botão, o jogo estava em andamento ou não.
Para isso, vamos substituir o bloco `||logic:verdadeiro||` pela variável `||variables:funcionando||`.

```blocks
input.onButtonPressed(Button.A, function () {
     basic.clearScreen()
    if (funcionando) {

    } else {

    }
})
```

## Step 7

Se apertarmos o botão e o jogo já estiver funcionando, vamos mostrar um rosto feliz dentro do `||logic:então||`.
Caso contrário, dentro do `||logic:senão||`, vamos exibir um rosto triste, usando blocos `||basic:mostrar leds||`
que se encontram na aba `||basic:Básico||`, e desenhando os rostos ao selecionar quais LEDs estarão acesos em cada caso.

```blocks
input.onButtonPressed(Button.A, function () {
		basic.clearScreen()
    if (funcionando) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
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

## Step 8

Agora já podemos testar a parte inicial do jogo do reflexo. Ele ainda é bem simples,
pois vamos adicionar outras funcionalidades. E aí, você está apertando antes da hora?

```blocks
let funcionando = 0
funcionando = false
basic.pause(2000)
led.plot(randint(0, 4), randint(0, 4))
funcionando = true
input.onButtonPressed(Button.A, function () {
		basic.clearScreen()
    if (funcionando) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
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
