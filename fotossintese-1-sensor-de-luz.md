

## Step 1

Vamos começar ligando o micro:bit ao adaptador, e conectando também o sensor 
de luz ao adaptador.

## Step 2

Agora vamos aprender a usar esse sensor pra medir a quantidade de luz no 
ambiente.

## Step 3

Primeiro, vamos pegar o bloco ``||basic:Mostrar Número||``, que pode ser achado 
na aba ``||basic:Básico||``, e colocá-lo dentro do laço ``||basic:sempre||``

```blocks
basic.forever(function () {
    basic.showNumber(0)
})
```

## Step 4

Para mostrarmos a quantidade de luz (em número), vamos precisar ir na aba 
``||pins:Pins||`` e pegar o bloco ``||pins:leitura analógica pin P0||``. 
Vamos então colocar esse bloco dentro do bloco ``||basic:Mostrar Número||``.

```blocks
basic.forever(function () {
    basic.showNumber(pins.analogReadPin(AnalogPin.P0))
})

```

## Step 4

Por fim, basta selecionar o pino correto no bloco ``||pins:leitura analógica pin P0||``. 
Esse pino deve ser o mesmo em que conectados o sensor de luz.

## Step 5

Pronto, já podemos usar o micro:bit para medir a luz do ambiente. O valor de luz pode ir 
de 0 (escuro) até 1023 (muito claro). E então, quão claro está sua sala agora?
