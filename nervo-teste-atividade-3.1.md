

## Step 1

Vamos aprender a usar os ``||input:pins||`` do Micro:bit. Eles funcionam 
de forma similar aos botões. Pra usar um botão, só preicsamos pressioná-lo, certo? Porém, para usar um 
 ``||input:pin||``, você deve conectá-lo com o GND. Então, como faremos isso?

## Step 2

Primeiro, vamos adicionar o bloco ``||input:no pin ... pressionado||``, situado 
na aba ``||input:input||``. Vamos escolher o ``||input:pin 0 (P0)||``.

```blocks
input.onPinPressed(TouchPin.P0, function () {
	
})

```


## Step 3

Agora, vamos garantir que toda vez que ``||input:P0||`` for pressionado, o 
Micro:bit exibirá um símbolo. Pra isso, usamos o bloco 
``||basic:mostrar ícone||``, e escolhemos o ícone de um rosto feliz.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.Happy)
})
```

## Step 4
Nosso programa está pronto, mas como fazemos para pressionar ``||input:P0||``? 
Para isso, vamos precisar de um fio de cobre. Transfira o código 
para o Micro:bit, e encoste uma ponta do fio no ``||input:GND||`` da plaquinha, e a outra 
extremidade no pino ``||input:P0||``. Assim que conectarmos ``||input:P0||`` e ``||input:GND||`` 
através do fio, o rosto feliz deve aparecer na tela!!