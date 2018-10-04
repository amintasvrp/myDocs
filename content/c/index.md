---
title: "C: Programação Imperativa em Baixo Nível"
date: 2018-08-21T16:50:59-03:00
author: "Amintas Victor"
type: "post"
---

## Introdução

C é uma linguagem de programação imperativa de propósito geral, com tipagem estática. Além disso, é uma linguagem de baixo nível, o que significa que fornece construções que mapeiam de forma eficiente para as instruções típicas da máquina. Basicamente, é uma maneira mais fácil de escrever programas de baixo nível. Em vez de escrever código de baixo nível em uma linguagem de montagem, você pode abstrair muito e escrever programas equivalentes em C.

Por ser um nível tão baixo, muitos kernels de sistemas operacionais e até mesmo outras linguagens de programação são implementadas, pelo menos em parte, usando o C. Além disso, muitas linguagens de programação modernas atualmente usam a sintaxe e as melhores práticas de C.

## Executando Programas em C

Precisamos compilar o código C em código de máquina legível pelo computador para executar um programa escrito nesta linguagem.

```bash
  gcc -o nome_executavel arquivo.cpp
```
Muitos desenvolvedores optam por escrever C usando um editor de texto básico, mas também há ambientes de desenvolvimento integrados mais especializados, alguns dos mais populares incluem **Code Blocks** , **Eclipse** e **NetBeans**.

## Main e Bibliotecas

Cada programa deve conter uma função principal que será o ponto de partida da execução.
```c
  int main(){
   //seu código aqui
   return 0;
  }
```

Para fazer uso das funções das bibliotecas, é necessário usar ```#include``` no cabeçalho do programa com esta sintaxe:

```c
  #include <libname>
```

Bibliotecas mais utilizadas:

1. ```stdio.h```: permite entrada e saída de valores;
2. ```stdlib.h```: Conjunto de funções para conversão numérica, geração de números pseudo-aleatórios, alocação de memória, funções de controle de processos e outras finalidades;
3. ```math.h```: Conjunto de matemática comum.


## Printando

```c
  printf("Olá\n");
  printf("Mundo");
  printf("!\n");
```

Nós podemos usar ```\n``` para quebrar a linha.

## Variáveis ​​e Tipos de Dados
Os nomes diferenciam maiúsculas de minúsculas e podem começar com: letras ou sublinhado. Depois, pode incluir letras, números e sublinhados.
A convenção diz: *Comece com uma palavra minúscula, então palavras adicionais são capitalizadas. Se é uma constante, usamos palavras maiúsculas separadas por sublinhado*.

```c
  char testGrade = 'A';    // único caractere de 8 bits.
  char name[] = "Amintas"; // array de caracteres (string)

  // você pode torná-los sem-sinal adicionando prefixo "unsigned"
  short age0 = 10;         // um inteiro de pelo menos 16 bits
  int age1 = 20;           // um inteiro de pelo menos 16 bits (não melnor que short)
  long age2 = 30;          // um inteiro de pelo menos 32 bits
  long long age3 = 40;     // um inteiro de pelo menos 64 bits

  float gpa0 = 2.5;       // ponto flutuante de precisão simples
  double gpa1 = 3.5;       // ponto flutuante de precisão dupla
  long double gpa2 = 3.5;  // ponto flutuante de precisão estendida

  int isTall;             // 0 se falso, diferente de zero se verdadeiro
  isTall = 1;

  const is IS_TALLER = 1; // podemos usar constantes com o prefixo "const"


  // você pode formatar a saída dessa maneira
  testGrade = 'F';
  printf ("% s, sua nota é% c \ n", name, testGrade);
  / *
  %c caractere
  %d número inteiro (base 10)
  %e número exponencial de ponto flutuante
  %f número de ponto flutuante
  %i inteiro (base 10)
  %o número octal (base 8)
  %s uma sequência de caracteres
  %u número decimal (inteiro) sem sinal
  %x numero em hexadecimal (base 16)
  %% imprime um sinal de porcentagem
  \% imprime um sinal de porcentagem
  * /
```

## Casting and Conversão

Realizamos casting e conversões usando a seguinte sintaxe:

```c
  printf("%d \n", (int)3.14);  // 3
  printf("%f \n", (double)3 / 2); // 1.0
```

## Ponteiros

Podemos manipular os ponteiros usando a seguinte sintaxe:

```c
  int num = 10;
  printf("%p \n", &num); // valor do num (10)

  int *pNum = &num; // armazenando o ponteiro
  printf("%p \n", pNum); // valor do num (10)
  printf("%d \n", *pNum); // endereço do num
```

## Números

Podemos manipular os números usando a seguinte sintaxe:

```c
  printf("%d \n", 2 * 3);       // Aritimética Básica: +, -, /, %, *
  printf("%d \n", 10 % 3);      
  printf("%d \n", (1 + 2) * 3);   // ordem das operações
  printf("%f \n", 10 / 3.0);    // ints e doubles


  int num = 10;
  num += 100;                   // +=, -=, /=, *=
  printf("%d \n",num);

  num++;                       // ++, --
  printf("%d \n", num);

  printf("%f \n", pow(2, 3));  // potência
  printf("%f \n", sqrt(144));  // raiz quadrada
  printf("%f \n", round(2.7)); // número arredondado
```

## Entrada do Usuário

Podemos obter e manipular a entrada do usuário usando a seguinte sintaxe:

```c
  // obtendo um array de char (String)
  char name[10];
  printf("Enter your name: ");
  fgets(name, 10, stdin);
  printf("Hello %s! \n", name);

  // obtendo um inteiro
  int age;
  printf("Enter your age: ");
  scanf("%d", &age);
  printf("You are %d \n", age);

  // obtendo um único char
  char grade;
  printf("Enter your grade: ");
  scanf("%c", &grade);
  printf("You got an %c on the test \n", grade);

  // recebendo um double
  double gpa;
  printf("Enter your gpa: ");
  scanf("%lf", &gpa);
  printf("Your gpa is %f \n", gpa);
```

## Vetores (Arrays) e Matrizes

Podemos instanciar e manipular matrizes e matrizes usando a seguinte sintaxe:
```c
  int luckyNumbers[6];                          // podemos definir o tamanho do array anteriormente
  int luckyNumbers[] = {4, 8, 15, 16, 23, 42};  // podemos definir o tamanho do array dinamicamente
  //        indexes:    0  1  2   3   4   5
  luckyNumbers[0] = 90;
  printf("%d \n", luckyNumbers[0]);             // podemos definir os elementos de um array
  printf("%d \n", luckyNumbers[1]);

  int  numberGrid[2][3];                        // podemos definir uma matriz similarmente
  int numberGrid[2][3] = { {1, 2, 3}, {4, 5, 6} };
  numberGrid[0][1] = 99;

  printf("%d \n", numberGrid[0][0]);
  printf("%d \n", numberGrid[0][1]);
```

## Funções

Nós usamos funções desta maneira:

```c
  int addNumbers(int num1, int num2);   // precisamos declarar funções antes do main

  int main(){
       int sum = addNumbers(4, 60);
       printf("%d \n", sum);

       return 0;
  }

  int addNumbers(int num1, int num2){  // depois do main, podemos implementar funções declaradas
       return num1 + num2;
  }
```

## Condicionais

```c
  int isStudent = 0;
  int isSmart = 0;

  // if then else
  if(isStudent != 0 && isSmart != 0){
       printf("You are a student\n");
  } else if(isStudent != 0 && isSmart == 0){
       printf("You are not a smart student\n");
  } else {
       printf("You are not a student and not smart\n");
  }

  // podemos fazer comparações:>, <,> =, <=,! =, ==
  if(1 > 3){
       printf("number omparison was true\n");
  }
  if('a' > 'b'){
       printf("character comparison was true\n");
  }


  char myGrade = 'A';

  // switch case
  switch(myGrade){
       case 'A':
            printf("You Pass\n");
            break;
       case 'F':
            printf("You fail\n");
            break;
       default:
            printf("Invalid grade\n");
  }
```

## Iterações (Loops)

Podemos iterar desta maneira:
```c
  // while loop
  int index = 1;
  while(index <= 5){
       printf("%d \n", index);
       index++;
  }

  // do-while loop
  index = 1;
  do{
       printf("%d \n", index);
       index++;
  }while(index <= 5);

  // for loop
  for(int i = 0; i < 5; i++){
       printf("%d \n", i);
  }
```

## Estruturas (Structs)

As estruturas são como objetos no Paradigma OO. Podemos usá-lo desta maneira:
```c
  // definindo struct
  struct Book{
       char title[100];
       char author[100];
  }

  // instanciando e manipulando struct
  int main(){

        struct Book book1;
        book1.numPages = 600;
        strcpy( book1.title, "Harry Potter" );
        strcpy( book1.author, "JK Rowling");

        printf("%s \n", book1.title);

        return 0;
  }
```

## Escrevendo e Lendo Arquivos

Podemos manipular arquivos externos desta maneira:
```c
  char line[255];

  // se o arquivo não existir, um novo arquivo será criado
  FILE * filePointer = fopen("PATH/file.txt", "w"); // criando/escrevendo/sobrescrevendo um arquivo
  FILE * filePointer = fopen("PATH/file.txt", "a"); // acrescentando conteúdo em um arquivo

  // podemos escrever, sobrescrever ou anexar conteúdo com este comando
  fprint(fpointer, "content");

  // podemos ler uma linha de um arquivo, uma linha por chamada
  fgets(line, 255, fpointer);

  // depois de usar um arquivo, precisamos fechar o ponteiro
  fclose(fpointer);
```
