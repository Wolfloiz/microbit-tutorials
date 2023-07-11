```template
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

## Step 1

Nesta atividade, vamos incluir um botão para iniciar uma contagem regressiva que indica o começo do jogo.

## Step 2

Acesse a aba `||input:Input||` e inclua o laço `||input:no botão A pressionado||`. Altere de `||input:botão A||` para `||input:botão B||`.
Em seguida, copie todos os comandos que se encontram no laço `||basic:no iniciar||` para o laço
`||input:no botão B pressionado||`. Por fim, exclua os blocos que estavam em `||basic:no iniciar||`, exceto o bloco `||variables:definir funcionando para falso||`.

```blocks
let funcionando = 0
funcionando = false
input.onButtonPressed(Button.B, function () {
		funcionando = false
		basic.pause(2000)
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
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

## Step 3

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

## Step 4

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

## Step 5

Agora podemos testar o jogo. Ele está um pouco mais desafiador e completo, já que
podemos reiniciá-lo ao pressionar o `||input:botão B||`. E então, consegue acertar
quantas vezes sem errar?

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
