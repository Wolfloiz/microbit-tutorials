# Caixa de engrenagens

## Step 1

Neste projeto, vamos construir uma estrutura com vários eixos e engrenagens para observarmos como podemos alterar a velocidade e o torque (força) do motor. 
Para isso, vamos programar os controles para **ligar** e **desligar** o motor, alterar sua **velocidade** e **sentido de rotação**.

## Step 2

Vamos começar indo até a aba ``||Input:Input||`` e adicionando dois laços ``||Input:no botão A pressionado||``. Altere o botão de um dos laços para o ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
```

## Step 3

Em seguida, vá até a aba ``||Variables:Variáveis||`` e crie a variável ``||Variables:Direção||``. Depois de criada, volte à aba ``||Variables:Variáveis||`` e insira um bloco ``||Variables:definir Direção para 0||`` em cada laço adicionado no passo anterior.

```blocks
let Direção = 0
input.onButtonPressed(Button.A, function () {
    Direção = 0
})
input.onButtonPressed(Button.B, function () {
    Direção = 0
})
```

## Step 4

Agora, clique na aba **Avançado** para acessar a aba ``||Text:Texto||``. Selecione o primeiro bloco ``||Text:" "||`` e o insira nos campos onde temos o número **0** nos blocos de ``||Variables:definição||``.
Ao fazer isso, criamos a possibilidade de definir as variáveis como ``||Text:palavras||``.

```blocks
let Direção = ""
input.onButtonPressed(Button.A, function () {
    Direção = ""
})
input.onButtonPressed(Button.B, function () {
    Direção = ""
})
```

## Step 5

Preencha o campo com a palavra ``||Text: "esquerda"||`` para o laço do ``||Input: botão A||``. Para o ``||Input: botão B||``, escreva ``||Text: "direita"||`` no bloco de definição da ``||Variables:definição||``.

```blocks
let Direção = ""
input.onButtonPressed(Button.A, function () {
    Direção = "esquerda"
})
input.onButtonPressed(Button.B, function () {
    Direção = "direita"
})
```

## Step 6

Vamos adicionar a exibição de uma seta apontando para cada direção. Faça isso indo até a aba ``||Basic:Básico||`` e selecionando o bloco ``||Basic:mostrar leds||``.
Em seguida, clique sobre os LEDs que deseja acender para criar a seta para direita e para esquerda.

```blocks
let Direção = ""
input.onButtonPressed(Button.A, function () {
    Direção = "esquerda"
    basic.showLeds(`
        . . # . .
        . # . . .
        # # # # #
        . # . . .
        . . # . .
        `)
})
input.onButtonPressed(Button.B, function () {
    Direção = "direita"
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

A partir daqui, vamos trabalhar dentro do laço ``||Basic:sempre||``. Para adicioná-lo, volte à aba ``||Basic:Básico||`` e selecione o laço ``||Basic:sempre||``.

```blocks
let Direção = ""
input.onButtonPressed(Button.A, function () {
    Direção = "esquerda"
    basic.showLeds(`
        . . # . .
        . # . . .
        # # # # #
        . # . . .
        . . # . .
        `)
})
input.onButtonPressed(Button.B, function () {
    Direção = "direita"
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
})
basic.forever(function () {
	
})
```

## Step 8

Vamos, novamente, até a aba ``||Variables:Variáveis||`` criar a variável ``||Variables:Velocidade||``. Adicione um bloco de ``||Variables:definição||`` dentro do laço ``||Basic:sempre||``.
Certifique-se de que o campo deste bloco esteja a variável ``||Variables:Velocidade||``.

```blocks
basic.forever(function () {
    Velocidade = 0
})
```

## Step 9

Para completar este bloco, vá até a aba ``||Pins:Pins||``, dentro da seção de comandos **Avançados** e selecione o bloco ``||Pins:leitura analógica pin P0||``.
Altere de ``||Pins:P0||`` para ``||Pins:P1||``, pois essa porta é onde conectamos o Bit Potenciômetro.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 10

Abaixo deste bloco, vamos incluir alguns testes lógicos para determinar as condições de rotação do motor: sua velocidade e seu sentido.
Para isso, vá até a aba ``||Logic:Lógica||`` e selecione o primeiro laço ``||Logic:se verdadeiro então ||``.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (true) {
    	
    }
})
```

## Step 11

Retorne à aba ``||Logic:Lógica||`` e insira o bloco de ``||Logic:comparação||`` dentro do campo ``||Logic:verdadeiro||`` do laço ``||Logic:se então||``.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (0 == 0) {
    	
    }
})
```

## Step 12

Preencha o primeiro campo da ``||Logic:comparação||`` com a variável ``||Variables:Direção||``. O outro lado deve ser preenchido com a palavra ``||Text:"esquerda"||``. Para conseguirmos digitá-la, devemos antes adicionar o primeiro bloco da aba ``||Text:Texto||``: ``||Text:""||``.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
    	
    }
})
```

## Step 13

Dentro do laço ``||Logic:se então||``, adicionaremos o bloco ``||Pins:gravação digital pin P0 para 0||`` encontrado na aba ``||Pins:Pins||``. Altere de pin ``||Pins:P0||`` para ``||Pins:P16||``, pois é onde conectamos a porta DIR do Motor. O valor também deve ser alterado de **0** para **1**.

 Obs.: Se o seu motor estiver girando para o lado direito quando você pressionou o ``||Input:botão A||``, altere o campo deste bloco de **1** para **0**. Essa diferença está associada à fabricação do Motor.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
})
```

## Step 14

Clique o botão direito do mouse e duplique este laço ``||Logic:se então||``, posicionando o novo logo abaixo do anterior. Altere a palavra de ``||Text:"esquerda"||`` para ``||Text:"direita"||`` e o número da ``||Pins:gravação digital||`` de **1** para **0**.

 Obs.: Se no passo anterior você teve que voltar o valor para **0**, neste laço você deve colocar **1**. O valor da gravação digital tem que ser o oposto do que foi definido no passo anterior. 
 Também certifique-se de não colocar um este laço se então dentro do anterior. Ele deve ser posicionado abaixo!

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
})
```

## Step 15

Neste estágio, já programamos o controle do sentido de rotação dos motores. Agora, volte até a aba ``||Logic:Lógica||`` e adicione outro laço ``||Logic:se então||`` com um ``||Logic:comparador||`` abaixo do anterior.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (0 == 0) {
    	
    }
})
```

## Step 16

Clique em **Avançado** para acessar a aba ``||Pins:Pins||`` e selecionar o bloco ``||Pins: leitura digital pin P0||``. Ele deve ser posicionado no primeiro campo do ``||Logic:comparador||``,
para testar se a ``||Pins: leitura digital pin P0||`` é igual a **0** neste laço.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
    	
    }
})
```

## Step 17

Agora, dentro deste laço, vamos adicionar dois blocos: ``||Pins:gravação analógica pin P0 para 1023||``, presente na aba ``||Pins:Pins||`` o bloco ``||Basic:mostrar ícone||``, encontrado na aba ``||Basic:Básico||``.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        pins.analogWritePin(AnalogPin.P0, 1023)
        basic.showIcon(IconNames.Heart)
    }
})
```

## Step 18

Altere o valor da ``||Pins:gravação analógica||`` gravação analógica de **1023** para **0**, e o porta de ``||Pins:P0||`` para ``||Pins:P8||``, pois é onde conectamos o pino *Speed* do motor. Além disso, substitua o ícone que será exibido pelo **X**.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        pins.analogWritePin(AnalogPin.P8, 0)
        basic.showIcon(IconNames.No)
    }
})
```

## Step 19

Clique com o botão direito do mouse sobre o último laço ``||Logic:se então||`` e o duplique. Posicione o novo laço abaixo do anterior.
Altere a condição do ``||Logic:comparador||`` para ``||Pins:leitura digital pin P0||`` igual a **1**.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        pins.analogWritePin(AnalogPin.P8, 0)
        basic.showIcon(IconNames.No)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 1) {
        pins.analogWritePin(AnalogPin.P8, 0)
        basic.showIcon(IconNames.No)
    }
})
```

## Step 20

Altere o campo da ``||Pins:gravação analógica||`` de **0** para a variável  ``||Variables:Velocidade||``. Além disso, exclua o bloco ``||Basic:mostrar ícone||``.

```blocks
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        pins.analogWritePin(AnalogPin.P8, 0)
        basic.showIcon(IconNames.No)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 1) {
        pins.analogWritePin(AnalogPin.P8, Velocidade)
    }
})
```

## Step 21

Confira seu código e o transfira para o Micro:bit para testar como a associção de engrenagens pode interferir na velocidade e torque (força) do Motor.

```blocks
let Direção = ""
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    Direção = "esquerda"
    basic.showLeds(`
        . . # . .
        . # . . .
        # # # # #
        . # . . .
        . . # . .
        `)
})
input.onButtonPressed(Button.B, function () {
    Direção = "direita"
    basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    if (Direção == "esquerda") {
        pins.digitalWritePin(DigitalPin.P16, 1)
    }
    if (Direção == "direita") {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        pins.analogWritePin(AnalogPin.P8, 0)
        basic.showIcon(IconNames.No)
    }
    if (pins.digitalReadPin(DigitalPin.P0) == 1) {
        pins.analogWritePin(AnalogPin.P8, Velocidade)
    }
})
```
