

```template
let funcionando = false
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen(
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
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



## Step 1

Vamos incluir agora uma contagem de tempo, para mostrar quão bom é nosso reflexo.

## Step 2

Vamos começar criando duas variáveis ``||variables:inicio||`` e ``||variables:fim||``. 
Adicionaremos então dois blocos ``||variable:definir inicio para 0||`` e
``||variable:definir fim para 0||`` dentro do bloco ``||basic:no iniciar||``.



```blocks
let funcionando = false
let inicio = 0
let fim = 0
```

## Step 3

Agora, dentro do bloco ``||input:no botão B pressionado||``, logo abaixo do bloco 
``||led:plotar x y||``, vamos adicionar o bloco ``||variable:definir início para 0||``. 
Vamos então definir ``||variables:inicio||`` como sendo igual ao tempo que o micro:bit está 
funcionando, usando o bloco ``||input:tempo de execução (ms)||``, que se encontra na aba 
``||input:Input-> mais||``.


```blocks
let funcionando = false
let inicio = 0
let fim = 0
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		inicio = input.runningTime()
		funcionando = true
})
```

## Step 4

Agora, dentro do bloco ``||input:no botão A pressionado||``, acima do rosto feliz, 
iremos repetir o procedimento, mas para a variável ``||variables:fim||``.


```blocks
input.onButtonPressed(Button.A, function () {
		basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
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

Por fim, vamos usar um bloco ``||basic:mostrar número||``, colocado abaixo do rosto 
feliz, para mostrar quão rápidos fomos. Vamos colocar nesse bloco a expressão matemática 
``||math:subtração||`` que pode ser achada na aba ``||math:Matemática||``, e realizar 
a operação ``||math:fim - inicio||`` (podemos obter as variáveis na aba 
``||variables:Variáveis||``). Entre o bloco ``||basic:mostrar número||`` e o rosto feliz, 
vamos também colocar uma pausa de 1 segundo (1000ms).


```blocks
input.onButtonPressed(Button.A, function () {
		basic.clearScreen()
    if (funcionando) {
				fim = input.runningTime()
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
				basic.pause(1000)
        basic.showNumber(fim-inicio)
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


## Step 6

Agora podemos jogar o jogo. Ele está um pouco mais difícil e mais arrumado, e agora 
podemos recomeçar quantas vezes quisermos apertando o botão B. E então, consegue 
quantas vezes sem errar?








