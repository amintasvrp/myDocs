---
title: "Python 3: Minimalismo e Legibilidade"
date: 2018-06-17T23:53:59-03:00
author: "Amintas Victor"
type: "post"
---

## Introdução a Python

Python é uma linguagem de programação orientada a objetos, dinamicamente tipificada e interpretada. A filosofia de design do Python é baseada em uma sintaxe não-tradicional e minimalista, girando em torno da legibilidade. Isso é feito usando-se espaço em branco para delinear escopos em vez das mais tradicionais chaves e ponto-e-vírgula. Geralmente todo o código python é executado usando um interpretador, sendo o mais popular e original chamado CPython, porque é implementado utilizando C e usa um coletor de lixo automático para gerenciar a memória. Existem vários outros intérpretes, muitos dos quais implementados em Java e C#.

Muitos desenvolvedores optam por escrever Python usando um ambiente de desenvolvimento integrado específico, como o Eclipse, o PyCharm e o NetBeans.

### Versões do Python

Ao entrar em contato com Python pela primeira vez pode ser um pouco confuso porque, ao contrário de muitas outras linguidadens de programação, o Python tem duas versões principais, não compatíveis, que são atualmente amplamente utilizadas.

A versão 2.7.3 do Python é na maior parte, compatível com todas as versões anteriores. Ao refatorar a linguidadem, foi criada Python 3, o qual foi adotado lentamente no início, principalmente pela incompatibilidade. Mas hoje em dia o ecossistema do Python 3 está em grande parte comprometido, tornando o Python 3 a escolha óbvia para novos desenvolvedores que desejam aprender a linguidadem.

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
  nome = input("Enter your nome: ")        
  print("Hello", nome + "!")              

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

## Tuplas

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

## Funções

```python
  def funcao(param1, param2 = valor_default):
       return resultado

  funcao(valor1)
  funcao(valor1, valor2)
```

## Condicionais

```python
a = True
b = False

if a and b:
	# Ações Executadas ao Validar o If
elif a or not(b):
	# Ações Executadas ao Validar o Else If
else:
	# Ações Executadas ao Validar o Else

# Comparações: >, <, >=, <=, !=, ==
if (1 < 3) or ("string1" == "string2"):
	# Execução ao validar condição
```

## Dicionários

```python

# Definindo um dicionário
dicionario = {
    "a" : "b",
    5 : ["a", 3],
    3 : 5
}

# Acessando o Valor, dado uma Chave, em um Dicionário
print( dicionario["a"] )

# Acessando o Valor, dado uma Chave, em um Dicionário. Caso a Chave não Exista,
# um Valor Passado como Parâmetro será Retornado
print( dicionario.get(5, "Chave não consta") )
```

## Iterações (Loops)

```python
# While Loop
indice = 1
while indice <= 5:
	print(indice)
	indice += 1

# For Loop
for indice in range(5):         # range(n) = [0, 1, ..., n-1]
    print(indice)

numeros = [4, 8, 15, 16, 23, 42]
for numero in numeros:
    print(numeros)

for letra in "Palavra":
    print(letra)
```

## Tratamento de Exceções

```python
  try:
      # Comandos a serem Executados
  except ExcecaoPrevista as e:
      # Tratamento de uma Exceção Prevista
      print(e)
  except:
      # Tratamento de uma Exceção Imprevista
      print("HOUVE UM ERRO")       
```

## Classes e Objetos

```python
  # Definindo o Objeto
  class Livro:
      # Construtor do Objeto
      def __init__(self, titulo, autor):
          self.titulo = titulo
          self.titulo = titulo

      # Função Inerente aos Atributos
      def ler_livro(self):
           print("Lendo ", self.titulo, " de ", self.autor)

  # Instanciando Objeto
  book1 = Book("Dracula", "Bram Stocker");

  # Acessando Atributo do Objeto
  print(book1.titulo)
  # Utilizando Função do Objeto
  book1.ler_livro()
```

## Getters e Setters

```python
  class Livro:
      def __init__(self, titulo, autor):
          self.titulo = titulo;
          self.autor = autor

      # Getter
      @property
      def title(self):
          return self._titulo     # Usamos Underscore antes do Atributo para
                                 # indicá-lo como Privado

      # Setter
      @titulo.setter
      def title(self, novo_titulo):
          self._titulo = novo_titulo

      # Setter to Null
      @titulo.deleter
      def titulo(self):
          del self._titulo

      def ler_livro(self):
         print("Lendo ", self.titulo, " de ", self.autor)

  book1 = Book("Dracula", "Bram Stocker");

  print(book1.titulo)
  book1.ler_livro()
```

## Herança

```python

  # Superclasse
  class Chef:

     def __init__(self, nome, idade):
         self.nome = nome
         self.idade = idade

     def cozinhar_frango(self):
         print("Frango Cozinhado")

     def temperar_salada(self):
         print("Salada Temperada")

     def cozinhar_prato_especial(self):
         print("Costeletas de Porco")

  # Subclasse
  class ChefEuropeu(Chef):

     def __init__(self, nome, idade, countryOfOrigin):
         self.countryOfOrigin = countryOfOrigin
         # Reaproveitamos o Construtor da Superclasse
         super().__init__(nome, idade)

     def cozinhar_massa(self):
         print("Macarronada")

     # Sobrescrevendo Função da Superclasse
     def cozinhar_prato_especial(self):
         print("Frango Parma")


  myChef = Chef("Gordon Ramsay", 50)
  myChefEuropeu = ChefEuropeu("Massimo Bottura", 55, "Itália")

  # Instâncias da Subclasse herdam Características da Superclasse
  myChef.cozinhar_frango()  
  myChefEuropeu.cozinhar_frango()

  # Instâncias da Subclasse podem Sobrescrever Características da Superclasse
  myChef.cozinhar_prato_especial()
  myChefEuropeu.cozinhar_prato_especial()
```
