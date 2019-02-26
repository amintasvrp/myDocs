# Node.js e HTTP: desenvolvendo uma API seguindo o estilo REST
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
## 



