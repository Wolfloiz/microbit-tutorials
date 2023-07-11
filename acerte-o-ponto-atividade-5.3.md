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

Já temos o `||game:sprite||` se movendo na velocidade que escolhemos, agora vamos criar o jogo para
acertar o ponto. O jogo consiste em apertar o `||input:botão A||` quando a mira estiver no centro da
matriz de LEDs.

## Step 2

Incialmente, inclua o laço `||input:no botão A pressionado||`, que se encontra na aba
`||input:Input||`. Dentro desse laço, adicionaremos o `||logic:se-então-senão||`,
que pode ser encontrado na aba `||logic:Lógica||`.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {

    } else {

    }
})
```

## Step 3

Agora, temos que criar as condições de acerto e erro quando o botão é pressionado. Para isso,
vamos substituir o bloco triangular `||logic:verdadeiro||` pelo comparador `||logic:0 = 0||`,
que também está na aba `||logic:Lógica||`.

```blocks
input.onButtonPressed(Button.A, function () {
    if (0 == 0) {

    } else {

    }
})
```

## Step 4

Vamos comparar se a posição atual da mira (quando o botão for apertado) é igual a 2, ou seja,
o ponto central da matriz de LEDs. Para isso, dentro do bloco comparador `||logic:0 = 0||`, vamos substituir
um dos zeros pelo bloco `||game:sprite x||`, localizado na aba `||game:Jogo||`, e o outro pelo número **2**.
Altere a variável do bloco `||variables:sprite x||` para `||variables:mira x||`.

```blocks
let mira = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
		if (mira.get(LedSpriteProperty.X) == 2) {

    } else {

    }
})
```

## Step 5

Por fim, temos que definir o que acontecerá quando o jogador acertar e quando ele errar.
Ao acertar, vamos aumentar sua pontuação e, quando errar, vamos terminar o jogo.
Para isso, vamos usar os blocos `||game:alterar pontuação em 1||` e `||game:fim do jogo||`
que se encontram na aba `||game:Jogo||`. A alteração da `||game:pontuação||` deve ficar dentro do `||logic:então||`,
enquanto o `||game:fim do jogo||` no `||logic:senão||`.

```blocks
let mira = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
		if (mira.get(LedSpriteProperty.X) == 2) {
			game.addScore(1)
    } else {
    	game.gameOver()
    }
})
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
		basic.pause(100)
		if (mira.isTouchingEdge()) {
				mira.change(LedSpriteProperty.X, -4)
				basic.pause(100)
    }
})
```

## Step 6

Pronto, agora podemos tentar acertar o ponto. Lembre-se que você pode alterar a dificuldade,
alterando o valor do bloco `||basic:Pausa||`. Se quiser algo ainda mais desafiador, pode
fazer esse valor ser um número aleatório! E então, quantos pontos você consegue fazer?
