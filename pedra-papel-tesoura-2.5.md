```template
let aleatório = randint(1, 3)
if (aleatório == 1) {
    basic.showIcon(IconNames.Happy)
} else if (aleatório == 2) {
    basic.showIcon(IconNames.Sad)
} else {
    basic.showIcon(IconNames.Surprised)
}

```

## Step 1

Com base no último programa que fizemos, vamos agora criar um jogo de
pedra, papel ou tesoura. Primeiro, precisamos dos símbolos para pedra, papel e
tesoura. Eles não se encontram prontos, então devemos desenhar usando o bloco
`||basic:mostrar leds||`.

```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
} else if (aleatório == 2) {
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
} else {
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
}
```

## Step 2

Desenhe seus símbolos para pedra, papel e tesoura.

```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
    basic.showLeds(`
        . # # # .
        # # # # #
        # # # # #
        # # # # #
        . # # # .
        `)
} else if (aleatório == 2) {
    basic.showLeds(`
        # # # # .
        # . . # .
        # . . # .
        # . # # .
        # # # . .
        `)
} else {
basic.showLeds(`
    . . # . .
    . . # . .
    # # # # #
    # # # . .
    . # # . .
    `)
}
```

## Step 3

Pronto! Agora temos um jogo simples de Pedra, Papel ou Tesoura. Toda vez que
ligarmos o micro:bit, ele vai escolher Pedra, Papel ou Tesoura. Tente ganhar do micro:bit!!!
