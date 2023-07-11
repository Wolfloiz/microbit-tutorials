```template
let pacman = game.createSprite(2, 2)
```

## Step 1

Agora que temos o `||game:sprite||` criado, vamos aprender a movê-lo horizontalmente.
Adicione os laços `||input:no botão A pressionado||` e `||input:no botão B pressionado||`,
que se encontram na aba `||input:Input||`.

```blocks
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {

})
input.onButtonPressed(Button.B, function () {

})
```

## Step 2

Em seguida, selecione o bloco `||game:pacman alterar x por 1||`, que se
encontra na aba `||game:Jogo||` na seção **Avançado**, e o posicione dentro dos laços
`||input:no botão A pressionado||` e `||input:no botão B pressionado||`.

```blocks
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    pacman.change(LedSpriteProperty.X, 1)
})
input.onButtonPressed(Button.B, function () {
    pacman.change(LedSpriteProperty.X, 1)
})
```

## Step 3

Com esse código, ao pressionarmos o `||input:botão A||` ou `||input:botão B||`, o `||game:sprite||` vai mover para
sempre para a direita. Então, vamos então alterar o bloco `||game:pacman alterar x por 1||`,
dentro de `||input:no botão A pressionado||` para **-1**, fazendo o
`||game:sprite||` ir para a esquerda quando apertarmos o `||input:botão A||`.

```blocks
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    pacman.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    pacman.change(LedSpriteProperty.X, 1)
})
```

## Step 4

Agora, podemos ver a vantagem de se usar o `||game:sprite||`. Se tivéssemos
acionados os LEDs normalmente, seria muito mais complicado movê-los. Mas, usando o `||game:sprite||`
podemos facilmente movimentá-lo usando controles. Com o código finalizado,
podemos carregá-lo para o micro:bit e brincar de mover o `||game:sprite||` de um lado pra outro.
