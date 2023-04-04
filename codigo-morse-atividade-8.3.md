


## Step 1

Vamos aprender a usar um micro:bit para enviar uma mensagem usando código morse.
Um micro:bit vai enviar a mensagem, e o outro vai receber. Primeiro, vamos 
programar o primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos pegar o bloco ``||radio:definir grupo do rádio 1||``, na aba 
``||radio:Rádio||``, e colocá-lo dentro do bloco ``||basic:no iniciar||``. Esse bloco 
serve para que todos os micro:bits dentro desse mesmo grupo estejam conectados uns com 
os outros.

```blocks
radio.setGroup(1)
```

## Step 3

Vamos agora determinar a "força" com que o micro:bit irá transmitir informações. Isso irá 
determinar a distância da comunicação. Vamos adicionar o bloco 
``||radio:conjunto de rádio transmite energia||`` que se encontra na 
aba ``||radio:Rádio->mais||``, e colocá-lo no bloco ``||basic:no iniciar||``. Pronto, 
agora a parte da comunicação do primeiro micro:bit está feita.


```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 4

Para enviar a mensagem, vamos precisar de três comandos, um comando para enviar um traço, 
um para enviar um ponto, e um para mostrar que a letra já acabou, e vamos passar para a 
próxima. Para isso, vamos adicionar os blocos ``||input:no botão A pressionado||``, 
``||input:no botão B pressionado||`` e ``||input:no botão A+B pressionado||``.


```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
input.onButtonPressed(Button.AB, function () {
	
})
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 5

Dentro do bloco ``||input:no botão A pressionado||``, vamos adicionar o bloco 
``||basic:mostrar leds||`` e desenhar um quadrado 3x3 para representar um ponto. Já 
no bloco ``||input:no botão B pressionado||``, vamos adicionar o bloco 
``||basic:mostrar leds||`` e desenhar uma linha de 3 leds para representar o traço.


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
Por fim, no bloco ``||input:no botão A+B pressionado||`` vamos adicionar o bloco 
``||basic:mostrar leds||`` e desenhar uma seta para a direita, representando que já 
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
Mas e agora, como iremos transmitir as letras e palavras que estamos digitando para 
o outro micro:bit? Para isso vamos usar o bloco ``||radio:rádio envia número||`` 
que pode ser achado na aba ``||radio:Rádio||``. Vamos adicionar esse bloco abaixo de cada 
um dos três desenhos. No caso do ponto, enviaremos o número 0, no caso do traço enviaremos 
o número 1, e para passar pra próxima palavra, enviaremos o número 2.

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
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 8
Para garantir que o sinal foi enviado, e podermos visualizar qual símbolo enviamos, vamos 
adicionar ainda, abaixo dos três blocos ``||radio:rádio envia número||``, uma 
``||basic:pausa (ms) 100||`` e ``||basic:limpar tela||``.

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
radio.setGroup(1)
radio.setTransmitPower(7)
```



## Step 9

Agora que configuramos o primeiro micro:bit para enviar o código,
 falta configurar o segundo para receber esse código. Vamos lá!







