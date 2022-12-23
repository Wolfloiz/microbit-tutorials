# My Tutorial

### @activities 1

## Introdução

### Introduction step

# Queda Livre 
Neste projeto, vamos observar como a aceleração da gravidade age sobre todos os objetos ao nosso redor. Vamos usar um servo motor para soltar uma esfera de metal,
e calcular o tempo gasto para que ela saia do repouso e chegue até o botão na base da torre de queda.

## Parte 1 - Controlando a torre de queda

### Step 1
## Parte 1 - Controlando a torre de queda

### Step 1
# Parte 1 - Controlando a torre de queda
Vamos começar programando a configuração da torre para que ela solte a esfera e usar um botão para reiniciar o experimento, voltando todas as variáveis ao seu estado inicial.
### Step 2
Acesse a aba ``||Basic:Básico||`` e adicione o laço ``||Basic:no iniciar||``. Em seguida, clique em **Avançado**, vá até a aba ``||Pins:Pins||`` e inclua o bloco ``||Pins:gravação analógica pin P0 para 1023||`` no laço ``||Basic:no iniciar||``.

```blocks
pins.analogWritePin(AnalogPin.P0, 1023)
```

### Step 3
Altere a porta de ``||Pins:P0||`` para ``||Pins:P12||``, pois essa é a porta onde conectamos o servo.

```blocks
pins.analogWritePin(AnalogPin.P12, 1023)
```
### Step 4
Adicione o laço ``||Input:no botão A pressionado||``, localizado na aba ``||Input:Input||`` para programarmos a etapa em que o servo solta a bolinha.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
pins.analogWritePin(AnalogPin.P12, 1023)
```
### Step 5
Agora, vá até a aba ``||Variables:Variáveis||`` e crie as quatro variáveis a seguir: ``||Variables:Servo acionado||``, ``||Variables:Tempo inicial||``, ``||Variables:Tempo final||`` e ``||Variables:Tempo de Queda||``.
Volte até a aba ``||Variables:Variáveis||`` e insira um bloco de definição no laço ``||Input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_de_queda = 0
})
let Tempo_de_queda = 0
pins.analogWritePin(AnalogPin.P12, 1023)
```

### Step 6
Altere a variável do bloco de definição para ``||Variables:Tempo inicial||``. Em seguida, volte até a aba ``||Input:Input||``, clique em ``||Input:...mais||`` e selecione o bloco ``||Input:tempo de execução (micros)||`` para substituir o **0**. 

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
})
let Tempo_inicial = 0
pins.analogWritePin(AnalogPin.P12, 1023)
```
### Step 7
Abaixo deste bloco, adicione a ``||Pins:gravação analógica pin P0 para 1023||``, situado na aba ``||Pins:Pins||``. Altere a porta para ``||Pins:P12||`` e o valor para **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.analogWritePin(AnalogPin.P12, 0)
})
let Tempo_inicial = 0
pins.analogWritePin(AnalogPin.P12, 1023)
```
### Step 8
Adicone outro bloco de ``||Variables:definição de variáveis||`` abaixo do anterior. Substitua os campos para a variável ``||Variables:Servo acionado||`` e **1**.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.analogWritePin(AnalogPin.P12, 0)
    Servo_acionado = 1
})
let Servo_acionado = 0
let Tempo_inicial = 0
pins.analogWritePin(AnalogPin.P12, 1023)
```
### Step 9
Agora, vamos programar o processo para reiniciar a torre de queda, ou seja, voltar o servo a sua posição inicial e redefinir as variáveis. 
Para isso, vá à aba ``||Input:Input||`` e adicione o laço ``||Input:no botão A pressionado||``. Altere o campo de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.analogWritePin(AnalogPin.P12, 0)
    Servo_acionado = 1
})
input.onButtonPressed(Button.B, function () {
	
})
let Servo_acionado = 0
let Tempo_inicial = 0
pins.analogWritePin(AnalogPin.P12, 1023)
```

### Step 10
Dentro do laço ``||Input:no botão B pressionado||``, duplique o bloco  ``||Pins:gravação analógica pin P0 para 1023||`` 
que inserimos no laço ``||Basic:no iniciar||`` quando começamos esta etapa do tutorial.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.analogWritePin(AnalogPin.P12, 0)
    Servo_acionado = 1
})
input.onButtonPressed(Button.B, function () {
    pins.analogWritePin(AnalogPin.P12, 1023)
})
let Servo_acionado = 0
let Tempo_de_queda = 0
pins.analogWritePin(AnalogPin.P12, 1023)
```

### Step 11
Abaixo deste bloco, inclua dois outros de ``||Variables:definição de variáveis||``. Neles, vamos definir ``||Variables:Tempo Inicial||`` para **0** e ``||Variables:Servo acionado||`` para **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.servoWritePin(AnalogPin.P12, 0)
    Servo_acionado = 1
})
input.onButtonPressed(Button.B, function () {
    pins.servoWritePin(AnalogPin.P12, 65)
    Tempo_inicial = 0
    Servo_acionado = 0
})
let Servo_acionado = 0
let Tempo_inicial = 0
pins.servoWritePin(AnalogPin.P12, 65)
```

## Parte 2 - Calculando o tempo de queda

### Step 1
# Parte 2 - Calculando o tempo de queda
A partir daqui, vamos criar o código para calcular o tempo que a esfera gastou para cair na torre.

### Step 2
Adicione um laço ``||Basic:sempre||`` presente na aba ``||Basic:Básico||`` ao código construído até o momento.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.analogWritePin(AnalogPin.P12, 0)
    Servo_acionado = 1
})
input.onButtonPressed(Button.B, function () {
    pins.analogWritePin(AnalogPin.P12, 1023)
    Tempo_inicial = 0
    Servo_acionado = 0
})
let Servo_acionado = 0
let Tempo_inicial = 0
pins.analogWritePin(AnalogPin.P12, 1023)
basic.forever(function () {
	
})
```

### Step 3
Vá até a aba ``||Logic:Lógica||`` e selecione o laço ``||Logic:se verdadeiro então||``. Ele deve ser posicionado dentro do laço ``||Basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})
```

### Step 4
Volte à aba ``||Logic:Lógica||`` e selecione o operador ``||Logic:Booleano||`` ``||Logic:E||`` para ser posicionado dentro do laço ``||Logic:se verdadeiro então||`` no campo onde estava *verdadeiro*.

```blocks
basic.forever(function () {
    if (false && false) {
    	
    }
})
```

### Step 5
Agora, adicione dois blocos ``||Logic:comparadores||``, também presentes na aba ``||Logic:Lógica||``, para ficarem dentro das condições do operador ``||Logic:E||``.

```blocks
basic.forever(function () {
    if (0 == 0 && 0 == 0) {
    	
    }
})
```

### Step 6
Neste momento, vamos preencher um dos campos das comparações com ``||Pins:leitura digital pin P1||`` igual a **1** presente na aba ``||Pins:Pins||``. Do outro lado, teremos a variável ``||Variables:Servo acionado||`` igual a **1**.
Lembre-se de alterar de Pin ``||Pins:P0||`` para ``||Pins:P1||``.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
    	
    }
})
```

### Step 7
Agora, dentro do laço ``||Logic:se verdadeiro então||``, adicione um bloco de ``||Variables:definição de variáveis||``. Altere o campo para a variável  ``||Variables:Tempo final||`` e o valor 
``||Input:tempo de execução (micros)||``, localizado na aba nas opções extras da ``||Input:Input||``, acessíveis quando clicamos em **...mais**.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
    }
})
```

### Step 8
Em seguida, adicione outro bloco de ``||Variables:definição||`` que usaremos para calcular a variável ``||Variables:Tempo de queda||``.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = 0
    }
})
```

### Step 9
Vá até a aba ``||Math:Matemática||`` e insira o bloco de ``||Math:subtração||`` onde estava **0** no bloco de ``||Variables:definição||`` adicionado no passo anterior.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = 0 - 0
    }
})
```

### Step 10
Em nossa ``||Math:subtração||``, teremos do lado esquerdo a variável ``||Variables:Tempo final||``, e do lado direito a variável ``||Variables:Tempo inicial||``. 
Assim, estamos dizendo que ``||Variables:Tempo de queda||`` é a diferença entre o tempo que a esfera chegou no fundo da torre e o tempo marcado quando abrimos o servo.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = Tempo_final - Tempo_inicial
    }
})
```

### Step 11
Abaixo deste bloco, adicione o comando ``||Basic:mostrar número||``, presente na aba ``||Basic:Básico||``.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = Tempo_final - Tempo_inicial
        basic.showNumber(0)
    }
})
```

### Step 12
Entretanto, o resultado da nossa subtração está em microssegundos. Para transformá-lo em segundos, vamos até a aba ``||Math:Matemática||`` e incluímos o bloco de ``||Math:divisão||`` no campo
onde estava **0**.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = Tempo_final - Tempo_inicial
        basic.showNumber(0 / 0)
    }
})
```

### Step 13
Altere os campos da operação para a variável ``||Variables:Tempo de queda||`` e o número **1000000**.

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = Tempo_final - Tempo_inicial
        basic.showNumber(Tempo_de_queda / 1000000)
    }
})
```

### Step 14
Finalmente, temos o programa completo para configurar, reiniciar a torre de queda e calcular o tempo gasto para a esfera cair.

```blocks
input.onButtonPressed(Button.A, function () {
    Tempo_inicial = input.runningTimeMicros()
    pins.analogWritePin(AnalogPin.P12, 0)
    Servo_acionado = 1
})
input.onButtonPressed(Button.B, function () {
    pins.analogWritePin(AnalogPin.P12, 1023)
    Tempo_inicial = 0
    Servo_acionado = 0
})
let Tempo_de_queda = 0
let Tempo_final = 0
let Servo_acionado = 0
let Tempo_inicial = 0
pins.analogWritePin(AnalogPin.P12, 1023)
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && Servo_acionado == 1) {
        Tempo_final = input.runningTimeMicros()
        Tempo_de_queda = Tempo_final - Tempo_inicial
        basic.showNumber(Tempo_de_queda / 1000000)
    }
})
```