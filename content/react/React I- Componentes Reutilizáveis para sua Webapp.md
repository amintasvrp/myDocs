# React I: Componentes Reutilizáveis para sua Webapp
## 
## Criando e configurando o projeto
### 
### Configurando Ambiente
```bash
# Instalando Node.js e o NPM
sudo apt install nodejs
sudo apt install npm
# Instalar o create-react-app localmente
npm install create-react-app
# Criando o projeto
./node_modules/.bin/create-react-app projeto
# Rodando o projeto
cd projeto
npm start
```
### 
### JSX, Babel e Webpack
Com o React, nós escrevemos uma linguagem escrita sobre JS. Nós utilizamos a linguagem JSX que nos permite usar marcações XML. O Babel, instalado juntamente com o create-react-app, um compilador (ou um transpiler) de código fonte JavaScript. Ele pegará um código escrito com ECMAScript 6, que ainda só é exportada pelo Node.js, e irá suportar a sintaxe inválida do JS.

Vamos conhecer a utilidade de outro plugin do Babel: ES2015 preset. Com ele, podemos fazer diversas conversões para versões antigas do JS. Ele ainda possui um script que ficar verificando se existem falhas no nosso código.

Webpack é utilizado para converter arquivos e pacotes para algo que rode no browser (no caso, código JavaScript).

## Definindo a estrutura do HTML
### 
### Importando CSS e Colocando HTML
```javascript
import './css/pure-min.css'; // Importando o Pure
import './css/side-menu.css'; // Importando o tema do Pure: Responsive Layout
```
Para colocar o respectivo HTML, basta colocar o HTML padrão do tema a partir da div **layout**, contido no arquivo `index.html`, no método `render()` que é retornado pelo **componente** do `App.js`.

### Comentando no HTML retornado pelo Componente JS
```javascript
{/* Comentário */}
```
### Abre e Fecha Tags
Em algumas situações devemos fechar tags que não são obrigatoriamente fechadas no HTML. Isso acontece porque estamos tratando o HTML como um XML, onde para o mesmo toda tag aberta deve ser fechada.

### Class e className
Dentro do HTML retornado devemos substituir o parâmetro `class` por `className`. Isso acontece porque class é uma palavra reservada do JS.

## Consumindo API
### Manutenção do Estado do Componente
```javascript
class App extends Component {
constructor() {
    super(); // Herdar construtor de componente
    this.state = { lista: [{nome:'alberto', email:'alberto.souza@caelum.com.br',senha:'123456'}]}; // Variável para definir estado
}
....
// Dentro do render()
<tbody>
  {
    this.state.lista.map(function(autor){
       return (
         <tr>
           <td>{autor.nome}</td>
           <td>{autor.email}</td>
         </tr>
       );
     })
  }
</tbody>
```
### Atualizando o Estado do Componente
Primeiramente, devemos instalar o JQuery como dependência:
```bash
npm install jquery --save
```

E em seguida importar no componente:
```javascript
import $ from 'jquery';
```

Podemos usar duas funções de atualização de estado: `componentDidMount()`, usada quando o componente acabou de ser montado ( logo após o método `render()` ser invocado pela primeira vez), e o `componentWillMount()`, que será chamada antes da invocação do `render()`.

```javascript
constructor() {
    super();    
    this.state = {lista : []};
}

// Realizando requisições assíncronas
componentDidMount(){  
    $.ajax({
        url:"http://localhost:8080/api/autores",
        dataType: 'json',
        success:function(resposta){    
          this.setState({lista:resposta});
        }.bind(this)
      } 
    );          
}
  
.......
  
 <tbody>
  {
    this.state.lista.map(function(autor){
      return (
      // Em estados atualizados por ajax, devemos colocar uma key para otimizar a atualização dinâmica do DOM
        <tr key={autor.id}>
          <td>{autor.nome}</td>
          <td>{autor.email}</td>
        </tr>
      );
    })
  }
</tbody>
```
## Cadastros: Eventos e Formulários
```javascript
 constructor() { 
    super();    
    this.state = {lista : [],nome:'',email:'',senha:''}; // Lista e dados do formulário
    this.enviaForm = this.enviaForm.bind(this);
    this.setNome = this.setNome.bind(this); 
    this.setEmail = this.setEmail.bind(this);
    this.setSenha = this.setSenha.bind(this); 
  }
 
 ....
 
 // Evento ao submeter formulário
   enviaForm(evento){
    evento.preventDefault();    
    $.ajax({
      url:'http://localhost:8080/api/autores',
      contentType:'application/json',
      dataType:'json',
      type:'post',
      data:        JSON.stringify({nome:this.state.nome,email:this.state.email,senha:this.state.senha}),
      success: function(resposta){
        this.setState({lista:resposta});        
      }.bind(this),
      error: function(resposta){
        console.log("erro");
      }      
    });
  }

// Alterar campo de nome
  setNome(evento){
    this.setState({nome:evento.target.value});
  }

// Alterar campo de email
  setEmail(evento){
    this.setState({email:evento.target.value});
  }  

// Alterar campo de senha
  setSenha(evento){
    this.setState({senha:evento.target.value});
  }
 
 .......
 
 <div className="pure-form pure-form-aligned">
    <form className="pure-form pure-form-aligned" onSubmit={this.enviaForm.bind(this)} method="post">
    <label htmlFor="nome">Nome</label>
        <input id="nome" type="text" name="nome" value={this.state.nome} onChange={this.setNome}/>  
 </div>
 <div className="pure-control-group">
     <label htmlFor="email">Email</label>
     <input id="email" type="email" value={this.state.email} onChange={this.setEmail} />           
 </div>
 <div className="pure-control-group">
     <label htmlFor="senha">Senha</label>
     <input id="email" type="password" name="senha" value={this.state.senha} onChange={this.setSenha} />
 <div className="pure-control-group">                                  
     <label></label> 
     <button type="submit" className="pure-button pure-button-primary">Gravar</button>                                    
 </div>
 </form>
```
## Componentes Reutilizáveis
Criamos primeiro o seguinte arquivo: `./componentes/InputCustomizado`
```javascript
import React, { Component } from 'react';

export default class InputCustomizado extends Component{

	render() {
		return (
			<div className="pure-control-group">
			  <label htmlFor={this.props.id}>{this.props.label}</label> 
			  <input id={this.props.id} type={this.props.type} name={this.props.name} value={this.props.value}  onChange={this.props.onChange}/>                  
			</div>			
		);
	}
}
```
Importamos esse arquivo dessa forma em nosso `App.js`:
```javascript
import InputCustomizado from './componentes/InputCustomizado';
```
E utilizamos esse componente assim:
```javascript
<form className="pure-form pure-form-aligned" onSubmit={this.enviaForm} method="post">
     <InputCustomizado id="nome" type="text" name="nome" value={this.state.nome} onChange={this.setNome} label="Nome"/>                                              
     <InputCustomizado id="email" type="email" name="email" value={this.state.email} onChange={this.setEmail} label="Email"/>                                              
     <InputCustomizado id="senha" type="password" name="senha" value={this.state.senha} onChange={this.setSenha} label="Senha"/>                                                                      
     <div className="pure-control-group">                                  
         <label></label> 
         <button type="submit" className="pure-button pure-button-primary">Gravar</button>                                    
     </div>
 </form>
```

## Comunicação entre Componentes
Ao desacoplar funcionalidades de uma tela em outros componentes, podemos nos deparar com a situação de termos componentes diferentes que compartilham um mesmo estado. Para solucionar esta situação, temos a disposição 2 soluções: os High-Order Components e a biblioteca pubsub. 

Os primeiros, também chamados de wrappers ou boxes, são componentes que possuem um estado onde enquanto uns consomem outros modificam, de maineira que são simples de implementar, mas ainda possui um alto acoplamento. A segunda possui a seguinte ideia: Um componente publica um determinado objeto, enquanto outros se inscrevem para consumir esse objeto, sem saber da existência um do outro.

### Componente de Alta Ordem
```javascript
// Componente Modificador
class FormularioAutor extends Component {

  constructor() {
    super();    
    this.state = {nome:'',email:'',senha:''};
    this.enviaForm = this.enviaForm.bind(this);
    this.setNome = this.setNome.bind(this);
    this.setEmail = this.setEmail.bind(this);
    this.setSenha = this.setSenha.bind(this);
  }
  
    enviaForm(evento){
    evento.preventDefault();    
    $.ajax({
      url:'http://localhost:8080/api/autores',
      contentType:'application/json',
      dataType:'json',
      type:'post',
      data: JSON.stringify({nome:this.state.nome,email:this.state.email,senha:this.state.senha}),
      success: function(resposta){
        this.props.callbackAtualizaListagem(resposta); // Atualizando a lista
        this.setState({nome:'',email:'',senha:''});
      }.bind(this),
      error: function(resposta){
         // Tratamento de Erros
      }    
    });
  }
  
  ....
}

// Componente Consumidor
class TabelaAutores extends Component {

    render() {
        return(
        .....
                        <tbody>
                          {
                            this.props.lista.map(function(autor){
                              return (
                                <tr key={autor.id}>
                                  <td>{autor.nome}</td>
                                  <td>{autor.email}</td>
                                </tr>
                              );
                            })
                          }
                        </tbody>
       .......                   
        );
    }
}

// Componente de Alta Ordem
export default class AutorBox extends Component {

  constructor() {
    super();    
    this.state = {lista : []};
    this.atualizaListagem = this.atualizaListagem.bind(this);    
  }

  componentDidMount(){  
    $.ajax({
        url:"http://localhost:8080/api/autores",
        dataType: 'json',
        success:function(resposta){    
          this.setState({lista:resposta});
        }.bind(this)
      } 
    );          
  }   

 atualizaListagem(novaLista) {
  this.setState({lista:novaLista});
}

  render(){
    return (
      <div>
        <FormularioAutor callbackAtualizaListagem={this.atualizaListagem}/>
        <TabelaAutores lista={this.state.lista}/>

      </div>
    );
  }
}
```

### PubSub
Instalamos como dependência usando o seguinte comando:
```bash
npm install --save pubsub-js
```
Realizamos o seguinte import em cada módulo que utiliza o PubSub:
```javascript
import PubSub from 'pubsub-js';
```
Usamos da seguinte forma:
```javascript
// Publisher
class FormularioAutor extends Component {

  constructor() {
    super();    
    this.state = {nome:'',email:'',senha:''};
    this.enviaForm = this.enviaForm.bind(this);
    this.setNome = this.setNome.bind(this);
    this.setEmail = this.setEmail.bind(this);
    this.setSenha = this.setSenha.bind(this);
  }

  enviaForm(evento){
    evento.preventDefault();    
    $.ajax({
      url:'http://localhost:8080/api/autores',
      contentType:'application/json',
      dataType:'json',
      type:'post',
      data: JSON.stringify({nome:this.state.nome,email:this.state.email,senha:this.state.senha}),
      success: function(novaListagem){
        PubSub.publish('atualiza-lista-autores',novaListagem); // Publicando nova listagem       
        this.setState({nome:'',email:'',senha:''});
      }.bind(this),
      error: function(resposta){
        // Tratamento de Erros
      }      
    });
    ....
}

....

// Subscriber
export default class AutorBox extends Component {

  constructor() {
    super();    
    this.state = {lista : []};    
  }

  componentDidMount(){  
    $.ajax({
        url:"http://localhost:8080/api/autores",
        dataType: 'json',
        success:function(resposta){    
          this.setState({lista:resposta});
        }.bind(this)
      } 
    );          
    // Atualizando a lista
    PubSub.subscribe('atualiza-lista-autores',function(topico,novaLista){ 
      this.setState({lista:novaLista});
    }.bind(this));
  }  
}
```

## Tratamento de Erros
Em `InputCustomizado.js`:
```javascript
export default class InputCustomizado extends Component{

    constructor(){
        super();
        this.state = {msgErro:''};  // Estado da msg de erro
    }

    render() {
        return (
            <div className="pure-control-group">
              <label htmlFor={this.props.id}>{this.props.label}</label> 
              <input id={this.props.id} type={this.props.type} name={this.props.name} value={this.props.value}  onChange={this.props.onChange}/>                  
              <span className="error">{this.state.msgErro}</span> // Mostrar Erro
            </div>            
        );
    }

    componentDidMount() {
        // Mostrar o erro apenas para o campo correto
        PubSub.subscribe("erro-validacao",function(topico,erro){            
            if(erro.field === this.props.name){
                this.setState({msgErro:erro.defaultMessage});            
            }
        }.bind(this));
        
        // Limpar msg ao ser clicado o botão de submissão
        PubSub.subscribe("limpa-erros",function(topico){                        
            this.setState({msgErro:''});                        
        }.bind(this));        
    }
}
```
Em `Autor.js`:
```javascript
class FormularioAutor extends Component {

  constructor() {
    super();    
    this.state = {nome:'',email:'',senha:''};
    this.enviaForm = this.enviaForm.bind(this);
    this.setNome = this.setNome.bind(this);
    this.setEmail = this.setEmail.bind(this);
    this.setSenha = this.setSenha.bind(this);
  }

  enviaForm(evento){
    evento.preventDefault();    
    $.ajax({
      url:'http://localhost:8080/api/autores',
      contentType:'application/json',
      dataType:'json',
      type:'post',
      data: JSON.stringify({nome:this.state.nome,email:this.state.email,senha:this.state.senha}),
      success: function(novaListagem){
        PubSub.publish('atualiza-lista-autores',novaListagem);        
        this.setState({nome:'',email:'',senha:''});
      }.bind(this),
      error: function(resposta){
        if(resposta.status === 400) {
          // Acionar tratador de erros
          new TratadorErros().publicaErros(resposta.responseJSON);
        }
      },
      beforeSend: function(){
        PubSub.publish("limpa-erros",{}); // Sinal de apagar msg de erro
      }      
    });
  }
  .....
}
......
```
Em `TratadorErros.js`:
```javascript
export default class TratadorErros {
    publicaErros(erros){
        for(var i=0;i<erros.errors.length;i++){
            var erro = erros.errors[i];
            PubSub.publish("erro-validacao",erro); // Publicar cada erro ocorrido
        }
    }
}
```



### 