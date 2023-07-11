## Step 1

Neste tutorial, vamos aprender a usar Micro:bits para conversar usando Código Morse.
Para a comunicação acontecer, cada Micro:bit deve ser capaz de enviar e receber as mensagens.

## Step 2

Vamos selecionar o bloco `||radio:definir grupo do rádio 1||`, na categoria
`||radio:Rádio||`, e colocá-lo dentro do laço `||basic:no iniciar||`.
Esse bloco
serve para garantir que todos os micro:bits dentro desse mesmo grupo
de rádio estejam conectados uns com
os outros. Portanto, certifique-se de que o grupo do seu Micro:bit seja
diferente dos outros grupos da sua sala de aula.

Altere o número do grupo de **1** para **255**, ou outro número próximo
deste valor.

```blocks
radio.setGroup(255)
```

## Step 3

Agora, vamos determinar a força com que o micro:bit irá transmitir informações. Isso
determina a distância da comunicação. Devemos escolher esse número de acordo com o tamanho
do lugar escolhido para esconder/procurar o tesouro. Para isso, vamos adicionar o bloco
`||radio:conjunto de rádio transmite energia 6||` que se encontra na
aba `||radio:Rádio->mais||`, e colocá-lo no laço `||basic:no iniciar||`.
Assim, a configuração da comunicação do primeiro micro:bit está feita. Mas o que vamos
comunicar?

```blocks
radio.setGroup(255)
radio.setTransmitPower(7)
```

## Step 4

Para enviar mensagens em Código Morse, precisaremos inicialmente de três
comandos: um para enviar um traço,
outro para enviar um ponto, e um último para mostrar que a
letra já acabou e vamos passar para a
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

Agora temos que fazer a parte do código responsável por receber a informação de
outro micro:bit e mostrar essas informações na tela, de forma a possibilitar a
comunicação.

## Step 10

Vamos então adicionar o laço `||radio:ao receber rádio receivedNumber||`,
que pode ser encontrado na aba `||radio:Rádio||`.
Esse bloco executa tudo que está dentro dele quando recebe um número de outro Micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {

})
```

## Step 11

Feito isso, dentro do laço `||radio:ao receber rádio receivedNumber||`, vamos adicionar
o laço condicional `||logic:se-então-senão||`, que está na aba
`||logic:Lógica||`. Em seguida, devemos clicar no símbolo `||logic:+||` no canto
inferior na esquerda do bloco `||logic:se-então-senão||` para adicionar mais uma condição.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (true) {

    } else if (false) {

    } else {

    }
})
```

## Step 12

Agora, adicionamos os comparadores lógicos ao laço `||logic:se-então-senão||`.
Os blocos comparadores podem ser encontrados na aba `||logic:Lógica||`. A primeira
condição será `||logic:receivedNumber = 0||`, e a segunda será
`||logic:receivedNumber = 1||`. Para incluir o bloco `||radio:receivedNumber||`,  
vamos arrastar _(clique sobre ele e mova o mouse)_ a variável `||variables:receivedNumber||` do laço
`||radio:ao receber rádio receivedNumber||`.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {

    } else if (receivedNumber == 1) {

    } else {

    }
})
```

## Step 13

Em seguida, vamos utilizar a estrutura condicional para mostrar o símbolo (**ponto**, **traço**
ou **seta**) na tela, de acordo com o número recebido. Se o número recebido - `||variables:receivedNumber||` - for igual a **zero**,
mostraremos o **ponto**, se for igual a **1**, mostraremos o **traço**. Por fim, se não for nenhum dos dois, mostraremos a **seta**.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
    } else {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
    }
})
```

## Step 14

Finalmente, vamos adicionar um bloco de `||basic:pausa||` e um para `||basic:limpar tela||`
abaixo do `||logic:se-então-senão||`, para termos tempo de ver o símbolo nos LEDs, e
depois apagá-lo, para esperarmos o próximo.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
    } else {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
    }
    basic.pause(100)
    basic.clearScreen()
})
radio.setGroup(255)
```

## Step 15

E se apertarmos um botão errado por acidente? Precisamos avisar a pessoa que estamos
nos comunicando que erramos, e então, começar a escrever a palavra novamente! Mas como fazemos isso?

## Step 16

Da mesma forma que podemos escolher enviar um ponto, traço ou próxima palavra, também podemos enviar uma informação que significa reiniciar palavra. Para isso, vamos começar adicionando o laço
`||input:em agitar||`, localizado na categoria `||input:input||`.
Assim, sempre que quisermos reiniciar a palavra, vamos precisar agitar o micro:bit.

```blocks
input.onGesture(Gesture.Shake, function () {

})
```

## Step 17

Em seguida, coloque os mesmos blocos que estão dentro de `||input:no botão A pressionado||`, dentro também do laço `||input:em agitar||`.
Para facilitar, podemos fazer isso copiando e colando todo o laço, ou duplicando os blocos.

```blocks
input.onGesture(Gesture.Shake, function () {
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
```

## Step 18

Agora, vamos mudar tanto o símbolo exibido, quanto o número enviado ao agitarmos o micro:bit.
Dentro do laço `||input:em agitar||`, modificamos o bloco `||basic:mostrar leds||`
para exibir um **X**. Já no bloco `||radio:rádio envia número 0||`, vamos trocar o número **0** pelo número **3**.

```blocks
input.onGesture(Gesture.Shake, function () {
	basic.showLeds(`
        # . . . #
        . # . # .
        . . # . .
        . # . # .
        # . . . #
        `)
    radio.sendNumber(3)
    basic.pause(100)
    basic.clearScreen()
})
```

## Step 19

Assim, já terminamos a parte de enviar a mensagem para reiniciar a palavra. Porém, ainda falta modificar a
parte de receber essa informação.

## Step 20

No laço `||logic:se-então-senão||` vamos clicar no símbolo `||logic:+||`
que fica na extremidade inferior do bloco para acrescentar uma condição.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
    } else if (false) {

    } else {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
    }
    basic.pause(100)
    basic.clearScreen()
})
```

## Step 21

Neste laço condicional que acabou de ser criado, vamos incluir a condição
`||logic:receivedNumber = 3||`. Por fim, dentro do `||logic:então||` desse laço, adicionamos o bloco
`||basic:mostrar leds||` e desenhamos um **X**.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 0) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . # # # .
            . # # # .
            . . . . .
            `)
    } else if (receivedNumber == 1) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . # # # .
            . . . . .
            . . . . .
            `)
    } else if (receivedNumber == 3) {
        basic.showLeds(`
            # . . . #
            . # . # .
            . . # . .
            . # . # .
            # . . . #
            `)
    } else {
        basic.showLeds(`
            . . # . .
            . . . # .
            # # # # #
            . . . # .
            . . # . .
            `)
    }
    basic.pause(100)
    basic.clearScreen()
})
```

## Step 22

Pronto, agora podemos carregar esse programa para os dois micro:bits, e nos comunicar
via Código Morse! E então, consegue ter uma conversa com um amigo só em Código Morse?
Se errar, não se esqueça de agitar o micro:bit e recomeçar a palavra.
