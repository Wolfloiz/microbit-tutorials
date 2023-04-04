


## Step 1

Vamos aprender a fazer dois micro:bits se comunicarem via rádio. Primeiro, vamos 
programar o primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos pegar o bloco ``||radio:definir grupo do rádio 1||``, na aba 
``||radio:Rádio||``, e colocá-lo dentro do bloco ``||basic:no iniciar||``. Esse bloco 
serve para que todos os micro:bits dentro desse mesmo grupo estejam conectados uns com 
os outros.

```blocks
radio.setGroup(1)
```

## Step 3

Vamos agora determinar a "força" com que o micro:bit irá transmitir informações. Isso irá 
determinar a distância da comunicação. Vamos adicionar o bloco 
``||radio:conjunto de rádio transmite energia||`` que se encontra na 
aba ``||radio:Rádio->mais||``, e colocá-lo no bloco ``||basic:no iniciar||``. Pronto, 
agora a parte da comunicação do primeiro micro:bit está feita. Mas o que estaremos 
comunicando?


```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
```

## Step 4

Vamos fazer um teste simples, iremos enviar um número de um micro:bit para outro. 
Temos então que adicionar o bloco ``||radio:rádio envia número 0||`` localizado na aba 
``||radio:Rádio||``, e colocá-lo dentro de ``||basic:sempre||``. Pronto, podemos agora 
escolher que número queremos enviar.


```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
basic.forever(function () {
    radio.sendNumber(7)
})
```


## Step 5

Agora que configuramos o primeiro micro:bit, falta configurar o segundo. Vamos lá!







