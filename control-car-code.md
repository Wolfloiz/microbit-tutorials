# Carrinho Aceleração

```template
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

## Step 1

Neste tutorial, vamos incrementar o código do carrinho para que ele seja capaz de acelerar e frear.
Ou seja, vamos modificar a velocidade que ele realiza os movimentos.

Este código reutiliza boa parte do que fizemos na atividade anterior, então recomendamos que você
finalize o projeto do Carrinho com Funções antes de presseguir.

## Step 2

Como vamos trabalhar com a velocidade do carrinho, vamos criar uma variável para essa informação.
Para isso, acesse a aba ``||variables:Variáveis||`` e clique em **Fazer uma variável**.
Nomeie essa variável como ``||variables:Velocidade||``. 
Ela poderá ser igual a qualquer número entre **0** e **1023**. Quanto maior o número, 
mais rápido estará o carrinho.

## Step 3

Acesse a categoria ``||Basic:Básico||`` e inclua o laço ``||Basic:no iniciar||``.
Em seguida, retorne à aba ``||variables:Variáveis||``, selecione o bloco 
``||variables:definir Velocidade para 0||``, e o posicione dentro do laço
``||basic:no iniciar||``, alterando o valor de **0** para **512**. Essa será 
a velocidade inicial do carrinho.

```blocks
let Velocidade = 512
```

## Step 4

Agora, vamos garantir que as funções de movimento criadas na atividade anterior recebam essa variável
para determinar a velocidade do carrinho. Para isso, retorne à aba ``||variables:Variáveis||`` e selecione o bloco de dados
redondo ``||variables:Velocidade||``. Substitua o valor **512** das ``||pins:gravações analógicas pin P12 para 512||`` das funções
``||functions:Andar para Frente||``, ``||functions:Andar para Trás||``,
``||functions:Virar para Direita||`` e ``||functions:Virar para Esquerda||``.

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
```

## Step 5

A função ``||functions:Parar||`` **não** deve ser modificada, pois o valor da ``||pins:gravação analógica pin P12 para 0||``
deve ser mantido em **0**, pois o carinho não vai se movimentar.

```blocks
function Parar () {
    pins.analogWritePin(AnalogPin.P12, 0)
}
```

## Step 6

Agora devemos criar as funções para acelerar e frear o veículo. São funções simples que vão apenas alterar o valor
da variável ``||variables:Velocidade||``.
 
Acesse a seção **Avançado**, vá até a categoria ``||functions:Funções||``, 
e clique em **Fazer uma função**. Clique no espaço do nome e o altere 
para ``||functions:Acelerar||``. Clique em **Feito**, e o laço 
``||functions:Acelerar||`` será automaticamente adicionado.

```blocks
function Acelerar () {
	
}
```

## Step 7

Em seguida, retorne à categoria ``||variables:Variáveis||`` e selecione o bloco 
``||variables:alterar Velocidade por 1||``. Posicione-o dentro da ``||functions:função Acelerar||``
recém criada. Altere o seu valor de **1** para **100**.

```blocks
function Acelerar () {
    Velocidade += 100
}
```

## Step 8

A ``||functions:função Frear||`` será bem similar a ``||functions:função Acelerar||``. Entretanto, vamos 
alterar o valor da velocidade por **-100** (negativo). Então, crie a ``||functions:função Frear||`` e inclua
o laço ``||variables:alterar Velocidade por -100||``.

```blocks
function Frear () {
    Velocidade += -100
}
```

## Step 9

Agora, nos resta alterar o movimento que programamos na atividade anterior, incluindo chamadas
dessas funções ``||functions:Frear||`` e ``||functions:Acelerar||``. Vamos começar incluindo
quatro ``||functions:ligar Acelerar||`` depois da primeira curva para direita e antes do segundo movimento para frente.

Isso siginifica que os quatro blocos ``||functions:ligar Acelerar||`` estarão depois da segunda ``||Basic:Pausa(ms)||``, cujo valor
é de **500ms** dentro do laço ``||Input:no botão A pressionado||``. 

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Acelerar () {
    Velocidade += 100
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
    Acelerar()
    Acelerar()
    Acelerar()
    Acelerar()
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
function Frear () {
    Velocidade += -100
}
let Velocidade = 0
Velocidade = 512
```

## Step 10

Por fim, inclua quatro blocos ``||functions:ligar Frear||`` depois da quarta ``||Basic:Pausa(ms)||``,
dentro do laço ``||Input:no botão A pressionado||``, cujo valor também é de **500ms** . 

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Acelerar () {
    Velocidade += 100
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
    Acelerar()
    Acelerar()
    Acelerar()
    Acelerar()
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Esquerda()
    basic.pause(500)
    Frear()
    Frear()
    Frear()
    Frear()
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
function Frear () {
    Velocidade += -100
}
let Velocidade = 0
Velocidade = 512

```

## Step 11

Teste a movimentação do seu carrinho e experimente com a inclusão de mais blocos acelerar e frear em diversos pontos do trajeto.
Fique atento para que o valor de velocidade não passe de 1023 ou fique abaixo de 0 em algum momento, já que estes são os valores máximos
que conseguimos gravar na porta P12.

Agora, você já possui todas as funções necessárias para programar seu veículo para completar diversos circuitos diferentes!
Que tal promover uma competição de robótica com sua turma?

```blocks
function Andar_para_Frente () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Virar_para_Direita () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 1)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Virar_para_Esquerda () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 0)
}
function Andar_para_Trás () {
    pins.analogWritePin(AnalogPin.P12, Velocidade)
    pins.digitalWritePin(DigitalPin.P8, 0)
    pins.digitalWritePin(DigitalPin.P16, 1)
}
function Acelerar () {
    Velocidade += 100
}
input.onButtonPressed(Button.A, function () {
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Direita()
    basic.pause(500)
    Acelerar()
    Acelerar()
    Acelerar()
    Acelerar()
    Andar_para_Frente()
    basic.pause(2000)
    Virar_para_Esquerda()
    basic.pause(500)
    Frear()
    Frear()
    Frear()
    Frear()
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
function Frear () {
    Velocidade += -100
}
let Velocidade = 0
Velocidade = 512
```