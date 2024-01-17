# Carrinho Funções

## Step 1

Neste tutorial, você irá aprender como programar o carrinho utilizando estruturas de
funções para facilitar a construção do código. Perceba que no último projeto tivemos que
repetir várias vezes os comandos de gravação analógica e digital das portas que controlam
os motores. Com as funções, esse processo vai ficar mais simples e nos permitirá construir
códigos para percursos maiores.

## Step 2

Nosso objetivo será reconstruir o mesmo trajeto do último projeto, mas utilizando esta nova técnica.
Portanto, o carrinho deverá:

1. andar pra frente
2. virar para direita
3. andar pra frente
4. virar para esquerda
5. andar para frente
6. andar pra trás
7. parar.

## Step 3

Primeiramente, acesse a seção **Avançado**, vá até a categoria ``||functions:Funções||``, 
e clique em **Fazer uma função**. No bloco que aparecerá dentro da nova janela, clique no espaço do nome e o altere 
para ``||functions:função Andar para Frente||``. Clique em **Feito**, e o laço 
``||functions:função Andar para Frente||`` será automaticamente adicionado.

```blocks
function Andar_para_Frente () {
	
}
```

## Step 4

Em seguida, acesse a categoria **Avançado** e, na aba ``||pins:Pins||``, selecione o bloco
``||pins:gravação analógica pin P0||``. Coloque esse bloco dentro do laço 
``||functions:função Andar para Frente||``, substituindo o pino **P0** por **P12** e o seu valor de **0** por **512**.

 Este comando define a velocidade do seu carrinho, que pode variar de 0 a 1023. Logo, estamos definindo uma
 velocidade média para ambos os motores (512).

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
}
```

## Step 5

Retone à categoria **Avançado** e, na aba ``||pins:Pins||``, selecione dois blocos
``||pins:gravação digital pin P0||``. Posicione-os dentro do laço 
``||functions:função Andar para Frente||``, substituindo o pino **P0** por **P8** e **P16** respectivamente.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
```

## Step 6

Estes dois blocos de ``||pins:gravação digital||`` determinam os sentidos de rotação de nossos motores.
Dito isso, o primeiro movimento do carrinho deve ser para frente em linha reta. Então, devemos definir 
direções opostas para os motores, já que estão posicionados em sentidos opostos.

Para isso, basta alterar o valor da ``||pins:gravação digital pin P8||`` de **0** para **1**.

 *Se seu carrinho estiver indo para trás, basta inverter os valores das portas **P8** e **P16** para que ele ande para frente.*

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
```

## Step 7

Assim, temos a primeira função que faz o carrinho andar para frente pronta. 
Agora, podemos repetir o processo para criar a função ``||functions:função Andar para Trás||``.

 Acesse a seção **Avançado**, vá até a categoria ``||functions:Funções||``, 
e clique em **Fazer uma função**. Clique no espaço do nome e o altere 
para ``||functions:função Andar para Trás||``. Clique em **Feito**, e o laço 
``||functions:função Andar para Trás||`` será automaticamente adicionado.

```blocks
function Andar_para_Trás () {
	
}
```

## Step 8

Os blocos dentro dessa função serão os mesmos da função de ``||functions:função Andar para Frente||``.
Porém, vamos trocar os valores das portas **P8** e **P16**. Onde era **1** deve ser tornar **0**. Onde tínhamos 
**0**, devmos substituir por **1**.

 A ``||pins:gravação analógica pin P12 para 512||`` também deve ser inserida na nova função.

```blocks
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
```

## Step 9

Perceba que, se o seu carrinho estiver andando para trás quando você deseja que ele ande para frente,
você deverá inverter os valores das ``||pins:gravações digitais||`` das portas **P8** e **P16** nestas duas funções.
O importante é que eles sempre sejam o oposto um do outro.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
```

## Step 10

Agora, seguimos para a função ``||functions:Virar para Direita||``. 
Acesse a seção **Avançado**, vá até a categoria ``||functions:Funções||``, 
e clique em **Fazer uma função**. Altere o nome 
para ``||functions:função Virar para Direita||``. Clique em **Feito**, e o laço 
``||functions:função Virar para Direita||`` será adicionado.

```blocks
function Virar_para_Direita () {
	
}
```

## Step 11

Assim como nas outras duas funções, esta também deve conter os três blocos das portas **P12**, **P8** e **P16**.
Duplique-os e os insira no novo laço ``||functions:função Virar para Direita||``.
Defina os valores das ``||pins:gravações digitais||`` das portas **P8** e **P16** para **1**.

```blocks
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
```

## Step 12

Vamos repetir o processo para criar a ``||functions:função Virar para Esquerda||``. Entretanto,
agora teremos os valores **0** nas portas **P8** e **P16**.

```blocks
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
```

## Step 13

Se o seu carrinho estiver virando para os lados incorretos ao chamar estas funções, você deverá alterar
os valores de **P8** e **P16** dentro destes laços, mas sempre garantindo que eles sejam os iguais dentro de cada função.

```blocks
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
```

## Step 14

Feito isso, ainda falta definir a última função: ``||functions:Parar||``.
Crie a função acessando a seção **Avançado**, depois a categoria ``||functions:Funções||``, 
e clicando em **Fazer uma função**.

```blocks
function Parar () {
	
}
```

## Step 15

Dentro deste laço, devemos apenas parar o motor. Portanto, duplique somente o bloco
``||pins:gravação analógica pin P12 para 512||``. Altere o seu valor de **512** para **0**.

```blocks
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
```

## Step 16

Com todas as funções programadas, podemos criar um código que será uma combinação destes movimentos.
Precisamos programar o carrinho para executar os movimentos abaixo quando pressionarmos o ``||Input:Botão A||``:

1. andar pra frente
2. virar para direita
3. andar pra frente
4. virar para esquerda
5. andar para frente
6. andar pra trás
7. parar.

## Step 17

Então, acesse a aba ``||input:Input||`` e selecione o laço 
``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
```

## Step 18

Dentro deste laço, vamos "chamar" as funções que definem cada movimento. Para isso,
vá à aba ``||functions:Funções||`` e selecione o bloco ``||functions:ligar Andar_para_Frente||``.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
})
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
```

## Step 19

Antes de chamarmos a próxima função para que ele vire à direita, devemos determinar por quanto tempo
o carrinho vai andar para frente. Fazemos isso adicionando um bloco de ``||basic:pausa||``,
localizado na aba ``||basic:Básico||``. Ajuste a duração da pausa, trocando o valor **100** por **2000** 
ou qualquer outro valor desejado. 

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
})
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
```

## Step 20

Agora, adicionamos o bloco ``||functions:função Virar para Direita||`` seguido de uma ``||basic:pausa||``.
Altere a duração deste movimento para **500ms** ou de acordo com sua preferência.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
})
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
```

## Step 21

Repita esse processo para os próximos movimentos, lembrando de ajustar os valores de pausa para cada um deles.
Se necessário, confira a sequência do seu código clicando na lâmpada de dicas.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Esquerda()
    basic.pause(500)
    Andar_para_Frente()
    basic.pause(2000)
    Andar_para_Trás()
    basic.pause(1000)
    Parar()
})
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
```

## Step 22

Para finalizarmos nosso programa, precisamos atribuir um botão para interromper o movimento do carrinho a qualquer momento. 
Então, acesse a aba ``||Input:Input||`` e adicione mais um laço ``||Input:no botão A pressionado||`` ao código. 
Altere de ``||Input:botão A||`` para ``||Input:botão B||``.

```blocks
input.onButtonPressed(Button.B, function () {
	
})
```

## Step 23

Dentro deste laço, inclua o chamado da função ``||functions:Parar||``.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Esquerda()
    basic.pause(500)
    Andar_para_Frente()
    basic.pause(2000)
    Andar_para_Trás()
    basic.pause(1000)
    Parar()
})
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
input.onButtonPressed(Button.B, function () {
    Parar()
})
```

## Step 24

Agora o carrinho já pode percorrer o percurso ao pressionar o ``||input:botão A||``. 
Teste como essa nova estrutura de código, utilizando ``||functions:funções||``, facilita o
acréscimo de movimentos utilizando poucos blocos. O limite é apenas sua imaginação.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, 512)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Esquerda()
    basic.pause(500)
    Andar_para_Frente()
    basic.pause(2000)
    Andar_para_Trás()
    basic.pause(1000)
    Parar()
})
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
input.onButtonPressed(Button.B, function () {
    Parar()
})
```
