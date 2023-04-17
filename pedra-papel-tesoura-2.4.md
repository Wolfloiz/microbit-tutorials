

# 002.04- showLeds Random


## Step 1

Vamos criar um programa que mostra um símbolo aleatório toda vez que 
ligamos o micro:bit. Para isso, acesse a aba ``||variables:Variáveis||`` e crie uma variável chamada 
``||variables:aleatório||``. Em seguida, adicione o bloco ``||variables: definir aleatório para||`` dentro do laço ``||basic: no iniciar||``. 


```blocks
let aleatório = 0
```

## Step 2

Agora, alteramos o valor da variável ``||variables:aleatório||`` para que seja 
um valor aleatório entre 1 e 3, usando o bloco ``||math:escolher aleatório entre 0 até 10||`` localizado na aba  ``||math:Matemática||``.
Lembre-se de alterar os valores do intervalo de ``||math:0 até 10||`` para ``||math:1 até 3||``.

```blocks
let aleatório = randint(1, 3)
```


## Step 3
Acesse a aba ``||logic:Lógica||`` e adicione o primeiro laço ``||logic:Se-Então||``. Vamos usá-lo para verificar o valor da variável ``||variables:aleatório||`` e mostrar um 
símbolo para cada caso. 
Colocaremos esse bloco abaixo do bloco ``||variables: definir aleatório para||``. 

```blocks
let aleatório = randint(1, 3)
if (true) {
	
}
```

## Step 4
Como temos três valores possíveis (1, 2 ou 3), vamos clicar no símbolo **+** dentro do laço 
``||logic:Se-Então||`` duas vezes para adicionar espaços para testarmos todos as possibilidades.

```blocks
let aleatório = randint(1, 3)
if (true) {
	
} else if (false) {
	
} else {
	
}

```

## Step 5
Para verificar o valor de ``||variables:aleatório||``, vamos precisar de um bloco 
de comparação ``||logic:0  =  0||``, localizado na aba ``||logic:Lógica||``. Primeiramente, vamos testar se ``||variables:aleatório||`` 
é igual a **1**.

```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
	
} else if (false) {
	
} else {
	
}

```

## Step 6
Repetiremos o processo na segunda parte do laço ``||logic:Se-Então||``,
 onde temos ``||logic:Senão se-Então||``. Porém, agora testamos se ``||variables:aleatório||`` 
é igual a **2**.   

```blocks
let aleatório = randint(1, 3)
if (aleatório == 1) {
	
} else if (aleatório == 2) {
	
} else {
	
}

```

## Step 7
Por fim, devemos colocar três desenhos diferentes dentro do laço ``||logic:Senão se-Então||``,
 usando o bloco ``||basic:mostrar ícone||`` ou ``||basic:mostrar leds||``, ambos localizados na aba ``||basic:Básico||``. 
 Vamos exibir um rosto feliz quando ``||variables:aleatório||`` for igual a **1**, 
 um rosto triste quando ``||variables:aleatório||`` for igual a **2**, e um rosto surpreso quando ``||variables:aleatório||`` não for 1 ou 2.


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
Pronto! Agora, podemos carregar o código para o micro:bit. Experimente com
 outros desenhos ou com mais possibilidades de números aleatórios.