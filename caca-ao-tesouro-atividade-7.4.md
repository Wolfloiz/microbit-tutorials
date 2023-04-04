


## Step 1

Agora que já programamos o Tesouro, resta programar o Caçador, para podermos encontrar 
o Tesouro!


## Step 2

Primeiramente, vamos pegar o bloco ``||radio:definir grupo do rádio 1||``, na aba 
``||radio:Rádio||``, e colocá-lo dentro do bloco ``||basic:no iniciar||``, igual fizemos 
para o Tesouro.

```blocks
radio.setGroup(1)
```

## Step 3

Em seguida, vamos adicionar o bloco ``||radio:ao receber rádio receivedNumber||``,
 que pode ser achado na aba 
``||radio:Rádio||``. Esse bloco executa tudo que está dentro dele quando recebe um 
número de outro micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
	
})
radio.setGroup(1)
```

## Step 4

Agora, para procurarmos o Tesouro, vamos nos basear na distância entre os micro:bits. 
Para estimarmos essa distância, vamos usar a potência do sinal. Quão mais fraco o sinal 
enviado pelo Tesouro for, mais longe ele se encontra. E quão mais forte for o sinal, 
mais perto estamos de encontrar o Tesouro!!

## Step 5

Para verificarmos quão forte ou fraco está o sinal, vamos primeiro criar uma variável 
chamada ``||variables:Sinal||``. Vamos então colocar o bloco 
``||variables:definir Sinal para||`` dentro do bloco 
``||radio:ao receber rádio receivedNumber||`` e dentro do bloco ``||basic:no iniciar||``.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = 0
})
let Sinal = 0
radio.setGroup(1)
```

## Step 6

Vamos agora pegar o sinal ``||radio:received packet intensidade do sinal||`` na aba 
``||radio:Rádio||`` e adicioná-lo ao bloco ``||variables:definir Sinal para||``. 
Dessa forma, a variável ``||variables:Sinal||`` agora tem o valor da intensidade atual 
do sinal.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
})
let Sinal = 0
radio.setGroup(1)
```

## Step 7

Com a informação da intensidade do sinal, vamos agora mostrar na tela símbolos 
para representar quão perto ou longe está o Tesouro. Para isso, dentro do bloco 
``||radio:ao receber rádio receivedNumber||``, vamos adicionar três laços 
``||logic:se-então||``.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (true) {
    	
    }
    if (true) {
    	
    }
    if (true) {
    	
    }
})
let Sinal = 0
radio.setGroup(1)
```

## Step 8

No primeiro laço ``||logic:se-então||``, vamos adicionar a condição 
``||logic:Sinal ≤ -80||``, que é um sinal fraco, ou seja, o Tesouro está longe. No 
segundo laço ``||logic:se-então||``, vamos adicionar a condição 
``||logic:Sinal ≤ -50 e Sinal ≥ -80||``, que é um sinal intermediário, ou seja, o 
Tesouro não está nem perto, nem longe. Por fim, no laço restante, 
vamos adicionar a condição 
``||logic:Sinal ≥ -50||``, que é um sinal forte, ou seja, o Tesouro está próximo.


```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Sinal <= -80) {
    	
    }
    if (Sinal <= -50 && Sinal >= -80) {
    	
    }
    if (Sinal >= -50) {
    	
    }
})
let Sinal = 0
radio.setGroup(1)
```

## Step 9

Por fim, para que o micro:bit nos permite saber se o Tesouro está perto ou longe, 
precisamos que ele nos mostre algo visualmente. Para isso, vamos adicionar o bloco 
``||basic:mostrar ícone||`` dentro de cada um dos laços ``||logic:se-então||``. Vamos 
selecionar o primeiro ícone como um diamante pequeno (distante), o segundo como um diamante 
maior (intermediário) e o terceiro como um quadrado (próximo).

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
    if (Sinal <= -50 && Sinal >= -80) {
        basic.showIcon(IconNames.Diamond)
    }
    if (Sinal >= -50) {
        basic.showIcon(IconNames.Square)
    }
})
let Sinal = 0
radio.setGroup(1)
```



## Step 10

Pronto, agora que temos o Tesouro e o Caçador, está na hora de brincar! Peça alguém para 
esconder o Tesouro para que você possa caçá-lo!! Ou esconda o Tesouro e veja se seus 
amigos conseguem encontrá-lo!!!







