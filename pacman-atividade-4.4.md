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
})
```

## Step 1

Neste tutorial, vamos permitir que o `||game: sprite||` se mova também na vertical.
Para isso, duplique os dois laços `||logic: se verdadeiro então||` inteiros, e os posicione abaixo dos anteriores.
Certifique-se de que estejam abaixo, e não dentro, dos anteriores.

```blocks
let pacman = game.createSprite(2, 2)
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

Em seguida, altere todos os quatro **X** dentro dos dois últimos laços `||logic: se verdadeiro então||` para **Y**.
Confira se foram feitas quatro alterações, dentro dos blocos redondos de `||input: aceleração||` e nos que mudam a posição do `||game: sprite||`.

```blocks
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

## Step 3

Pronto! Agora podemos carregar o programa para o Micro:bit, e mover
o `||game: sprite||` em qualquer direção apenas inclinando a plaquinha.
