# Gangorra
```package
datalogger=github:pxt-microbit/tree/master/libs/datalogger
```
## Step 1

Neste projeto vamos construir um programa capaz de armazenar dados e informações sobre a aceleração que submetemos o Micro:bit. Quando ele estiver oscilando na gangorra, observaremos valores altos de aceleração que irão diminuir até que ela chegue no estado de equilíbrio.
```blocks

```
## Step 2

Começaremos o projeto indo até a aba ``||Variables:Variáveis||`` para criar uma variável denominada ``||Variables:Registrando dados||``. Retorne até a mesma aba e adicione um bloco de ``||Variables:definição||`` dentro do laço ``||Basic:no iniciar||``.

```blocks
let Registrando_dados = 0
```

## Step 3

Vá até a aba ``||Logic:Lógica||`` e selecione o bloco com pontas triangulares ``||Logic:falso||``. Posicione-o onde estava o **0** no bloco de definição da variável ``||Variables:Registrando dados||``.

```blocks
let Registrando_dados = false
```

## Step 4

Em seguida, acesse a aba ``||datalogger:Data Logger||`` e selecione o bloco ``||datalogger:set columns||``. Ele deve ser posicionado abaixo do anterior, ainda dentro do laço ``||Basic:no iniciar||``. Dentro do campo em branco, escreva **"aceleração"**.

```blocks
let Registrando_dados = false
datalogger.setColumnTitles("aceleração")
```

## Step 5

Adicione três laços ``||Input:no botão A pressionado||``, localizados na aba ``||Input:Input||``. Altere dois deles para ``||Input:botão B||`` e ``||Input:botões A+B||`` pressionados.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.AB, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let Registrando_dados = false
datalogger.setColumnTitles("aceleração")
```

## Step 6

Dentro do primeiro laço, ``||Input:no botão A pressionado||``, vamos adicionar um bloco para definir a variável ``||Variables:Registrando dados||``. Ela será definida como ``||Logic:verdadeiro||``, através do bloco de pontas triangulares presente na aba ``||Logic:Lógica||``.

```blocks
input.onButtonPressed(Button.A, function () {
    Registrando_dados = true
})
```

## Step 7

Abaixo do bloco anterior, adicione um bloco de ``||Basic:mostrar ícone||``, pertencente à aba ``||Basic:Básico||``. Vamos mostrar o ícone de **check** para sinalizar que estamos registrando os dados.

```blocks
input.onButtonPressed(Button.A, function () {
    Registrando_dados = true
    basic.showIcon(IconNames.Yes)
})
```

## Step 8

Vamos inserir os mesmmos comandos no segundo laço, ``||Input:no botão B pressionado||``. Porém, a variável ``||Variables:Registrando dados||`` será definida como ``||Logic:falso||`` e o ``||Basic:ícone||`` exibido será o **X** para indicar que encerramos a captura de dados.

```blocks
input.onButtonPressed(Button.B, function () {
    Registrando_dados = false
    basic.showIcon(IconNames.No)
})
```

## Step 9

No terceiro laço, ``||Input:no botão A+B pressionado||``, vamos incluir o bloco  ``||datalogger:delete log||`` encontrado na aba ``||datalogger:Data Logger||``. Abaixo dele, adicione dois comandos de ``||Basic:mostrar ícone ||`` e o bloco ``||Basic:limpar tela ||``, todos pertencentes à aba ``||Basic:Básico||``.

```blocks
input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog()
    basic.showIcon(IconNames.Heart)
    basic.showIcon(IconNames.Heart)
    basic.clearScreen()
})
```

## Step 10

Altere os ``||Basic:ícones||`` que serão exibidos para o ``||Basic:quadrado pequeno||``seguido do ``||Basic:quadrado grande||``, para criar uma animação indicando que os dados registrados foram ``||datalogger:deletados||``.

```blocks
input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog()
    basic.showIcon(IconNames.SmallSquare)
    basic.showIcon(IconNames.Square)
    basic.clearScreen()
})
```

## Step 11

Agora, volte até a aba ``||datalogger:Data Logger||`` e adicione o laço ``||datalogger: on log full||``. Dentro dele, vamos novamente definir a variável ``||Variables:Registrando dados||`` como ``||Logic:falsa||``.

```blocks
datalogger.onLogFull(function () {
    Registrando_dados = false
})
```

## Step 12

Abaixo do comando de ``||Variables:definição||``, vamos mostrar o ``||Basic:ícone||`` de uma caveira para indicar que o registro está cheio e não é possível armazenar mais nenhum dado.

```blocks
datalogger.onLogFull(function () {
    Registrando_dados = false
    basic.showIcon(IconNames.Skull)
})
```

## Step 13

Acesse a aba ``||Loops:Loops||`` e selecione o laço ``||Loops:every 500 ms||``. Esse laço executará uma determinada sequência de comandos com um intervalo de tempo que estabelecermos dentro de seu campo de dados.
Altere este intervalo de ``||Loops:500ms||`` para ``||Loops:15ms||`` clicando duas vezes na área de edição e digitando o valor.

```blocks
loops.everyInterval(15, function () {
	
})
```

## Step 14

Retorne à aba ``||Logic:Lógica||`` e selecione o laço``||Logic:se verdadeiro então||``. Posicione-o dentro do ``||Loops:Loop||`` que criamos no passo anterior.

```blocks
loops.everyInterval(15, function () {
    if (true) {
    	
    }
})
```

## Step 15

Dentro do campo ``||Logic:verdadeiro||``, vamos inserir a variável ``||Variables:Registrando dados||``. 
Para isso, apenas acesse a aba ``||Variables:Variáveis||``, selecione o bloco redondo referente à variável e o posicione no campo triangular do laço ``||Logic: se então||``.

```blocks
loops.everyInterval(15, function () {
    if (Registrando_dados) {
    	
    }
})
```

## Step 16

Dentro do laço ``||Logic: se então||``, inclua o bloco  ``||datalogger:log data||`` situado na aba ``||Logic: Data Logger||``.

```blocks
loops.everyInterval(15, function () {
    if (Registrando_dados) {
        datalogger.log(datalogger.createCV("", 0))
    }
})
```

## Step 17

Ele possui dois campos para preenchermos. Clique sobre o primeiro, e selecione a palavra "aceleração" que determinamos como coluna no início do código. No segundo campo, o valor de ``||Input:aceleração (mg) no eixo X||`` do Micro:bit. Este bloco está localizado na aba ``||Input:Input||``. 

```blocks
loops.everyInterval(15, function () {
    if (Registrando_dados) {
        datalogger.log(datalogger.createCV("aceleração", input.acceleration(Dimension.X)))
    }
})
```

## Step 18

Transfira seu código completo para o Micro:bit e o posione na estrutura da gangorra. 

 Utilize o ``||Input:botão A||`` para iniciar a captura de dados. O ``||Input:botão B||`` interrompe a aquisição de dados, e os ``||Input:botões A+B||`` juntos servem para apagar os dados já registrados.

```blocks
datalogger.onLogFull(function () {
    Registrando_dados = false
    basic.showIcon(IconNames.Skull)
})
input.onButtonPressed(Button.A, function () {
    Registrando_dados = true
    basic.showIcon(IconNames.Yes)
})
input.onButtonPressed(Button.AB, function () {
    datalogger.deleteLog()
    basic.showIcon(IconNames.SmallSquare)
    basic.showIcon(IconNames.Square)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    Registrando_dados = false
    basic.showIcon(IconNames.No)
})
let Registrando_dados = false
Registrando_dados = false
datalogger.setColumnTitles("aceleração")
loops.everyInterval(15, function () {
    if (Registrando_dados) {
        datalogger.log(datalogger.createCV("aceleração", input.acceleration(Dimension.X)))
    }
})
```

## Step 19

Realize os experimentos com o Micro:bit oscilando na gangorra para armazenar os dados de aceleração. Depois de finalizados, conecte o Micro:bit ao computador novamente e abra sua pasta no explorador de arquivos.

 Abra o arquivo **MY_DATA** com seu navegador para conseguir visualizar os dados. Clique em **visual preview** para analisar o gráfico resultante dos dados. Clique e arraste sobre ele para dar zoom nos dados que estiver interessado.
