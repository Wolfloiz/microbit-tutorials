

```template
let pacman = game.createSprite(2, 2)
```


## Step 1

Agora que temos o ``||game:sprite||`` criado, vamos aprender a movê-lo horizontalmente. 
Vamos adicionar os blocos ``||input:no botão A pressionado||`` e 
 ``||input:no botão B pressionado||``, que se encontram na aba 
  ``||input:Input||``.


```blocks
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
```


## Step 2

Vamos agora adicionar o bloco ``||game:pacman alterar x por 1||``, que se 
encontra na aba ``||game:Jogo||`` dentro dos blocos ``||input:no botão A pressionado||`` e 
 ``||input:no botão B pressionado||``.


```blocks
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    pacman.change(LedSpriteProperty.X, 1)	
})
input.onButtonPressed(Button.B, function () {
    pacman.change(LedSpriteProperty.X, 1)	
})
```

## Step 3

Desse jeito, ao apertarmos o botão A ou B, ``||game:sprite||`` vai mover para 
a direita. Vamos então alterar o bloco ``||game:pacman alterar x por 1||``, 
dentro de ``||input:no botão A pressionado||`` para -1, fazendo o 
``||game:sprite||`` ir para a esquerda.

```blocks
let pacman = game.createSprite(2, 2)
input.onButtonPressed(Button.A, function () {
    pacman.change(LedSpriteProperty.X, -1)	
})
input.onButtonPressed(Button.B, function () {
    pacman.change(LedSpriteProperty.X, 1)	
})
```


## Step 4

Podemos ver agora a vantagem de se usar o ``||game:sprite||``. Se tivessemos 
usado LED normalmente, seria muito mais complicado movê-lo. Mas usando o ``||game:sprite||``
 podemos facilmente mover ele usando controles. Com o programa pronto, podemos 
 carregá-lo para o micro:bit e brincar de mover o ``||game:sprite||`` de 
 um lado pra outro.