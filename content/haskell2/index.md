---
title: "Lambda Calculus, Tipos de Dados e Módulos em Haskell"
date: 2018-10-09T10:32:36-03:00
draft: false
author: "Amintas Victor"
type: "post"
---

## Lambda Calculus
### Conceito
Possui **semântica** de linguagens de programação. Surgiu na lógica matemática, baseada na Teoria das funções, a qual consiste em manipular funções de forma puramente sintática.

Contribuições:
1. Poder de representação, veículo de estudo de semântica de conceitos de linguagens de programação;
2. Todas linguagens funcionais são vistas como variações do lambda calculus;
3. Semântica denotacional usa conceitos do lambda calculus;
4. Menor linguagem de programação universal existente: Uma regra de definição de função e uma regra de transformação (substituição).

### Sintaxe
````
<expressão> | <variável>                 : identificadores minúsculos
            | <constante>                : objetos pré-definidos
            | (<expressão> <expressão>)  : combinações
            | (\<variável>.<expressão>)  : abstrações
````

### Expressões Lambda em Haskell
````
(\x -> f x) y  ==  f y  
````

### Recursões em Expressões Lambda
Para tal, fazemos uso do **Ponto Fixo**, que é o ponto mapeado para ele mesmo pela função. Nem toda função possui ponto fixo, mas existem funções que podem ter mais de um ponto fixo.

### Combinador de Ponto Fixo em Haskell

#### Implementação

````
fix :: (a -> a) -> a
fix f = f (fix f)                -- lambda lifted

-- alternativamente:

fix' f = let x = f x in x        -- lambda dropped
````

#### Aplicação

````
funcao x = fix funcao'
    where   funcao' <caso base>
            funcao' <caso recursivo>

-- alternativamente:

funcao = \x -> if (<caso base>) then <caso base> else <caso recursivo>  
````

## Tipos de Dados

Provém representação de estruturas comuns da programação. As linguagens possuem tipos básicos, mas é desejável criar suas próprias estruturas de dados.

### Sintaxe

````
data NomeDoTipo tipoParam1 tipoParam 2 = NomeConstrutor tipoParam1 tipoParam 2
````

Múltiplos construtores: lidar com situações particulares de um tipo de dado.

````
data NomeDoTipo tipoParam = Construtor1 | Construtor2 tipoParam
````

### Tipos de Dados Recursivos

````
data List a = Nil | Cons a (List a) deriving (Eq,Show)
data BinaryTree a = NIL | Node a (BinaryTree a) (BinaryTree a) deriving (Eq,Show)
````

### Conjuntos Enumerados

Tipos de Dados com finitos valores possíveis. Um exemplo clássico é o Color:

````
data Color
= Red
| Orange
| Yellow
| Green
| Blue
| Purple
| White
| Black
| Custom Int Int Int -- R G B components
````

### Sinônimos

Criação de novos tipos usando tipos pré-existentes, melhorando legibilidade.

````
type ID = Int
type BadType = Int -> BadType  -- Tipo Infinito
type List3D a = [(a,a,a)]      -- Tipo Parametrizado
````

### Typeclasses

Definem interfaces genéricas com feições comuns (análogo aos serviços). Conceito análogo a Objetos em Programação Orientada a Objetos.

````
-- Caso Geral e Assinaturas
-- Definição minimamente completa
class Servico a where
      metodo :: a -> a -> Int

-- Caso Particular
instance Servico bool where
      metodo True = 1
      metodo False = 0
````

#### Built-in Typeclasses

````
deriving (Eq, Show, Ord, Read, Bounded...)
````

{{< note title="Lembre-se" >}}
Podemos usar typeclasses para adicionar contexto, como no exemplo abaixo:

````
isEquals :: Eq a => a -> a -> bool
````
{{< /note >}}

## Módulos

Usados para particionar ou agrupar sub componentes do sistema, melhorando sua modularidade. São semelhantes a pacotes.

### Exportação

````
module Cards ( Tipo1(),                         -- sem construtores
               Tipo2(Construtor1, Construtor2), -- alguns construtores
               Tipo3(..),                       -- todos os construtores
               funcao
             )
  where

data Tipo1 = ...
data Tipo2 = ...
data Tipo3 = ...
funcao :: ... -> ...
funcao = ...
````

### Importação

#### Importando pacote

````
import NomeModulo                   -- Tudo
import NomeModulo(funcao)           -- Apenas funcao
import NomeModulo hiding (funcao)   -- Tudo exceto funcao
import qualified NomeModulo as m    -- Tudo, mas chamando NomeModulo de m
import NomeModulo.funcao as f       -- Importação Hierárquica
````

#### Utilizando importações

````
NomeModulo.funcao
NomeModulo.Tipo

````
