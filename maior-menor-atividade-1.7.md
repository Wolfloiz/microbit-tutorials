```template
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
        basic.showString("PTS=")
        basic.showNumber(Pontuação)
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
        basic.showString("PTS=")
        basic.showNumber(Pontuação)
    }
})
let Próximo_Número = 0
let Número = 0
let Pontuação = 0
Pontuação = 0
Número = randint(0, 100)
Próximo_Número = randint(0, 100)
basic.showNumber(Número)


```

## Step 1

Precisamos indicar ao jogador que o jogo começou! Para isso, vamos
adicionar o bloco `||basic:mostrar string||` que exibirá uma
palavra na matriz de LEDs.
`||basic:No iniciar||`,
mostraremos a mensagem **"VAI!"**, que deve ser digitada dentro do
bloco `||basic:mostrar string||`.

```blocks
basic.showString("VAI!")
let Pontuação = 0
let Número = randint(0, 100)
let Próximo_Número = randint(0, 100)
basic.showNumber(Número)
```

## Step 2

Vamos agora adicionar a opção de reiniciar o jogo ao apertar os botões A e B
ao mesmo tempo.
Os passos que devem ser executados são exatamente
iguais àqueles que definimos no nosso laço `||Basic:no iniciar||`.
Então, podemos duplicá-los e inseri-los dentro de um laço
`||Input: no botão A+B pressionado||`.

```blocks
input.onButtonPressed(Button.AB, function () {
    basic.showString("VAI!")
    Pontuação = 0
    Número = randint(0, 100)
    Próximo_Número = randint(0, 100)
    basic.showNumber(Número)
})
```
