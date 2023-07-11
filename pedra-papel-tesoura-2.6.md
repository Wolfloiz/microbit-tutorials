```template
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

## Step 1

A partir do último programa que fizemos, vamos criar uma forma de sortear
um novo ícone sem precisarmos reiniciar o Micro:bit. Para isso, adicione o laço
`||input:agitar||`, que pode ser encontrado na aba `||input:input||`.

```blocks
input.onGesture(Gesture.Shake, function () {

})

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

## Step 2

Agora, mova todos os blocos que estão dentro do laço `||basic:no iniciar||`
para o laço`||input:agitar||`. Para facilitar, apenas arraste o primeiro bloco
`||variables:definir aleatório como||`, e todos os outros comandos serão movidos juntos.

```blocks
input.onGesture(Gesture.Shake, function () {
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
})

```

## Step 3

Pronto! Agora temos um jogo de Pedra, Papel ou Tesoura. Basta sacudir o
Micro:bit para que ele escolha uma alternativa. Tente ganhar de seu
próprio Micro:bit, ou jogue contra outra pessoa.
