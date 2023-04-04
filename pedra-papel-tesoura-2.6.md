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

Com base no último programa que fizemos, vamos agora colocar um bloco para 
jogar novamente, sem ter que ligar o micro:bit novamente. Adicione o bloco 
``||input:agitar||``, que pode ser encontrado na aba ``||input:input||``.

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

Agora iremos mover todos os blocos que estão dentro do bloco ``||basic:no iniciar||``
 para o bloco ``||input:agitar||``. Para facilitar, pode apenas arrastar o bloco 
 ``||variables:definir aleatório como||``, e todos os outros blocos serão movidos também.


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
micro:bit para que ele escolha Pedra, Papel ou Tesoura. Tente ganhar de seu 
micro:bit, ou jogo com seu micr:bit contra outra pessoa.