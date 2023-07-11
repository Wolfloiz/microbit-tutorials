```template
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
    }
})
input.onButtonPressed(Button.B, function () {
    if (Próximo_Número > Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
    }
})
let Próximo_Número = 0
let Número = 0
Número = randint(0, 100)
Próximo_Número = randint(0, 100)
basic.showNumber(Número)

```

## Step 1

Vamos criar uma nova variável: **Pontuação**.

## Step 2

Adicione um novo bloco de `||variables:definição||` da variável `||variables:Pontuação||`.
`||basic:Ao iniciar||`, `||variables:Pontuação||` deve ser
igual a zero.

```blocks
let Pontuação = 0
let Número = randint(0, 100)
Próximo_Número = randint(0, 100)
basic.showNumber(Número)
```

## Step 3

Vamos incluir no bloco `||Input:botão A||` o bloco
`||variables: alterar Pontuação por 1||`, para aumentar a pontuação em 1
ao acertar.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
         basic.showNumber(Próximo_Número)
    }
})
```

## Step 4

Vamos repetir o processo para o bloco `||Input:botão B||` o bloco
`||variables: alterar Pontuação por 1||`, para aumentar a pontuação em 1
ao acertar.

```blocks
input.onButtonPressed(Button.B, function () {
    if (Próximo_Número > Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
         basic.showNumber(Próximo_Número)
    }
})
```

## Step 5

Por fim, devemos informar ao jogador qual foi sua
`||variables:Pontuação||` atingida, ou seja, quantas vezes
ele acertou as previsões.
Faremos isso incluindo o bloco`||basic:mostrar string||`
com as letras ‘**PTS**’, seguido do comando para
`||basic:mostrar número||` `||variables:Pontuação||`, dentro do laço
`||Logic:senão||`

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
        basic.showString("PTS= ")
        basic.showNumber(Pontuação)
    }
})
```

## Step 6

Como as ações que devem ser tomadas ao errar são as mesmas para o `||Input:botão A||` e para o `||Input:botão B||`,
podemos apenas duplicar os blocos dentro do laço `||Logic:senão||` do `||Input:botão A||` e movê-los para o do `||Input:botão B||`.

```blocks
input.onButtonPressed(Button.B, function () {
    if (Próximo_Número > Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
        basic.showString("PTS= ")
        basic.showNumber(Pontuação)
    }
})
```
