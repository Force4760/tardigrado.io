+++
title = "Números, Símbolos e Funções"
date = "2022-03-17"
tags = ['Lisp', 'Coding']
description = "Básicos sobre números, Símbolos e Fuções em Common Lisp"
+++

## 1 Números

Em matemática aprendemos sobre alguns conjuntos de números: os naturais `N`, inteiros `Z`, racionais `Q`, reais `R`, complexos `C`, entre outros. Em Lisp não é diferente e existem vários tipos de números:

- integers
- floats
- ratios

### 1.1 Integers

_Integers_ ou inteiros são números que não possuem virgulas, como:

- -10
- -1
- 0
- 1
- 10
- ...

Um inteiro obedece à seguinte expressão regular:

> ( \+ | - ) ? [ 0 - 9 ] +

Ou seja, um inteiro é um _sequencia de digitos_, de 0 a 9, que pode ser precedida por um _+_ ou um _-_.

### 1.2 Floats

_Floats_ ou números em ponto flutuante são os números reais da matemática (obviamente dentro dos limites de memória).

- -10.6
- -3.1416
- 0.001
- 1.150
- ...

Um float obedece à seguinte expressão regular:

> ( \+ | - ) ? [ 0 - 9 ] + . [ 0 - 9 ] +

Ou seja, um float é uma _sequencia de digitos_, incluindo um _ponto (.)_, que pode ser precedida por um _+_ ou um _-_.

### 1.3 Ratios

_Ratios_ são frações, como:

- -1/2
- 3/4
- 5/6
- 11/6

Um ratio obedece à seguinte expressão regular:

> ( \+ | - ) ? [ 0 - 9 ] + / [ 0 - 9 ] +

Ou seja, um ratio é uma _sequencia de digitos_, incluindo uma _barra (/)_, que pode ser precedida por um _+_ ou um _-_.

É de notar que, por exemplo _1/2_ e _4/8_ são o mesmo ratio.

## 2 Símbolos

Símbolos podem representar diversas coisas, no entanto, existem dois símbolos que são claramente mais importantes que os restantes: _T_ e _NIL_

Estes simbolos (_booleanos_) são as representações de _verdadeiro_ e _falso_:

- _T_ - "verdadeiro", "sim", "ligado"
- _NIL_ - "falso", "não", "desligado", "vazio"

## 3. Funções

Uma _função_ é uma forma de abstração e de processar argumentos. Podemos pensar nas mesmas como uma _black-box_ (caixa negra), que recebe um determinado _input_, processa o mesmo (através de uma estranha magia negra descohecida), e retorna um _output_.

Em Lisp, uma função pode ser chamada da seguinte forma:

```
(funcName arg1 arg2 ... argN)
 └──────┘ └─────────────────┘
   nome        argumentos
```

### 3.1 Predicados

Existe um tipo específico de funções que se revela extremamente útil: os _Predicados_

> _Def:_ Predicado
>
> Um predicado é uma função que retorna um valor _booleano_ (T ou NIL)

Por convenção, o nome de predicados deve terminar em _P_, de modo a indicar que se trata de uma função deste tipo.

- _zeroP_ - se o número é igual a 0
- _oddP_ - se o número é ímpar
- _evenP_ - se o número é par
- _..._
