## Step 1

Neste tutorial, vamos aprender o que é um sprite. Ele é um objeto gráfico que não
deixa rastros quando se move na matriz de LEDs. Ou seja, é um elemento, como um LED aceso,
que, ao mudar de um LED para outro, o LED em que ele estava é apagado.

## Step 2

Então, vamos criar uma variável chamada `||variables:pacman||`, na aba
`||variables:Variáveis||`. Em seguida, adicionamos o bloco `||variables:definir pacman para||`
dentro do laço `||basic:no iniciar||`.

```blocks
let pacman = 0
```

## Step 3

Agora, vamos criar o `||game:sprite||`. Selecione o bloco `||game:criar sprite em x:  y:||`
localizado na aba `||game:Jogo||`, que fica dentro da seção **Avançado**, e o posicione dentro do comando `||variables:definir pacman para||`.

```blocks
let pacman = game.createSprite(2, 2)
```

## Step 4

Ainda devemos determinar em qual posição da matriz de LEDs o `||game:sprite||` vai aparecer inicialmente.
Vamos definir as coordenadas **x** e **y** iguais a **1** e **3**.

```blocks
let pacman = game.createSprite(1, 3)
```

## Step 5

O `||game:sprite||` já está criado, e podemos carregar código para o Micro:bit para vermos o LED aceso na posição 1 e 3.
Por enquanto, não há nenhuma vantagem em usar o `||game:sprite||` em relação a apenas acender um LED normalmente.
Entretanto, nos próximos tutoriais veremos porque é vantajoso usar os sprites na criação de jogos.
