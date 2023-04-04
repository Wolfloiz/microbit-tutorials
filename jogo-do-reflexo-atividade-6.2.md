


```template
let funcionando = false
basic.pause(2000)
led.plot(randint(0, 4), randint(0, 4))
funcionando = true
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

Vamos incluir agora um botão de iniciar e uma contagem regressiva pra começo do jogo.

## Step 2

Vamos começar adicionando o bloco ``||input:no botão B pressionado||``. Vamos então 
copiar tudo que se encontra no bloco ``||basic:no iniciar||`` para o bloco 
``||input:no botão B pressionado||``. Vamos então remover tudo que se encontra no bloco 
``||basic:no iniciar||``, exceto o bloco ``||variable:definir funcionando para||``.


```blocks
let funcionando = false
input.onButtonPressed(Button.B, function () {
		funcionando = false
		basic.pause(2000)
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
```

## Step 3

Para fazer uma contagem regressiva, vamos colocar 3 blocos ``||basic:mostrar número||`` 
dentro do bloco ``||input:no botão B pressionado||``, acima de todos os outros. Vamos 
então mostrar os números 3, 2 e 1, nessa ordem. Logo abaixo iremos colocar o bloco 
``||basic:limpar tela||``


```blocks
let funcionando = false
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(2000)
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
```

## Step 4

O jogo ainda está muito previsível, para testar ainda mais o reflexo e a atenção, vamos 
colocar o valor da pausa aleatório (para não sabermos exatamente quando o LED irá acender). 
Vamos então substituir o número 2000 pelo bloco ``||math:aleatório entre 1000 e 3000||``.


```blocks
let funcionando = false
input.onButtonPressed(Button.B, function () {
		basic.showNumber(3)
		basic.showNumber(2)
		basic.showNumber(1)
		basic.clearScreen()
		funcionando = false
		basic.pause(randint(1000, 3000))
		led.plot(randint(0, 4), randint(0, 4))
		funcionando = true
})
```

## Step 5

Agora podemos jogar o jogo. Ele está um pouco mais difícil e mais arrumado, e agora 
podemos recomeçar quantas vezes quisermos apertando o botão B. E então, consegue 
quantas vezes sem errar?








