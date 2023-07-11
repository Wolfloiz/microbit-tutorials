```template
let mira = game.createSprite(2, 2)
```

## Step 1

Agora que temos o `||game:sprite||` criado, vamos aprender a movê-lo horizontalmente.
Vamos adicionar o laço `||basic:sempre||` que se encontra na aba `||basic:Básico||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {

})
```

## Step 2

Em seguida, selecione o bloco `||game:mira alterar x por 1||`, que se
encontra na aba `||game:Jogo||` na seção **Avançado**, e o posicione dentro do laço `||basic:sempre||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
})
```

## Step 3

Agora, devemos fazer com que a mira pule de uma extremidade da tela pra outra ao
chegar na borda. Para isso, vamos adicionar, ainda dentro do laço `||basic:sempre||`,
o laço `||logic:se-então||`. Substitua a condição **verdadeiro** pela condição
`||game:is mira touching edge||`, que se encontra na aba `||game:Jogo||`.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
		if (mira.isTouchingEdge()) {

    }
})
```

## Step 4

Dentro do laço `||logic:se-então||`, vamos deslocar a mira pra outra extremidade
usando o bloco `||game:mira alterar x por 1||`. Entretanto, altere o valor de **1** para **-4**.

```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)
		if (mira.isTouchingEdge()) {
				mira.change(LedSpriteProperty.X, -4)
    }
})
```

## Step 5

Em seguida, selecione dois blocos de `||basic:pausa||`, que se encontram na aba
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

## Step 6

Agora, podemos ver a vantagem de se usar o `||game:sprite||`. Se tivéssemos
acionados os LEDs normalmente, seria muito mais complicado movê-los. Mas, usando o `||game:sprite||`,
não precisamos deletar o LED anterior e acender o próximo, isso é feito de forma
automática. Com o código finalizado, podemos carregá-lo para o Micro:bit e observar o LED se movendo horizontalmente.
