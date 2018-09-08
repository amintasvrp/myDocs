---
title: "Haskell"
date: 2018-08-21T16:50:59-03:00
author: "Amintas Victor"
type: "post"
---

## Básico
### Operadores Básicos

    + - * / mod sqrt

### Operadores Lógicos
```haskell
&& || not
```
### Operadores Relacionais
```haskell
> < >= <= == /=
```
### Declarando Valores
```haskell
x = a
```
## Funções
### Aplicação
```haskell
f x y == (f x) y == x 'f' y
```
### Expressões Condicionais
```haskell
nomeFuncao param = if cond then resultado1 else resultado2
```
### Equações Guardadas
```haskell
nomeFuncao param | cond = resultado1
                 | otherwise = resultado2
```
### Expressões Case
```haskell
funcao xs = case expression of pattern1 -> result1
                               pattern2 -> result2
```
### Definição local
```haskell
-- relacionamos expressões com variáveis, melhorando visibilidade e escopo locais
-- (where)
funcao xs = ...
  where xs = ...
-- (let)
funcao xs = let <bindings> in <expression>
```
### Composição de Funções
```haskell
f (g xs) == (f . g) xs
```
## Listas
### Definição
```haskell
array = []
array = head:array
-- em funções definimos head:tail
(x:xs)
-- podemos ignorar o head/tail
(_:xs)
(x:_)
-- strings são arrays de caracteres
```
### Operadores
```haskell
-- (cons) define uma lista
:
-- (concatenação)                
++
-- (seleção) indexação
!!
-- comparação a partir do primeiro        
> < >= <= == /=
```
### Funções Básicas
```haskell
-- primeiro elemento
head xs
-- exceto primeiro elemento
tail xs
-- ultimo elemento
last xs
-- exceto ultimo elemento
init xs
-- tamanho
length xs
-- verifica se é vazia
null xs
-- inverte
reverse xs
-- do início até k-ésima posição
take k xs
-- da k-ésima posição até fim
drop k xs
-- maior
maximum xs
-- menor
minimum xs
-- soma dos elementos
sum xs
-- produto dos elementos
product xs
-- verifica se x pertence a xs
elem x xs
```
### Funções para Definição de Listas
```haskell
-- (range) lista de k até m
[k..m]
-- (range) lista de k até m seguindo sequência k,p
[k,p..m]
-- (range) lista infinita
[k..]
-- circulariza infinitamente
cycle xs
-- produzir lista infinita com um elemento
repeat x
-- lista de tamanho k com elementos x   
replicate k x
```
### Outras Funções
```haskell
-- aplicar função f a todos os elementos da lista xs
map f xs
-- lista com elementos que satrisfazem condição
filter cond xs
-- na lista xs, substitui o cons(:) pela função f e a lista vazia pelo valor inicial x
-- associativo à direita (não trabalha com listas infinitas)
foldr f x xs
-- associativo à esquerda
foldl f x xs  
```
### Compreensão de Listas
```haskell
[ x | x <- array, cond]
```
## Tuplas
### Definição
```haskell
(a,b)
```
### Funções
```haskell
-- Primeiro Elemento
fst (a,b) == a
-- Segundo Elemento
snd (a,b) == b
-- junta duas listas em uma lista de pares (índice com índice)
zip xs ys
```

## Tipos de Dados Ordenáveis
### Definição
```haskell
-- podemos definir um tipo ordenável no escopo da função
funcao :: (Ord a)
-- podemos retornar um Ordering
funcao :: Ordering
GT -- maior que
EQ -- igual
LT -- menor que
```
