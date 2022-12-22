# Intensidade Luminosa

## Step 1

Primeiramente, vamos criar uma ``||variables:variável||`` para salvarmos a informação de nível de luz sendo recebida pelo Micro:bit.
Optamos por nomeá-la como simplesmente ``||variables:luz||``.

## Step 2

Para atribuir um valor à ``||variables:variável||``, vamos adicionar um bloco de definição da ``||variables:variável||`` dentro do laço ``||basic:sempre||``. 

```blocks
let luz = 0
basic.forever(function () {
    luz = 0
})
```

## Step 3

Neste caso, nossa variável deve armazenar a quantidade de luz captada pela ``||input:entrada||`` (sensor) já integrada na placa. 
Então, adicionamos esse dado no círculo do bloco de ``||variables:definição||`` adicionado no passo anterior.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
})
```

## Step 4

Em seguida, vamos avaliar qual o ``||input:nível de luz||`` sendo captado para acionar os LEDs da matriz de acordo com esse valor.
Para isso, adicione um laço ``||logic:se-então||`` com um bloco ``||logic:comparador||``.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (0 == 0) {
    	
    }
})
```

## Step 5
Altere o sinal de igual (**=**) para menor que (**<**). Inicialmente, vamos verificar se nossa variável ``||variables:luz||`` é menor que **50**.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
    	
    }
})
```

## Step 6

Após criar essa condição, devemos estabelecer o que acontecerá se ela for atendida. Portanto, vamos até a aba ``||basic:Básico||``, 
selecionamos o bloco ``||basic:mostrar leds||`` e clicamos sobre os LEDs da primeira linha.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
})
```

## Step 7

Agora, temos duas condições simultâneas: a ``||variables:luz||`` deve ser **maior ou igual a 50**, **E** **menor que 100**.
Então, vamos precisar de um operador booleano ``||logic:"E"||`` (AND) também presente na aba ``||logic:Lógica|``.
Vamos inseri-lo dentro da parte de comparação do nosso laço ``||logic:se-então|``.

*Atenção: cuidado para não adionar um laço se-então dentro do outro. Devem ser laços distintos, um **abaixo** do outro.*

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (false && false) {
    	
    }
})
```

## Step 8

Feito isso, adicionamos dois blocos de ``||logic:comparação||``, um de cada lado do operador ``||logic:E||``.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (0 == 0 && 0 == 0) {
    	
    }
})
```

## Step 9

Neste momento, podemos inserir os valores em cada bloco comparador para testar se ``||variables:luz||`` é **maior ou igual a 50**, **E** **menor que 100**. 
Lembre-se de ajustar os sinais para **maior ou igual** e **menor que**.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (luz >= 50 && luz < 100) {
    	
    }
})
```

## Step 10

Em seguida, devemos inserir o bloco ``||basic:mostrar leds||`` dentro deste laço para ativar os LEDs da segunda linha da matriz do Micro:bit quando as duas condições forem verdadeiras. 

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (luz >= 50 && luz < 100) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            `)
    }
})
```
## Step 11

Agora, vamos replicar o processo para a terceira faixa alterando os dados de acordo com o novo intervalo e adicionando uma linha de LEDs acesos.
Vamos testar se ``||variables:luz||`` é **maior ou igual a 100**, **E** **menor que 150**.

*Dica: não precisamos adicionar todos os blocos novamente, podemos apenas duplicar o laço que acabamos de criar e alterar o necessário.*

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (luz >= 50 && luz < 100) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            `)
    }
    if (luz >= 100 && luz < 150) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            # # # # #
            `)
    }
})
```

## Step 12

Para a quarta faixa, podemos fazer o mesmo, mas alterando os intervalos para **maior ou igual que 150 E menor que 200**, acendendo também a quarta linha de LEDs.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (luz >= 50 && luz < 100) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            `)
    }
    if (luz >= 100 && luz < 150) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            # # # # #
            `)
    }
    if (luz >= 150 && luz < 200) {
        basic.showLeds(`
            . . . . .
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            `)
    }
})
```

## Step 13

Por fim, temos a quinta faixa que devemos garantir que a ``||variables:luz||`` seja apenas **maior ou igual a 200**.
Portanto, podemos duplicar o nosso primeiro laço, com apenas uma condição, e somente alterar os números para o novo intervalo, além de acionar todos os LEDs.

```blocks
let luz = 0
basic.forever(function () {
    luz = input.lightLevel()
    if (luz < 50) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            `)
    }
    if (luz >= 50 && luz < 100) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            `)
    }
    if (luz >= 100 && luz < 150) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # # #
            # # # # #
            # # # # #
            `)
    }
    if (luz >= 150 && luz < 200) {
        basic.showLeds(`
            . . . . .
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            `)
    }
    if (luz >= 200) {
        basic.showLeds(`
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            `)
    }
})
```
