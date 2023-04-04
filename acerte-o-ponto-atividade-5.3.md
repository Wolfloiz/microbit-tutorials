

```template
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


## Step 1

Já temos o sprite se movendo na velocidade que escolhemos, agora vamos criar o jogo de 
acertar o ponto. O jogo consiste em apertar o botão A quando a mira estiver no centro da
 matriz de LEDs.


## Step 2

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

## Step 3

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

## Step 4

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

## Step 5

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

## Step 6

Pronto, agora podemos tentar acertar o ponto. Lembre-se que você pode tentar alterar a dificuldade,
alterando o valor do bloco ``||basic:Pausa||``. Se quiser algo ainda mais desafiador, pode 
fazer esse valor ser um número aleatório!!! E então, acha que consegue fazer quantos pontos?
