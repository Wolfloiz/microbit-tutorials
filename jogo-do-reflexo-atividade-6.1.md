


## Step 1

Vamos fazer um jogo para testar nosso reflexo. Esse jogo consiste em apertar um botão 
assim que um LED acender (qualquer LED).

## Step 2

Vamos começar criando uma variável chamada ``||variable:funcionando||``, na aba 
``||variable:Variáveis||``. Vamos então colocar o bloco
 ``||variable:definir funcionando para||`` dentro do bloco ``||basic:no iniciar||``, e definiremos a variável como 
``||logic:falso||`` (podemos pegar esse bloco na aba ``||logic:Lógica||``).

```blocks
let funcionando = false
```

## Step 3

Em seguida, dentro do bloco ``||basic:no iniciar||``, vamos colocar um bloco de 
``||basic:pausa||`` com 2000ms. Logo abaixo, vamos colocar o bloco ``||led:plotar x y||``, 
que se encontra na aba ``||led:led||``. Vamos colocar nos valores de x e y o bloco 
``||math:escolher aleatório entre 0 e 4||``. Vamos então definir a variável 
``||variable:funcionando||`` como 
``||logic:verdadeiro||`` (podemos pegar esse bloco na aba ``||logic:Lógica||``).


```blocks
let funcionando = false
basic.pause(2000)
led.plot(randint(0, 4), randint(0, 4))
funcionando = true
```

## Step 4

Agora vamos implementar a parte do jogo. Vamos inserir o bloco ``||input:no botão A pressionado||``. 
Dentro desse bloco, vamos colocar o laço ``||logic:se-então-senão||``. 


```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Step 4

Vamos então verificar se,
 quando apertamos o botão, o jogo estava em andamento ou não. Para isso, vamos substituir 
o bloco ``||logic:verdadeiro||`` pela variável ``||variable:funcionando||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (funcionando) {
    	
    } else {
    	
    }
})
```

## Step 5

Caso apertemos o botão e o jogo já esteja funcionando, vamos mostrar um rosto feliz, e caso 
contrário, um rosto triste, usando o bloco ``||basic:mostrar leds||`` e desenhando os rostos.
Antes do ``||logic:se-então-senão||``, vamos incluir um bloco ``||basic:limpar tela||``.

```blocks
input.onButtonPressed(Button.A, function () {
		basic.clearScreen()
    if (funcionando) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
    } else {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
            `)
    }
})
```

## Step 5

Agora já podemos jogar o jogo do reflexo. Ele ainda é bem simples, ainda falta colocar 
mais algumas coisas, mas já podemos brincar um pouco. E aí, quão bom é o seu reflexo?







