---
title: "C++: Programação Imperativa e Orientada a Objetos"
date: 2018-06-17T23:58:59-03:00
author: "Amintas Victor"
type: "post"
---

## Introdução

C++ é uma linguagem de programação orientada a objetos, de tipagem estática, de uso geral. Por vários anos, a linguagem evoluiu até o lançamento oficial em 1985. C++ é essencialmente uma extensão da linguagem de programação C, portanto muitas das coisas que você pode fazer em C você também pode fazer em C++. Ambas são amplamente compatíveis e, em muitos casos, o código C pode ser usado com pouca ou nenhuma modificação como código C++. Mas, além disso, o C++ fornece todo o poder e flexibilidade da orientação a objetos. Então você pode usar chamadas de sistema de baixo nível, gerenciar a memória e lidar com ponteiros, enquanto, ao mesmo tempo, trabalha com classes, objetos, herança e todos os recursos de uma linguagem orientada a objetos.

## Executando Programas em C++

Para todos os programas em C++ deve-se utilizar um compilador cujo trabalho seja compilar o código C++ em código de máquina legível pelo computador. Utilizamos para tal o seguinte comando:

```bash
  gcc -o nome_executavel arquivo.c
```

Tal linguagem depende do usuário para gerenciar a memória do programa, embora existam coletores de lixo disponíveis para C++. Muitos desenvolvedores optam por escrever C ++ usando um editor de texto básico, mas também há ambientes de desenvolvimento integrados mais especializados, alguns dos mais populares incluem **Code Blocks** , **Eclipse** e **NetBeans**.

## Printando

```c++
cout << "Olá ";
cout << "Mundo ";
cout << "!" << endl;
```

## Variáveis e Tipos de Dados

```c++

/*
Nomes são case-sensitive e devem começar com: letters, _
Depois, devem incluir: letters, numbers, _
A convenção diz:
     "Comece com uma palavra começando com letra minúscula, então as palavras adicionais começam
     com letra maiúscula."
     Exemplo: minhaPrimeiraVariavel  
*/
string nome = "Amintas"; // lista de caracteres (não primitivo)
char nota = 'A';         // caractere simples 8 bits

short idade0 = 10;         // inteiro 16 bits com sinal
int idade1 = 20;           // inteiro 16 bits com sinal (maior do que short)
long idade2 = 30;          // inteiro 32 bits com sinal
long long idade3 = 40;     // inteiro 64 bits com sinal
// para torná-los sem sinal, basta adicionar o prefixo "unsigned"

float media0 = 2.5f;       // ponto flutuante de precisão simples
double media1 = 3.5;       // ponto flutuante de precisão dupla
long double media2 = 3.5;  // ponto flutuante de precisão extendida

bool ehAlto;             // 1 bit -> true/false
ehAlto = true;

// podemos printar o valor de variáveis:
cout << "Meu nome é " << nome << endl;
```

## Casting e conversão

```c++
cout <<  (int)3.14 << endl;    // 3
cout << (double)3 / 2 << endl; // 1.5
```

## Ponteiros

```c++
int num = 10;
cout << &num << endl;  // referência de num

int *pNum = &num;
cout << pNum << endl;  // referência de num
cout << *pNum << endl; // 10
```

## Strings

```c++
#include <string>            // importando biblioteca de strings
string palavra = "Olá";
//     índices:   012

cout << palavra.length();              // tamanho da string (5)
cout << palavra[0] << endl;            // char indexado ('')
cout << palavra.find("lá") << endl;    // a partir de qual índice encontramos a substring (1)
cout << palavra.substr(1) << endl;     // substring do índice até o final ("lá")
cout << palavra.substr(0, 1) << endl;  // substring do primeiro índice ao segundo ("Ol")
```

## Números

```c++
cout << 2 * 3 << endl;       // aritmética básica: +, -, /, *
cout << 10 % 3 << endl;      // módulo da divisão inteira
cout << 1 + 2 * 3 << endl;   // ordem das operações: 1 + (2 * 3)
cout << 10 / 3.0 << endl;    // ints operando com doubles = double


int n = 10;
num++;      // += 1
n += 100;   // +=, -=, /=, *=

#import <cmath>              // importando funções matemáticas úteis
cout << pow(2, 3) << endl;   // potenciação
cout << sqrt(144) << endl;   // radiciação quadrada
cout << round(2.7) << endl;  // arredondamento
```

## Entrada do Usuário

```c++
string nome;
cout << "Insira seu nome: ";
cin >> nome;                           // entrada do usuário (string)
cout << "Olá " << nome << endl;

int num1, num2;                        // declarando múltiplas vaŕiáveis com mesmo tipo na mesma linha
cout << "Insira o primeiro número: ";
cin >> num1;                           // conversão implícita (string -> int)  
cout << "Insira o segundo número: ";
cin >> num2;
cout << "Soma: " << num1 + num2 << endl;
```

## Arrays

```c++
int numeros[6];  // array com 6 posições vazias
int numeros[] = {4, 8, 15, 16, 23, 42};
//   índices:    0  1  2   3   4   5

cout << numeros[1] << endl;  // podemos acessar valores através dos índices
numeros[0] = 90;  // podemos editar valores através dos índices -> numeros[] = {90,8,15,16,23,42}   
```

## Arrays Bidimensionais

```c++
int matriz[2][3];  // matriz com 2 linhas e 3 colunas vazias
int matriz[2][3] = { {1, 2, 3}, {4, 5, 6} };
// 1 2 3
// 4 5 6

cout << matriz[0][0] << endl; // podemos acessar valores através dos índices
matriz[0][1] = 99; // podemos editar valores através dos índices -> matriz[2][3] = {{1,90,3},{4,5,6}}
```

## Vetores

```c++
#include <vector>              // importando biblioteca de vetores
vector<string> friends;        // instanciando vetor de strings vazio
friends.push_back("Oscar");    // adicionando ao final
friends.push_back("Angela");

friends.insert(friends.begin() + 1, "Jim"); // inserindo elemento no índice 1

friends.erase(friends.begin() + 1); // excluindo elemento do índice 1

cout << friends.at(1) << endl; // acessando elemento do índice 1

cout << friends.size() << endl; // obtendo tamanho do vector
```

## Funções

```c++

// assinatura do método antes de ser chamado no main
int addNumbers(int num1, int num2);

// main sempre retorna 0 (convenção)
int main()
{
     int sum = addNumbers(4, 60);
     cout << sum << endl;

     return 0;
}

// implementação antes ou depois do main
int addNumbers(int num1, int num2){
     return num1 + num2;
}
```

## Condicionais

```c++
bool a = true;
bool b = false;

// podemos usar and(&&), or(||), ou not(!) nas expressões booleanas
if(a && b){
  // ...
} else if(a || !b){
  // ...
} else {
  // ...
}

// podemos comparar números com >, <, >=, <=, != e == nas expressões booleanas
if(1 > 3){
  // ...
} else if ('a' > 'b'){ // e o mesmo se aplica ao comparar caracteres
  // ...
}

// comparamos strings com o método compare, que retorna 0 se as strings forem iguais
string s = "string";
if(s.compare("string") != 0){
     // ...
}
```

## Switch Case

```c++
char myGrade = 'A';

// dependo do valor da variável, um comportamento é tomado
switch(myGrade){
     case 'A':
          cout << "You Pass" << endl;
          break;
     case 'F':
          cout << "You fail" << endl;
          break;
     default:
          // o caso default funciona como um else
          cout << "Invalid grade" << endl;
}
```

## Loop Indefinido

```c++
int index = 1;

// não sabemos quantas iterações serão realizadas
// enquanto a condição for verdadeira, o comando é repitido
while (index <= 5) {
     cout << index << endl;
     index++;
}

// realiza o comando ao menos uma vez, verificando a condição depois
do{
     cout << index << endl;
     index++;
} while (index <= 5);
```

## Loop Definido

```c++
// sabemos quantas iterações serão realizadas
for(int i = 0; i < 5; i++){
     cout << i << endl;
}
```

## Tratamento de Exceções

```c++
double division(int a, int b) {
   if( b == 0 ) {
   	  // ao lançar a exceção, a mensagem que passamos como parâmetro é mostrada
      throw "Division by zero error!";
   }
   return (a/b);
}

int main(){
     try {
        division(10, 0);
     } catch (const char* msg) {
      cerr << msg << endl;
     }
     return 0;
}
```

## Classes e Objetos

```c++
// criando uma classe, definindo um objeto
class Book{
     public:
     	  // definindo atributos inerentes
          string title;
          string author;

          // definindo métodos inerentes
          // quando nos referimos aos atributos, usamos: this->atributo
          void readBook(){
               cout << "Reading " + this->title + " by " + this->author << endl;
          }
};

// podemos ter várias instâncias de um mesmo objeto
Book book1;
book1.title = "Harry Potter";
book1.author = "JK Rowling";

Book book2;
book2.title = "Lord of the Rings";
book2.author = "JRR Tolkien";

// usamos os métodos de forma independente
book2.readBook();
cout << book2.title << endl;
```

## Construtores

```c++
class Book{
     public:
          string title;
          string author;

          // usamos construtores para criar instâncias de forma elegante
          Book(string title, string author){
               this->title = title;
               this->author = author;
          }

          void readBook(){
               cout << "Reading " + this->title + " by " + this->author << endl;
          }
};

// criamos assim instâncias de forma muito mais legível e enxulta, garantindo bom design
Book book1("Harry Potter", "JK Rowling");
cout << book1.title << endl;

Book book2("Lord of the Rings", "JRR Tolkien");
cout << book2.title << endl;
```

## Getters e Setters

```c++
class Book{
     private:
          string title;
          string author;
     public:
          Book(string title, string author){
               this->setTitle(title);
               this->setAuthor(author);
          }

          // para acessar os atributos de um objeto, usamos métodos getters
          // para alterar os atributos de um objeto, usamos métodos setters

          string getTitle(){
               return this->title;
          }
          void setTitle(string title){
               this->title = title;
          }
          string getAuthor(){
               return this->author;
          }
          void setAuthor(string author){
               this->author = author;
          }

          void readBook(){
               cout << "Reading " + this->title + " by " + this->author << endl;
          }
};

Book book1("Harry Potter", "JK Rowling");
cout << book1.getTitle() << endl;

Book book2("Lord of the Rings", "JRR Tolkien");
book2.setTitle("LOTR: The Fellowship of the Ring");
```

## Herança

```c++
class Chef{
     public:

          string name;
          int age;

          Chef(string name, int age){
               this->name = name;
               this->age = age;
          }

          void makeChicken(){
               cout << "The chef makes chicken" << endl;
          }

          void makeSalad(){
               cout << "The chef makes salad" << endl;
          }

          void makeSpecialDish(){
               cout << "The chef makes a special dish" << endl;
          }
};

// com herança, podemos criar objetos que herdam atributos e/ou métodos de outro
// sendo estes mais específicos

class EuropeanChef : public Chef{
     public:

          string countryOfOrigin;

          // ao herdar atributos, estes são reaproveitados em construtores novos
          // a partir dos construtores da superclasse
          EuropeanChef(string name, int age, string countryOfOrigin) : Chef(name, age){
               this->countryOfOrigin = countryOfOrigin;
          }

          // da mesma forma, novos atributos e métodos podem ser criados
          void makePasta(){
               cout << "The chef makes pasta" << endl;
          }

          // assim como métodos podem ser sobrescritos (override)
          void makeSpecialDish(){
               cout << "The chef makes chicken parm" << endl;
          }
};

Chef myChef("Gordon Ramsay", 50);
myChef.makeChicken();

EuropeanChef myItalianChef("Massimo Bottura", 55, "Italy");
myItalianChef.makeChicken();
cout << myItalianChef.age << endl;
```

## Classes e Métodos Abstratos

```c++
// com a palavra-chave "virtual", criamos classes abstratas, ou seja, que não podem ser instanciadas
virtual class Vehicle{
     public:
     	  // determinamos a assinatura de um método a ser instanciado com "virtual"
          virtual void move() = 0;
          void getDescription(){
               cout << "Vehicles are used for transportation" << endl;
          }
};

class Plane : public Vehicle{
     public:
     	  // implementamos o método cuja assinatura foi herdada
          void move(){
               cout << "The plane flys through the sky" << endl;
          }
};

Plane myPlane;
myPlane.move();  // usamos o método implementado por Plane
```
