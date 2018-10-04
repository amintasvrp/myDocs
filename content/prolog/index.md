---
title: "Prolog e o Paradigma Lógico"
date: 2018-08-06
author: "Amintas Victor"
type: "post"
---

Mesmo diferentes paradigmas como Funcional e Imperativo têm algo em comum: ambos realizam mapeamento, isto é, lêem entradas e geram saídas. No entanto, um programa de acordo com o paradigma lógico **implementa relacionamentos**, que são mais gerais do que os mapeamentos. Em outras palavras, quando se trata de programação lógica, o nível é superior ao da programação imperativa ou funcional.

## Paradigma Lógico

Definimos as relações da seguinte forma:

>Considerando dois conjuntos S e T, dizemos que existe uma relação r entre S e T se, para cada x em S e y em T, a avaliação r(x, y) é verdadeira ou falsa.

Tendo implementado a relação r, podemos fazer consultas como:


* Dado x e y, determine se r(x, y) é verdadeiro;
* Dado x, encontre todo y onde r(x, y) é verdadeiro, e vice-versa;
* Encontre todos os x e y onde r(x, y) é verdadeiro.

Linguagens de programação lógicas são restritas a **Cláusulas de Horn**, que possuem o seguinte formato: **A0 se A1 e ... e An**, onde **Ai** é uma afirmação do formulário **Ri(...)**, com **Ri** sendo o nome de um relacionamento. Se **A1, ..., An** forem verdadeiras, inferimos que **A0** também é verdadeiro, caso contrário, falso. Se a cláusula for igual a **A0**, é considerado um **fato**.

O Paradigma Lógico faz parte da subcategoria "Paradigma Declarativo", preocupada com fatos e não com procedimentos, de modo que o conhecimento sobre o problema é descrito usando a lógica simbólica.

O formalismo lógico-computacional é baseado em três princípios:


* Uso de linguagem formal para representação do conhecimento;

> Uma linguagem formal é precisa, pois tem sentenças com sintaxe e semântica bem definidas, embora seja menos expressiva em comparação com a linguagem natural.

* Uso de regras de inferência para manipular conhecimento;

> Uma regra de inferência é um padrão de manipulação sintática que permite criar novas fórmulas a partir de fórmulas existentes e simular formas de raciocínio válidas.

* Uso de uma estratégia de busca para controlar inferências.

> Um agente pode ter uma enorme quantidade de conhecimento armazenado. Normalmente, ele precisa usar apenas parte dele para resolver um problema. Nesse sentido, a estratégia de busca serve para decidir qual parte do conhecimento armazenado deve ser explorada em busca da solução.

O programador deve se preocupar em descrever o problema a ser resolvido (especificação), deixando a máquina para procurar a solução.

## Prolog

Geralmente associado ao contexto de IA ou linguística ou ambos, tem suas raízes na lógica de primeira ordem. Como vantagem, permite representar o conhecimento que um agente tem sobre seu mundo em um nível simples, direto e alto.

## Cláusulas de Horn

```
    B :- A1, A2, ..., An.  % B = A1 and A2 and ... An
    B :- A1; A2; ...; An.  % B = A1 or A2 or ... An
    B :- A1 -> A2 ; A3.    % B = if A1 then A2 else A3
```

## Unificação

Ao responder a uma consulta, o interpretador de Prolog pode precisar atribuir valores às variáveis. Unificação é o mecanismo usado para determinar se existe uma maneira de instanciar as variáveis de dois predicados para torná-los iguais. Dois termos podem ser unificados se:

* Ambos são constantes;
* Um dos termos é uma variável;
* Ambos são termos complexos com o mesmo nome e número de argumentos.

## Listas

As listas consistem em uma estrutura que representa uma sequência de elementos de qualquer tamanho. Uma lista é definida recursivamente da seguinte maneira:

```
    []    % lista vazia
    [h|t] % lista com cabeça e cauda                                           
```

Nessa linguagem, as listas são heterogêneas, ou seja, podem conter valores de diferentes tipos. Podemos até comparar valores de diferentes tipos usando a relação "=", mas o resultado será falso.

Para ver exemplos de implementações, [clique aqui] (https://github.com/amintasvrp/Dirlididi_PLP/tree/master/questoesProlog). Para saber mais sobre o projeto _Prolog Story: Colosseum of Champions_, que consiste em um jogo de batalha de personagens da Marvel, implementado no Prolog, [clique aqui] (https://github.com/amintasvrp/A_Prolog_Story_CoC).
