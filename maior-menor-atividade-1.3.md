


## Step 1
Vamos, antes de tudo, acessar a aba ``||Variables:variável||``,
 clicar em Fazer uma variável e nomeá-la como
  ``||Variables:Número||``. Em seguida, inserimos o bloco 
``||Variables:definir variável para||`` dentro do laço ``||basic:no iniciar||``.
Uma variável serve para armazenarmos informações que serão usadas em outros lugares sem que
precisemos digitar seu valor repetidamente.

```blocks
let Número = 0
```

## Step 2

Agora aprenderemos a usar o bloco ``||Math:escolher aleatório||``, que se encontra
 na aba ``||Math:Matemática||``. Essa função gera
 um número inteiro aleatório entre os dois valores que você escolher. Devemos inserir 
este comando ``||Math:escolher aleatório||`` dentro do bloco 
 ``||Variables:definir variável para||``.

```blocks
let Número = randint(0, 10)
```

## Step 3
Logo abaixo do bloco ``||Variables:definir variável para||``, vamos adicionar a variável ``||Variables:Número||`` dentro
  do campo do bloco ``||basic:mostrar número||`` para visualizarmos qual número aleatório foi gerado.

```blocks
let Número = randint(0, 10)
basic.showNumber(Número)
```


## Step 4
Agora que conhecemos o comando ``||Math:escolher aleatório||``, vamos experimentar 
com outros intervalos alterando os números dentro do bloco.

```blocks
let Número = randint(-3, 17)
basic.showNumber(Número)
```