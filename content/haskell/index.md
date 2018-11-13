---
title: "Haskell I: Introdução ao Paradigma Funcional"
date: 2018-06-17T23:57:59-03:00
author: "Amintas Victor"
type: "post"
---

## Básico
### Operadores Básicos
````
    + - * / mod sqrt
````
### Operadores Lógicos
````
    && || not
````
### Operadores Relacionais
````
    > < >= <= == /=
````
### Declarando Valores
````
    x = a
````
### Comentários
````
    -- linha comentada
    {-
    - bloco comentado  
    -}
````
## Funções
### Aplicação
````
    f x y == (f x) y == x 'f' y
````
### Expressões Condicionais
````
    nomeFuncao param = if cond then resultado1 else resultado2
````
### Equações Guardadas
````
    nomeFuncao param | cond = resultado1
                     | otherwise = resultado2
````
### Expressões Case
````
    funcao xs = case expression of pattern1 -> result1
                               pattern2 -> result2
````
### Definição local
````
    -- relacionamos expressões com variáveis, melhorando visibilidade e escopo locais
    -- (where)
    funcao xs = ...
      where xs = ...
    -- (let)
    funcao xs = let <bindings> in <expression>
````
### Composição de Funções
````
    f (g xs) == (f . g) xs
````
## Listas
### Definição Recursiva
````
    array = []
    array = head:array
````
### Definição Funcional
````
    arrayCompleto = (x:xs)
    arraySemCabeca = (_:xs)
    arraySemCauda = (x:_)
````
{{< note title="Lembre-se" >}}
Strings são arrays de caracteres.
{{< /note >}}

### Operadores
````
    -- (cons) define uma lista
    :
    -- (concatenação)                
    ++
    -- (seleção) indexação
    !!
    -- comparação a partir do primeiro        
    > < >= <= == /=
````
### Funções Básicas
````
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
````
### Funções para Definição de Listas
````
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
````
### Outras Funções
````
    -- aplicar função f a todos os elementos da lista xs
    map f xs
    -- lista com elementos que satrisfazem condição
    filter cond xs
    -- na lista xs, substitui o cons(:) pela função f e a lista vazia pelo valor inicial x
    -- associativo à direita (não trabalha com listas infinitas)
    foldr f x xs
    -- associativo à esquerda
    foldl f x xs  
````
### Compreensão de Listas
````
    [ x | x <- array, cond]
````
## Tuplas
### Definição
````
    (a,b)
````
### Funções
````
    -- primeiro Elemento
    fst (a,b) == a
    -- segundo Elemento
    snd (a,b) == b
    -- junta duas listas em uma lista de pares (índice com índice)
    zip xs ys
````
## Tipos Ordenáveis
### Definição
````
    -- podemos definir um tipo ordenável no escopo da função
    funcao :: (Ord a)
    -- podemos retornar um Ordering
    funcao :: Ordering
    GT -- maior que
    EQ -- igual
    LT -- menor que
````
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

### Classes (Typeclasses)

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

#### Classes Padrão (Built-in Typeclasses)

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

#### Importando pacotes

````
import NomeModulo                   -- Tudo
import NomeModulo(funcao)           -- Apenas funcao
import NomeModulo hiding (funcao)   -- Tudo exceto funcao
import qualified NomeModulo as m    -- Tudo, mas chamando NomeModulo de m
import Pacote.Modulo as m           -- Importação Hierárquica
````

#### Utilizando importações

````
NomeModulo.funcao
NomeModulo.Tipo
````

## Entrada e Saída (IO)

````
-- Main: ação IO com tipo IO(). Todo programa Haskell que precisa fazer IO começa sua execução com essa ação
-- Do: forma conveniente de definir uma sequencia de ações

main :: IO()
main = do
  -- Código IO
````

{{< note title="Lembre-se" >}}
A função **read** pode nos ajudar a converter tipos, o que é bastante útil quando estamos lidando com entrada e saída:
````
read a :: (Read tipo) => tipo
````
{{< /note >}}


Segue adiante o básico que é fornecido pela biblioteca IO ao utilizarmos ``import IO``:

````
data IOMode = ReadMode | WriteMode| AppendMode | ReadWriteMode
type FilePath = String

-- Read
openFile :: FilePath -> IOMode -> IO Handle
hClose :: Handle -> IO ()
hIsEOF :: Handle -> IO Bool
hGetChar :: Handle -> IO Char
hGetLine :: Handle -> IO String
hGetContents :: Handle -> IO String
getChar :: IO Char                                    -- Obter caractere da entrada
getLine :: IO String                                  -- Obter linha da entrada
getContents :: IO String

-- Write
hPutChar :: Handle -> Char -> IO ()
hPutStr :: Handle -> String -> IO ()
hPutStrLn :: Handle -> String -> IO ()
putChar :: Char -> IO ()
putStr :: String -> IO ()                              -- Printar linha
putStrLn :: String -> IO ()                            -- Printar e pular linha
readFile :: FilePath -> IO String
writeFile :: FilePath -> String -> IO ()
````

## Manipulação de Erros
### Pura
````
-- Maybe
data Maybe a = Just a | Nothing deriving (Eq, Ord)

-- Either
data Either a b = Left a | Right b deriving (Eq, Ord, Read, Show)
````

### Exceções
````
-- Retorna um IO() ou a mensagem de uma exceção
try :: Exception e => IO a -> IO (Either e a)

-- Permite realizar uma ação quando acontece exceção
handle :: Exception e => (e -> IO a) -> IO a -> IO a

-- Permite levantar exceções
throwIO :: Exception e => e -> IO a

-- Permite levantar erros
ioError :: IOError -> IO a
````

## Testes

### HUNit

````
-- importando HUnit

import Test.HUnit

-- elementos importantes

data Test = TestCase Assertion 	    -- um caso de teste simples
          | TestList [Test]		      -- uma lista de casos de teste
          | TestLabel String Test		-- um teste indentificado por um label

data Counts = Counts { cases, tried, errors, failures :: Int }  -- contadores de testes
            deriving (Eq, Show, Read)


-- funções baseadas em casos de teste

testCaseCount :: Test -> Int
testCasePaths :: Test -> [Path]

-- funções baseadas em afirmação

assertFailure :: String -> Assertion
assertFailure msg = ioError (userError ("HUnit:" ++ msg))

assertBool :: String -> Bool -> Assertion
assertBool msg b = unless b (assertFailure msg)

assertString :: String -> Assertion
assertString s = unless (null s) (assertFailure s)

assertEqual :: (Eq a, Show a) => String -> a -> a -> Assertion

-- funções baseadas em contadores

runTestText :: PutText st -> Test -> IO (Counts, st)
showCounts :: Counts -> String
showPath :: Path -> String
runTestTT :: Test -> IO Counts  
````

## Concorrência e Paralelismo

Compilando programa para arquiteturas paralelas:
```bash
ghc --make -threaded codigo.hs
```
Execução:

```bash
## sendo x = quantidade de núcleos utilizados
codigo +RTS -Nx
```
Módulos e funções envolvidas:
````
-- importando o módulo de paralelismo
import Control.Parallel

-- funções
par :: a −> b −> b -- avalia argumentos em paralelo. Retorna como resultado o valor do
segundo argumento. par a b = b. escrita as vezes como a ‘par’ b
pseq :: a −> b −> b
````
