

```template
let mira = game.createSprite(2, 2)
```


## Step 1

Agora que temos o ``||game:sprite||`` criado, vamos aprender a movê-lo horizontalmente. 
Vamos adicionar o bloco ``||basic:sempre||`` que se encontra na aba 
  ``||basic:Básico||``.


```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
	
})
```


## Step 2

Vamos agora adicionar o bloco ``||game:mira alterar x por 1||``, que se 
encontra na aba ``||game:Jogo||`` dentro do bloco ``||basic:sempre||``.


```blocks
let mira = game.createSprite(2, 2)
basic.forever(function () {
    mira.change(LedSpriteProperty.X, 1)	
})
```

## Step 3

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

## Step 4

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


## Step 5

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


## Step 4

Podemos ver agora a vantagem de se usar o ``||game:sprite||``. Se tivessemos 
usado LED normalmente, seria muito mais complicado movê-lo. Mas usando o ``||game:sprite||``
 não precisamos deletar o LED anterior e acender o próximo, isso é feito de forma 
automática. Com o programa pronto, podemos 
 carregá-lo para o micro:bit e ver o LED se movendo horizontalmente.