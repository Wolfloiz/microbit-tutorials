

## Step 1
Vamos, antes de tudo, criar uma variável chamada
  ``||Variables:auxiliar||``. Em seguida colocaremos o bloco 
``||Variables:definir variável para||`` dentro do bloco ``||basic:no iniciar||``.

```blocks
let auxiliar = 0
```

## Step 2

Iremos então definir a variável ``||Variables:auxiliar||`` como um número aleatório 
entre 0 e 10 usando o bloco ``||Math:escolher aleatório||``.

```blocks
let auxiliar = randint(0, 10)
```

## Step 3

Agora aprenderemos a usar os botões. Podemos fazer com que o micro:bit faça coisas 
diferentes quando apertarmos o botão A, o botão B, ou os 2 botões ao mesmo tempo.
Na aba ``||input:Input||``, encontraremos o bloco ``||input:no botão A pressionado||``. 
Coloque 2 desses blocos, e mude um deles para que seja o botão B.

```blocks
input.onButtonPressed(Button.A, function () {
})
input.onButtonPressed(Button.B, function () {
})
```


## Step 4
Agora usaremos o bloco ``||Variables:alterar auxiliar por||``, que se encontra 
na aba ``||Variables:Variáveis||``. Utilizaremos dois desses blocos, um deve ser 
colocado dentro do bloco ``||input:no botão A pressionado||``, e outro dentro 
do bloco ``||input:no botão B pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    auxiliar += 1
})
input.onButtonPressed(Button.B function () {
    auxiliar += 1
})
```

## Step 5
No momento, o programa gera um número aleatório, e quando apertamos o botão A ou
 o botão B, esse número aumenta em 1. Vamos alterar um dos blocos 
 ``||Variables:alterar auxiliar por||`` para que um dos botões diminua o número em 1.
 É só trocar o valor 1 pelo valor -1. 

```blocks
input.onButtonPressed(Button.A, function () {
    auxiliar += -1
})
input.onButtonPressed(Button.B function () {
    auxiliar += 1
})
```

## Step 6
Para ver o número original, e os novos números quando algum botão for apertado,
 vamos colocar o bloco ``||Variables:auxiliar||`` dentro
  do bloco ``||basic:mostrar número||``, colocando ele 
  dentro do bloco ``||basic:sempre||``.

```blocks
basic.forever(function () {
    basic.showNumber(auxiliar)
})
```
