


## Step 1

Vamos agora aprender a usar os ``||input:pins||`` do micro:bit. Eles funcionam 
de forma parecida com os botões. Pra usar um botão, basta apertar. Pra usar um 
 ``||input:pins||``, você deve conectar ele com o GND. Mas como faremos isso?

## Step 2

Primeiro, vamos adicionar o bloco  ``||input:no pin ... pressionado||``, que está 
na aba  ``||input:input||``. Vamos escolher o ``||input:pin 0 (P0)||``.

```blocks
input.onPinPressed(TouchPin.P0, function () {
	
})

```


## Step 3

Agora vamos fazer com que, toda vez que ``||input:P0||`` for pressionado, o 
micro:bit mostre um símbolo. Pra fazer isso vamos usar o bloco 
``||basic:mostrar ícone||``, e vamos escolher como símbolo um rosto feliz.

```blocks
input.onPinPressed(TouchPin.P0, function () {
    basic.showIcon(IconNames.Happy)
})
```

## Step 4
Nosso programa está pronto. Mas como fazemos para pressionar ``||input:P0||``? 
Para isso, vamos precisar de um fio de cobre. Vamos então carregar o código 
para o micro:bit, e encostar uma ponta do fio no ``||input:GND||``, e outra 
ponta no pino ``||input:P0||``. Assim que conectarmos ``||input:P0||`` e ``||input:GND||`` 
através do fio, o rosto feliz vai aparecer na tela!!