# Maior ou Menor

## Step 1

Precisamos indicar ao jogador que o jogo começou! Para isso, vamos adicionar o bloco ``||basic:mostrar string||`` que exibirá uma palavra na matriz de LEDs.
``||basic:No iniciar||``, mostraremos a mensagem **"VAI!"**, que deve ser digitada dentro do bloco ``||basic:mostrar string||``.

```blocks
basic.showString("VAI!")
```

## Step 2

Vamos criar três ``||variables:variáveis||``: **Número**, **Próximo Número** e **Pontuação**.

## Step 3

Adicione três blocos de ``||variables:definição||`` das variáveis. ``||basic:Ao iniciar||``,  ``||variables:Pontuação||`` deve ser igual a zero, 
enquanto ``||variables:Número||`` e ``||variables:Próximo Número||`` devem ser iguais a ``||Math:Números aleatórios entre 0 e 100||``.

```blocks
basic.showString("VAI!")
let Pontuação = 0
let Número = randint(0, 100)
Próximo_Número = randint(0, 100)
```
## Step 4

Precisamos mostrar ao usuário qual o primeiro número do jogo. Para isso, selecionamos o bloco  ``||basic:mostrar número||``. 
Em seguida, vamos até a seção de ``||variables:Variáveis||`` e selecionamos ``||variables:Número||``.

```blocks
basic.showString("VAI!")
let Pontuação = 0
let Número = randint(0, 100)
let Próximo_Número = randint(0, 100)
basic.showNumber(Número)
```

## Step 5

O jogador pode pressionar o **botão A**, o **botão B**, ou reiniciar com os dois acionados ao mesmo tempo.
Começando pelo ``||input:botão A||``, vamos até a aba ``||input:Input||`` e selecionamos o laço ``||Input:no botão A pressionado||``. 

```blocks
input.onButtonPressed(Button.A, function () {
	
})
basic.showString("VAI!")
let Pontuação = 0
let Número = randint(0, 100)
let Próximo_Número = randint(0, 100)
basic.showNumber(Número)
```

## Step 6

 Quando o usuário aperta o ``||input:botão A||``, significa que ele acredita que o  ``||variables:Próximo Número||`` será menor que ``||variables:Número||``.
 Portanto,  ``||logic:SE||`` isso for realmente verdade, ``||logic:ENTÃO||`` ele terá acertado. ``||logic:SENÃO||``, significa que ele errou sua previsão.

 Por isso, usaremos o laço ``||logic:se-então-senão||`` localizado dentro da aba ``||logic:Lógica||``.
 
 ```blocks
 input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    } else {
    	
    }
})
basic.showString("VAI!")
let Pontuação = 0
let Número = randint(0, 100)
let Próximo_Número = randint(0, 100)
basic.showNumber(Número)
```

## Step 7

Agora, precisamos testar se ``||variables:Próximo Número||`` realmente é menor que ``||variables:Número||``. Para isso, adicionamos o ``||logic:comparador||`` dentro da aba ``||logic:Lógica||`` e alteramos seus campos para as respectivas variáveis. 
Fique atento ao sinal!

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
    	
    } else {
    	
    }
})
let Próximo_Número = 0
let Número = 0
basic.showString("VAI!")
let Pontuação = 0
Número = randint(0, 100)
Próximo_Número = randint(0, 100)
basic.showNumber(Número)
```

## Step 8

Dentro da primeira parte do laço ``||logic:se-então-senão||``, ou seja, quando a condição é atendida,
vamos ``||basic:mostrar o ícone||`` de um rosto feliz na tela do Micro:bit e adicionar uma ``||basic:pausa||`` de meio segundo (**500ms**).

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
    } else {
    	
    }
})

```

## Step 9

Também devemos aumentar sua pontuação em um ponto, para isso vamos usar o ``||variables: alterar Pontuação por 1||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
    } else {
    	
    }
})

```

## Step 10

Ainda dentro do ``||logic: então||``, vamos adicionar dois blocos de ``||variables: definição||`` de variáveis, com os seguintes dados:

- Definir ``||variables:Número||`` para ``||variables:Próximo Número||``;
- Definir ``||variables:Próximo Número||`` para ``||math:escolher aleatório 0 até 100||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
    } else {
    	
    }
})
```

## Step 11

Finalizando essa estrutura, devemos mostrar ao jogador o número adivinhado corretamente para que ele possa estimar o próximo.
Para isso, vamos até a aba ``||basic:Básico||`` e selecionamos o bloco ``||basic:mostrar número||`` para exibir nossa variável ``||variables:Número||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
    	
    }
})
```

## Step 12

Vamos aproveitar essa parte do código para já criarmos a situação quando o jogador acerta pressionando o ``||Input:botão B||``.
Isso significa que o ``||variables:Próximo Número||`` realmente é maior que o atual.

Duplique este laço e altere para ``||Input:no botão B pressionado||``. Substitua a condição dentro do laço ``||logic:SE||`` para ``||variables:Próximo Número||`` **maior que** ``||variables:Número||``.

```blocks
input.onButtonPressed(Button.B, function () {
    if (Próximo_Número > Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
    	
    }
})
```

## Step 13

A partir daqui, passamos a programar os casos quando o usuário **erra** sua previsão. Portanto, esses blocos devem ficar dentro do ``||logic:senão||`` de cada um de nossos laços ``||logic:se-então-senão||``.
Começamos exibindo o ``||basic:ícone||`` de um rosto triste na tela do Micro:bit seguido de uma ``||basic:pausa||`` de **500ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
    }
})
```

## Step 14

Vamos exibir o número que erramos na previsão. Para isso, usamos o bloco ``||basic:mostrar número||`` para exibir o valor da variável ``||variables:Próximo Número||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
    }
})
```

## Step 15

Por fim, devemos informar ao jogador qual foi sua ``||variables:Pontuação||`` atingida, ou seja, quantas vezes ele acertou as previsões. 
Faremos isso com o bloco ``||basic:mostrar string||`` com as letras '**PTS**', seguido do comando para ``||basic:mostrar número||`` ``||variables:Pontuação||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (Próximo_Número < Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
        basic.showString("PTS")
        basic.showNumber(Pontuação)
    }
})
```

## Step 16

Como as ações que devem ser tomadas ao errar são as mesmas para o ``||Input:botão A||`` e para o ``||Input:botão B||``,
podemos apenas duplicar os blocos dentro do laço ``||Logic:senão||`` do ``||Input:botão A||`` e movê-los para o do ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.B, function () {
    if (Próximo_Número > Número) {
        basic.showIcon(IconNames.Happy)
        basic.pause(500)
        Pontuação += 1
        Número = Próximo_Número
        Próximo_Número = randint(0, 100)
        basic.showNumber(Número)
    } else {
        basic.showIcon(IconNames.Sad)
        basic.pause(500)
        basic.showNumber(Próximo_Número)
        basic.showString("PTS")
        basic.showNumber(Pontuação)
    }
})
```

## Step 17

Para finalizarmos nosso programa, devemos apenas considerar o caso em que o usuário deseja reiniciar o jogo. 
Os passos que devem ser executados são exatamente iguais àqueles que definimos no nosso laço ``||Basic:no iniciar||``. Então, podemos duplicá-los e inseri-los dentro de um laço ``||Input: no botão A+B pressionado||``.

```blocks
input.onButtonPressed(Button.AB, function () {
    basic.showString("VAI!")
    Pontuação = 0
    Número = randint(0, 100)
    Próximo_Número = randint(0, 100)
    basic.showNumber(Número)
})
```