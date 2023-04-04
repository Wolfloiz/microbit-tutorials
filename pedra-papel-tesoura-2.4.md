

## Step 1

Vamos criar um programa que mostra um símbolo aleatório toda vez que 
ligamos o micro:bit. Vamos começar criando uma variável chamada 
``||variables:aleatório||`` e adicionar o bloco ``||variables: definir aleatório para||``. 


```blocks
let aleatório = 0
```

## Step 2

Agora iremos alterar o valor da variável ``||variables:aleatório||`` para que seja 
um valor aleatório entre 1 e 3, usando o bloco ``||math:aleatório entre||``. 

```blocks
let aleatório = randint(1, 3)
```


## Step 3
Para verificar o valor da variável ``||variables:aleatório||`` e mostrar um 
símbolo para cada caso, iremos usar o bloco  ``||logic:se ... então||``. 
Colocaremos esse bloco abaixo do bloco ``||variables: definir aleatório para||``. 

```blocks
let aleatório = randint(1, 3)
if (true) {
	
}
```

## Step 4
Como temos três possíveis valores, vamos clicar no símbolo + dentro do bloco 
``||logic:se ... então||`` duas vezes.

```blocks
let aleatório = randint(1, 3)
if (true) {
	
} else if (false) {
	
} else {
	
}

```

## Step 5
Para verificar o valor de ``||variables:aleatório||``, vamos usar um bloco 
de comparação ``||logic:0  =  0||``, e vamos verificar se ``||variables:aleatório||`` 
é igual a 1.

```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
	
} else if (false) {
	
} else {
	
}

```

## Step 6
Repetiremos o processo para a segunda parte do bloco ``||logic:se ... então||``,
 na parte ``||logic:se não ... então||``, vamos verificar se ``||variables:aleatório||`` 
é igual a 2.   

```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
	
} else if (aleatório == 2) {
	
} else {
	
}

```

## Step 7
Agora, devemos colocar três desenhos diferentes dentro do bloco ``||logic:se ... então||``,
 podemos fazer isso usando o bloco  ``||basic:mostrar ícone||`` ou o bloco 
  ``||basic:mostrar leds||``. Vamos mostrar um rosto feliz quando ``||variables:aleatório||`` for igual a 1, 
   um rosto triste quando ``||variables:aleatório||`` for igual a 2, e um rosto surpreso quando ``||variables:aleatório||`` não for 1 nem 2.


```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
	basic.showIcon(IconNames.Happy)
} else if (aleatório == 2) {
	basic.showIcon(IconNames.Sad)
} else {
	basic.showIcon(IconNames.Surprised)
}

```

## Step 7
Pronto! Podemos agora carregar o código para o micro:bit. Experimente com
 outros desenhos. Experimente também com um número maior de desenhos!
