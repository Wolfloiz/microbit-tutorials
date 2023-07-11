## Step 1

Neste tutorial, vamos programar o segundo micro:bit (M2), que irá receber as informações enviadas
pelo primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos selecionar o bloco `||radio:definir grupo do rádio 1||`, na categoria
`||radio:Rádio||`, e colocá-lo dentro do laço `||basic:no iniciar||`. Esse bloco
serve para garantir que todos os micro:bits dentro desse mesmo grupo de rádio estejam conectados uns com
os outros. Altere o número do grupo para o mesmo valor que você usou no tutorial anterior no código do primeiro Micro:bit.

```blocks
radio.setGroup(255)
```

## Step 3

Em seguida, vamos adicionar o laço `||radio:ao receber rádio receivedNumber||`,
que pode ser encontrado na aba `||radio:Rádio||`.
Esse bloco executa tudo que está dentro dele quando recebe um número de outro Micro:bit.

```blocks
radio.onReceivedNumber(function (receivedNumber) {

})
radio.setGroup(255)
```

## Step 4

Para exibir na tela o número que estamos recebendo via rádio (e ver se os micro:bits estão
se comunicando corretamente), devemos adicionar o bloco `||basic:mostrar número||`, situado na categoria `||basic:Básico||`,
dentro do laço `||radio:ao receber rádio receivedNumber||`.
Por fim, vamos arrastar _(clique sobre ela e mova o mouse)_ a variável `||variables:receivedNumber||` do laço
`||radio:ao receber rádio receivedNumber||` para o bloco `||basic:mostrar número||`, para termos: `||basic:mostrar número||` `||variables:receivedNumber||`.

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    basic.showNumber(receivedNumber)
})
radio.setGroup(255)
```

## Step 6

Pronto, agora temos os dois Micro:bits configurados e comunicando entre si. Verifique se o número que
M1 transmite está aparecendo em M2 corretamente!
