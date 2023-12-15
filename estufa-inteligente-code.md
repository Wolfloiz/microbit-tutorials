# Estufa Inteligente

## Step 1

Neste tutorial, você irá aprender a fazer um sistema de monitoramento de 
temperatura e luz de uma estufa.

## Step 2

Primeiramente, vá até a aba ``||variables:Variáveis||`` e clique em **Fazer uma variável**.
Coloque o nome dessa variável como ``||variables:Botão||``. Ela poderá 
ser igual a **0** ou **1**, e irá mudar toda vez que o botão for apertado. Sua função será 
permitir a alternância de visualização da temperatura ou da luz na matriz de LEDs do Micro:bit.

## Step 3

Retorne à aba ``||variables:Variáveis||``, selecione o bloco 
``||variables:definir Botão para 0||``, e o posicione dentro do laço ``||basic:sempre||``.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = 0
})
```

## Step 4

Em seguida, acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco circular
``||pins:leitura digital pin P0||``. Coloque esse bloco dentro de ``||variables:definir Botão para 0||``, 
substituindo o número **0**.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
})
```

## Step 5

Agora, na aba ``||logic:Lógica||``, selecione o laço 
``||logic:se-verdadeiro-então||``. Ele deve ser posicionado dentro do laço 
``||basic:sempre||``, abaixo do bloco ``||variables:definir Botão para||``.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (true) {
    	
    }
})
```

## Step 6

Retorne à aba ``||logic:Lógica||`` e pegue o bloco triangular comparador
``||logic:0 = 0||``. Posicione-o dentro do espaço triangular do laço 
``||logic:se-verdadeiro-então||``, substituindo a palavra ``||logic:verdadeiro||``.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (0 == 0) {
    	
    }
})
```

## Step 7

Volte à aba ``||variables:Variáveis||`` e pegue o bloco redondo 
``||variables:Botão||``. Insira essa variável no primeiro espaço do bloco 
``||logic:0 = 0||``, substituindo o primeiro número **0**.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
    	
    }
})
```

## Step 8

Acesse a categoria ``||basic:Básico||``, selecione o bloco ``||basic:mostrar número||`` e coloque-o 
dentro do laço ``||logic:se-verdadeiro-então||``.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(0)
    }
})
```

## Step 9

Agora, precisamos pegar o valor da temperatura vindo do próprio sensor já integrado ao Micro:bit.
Para acessá-lo, vá até a aba ``||input:Input||``, selecione o bloco circular ``||input:temperatura||`` 
e posicione-o dentro do espaço circular do comando ``||basic:mostrar número||``, substituindo o número **0**.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
    basic.showNumber(input.temperature())
    }
})
```

## Step 10

Volte à aba ``||logic:Lógica||`` e selecione mais um laço ``||logic:se-verdadeiro-então||``. 
Posicione esse bloco dentro do laço ``||basic:sempre||``, **abaixo** do outro laço ``||logic:se-verdadeiro-então|`` que já 
foi adicionado anteriormente.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (true) {
    	
    }
})
```

## Step 11

Ainda na aba ``||logic:Lógica||``, adicione o bloco 
``||logic:___ e ____||`` dentro do espaço triangular do laço  
``||logic:se-verdadeiro-então||``, substituindo a palavra ``||logic:verdadeiro||``.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (false && false) {
    	
    }
})
```

## Step 12

Copie o bloco triangular ``||logic:Botão = 0||``, que se encontra no primeiro laço  
``||logic:se-verdadeiro-então||``, e coloque a cópia dentro do bloco 
``||logic:___ e ___||``, no primeiro espaço. Substitua o número **0** por **1**


```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && false) {
    	
    }
})
```

## Step 13

Retorne à aba ``||logic:Lógica||`` e inclua mais um bloco comparador ``||logic:0 < 0||`` dentro do espaço triangular restante
do bloco ``||logic:Botão=1 e ___||``.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && 0 < 0) {
    	
    }
})
```

## Step 15

Feito isso, acesse a aba ``||input:Input||`` e selecione o bloco circular ``||input:nível de luz||``. 
Coloque esse bloco dentro do comparador ``||logic:0 < 0||``, substituindo o primeiro número **0**.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && input.lightLevel() < 0) {
    	
    }
})
```

## Step 15

O nível de luz indica a luminosidade como um valor entre **0** (muito escuro) e **255** 
(muito claro). Para esta atividade, vamos mostrar um rosto triste 
quando o nível de luz for menor que **200**. Então, no bloco  ``||nível de luz < 0||``, substitua o valor **0** por **200**.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && input.lightLevel() < 200) {
    	
    }
})
```

## Step 16

Para mostrar o rosto triste, acesse a categoria ``||basic:Básico||`` e selecione o bloco 
``||basic:mostrar ícone||``. Posicione-o dentro do laço ``||logic:se-verdadeiro-então||`` 
que foi criado por último. Neste comando, selecione o ícone de um rosto triste.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && input.lightLevel()< 200) {
        basic.showIcon(IconNames.Sad)
    }
})
```

## Step 17

Agora, devemos mostrar um rosto feliz quando o sensor de luz detectar que está claro. 
Para isso, copie todo o laço ``||logic:se-verdadeiro-então||`` que foi criado por último e 
que mostra o rosto triste. Para facilitar, clique com o botão direito do mouse sobre o laço e selecione duplicar.
Coloque a cópia logo abaixo do original.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && input.lightLevel() < 200) {
        basic.showIcon(IconNames.Sad)
    }
    if (Botão == 1 && input.lightLevel() < 200) {
        basic.showIcon(IconNames.Sad)
    }
})
```

## Step 18

Porém, nesse laço que copiamos, altere o sinal do ``||nível de luz < 0||`` de **<** para **>**, e mude o ícone para 
um rosto feliz.

```blocks
let Botão = 0
basic.forever(function () {
    Botão = pins.digitalReadPin(DigitalPin.P0)
    if (Botão == 0) {
        basic.showNumber(input.temperature())
    }
    if (Botão == 1 && input.lightLevel() < 200) {
        basic.showIcon(IconNames.Sad)
    }
    if (Botão == 1 && input.lightLevel() > 200) {
        basic.showIcon(IconNames.Happy)
    }
})
```

## Step 19
Pronto! Agora você já pode monitorar a temperatura e luz de sua estufa!
