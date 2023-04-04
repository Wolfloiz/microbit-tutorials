

## Step 1

Vamos começar aprendendo o que é um sprite. Ele é um objeto gráfico que não 
deixa rastros durante a locomoção na matriz de LEDs, ou seja, quando ele 
muda de um LED para outro, o LED que ele estava é apagado.

## Step 2

Vamos então criar uma variável chamada ``||variable:pacman||``, na aba 
``||variable:Variáveis||``. Vamos então adicionar o bloco
 ``||variable:definir pacman para||``.

```blocks
let pacman = 0
```

## Step 3

Em seguida, vamos criar o ``||game:sprite||``. Vamos pegar o bloco
 ``||game:criar sprite em x:  y:||`` na aba ``||game:Jogo||`` e colocá-lo 
 na aba ``||variable:definir pacman para||``.

```blocks
let pacman = game.createSprite(2, 2)
```


## Step 4

Falta agora apenas escolher a posição do ``||game:sprite||``. Vamos definir 
x e y iguais a 1 e 3. 

```blocks
let pacman = game.createSprite(1, 3)
```


## Step 5

O  ``||game:sprite||`` agora está criado, podemos carregar 
código e veremos um LED aceso. Por enquanto, não há nenhuma vantagem em usar 
o  ``||game:sprite||`` ao invés de um LED, mas veremos futuramente o porque 
é vantajoso usar os sprites.