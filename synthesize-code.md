# Sintetizador

## Step 1

Neste tutorial, vamos utilizar o Micro:bits com os Bits Potenciômetro e Sensor infravermelho
para produzir diferentes tipos de sons com o alto falante. A proposta é criar a base lógica
para experimentação criativa, como um sintetizador.

## Step 2

Primeiramente, acesse a aba ``||Input:Input||`` e inclua três laços: ``||Input:no botão A pressionado||``,  ``||Input:no botão B pressionado||``
e  ``||Input:no logotipo pressionado||``. Usaremos estes três dispositivos de entrada para criar sons distintos.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
```

## Step 3

Em seguida, vá até a categoria ``||Music:Música||``, desça para os últimos blocos (Micro:bit V2)
e selecione três comandos ``||Music:play (gráfico) until done||``. Coloque cada bloco dentro
de cada laço adicionado no passo anterior.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
```

## Step 4

Clique no gráfico dentro destes blocos para abrir o editor do som que será produzido. 
Por padrão, temos inicialmente uma onda senoidal, com duração de 500ms, frequência inicial de 5000Hz
e final de 1Hz, volume inicial de 255 e final 0. Clique no símbolo de *play* para escutar
o som produzido por estas configurações.

```blocks
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
```

## Step 5

Agora, teste algumas alterações destas características do som que será tocado em cada botão.
Você pode alterar a forma de onda para: **quadrada** (*square*), **dente de serra** (*sawtooth*),
**triangular** (triângulo) e **ruído** (noise). Teste cada caso e escolha os que gostou mais.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Noise, 5000, 0, 255, 0, 500, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
```

## Step 6

Feito isso, experimente alterar a duração e as características da frequência no primeiro quadro do editor, como as frequências iniciais e finais,
além dos efeitos (vibrato, tremolo e warble) e tipo de interpolação (linear, curva ou logarítmica).

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 1, 255, 0, 500, SoundExpressionEffect.Warble, InterpolationCurve.Logarithmic), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 2387, 0, 255, 2000, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Noise, 5000, 0, 255, 0, 1000, SoundExpressionEffect.Tremolo, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
```

## Step 7

Neste momento, vamos programar os sons gerados pelo Potenciômetro e pelo Sensor infravermelho.
Para isso, acesse a categoria ``||Basic:Básico||`` e selecione o laço ``||Basic:sempre||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 1, 255, 0, 500, SoundExpressionEffect.Warble, InterpolationCurve.Logarithmic), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 2387, 0, 255, 2000, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Noise, 5000, 0, 255, 0, 1000, SoundExpressionEffect.Tremolo, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
basic.forever(function () {
	
})
```

## Step 8

Retorne à aba ``||Music:Música||`` e adicione dois blocos ``||Music:play tone C Médio for 1 batida until done||`` 
dentro do laço ``||Basic:sempre||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 1, 255, 0, 500, SoundExpressionEffect.Warble, InterpolationCurve.Logarithmic), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 2387, 0, 255, 2000, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Noise, 5000, 0, 255, 0, 1000, SoundExpressionEffect.Tremolo, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
basic.forever(function () {
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
})
```

## Step 9

Acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione dois blocos
``||pins:leitura analógica pin P0||``. Altere de porta **P0** para as portas **P1** e **P2** e insira esse blocos
nos comandos ``||Music:play tone C Médio for 1 batida until done||`` substituindo o tom ``||Music:C Médio||`` pelas ``||pins:leituras analógicas||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 1, 255, 0, 500, SoundExpressionEffect.Warble, InterpolationCurve.Logarithmic), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 2387, 0, 255, 2000, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Noise, 5000, 0, 255, 0, 1000, SoundExpressionEffect.Tremolo, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
basic.forever(function () {
    music.play(music.tonePlayable(pins.analogReadPin(AnalogPin.P1), music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    music.play(music.tonePlayable(pins.analogReadPin(AnalogPin.P2), music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
})
```

## Step 10

Por fim, altere a quantidade de batidas que cada um destes tons tocarão. O primeiro bloco da ``||pins:leitura analógica pin P1||``
deve tocar por **1/16** batidas. O segundo comando, da ``||pins:leitura analógica pin P2||`` deve tocar por **1/8**.

Teste o resultado dessas alterações e sinta-se livre para improvisar e criar novos sons.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Triangle, 1, 5000, 255, 0, 2000, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 1, 255, 0, 2000, SoundExpressionEffect.Tremolo, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 1, 255, 0, 1000, SoundExpressionEffect.Vibrato, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
basic.forever(function () {
    music.play(music.tonePlayable(pins.analogReadPin(AnalogPin.P1), music.beat(BeatFraction.Sixteenth)), music.PlaybackMode.UntilDone)
    music.play(music.tonePlayable(pins.analogReadPin(AnalogPin.P2), music.beat(BeatFraction.Eighth)), music.PlaybackMode.UntilDone)
})
```

## Step 11

Este projeto é uma atividade introdutória para descobrirmos as funcionalidades musicais do Micro:bit. Utilize-o como base
para experimentar as infinitas possibilidades e use sua criatividade para se expressar.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    music.play(music.createSoundExpression(WaveShape.Triangle, 1, 5000, 255, 0, 2000, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.A, function () {
    music.play(music.createSoundExpression(WaveShape.Sine, 5000, 1, 255, 0, 2000, SoundExpressionEffect.Tremolo, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
input.onButtonPressed(Button.B, function () {
    music.play(music.createSoundExpression(WaveShape.Square, 5000, 1, 255, 0, 1000, SoundExpressionEffect.Vibrato, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
})
basic.forever(function () {
    music.play(music.tonePlayable(pins.analogReadPin(AnalogPin.P1), music.beat(BeatFraction.Sixteenth)), music.PlaybackMode.UntilDone)
    music.play(music.tonePlayable(pins.analogReadPin(AnalogPin.P2), music.beat(BeatFraction.Eighth)), music.PlaybackMode.UntilDone)
})
```
