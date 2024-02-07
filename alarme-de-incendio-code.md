# Alarme de Incêndio

## Step 1

Neste tutorial, você irá aprender a fazer um alarme de incêndio simples, utilizando 
o Micro:bit, os Fuzzy Bits e o Expansor para Micro:bit.

## Step 2

Primeiramente, vá até a aba ``||logic:Lógica||`` e selecione o laço 
``||logic:se-verdadeiro-então|``. Em seguida, coloque esse bloco dentro do laço 
``||basic:sempre||``. 

```blocks
basic.forever(function () {
    if (true) {

    }
})
```

## Step 3

Retorne à aba ``||logic:Lógica||`` e pegue o bloco triangular comparador
``||logic:0 = 0||``. Ele deve ser inserido no espaço triangular do laço 
``||logic:se-verdadeiro-então||``, substituindo a palavra ``||logic:verdadeiro||``.

```blocks
basic.forever(function () {
    if (0 == 0) {

    }
})
```


## Step 4

Agora acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco circular
``||pins:leitura digital pin P0||``. Coloque esse bloco dentro do comparador ``||logic:0 = 0||``, 
substituindo o primeiro **0**.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
    	
    }
})
```

## Step 5

O Bit Botão que utilizamos, envia ao Micro:bit o valor **0** ou **1**. Quando ele está na posição pressionada, 
o valor enviado é **1**. Se você o pressiona novamente, ele volta para sua posição padrão, quando passa a enviar **0**. 
Dessa forma, quando apertarmos o botão, devemos fazer o alarme de incêndio disparar, e ao pressionar outra vez, 
o alarme deve parar.

## Step 6

Para incluir essas instruções no código, vá até a aba ``||music:Música||`` e selecione o bloco ``||music:play tone C Médio for 1 batida until done||``. 
Coloque esse bloco dentro do laço do ``||logic:se-verdadeiro-então||``.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
```
## Step 7

Neste comando, você pode personalizar como será o som do seu alarme. Para isso, experimente outros
tons dentro do campo redondo ``||music:tone||``, e teste a duração de cada toque no campo redondo ``||music:1 batida||``. 

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        music.play(music.tonePlayable(370, music.beat(BeatFraction.Eighth)), music.PlaybackMode.UntilDone)
    }
})
```

## Step 8

Pronto! Seu alarme de incêndio já está funcionando, agora é só testar e se divertir!