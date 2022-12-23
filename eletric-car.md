# Carro elétrico

## Step 1

Neste projeto, vamos construir um veículo com dois motores, que variam a velocidade de acordo com a posição do ponteiro do nosso potenciômetro. 
Nosso veículo irá executar uma sequência de movimentos predefinidos pelo código de programação.

## Step 2

Para iniciarmos a atividade, vamos manter apenas o laço ``||Basic:sempre||``, localizado na aba ``||Basic:Básico||``.

```blocks
basic.forever(function () {
	
})
```

## Step 3
Va até a aba ``||Variables:Variáveis||`` e crie uma variável denominada ``||Variables:Velocidade||``. Em seguida, volte à mesma aba e adicone o bloco ``||Variables:Definir Velocidade para 0||`` dentro do laço ``||Basic:sempre||``.

```blocks
let Velocidade = 0
basic.forever(function () {
    Velocidade = 0
})
```

## Step 4
Agora, clique em **Avançado** para acessar a aba ``||Pins:Pins||``. Nela, selecione o bloco ``||Pins:leitura analógica pin P0||``, que deve ser posicionado dentro do bloco de ``||Variables:definição da variável||``. Altere a porta de ``||Pins:P0||`` para ``||Pins:P1||``.

```blocks
let Velocidade = 0
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 5
Acesse a aba ``||Input:Input||`` e selecione o laço ``||Input:no botão A pessionado||``.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
	
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 6
A partir daqui, vamos programar os movimentos do carrinho que serão executados quando pressionarmos o ``||Input:botão A||`` do Micro:bit.
Comece indo à aba ``||Pins:Pins||`` e selecionando o bloco ``||Pins:gravação analógica pin P0 para 1023||``.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P0, 1023)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 7
Altere a porta de ``||Pins:P0||`` para ``||Pins:P12||`` e volte à aba ``||Variables:Variáveis||`` para substituir o valor **1023** pela variável ``||Variables:Velocidade||``.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 8
Agora, devemos controlar os sentidos de rotação dos motores, conectados nos pinos ``||Pins:P8||`` e ``||Pins:P16||``. Neste caso, podemos enviar sinais digitais, que variam entre **0** ou **1**.
Para isso, selecione dois blocos ``||Pins:gravação digital pin P0 para 0||`` situado na aba ``||Pins:Pins||``.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P0, 0)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 9
Altere as portas para ``||Pins:P8||`` e ``||Pins:P16||``. Os valores das gravações digitais devem ser diferentes para que o carrinho ande em linha reta,
pois os motores estão posicionados em lados opostos. Por isso, envie o valor **1** para ``||Pins:P8||``, e o valor **0** na porta ``||Pins:P16||`` para testar. Se ele estiver indo para trás, basta inverter os valores das portas para que ele ande para frente.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 10
Adicione uma ``||Basic:pausa (ms)||`` de **4 segundos** (4000 ms) para que ele execute esse movimento durante esse período de tempo. Esse comando encontra-se na aba ``||Basic:Básico||``.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 11
Ainda dentro do laço ``||Input:no botão A pressionado||``, vamos duplicar *(botão direito do mouse)* estes três últimos blocos para programar um movimento de giro do carrinho. Após duplicá-los, altere o valor de uma das portas para que ambas estejam recebendo **1**.
Também altere o tempo da ``||Basic:pausa||`` de **4 segundos** para **300ms**.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 12
Depois de girar o carrinho, replique os blocos para que ele se movimente em linha reta novamente por 4 segundos.
Para isso, duplique as ``||Pins:gravações digitais||`` da primeira parte do movimento, quando os valores nas portas eram diferentes entre si. Lembre-se da ``||Basic:pausa||`` de **4000 ms**.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 13 
Agora, vamos programar uma curva para o lado oposto da que fizemos anteriormente. Para isso, duplique os blocos de ``||Pins:gravações digitais||``
e insira o número **0** em ambas as portas, ``||Pins:P8||`` e ``||Pins:P16||``. Além disso, lembre-se de inserir a ``||Basic:pausa||`` de **300ms** em sequência.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(300)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 14

Novamente, adicionaremos um movimento em linha reta durante quatro segundos. Neste caso, duplicamos os blocos que estão com valores distintos nas portas.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 15
Em seguida, devemos apenas para os motores. Conseguimos fazer isso enviando **0** na porta conectada ao lado *Speed* dos motores.
Portanto, vá até a aba ``||Pins:Pins||`` e selecione o bloco ``||Pins:gravação analógica pin P0 para 1023||``. Altere seus campos para a porta ``||Pins:P12||`` e o valor **0**.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.analogWritePin(AnalogPin.P12, 0)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 16
Para finalizarmos nosso programa, precisamos atribuir um botão para interromper o movimento do carrinho a qualquer momento. 
Então, acesse a aba ``||Input:Input||`` e adicione mais um laço ``||Input:no botão A pressionado||`` ao código. Altere de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.analogWritePin(AnalogPin.P12, 0)
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```

## Step 17
Neste caso, podemos apenas enviar **0** na porta que usamos para controlar a velocidade dos motores. Ou seja, vá até a aba ``||Pins:Pins||``
e insira o bloco ``||Pins:gravação analógica pin P0 para 1023||`` dentro deste laço ``||Input:no botão B pressionado||``. Altere para a porta ``||Pins:P12||`` e substitua o **1023** por **0**. 

```blocks
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(300)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.analogWritePin(AnalogPin.P12, 0)
})
input.onButtonPressed(Button.B, function () {
    pins.analogWritePin(AnalogPin.P12, 0)
})
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```
