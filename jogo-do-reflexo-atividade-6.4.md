

```template
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



## Step 1

Vamos incluir agora uma função para não deixar que o botão seja apertado antes do LED aparecer, 
chamada de Começo Falso.

## Step 2

Vamos começar criando uma variáveis ``||variables:comeco_falso||``. 
Adicionaremos então o bloco ``||variable:definir comeco_falso para 0||`` no 
``||basic:no iniciar||`` e
colocar, no lugar do zero, a afirmação lógica ``||logic:falso||``.



```blocks
let funcionando = false
let inicio = 0
let fim = 0
let comeco_falso = false
```

## Step 3

Agora, dentro do bloco ``||input:no botão B pressionado||``, logo abaixo do bloco 
``||basic:limpar tela||``, vamos adicionar o bloco 
``||variable:definir comeco_falso para falso||`` (igual ao que colocamos no bloco 
``||basic:no iniciar||``).

```blocks
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		comeco_falso = false
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		inicio = input.runningTime()
		funcionando = true
})
```

## Step 4

Em seguida, ainda dentro do bloco ``||input:no botão B pressionado||``, abaixo da 
``||basic:pausa||``, vamos colocar um laço ``||logic:se-então||``. Como condição, 
vamos colocar ``||logic:comeco_falso = falso||``. Vamos então mover os blocos 
``||led:plotar x y||``, ``||variables:definir inicio||`` e 
``||variables:definir funcionando||`` para dentro do laço ``||logic:se-então||``.

```blocks
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		comeco_falso = false
		funcionando = false
		basic.pause(randint(1000, 3000))
		if (comeco_falso == false) {
				led.plot(randint(0, 4), randint(0, 4))
				inicio = input.runningTime()
				funcionando = true
    }
})
```

## Step 5

Por fim, vamos colocar um bloco ``||variable:definir comeco_falso para verdadeiro||``, 
dentro do laço ``||logic:se-então- senão||``, abaixo do rosto triste.


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
				comeco_falso = true
    }
})
```


## Step 6

Agora podemos jogar o jogo. E então, consegue 
quantas vezes sem errar?








