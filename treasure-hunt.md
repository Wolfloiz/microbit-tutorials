# Caça ao Tesouro

### @activities 1

## Introdução

## Parte 1 - Micro:bit Tesouro

### Step 1
# Parte 1 -  Micro:bit Tesouro

Vamos começar a programar nosso Micro:bit Tesouro, ou seja, a placa que ficará escondida enviando sinais de rádio para ser encontrada.
Precisamos atribuir um ``||radio:grupo de rádio||`` no início do código, quando ligarmos as placas. 

 Para fazer isso, vamos até a aba ``||radio:Rádio||``, selecionamos o bloco ``||radio:definir grupo de rádio 1||``, e o adicionamos dentro do laço ``||basic:no iniciar||``. 
```blocks
radio.setGroup(1)
```
### Step 2

Ajuste o valor dentro do bloco ``||radio:definir grupo de rádio 1||`` para que seja diferente dos outros grupos de alunos.
Se ficarem iguais, os sinais dos Micro:bits de seus colegas irão interferir no funcionamento do seu projeto. 

### Step 3

Agora, vamos definir a intensidade dos sinais que serão enviados. Retorne à aba  ``||radio:Rádio||``, clique nos três pontos que se abrem abaixo do ícone da aba e selecione o bloco ``||radio:conjunto de rádio transmite energia 7||``.

```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
```
### Step 4

Vamos alterar a potência para **6**, para restringir um pouco a área em que vamos procurar o "tesouro". Porém, você pode ajustar de acordo com sua preferência e ambiente em que deseja testar. Por exemplo, se você realizar essa atividade em ambientes abertos e mais extensos, o valor **7** pode ser mantido.

### Step 5

Agora, podemos programar o sinal que ``||basic:sempre||`` será enviado por este Micro:bit Tesouro. Perceba que dentro da aba ``||radio:Rádio||`` temos a seção *Send*, onde definimos que tipo de informação desejamos enviar. 

 Adicione o bloco  ``||radio:rádio envia número 0||`` no laço  ``||basic:sempre||``.
```blocks
radio.setGroup(1)
radio.setTransmitPower(6)
basic.forever(function () {
    radio.sendNumber(0)
})
```

### Step 6
Para sinalizar ao usuário esse envio, também podemos incluir a exibição de um coração pulsante. Para isso, usamos dois ícones presentes no bloco ``||basic:mostrar ícone||``. 
Ao posicioná-los dentro do laço ``||basic:sempre||``, podemos alterar a figura exibida clicando na setinha que abre as opções de exibição.

```blocks
radio.setGroup(1)
radio.setTransmitPower(6)
basic.forever(function () {
    radio.sendNumber(0)
    basic.showIcon(IconNames.SmallHeart)
    basic.showIcon(IconNames.Heart)
})
```

## Parte 2 - Micro:bit Guia

### Step 1
# Parte 2 - Micro:bit Guia

Agora, podemos criar o código do Micro:bit Guia. Também começaremos definindo um grupo de rádio igual ao do programa que construímos para o Micro:bit Tesouro. 
Para isso, vamos à aba ``||radio:Rádio||`` e posicionamos o bloco ``||radio:definir grupo de rádio 1||`` dentro do laço ``||basic:no iniciar||``.
 
```blocks
radio.setGroup(1)
```

### Step 2

Neste momento, devemos observar que tudo que este Micro:bit irá executar dependerá de um sinal de rádio recebido. 
Portanto, o laço que vamos usar não é o ``||basic:sempre||``, e sim o laço ``||radio: ao receber rádio receivedNumber||`` presente na aba ``||radio:Rádio||`` na seção *Receive*. 

```blocks
radio.onReceivedNumber(function (receivedNumber) {
	
})
radio.setGroup(1)
```

### Step 3

Feito isso, precisamos identificar qual a intensidade da mensagem recebida pelo rádio e, consequentemente, inferir a distância do Micro:bit escondido.
Então, criaremos uma ``||variables:variável||`` denominada ``||variables: Intensidade Sinal||`` e adicionaremos o seu bloco de definição dentro do laço ``||radio: ao receber rádio receivedNumber||`` que incluímos anteriormente.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = 0
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

### Step 4

Essa variável deve armazenar a intensidade do sinal de rádio recebido. Para isso, volte à aba ``||radio:Rádio||`` , 
selecione o último bloco, ``||radio: received packet intensidade do sinal||``, e o insira como dado do bloco ``||variables:definir||`` adicionado anteriormente.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Intensidade_Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
})
let Intensidade_Sinal = 0
radio.setGroup(1)
```

### Step 5

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

### Step 6

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

### Step 7

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

### Step 8

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

### Step 9

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

### Step 10

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

### Step 11

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