```template
basic.forever(function () {
basic.showIcon(IconNames.Heart)
})
```

## Step 1

Agora que já aprendemos a usar os símbolos, vamos fazer um símbolo animado.
Vamos desenhar um coração batendo.

```blocks
basic.forever(function () {
basic.showIcon(IconNames.Heart)
})
```

## Step 2

Para representar o coração batendo, precisaremos colocar um outro bloco
`||basic:mostrar ícone||`, abaixo do primeiro, dentro do bloco
`||basic:sempre||`.

```blocks
basic.forever(function () {
basic.showIcon(IconNames.Heart)
basic.showIcon(IconNames.Heart)
})
```

## Step 3

Vamos agora mudar um dos dois blocos `||basic:mostrar ícone||`, trocando
o símbolo para o coração pequeno (o segundo símbolo da lista).

```blocks
basic.forever(function () {
    basic.showIcon(IconNames.SmallHeart)
    basic.showIcon(IconNames.Heart)
})
```

## Step 4

Pronto! Podemos agora carregar o código para o micro:bit e ver o
coração batendo!
