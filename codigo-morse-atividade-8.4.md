## Step 1

Neste tutorial, vamos programar o segundo micro:bit (M2), que irá receber as informações enviadas
pelo primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos selecionar o bloco `||radio:definir grupo do rádio 1||`, na categoria
`||radio:Rádio||`, e colocá-lo dentro do laço `||basic:no iniciar||`. Esse bloco
serve para garantir que todos os micro:bits dentro desse mesmo grupo de rádio estejam conectados uns com
os outros. Altere o número do grupo para o mesmo valor que você usou no tutorial anterior no código do primeiro Micro:bit.

```blocks
radio.setGroup(255)
```

## Step 3

Em seguida, vamos adicionar o laço `||radio:ao receber rádio receivedNumber||`,
que pode ser encontrado na aba `||radio:Rádio||`.
Esse bloco executa tudo que está dentro dele quando recebe um número de outro Micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {

})
radio.setGroup(255)
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
radio.setGroup(255)
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
radio.setGroup(255)
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
radio.setGroup(255)
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

Agora temos os dois micro:bits configurados e se comunicando. Tente enviar uma
mensagem em Código Morse para um amigo e veja se ele consegue decifrar!
