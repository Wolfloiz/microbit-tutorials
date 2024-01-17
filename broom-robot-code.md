# Robô Vassoura

## Step 1

Neste tutorial, você irá aprender a programar seu próprio robô vassoura.
Ele será um robô que se movimenta com um Motor CC e monitora a presença de lixo na sua frente
com o Sensor Infravermelho. Quando identifica o lixo, ele aciona um Servo motor para remover 
esse obstáculo.

## Step 2

Primeiramente, acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0 para 1023||``. Coloque esse bloco dentro do laço
``||basic:sempre||``, substituindo o pino **P0** por **P8**, e o valor de 
**1023** para **512**. Esse bloco fará o robô vassoura andar para frente.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
})
```

## Step 3

Agora, na aba ``||logic:Lógica||``, selecione o laço 
``||logic:se-verdadeiro-então||``. Ele deve ser posicionado dentro do laço 
``||basic: sempre||``.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (true) {
    	
    }
})
```

## Step 4

Retorne à aba ``||logic:Lógica||`` e pegue o bloco triangular comparador
``||logic:0 > 0||``. Posicione-o dentro do espaço triangular do laço 
``||logic:se-verdadeiro-então||``, substituindo a palavra ``||logic:verdadeiro||``.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (0 > 0) {
    	
    }
})
```

## Step 5

Acesse novamente a categoria **Avançado** e, na aba ``||pins:Pins||``, 
selecione o bloco circular ``||pins:leitura analógica pin P0||`` modificando a porta de **P0** para **P1**. 
Insira esse bloco no primeiro espaço do comparador ``||logic:0 > 0||``, substituindo o primeiro número **0**. 
Altere o segundo número **0** para **600**. Esse comparador irá usar 
as informaçoes do sensor infravermelho para verificar se há ou não um obstáculo (lixo).

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (pins.analogReadPin(AnalogPin.P1) > 600) {
    	
    }
})
```

## Step 6

Ainda na aba ``||pins:Pins||``, selecione o bloco ``||pins:gravação analógica pin P0 para 1023||`` 
e coloque-o **dentro** do laço ``||logic:se-verdadeiro-então||``, alterando o pino de **P0** para **P8** e o valor 
de **1023** para **0**. Esse bloco será responsável por parar o robô vassoura quando lixo for detectado.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (pins.analogReadPin(AnalogPin.P1) > 600) {
        pins.analogWritePin(AnalogPin.P8, 0)
    }
})
```

## Step 7

Novamente, ainda na aba ``||pins:Pins||``, selecione o bloco ``||pins:gravação analógica pin P0 para 1023||`` 
e coloque-o **dentro** do laço ``||logic:se-verdadeiro-então||``, alterando o pino de **P0** para **P16**.
Mantenha o valor de **1023**. Esse bloco será responsável por acionar o Servo motor para remover o lixo.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (pins.analogReadPin(AnalogPin.P1) > 600) {
        pins.analogWritePin(AnalogPin.P8, 0)
        pins.analogWritePin(AnalogPin.P16, 1023)
    }
})
```

## Step 8

Em seguida, acesse a categoria ``||basic:Básico||``, selecione o comando ``||basic:pausa||``, 
e o coloque **dentro** do laço ``||logic:se-verdadeiro-então||`` após o bloco adicionado no passo anterior. 
Ajuste o valor da pausa, substituindo o número **100** por **2000**. 
Essa pausa possibilita que o robô vassoura tenha tempo suficiente para varrer o lixo antes de continuar andando.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (pins.analogReadPin(AnalogPin.P1) > 600) {
        pins.analogWritePin(AnalogPin.P8, 0)
        pins.analogWritePin(AnalogPin.P16, 1023)
        basic.pause(2000)
    }
})
```

## Step 9

Feito isso, devemos parar a vassoura utilizando o bloco ``||pins:gravação analógica pin P16 para 0||``
posicionado depois da pausa, ainda **dentro** do laço ``||logic:se-verdadeiro-então||``.
Certifique-se de que a porta seja a **P16** e o valor seja **0**.

```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P8, 512)
    if (pins.analogReadPin(AnalogPin.P1) > 600) {
        pins.analogWritePin(AnalogPin.P8, 0)
        pins.analogWritePin(AnalogPin.P16, 1023)
        basic.pause(2000)
        pins.analogWritePin(AnalogPin.P16, 0)
    }
})
```

## Step 10

Pronto, agora podemos testar o robô vassoura. Experimente colocando alguns obstáculos 
no caminho e veja se ele consegue varrer todos.