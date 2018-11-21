---
title: "Python 3"
date: 2018-06-17T23:53:59-03:00
author: "Amintas Victor"
type: "post"
---

## Introdução a Python

Python é uma linguagem de programação orientada a objetos, dinamicamente tipificada e interpretada. A filosofia de design do Python é baseada em uma sintaxe não-tradicional e minimalista, girando em torno da legibilidade. Isso é feito usando-se espaço em branco para delinear escopos em vez das mais tradicionais chaves e ponto-e-vírgula. Geralmente todo o código python é executado usando um interpretador, sendo o mais popular e original chamado CPython, porque é implementado utilizando C e usa um coletor de lixo automático para gerenciar a memória. Existem vários outros intérpretes, muitos dos quais implementados em Java e C#.

Muitos desenvolvedores optam por escrever Python usando um ambiente de desenvolvimento integrado específico, como o Eclipse, o PyCharm e o NetBeans.

### Versões do Python

Ao entrar em contato com Python pela primeira vez pode ser um pouco confuso porque, ao contrário de muitas outras linguagens de programação, o Python tem duas versões principais, não compatíveis, que são atualmente amplamente utilizadas.

A versão 2.7.3 do Python é na maior parte, compatível com todas as versões anteriores. Ao refatorar a linguagem, foi criada Python 3, o qual foi adotado lentamente no início, principalmente pela incompatibilidade. Mas hoje em dia o ecossistema do Python 3 está em grande parte comprometido, tornando o Python 3 a escolha óbvia para novos desenvolvedores que desejam aprender a linguagem.

## Printando

```python
  print("Hello")
  print("World")      
  print("!")
```

## Variáveis e Tipos de Dados

```python
  # Nomes são case-sensitive e devem começar com: letras, $, _
  # Depois, devem incluir: letras, números, $, _
  # Segundo a conveção:
  #  "Comece com uma letra minúscula, e as palavras seguintes são separadas por underscores"
  # Exemplo: minha_primeira_variavel

  nome = "Mike"    # String
  idade = 30       # Inteiro
  peso = 3.5       # Decimal
  eh_alto = True   # Boolean (True/False)
```

## Casting e Conversão

```python
  print( int(3.14) )                 # 3
  print( float(3) )                  # 3.0
  print( str(True) )                 # "True"
  print( int("50") + float("70") )   # 120.0
```

## Strings

```python
  palavra = "String"
  # índices: 012345

  print( len(palavra) )         # 6
  print( palavra[0] )           # S
  print( palavra[-1] )          # g

  # A partir de qual índice encontramos uma substring
  print( palavra.find("ing") )  # 3
  print( palavra.find("z") )    # -1

  # Obter uma substring
  print( palavra[3:] )         # "ing"
  print( palavra[1:4] )        # "tri"
```

## Números

```python
  print( 2 * 3 )       # Aritmética Básica: +, -, /, %, *, **
  print( 2**3 )       
  print( 10 % 3 )      
  print( 1 + 2 * 3 )   # Precedência das operações é avaliada
  print(10 / 3.0)      # Inteiro (Operação) Decimal = Decimal


  num = 10
  num += 100           # Atualização de Variável: +=, -=, /=, *=

  ++num                # num += 1
  --num                # num -= 1

  # Módulo Matemático
  import math
  print( pow(2, 3) )       # Potenciação
  print( math.sqrt(144) )  # Raiz Quadrada
  print( round(2.7) )      # Arredondamento
```
## Entrada do Usuário

```python
  # Entrada Recebida como String
  name = input("Enter your name: ")        
  print("Hello", name + "!")              

  # Entrada Convertida para Inteiro/Decimal
  num1 = int(input("Enter First Num: "))
  num2 = float(input("Enter Second Num: "))
  print(num1 + num2)
```

## Listas

```python
  lista_numeros = [2, 4, "six", 8.0, 10, 12]  # Listas, em Python, são Heterogêneas
  #  Índices:      0  1    2     3   4   5

  lista_numeros[0] = 100     # Alterando Valor Contido na Lista
  print(lista_numeros[0])    # Acessando Valor Contido na Lista: 100
  print(lista_numeros[-1])   # Acessando Valor Contido na Lista: 12
  print(lista_numeros[2:])   # Obtendo Sublista: ["six", 8.0, 10, 12]
  print(lista_numeros[2:4])  # Obtendo Sublista: ["six", 8.0]
  print(len(lista_numeros))  # Obtendo Tamanho da Lista
```

## Listas Bidimensionais

```python
  matriz = [ [1, 2], [3, 4] ]  # Definindo uma Lista Bidimensional
  print(matriz[0][1])          # Acessando Valor Contido na Lista[Linha][Coluna]: 2
  matriz[0][1] = 100           # Alterando Valor Contido na Lista
```

## Funções de Listas

```python
  friends = []

  friends.append("Oscar")            # Adicionando Elementos ao Final da Lista
  friends.append("Angela")

  friends.insert(1, "Kevin")         # Inserindo Elemento em uma Determinado Índice
  friends.remove("Kevin")            # Removendo a Primeira Ocorrência de um Elemento
  print( friends.index("Oscar") )    # Obtendo o Índice de um Determinado Elemento
  print( friends.count("Angela") )   # Obtendo Quantidade de Ocorrências de um Determinado Elemento
  friends.sort()                     # Ordenando a Lista
  friends.clear()                    # Esvaziando a Lista
```

## tupla_numeross

```python
  tupla_numeros = (2, 4, "six", 8.0, 10, 12)
  # Índices:       0  1    2     3   4   5

  tupla_numeros[0] = 100     # Alterando Valor Contido na Tupla      
  print(tupla_numeros[0])    # Acessando Valor Contido na Tupla: 100
  print(tupla_numeros[-1])   # Acessando Valor Contido na Tupla: 12
  print(tupla_numeros[2:])   # Obtendo Subtupla: ("six", 8.0, 10, 12)
  print(tupla_numeros[2:4])  # Obtendo Subtupla: ("six", 8.0)
  print(len(tupla_numeros))  # Obtendo Tamanho da Tupla
```
