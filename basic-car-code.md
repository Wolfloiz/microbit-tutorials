# Carrinho Básico

## Step 1

Neste tutorial, você irá aprender a programar um carrinho para percorrer um 
percurso determinado. O carrinho deve:
1. andar pra frente
2. virar para um lado
3. andar pra frente
4. virar para o outro
5. andar para frente
6. andar pra trás
7. parar.


## Step 2

Primeiramente, acesse a aba ``||input:Input||`` e selecione o laço 
``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
```

## Step 3

Em seguida, acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0||``. Coloque esse bloco dentro do laço 
``||input:no botão A pressionado||``, substituindo o pino **P0** por **P12** e o seu valor de **0** por **512**.

 Este comando define a velocidade do seu carrinho, que pode variar de 0 a 1023. Logo, estamos definindo uma
 velocidade média para ambos os motores (512).

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
})
```

## Step 4

Retone à categoria **Avançado** e, na aba ``||pins:Pins||``, selecione dois blocos
``||pins:gravação digital pin P0||``. Posicione-os dentro do laço 
``||input:no botão A pressionado||``, substituindo o pino **P0** por **P8** e **P16** respectivamente.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
})
```

## Step 5

Estes dois blocos de ``||pins:gravação digital||`` determinam os sentidos de rotação de nossos motores.
Dito isso, o primeiro movimento do carrinho deve ser para frente em linha reta. Então, devemos definir 
direções opostas para os motores, já que estão posicionados em sentidos opostos.

Para isso, basta alterar o valor da ``||pins:gravação digital pin P8||`` de **0** para **1**.

 *Se seu carrinho estiver indo para trás, basta inverter os valores das portas **P8** e **P16** para que ele ande para frente.*

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
})
```

## Step 6

Vá até a aba ``||basic:Básico||``, selecione o bloco ``||basic:pausa||`` e o posicione 
abaixo do bloco ``||pins:gravação digital pin P16||``. Ajuste o valor da pausa, 
trocando o valor **100** por **4000**. 

Com isso terminamos o primeiro trecho, 
em que o carrinho vai andar pra frente por  **4** segundos. Para ajustar a duração deste movimento
altere o valor da pausa.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
})
```

## Step 7

Ainda dentro do laço ``||Input:no botão A pressionado||``, vamos duplicar *(botão direito do mouse)* os dois blocos de ``||pins:gravação digital||`` e a ``||basic:pausa||``
para programar um movimento de giro do carrinho. Após duplicá-los, altere o valor de uma das portas para que ambas estejam recebendo **1**.
Também altere o tempo da ``||Basic:pausa||`` de **4 segundos** para **500ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
})
```

## Step 8

Depois de girar o carrinho, replique os blocos para que ele se movimente em linha reta novamente por 4 segundos.
Para isso, duplique as ``||Pins:gravações digitais||`` da primeira parte do movimento, quando os valores nas portas eram diferentes entre si. 
Lembre-se da ``||Basic:pausa||`` de **4000 ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
})
```

## Step 9

Agora, vamos programar uma curva para o lado oposto da que fizemos anteriormente. Para isso, duplique os blocos de ``||Pins:gravações digitais||``
e insira o número **0** em ambas as portas, ``||Pins:P8||`` e ``||Pins:P16||``. 
Além disso, lembre-se de inserir a ``||Basic:pausa||`` de **500ms** em sequência.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(500)
})
```

## Step 10

Novamente, adicionaremos um movimento em linha reta durante quatro segundos. 
Neste caso, duplicamos os blocos de ``||Pins:gravações digitais||`` que estão com valores distintos 
nas portas e a ``||Basic:pausa||`` de **4000ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
})
```

## Step 11

Feito isso, devemos configurar o movimento para trás. Como ele é o oposto do movimento para frente,
podemos duplicar as ``||Pins:gravações digitais||`` que estavam com valores diferentes e invertê-los entre as portas **P8** e **P16**.

Portanto, altere o valor da ``||pins:gravação digital pin P8||`` de **1** para **0**, e o da **P16** de **0** para **1**.
Lembre-se de adicionar a ``||Basic:pausa||`` para determinar a duração do movimento. Utilizaremos uma pausa de **2000ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(2000)
})
```

## Step 12

*Obs.: Se na configuração do movimento para frente você precisou inverter os valores, deverá repetir esse procedimento aqui para que ele ande para trás. Se for o caso, inverta os valores das portas **P8** e **P16**.*

## Step 13

Em seguida, devemos parar os motores. Conseguimos fazer isso enviando **0** na porta conectada ao lado *Speed* dos motores.
Portanto, vá até a aba ``||Pins:Pins||`` e selecione o bloco ``||Pins:gravação analógica pin P0 para 1023||``. 
Altere seus campos para a porta ``||Pins:P12||`` e o valor **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(2000)
    pins.analogWritePin(AnalogPin.P12, 0)
})
```

## Step 14

Para finalizarmos nosso programa, precisamos atribuir um botão para interromper o movimento do carrinho a qualquer momento. 
Então, acesse a aba ``||Input:Input||`` e adicione mais um laço ``||Input:no botão A pressionado||`` ao código. Altere de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.B, function () {
	
})
```

## Step 15

Neste caso, podemos enviar **0** na porta que usamos para controlar a velocidade dos motores. Ou seja, vá até a aba ``||Pins:Pins||``
e insira o bloco ``||Pins:gravação analógica pin P0 para 1023||`` dentro do laço ``||Input:no botão B pressionado||``. Altere para a porta ``||Pins:P12||`` e substitua o **1023** por **0**. 

```blocks
input.onButtonPressed(Button.B, function () {
    pins.analogWritePin(AnalogPin.P12, 0)
})
```

## Step 16

Pronto! Você já pode testar seu carrinho. Lembre-se de que você pode modificar 
o código para alterar a trajetória que o carrinho vai percorrer.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
    basic.pause(4000)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
    basic.pause(2000)
    pins.analogWritePin(AnalogPin.P12, 0)
})
input.onButtonPressed(Button.B, function () {
    pins.analogWritePin(AnalogPin.P12, 0)
})
```