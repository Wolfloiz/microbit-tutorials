# Cancela

## Step 1

Neste tutorial, você irá aprender a fazer uma cancela que pode operar automaticamente, utilizando o Sensor Infravermelho, 
ou manualmente, utilizando o Potenciômetro. Esses modos de operação serão alterados ao pressionar os botões A e B do Micro:bit.


## Step 2

Primeiramente, acesse a aba ``||variables:Variáveis||`` e clique em **Fazer uma variável**.
Coloque o nome dessa variável como ``||variables:Modo||``.

## Step 3

Retorne à aba ``||variables:Variáveis||`` e selecione o bloco 
``||variables:Definir Modo para 0||``. Então, coloque esse comando dentro do 
laço ``||basic:no iniciar||``. Altere o seu valor de **0** para **1**.

```blocks
let Modo = 1
basic.forever(function () {
	
})
```

## Step 4

Acesse a categoria ``||input:Input||`` e adicione dois laços ``||input:no botão A pressionado||``.  
Altere um destes laços de ``||input:botão A||`` para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let Modo = 1
basic.forever(function () {
	
})
```

## Step 5

Clique em ``||variables:Variáveis||`` novamente e adicione um bloco ``||variables:Definir Modo para 0||`` 
em cada laço de ``||input:botão pressionado||``. Certifique-se de que dentro do laço do ``||input:Botão A||``, o valor 
definido é **1** e, no ``||input:botão B||``, o valor é **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    Modo = 1
})
input.onButtonPressed(Button.B, function () {
    Modo = 0
})
let Modo = 0
Modo = 1
basic.forever(function () {
	
})
```

## Step 6

Agora, vamos trabalhar no laço ``||basic:sempre||``, onde construíremos a lógica de controle da cancela.
Para isso, acesse a aba ``||logic:Lógica||``, e selecione o laço 
``||logic:se-verdadeiro-então-senão||``. Ele deve ser posicionado dentro do laço 
``||basic:sempre||``. 

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Step 7

Retorne à aba ``||logic:Lógica||`` e selecione o bloco triangular comparador
``||logic:0 = 0||``. Posicione-o dentro do espaço triangular do laço 
``||logic:se-verdadeiro-então-senão||``, substituindo a palavra ``||logic:verdadeiro||``.

```blocks
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Step 8

Volte à aba ``||variables:Variáveis||`` e adicione o bloco redondo 
``||variables:Modo||``. Insira essa variável no primeiro espaço do bloco 
``||logic:0 = 0||``, substituindo o primeiro número **0**.

```blocks
basic.forever(function () {
    if (Modo == 0) {
    	
    } else {
    	
    }
})
```

## Step 9

Em seguida, acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0 para 1023||``. Coloque esse bloco **dentro** do ``||logic:então||`` do laço 
``||logic:se-verdadeiro-então-senão||``, substituindo o pino **P0** por **P12**.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, 1023)
    } else {
    	
    }
})
```

## Step 10

Ainda na aba ``||pins:Pins||``, selecione o bloco circular 
``||pins:leitura analógica pin P0||``. Coloque esse bloco dentro do bloco 
``||pins:gravação analógica pin P0 para 1023||``, substituindo o valor **1023**. 
Ao mesmo tempo, substitua o pino **P0** por **P1**.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
    	
    }
})
```

## Step 11

Agora, retorne à aba ``||logic:Lógica||`` e selecione um laço 
``||logic:se-verdadeiro-então||``. Coloque esse bloco **dentro** do **senão** do laço 
``||logic:se-verdadeiro-então-senão||``.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (true) {
        	
        }
    }
})
```

## Step 12

Ainda na aba ``||logic:Lógica||``, adicione o bloco triangular comparador
``||logic:0 < 0||``. Posicione-o dentro do espaço triangular do laço 
``||logic:se-verdadeiro-então||``, substituindo a palavra ``||logic:verdadeiro||``.
Altere o sinal deste comparador de **<** para **>**.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (0 > 0) {
        	
        }
    }
})
```

## Step 13

Acesse novamente a categoria **Avançado** e, na aba ``||pins:Pins||``,
selecione o bloco circular
``||pins:leitura analógica pin P0||``. Coloque esse bloco dentro de 
``||logic:0 > 0||``, substituindo o primeiro número **0**. Altere o pino de **P0** 
para **P2** e substitua o segundo número **0** pelo número **600**.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (pins.analogReadPin(AnalogPin.P2) > 600) {
        	
        }
    }
})
```

## Step 14

Ainda na aba ``||pins:Pins||``, selecione o bloco ``||pins:gravação analógica pin P0 para 1023||``. 
Coloque esse bloco dentro do laço ``||logic:se-verdadeiro-então||``. Troque o pino de **P0** para **P12** e o valor 
de **1023** para **512**.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (pins.analogReadPin(AnalogPin.P2) > 600) {
            pins.analogWritePin(AnalogPin.P12, 512)
        }
    }
})
```

## Step 15

Acesse a categoria ``||basic:Básico||``, selecione o bloco ``||basic:pausa||``, e o coloque 
abaixo do comando ``||pins:gravação analógica pin P12 para 512||``, dentro do laço  
``||logic:se-verdadeiro-então||``. Ajuste o tempo desta pausa, 
alterando o valor **100** para **5000**. Essa pausa faz com que a cancela espere um 
tempo antes de fechar, possibilitando a passagem do veículo durante este período.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (pins.analogReadPin(AnalogPin.P2) > 600) {
            pins.analogWritePin(AnalogPin.P12, 512)
            basic.pause(5000)
        }
    }
})
```

## Step 16

Por fim, novamente na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0 para 1023||``. Coloque esse bloco dentro do laço
``||logic:se-verdadeiro-então||``, abaixo da ``||basic:pausa||``. 
Troque o pino de **P0** para **P12** e o valor de **1023** para **0**. 
Esse comando será responsável por fechar a cancela após a pausa.

```blocks
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (pins.analogReadPin(AnalogPin.P2) > 600) {
            pins.analogWritePin(AnalogPin.P12, 512)
            basic.pause(5000)
            pins.analogWritePin(AnalogPin.P12, 0)
        }
    }
})
```

## Step 17

Pronto! Verifique seu código e teste sua cancela no modo automático e no modo manual.

```blocks
input.onButtonPressed(Button.A, function () {
    Modo = 1
})
input.onButtonPressed(Button.B, function () {
    Modo = 0
})
let Modo = 0
Modo = 1
basic.forever(function () {
    if (Modo == 0) {
        pins.analogWritePin(AnalogPin.P12, pins.analogReadPin(AnalogPin.P1))
    } else {
        if (pins.analogReadPin(AnalogPin.P2) > 600) {
            pins.analogWritePin(AnalogPin.P12, 512)
            basic.pause(5000)
            pins.analogWritePin(AnalogPin.P12, 0)
        }
    }
})
```