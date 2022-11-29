```package
datalogger=github:pxt-microbit/tree/master/libs/datalogger
```
```package
fuzzyLibrary=github:Wolfloiz/pxt-fuzzyLibrary
```
# My Tutorial

### @activities 1

## Introdução

### Introduction step

# Carro elétrico 
Neste projeto, vamos construir um veículo com quatro rodas e dois motores, 
que variam a velocidade de acordo com a posição do ponteiro do nosso potenciômetro.

## Parte 1 - Ligar e desligar o carrinho

### Step 1
# Parte 1 - ligar e desligar o carro
Vamos começar programando os ``||input:botões A||`` e ``||input:B||`` para ligar e desligar nosso veículo. Para isso,
vá até a aba ``||input:Input||`` e adicione o primeiro laço ``||Input:No botão A pressionado||``.

```blocks
basic.forever(function () {
fuzzyLibrary.servo2(fuzzyLibrary.servoPorts.P1, 0)
    datalogger.log(datalogger.createCV("", 0))
})
```

### Step 2
Vamos criar a variável ``||Variables:Ligar||`` utilizando a aba ``||Variables:Variáveis||``. Em seguida, adicione o bloco ``||Variables:definir Ligar para 0||``. Substitua o algarismo **0** por **1**.

```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
```
### Step 3
Agora, devemos indicar ao usuário que o veículo foi ligado. Para isso, utilizamos o bloco ``||Basic:mostrar ícone||`` com o sinal de visto (*check*).

```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
```
### Step 4
Neste momento, finalizamos o código para ligar o carro. Mas ainda precisamos programar seu desligamento.

 Clique com o botão direito no laço ``||Input:no botão A pressionado||`` e o duplique. Em seguida, altere de ``||Input:botão A||`` para ``||Input:botão B||``. 
```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
```
### Step 5
Para finalizar esta parte, altere o número do bloco de ``||Variables:definição da variável||`` de **1** para **0**. Além disso, substitua o item de *check* para o *X*.

```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
    basic.showIcon(IconNames.No)
})
```
### Step 6
Envie o código para o Micro:bit e teste se o ícone se altera quando os ``||input:botões A||`` e ``||input:B||`` são pressionados.

## Parte 2 - Ler potenciômetro

### Step 1
# Parte 2 - Ler potenciômetro
Nesta parte, vamos programar como o Micro:bit pode entender a posição do ponteiro do bloco potenciômetro para, posteriormente,
usarmos essa leitura para controlar a velocidade dos motores.
### Step 2
Para começar, apague todos os blocos da parte anterior. Adicione um laço ``||Basic:sempre||`` presente na aba ``||Basic:Básico||``.
```blocks
basic.forever(function () {
	
})
```
### Step 3
Crie uma ``||Variables:variável||`` chamada ``||Variables:Velocidade||`` e adicione seu bloco de ``||Variables:definição||`` dentro do laço ``||Basic:sempre||``.
```blocks
let Velocidade = 0
basic.forever(function () {
    Velocidade = 0
})
```
### Step 4
Vamos definir essa variável como o valor lido pelo Micro:bit na porta em que conectamos o potenciômetro. Ou seja, utilizaremos o bloco ``||Pins:leitura analógica pin P0||`` presente na aba ``||Pins:Pins||``, do menu **Avançado** no final da lista.
```blocks
let Velocidade = 0
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P0)
})
```
### Step 5
Em seguida, devemos alterar o pino de ``||Pins:P0||`` para ``||Pins:P1||``, pois foi onde conectamos o potenciômetro.
```blocks
let Velocidade = 0
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
})
```
### Step 6
Agora, devemos apenas mostrar o valor da ``||Variables:variável||`` ao usuário. Acione o bloco ``||Basic:mostrar número||``, presente na aba ``||Basic:Básico||``. Feito isso, insira a variável ``||Variables:Velocidade||`` no espaço circular
especificar o dado que será exibido.
```blocks
let Velocidade = 0
basic.forever(function () {
    Velocidade = pins.analogReadPin(AnalogPin.P1)
    basic.showNumber(Velocidade)
})
```
### Step 7
Transfira o código para o Micro:bit e teste o programa girando o ponteiro do potenciômetro. É necessário aguardar a exibição do valor nos LEDs do Micro:bit antes de alterar a posição do ponteiro
para se ter uma leitura condizente com a posição atual. 
## Parte 3 - Acionar os motores

### Step 1
# Parte 3 - Acionar os motores
Nesta parte, vamos construir um programa para comandar os motores com o Micro:bit, fazendo com que eles girem e alterem suas velocidades.
Para começarmos, apague os blocos da parte anterior.

### Step 2
Inicie com um laço ``||Basic:sempre||`` presente na aba ``||Basic:Básico||``. Em seguida, adicione dois blocos de ``||Pins:gravação analógica pin P0 para 1023||``, localizado na aba ``||Pins:Pins||``,
na seção de abas **avançadas**.
```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P0, 1023)
    pins.analogWritePin(AnalogPin.P0, 1023)
})
```
### Step 3
Altere as portas de ``||Pins:P0||`` para ``||Pins:P13||`` e ``||Pins:P15||``, pois são os pinos onde conectamos os dois motores. O valor **1023** significa que os motores serão acionados na velocidade máxima. 
```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P13, 1023)
    pins.analogWritePin(AnalogPin.P15, 1023)
})
```
### Step 4
Agora, vamos determinar por quanto tempo os motores giram em velocidade máxima. Para isso, adicone um bloco ``||Basic:pausa (ms)||``, localizado na aba ``||Basic:Básico||``, e altere seu valor para **2 segundos (2000ms)**.
```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P13, 1023)
    pins.analogWritePin(AnalogPin.P15, 1023)
    basic.pause(2000)
})
```
### Step 5
Neste momento, vamos repetir a lógica usada, mas alterar o código para que os motores girem mais lentamente.
Para isso, duplique os blocos ``||Pins:gravação analógica pin P13 e P15||`` e altere os valores de **1023** para **512**.
```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P13, 1023)
    pins.analogWritePin(AnalogPin.P15, 1023)
    basic.pause(2000)
    pins.analogWritePin(AnalogPin.P13, 512)
    pins.analogWritePin(AnalogPin.P15, 512)
})
```
### Step 6
Depois disso, duplique a ``||Basic:pausa (ms)||`` para que eles se mantenham assim por **2 segundos**.
```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P13, 1023)
    pins.analogWritePin(AnalogPin.P15, 1023)
    basic.pause(2000)
    pins.analogWritePin(AnalogPin.P13, 512)
    pins.analogWritePin(AnalogPin.P15, 512)
    basic.pause(2000)
})
```
### Step 7
Por fim, repetimos essa estrutura para estabelecer que os motores fiquem parados por **2 segundos**. 
Então, duplique os blocos das ``||Pins:gravações analógicas pin P13 e P15||`` e altere seus valores para **0**. Lembre-se de repetir a ``||Basic:pausa (ms)||`` também! 
```blocks
basic.forever(function () {
    pins.analogWritePin(AnalogPin.P13, 1023)
    pins.analogWritePin(AnalogPin.P15, 1023)
    basic.pause(2000)
    pins.analogWritePin(AnalogPin.P13, 512)
    pins.analogWritePin(AnalogPin.P15, 512)
    basic.pause(2000)
    pins.analogWritePin(AnalogPin.P13, 0)
    pins.analogWritePin(AnalogPin.P15, 0)
    basic.pause(2000)
})
```
## Parte 4 - Juntando os códigos

### Step 1
# Parte 4 - Juntando os códigos
Na última parte, vamos juntar o que aprendemos em cada um dos códigos até então, para programar um veículo
que conseguimos alterar sua velocidade com o potenciômetro, além de ligá-lo e desligá-lo com os botões A e B.

### Step 2
Comece excluindo todos os blocos da parte anterior. Em seguida, crie duas ``||Variables:variáveis||``: ``||Variables:Ligar||`` e ``||Variables:Velocidade||``.

### Step 3
Vamos construir novamente os casos em que ligamos e desligamos o veículo com os botões. Adicione dois laços: ``||Input: no botão A pressionado||`` e ``||Input: no botão B pressionado||``, presentes na aba ``||Input:Input||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
```
### Step 4
Então, adicionamos blocos para ``||Variables:definir||`` a variável ``||Variables:Ligar||``. Dentro do laço do ``||Input:botão A||``, vamos defini-la como **1**. Já no ``||Input:botão B||``, vamos defini-la como **0**.

```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
```
### Step 5
Adicione os blocos para ``||Basic:mostrar os ícones||`` de *check* no ``||Input:botão A||`` e *X* no ``||Input:botão B||``. Este comando está presente na aba ``||Basic:Básico||``.
```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
    basic.showIcon(IconNames.No)
})
```

### Step 6
Agora, vamos inserir um laço ``||Basic:sempre||`` para controlarmos a velocidade dos motores com o potenciômetro.

```blocks
let Ligar = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
    basic.showIcon(IconNames.No)
})
basic.forever(function () {
	
})
```
### Step 7
Vá até a aba ``||Logic:Lógica||`` e selecione o laço ``||Logic:Se verdadeiro então||``, posicionando-o dentro do laço ``||Basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})
```

### Step 8
Volte à aba ``||Logic:Lógica||`` e insira o bloco ``||Logic:comparador||`` no campo **verdadeiro** do laço ``||Logic:Se-então||``.
```blocks
basic.forever(function () {
    if (0 == 0) {
    	
    }
})
```

### Step 9
Vá até a aba ``||Variables:Variáveis||`` e selecione a variável ``||Variables:Ligar||`` para ficar no primeiro campo do ``||Logic:comparador||``. 
Em seguida, altere o valor de **0** para **1**, se tornando **Ligar = 1**.
```blocks
basic.forever(function () {
    if (Ligar == 1) {
    	
    }
})
```

### Step 10
Se ``||Variables:Ligar||`` é igual a **1**, significa que o  ``||Input:botão A||`` foi pressionado e o veículo está ligado. Portanto, devemos definir a velocidade do carro para acionar os motores.
Para isso, adicione o bloco ``||Variables:definir Velocidade para 0||`` encontrado em ``||Variables:Variáveis||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = 0
    }
})
```
### Step 11
Agora, vamos atribuir o valor do potenciômetro para essa variável. Então, substitua o **0** pela ``||Pins:leitura analógica pin P0||``, situado na aba ``||Pins:Pins||``. 
Altere o pino de ``||Pins:P0||`` para ``||Pins:P1||``, pois é a porta onde conectamos o potenciômetro.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
    }
})
```
### Step 12
Feito isso, adicione dois blocos de ``||Pins:gravação analógica pin P0 para 1023||``, encontrados na aba ``||Pins:Pins||``. Altere as portas para ``||Pins:P13||`` e ``||Pins:P15||``, pois é onde estão conectados os motores. 

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
        pins.analogWritePin(AnalogPin.P13, 1023)
        pins.analogWritePin(AnalogPin.P15, 1023)
    }
})
```

### Step 13
Substitua os valores **1023** pela variável ``||Variables:Velocidade||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
        pins.analogWritePin(AnalogPin.P13, Velocidade)
        pins.analogWritePin(AnalogPin.P15, Velocidade)
    }
})
```
### Step 14
Em seguida, devemos programar o caso em que ``||Variables:Ligar||`` é igual a **0**, ou seja, quando o veículo é desligado. Para isso, duplique todo o laço ``||Logic:Se-então||`` que acabamos de criar e altere o **Ligar = 1** para **Ligar = 0**.

 **Atenção:** não posicione o novo laço dentro do anterior! Ele deve ficar abaixo do que programamos, dentro do laço ``||Basic:sempre||``.
```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
        pins.analogWritePin(AnalogPin.P13, Velocidade)
        pins.analogWritePin(AnalogPin.P15, Velocidade)
    }
    if (Ligar == 0) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
        pins.analogWritePin(AnalogPin.P13, Velocidade)
        pins.analogWritePin(AnalogPin.P15, Velocidade)
    }
})
```
### Step 15
Exclua o bloco de ``||Variables:definição||`` da velocidade dentro deste laço e altere as ``||Pins:gravações analógicas||`` de ``||Variables:Velocidade||`` para **0**.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
        pins.analogWritePin(AnalogPin.P13, Velocidade)
        pins.analogWritePin(AnalogPin.P15, Velocidade)
    }
    if (Ligar == 0) {
        pins.analogWritePin(AnalogPin.P13, 0)
        pins.analogWritePin(AnalogPin.P15, 0)
    }
})
```
### Step 16
Assim, finalizamos o código do nosso carro elétrico! Transfira o arquivo para o Micro:bit e teste seu veículo alterando a velocidade a partir do potenciômetro e ligando e desligando
através dos botões A e B.

```blocks
let Ligar = 0
let Velocidade = 0
input.onButtonPressed(Button.A, function () {
    Ligar = 1
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
    basic.showIcon(IconNames.No)
})
basic.forever(function () {
    if (Ligar == 1) {
        Velocidade = pins.analogReadPin(AnalogPin.P1)
        pins.analogWritePin(AnalogPin.P13, Velocidade)
        pins.analogWritePin(AnalogPin.P15, Velocidade)
    }
    if (Ligar == 0) {
        pins.analogWritePin(AnalogPin.P13, 0)
        pins.analogWritePin(AnalogPin.P15, 0)
    }
})
```