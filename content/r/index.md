---
title: "R: Introdução a Ciência de Dados"
date: 2018-06-17T23:52:30-03:00
author: "Amintas Victor"
type: "post"
---

## Preparando o Ambiente
````bash
  sudo apt update
  sudo apt install r-base r-base-dev
````

O uso da linguagem pode se dar tanto via terminal, ao utilizar o comando ```R```, quanto através da IDE **RStudio**, sendo este último a maneira recomendada.

## Tipos de Dados Básicos e Variáveis

````python
  # Tipos de Dados
  numerico <- 10.5            # Decimal (Padrão)
  inteiro <- as.integer(6)    # is.integer(inteiro) == True
  logico <- False             # ||, &&, !
  string <- paste("a","b")    # "a b"  
  string <- paste0("a","b")   # "ab"

  # Ambas as formas são válidas
  numero1 <- 10
  numero2 = 10

  # Printando Valor da Variável
  numero1
  numero2 - 5
````

## Datas

````python
  Sys.Date() # Date: Manipulação em Dias
  Sys.time() # POSIXct: Manipulação em Segundos

  # Converter String para Data
  as.Date("YYYY-MM-DD")               # Formato Padrão
  as.Date("DD/MM/YYYY", "%d/%m/%y")   # Convertendo o Formato
````
## Operações Básicas

````python
  # +, - , *, /, %
  (3 * 8) + 2 / 5
````

## Criando e Manipulando Vetores
````python
  # Instanciando Vetor
  vetor <- c(1, 2, 3, 4, 5, 6)

  vetor * 2             # Manipulando Vetor como Único Elemento
                        # [2, 4, 6, 8, 10, 12]

  # Acessando Elementos do Vetor
  vetor[i]              # Elemento Indicado pelo Índice (1..n)
  vetor[-i]             # Todos os Elementos, Exceto o Indicado
  vetor[i:j]            # Intervalo Fechado
  vetor[-i:-j]          # Intervalo Aberto

  # Nomeando Elementos
  names(vetor) <- c("nome1",...,"nomen")

  # Repetir Elementos
  rep(elemento,quantidade)
````

## Fator

````python
  # Vetor de Categorias e Níveis sem Repetição
  fator <- factor(vetor)
````

## Tabela

````python
  # Elimina Repetições e Determina Frequências
  fator <- table(vetor)
````

## Matriz

````python
  matriz <- matrix(vetor, ncol=numeroColunas, nrow=numeroLinhas) # Definindo Matriz, Preenchendo em Coluna
  matrizt <- t(matriz)                                           # Matriz Transposta
  matrizi <- solve(matriz)                                       # Matriz Inversa

  # Combinar Matrizes
  matrizl <- rbind(matriz1, matriz2) # Linha
  matrizc <- cbind(matriz1, matriz2) # Coluna

  matriz1 %*% matriz2 # Multiplicação Matricial  
````

## Lista

````python
  lista <- list(valor1,...,valorn) # Definindo uma Sequência de Diferentes Tipos

  # Acessando Elementos do Vetor
  lista[i]              # Retorna uma Lista com Elemento Indicado pelo Índice (1..n)
  lista[[i]]            # Retorna o Elemento Indicado pelo Índice (1..n)

  # Definindo Lista com Elementos Nomeados
  lista <- list(nome1=valor1,...,nomen=valorn)
````

## Data Frames

````python
# Tabela de Dados compostas por Listas de Valores de Igual Tamanho

# Indexação de Elementos
dataFrame[i,j]      # Numeração
dataFrame["a","b"]  # Nomes
dataFrame[i,]       # Linha
dataFrame[,j]       # Coluna

# Tamanho
ncol(dataFrame)  # Total de Linhas
nrow(dataFrame)  # Total de Colunas

head(dataFrame)  # Início do Data Frame
````

## Desenhando Gráficos

````python
  amostra <- c(2, 4, 4, 6, 6, 6, 6, 8, 8, 10) # Elemento x Frequência

  # Gráfico de Barras: Dados Categóricos
  barplot(amostra)

  # Histograma: Dados Intervalares
  hist(amostra)

  # Gráfico Pizza
  pie(amostra)

  # Gráfico de Dispersão
  plot(amostra)

  # Definindo Legenda
  legend("Posição da Legenda", fill=c(cor1,...,corn), legend=c("legenda1",...,"legendan"))

  # Desenhando Linha no Histograma
  abline(v=valor, col="cor", lwd=larguraDaLinha)
````

## Média

````python
  mean(amostra)             
````

## Mediana

````python
  median(amostra)             
````

## Funcão Própria

````python
  funcao <- function(param1, param2, ...) {
    # Código a ser Executado
  }             
````

## Moda

````python
  mode <- function(amostra) {
     amostraSemRep <- unique(amostra)
     amostraSemRep[which.max(tabulate(match(amostra, amostraSemRep)))]
  }           
````

## Distribuição Normal

````python
  shapiro.test(amostra)  # Distribuição não é Normal: p-value < 0.05
                         # Distribuição é Normal: p-value >= 0.05
````

## Sumário

````python
  summary(amostra)  # Resumo das Informações de uma Conjunto de Dados
````

## Boxplot

````python
  boxplot(amostra)  # Gráfico que expõe o Primeiro e o Terceiro Quartis
````

## Salvando como .png

````python
  png(file="/path/da/imagem.png", width=comprimento, height=altura)  # Determinando o Path, o Comprimento e a Altura
                                                                     # da Figura
  dev.off()                                                          # Salvando Modificações na Imagem
````

## Variância

````python
  var(amostra)  # Se a Amostra for Pequena: (Xi - X)**2 / (n - 1)
                # Se a Amostra for Grande: (Xi - X)**2 / n
````

## Desvio Padrão

````python
  sd(amostra)
````

## Manipulando Dados Tabulados

````python
  amostra <- read.table(file="/path/da/amostra.csv") # Criando Data Frame a partir de table
  amostra <- read.csv(file="/path/da/amostra.csv")   # Criando Data Frame a partir do .csv

  amostra$coluna                                     # Acessando coluna do Data Frame
````

## Intervalos de Confiança

````python
  # Obtemos o Intervalo de Confiança através do Teste com a Distribuição t de Student
  t.test(amostra)                     # 90% de Confiança
  t.test(amostra,  conf.level=0.9)
````

## Manipulação do Sistema

````python
# Diretório de Trabalho
getwd()         # Obter
setwd("path")   # Modificar

# Pacotes e Dados do Sistema
search()        # Listar
attach(dados)   # Adicionar
detach(dados)   # Remover
````
