# Caça ao tesouro - Micro:bit Guia

## Step 1


Agora, podemos criar o código do Micro:bit Guia. Também começaremos definindo um grupo de rádio igual ao do programa que construímos para o Micro:bit Tesouro. 
Para isso, vamos à aba ``||radio:Rádio||`` e posicionamos o bloco ``||radio:definir grupo de rádio 1||`` dentro do laço ``||basic:no iniciar||``.
 
```blocks
radio.setGroup(1)
```

## Step 2

Neste momento, devemos observar que tudo que este Micro:bit irá executar dependerá de um sinal de rádio recebido. 
Portanto, o laço que vamos usar não é o ``||basic:sempre||``, e sim o laço ``||radio: ao receber rádio receivedNumber||`` presente na aba ``||radio:Rádio||`` na seção *Receive*. 

```blocks
radio.onReceivedNumber(function (receivedNumber) {
	
})
radio.setGroup(1)
```

## Step 3

Feito isso, precisamos identificar qual a intensidade da mensagem recebida pelo rádio e, consequentemente, inferir a distância do Micro:bit escondido.
Então, criaremos uma ``||variables:variável||`` denominada ``||variables: Intensidade Sinal||`` e adicionaremos o seu bloco de definição dentro do laço ``||radio: ao receber rádio receivedNumber||`` que incluímos anteriormente.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = 0
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 4

Essa variável deve armazenar a intensidade do sinal de rádio recebido. Para isso, volte à aba ``||radio:Rádio||`` , 
selecione o último bloco, ``||radio: received packet intensidade do sinal||``, e o insira como dado do bloco ``||variables:definir||`` adicionado anteriormente.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 5

Agora, vá até a aba ``||Logic:Lógica||`` e adicione um laço ``||Logic:se-então||`` com um ``||Logic:comparador||``.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (0 == 0) {
    	
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 6

Nesta primeira faixa, desejamos comparar ``||Logic:SE||`` a variável ``||variables:Intensidade Sinal||`` é **menor ou igual a -80**.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Intensidade_Sinal <= -80) {
    	
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 7

Se a condição for atendida, vamos ``||basic:mostrar o ícone||`` com quatro LEDs centrais acesos.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Intensidade_Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 8

Para a próxima faixa, vamos usar o operador booleano ``||logic:E||``, pois temos duas condições que devem ser atendidas ao mesmo tempo. Temos que avaliar ``||Logic:se||`` a ``||variables:Intensidade Sinal||`` é **maior que -80** ``||logic:E||`` **menor que -50**.

 Vamos precisar de outro laço ``||logic:se-então||``, o operador ``||logic:E||`` e dois ``||logic:comparadores||``.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Intensidade_Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
    if (Intensidade_Sinal > -80 && Intensidade_Sinal < -50) {
    	
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 9

Adicione o símbolo similar ao anterior, mas com lados maiores. Ele é o primeiro ícone da última linha do bloco ``||basic:mostrar ícone||``, ao lado do que usamos no passo anterior.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Intensidade_Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
    if (Intensidade_Sinal > -80 && Intensidade_Sinal < -50) {
        basic.showIcon(IconNames.Diamond)
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 10

Para a última faixa, devemos apenas analisar se o valor da ``||variables:Intensidade Sinal||`` é **maior ou igual a -50**. Ou seja, estamos no intervalo em que o sinal é o mais forte possível, se aproximando do limite máximo de -42dB.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Intensidade_Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
    if (Intensidade_Sinal > -80 && Intensidade_Sinal < -50) {
        basic.showIcon(IconNames.Diamond)
    }
    if (Intensidade_Sinal >= -50) {
    	
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

## Step 11

Por fim, adicione o bloco para ``||basic:mostrar o ícone||`` mostrar o ícone do quadrado se a última condição for atendida.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Intensidade_Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
    if (Intensidade_Sinal > -80 && Intensidade_Sinal < -50) {
        basic.showIcon(IconNames.Diamond)
    }
    if (Intensidade_Sinal >= -50) {
        basic.showIcon(IconNames.Square)
    }
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```