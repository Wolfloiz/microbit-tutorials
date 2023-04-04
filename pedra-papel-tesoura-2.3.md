


## Step 1

Podemos usar símbolos prontos com o bloco ``||basic:mostrar ícone||``, mas 
podemos também criar novos símbolos usando o bloco 
``||basic:mostrar leds||``. Adicione o bloco ``||basic:mostrar leds||`` 
dentro do bloco ``||basic:ao iniciar||``

```blocks
basic.showLeds(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `)
```

## Step 2

O bloco mostra um quadrado, com vários quadradinhos. Podemos usar esses 
quadradinhos para desenhar alguma coisa. Vamos tentar desenhar alguma coisa?
 Que tal um X? 

```blocks
    basic.showLeds(`
        # . . . #
        . # . # .
        . . # . .
        . # . # .
        # . . . #
        `)
```


## Step 3

Pronto! Podemos agora carregar o código para o micro:bit. Experimente com 
o bloco  ``||basic:mostrar leds||`` e tente fazer outros desenhos!
