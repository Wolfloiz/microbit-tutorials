```template
let pacman = game.createSprite(2, 2)
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)
    }
    if (input.acceleration(Dimension.Y) < 0) {
    pacman.change(LedSpriteProperty.Y, -1)
    }
    if (input.acceleration(Dimension.Y) > 0) {
     pacman.change(LedSpriteProperty.Y, 1)
    }
})
```

## Step 1

Como já temos o `||variables: pacman||` criado e já é possível movimentá-lo, vamos apenas
criar a moeda que deve ser coletada. Para isso, crie uma variável chamada `||variables: moeda||` na aba
`||variables: Variáveis||`. Duplique o bloco `||variables: definir pacman para||`, altere a variável de
`||variables: pacman||` para `||variables: moeda||`, e o posicione abaixo do original,
ainda dentro do laço `||basic: no iniciar||`.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(2, 2)
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)
    }
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)
    }
})
```

## Step 2

Em seguida, vá até a aba `||Math: matemática||`, selecione o bloco `||Math: escolher aleatório entre||` e
altere os valores para **0** e **4**. Então, adicione dois blocos como este dentro dos campos das coordenadas de de
`||variables: definir moeda para||`, para fazer a moeda apareça em uma posição aleatória ao iniciar.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(randint(0, 4), randint(0, 4))
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)
    }
    if (input.acceleration(Dimension.Y) < 0) {
    pacman.change(LedSpriteProperty.Y, -1)
    }
    if (input.acceleration(Dimension.Y) > 0) {
     pacman.change(LedSpriteProperty.Y, 1)
    }
})
```

## Step 3

Como o código para mover o `||variables: pacman||` já está pronto, resta apenas
fazer a moeda desaparecer e uma nova aparecer em outro lugar,
quando o `||variables: pacman||` tocar a `||variables: moeda||`.
Para isso, adicione mais um laço `||logic: se verdadeiro então||`, que se encontra na aba `||logic: Lógica||`, dentro do laço `||basic: sempre||`.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(randint(0, 4), randint(0, 4))
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
        pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
        pacman.change(LedSpriteProperty.X, 1)
    }
    if (input.acceleration(Dimension.Y) < 0) {
        pacman.change(LedSpriteProperty.Y, -1)
    }
    if (input.acceleration(Dimension.Y) > 0) {
        pacman.change(LedSpriteProperty.Y, 1)
    }
    if (true) {

    }
})
```

## Step 4

Em seguida, vá até a aba `||game: Jogo||` e insira o bloco triangular `||game: is ... touching ...||` no campo **verdadeiro** do laço `||logic: Se verdadeiro então||`.
Altere os campos redondos deste bloco para `||variables: pacman||` e `||variables: moeda||`.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(randint(0, 4), randint(0, 4))
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
        pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
        pacman.change(LedSpriteProperty.X, 1)
    }
    if (input.acceleration(Dimension.Y) < 0) {
        pacman.change(LedSpriteProperty.Y, -1)
    }
    if (input.acceleration(Dimension.Y) > 0) {
        pacman.change(LedSpriteProperty.Y, 1)
    }
    if (pacman.isTouching(moeda)) {

    }
})
```

## Step 5

Agora, dentro do laço `||logic: Se verdadeiro então||`, adicione o bloco `||game: delete sprite||`, presente na aba `||game:Jogo||`.
Altere o campo para a variável `||variables: moeda||`, para deletar a moeda.
Por fim, copie o bloco `||variables: definir moeda para||`, que se encontra no
laço `||basic: no iniciar||` e posicione o novo dentro do `||logic: Se verdadeiro então||`,
para criar uma nova moeda em uma posição aleatória.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(randint(0, 4), randint(0, 4))
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
        pacman.change(LedSpriteProperty.X, -1)
    }
    if (input.acceleration(Dimension.X) > 0) {
        pacman.change(LedSpriteProperty.X, 1)
    }
    if (input.acceleration(Dimension.Y) < 0) {
        pacman.change(LedSpriteProperty.Y, -1)
    }
    if (input.acceleration(Dimension.Y) > 0) {
        pacman.change(LedSpriteProperty.Y, 1)
    }
    if (pacman.isTouching(moeda)) {
        moeda.delete()
        moeda = game.createSprite(randint(0, 4), randint(0, 4))
    }
})

```

## Step 6

Pronto! Já podemos carregar o programa para o Micro:bit. Se quiser experimentar com o código,
tente variar o tempo da pausa para observar a velocidade do Pac-Man se alterando.
