# Pêndulo

## Step 1

Nesta atividade, vamos construir um pêndulo para visualizarmos a transferência de energia entre as esferas ao colidirem. Portanto, criaremos um código para controlar o servo motor e outro para ler o sensor infravermelho para identificarmos
que a esfera recebeu e conservou energia suficiente para alcançar o outro lado.

## Step 2

Começaremos pelo laço ``||Basic:no iniciar||``, presente na aba ``||Basic:Básico||``. Dentro dele, adicione o bloco ``||Pins:gravação digital pin P0 para 0||``, encontrado na aba ``||Pins:Pins||`` dentro da seção **Avançado**. Altere o campo da porta de pin ``||Pins:P0||`` para pin ``||Pins:P8||``.

```blocks
pins.digitalWritePin(DigitalPin.P8, 0)
```

## Step 3

Em seguida, crie uma variável denominada ``||Variables:Servo acionado||`` acessando a aba ``||Variables:Variáveis||``. Então, adicione um bloco de ``||Variables:definição||`` dentro do laço ``||Basic:no iniciar||``.
Vamos defini-la como ``||Logic:falso||``, utilizando o bloco triangular pertencente à aba ``||Logic:Lógica||``.

```blocks
pins.digitalWritePin(DigitalPin.P8, 0)
let Servo_acionado = false
```

## Step 4

Feito isso, retorne à aba ``||Basic:Básico||`` e insira o bloco mostrar ícone. O ``||Basic:ícone||`` escolhido para ser exibido foi o do alvo, um losango com um LED apagado em seu centro.

```blocks
pins.digitalWritePin(DigitalPin.P8, 0)
let Servo_acionado = false
basic.showIcon(IconNames.Target)
```

## Step 5 

Acesse a aba ``||Input:Input||`` e adicione dois laços ``||Input: no botão A pressionado||``. Altere o segundo de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
pins.digitalWritePin(DigitalPin.P8, 0)
let Servo_acionado = false
basic.showIcon(IconNames.Target)
```

## Step 6

Focando inicialmente no laço ``||Input: no botão A pressionado||``, insira os mesmos blocos que incluímos dentro do laço ``||Basic:no iniciar||``. Entretanto, altere a ``||Pins:gravação digital pin P8||`` para **1** e a definição da variável ``||Variables:Servo acionado||`` de ``||Logic:falso||`` para ``||Logic:verdadeiro||``.
O ``||Basic:ícone||`` também deve ser alterado para o **check**, para indicar ao usuário que o servo foi acionado. 

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P8, 1)
    Servo_acionado = true
    basic.showIcon(IconNames.Yes)
})
```

## Step 7

Para finalizar este laço, vá até a aba ``||Basic:Básico||`` e adicione o comando ``||Basic:limpar tela||``.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P8, 1)
    Servo_acionado = true
    basic.showIcon(IconNames.Yes)
    basic.clearScreen()
})
```

## Step 8

No laço ``||Input:no botão B pressionado||`` teremos exatamente os mesmos comandos inseridos no laço ``||Basic:no inciar||``. Portanto, apenas duplique os três blocos e os adicione dentro do laço do ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P8, 0)
    Servo_acionado = false
    basic.showIcon(IconNames.Target)
})
```

## Step 9

Agora seguimos para o último laço do nosso programa, o laço ``||Basic:sempre||``. Comece adicionando um laço ``||Logic:se então||``, localizado na aba ``||Logic:Lógica||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Step 10

Volte à aba ``||Logic:Lógica||`` e adicione um operador Booleano ``||Logic:E||`` no campo ``||Logic:verdadeiro||`` do laço ``||Logic:se então||``. Em seguida, em cada um dos campos deste operador, adicione um ``||Logic:comparador||``.

```blocks
basic.forever(function () {
    if (0 == 0 && 0 == 0) {
    	
    }
})
```

## Step 11

No primeiro campo, vamos comparar se a variável ``||Variables:Servo acionado||`` é igual a ``||Logic:verdadeiro||``.

```blocks
basic.forever(function () {
    if (Servo_acionado == true && 0 == 0) {
    	
    }
})
```

## Step 12

Do outro lado, avaliaremos se a ``||Pins:leitura digital||`` do pin ``||Pins:P1||`` é igual a **1**. O bloco leitura digital é encontrado na aba ``||Pins:Pins||``. Lembre-se de alterar do pin ``||Pins:P0||`` para ``||Pins:P1||``.

```blocks
basic.forever(function () {
    if (Servo_acionado == true && pins.digitalReadPin(DigitalPin.P1) == 1) {
    	
    }
})
```

## Step 13

Dentro deste laço, ou seja, quando ambas as condições forem atendidas, vamos emitir um som com o alto falante do Micro:bit V.2. Para isso, acesse a aba ``||Music:Música||`` e selecione o bloco ``||Music:play sound until done||``, encontrado mais no final da lista de comandos.

```blocks
basic.forever(function () {
    if (Servo_acionado == true && pins.digitalReadPin(DigitalPin.P1) == 1) {
        music.playSoundEffect(music.createSoundEffect(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), SoundExpressionPlayMode.UntilDone)
    }
})
```

## Step 14

Neste bloco existem dois campos editáveis. No primeiro, você pode controlar o tipo de som que será emitido, como sua forma de onda, frequência, volume e duração. Nós alteramos somente a ``||Music:duração||`` de **500ms** para **1000ms**.
No outro campo, podemos definir se o som será tocado sozinho ou em segundo plano ``||Music:(background)||``. Alteramos para que ele seja tocado no em segundo plano, enquanto o Micro:bit executa os próximos comandos que adicionaremos.

```blocks
basic.forever(function () {
    if (Servo_acionado == true && pins.digitalReadPin(DigitalPin.P1) == 1) {
        music.playSoundEffect(music.createSoundEffect(WaveShape.Sine, 5000, 0, 255, 0, 1000, SoundExpressionEffect.None, InterpolationCurve.Linear), SoundExpressionPlayMode.InBackground)
    }
})
```

## Step 15

Agora, vamos apenas adicionar três blocos de ``||Basic:mostrar ícone||`` e um de ``||Basic:limpar tela||``, todos pertencentes à aba ``||Basic:Básico||``. Assim, criaremos uma animação para ser exibida na tela do Micro:bit enquanto o som é tocado.

```blocks
basic.forever(function () {
    if (Servo_acionado == true && pins.digitalReadPin(DigitalPin.P1) == 1) {
        music.playSoundEffect(music.createSoundEffect(WaveShape.Sine, 5000, 0, 255, 0, 1000, SoundExpressionEffect.None, InterpolationCurve.Linear), SoundExpressionPlayMode.InBackground)
        basic.showIcon(IconNames.Heart)
        basic.showIcon(IconNames.Heart)
        basic.showIcon(IconNames.Heart)
        basic.clearScreen()
    }
})
```

## Step 16

Em nossa animação, escolhemos o ícone do ``||Basic:losango pequeno||``, seguido do ``||Basic:losango maior||`` e finalizamos com o ``||Basic:quadrado grande||``, em que todos os LEDs das bordas estão acesos.

```blocks
basic.forever(function () {
    if (Servo_acionado == true && pins.digitalReadPin(DigitalPin.P1) == 1) {
        music.playSoundEffect(music.createSoundEffect(WaveShape.Sine, 5000, 0, 255, 0, 1000, SoundExpressionEffect.None, InterpolationCurve.Linear), SoundExpressionPlayMode.InBackground)
        basic.showIcon(IconNames.SmallDiamond)
        basic.showIcon(IconNames.Diamond)
        basic.showIcon(IconNames.Square)
        basic.clearScreen()
    }
})
```

## Step 17

Transfira seu programa para o Micro:bit e use o ``||Input:botão A||`` para soltar o pêndulo e o ``||Input:botão B||`` botão B para retornar o servo a sua posição inicial. Verifique se o Micro:bit está emitindo o som a partir da detecção da esfera pelo sensor infravermelho posicionado do outro lado.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P8, 1)
    Servo_acionado = true
    basic.showIcon(IconNames.Yes)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P8, 0)
    Servo_acionado = false
    basic.showIcon(IconNames.Target)
})
let Servo_acionado = false
pins.digitalWritePin(DigitalPin.P8, 0)
Servo_acionado = false
basic.showIcon(IconNames.Target)
basic.forever(function () {
    if (Servo_acionado == true && pins.digitalReadPin(DigitalPin.P1) == 1) {
        music.playSoundEffect(music.createSoundEffect(WaveShape.Sine, 5000, 0, 255, 0, 1000, SoundExpressionEffect.None, InterpolationCurve.Linear), SoundExpressionPlayMode.InBackground)
        basic.showIcon(IconNames.SmallDiamond)
        basic.showIcon(IconNames.Diamond)
        basic.showIcon(IconNames.Square)
        basic.clearScreen()
    }
})
```