# Termostato Digital

## Step 1

Neste tutorial, você irá aprender a fazer um termômetro digital usando o micro:bit.

## Step 2

Primeiramente, acesse a categori ``||basic:Básico||`` e pegue o bloco 
``||basic:mostrar número||``. Então, coloque esse bloco dentro do laço 
``||basic:sempre||``. O bloco ``||basic:mostrar número||`` será usado para exibir  
o um número na matriz de LEDs do Micro:bit, neste caso, o valor da temperatura ambiente.

```blocks
basic.forever(function () {
    basic.showNumber(0)
})

```

## Step 3

Entretanto, ainda precisamos pegar o valor da temperatura. A boa notícia é que o próprio Micro:bit 
já possui um sensor de temperatura integrado. Para utilizá-lo, vá até a aba 
``||input:Input||``, selecione o bloco circular ``||input:temperatura||`` e posicione-o 
dentro do espaço circular do comando ``||basic:mostrar número||``, 
substituindo o número **0**.

```blocks

basic.forever(function () {
    basic.showNumber(input.temperature())
})

```

## Step 4
Pronto! Você já pode carregar seu código para o micro:bit e testar seu termômetro digital!