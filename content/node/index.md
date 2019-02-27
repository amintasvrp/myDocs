---
title: "NodeJS: desenvolvendo uma API REST"
date: 2018-06-17T23:54:00-03:00
author: "Amintas Victor"
type: "post"
---

## Instalando o NodeJS
```bash
sudo apt install nodejs -y
# Checando se o node foi instalado
node -v
# Checando se o npm foi instalado
npm -v
## Se o npm não foi instalado, use o comando: sudo apt install npm -y
```
## Criando Estrutura
```bash
mkdir node-api # node-api é o nome do projeto
cd node-api
npm init -y # criando projeto node
```
Teremos um arquivo chamado `package.json`. Ele é responsável por manter metadados do projeto e informações sobre as dependências.
```bash
# Instalando express (usado para implementar as rotas de requisição)
npm install express --save
# O diretório criado node-modules armazena as dependências
```
## Criando Primeira Rota
Criamos o arquivo `server.js` e nele temos o seguinte conteúdo:
```javascript
// Importando express
const express = require("express");
// Instanciando a função do express
const app = express();

// Rota
app.get("/", (req,res) => {
    // send() : Envio de dados genérico
    res.send("Hello World");
});

// Definindo porta localhost
app.listen(3001);
```
## Utilizando Nodemon
```bash
# Instalando o Nodemon (atualização dinâmica com reinicialização automática da api)
npm install --save-dev nodemon
```
Editamos o arquivo `package.json`:
```javascript
{
  ...
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "nodemon server.js"
  }
  ...
}
```
Usando o comando abaixo nós executamos o nodemon:
```bash
npm run dev
```
## Instalando MongoDB
Instalaremos primeiro o Docker para isolar a instalação do MongoDB:
```bash
# Instalação do Docker em Ubuntu 18.04 Based Linux
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
sudo apt install docker-ce
# Para verificar se já está ativo
sudo systemctl status docker
```
Instalando o MongoDB:
```bash
# Baixando container do mongo
docker pull mongo
# Subindo container com mongo
docker run --name mongodb -p 27017:27017 -d mongo
# --name nome que será chamado o container
# -p porta de origem nossa máquina : porta de destino no container
# -d imagem que iremos subir
```
Alguns comandos do Docker:
```bash
# Verificamos as imagens que estão rodando
docker ps
# Verificamos todas as imagens, estejam rodando ou pausadas
docker ps -a
# Iniciar imagem já subida
docker start nome_do_container
```
Para termos uma interface gráfica nos ajudando nesse processo, vamos instalar o Robo3T clicando [aqui](https://snapcraft.io/robo3t-snap).
## Conectando Banco de Dados
```bash
# Instalando o Mongoose
npm install mongoose --save
```
No `server.js`:
```javascript
// Importando Dependências
const express = require("express");
const mongoose = require("mongoose");

// Iniciando o App
const app = express();

// Iniciando o DB
mongoose.connect("mongodb://localhost:27017/nodeapi",{useNewUrlParser: true});

// Primeira Rota
app.get("/", (req,res) => {
    // send() : Envio de dados genérico
    res.send("Hello World");
});

// Definindo porta localhost
app.listen(3001);
```
## Criando Models
Instalamos o require-dir para usar o require recursivamente em um diretório:
```bash
npm install require-dir --save
```
Em `src/models/Product.js`:
```javascript
const mongoose = require("mongoose");

const ProductSchema = new mongoose.Schema({
    title: {
        type: String,
        required: true
    },
    description: {
        type: String,
        required: true
    },
    url: {
        type: String,
        required: true
    },
    createdAt: {
        type: Date,
        defaut: Date.now
    }
});

mongoose.model("Product", ProductSchema);
```
Em `server.js`:
```javascript
// Importando Dependências
const express = require("express");
const mongoose = require("mongoose");
const requireDir = require("require-dir");

// Iniciando o App
const app = express();

// Iniciando o DB
mongoose.connect("mongodb://localhost:27017/nodeapi",{useNewUrlParser: true});
requireDir("./src/models");

// Primeira Rota
app.get("/", (req,res) => {
    // send() : Envio de dados genérico
    res.send("Hello World");
});


// Definindo porta localhost
app.listen(3001);
```
## Estruturação e CRUD
```bash
# Hierarquia
node_modules
src
|_ models _ Product.js
|_ controllers _ ProductController.js
|_ routes.js
server.js
package.json
```
Em `src/models/Product.js`:
```javascript
// Importando mongoose
const mongoose = require("mongoose");

// Criando Esquema de Produto
const ProductSchema = new mongoose.Schema({
    title: {
        type: String,
        required: true
    },
    description: {
        type: String,
        required: true
    },
    url: {
        type: String,
        required: true
    },
    createdAt: {
        type: Date,
        default: Date.now
    }
});

// Exportando para ProductController.js
mongoose.model("Product", ProductSchema);
```
Em `src/controllers/ProductController.js`:
```javascript
// Importando o mongoose
const mongoose = require("mongoose");

// Importando o Product.js
const Product = mongoose.model("Product");

// Exportando lógicas de negócio (requisições assíncronas) para routes.js
module.exports = {
    async index(req,res){
        const products = await Product.find();
        // Retornando json
        return res.json(products);
    },

    async show(req, res){
        const product = await Product.findById(req.params.id);
        return res.json(product);
    },

    async store(req, res){
        const product = await Product.create(req.body);
        return res.json(product);
    },

    async update(req, res){
        const product = await Product.findOneAndUpdate({_id: req.params.id}, req.body, {new: true});
        return res.json(product);
    },

    async destroy(req, res){
        await Product.findOneAndDelete({_id: req.params.id});
        return res.send();    
    }

};

```
Em `src/routes.js`:
```javascript
// Importando o express router
const express = require("express");
const routes = express.Router();

// Importando o ProductController
const ProductController = require("./controllers/ProductController");

// Rotas
routes.get("/products", ProductController.index);
routes.get("/products/:id", ProductController.show);
routes.post("/products", ProductController.store);
routes.put("/products/:id", ProductController.update);
routes.delete("/products/:id", ProductController.destroy);


// Exportando módulo para server.js
module.exports = routes;
```
Em `server.js`:
```javascript
// Importando Dependências
const express = require("express");
const mongoose = require("mongoose");
const requireDir = require("require-dir");

// Iniciando o App e habilitando recebimento de json
const app = express();
app.use(express.json());

// Iniciando o DB com os Esquemas
mongoose.connect("mongodb://localhost:27017/nodeapi",{useNewUrlParser: true});
requireDir("./src/models");

// Prefixo e Importando routes.js
app.use("/api", require("./src/routes"));

// Definindo Porta localhost
app.listen(3001);
```
## Testando Requisições
Podemos utilizar Front-Ends de teste como o Postman (baixando ao clicar [aqui](https://snapcraft.io/postman)) ou o Insomnia (baixando ao clicar [aqui](https://snapcraft.io/insomnia)).
## Paginação de Listas
Caso tenhamos uma requisição que retorna uma lista de muitos elementos, é recomendado fazer uma paginação dessa listagem para não comprometer a performance. Primeiro instalamos o mongoose-paginate como dependência:
```bash
npm install mongoose-paginate --save
```
Em `src/models/Product.js`:
```javascript
// Importando dependências
const mongoose = require("mongoose");
const mongoosePaginate = require("mongoose-paginate");

// Criando Esquema de Produto
...

// Adicionando plugin do paginate
ProductSchema.plugin(mongoosePaginate);
...
```
Em `src/controllers/ProductController.js`:
```javascript
...
// Exportando lógicas de negócio (requisições assíncronas) para routes.js
module.exports = {
    async index(req,res){
        // Determinando parâmetro get (/products?page=x)
        const { page = 1 } = req.query ;
        // Realizando paginação
        const products = await Product.paginate({}, { page , limit: 10});
        // Retornando json
        return res.json(products);
    },

   ....
};
```
## Usando o CORS
Utilizamos o CORS para permitir que outros domínios acessem nossa API. Para tal, primeiramente instalaremos o CORS como dependência:
```bash
npm install cors --save
```
Em `server.js`:
```javascript
// Importando Dependências
const express = require("express");
const mongoose = require("mongoose");
const requireDir = require("require-dir");
const cors = require("cors");

// Iniciando o App, habilitando recebimento de json e usando o cors
const app = express();
app.use(express.json());
app.use(cors());
....
```
## Autenticação
Primeiramente instalamos o JWT como dependência:
```bash
npm install jsonwebtoken --save
```
Depois realizamos modificações:
```bash
# Hierarquia
node_modules
src
|_ models _ Product.js
|_ config _ auth.json
|_ controllers _ ProductController.js
|_ midlewares _ auth.js
|_ routes.js
server.js
package.json
```
Em `src/config/auth.js`:
```javascript
{
    "secret": "099af4803fcb3069a85cfb3869521298"
}
```
Em `src/controllers/ProductController.js`:
```javascript
// Importando o mongoose
const mongoose = require("mongoose");

// Importando o Product.js
const Product = mongoose.model("Product");

// Importando o jwt e o secret
const jwt = require("jsonwebtoken");
const authConfig = require("../config/auth");

// Gerando Token
function generateToken(params = {}){
    // Validade: 60 seg
    return jwt.sign(params, authConfig.secret, {
        expiresIn: 60
    });
}

// Exportando lógicas de negócio (requisições assíncronas) para routes.js
module.exports = {
    async index(req,res){
        // Determinando parâmetro get (/products?page=x)
        const { page = 1 } = req.query ;
        // Realizando paginação
        const products = await Product.paginate({}, { page , limit: 10});
        // Retornando json
        return res.json(products);
    },

    async show(req, res){
        const product = await Product.findById(req.params.id);
        return res.json(product);
    },

    // Gerando token ao criar produto
    async store(req, res){
        const product = await Product.create(req.body);
        return res.send({
            product: product,
            token: generateToken({ id: product.id})
        });
    },

    async update(req, res){
        const product = await Product.findOneAndUpdate({_id: req.params.id}, req.body, {new: true});
        return res.json(product);
    },

    async destroy(req, res){
        await Product.findOneAndDelete({_id: req.params.id});
        return res.send();    
    }

};
```
Em `src/middlewares/auth.js`:
```javascript
// Importando JWT
const jwt = require("jsonwebtoken");

// Importando auth.json
const authConfig = require("../config/auth.json");

// Exportando a autenticação para routes.js
module.exports = (req, res, next) => {
    // Obtendo cabeçalho authorization com token
    const authHeader = req.headers.authorization;

    // Verificando se existe o cabeçalho authorization
    if(!authHeader)
        return res.status(401).send({ error: "No Token Provided" });

    // Verificando se respeita o formato: Bearer token
    const parts = authHeader.split(" ");

    if(!parts.length === 2)
        return res.status(401).send({ error: "Token error" });

    const [scheme, token] = parts;

    //Usando Regex para verificar se começa com Bearer

    if(! /^Bearer$/i.test(scheme))
        return res.status(401).send({ error: "Token Malformatted" });

    //Autenticando o token com o auth.secret e verificando a validade    
    jwt.verify(token, authConfig.secret, (error, decoded) => {
        if(error)
            return res.status(401).send({ error: "Token Invalid" });
        return next();
    });
}
```
Em `src/routes.js`:
```javascript
// Importando o express router
const express = require("express");
const routes = express.Router();

// Importando o ProductController
const ProductController = require("./controllers/ProductController");

// Importando o auth.js
const authMiddleware = require("./middlewares/auth");

// Rotas
// A primeira rota necessita de autenticação por token
routes.get("/products", authMiddleware, ProductController.index);
routes.get("/products/:id", ProductController.show);
routes.post("/products", ProductController.store);
routes.put("/products/:id", ProductController.update);
routes.delete("/products/:id", ProductController.destroy);


// Exportando módulo para server.js
module.exports = routes;
```
