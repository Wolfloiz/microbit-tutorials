```template
radio.setGroup(255)
radio.setTransmitPower(7)
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

```

## Step 1

Os programas que fizemos até então permitem que um dos micro:bits envie o Código Morse e o outro
receba. Agora, vamos complementar nossos códigos para que os dois micro:bits possam enviar e
receber mensagens em Código Morse.

## Step 2

Estamos partindo do código que fizemos anteriormente para o micro:bit que apenas envia as mensagens.
Por isso, devemos acrescentar a parte que faz com que o micro:bit receba informação  
e mostre o símbolo na tela de acordo com o que foi recebido.

## Step 3

Em seguida, vamos adicionar o laço `||radio:ao receber rádio receivedNumber||`,
que pode ser encontrado na aba `||radio:Rádio||`.
Esse bloco executa tudo que está dentro dele quando recebe um número de outro Micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {

})
```

## Step 4

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

## Step 5

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

## Step 6

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

## Step 7

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

## Step 8

Pronto, agora podemos carregar esse programa para os dois micro:bits, e nos comunicar
via Código Morse! E então, consegue ter uma conversa com um amigo só em Código Morse?
