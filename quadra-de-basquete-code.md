# Marcador de Cestas de Basquete Automático

## Step 1

Neste tutorial, você irá aprender a fazer um sistema para marcar o número 
de cestas de basquete automaticamente, através do bit de Sensor Infravermelho.

## Step 2

Primeiramente, acesse a categoria ``||logic:Lógica||`` e selecione o laço 
``||logic:se-verdadeiro-então|``. Em seguida, coloque esse laço dentro do ``||basic:sempre||``. 

```blocks
basic.forever(function () {
    if (true) {

    }
})
```

## Step 3

Retorne à aba ``||logic:Lógica||`` e selecione o bloco triangular comparador ``||logic:0 > 0||``. 
Posicione-o dentro do espaço triangular do comando ``||logic:se-verdadeiro-então||``, substituindo a palavra **verdadeiro**.

```blocks
basic.forever(function () {
    if (0 > 0) {

    }
})
```

## Step 4

Agora, acesse a seção **Avançado** e, na categoria ``||pins:Pins||``, selecione o bloco circular
``||pins:leitura analógica pin P0||``. Posicione esse bloco dentro de ``||logic:0 > 0||``, 
substituindo o primeiro **0** e modifique sua porta de **P0** para **P2**. Feito isso, altere o segundo valor de **0** para **850**.

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P2) > 850) {
    	
    }
})
```

## Step 5

Então, acesse a aba ``||variables:Variáveis||`` e clique em **Fazer uma variável**.
Nomeie essa variável como ``||variables:Cestas||``.

## Step 6

Ainda na aba ``||variables:Variáveis||``, selecione o bloco ``||variables:alterar Cestas por 1||``.
Posicione esse bloco dentro do laço ``||logic:se-verdadeiro-então||``. 
Desse modo, através da variável, a pontuação está sendo marcada, 
mas ainda devemos exibir a contagem na matriz de LEDs do Micro:bit. 

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P2) > 850) {
    	Cestas += 1
    }
})
```

## Step 7

Para isso, acesse a aba ``||basic:Básico||``, selecione o comando ``||basic:mostrar número||`` e coloque-o 
abaixo do bloco ``||variables:alterar Cestas por 1||``.

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P2) > 850) {
    	Cestas += 1
        basic.showNumber(0)
    }
})
```

## Step 8

Retorne à aba ``||variables:Variáveis||`` e escolha o bloco arredondado 
``||variables:Cestas||``. Posicione-o dentro do espaço do bloco ``||basic:mostrar número||``, substituindo o número **0**.

```blocks
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P2) > 850) {
    	Cestas += 1
        basic.showNumber(Cestas)
    }
})
```

## Step 9

Por fim, acesse a aba ``||basic:Básico||``, selecione o bloco ``||basic:pausa||`` 
e coloque-o abaixo do comando ``||basic:mostrar número||``, alterando o valor de **100** para 
**5000**. Esse bloco de pausa evita que o contador automático conte a mesma cesta 
mais de uma vez. Portanto, caso necessário, ajuste para que você consiga tirar a bola de 
dentro da cesta neste intervalo de tempo.

```blocks
let Cestas = 0
basic.forever(function () {
    if (pins.analogReadPin(AnalogPin.P2) > 850) {
        Cestas += 1
        basic.showNumber(Cestas)
        basic.pause(5000)
    }
})
```

## Step 10

Pronto! Agora você já pode tentar marcar umas cestas sem se preocupar em perder a conta.
