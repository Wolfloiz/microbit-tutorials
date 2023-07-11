```template
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    pacman.change(LedSpriteProperty.X, -1)
})
input.onButtonPressed(Button.B, function () {
    pacman.change(LedSpriteProperty.X, 1)
})
```

## Step 1

Neste tutorial, vamos modificar o programa anterior para usarmos o acelerômetro para movimentar o `||game: sprite||`,
não mais os botões. Para isso, usaremos dois laços `||logic:se verdadeiro então||`,
que se encontram na aba `||logic:Lógica||`. Posicione-os dentro do laço `||basic:sempre||`.

```blocks
let pacman = game.createSprite(2, 2)
basic.forever(function () {
    if (true) {

    }
    if (true) {

    }
})
```

## Step 2

Em seguida, retorne à aba `||logic:Lógica||` e selecione dois blocos comparadores `||logic:0 < 0||`.
Eles devem ser inseridos dentro do laço `||logic:se verdadeiro então||`, no campo triangular **verdadeiro**.

```blocks
let pacman = game.createSprite(2, 2)
basic.forever(function () {
    if (0<0) {

    }
    if (0<0) {

    }
})
```

## Step 3

Agora, acesse a aba `||input:Input||` e escolha o bloco redondo `||input:aceleração (mg) x||`.
Ele deve ser inserido no primeiro espaço dos dois blocos de comparação, em ambos os laços `||logic:se verdadeiro então||`.
Assim, teremos: `||logic:aceleração (mg) x < 0||`.
Por fim, altere o sinal do segundo comparador de **<** para **>**.

```blocks
let pacman = game.createSprite(2, 2)
basic.forever(function () {
    if (input.acceleration(Dimension.X) < 0) {

    }
    if (input.acceleration(Dimension.X) > 0) {

    }
})
```

## Step 4

Feito isso, arraste tudo que está dentro do laço `||input:no botão A pressionado||`
e solte dentro do primeiro laço `||logic:se verdadeiro então||`.
Em seguida, faça o mesmo para o comando que está dentro do laço `||input:no botão B pressionado||`,
mas solte no segundo `||logic:se verdadeiro então||`.

```blocks
let pacman = game.createSprite(2, 2)
basic.forever(function () {
   if (input.acceleration(Dimension.X) < 0) {
   pacman.change(LedSpriteProperty.X, -1)
   }
   if (input.acceleration(Dimension.X) > 0) {
    pacman.change(LedSpriteProperty.X, 1)
   }
})
```

## Step 5

Confira se no laço em que temos `||logic:aceleração (mg) x < 0||`, estamos alterando a coordenada **x** do `||game: sprite||` com **-1**.
E, de forma oposta, no laço em que `||logic:aceleração (mg) x > 0||`, estamos alterando a coordenada **x** do `||game: sprite||` com **1**.

```blocks
let pacman = game.createSprite(2, 2)
basic.forever(function () {
   if (input.acceleration(Dimension.X) < 0) {
   pacman.change(LedSpriteProperty.X, -1)
   }
   if (input.acceleration(Dimension.X) > 0) {
    pacman.change(LedSpriteProperty.X, 1)
   }
})
```

## Step 6

Para auxiliar a visualização, adicione um bloco `||basic: pausa||`
de **100ms** antes dos `||logic:se verdadeiro então||`, dentro do laço `||basic: sempre||`,
fazendo com que o `||game: sprite||` se mova mais devagar.

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
})
```

## Step 7

Pronto! Agora podemos carregar o programa para o Micro:bit e mover
o `||game: sprite||` ao inclinar a placa para esquerda e para a direita!
