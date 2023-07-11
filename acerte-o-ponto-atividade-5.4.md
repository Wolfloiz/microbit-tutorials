## Step 1

Vamos criar um jogo em que um `||game:sprite||` se movimenta ao longo dos LEDs do Micro:bit na direção horizontal.
O jogo consiste em pressionar o `||input:botão A||` quando a mira estiver no centro da matriz de LEDs, para testar nosso tempo de reação, atenção e
previsibilidade através de estímulos visuais.

## Step 2

Primeiramente, vamos aprender o que é um sprite. Ele é um objeto gráfico que não
deixa rastros quando se move na matriz de LEDs. Ou seja, é um elemento, como um LED aceso,
que, ao mudar de um LED para outro, o LED em que ele estava é apagado.

## Step 3

Então, devemos criar uma variável chamada `||variables:mira||` na aba `||variables:Variáveis||`.
Feito isso, adicione o bloco `||variables:definir mira para||` dentro do laço `||basic:no iniciar||`.

```blocks
let mira = 0
```

## Step 4

Em seguida, vamos criar o `||game:sprite||`. Selecione o bloco redondo `||game:criar sprite em x:  y:||`
na aba `||game:Jogo||` situada dentro de **Avançado**. Posicione este bloco no campo redondo do bloco `||variables:definir mira para||`.

```blocks
let mira = game.createSprite(2, 2)
```

## Step 5

Agora que temos o `||game:sprite||` criado, vamos inserir os comandos para movê-lo horizontalmente.
Acesse a aba `||basic:Básico||` e selecione o laço `||basic:sempre||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {

})
```

## Step 6

Dentro deste laço, insira o bloco `||game:sprite alterar x por 1||`, que se
encontra na aba `||game:Jogo||`. Altere a variável do comando de `||variables:sprite||` para `||variables:mira||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
})
```

## Step 7

Agora, devemos fazer a mira pular de uma extremidade da tela pra outra, ao alcançar a borda da matriz de LEDs.
Para isso, vamos adicionar um laço `||logic:se-então||`, ainda dentro do laço `||basic:sempre||`.
Substitua a condição **verdadeiro** pelo bloco triangular `||game:is sprite touching edge||`, que se encontra na aba `||game:Jogo||`.
Lembre-se de alterar a variável de `||variables:sprite||` para `||variables:mira||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
		if (mira.isTouchingEdge()) {

    }
})
```

## Step 8

Dentro do laço `||logic:se-então||`, vamos deslocar a mira pra outra extremidade
usando o bloco `||game:sprite alterar x por 1||` situado na aba `||game:Jogo||`. Altere o valor de **1** para **-4**, e a variável de `||variables:sprite||` para `||variables:mira||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
		if (mira.isTouchingEdge()) {
				mira.change(LedSpriteProperty.X, -4)
    }
})
```

## Step 9

Feito isso, selecione dois blocos de `||basic:pausa||`, que se encontram na aba
`||basic:Básico||`, para regular a velocidade da mira. Eles devem ser posicionados
dentro dos laços `||basic:sempre||` e `||logic:se-então||`, exatamente depois dos blocos de alteração da posição **x**.
Sugerimos o valor **100 ms**, mas se quiser aumentar a dificuldade, escolha um valor menor. Para diminuir a dificuldade,
escolha um valor maior. Lembre-se que os dois blocos devem ter o mesmo valor.

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

## Step 10

Inclua o laço `||input:no botão A pressionado||`, que se encontra na aba
`||input:Input||`. Dentro desse laço, adicionaremos o `||logic:se-então-senão||`,
que pode ser encontrado na aba `||logic:Lógica||`.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {

    } else {

    }
})
```

## Step 11

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

## Step 12

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

## Step 13

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

## Step 14

Pronto, agora podemos tentar acertar o ponto. Lembre-se que você pode alterar a dificuldade,
alterando o valor do bloco `||basic:Pausa||`. Se quiser algo ainda mais desafiador, pode
fazer esse valor ser um número aleatório! E então, quantos pontos você consegue fazer?
