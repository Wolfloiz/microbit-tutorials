# Caça ao tesouro - Micro:bit Tesouro

## Step 1

Vamos começar a programar nosso Micro:bit Tesouro, ou seja, a placa que ficará escondida enviando sinais de rádio para ser encontrada.
Precisamos atribuir um ``||radio:grupo de rádio||`` no início do código, quando ligarmos as placas. 

 Para fazer isso, vamos até a aba ``||radio:Rádio||``, selecionamos o bloco ``||radio:definir grupo de rádio 1||``, e o adicionamos dentro do laço ``||basic:no iniciar||``. 
```blocks
radio.setGroup(1)
```

## Step 2

Ajuste o valor dentro do bloco ``||radio:definir grupo de rádio 1||`` para que seja diferente dos outros grupos de alunos.
Se ficarem iguais, os sinais dos Micro:bits de seus colegas irão interferir no funcionamento do seu projeto. 

##Step 3

Agora, vamos definir a intensidade dos sinais que serão enviados. Retorne à aba  ``||radio:Rádio||``, clique nos três pontos que se abrem abaixo do ícone da aba e selecione o bloco ``||radio:conjunto de rádio transmite energia 7||``.

```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
```
##Step 4

Vamos alterar a potência para **6**, para restringir um pouco a área em que vamos procurar o "tesouro". Porém, você pode ajustar de acordo com sua preferência e ambiente em que deseja testar. Por exemplo, se você realizar essa atividade em ambientes abertos e mais extensos, o valor **7** pode ser mantido.

## Step 5

Agora, podemos programar o sinal que ``||basic:sempre||`` será enviado por este Micro:bit Tesouro. Perceba que dentro da aba ``||radio:Rádio||`` temos a seção *Send*, onde definimos que tipo de informação desejamos enviar. 

 Adicione o bloco  ``||radio:rádio envia número 0||`` no laço  ``||basic:sempre||``.
```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
basic.forever(function () {
    radio.sendNumber(0)
})
```

## Step 6
Para sinalizar ao usuário esse envio, também podemos incluir a exibição de um coração pulsante. Para isso, usamos dois ícones presentes no bloco ``||basic:mostrar ícone||``. 
Ao posicioná-los dentro do laço ``||basic:sempre||``, podemos alterar a figura exibida clicando na setinha que abre as opções de exibição.

```blocks
radio.setGroup(1)
radio.setTransmitPower(7)
basic.forever(function () {
    radio.sendNumber(0)
    basic.showIcon(IconNames.SmallHeart)
    basic.showIcon(IconNames.Heart)
})
```
