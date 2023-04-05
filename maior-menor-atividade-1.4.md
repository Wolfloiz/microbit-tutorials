


## Step 1
Começaremos criando uma variável denominada
  ``||Variables:auxiliar||``. Em seguida, insira o bloco 
``||Variables:definir variável para||`` dentro do laço ``||basic:no iniciar||``.

```blocks
let auxiliar = 0
```

## Step 2

Agora, defina a variável ``||Variables:auxiliar||`` como um número aleatório 
entre 0 e 10 usando o bloco ``||Math:escolher aleatório||``.

```blocks
let auxiliar = randint(0, 10)
```

## Step 3

Feito isso, vamos descobrir como usar os botões do Micro:bit. Podemos programar instruções específicas para 
quando apertarmos o botão A, o botão B, ou os 2 ao mesmo tempo.
Na aba ``||input:Input||``, encontre o laço ``||input:no botão A pressionado||``. 
Adicione dois desses comandos em seu código e altere um deles para que seja ``||input:no botão B pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
})
input.onButtonPressed(Button.B, function () {
})
```


## Step 4
Agora, usaremos o bloco ``||Variables:alterar auxiliar por||``, que se encontra 
na aba ``||Variables:Variáveis||``. Utilizaremos dois desses blocos, um deve ser 
colocado dentro do laço ``||input:no botão A pressionado||``, e outro no laço ``||input:no botão B pressionado||``.

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
 ``||Variables:alterar auxiliar por||`` para que um dos botões diminua o número atual em 1.
 Para isso, basta trocar o valor de 1 para -1. 

```blocks
input.onButtonPressed(Button.A, function () {
    auxiliar += -1
})
input.onButtonPressed(Button.B function () {
    auxiliar += 1
})
```

## Step 6
Para ver o número original, e os novos números gerados quando algum botão for apertado,
 vamos colocar a ``||Variables:auxiliar||`` dentro
 de um bloco ``||basic:mostrar número||`` inserido
 no laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    basic.showNumber(auxiliar)
})
```