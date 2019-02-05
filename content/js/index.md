---
title: "JavaScript: Programando em Web"
date: 2018-06-17T23:56:45-03:00
author: "Amintas Victor"
type: "post"
---

## Introdução

JavaScript é uma linguidadem de programação de alto nível, dinamicamente tipificada e interpretada. Foi criado com o único propósito de tornar os sites mais responsivos e dinâmicos. Como é capaz de responder às interações do usuário e acessar e manipular o modelo de objeto de documento (DOM), permite que os desenvolvedores da Web criem sites mais dinâmicos.

Hoje JavaScript é usado em praticamente todos os sites modernos. Tornou-se uma das três principais tecnologias de desenvolvimento Web ao lado de HTML e CSS. Hoje em dia, existem milhares de estruturas de JavaScript e é usado até mesmo como um idioma do lado do servidor. O JavaScript utiliza um coletor de lixo e sua sintaxe é baseada em C e C ++.

Em muitos casos, o JavaScript será escrito diretamente dentro de um arquivo HTML, mas também pode ser inserido em seu próprio arquivo JavaScript separado e importado para HTML.

## Printando

```javascript

// Adicionando linhas ao HTML
document.write("<h1>Hello World</h1>");
document.write("<hr>");
document.write("<p>This is a javascript tutorial</p>");

// Mostrando pop up
alert("This is an alert");

// Printando no console (F12)
console.log("Logging to the console");

```

## Variáveis e Tipos de Dados

```javascript

/*
Nomes são case-sensitive e devem começar com: letras, $, _
Após, podem incluir: letters, numbers, $, _
Segundo a convenção:
     "Comece com minúscula, e as palavras adicionais são separadas pela primeira letra maiúscula
     ex. minhaPrimeiraVariavel"
*/

var nome = "Amintas";                     // String com aspas duplas
var ocupacao = 'programador';             // String com aspas simples

var idade = 20;                           // Inteiro
var altura = 1.73;                        // Número com ponto flutuante

var ehAlto;                               // Booleano
ehAlto = true;

nome = "John";                            // Mudando valor da variável

document.write("Your nome is " + nome);   // Concatenando valor da variável
                                          // ex: Seu nome é Amintas

```

## Cast e Conversão

```javascript

// Convertendo em um número qualquer
document.write( 100 + Number("25") + "<br>");         // 125

// Convertendo em um inteiro
document.write( 100 + parseInt("50") + "<br>");       // 150

// Convertendo em um número com ponto flutuante
document.write( 100 + parseFloat("50.99") + "<br>");  // 150.99

```

## Strings

```javascript

var cumprimento = "Ola";
//   índices:      012

document.write( cumprimento.length + "<br>" );            // 3
document.write( cumprimento.charAt(0) + "<br>"  );        // O
document.write( cumprimento.iOf("la") + "<br>"  );    // 1
document.write( cumprimento.iOf("z") + "<br>"  );     // -1
document.write( cumprimento.substring(1) + "<br>"  );     // la
document.write( cumprimento.substring(0, 2) + "<br>"  );  // Ol

```

## Números

```javascript

document.write( 2 * 3 + "<br>" );       // Aritimética Básica: +, -, /, *
document.write( 2**3 + "<br>" );        // Exponenciação
document.write( 10 % 3 + "<br>" );      // Resto
document.write( 1 + 2 * 3 + "<br>" );   // Ordem das operações
document.write(10 / 3.0 + "<br>");      // Inteiros e Flutuantes: 3.333333

// Incrementado e decrementando variáveis
var num = 10;

num += 100;                              // +=, -=, /=, *=
document.write(num + "<br>");

num++;                                   // ++ (num += 1), -- (num -= 1)  
document.write(num + "<br>");

// A classe Math tem métodos úteis
document.write( Math.pow(2, 3) + "<br>" );    // Potenciação
document.write( Math.sqrt(144) + "<br>" );    // Raiz quadrada
document.write( Math.round(2.7) + "<br>" );   // Arredondamento

```

## Entrada de Usuário

```javascript

// Pop ups
var nome = window.prompt("Diga seu nome: ");
alert("Olá " + nome);

```

## Acessando HTML

Em **i.html**:

```html

<script src="script.js"></script>
<h1 id="cabecalho" atributo="Valor do Atributo">Título do Site</h1>

```

Em **script.js**:

```javascript

// Obtendo o elemento
var cabecalho = document.getElementById("cabecalho");

// Acessando atributo do elemento
var atributo = cabecalho.getAttribute("atributo");

// Modificando atributo do elemento
cabecalho.style="color:blue; background-color:red;"

// Modificando conteúdo dentro da tag
cabecalho.innerHTML = "Novo Título do Site";

```

## Arrays

```javascript

//Array vazio
array = [];

//       0  1  2   3      4       5
array = [4, 8, 15, 16, "vinte", false];

// Alterando elemento do índice
array[0] = 90;

document.write(array[0] + "<br>");  // 90
document.write(array[1] + "<br>");  // 8
document.write(array.length);       // 6

```

## Arrays Bidimencionais

```javascript

// Definindo matriz: 2 linhas, 2 colunas
matriz = [ [1, 2], [3, 4] ];

// Obtendo elemento: [linha][coluna]
matriz[0][1] = 99;

document.write(numberGrid[0][0] + "<br>");  // 1
document.write(numberGrid[0][1] + "<br>");  // 3

```

## Funções de Arrays

```javascript

// Criando array vazio
amigos = new Array();

// Adiconando ao final do array
amigos.push("Edvaldo");
amigos.push("André");
amigos.push("Daniel");
amigos.push("Thomaz");

// Removendo último elemento
amigos.pop();

document.write( amigos + "<br>" );                    // [Edvaldo, André, Daniel]
document.write( amigos.iOf("André") + "<br>" );   // 1
document.write( amigos.iOf("Z") + "<br>" );       // -1
document.write( amigos.reverse() + "<br>" );          // [Daniel, André, Edvaldo]
document.write( amigos.sort() + "<br>" );             // [André, Daniel, Edvaldo]

```

## Objetos

```javascript

// Criando objeto
var aluno = {
     nome: "Amintas",
     graduacao: "Ciência da Computação",
     idade: 20,
     altura: 1.73
};

// Acessando variável
document.write( student.nome + "<br>" );

// Moficando variável
student.nome = "Thomaz"

```

## Funções

```javascript

// Podemos usar funções antes mesmo de defini-las

var soma = somaNumeros(4, 60);
document.write(soma);

function somaNumeros(num1, num2){
     return num1 + num2;
}

```

## Escutadores de Eventos

### Escutadores Definidos em Linha

Em **i.html**:

```html

<script src="script.js"></script>
<h1 id="cabecalho" onclick="checarClique(this)"> Clique Aqui </h1>

```

Em **script.js**:

```javascript

function handleClick(elemento){
     alert(elemento.id + " clicado");
}

```

### Escutadores Programáticos

Em **i.html**:

```html

<script src="script.js"></script>
<h1 id="cabecalho"> Clique Aqui </h1>

```

Em **script.js**:

```javascript

var cabecalho = document.getElementById("cabecalho");

cabecalho.addEventListener("click", function(){
     alert("Você clicou em " + cabecalho.id);
});

```

Para consultar os eventos do DOM, consulte esta página (em inglês) clicando [aqui](https://www.w3schools.com/jsref/dom_obj_event.asp) !

## Condicionais

```javascript

var ehEstudante = true;
var ehInteligente = false;

// Operadores lógicos: &&, ||, !

if(ehEstudante && ehInteligente){
     document.write("Você é um estudante inteligente");
} else if(ehEstudante && !ehInteligente){
     document.write("Você não é um estudante inteligente");
} else {
     document.write("Você não é um estudante nem inteligente");
}
document.write("<br>");

// Comparadores: >, <, >=, <=, !=, ==, string1.equals(string2)

if(1 > 3){
     document.write("Comparação de números deu verdadeiro");
}

var string = "Amintas";
if(string.equals("Amintas")){
     document.write("Comparação de strings deu verdadeiro");
}

```

## Switch Case

```javascript

var minhaNota = "A";

switch(minhaNota){
     case "A":
          document.write("Aprovado");
          break;
     case "F":
          document.write("Reprovado");
          break;
     default:
          document.write("Nota Inválida");
}

```

## Iterações

### Indefinidas

```javascript

var i = 1;
while(i <= 5){
     document.write(i);
     i++;
}

// 1 2 3 4 5

i = 1;
do{
	document.write(i);
	i++;
}while(i <= 5);

// 1 2 3 4 5 6

```

### Definidas

```javascript

for(var i = 0; i < 5; i++){
     document.write(i);
}

// 0 1 2 3 4

var numeros = [4, 8, 15, 16, 23, 42];
numeros.forEach(function(numero){
     document.write(numero);
});

// 4 8 15 16 23 42

```

## Tratamento de Exceção

```javascript

var num1 = 10;

try{
     var num1 = num2 + 3
}catch(erro){
     // Esse código é executado quando ocorre um erro
     throw "Mensidadem de Erro"
}finally{
     // Esse código é sempre executado
     document.write(num1);
}

```

## Classes e Objetos

```javascript

// Implementando classe com métodos e atributos

class Livro{
     constructor(titulo, autor){
          this.titulo = titulo;
          this.autor = autor;
     }

     lerLivro(){
          document.write("Lendo " + this.titulo + " de " + this.autor);
     }
}

// Criando nova instância

var harryPotter = new Book("Harry Potter", "JK Rowling");

// Acessando atributos do objeto

document.write(harryPotter.titulo + "<br>");

// Chamando método do objeto

book1.lerLivro();

```

## Getters e Setters

```javascript
### Getters and Setters

/*
Implementamos getters e setters apenas quando desejamos que haja algum comportamento antes de acessar/modificar os atributos
*/

class Livro{
     constructor(titulo, autor){
          this.titulo = titulo;
          this.autor = autor;
     }

     get titulo(){
          document.write("Acessando título");
          return this._title;
     }

     set titulo(title){
          document.write("Editando título");
          this._title = title;
     }

     lerLivro(){
          document.write("Lendo " + this.titulo + " de " + this.autor);
     }
}

// A forma de acesso/modificação de atributos é o mesmo independente da implementação de getters e setters

var harryPotter = new Book("Harry Potter", "JK Rowling");
document.write(harryPotter.titulo + "<br>");
book1.lerLivro();

```

## Herança

```javascript

class Chef{

     constructor(nome, idade){
          this.nome = nome;
          this.idade = idade;
     }

     fazerFrango(){
          document.write("Frango");
     }

     fazerSalada(){
          document.write("Salada");
     }

     fazerPratoEspecial(){
          document.write("Prato Especial");
     }
}

class ChefItaliano extends Chef{

     constructor(nome, idade, regiao){
          super(nome, idade);
          this.regiao = regiao;
     }

     // Novo método

     fazerMassa(){
          document.write("Massa");
     }

     // Método sobrescrito

     fazerPratoEspecial(){
          document.write("Lasanha");
     }
}

var chef = new Chef("Gordon", 50);
chef.fazerFrango();                   // Frango


var chefItaliano = new ItalianChef("Bottura", 55, "Sicília");
chefItaliano.fazerFrango();           // Frango
chefItaliano.fazerPratoEspecial();    // Lasanha

```
