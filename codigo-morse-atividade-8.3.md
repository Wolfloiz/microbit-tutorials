## Step 1

Neste tutorial, vamos aprender a usar Micro:bits para conversar usando Código Morse.
Para a comunicação acontecer, um Micro:bit vai enviar a mensagem e o outro vai receber. Primeiramente, vamos
programar o Micro:bit (M1).

## Step 2

vamos selecionar o bloco `||radio:definir grupo do rádio 1||`, na categoria
`||radio:Rádio||`, e colocá-lo dentro do laço `||basic:no iniciar||`. Esse bloco
serve para garantir que todos os micro:bits dentro desse mesmo grupo de rádio estejam conectados uns com
os outros. Portanto, certifique-se de que o grupo do seu Micro:bit seja diferente dos outros grupos da sua sala de aula.

Altere o número do grupo de **1** para **255**, ou outro número próximo deste valor.

```blocks
radio.setGroup(255)
```

## Step 3

Agora, vamos determinar a força com que o micro:bit irá transmitir informações. Isso
determina a distância da comunicação. Devemos escolher esse número de acordo com o tamanho
do lugar escolhido para esconder/procurar o tesouro. Para isso, vamos adicionar o bloco
`||radio:conjunto de rádio transmite energia 6||` que se encontra na
aba `||radio:Rádio->mais||`, e colocá-lo no laço `||basic:no iniciar||`.
Assim, a configuração da comunicação do primeiro micro:bit está feita. Mas o que vamos comunicar?

```blocks
radio.setGroup(255)
radio.setTransmitPower(7)
```

## Step 4

Para enviar mensagens em Código Morse, precisaremos de três comandos: um para enviar um traço,
outro para enviar um ponto, e um último para mostrar que a letra já acabou e vamos passar para a
próxima. Então, vamos adicionar os três laços `||input:no botão A pressionado||`,
`||input:no botão B pressionado||` e `||input:no botão A+B pressionado||`.

```blocks
input.onButtonPressed(Button.A, function () {

})
input.onButtonPressed(Button.B, function () {

})
input.onButtonPressed(Button.AB, function () {

})
radio.setGroup(255)
radio.setTransmitPower(7)
```

## Step 5

Dentro do laço `||input:no botão A pressionado||`, vamos adicionar o bloco
`||basic:mostrar leds||` e desenhar um quadrado 3x3 para representar um ponto. Já
no laço `||input:no botão B pressionado||`, vamos adicionar outro bloco
`||basic:mostrar leds||` para desenhar uma linha de 3 leds acesos para representar o traço.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
})
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        . . . . .
        . . . . .
        . # # # .
        . . . . .
        . . . . .
        `)
})
```

## Step 6

Por fim, no laço `||input:no botão A+B pressionado||` vamos adicionar o bloco
`||basic:mostrar leds||` e desenhar uma seta para a direita, representando que já
acabamos a palavra e estamos passando para a próxima.

```blocks
input.onButtonPressed(Button.AB, function () {
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
})
```

## Step 7

Mas e agora? Como iremos transmitir as letras e palavras que estamos digitando para
o outro micro:bit? Para isso, usaremos o bloco `||radio:rádio envia número||`
que pode ser encontrado na categoria `||radio:Rádio||`. Adicionamos este bloco abaixo de cada
um dos três desenhos. No caso do **ponto**, enviaremos o número **0**, no caso do **traço** enviaremos
o número **1**, e para passar pra **próxima palavra**, enviaremos o número **2**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    radio.sendNumber(0)
})
input.onButtonPressed(Button.AB, function () {
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
    radio.sendNumber(2)
})
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        . . . . .
        . . . . .
        . # # # .
        . . . . .
        . . . . .
        `)
    radio.sendNumber(1)
})
radio.setGroup(255)
radio.setTransmitPower(7)
```

## Step 8

Para garantir que o sinal foi transmitido, e podermos visualizar qual símbolo enviamos, vamos
adicionar os blocos `||basic:pausa (ms) 100||` e `||basic:limpar tela||`
abaixo de cada bloco `||radio:rádio envia número||` nos três laços.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    radio.sendNumber(0)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.AB, function () {
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
    radio.sendNumber(2)
    basic.pause(100)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        . . . . .
        . . . . .
        . # # # .
        . . . . .
        . . . . .
        `)
    radio.sendNumber(1)
    basic.pause(100)
    basic.clearScreen()
})
radio.setGroup(255)
radio.setTransmitPower(7)
```

## Step 9

Agora que configuramos o primeiro Micro:bit para enviar o código,
ainda devemos programar o segundo para receber as mensagens. Vamos lá!
