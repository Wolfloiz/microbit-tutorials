# 008 Elevador

## Step 1

Neste tutorial, você irá aprender a fazer um elevador para uma estrutura de 3 andares. 

## Step 2

Primeiramente, acesse a aba ``||input:Input||`` e inclua o laço ``||input:no botão A pressionado||`` em seu programa. 
Esse input será utilizado como o comando para fazer o elevador **subir**.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
```

## Step 3

Agora, na aba ``||logic:Lógica||``, selecione o laço ``||logic:se-verdadeiro-então||``. 
Ele deve ser posicionado dentro do laço ``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    }	
})
```

## Step 4

Retorne à aba ``||logic:Lógica||`` e selecione o bloco triangular booleano
``||logic:ou||``. Posicione-o dentro do espaço triangular do laço 
``||logic:se-verdadeiro-então||``, substituindo a palavra ``||logic:verdadeiro||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (false || false) {
    	
    }
})
```

## Step 5

Retorne à aba ``||logic:Lógica||`` e selecione dois blocos triangulares comparadores
``||logic:0 = 0||``. Posicione-o dentro dos dois espaços triangulares do bloco
``||logic:ou||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (0 == 0 || 0 == 0) {
    	
    }
})
```

## Step 6

Agora, acesse a aba ``||variables:Variáveis||`` e clique em **Fazer uma variável**.
Nomeie essa variável como ``||variables:Andar||``. 
Ela poderá ser igual a **0** ou **1**, e representa o andar no qual o elevador se encontra no momento.

## Step 7

Volte à aba ``||variables:Variáveis||`` e selecione o bloco redondo 
``||variables:Andar||``. Insira essa variável no primeiro espaço de cada um 
dos blocos ``||logic:0 = 0||``, substituindo os primeiros números **0**. 
Em seguida, altere um dos dois valores **0** restantes pelo número **1**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
    	
    }
})
```

## Step 8

Em seguida, acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação digital pin P0||``. Coloque esse bloco dentro do laço 
``||logic:se-verdadeiro-então||``, substituindo o pino **P0** por **P12**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
    }
})

```
## Step 9

Retorne à categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0||``. Coloque esse bloco dentro do laço 
``||logic:se-verdadeiro-então||``, abaixo do bloco ``||pins:gravação digital pin P12||``, 
substituindo o pino **P0** por **P16**, e o número **1023** por **512**.

```blocks
input.onButtonPressed(Button.A, function () {
    let Andar = 0
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
    }
})
```
## Step 10

Acesse a aba ``||basic:Básico||``, selecione o bloco ``||basic:pausa||``, e o coloque 
abaixo do comando ``||pins:gravação analógica pin P16||``. Ajuste o valor da pausa, 
trocando o valor **100** por **1000**. *Este valor será ajustado posteriormente na etapa de calibração do elevador.*

```blocks
input.onButtonPressed(Button.A, function () {
    let Andar = 0
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
    }
})
```

## Step 11

Volte à categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0||``. Coloque esse bloco dentro do laço 
``||logic:se-verdadeiro-então||``, abaixo do bloco ``||basic:pausa||``, 
substituindo o pino **P0** por **P16**, e o número **1023** por **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    let Andar = 0
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
    }
})
```

## Step 12

Retorne à aba ``||variables:Variáveis||``, selecione o bloco 
``||variables:alterar Andar por 1||``, e o posicione dentro do laço 
``||logic:se-verdadeiro-então||``.

```blocks
let Andar = 0
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
```
## Step 13

Com isso, a parte do código que faz o elevador subir quando o botão é pressionado, está pronta. Porém, ainda nos resta fazer o código 
responsável pela descida do elevador.

## Step 14

Copie o laço ``||input:no botão A pressionado||`` (com todo seu conteúdo). Modifique a 
cópia para que ela se torne ``||input:no botão B pressionado||``, alterando de **A** para **B**.

```blocks
let Andar = 0
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
input.onButtonPressed(Button.B, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
```

## Step 15

No laço ``||input:no botão B pressionado||``, altere a condição do teste 
``||logic:se-verdadeiro-então||``, de **Andar = 0** para **Andar = 2**.

```blocks
let Andar = 0
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
input.onButtonPressed(Button.B, function () {
    if (Andar == 2 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
```

## Step 16

Ainda no laço ``||input:no botão B pressionado||``, altere o bloco 
``||pins:gravação digital pin P12||``, trocando o valor de **0** para **1**.

```blocks
let Andar = 0
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
input.onButtonPressed(Button.B, function () {
    if (Andar == 2 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 1)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
```

## Step 17

Por fim, ainda no laço ``||input:no botão B pressionado||``, altere o bloco 
``||variables:alterar Andar por 1||``, trocando o valor **1** por **-1**.

```blocks
let Andar = 0
input.onButtonPressed(Button.A, function () {
    if (Andar == 0 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += 1
    }
})
input.onButtonPressed(Button.B, function () {
    if (Andar == 2 || Andar == 1) {
        pins.digitalWritePin(DigitalPin.P12, 1)
        pins.analogWritePin(AnalogPin.P16, 512)
        basic.pause(1000)
        pins.analogWritePin(AnalogPin.P16, 0)
        Andar += -1
    }
})
```

## Step 18
Pronto! Agora você já pode baixar o código para o Micro:bit e testar seu elevador. Após construir a estrutura, lembre-se 
de realizar a calibração dos valores de pausa do seu código na próxima etapa do projeto.
