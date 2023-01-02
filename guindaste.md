# Guindaste

## Step 1

Neste projeto, vamos construir o programa para controlarmos o guindaste. Basicamente, vamos definir os valores de velocidade e sentido de rotação de cada um dos dois motores que determinam a movimentação da base do guindaste e da corda que eleva as cargas.

## Step 2

Inicie acessando a aba ``||Input:Input||`` e adicionando dois laços ``||Input: no botão A pressionado||``. Altere o segundo de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
```

## Step 3

Vá até a aba ``||Variables:Variáveis||`` e crie a variável ``||Variables:Direção||``. Em seguida, insira um bloco de ``||Variables:definição||`` em cada um dos laços adicionados no passo anterior.
No laço ``||Input:no botão A pressionado||``, altere a definição da variável de **0** para **1**. 

```blocks
let Direção = 0
input.onButtonPressed(Button.A, function () {
    Direção = 1
})
input.onButtonPressed(Button.B, function () {
    Direção = 0
})
```

## Step 4

Agora, acesse a aba ``||Basic:Básico||`` e selecione o laço ``||Basic:sempre||``. O primeiro bloco dentro deste laço será a ``||Pins:gravação digital pin P0 para 0||``, encontrado na aba ``||Pins:Pins||`` dentro da seção **Avançado**.

```blocks
let Direção = 0
input.onButtonPressed(Button.A, function () {
    Direção = 1
})
input.onButtonPressed(Button.B, function () {
    Direção = 0
})
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

## Step 5

Altere a porta de gravação do pin ``||Pins:P0||`` para ``||Pins:P12||`` e substitua o valor de **0** pelo valor da variável ``||Variables:Direção||`` utilizando o bloco redondo presente na aba ``||Variables:Variáveis||``.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
})
```

## Step 6

Em seguida, acesse a aba de ``||Logic:Lógica||`` e adicione um laço ``||Logic:se verdadeiro então||``. Retorne à mesma aba e insira um ``||Logic:comparador||`` no campo ``||Logic:verdadeiro||`` do laço.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (0 == 0) {
    	
    }
})
```

## Step 7

No primeiro campo do ``||Logic:comparador||``, teremos a ``||Pins:leitura digital do pin P2||`` encontrada na aba ``||Pins:Pins||``. Lembre-se de alterar a porta de ``||Pins:P0||`` para ``||Pins:P2||``. O segundo campo deve se manter como **0**.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
    	
    }
})
```

## Step 8

Dentro deste laço ``||Logic:se então||``, adicione dois comandos de ``||Pins:gravação analógica pin P0 para 1023||``. O primeiro deles será na porta ``||Pins:P8||``, enquanto o segundo na porta ``||Pins:P16||``. Já nos campos de dados, o que está na porta  ``||Pins:P8||`` deve escrever a ``||Pins:leitura analógica pin P0||``. Já o segundo, na porta ``||Pins:P16||`` deve ser alterado de **1023** para **0**.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
    }
})
```

## Step 9

Ainda **dentro** (não abaixo!) deste mesmo laço ``||Logic:se então||``, vamos inserir outro laço ``||Logic:se então||`` com ``||Logic:comparador||``. Clique no sinal de **+** deste laço para adicionar o ``||Logic:senão||``.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (0 == 0) {
        	
        } else {
        	
        }
    }
})
```

## Step 10

No ``||Logic:comparador||`` deste laço, vamos avaliar se a variável ``||Variables:Direção||`` é igual a **1**. Altere os dois campos do comparador e, em seguida, inclua um bloco ``||Basic:mostrar LEDs||`` dentro do primeiro espaço do ``||Logic:então||`` e no segundo espaço no ``||Logic:senão||``.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . . . .
                . . . . .
                . . . . .
                . . . . .
                . . . . .
                `)
        } else {
            basic.showLeds(`
                . . . . .
                . . . . .
                . . . . .
                . . . . .
                . . . . .
                `)
        }
    }
})
```

## Step 11

No primeiro bloco ``||Basic:mostrar LEDs||``, desenhe uma seta para esquerda, pois quando ``||Variables:Direção||`` for igual a **1**, significa que pressionamos o ``||Input:botão A||``. Já no segundo bloco, desenhe uma seta para a direita que aparecerá quando pressionarmos o ``||Input:botão B||``.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
})
```

## Step 12

Neste momento, fechamos os dois laços ``||Logic:se então||``. Agora, duplique o primeiro (e maior) ``||Logic:se então||`` que criamos e o posicione **abaixo** dos dois anteriores. Nos próximos passos, vamos alterar alguns detalhes nestes blocos...

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
})
```

## Step 13

Neste segundo laço maior, ao contrário de avaliar se ``||Pins:leitura digital pin P2||`` é igual a **0** no primeiro ``||Logic:comparador||``, vamos avaliar se ela é igual a **1**.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 1) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
})
```

## Step 14

Nas duas ``||Pins:gravações analógicas||`` que se seguem, vamos inverter as portas. Onde estava ``||Pins:P8||`` passará a ser ``||Pins:P16||`` e vice-versa.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 1) {
        pins.analogWritePin(AnalogPin.P16, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P8, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
})
```

## Step 15

Por fim, edite os blocos ``||Basic:mostrar LEDs||`` substituindo a seta para esquerda por uma seta para cima. Consequentemente, altere a seta da direita para uma seta para baixo.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 1) {
        pins.analogWritePin(AnalogPin.P16, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P8, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # # # .
                # . # . #
                . . # . .
                . . # . .
                `)
        } else {
            basic.showLeds(`
                . . # . .
                . . # . .
                # . # . #
                . # # # .
                . . # . .
                `)
        }
    }
})
```

## Step 16

Transfira o código para o Micro:bit e utilize o **Bit botão** para alterar entre os motores que serão controlados. 
 
 O **Bit potenciômetro** controla a *velocidade* do motor selecionado.

 Os **botões A** e **B** alteram a *direção* dos motores, de direita para esquerda no caso do motor da base, ou no caso do motor superior, para cima ou para baixo.

```blocks
 let Direção = 0
input.onButtonPressed(Button.A, function () {
    Direção = 1
})
input.onButtonPressed(Button.B, function () {
    Direção = 0
})
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P12, Direção)
    if (pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.analogWritePin(AnalogPin.P8, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P16, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
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
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 1) {
        pins.analogWritePin(AnalogPin.P16, pins.analogReadPin(AnalogPin.P0))
        pins.analogWritePin(AnalogPin.P8, 0)
        if (Direção == 1) {
            basic.showLeds(`
                . . # . .
                . # # # .
                # . # . #
                . . # . .
                . . # . .
                `)
        } else {
            basic.showLeds(`
                . . # . .
                . . # . .
                # . # . #
                . # # # .
                . . # . .
                `)
        }
    }
})
```