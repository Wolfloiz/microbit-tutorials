# Catapulta

## Step 1

Nesta atividade vamos programar um jogo envolvendo o uso da catapulta construída. Usaremos o Bit Potenciômetro para controlar sua mira e o Bit Botão para dispararmos o projétil.
 
 Ao disparar, o jogador deve pressionar os botões A ou B para indicar se acertou ou errou a tentativa. Se errar três vezes, o jogador passa a vez e o jogo se reinicia exibindo sua pontuação.

## Step 2

Começaremos pelo laço ``||Basic:no iniciar||`` presente na aba ``||Basic:Básico||``. Dentro dele, adicionaremos dois comandos pertencentes à aba ``||Game:Jogo||``, acessível ao clicar em **Avançado**.
Os blocos em questão são ``||Game:definir pontuação 0||`` e ``||Game:set life 0||``.

```blocks
game.setScore(0)
game.setLife(0)
```

## Step 3

Em seguida, altere o número de ``||Game:vidas||`` no segundo bloco de **0** para **3**. Fique livre para usar outros valores, pois este dado determina o número de vezes que o jogador pode errar.

```blocks
game.setScore(0)
game.setLife(3)
```

## Step 4

Volte à aba ``||Basic:Básico||`` e adicione o bloco ``||Basic:mostrar ícone||`` para indicarmos que o o jogador já pode iniciar sua tentativa. 
Sugerimos o ícone do quadrado pequeno, mas isso pode ser alterado de acordo com sua preferência.

```blocks
game.setScore(0)
game.setLife(3)
basic.showIcon(IconNames.SmallSquare)
```

## Step 5

Agora, vá até a aba ``||Input:Input||`` e adicione **três** laços ``||Input:no botão A pressionado||``. Altere dois deles para o ``||Input:botão B||`` e a combinação de ``||Input:botões A+B||``. 

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.AB, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
game.setScore(0)
game.setLife(3)
basic.showIcon(IconNames.SmallSquare)
```

## Step 6

Dentro do primeiro laço ``||Input:no botão A pressionado||``, vamos inserir o bloco ``||Game: alterar pontuação em 1||``, localizado na aba ``||Game:Jogo||``. Portanto, o ``||Input:botão A||`` deve ser pressionado quando o jogador acertar o alvo, por isso estamos somando **1** a sua ``||Game:pontuação||``.

```blocks
input.onButtonPressed(Button.A, function () {
    game.addScore(1)
})
```

## Step 7

Quando pressionarmos o ``||Input:no botão B||``, significa que erramos o alvo. Por isso, vamos inserir, no laço ``||Input:no botão B pressionado||``, o bloco ``||Game:remove life||``, também pertencente à aba ``||Game:Jogo||``.
Altere o valor deste bloco de **0** para **1**.

```blocks
input.onButtonPressed(Button.B, function () {
    game.removeLife(1)
})
```

## Step 8

No terceiro laço, quando pressionarmos os ``||Input:botões A+B||``, vamos finalizar e reiniciar a brincadeira, mostrando a pontuação acumulada com o bloco ``||Game:fim do jogo||`` encontrado na aba ``||Game:Jogo||``.

```blocks
input.onButtonPressed(Button.AB, function () {
    game.gameOver()
})
```

## Step 9

Agora, retorne à aba ``||Basic:Básico||`` e adicione o laço ``||Basic:sempre||`` para programarmos o controle de mira e disparo da catapulta.

```blocks
input.onButtonPressed(Button.A, function () {
    game.addScore(1)
})
input.onButtonPressed(Button.AB, function () {
    game.gameOver()
})
input.onButtonPressed(Button.B, function () {
    game.removeLife(1)
})
game.setScore(0)
game.setLife(3)
basic.showIcon(IconNames.SmallSquare)
basic.forever(function () {
	
})
```

## Step 10

Acesse a aba ``||Variables:Variáveis||`` e crie as variáveis ``||Variables:Mira||`` e ``||Variables:Disparo||``. Em seguida, adicione um bloco de ``||Variables:definição||`` para cada uma delas dentro do laço ``||Basic:sempre||``. 

```blocks
basic.forever(function () {
    Mira = 0
    Disparo = 0
})
```

## Step 11

A variável ``||Variables:Mira||`` será definida como a ``||Pins:leitura analógica pin P0||``, localizado na aba ``||Pins:Pins||``, dentro da seção **Avançado**.

```blocks
basic.forever(function () {
    Mira = pins.analogReadPin(AnalogPin.P0)
    Disparo = 0
})
```

## Step 12

Já a variável ``||Variables:Disparo||`` será definida como a ``||Pins:leitura digital pin P2||``, também pertencente à aba ``||Pins:Pins||``. Lembre-se de alterar de ``||Pins:P0||`` para ``||Pins:P2||``.

```blocks
basic.forever(function () {
    Mira = pins.analogReadPin(AnalogPin.P0)
    Disparo = pins.digitalReadPin(DigitalPin.P2)
})
```

## Step 13

Abaixo dos dois blocos de definição, adicione uma ``||Pins:gravação analógica||`` e uma ``||Pins:gravação digital||``, ambos situados na aba ``||Pins:Pins||``.

```blocks
basic.forever(function () {
    Mira = pins.analogReadPin(AnalogPin.P0)
    Disparo = pins.digitalReadPin(DigitalPin.P2)
    pins.analogWritePin(AnalogPin.P0, 1023)
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

## Step 14

Para a ``||Pins:gravação analógica||``, devemos alterar o pin de ``||Pins:P0||`` para ``||Pins:P8||``. Além disso, o dado a ser gravado não será o número **1023**, será a variável ``||Variables:Mira||``.

```blocks
basic.forever(function () {
    Mira = pins.analogReadPin(AnalogPin.P0)
    Disparo = pins.digitalReadPin(DigitalPin.P2)
    pins.analogWritePin(AnalogPin.P8, Mira)
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

## Step 15

Por fim, a ``||Pins:gravação digital||`` deve ser feita na porta ``||Pins:P16||`` com o valor da variável ``||Variables:Disparo||``.

```blocks
basic.forever(function () {
    Mira = pins.analogReadPin(AnalogPin.P0)
    Disparo = pins.digitalReadPin(DigitalPin.P2)
    pins.analogWritePin(AnalogPin.P8, Mira)
    pins.digitalWritePin(DigitalPin.P16, Disparo)
})
```

## Step 16

Transfira seu código para o Micro:bit e tente acertar alvos com a catapulta. Aproveite para alterar as regras do jogo para desenvolver suas habilidades de programação.


```blocks
input.onButtonPressed(Button.A, function () {
    game.addScore(1)
})
input.onButtonPressed(Button.AB, function () {
    game.gameOver()
})
input.onButtonPressed(Button.B, function () {
    game.removeLife(1)
})
let Disparo = 0
let Mira = 0
game.setScore(0)
game.setLife(3)
basic.showIcon(IconNames.SmallSquare)
basic.forever(function () {
    Mira = pins.analogReadPin(AnalogPin.P0)
    Disparo = pins.digitalReadPin(DigitalPin.P2)
    pins.analogWritePin(AnalogPin.P8, Mira)
    pins.digitalWritePin(DigitalPin.P16, Disparo)
})
```
