# 002 Luz Automática

## Step 1

Neste tutorial, você irá aprender a fazer um sistema que acende luzes automaticamente 
quando o ambiente fica escuro.

## Step 2

Primeiramente, acesse a aba ``||logic:Lógica||`` e selecione o laço 
``||logic:se-verdadeiro-então-senão||``. Em seguida, coloque esse bloco dentro do laço ``||basic:sempre||``. 

```blocks
basic.forever(function () {
    if (true) {

    } else {

    }
})
```

## Step 3

Retorne à aba ``||logic:Lógica||`` e pegue o bloco triangular comparador
``||logic:0 < 0||``. Posicione-o dentro do espaço triangular ``||logic:verdadeiro||`` do laço 
``||logic:se-verdadeiro-então-senão||``.

```blocks
basic.forever(function () {
    if (0 < 0) {

    } else {

    }
})
```

## Step 4

Agora, precisamos incluir o valor do nível de luz, para poder verificar se está claro 
ou escuro. Portanto, acesse a categoria ``||input:Input||``, selecione o bloco circular ``||input:nível de luz||`` 
e o poscione dentro do primeiro espaço circular do bloco comparador ``||logic:0 < 0||``, substituindo o primeiro **0**.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 0) {

    } else {

    }
})
```

## Step 5

O nível de luz indica a luminosidade como um valor entre **0** (muito escuro) e **255** 
(muito claro). Para esta atividade, desejamos que a luz acenda quando o nível de luz for menor 
que **200**. Então, no bloco ``||logic:nível de luz < 0||``, substitua o valor **0** por **200**.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 200) {

    } else {

    }
})
```

## Step 6

Por fim, é necessário enviar os comandos para acender e apagar a "luz" (matriz de LEDs), de acordo com a 
necessidade. Logo, acesse a categoria ``||basic:Básico||``, selecione o bloco ``||basic:mostrar leds||`` e o posicione 
dentro do laço ``||logic:então||``. Preencha o bloco ``||basic:mostrar leds||``, para que todos os LEDs se acendam.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 200) {
        basic.showLeds(`
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            `)
    } else {

    }
})
```

## Step 7

Para apagar a luz quando estiver claro, retorne à aba ``||basic:Básico||`` e insira o bloco ``||basic:limpar tela||`` no laço``||logic:senão||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() < 200) {
        basic.showLeds(`
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            `)
    } else {
        basic.clearScreen()
    }
})
```

## Step 8
Pronto! Você já pode carregar seu código para o micro:bit e testar sua luz automática.