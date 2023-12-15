# Contador de Palmas

## Step 1

Neste tutorial, você irá aprender a fazer um contador de palmas utilizando o 
Micro:bit.

## Step 2

Primeiramente, acesse a aba ``||variables:Variáveis||`` e clique em **Fazer uma variável**.
Coloque o nome dessa variável como ``||variables:Contador||``.

## Step 3

Na aba ``||input:Input||``, pegue o laço ``||input:ao som do alto||``. Esse 
laço usa o sensor de som do Micro:bit, executando todos os blocos que 
forem colocados dentro dele quando o micro:bit percebe um som **alto**. 
Ele será o reponsável por "escutar" as palmas em nosso programa.

```blocks
input.onSound(DetectedSound.Loud, function () {

})
```

## Step 4

Retorne à aba ``||variables:Variáveis||`` e pegue o comando 
``||variables:alterar Contador por 1||``. Coloque esse bloco dentro do 
laço ``||input:ao som do alto||``. Agora, com o auxílio dessa variável, as palmas 
já estão sendo contadas, falta apenas mostrar essa contagem na matriz de LEDs. 

```blocks
input.onSound(DetectedSound.Loud, function () {
    Contador += 1
})
```


## Step 5

Para isso, acesse a aba ``||basic:Básico||``, pegue o bloco ``||basic:mostrar número||`` e coloque-o 
abaixo do bloco ``||variables:alterar Contador por 1||``.

```blocks
input.onSound(DetectedSound.Loud, function () {
    Contador += 1
    basic.showNumber(0)
})
})
```
## Step 6

Por fim, volte na aba ``||variables:Variáveis||`` e pegue o bloco redondo 
``||variables:Contador||``. Coloque essa variável dentro do espaço circular do bloco 
``||basic:mostrar número||``, substituindo o número **0**.

```blocks
input.onSound(DetectedSound.Loud, function () {
    Contador += 1
    basic.showNumber(Contador)
})
```

## Step 7
Pronto! Você já pode carregar seu código para o Micro:bit e testar seu contador de palmas.
