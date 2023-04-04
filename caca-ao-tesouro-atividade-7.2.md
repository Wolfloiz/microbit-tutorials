


## Step 1

Vamos agora programar o segundo micro:bit (M2), que irá receber as informações enviadas 
pelo primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos pegar o bloco ``||radio:definir grupo do rádio 1||``, na aba 
``||radio:Rádio||``, e colocá-lo dentro do bloco ``||basic:no iniciar||``, igual fizemos 
para o primeiro micro:bit.

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

Para mostrar o número que estamos recebendo na tela (e ver se os micro:bits estão 
se comunicando corretamente), vamos então adicionar o bloco ``||basic:mostrar número||`` e 
colocá-lo dentro do bloco ``||radio:ao receber rádio receivedNumber||``. Por fim, vamos 
arrastar a variável ``||radio:receivedNumber||`` do bloco 
``||radio:ao receber rádio receivedNumber||`` para o bloco ``||basic:mostrar número||``, de forma a 
ficar ``||basic:mostrar número receivedNumber||``.


```blocks
radio.onReceivedNumber(function (receivedNumber) {
    basic.showNumber(receivedNumber)
})
radio.setGroup(1)
```


## Step 5

Pronto, agora temos os dois micro:bits configurados e comunicando. Veja se o número que 
M1 transmite está aparecendo em M2 corretamente!







