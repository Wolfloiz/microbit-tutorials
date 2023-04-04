


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
})
```


## Step 1

Agora iremos permitir que o ``||game: sprite||`` se mova também na vertical. 
Para isso, vamos copiar os dois blocos ``||logic: se||``, e colocar os dois 
logo abaixo.

```blocks
let pacman = game.createSprite(2, 2)
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

Agora basta alterar, nos dois últimos ``||logic: se||``, todos os X, para Y.


```blocks
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
## Step 3

Pronto! Agora podemos carregar o programa para o micro:bit, e poderemos
 mover 
o ``||game: sprite||`` em qualquer direção 
só inclinando o micro:bit para um lado ou outro!