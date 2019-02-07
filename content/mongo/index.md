---
title: "MongoDB e os Bancos de Dados Não Relacionais (noSQL)"
date: 2018-06-17T23:55:15-03:00
author: "Amintas Victor"
type: "post"
---

## Instalação

Primeiramente, baixamos o MongoDB:

```bash

sudo apt update
sudo apt install -y mongodb
mongo --version

```

Depois, baixamos o MongoDB Compass na versão Community Edition Stable clicando [aqui](https://www.mongodb.com/download-center/compass?jmp=hero).

## Configurando o MongoDB

Vamos criar na raiz o diretório /data/db e rodar o servidor com o comando a seguir:

```bash

mongod

```
Podemos criar diretórios em outros lugares e rodar o servidor neles, basta utilizar o comando abaixo:

```bash

mongod --dbpath /path/diretorio

```

Para nos conectarmos ao servidor, vamos utilizar (em outro terminal) o comando abaixo. A porta por padrão é 27017, mas devemos conferir no terminal em que está rodando o servidor.

```bash

mongo --host localhost:porta

```

Dessa forma, nos deparamos com o terminal de uso do Mongo BD, que suporta a linguagem BSON.

## Criando Banco de Dados

Criamos o análogo ao esquema em SQL:

```bash

use nome_do_banco

```

Assim que o BD é criado, somos mandados para ele.

## Criando Coleções

Criamos o análogo às tabelas em SQL:

```javascript

db.createCollection("nome_da_colecao")

```

Nós nos referimos a coleção como nome_do_banco.nome_da_colecao .

## Deletando Coleções

```javascript

db.nome_da_colecao.drop()

```

## Inserindo Documentos

```javascript

// Tipos de dados
// Dados são sempre armazenados como objetos

{
     string: "String of text",
     inteiro: 405,
     double: 3.565,
     booleano: true,
     array: [1, 2, 3],
     objeto: {atr1: "atr1", atr2: "atr2"},
     data: new Date("<YYYY-mm-dd>"),
     id_objeto: <IdObjeto>,
     sem_valor: null
}

/*
Outros Tipos de dados
---------------------
Timestamp
Binary data
Regular expressions
JS Code
*/

// Inserindo um objeto
db.students.insertOne({name: "Jack", major: "Biology", gpa: 3.5})

// Insreindo um objeto com id detreminado
db.students.insertOne({_id: 4, name: "John", major: "Biology", gpa: 3.2})

// Inserindo um objeto com um atributo a mais
db.students.insertOne({name: "Claire", major: "Marketing", gpa: 3.7, awards: ["Valedictorian", "Summa Cum Laude"]} )

// Inserindo mais de um objeto
db.students.insertMany([
     {name: "Mike", major: "Computer Science", gpa: 2.7},
     {name: "Andrea", major: "Math", gpa: 4.0, awards: ["Summa Cum Laude"]}
])

```

## Buscando Documentos

```javascript

// Obtendo todos os estudantes
db.students.find( {} )

// Obtendo todos os estudantes ignorando o id
db.students.find( {} , {_id: 0})

// Obtendo os primeiros 3 estudantes
db.stuents.find( {} ).limit(3)

// Obter todos os estudantes ordenados pelo nome
db.students.find( {} ).sort( {name: 1} )

// Obter todos os estudantes inversamente ordenados pelo gpa, e depois ordenados pelo nome
db.students.find( {} ).sort( {gpa: -1, name: 1} )

// Obter os estudantes graduados em Biologia
db.students.find( {major: "Biology"} )

// Obter os estudantes com nome Jack e graduação em Biologia
db.students.find( {name: "Jack", major: "Biology"} )

// Obter os estudantes com o objeto contato gujo número é 333-3333 e o email é student@school.edu
db.students.find( {contact: {phone: "333-3333", email: "student@school.edu"} } )

// Obter todos os estudantes com nome Jack ou graduação em Química
db.students.find( { $or: [ {name: "Jack"}, {major: "Chemistry"} ] } )

// Obter todos os estudantes com gpa maior do que 7.5
// $eq, $ne, $lt, $lte, $gt, $gte
db.students.find( {gpa: {$gt: 7.5} } )

// Obter os estudantes com o nome contido no array
// $in, $nin
db.students.find( {name: {$in: ["Kate", "Claire"]} } )   

// Obter os estudantes que possuem o atributo awards
db.students.find( {awards: {$exists: true} } )

// Obter os estudantes cujo nome é uma string
// Lista de Tipos e $types - https://docs.mongodb.com/manual/reference/bson-types/
db.students.find({name: {$type: 2} })

// Obter os estudantes em que o documento de índice 0 no array Notas é igual a 90
db.students.find( {"grades.0": 90 } )

// Obter os estudantes que possuem no array Notas o elemento 80
db.students.find( {grades: {$elemMatch: 80 } } )

// Obter os estudantes que possuem no array Notas um elemento maior do que 80
db.students.find( {grades: {$elemMatch: { $gt: 80} } } )

// Obter os estudantes que possuem um array Notas de tamanho 4
db.students.find( {grades: {$size: 4 } } )

```

## Atualizando Documentos

```javascript

// Mesmos filtros da inserção
db.stuents.metodoAtualizar(filtro, atualização, opções)

// Atualizar um atributo do primeiro documento
db.students.updateOne(
     {major: "Biology"},
     {
       $set:
          {major: "Bio"}
     }
)

// Atualizar um atributo de todos os documentos
db.students.updateMany(
     {major: "Bio"},
     {
       $set:
          {major: "Biology"}
     }
)

// Atualizar todo o primeiro documento
db.students.replaceOne(
     {major: "Bio"},
     {name: "new name", major: "new major", gpa: 4.0}
)

// Atualizar todos os documentos por inteiro
db.students.replaceMany(
     {major: "Bio"},
     {name: "new name", major: "new major", gpa: 4.0}
)

```

## Deletando Documentos

```javascript

// Deletar todos os documentos do banco
db.students.deleteMany({})

// Deletar apenas o primeiro documento
db.students.deleteOne({major: "Biology"})

// Deletar os documentos
db.students.deleteMany({gpa: {$gte: 3.5}})

```

## Ações em Massa

```javascript

db.students.bulkWrite(
      [
         { insertOne : // Inserindo um elemento
            {
               "document" :
               {
                  name: "Andrew", major: "Architecture", gpa: 3.2
               }
            }
         },
         { insertOne :
            {
               "document" :
               {
                  name: "Terry", major: "Math", gpa: 3.8
               }
            }
         },
         { updateOne : // Atualizando um elemento
            {
               filter : { name : "Terry" },
               update : { $set : { gpa : 4.0 } }
            }
         },
         { deleteOne : // Deletando um elemento
            { filter : { name : "Kate"} }
         },
         { replaceOne : // Substituindo um elemento
            {
               filter : { name : "Claire" },
               replacement : { name: "Genny", major: "Counsling", gpa: 2.4 }
            }
         }
    ],
    {ordered: true} // Indicando que as ações devem ser feitas na ordem. Por padrão: true
   );

```

## Indexando Texto

```javascript

// Criando um index de Nomes e Descrições chamado "text"
db.stores.createIndex( { name: "text", description: "text" } )

// Buscando, através de "text", documentos com a substring "Coffee"
db.stores.find({ $text: {$search: "Coffee" } })

// Buscando, através de "text", documentos com pelo menos uma das substrings: "Java", "Hut", "Coffee"
db.stores.find({ $text: {$search: "Java Hut Coffee" } })

// Buscando, através de "text", documentos com pelo menos uma das substrings: "Java", "Hut", "Coffee". Além disso, os documentos são rankeados pela proximidade com a pesquisa "text" (o score é "pesquisa" + "Score")
db.stores.find(
   { $text: { $search: "Java Hut Coffee" } },
   { score: { $meta: "textScore" } }
)

```

## Agregação

```javascript

db.purchase_orders.insertMany(
     [
          {product: "toothbrush", total: 4.75, customer: "Mike"},
          {product: "guitar", total: 199.99, customer: "Tom"},
          {product: "milk", total: 11.33, customer: "Mike"},
          {product: "pizza", total: 8.50, customer: "Karen"},
          {product: "toothbrush", total: 4.75, customer: "Karen"},
          {product: "pizza", total: 4.75, customer: "Dave"}
          {product: "toothbrush", total: 4.75, customer: "Mike"},
     ]
)

// Contar quantos documentos possuem determinado atributo
db.purchase_orders.count({product: "toothbrush"})

// Listar os documentos sem valores repetidos de um certo atributo
db.purchase_orders.distinct("product")

// Agrupar os documentos por um atributo e somar os valores de outro atributo
db.purchase_orders.aggregate(
     [
          {$match: {} },
          {$group: {_id: "$customer", total: { $sum: "$total"} } }
     ]
)

// Agrupar os documentos por um atributo, somar os valores de outro atributo e inversamente ordenar por ele
db.purchase_orders.aggregate(
     [
          {$match: {} },
          {$group: {_id: "$product", total: { $sum: "$total"} } },
          {$sort: {total: -1}}
     ]
)

// Filtrar uma coleção, e em seguida agrupar os documentos por um atributo e somar os valores de outro atributo
db.purchase_orders.aggregate(
     [
          {$match: {product: {$in: ["toothbrush", "pizza"]} } },
          {$group: {_id: "$product", total: { $sum: "$total"} } },
     ]
)

```
Para consultar os outros operadores de agregação, segue a página (em inglês) clicando [aqui](https://docs.mongodb.com/manual/reference/operator/aggregation/).

## Problemas e Soluções

### Endereço já em uso

Podemos nos deparar, ao tentar rodar o servidor do Mongo, com o seguinte erro:

```bash

Failed to set up listener: SocketException: Address already in use

```

Como proceder ? Basta matarmos o processo com o comando abaixo e rodar novamente o servidor.

```

sudo killall -15 mongod

```
