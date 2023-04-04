

```template
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    pacman.change(LedSpriteProperty.X, -1)	
})
input.onButtonPressed(Button.B, function () {
    pacman.change(LedSpriteProperty.X, 1)	
})
```


## Step 1

Vamos agora modificar o programa para usar o acelerômetro ao invés dos 
botões. Para isso, usaremos dois blocos ``||logic:se verdadeiro então||``, 
que se encontram na aba ``||logic:Lógica||`` e colocar no bloco 
``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
    if (true) {
    	
    }
})
```


## Step 2

O próximo passo é pegar os blocos de comparação 
``||logic:0 < 0||``, na aba ``||logic:Lógica||`` e colocar eles nos blocos 
``||logic:se verdadeiro então||``.

```blocks
basic.forever(function () {
    if (0<0) {
    	
    }
    if (0<0) {
    	
    }
})
```

## Step 3

Agora iremos pegar o bloco ``||input:aceleração (mg) x||`` na aba 
``||input:Input||`` e adicionar ele nos dois blocos de comparação, para 
ficarem no formato ``||logic:aceleração (mg) x < 0||``, e vamos trocar o sinal 
de um dos blocos de comparação para >.

```blocks
basic.forever(function () {
    if (input.acceleration(Dimension.X) < 0) {
    	
    }
    if (input.acceleration(Dimension.X) > 0) {
    	
    }
})
```


## Step 4

Por fim, vamos pegar tudo que está dentro do
 bloco ``||input:no botão A pressionado||`` e colocar dentro do primeiro 
 ``||logic: se||``, e tudo que está dentro do
 bloco ``||input:no botão B pressionado||`` e colocar dentro do segundo 
 ``||logic: se||``.

 ```blocks
basic.forever(function () {
    if (input.acceleration(Dimension.X) < 0) {
    pacman.change(LedSpriteProperty.X, -1)	    	
    }
    if (input.acceleration(Dimension.X) > 0) {
     pacman.change(LedSpriteProperty.X, 1)	   	
    }
})
```

## Step 5

Para auxiliar a visualização, vamos colocar um bloco ``||basic: pausa||`` 
de 100ms antes dos ``||logic: se||``, dentro do bloco ``||basic: sempre||``, 
fazendo com que o ``||game: sprite||`` se mova mais devagar. 


 ```blocks
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

## Step 6

Pronto! Agora podemos carregar o programa para o micro:bit, e poderemos mover 
o ``||game: sprite||`` só inclinando o micro:bit para um lado ou outro!