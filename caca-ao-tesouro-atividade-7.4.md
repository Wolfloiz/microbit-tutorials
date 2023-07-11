## Step 1

Agora que já programamos o Tesouro, resta configurar o Caçador para podermos encontrar
o Micro:bit escondido!

## Step 2

Primeiramente, selecionamos o bloco `||radio:definir grupo do rádio 1||`, na aba
`||radio:Rádio||`, e o inserimos no `||basic:no iniciar||`, como fizemos
para o Micro:bit Tesouro. Certifique-se de que os dois estão com o mesmo valor do grupo
de rádio.

```blocks
radio.setGroup(1)
```

## Step 3

Em seguida, vamos adicionar o laço `||radio:ao receber rádio receivedNumber||`,
situado na aba `||radio:Rádio||`. Esse bloco executa tudo que está dentro dele quando
o Micro:bit recebe um número enviado por Rádio.

```blocks
radio.onReceivedNumber(function (receivedNumber) {

})
radio.setGroup(1)
```

## Step 4

Agora, para procurarmos o Tesouro, vamos nos basear na distância entre os Micro:bits.
Para estimarmos essa distância, usamos a potência do sinal. Quanto mais longe eles estiverem
um do outro, mais fraco será o sinal. Se estiverem perto, o sinal de rádio estará mais forte.

## Step 5

Para isso, vamos criar uma variável chamada `||variables:Sinal||`. Em seguida, adicionamos o bloco
`||variables:definir Sinal para||` dentro do laço `||radio:ao receber rádio receivedNumber||`.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = 0
})
let Sinal = 0
radio.setGroup(1)
```

## Step 6

Agora usamos o bloco `||radio:received packet intensidade do sinal||` na aba
`||radio:Rádio||` e o inserimos no comando `||variables:definir Sinal para||`.
Dessa forma, a variável `||variables:Sinal||` passa a ter o valor da intensidade atual
do sinal.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
})
let Sinal = 0
radio.setGroup(1)
```

## Step 7

Agora que temos a informação da intensidade do sinal, vamos mostrar símbolos na tela
para representar a distância do Tesouro. Para isso, dentro do laço
`||radio:ao receber rádio receivedNumber||`, vamos adicionar três laços
`||logic:se-então||` presentes na aba `||logic:Lógica||`.

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

No primeiro laço `||logic:se-então||`, vamos adicionar a condição
`||logic:Sinal ≤ -80||`, que seria um sinal fraco, pois o Tesouro estaria longe. No
segundo, vamos precisar do operador `||logic:E||`, também presente na aba `||logic:Lógica||`,
para testarmos duas condições simultâneas. Vamos avaliar se `||logic:Sinal ≤ -50 e Sinal < -80||`,
o que seria uma distância média. Por fim, no último laço, usamos a condição
`||logic:Sinal > -50||`, que seria um sinal forte, indicando que o Tesouro está próximo.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Sinal <= -80) {

    }
    if (Sinal <= -50 && Sinal > -80) {

    }
    if (Sinal > -50) {

    }
})
let Sinal = 0
radio.setGroup(1)
```

## Step 9

Por fim, para que o micro:bit nos indique se o Tesouro está perto ou longe,
precisamos que ele nos mostre algo visual na tela. Para isso, vamos adicionar o bloco
`||basic:mostrar ícone||` dentro de cada um dos laços `||logic:se-então||`. Vamos
selecionar o primeiro ícone como um diamante pequeno (distante), o segundo como um diamante
maior (intermediário) e o terceiro como um quadrado (próximo).

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    Sinal = radio.receivedPacket(RadioPacketProperty.SignalStrength)
    if (Sinal <= -80) {
        basic.showIcon(IconNames.SmallDiamond)
    }
    if (Sinal <= -50 && Sinal > -80) {
        basic.showIcon(IconNames.Diamond)
    }
    if (Sinal > -50) {
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
