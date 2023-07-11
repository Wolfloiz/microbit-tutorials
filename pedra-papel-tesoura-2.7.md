## Step 1

Vamos começar adicionando um laço `||input:agitar||`.

```blocks
input.onGesture(Gesture.Shake, function ())
```

## Step 2

Vá até a aba `||variables:Variáveis||` e crie uma `||variables:variável||` denominada `||variables:ppt||` para armazenar o valor de pedra, papel ou tesoura.
Em seguida, adicione o bloco `||variables:definir ppt para 0||` dentro do laço `||input:agitar||`.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
    ppt = 0
})
```

## Step 3

Em seguida, devemos atribuir a essa variável um `||Math: valor aleatório ||` entre **0** e **2**.
Esse comando pode ser encontrado dentro da aba `||Math:Matemática||`.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
    ppt = randint(0, 2)
})
```

## Step 4

Vá até a aba `||Logic:Lógica ||` e selecione o primeiro laço, `||Logic:se ‘verdadeiro’ então ||`.
Devemos posicioná-lo dentro do laço `||input:agitar||`,
pois desejamos que essa parte do código só seja executada quando agitarmos o Micro:bit.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
   ppt = randint(0, 2)
   if (true) {

   }
})
```

## Step 5

Agora, devemos comparar se o número gerado é igual a **0**, **1** ou **2**.
Para isso, retorne à aba `||Logic:Lógica ||`, selecione o bloquinho com as pontas triangulares de comparação
e o posicione dentro do campo `||Logic:verdadeiro||` do laço `||Logic:se-então||`.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
   ppt = randint(0, 2)
   if (0 == 0) {

   }
})
```

## Step 6

Vamos testar se nossa variável `||variables:ppt||` é igual a **zero**.
Para isso, preenchemos os dois campos redondos da comparação com esses dados.
Vá até a aba `||variables:Variáveis||` e selecione o bloquinho redondo `||variables:ppt||`.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
   ppt = randint(0, 2)
   if (ppt == 0) {

   }
})
```

## Step 7

Vamos exibir uma pedra na matriz de LEDs. Para isso, selecione o bloco `||Basic:mostrar leds||`, na aba `||Basic:Básico||`,
e o posicione dentro do laço `||Logic:se-então||`. Depois, basta colorir quais LEDs ficarão acesos em nosso símbolo de pedra.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
    ppt = randint(0, 2)
    if (ppt == 0) {
        basic.showLeds(`
            . # # # .
            # # # # #
            # # # # #
            # # # # #
            . # # # .
            `)
    }
})
```

## Step 8

Vamos replicar esse processo para o papel. Para facilitar, podemos clicar com o botão direito do mouse no laço `||Logic:se-então||`
inteiro para duplicá-lo e alterar o número de **0** para **1**.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
    ppt = randint(0, 2)
    if (ppt == 0) {
        basic.showLeds(`
            . # # # .
            # # # # #
            # # # # #
            # # # # #
            . # # # .
            `)
    }
    if (ppt == 1) {

    }
})
```

## Step 9

Agora vamos desenhar o símbolo do papel nos LEDs usando o bloco `||Basic:mostrar leds||`.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
    ppt = randint(0, 2)
    if (ppt == 0) {
        basic.showLeds(`
            . # # # .
            # # # # #
            # # # # #
            # # # # #
            . # # # .
            `)
    }
    if (ppt == 1) {
        basic.showLeds(`
            # # # . .
            # . # # .
            # . . # .
            # . . # .
            # # # # .
            `)
    }
})
```

## Step 10

Por fim, criamos o caso da tesoura, alterando a comparação para `||variables:ppt||` igual a **2**
e ajustando quais LEDs ficam acesso para formar o símbolo de uma tesoura.

```blocks
let ppt = 0
input.onGesture(Gesture.Shake, function () {
    ppt = randint(0, 2)
    if (ppt == 0) {
        basic.showLeds(`
            . # # # .
            # # # # #
            # # # # #
            # # # # #
            . # # # .
            `)
    }
    if (ppt == 1) {
        basic.showLeds(`
            # # # . .
            # . # # .
            # . . # .
            # . . # .
            # # # # .
            `)
    }
    if (ppt == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            # # # # #
            # # # . .
            . # # . .
            `)
    }
})
```
