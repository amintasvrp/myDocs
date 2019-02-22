# Node.js e HTTP: desenvolvendo uma API seguindo o estilo REST
## Configuração do Ambiente
### Instalando o Node
```bash
sudo apt install -y nodejs
```
### Criando um Projeto Node
```bash
npm init
```
Será criado um arquivo `package.json` que será útil para informações de configuração e dependências do projeto. Vamos criar o arquivo `index.js` que é recomendado pelo node para iniciar a aplicação.

### Instalando o Express como Dependência
Para suportar todas as características básicas de uma aplicação web sem que tenhamos que nos preocupar em ficar implementando coisas repetitivas, usaremos o **Express.** Para sua instalação, usamos o seguinte comando:
```bash
npm install express --save
```
### Instalando o Nodemon com Dependência
O **nodemon** facilita a execução de aplicações em Node porque já faz uma espécie de "deploy automático" da aplicação sempre que identifica mudança em algum dos arquivos.
```bash
sudo npm install -g nodemon
```
### Iniciando Aplicação
```bash
# Usando o node
node index.js
# Usando o nodemon (recomendado)
nodemon index.js
```


### 
### 