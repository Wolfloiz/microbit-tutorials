


## Step 1

Vamos aprender a fazer um jogo de caça ao tesouro usando dois micro:bits, um deles 
será o escondido e enviará sinais de rádio para outro será o caçador, funcionando como um radar. 
Começaremos pela programação do Micro:bit Tesouro.

## Step 2

Primeiramente, vamos até a aba ``||radio:Rádio||``, selecionamos o bloco ``||radio:definir grupo do rádio 1||`` 
e o colocamos dentro do laço ``||basic:no iniciar||``. Esse comando
serve para determinar que todos os Micro:bits dentro desse mesmo grupo estejam conectados entre si. 
Portanto, certifique-se de que o grupo do seu Micro:bit seja diferente dos outros grupos da sua sala de aula.

```blocks
radio.setGroup(1)
```

## Step 3

Em seguida, vamos adicionar o bloco ``||radio:conjunto de radio transmite o número serial verdadeiro||``,
 localizado na aba 
``||radio:Rádio->mais||``. Ele deve ser inserido logo abaixo do ``||radio:definir grupo do rádio 1||``.

```blocks
radio.setGroup(1)
radio.setTransmitSerialNumber(true)
```

## Step 4

Agora, vamos determinar a força com que o micro:bit irá transmitir informações. Isso
determina a distância da comunicação. Devemos escolher esse número de acordo com o tamanho 
do lugar escolhido para esconder/procurar o tesouro. Vamos adicionar o bloco 
``||radio:conjunto de rádio transmite energia 6||`` que se encontra na 
aba ``||radio:Rádio->mais||``, e colocá-lo no laço ``||basic:no iniciar||``. Feito isso, 
a parte da comunicação do Micro:bit Tesouro está finalizada. 


```blocks
radio.setGroup(1)
radio.setTransmitSerialNumber(true)
radio.setTransmitPower(6)
```

## Step 5

Vamos enviar um número qualquer para o outro Micro:bit Caçador para que os Micro:bits 
se comuniquem constantemente. 
Então, adicionamos o bloco ``||radio:rádio envia número 0||`` localizado na aba 
``||radio:Rádio||``, e o inserimos dentro do laço ``||basic:sempre||``.


```blocks
radio.setGroup(1)
radio.setTransmitSerialNumber(true)
radio.setTransmitPower(6)
basic.forever(function () {
    radio.sendNumber(0)
})
```


## Step 6

Agora que configuramos o Micro:bit Tesouro, ainda falta programar o Caçador. Então, vamos lá!
