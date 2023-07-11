## Step 1

Neste tutorial, vamos aprender como fazer dois micro:bits se comunicarem via rádio. Para iniciar, vamos
programar o primeiro micro:bit (M1).

## Step 2

Primeiramente, vamos selecionar o bloco `||radio:definir grupo do rádio 1||`, na categoria
`||radio:Rádio||`, e colocá-lo dentro do laço `||basic:no iniciar||`. Esse bloco
serve para garantir que todos os micro:bits dentro desse mesmo grupo de rádio estejam conectados uns com
os outros. Portanto, certifique-se de que o grupo do seu Micro:bit seja diferente dos outros grupos da sua sala de aula.

Altere o número do grupo de **1** para **255**, ou outro número próximo deste valor.

```blocks
radio.setGroup(255)
```

## Step 3

Agora, vamos determinar a força com que o micro:bit irá transmitir informações. Isso
determina a distância da comunicação. Devemos escolher esse número de acordo com o tamanho
do lugar escolhido para esconder/procurar o tesouro. Para isso, vamos adicionar o bloco
`||radio:conjunto de rádio transmite energia 6||` que se encontra na
aba `||radio:Rádio->mais||`, e colocá-lo no laço `||basic:no iniciar||`.
Assim, a configuração da comunicação do primeiro micro:bit está feita. Mas o que vamos comunicar?

```blocks
radio.setGroup(255)
radio.setTransmitPower(7)
```

## Step 5

Vamos fazer um teste simples, enviaremos um número de um Micro:bit para o outro.
Então, temos então que adicionar o bloco `||radio:rádio envia número 0||` localizado na aba
`||radio:Rádio||`, e colocá-lo dentro de `||basic:sempre||`.
Desse modo, podemos escolher qual número queremos enviar alterando o valor dentro deste bloco.

```blocks
radio.setGroup(255)
radio.setTransmitPower(7)
basic.forever(function () {
    radio.sendNumber(7)
})
```

## Step 6

Agora que configuramos o primeiro micro:bit, ainda falta configurar o segundo. Vamos lá!
