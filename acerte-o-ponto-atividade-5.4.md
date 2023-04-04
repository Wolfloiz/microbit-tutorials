

## Step 0
Vamos criar juntos um jogo de acertar o ponto. O jogo consiste em apertar o botão A quando
 a mira estiver no centro da matriz de LEDs, para testar nosso tempo de reação, atenção e
previsibilidade através de estímulos visuais!!


## Step 1

Vamos começar aprendendo o que é um sprite. Ele é um objeto gráfico que não 
deixa rastros durante a locomoção na matriz de LEDs, ou seja, quando ele 
muda de um LED para outro, o LED que ele estava é apagado.

## Step 2

Vamos então criar uma variável chamada ``||variable:mira||``, na aba 
``||variable:Variáveis||``. Vamos então adicionar o bloco
 ``||variable:definir mira para||``.

```blocks
let mira = 0
```

## Step 3

Em seguida, vamos criar o ``||game:sprite||``. Vamos pegar o bloco
 ``||game:criar sprite em x:  y:||`` na aba ``||game:Jogo||`` e colocá-lo 
 na aba ``||variable:definir mira para||``.

```blocks
let mira = game.createSprite(2, 2)
```

## Step 4

Agora que temos o ``||game:sprite||`` criado, vamos aprender a movê-lo horizontalmente. 
Vamos adicionar o bloco ``||basic:sempre||`` que se encontra na aba 
  ``||basic:Básico||``.


```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
	
})
```


## Step 5

Vamos agora adicionar o bloco ``||game:mira alterar x por 1||``, que se 
encontra na aba ``||game:Jogo||`` dentro do bloco ``||basic:sempre||``.


```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)	
})
```

## Step 6

Devemos agora fazer com que a mira pule de uma extremidade da tela pra outra, quando 
chegar na extremidade. Para isso, vamos adicionar, ainda dentro do bloco ``||basic:sempre||``, 
o laço ``||logic:se-então||``. Vamos então substituir a condição verdadeiro pela condição 
``||game:is mira touching edge||``, que se encontra na aba ``||game:Jogo||``.


```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)	
		if (mira.isTouchingEdge()) {

    }
})
```

## Step 7

Dentro do laço ``||logic:se-então||``, vamos então deslocar a mira pra outra extremidade, 
usando o bloco ``||game:mira alterar x por 1||``, mas iremos alterar o valor por -4. 


```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)	
		if (mira.isTouchingEdge()) {
				mira.change(LedSpriteProperty.X, -4)
    }
})
```


## Step 8

Vamos agora colocar o bloco ``||basic:pausa||`` que se encontra na aba 
  ``||basic:Básico||``, para regular a velocidade da mira. Vamos colocar esse bloco 
dentro do bloco ``||basic:sempre||`` e dentro do laço ``||logic:se-então||``. 
Sugerimos o valor 100, mas se quiser aumentar a 
dificuldade, pode escolher um valor menor. Ou se quiser diminuir a dificuldade, 
pode escolher 
um valor maior. Lembre-se que os dois blocos devem ter o mesmo valor.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)	
		basic.pause(100)
		if (mira.isTouchingEdge()) {
				mira.change(LedSpriteProperty.X, -4)
				basic.pause(100)
    }
})
```

## Step 9

Vamos então adicionar o bloco ``||input:no botão A pressionado||``, que se encontra na aba 
``||input:Input||``. Dentro desse bloco, adicionaremos o laço ``||logic:se-então-senão||``, 
que pode ser achado na aba ``||logic:Lógica||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Step 10

Agora temos que criar as condições de acerto e erro quando o botão é apertado. Para isso, 
vamos substituir o bloco ``||logic:verdadeiro||`` pelo bloco comparador ``||logic:0 = 0||``, 
que pode ser achado na aba ``||logic:Lógica||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Step 11

Vamos agora comparar se a posição atual da mira (quando o botão for apertado) é igual a 2, 
o ponto central. Para isso, dentro do bloco comparador ``||logic:0 = 0||``, vamos substituir 
um dos zeros pelo bloco ``||game:Mira x||`` (que se encontra na aba ``||game:Jogo||``), e o outro pelo número 2.

```blocks
input.onButtonPressed(Button.A, function () {
		if (mira.get(LedSpriteProperty.X) == 2) {
    	
    } else {
    	
    }
})
```

## Step 12

Por fim, temos que definir o que acontecerá quando o jogador acertar e errar. Quando o 
jogador acertar, iremos aumentar sua pontuação, e quando ele errar vamos terminar o jogo. 
Para isso vamos usar os blocos ``||game:alterar pontuação em 1||`` e ``||game:fim do jogo||`` 
que se encontram na aba ``||game:Jogo||``.

```blocks
input.onButtonPressed(Button.A, function () {
		if (mira.get(LedSpriteProperty.X) == 2) {
			game.addScore(1)
    } else {
    	game.gameOver()
    }
})
```

## Step 13

Pronto, agora podemos tentar acertar o ponto. Lembre-se que você pode tentar alterar a dificuldade,
alterando o valor do bloco ``||basic:Pausa||``. Se quiser algo ainda mais desafiador, pode 
fazer esse valor ser um número aleatório!!! E então, acha que consegue fazer quantos pontos?
