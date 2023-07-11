```template
let funcionando = false
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

## Step 1

Nesta atividade, vamos incluir um medidor de tempo para exibir quanto tempo levamos para pressionar
o botão depois que o LED apareceu.

## Step 2

Primeiramente, crie as variáveis `||variables:início||` e `||variables:fim||`.

## Step 3

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

## Step 4

Feito isso, dentro do laço `||input:no botão A pressionado||` e acima do rosto feliz,
repita o procedimento, mas, agora, para a variável `||variables:fim||`. Defina `||variables:fim||` como sendo igual ao tempo que o Micro:bit está
funcionando, usando o bloco `||input:tempo de execução (ms)||`, que se encontra na aba
`||input:Input-> mais||`

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

Em seguida, inclua uma `||basic:pausa||` de um segundo (**1000ms**) depois do **rosto feliz**.
Então utilize um bloco `||basic:mostrar número||`, para mostrar quanto tempo levamos. O número exibido será uma operação matemática de
`||math:subtração||`, que pode ser encontrada na aba `||math:Matemática||`.

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
        basic.showNumber(0-0)
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

## Step 6

Dentro dos campos da operação, preencha com as varíaveis `||math:fim - inicio||`, localizadas na aba `||variables:Variáveis||`.

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
        basic.showNumber(fim-início)
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

## Step 7

Agora, já somos capazes de medir quanto tempo levamos para pressionar o `||input:botão A||`
depois que o LED acendeu. Passe seu código para o Micro:bit e tente reduzir sem tempo de reação!

```blocks
let funcionando = false
funcionando = false
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
        basic.showNumber(fim-início)
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
