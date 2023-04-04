


```template
let pacman = game.createSprite(2, 2)
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)	    	
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)	   	
    }
    if (input.acceleration(Dimension.Y) < 0) {
    pacman.change(LedSpriteProperty.Y, -1)	    	
    }
    if (input.acceleration(Dimension.Y) > 0) {
     pacman.change(LedSpriteProperty.Y, 1)	   	
    }
})
```


## Step 1

Já temos o ``||variables: pacman||`` criado, e já podemos movê-lo. Vamos agora 
criar a moeda que o ``||variables: pacman||`` deve pegar de forma a fazer pontos. 
Para isso vamos criar uma variável chamada ``||variables: moeda||`` na aba 
``||variables: Variáveis||``, e vamos copiar o bloco ``||variables: definir pacman para||`` e 
colocar ele logo abaixo do original, trocando a variável ``||variables: pacman||`` pela 
variável ``||variables: moeda||``.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(2, 2)
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)	    	
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)	   	
    }
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)	    	
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)	   	
    }
})
```


## Step 2

Agora vamos na aba ``||Math: matemática||`` e pagar o bloco ``||Math: escolher aleatório entre||`` e 
mudar os valores para 0 e 4. Vamos então colocar dois desses blocos dentro de 
``||variables: definir moeda para||``, para fazer a moeda começar em um lugar 
aleatório.

```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(randint(0, 4), randint(0, 4))
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)	    	
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)	   	
    }
    if (input.acceleration(Dimension.Y) < 0) {
    pacman.change(LedSpriteProperty.Y, -1)	    	
    }
    if (input.acceleration(Dimension.Y) > 0) {
     pacman.change(LedSpriteProperty.Y, 1)	   	
    }
})
```
## Step 3

Como a parte de mover o ``||variables: pacman||`` já está feita, resta apenas 
fazer que, quando o ``||variables: pacman||`` tocar a ``||variables: moeda||``, 
a moeda desapareça e uma nova apareça em outro lugar. Para isso usaremos o bloco 
``||logic: se verdadeiro então||`` que se encontra na aba ``||logic: Lógica||``, e o 
bloco ``||game: is ... touching ...||`` na aba ``||game: Jogo||``.


```blocks
basic.forever(function () {
    let sprite: game.LedSprite = null
    if (sprite.isTouching()) {
    	
    }
})
```

## Step 4

Vamos então colocar as variáveis ``||variables: pacman||`` e ``||variables: moeda||`` 
no bloco ``||game: is ... touching ...||``, em qualquer ordem.


```blocks
basic.forever(function () {
    let pacman: game.LedSprite = null
    let moeda: game.LedSprite = null
    if (pacman.isTouching(moeda)) {
    	
    }
})
```

## Step 5

Vamos adicionar o bloco ``||game: delete sprite||`` dentro do bloco ``||logic: se||`` 
e adicionar a variável ``||variables: moeda||``, para deletarmos a moeda. 
Por fim, vamos copiar o bloco 
``||variables: definir moeda para||``, que se encontra no 
bloco ``||basic: no iniciar||`` e colocar dentro do ``||logic: se||``, 
para criarmos uma nova moeda em um lugar aleatório.


```blocks
let pacman = game.createSprite(2, 2)
let moeda = game.createSprite(randint(0, 4), randint(0, 4))
basic.forever(function () {
    basic.pause(100)
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)	    	
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)	   	
    }
    if (input.acceleration(Dimension.Y) < 0) {
    pacman.change(LedSpriteProperty.Y, -1)	    	
    }
    if (input.acceleration(Dimension.Y) > 0) {
     pacman.change(LedSpriteProperty.Y, 1)	   	
    }
})
basic.forever(function () {
    let sprite: game.LedSprite = null
    let pacman: game.LedSprite = null
    let moeda: game.LedSprite = null
    if (pacman.isTouching(moeda)) {
    	 sprite.delete()
         let moeda = game.createSprite(randint(0, 4), randint(0, 4))
    }
})
```

## Step 6

Pronto, já podemos carregar o código para o micro:bit. Se quiser experimentar, 
pode tentar variar o tempo da pausa, ou tentar adicionar uma pontuação ao jogo.