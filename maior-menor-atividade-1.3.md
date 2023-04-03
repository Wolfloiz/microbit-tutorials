# 001.03- randint

## Step 1
Vamos, antes de tudo, acessar a aba ``||Variables:variável||``,
 clicar em Fazer uma variável e definir o nome como
  ``||Variables:Número||``. Em seguida colocaremos o bloco 
``||Variables:definir variável para||`` dentro do bloco ``||basic:no iniciar||``.
Variáveis servem para armazenar valores, para usar em outros lugares sem precisar 
digitar o valor denovo e denovo.

```blocks
let Número = 0
```

## Step 2

Agora aprenderemos usar o bloco ``||Math:escolher aleatório||``, que se encontra
 na aba ``||Math:Matemática||``. Essa função gera
 um número inteiro aleatório entre os dois valores que você escolher. Iremos 
 colocar o bloco ``||Math:escolher aleatório||`` dentro do bloco 
 ``||Variables:definir variável para||``.

```blocks
let Número = randint(0, 10)
```

## Step 3
Para ver qual número aleatório foi gerado, vamos colocar o bloco ``||Variables:Número||`` dentro
  do bloco ``||basic:mostrar número||``, colocando este bloco abaixo do bloco 
  ``||Variables:definir variável para||``, dentro do bloco ``||basic:no iniciar||``.

```blocks
let Número = randint(0, 10)
basic.showNumber(Número)
```


## Step 4
Agora que conhecemos o bloco ``||Math:escolher aleatório||``, vamos tentar experimentar 
um pouco com os intervalos. Coloque os números que quiser nos intervalos do bloco e 
se divirta um pouco.

```blocks
let Número = randint(-3, 17)
basic.showNumber(Número)
```