+++
title = "Listas"
date = "2022-03-18"
tags = ['Lisp', 'Coding']
description = "Básicos sobre listas em Common Lisp"
+++

Listas são _simples_, mas isso não quer dizer que não sejam poderosas. Listas são a base para outras estruturas de dados e são muito importantes em Lisp (aliás, Lisp quer dizer *LIS*t *P*rocessing).

## 1 Representação

Podemos pensar em listas de duas formas:

- forma _Escrita_

- forma como são guardadas em _Memória_

### 1.1 Escrita

Na 1ª, uma lista é simplesmente uma sequencia de _elementos_ rodeada por parênteses. Vamos ver alguns exemplos:

- (1 2 3 4 5)
- (abc de)
- (2 4 6 8)

### 1.2 Memória

No entando, para o computador, listas são: _sequencias ordenadas de cons cells, terminadas em NIL_.

Eu sei que parece complicado, mas não é. Vamos começar por entender o que é uma _cons cell_.

> _Def_: cons cell
>
> Uma _cons cell_ é um "pedaço" de memória constituido por duas células de memória, onde cada uma guarda um _apontador_ : um para o valor e um para outra célula.
>
> ```
> ┌───┬───┐
> │   │  ─┼──> prox. célula
> └─┼─┴───┘
>   v
> valor
> ```

Agora será mais fácil entender. Uma lista é, portanto, uma sequencia ordenada destes pequenos elementos, onde a última _cons cell_ aponta para _NIL_. Por exemplo:

- (1 2 3)

```
┌───┬───┐   ┌───┬───┐   ┌───┬───┐
│   │  ─┼──>│   │  ─┼──>│   │  ─┼──> NIL
└─┼─┴───┘   └─┼─┴───┘   └─┼─┴───┘
  v           v           v
  1           2           3
```

- (abc de)

```
┌───┬───┐   ┌───┬───┐
│   │  ─┼──>│   │  ─┼──> NIL
└─┼─┴───┘   └─┼─┴───┘
  v           v
  abc        de
```

- (2 4 6 8)

```
┌───┬───┐   ┌───┬───┐   ┌───┬───┐   ┌───┬───┐
│   │  ─┼──>│   │  ─┼──>│   │  ─┼──>│   │  ─┼──> NIL
└─┼─┴───┘   └─┼─┴───┘   └─┼─┴───┘   └─┼─┴───┘
  v           v           v           v
  2           4           6           8
```

Pelos exemplos anteriores, podemos ver que um elemento pode ser um número ou um símbolo, mas será que pode ser outra lista? A resposta é SIM, e chama-mos a essas listas de _nested lists_.

- ( (1 2) 3 4 5 )

```
┌───┬───┐   ┌───┬───┐   ┌───┬───┐   ┌───┬───┐
│   │  ─┼──>│   │  ─┼──>│   │  ─┼──>│   │  ─┼──> NIL
└─┼─┴───┘   └─┼─┴───┘   └─┼─┴───┘   └─┼─┴───┘
  │           v           v           v
  │           3           4           5
  │
┌─┼─┬───┐   ┌───┬───┐
│ v │  ─┼──>│   │  ─┼──> NIL
└─┼─┴───┘   └─┼─┴───┘
  v           v
  1           2
```

## 2 Tamanho

Saber o tamanho de uma lista (ou seja, o número de elementos) é bastante util, e _common lisp_ tem uma função para esse fim: _length_.

- (1 2 3 4) -> 4
- (1 2 (3 4) (5 6) 7) -> 5
- ( (1 2 3) ) -> 1

É de notar que apenas os elemntos de _1º nível_ contam, ou seja, se um elemento for uma nova lista, apenas conta como 1.

Uma pergunta que pode surgir destes exemplos é: _"E uma lista com 0 elementos?"_

Essa lista existe. É chamada de _empty list_ e represenada como _()_.

Na realidade já conhecemos esta lista, mas com outro nome: _NIL_.

## 3 Igualdade

Para duas listas serem iguais, _todos_ os seus elementos têm de ser _iguais_, e por consequencia, têm de possuir o _mesmo número de elementos_

- (A B C) ≠ (C B A)
- (A (B C) D) ≠ (A B C D)

## 4 Funções

Existem funções primitivas para manipular listas:

- first -> 1º elemento
- second -> 2º elemento
- third -> 3º elemento
- rest -> tudo o que não seja o 1º elemento

Para ser mais correto, estas funções retornam _apontadores_ para _con cells_, mas para efeitos práticos podemos pensar neles como novas listas

## 5 CAR e CDR

Já sabemos que as _cons cells_ são constituidas por 2 partes. É então expectável que nos seja possível aceder a cada uma delas, e é isso que fazem as funções _CAR_ e _CDR_

### 5.1 CAR

O _CAR_ acede à _primeira parte_ da _cons cell_

```
           ┌─────┐
(1 2 3) ──>│ CAR │──> 1
           └─────┘
```

Como podemos ver, se passarmos uma lista a _CAR_ vamos obter o _first_ da lista (primeiro elemento), uma vez que é para este valor que a 1º parte da 1ª _cons cell_ aponta.

### 5.2 CDR

O _CDR_ acede à _segunda parte_ da _cons cell_

```
           ┌─────┐
(1 2 3) ──>│ CAR │──> (2 3)
           └─────┘
```

Como podemos ver, se passarmos uma lista a _CDR_ vamos obter o _rest_ da lista, uma vez que é para isto que a 2º parte da 1ª _cons cell_ aponta.

### 5.3 NIL

Por definição, temos que:

```
       ┌─────┐
NIL ──>│ CAR │──> NIL
       └─────┘
```

```
       ┌─────┐
NIL ──>│ CDR │──> NIL
       └─────┘
```

### 5.4 Conbinações

E se eu quiser aceder ao _CAR do CDR_, ou o _CAR do CDR do CDR_?

Common Lisp permite-nos expressar qualuqer combinação de _4 A's ou D's_ de modo a usar estas funções compostas. Assim, podemos simplificar muitas destas expressões:

- CAR do CDR do CDR -> CADDR

```
             ┌───────┐
(1 2 3 4) ──>│ CADDR │──> 3
             └───────┘

            ┌───┐  ┌───┐  ┌───┐
(1 2 3 4) ─>│CDR│─>│CDR│─>│CAR│─> 3
            └───┘  └───┘  └───┘
```

- CAR do CDR -> CADR

```
             ┌──────┐
(1 2 3 4) ──>│ CADR │──> 3
             └──────┘

            ┌───┐  ┌───┐
(1 2 3 4) ─>│CDR│─>│CAR│─> 2
            └───┘  └───┘
```

- CDR do CDR do CDR -> CDDDR

```
             ┌───────┐
(1 2 3 4) ──>│ CDDDR │──> 3
             └───────┘

            ┌───┐  ┌───┐  ┌───┐
(1 2 3 4) ─>│CDR│─>│CDR│─>│CDR│─> (4)
            └───┘  └───┘  └───┘
```

É de notar que a forma como as funções são aplicadas é da _direita_ para a _esquerda_

Também podemos ver que existe uma correspondência entre _CAR, CDR e combinações_ com as funções previamente referidas _rest, first, second,..._

| CAR - CDR | Funções correspondentes |
| --------- | ----------------------- |
| CAR       | First                   |
| CDR       | Rest                    |
| CADR      | Second                  |
| CADDR     | Third                   |
| ...       | ...                     |

## 6 Cons

Podemos criar _cons cells_, e para isso usa-mos, surpreendam-se, a função _CONS_

Esta função recebe _2 inputs_ e cria uma nova _cons cell_ cujo _CAR_ é o 1º input e o _CDR_ é o 2º input:

```
    1 ──>┌──────┐
         │ CONS │──> (1 2 3)
(2 3) ──>└──────┘
```

Se pensarmos nisto como cadeias de _cons cells_, temos algo como:

```
┌───┬───┐
│   │  ─┼─┐
└─┼─┴───┘ │
  │       v
  v     ┌───┬───┐   ┌───┬───┐
  1     │   │  ─┼──>│   │  ─┼──> NIL
        └─┼─┴───┘   └─┼─┴───┘
          v           v
          2           3
```

Assim, podemos construir qualquer lista, por mais complexa que seja, através de chamadas encadeadas de _CONS_. No entanto, isto tem um problema: _Trabalho_.

Torna-se cansativo e pouco legível fazer este processo para listas com mais do que 2 ou 3 elementos, e por isso existe a função _LIST_, que recebe argumentos e cria uma lista (cadeia de células) com esses mesmos elementos.

```
    1 ──>┌──────┐
         │      │
    2 ──>│ LIST │──> (1 2 (3 4))
         │      │
(3 4) ──>└──────┘
```
