---
title: "Angular 7"
date: 2018-06-18T01:00:00-03:00
author: "Amintas Victor"
type: "post"

---

## Instalando Angular CLI
```bash
sudo npm install @angular/cli
```
## Criando Projeto Angular
```bash
ng new nome_do_projeto
```
É recomendado escolher **usar Angular Router** e usar o **SASS**.
## Subir Projeto Angular
Podemos subir nosso projeto Angular, através de um servidor node.js local, através do seguinte comando:
```bash
ng serve -o
```
Podemos acessar através do link **http://localhost:4200/**.
## Criando Componente
```bash
ng generate component nome_do_componente
# ou
ng g c nome_do_componente
```
## Estrutura do Projeto
```bash
# Os componentes estão em negrito
src
|_ app
    |_ about
    |_ contact
    |_ home
    |_ nav
```
## Implementando Componente
Eis o exemplo da implementação de um componente `./src/app/nav`:

Em `./src/app/app.component.html`:
```html
<app-nav></app-nav>

<section>
  <router-outlet></router-outlet>
</section>
```
Em `./src/app/nav/nav.component.html`:
```html
<header>
  <div class="container">
    <a routerLink="/" class="logo">{{ myTitle }}</a>
    <nav>
      <ul>
        <li><a routerLink="/">Home</a></li>
        <li><a routerLink="/about">About</a></li>
        <li><a routerLink="/contact">Contact us</a></li>
      </ul>
    </nav>
  </div>
</header>
```
Em `./src/app/nav/nav.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-nav',
  templateUrl: './nav.component.html',
  styleUrls: ['./nav.component.scss']
})
export class NavComponent implements OnInit {

  myTitle: string = 'myapp';

  constructor() { }

  ngOnInit() {
  }

}
```
Podemos aplicar um **scss geral para os componentes** através do arquivo `./src/styles.scss`, da mesma forma que podemos aplicar um **scss particular a um componente** através do arquivo `./src/app/nome_comp/nome_comp.component.scss`.
## Implementando Rotas
Eis a implementação de rotas para os componentes `./home/home.component`, `./about/about.component`, e `./contact/contact.component`:

Em `./src/app/app-routing.module.ts`:
```javascript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';
import { ContactComponent } from './contact/contact.component';

const routes: Routes = [
  {path: '', component: HomeComponent},
  {path: 'about', component: AboutComponent},
  {path: 'contact', component: ContactComponent}
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```
## Eventos Dinâmicos
Em `./src/app/home/home.component.html`:
```html
<h1>Home</h1>

<button (click)="firstClick()">Click me</button>
```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

  firstClick(){
    console.log('clicked');
  }

}
```
Outros tipos de eventos:
```markdown
(focus)="myMethod()"
(blur)="myMethod()"
(submit)="myMethod()"  
(scroll)="myMethod()"

(cut)="myMethod()"
(copy)="myMethod()"
(paste)="myMethod()"

(keydown)="myMethod()"
(keypress)="myMethod()"
(keyup)="myMethod()"

(mouseenter)="myMethod()"
(mousedown)="myMethod()"
(mouseup)="myMethod()"

(click)="myMethod()"
(dblclick)="myMethod()"

(drag)="myMethod()"
(dragover)="myMethod()"
(drop)="myMethod()"
```
## Classe e Estilos Dinâmicos
### Uma classe
Em `./src/app/home/home.component.html`:
```html
<h1 [class.gray]='h1Style'>Home</h1>

<button (click)="firstClick()">Click me</button>
```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  h1Style: boolean = false;

  constructor() { }

  ngOnInit() {
  }

  firstClick(){
    this.h1Style = !this.h1Style;
  }

}
```
Em `./src/app/home/home.component.scss`:
```scss
.gray{
  color: gray;
}
```
### Várias classes
Em `./src/app/home/home.component.html`:
```html
<h1 [ngClass]="{
  'gray': h1Style,
  'large': !h1Style
}">Home</h1>

<button (click)="firstClick()">Click me</button>

```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  h1Style: boolean = false;

  constructor() { }

  ngOnInit() {
  }

  firstClick(){
    this.h1Style = !this.h1Style;
  }

}
```
Em `./src/app/home/home.component.scss`:
```scss
.gray{
  color: gray;
}

.large{
  font-size: 4em
}
```
### Um estilo
Em `./src/app/home/home.component.html`:
```html
<h1 [style.color]="h1Style ? 'blue': 'red'">Home</h1>

<button (click)="firstClick()">Click me</button>
```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  h1Style: boolean = false;

  constructor() { }

  ngOnInit() {
  }

  firstClick(){
    this.h1Style = !this.h1Style;
  }

}
```
### Vários estilos
Em `./src/app/home/home.component.html`:
```html
<h1 [ngStyle]="{
  'color': h1Style ? 'gray' : 'black',
  'font-size': !h1Style ? '1em' : '4em'
}">Home</h1>

<button (click)="firstClick()">Click me</button>

```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  h1Style: boolean = false;

  constructor() { }

  ngOnInit() {
  }

  firstClick(){
    this.h1Style = !this.h1Style;
  }

}
```
## Services
### Criando Services
```bash
ng generate service nome_do_service
# ou
ng g s nome_do_service
```
### Oferecendo funcionalidades a outros componentes
Podemos oferecer funções a todos os outros componentes da aplicação através do service. Um exemplo de uma simples implementação se encontra aqui:

Em `./src/app/data.service.ts`:
```javascript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor() { }

  firstClick() {
    return console.log('clicked');
  }
}
```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';
// Importando service
import { DataService } from '../data.service';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {
// Injetando service
  constructor(private data: DataService) { }

  ngOnInit() {
  }

  firstClick() {
    this.data.firstClick();
  }

}
```
Em `./src/app/home/home.component.html`:
```html
<h1>Home</h1>

<button (click)="firstClick()">Click me</button>
```
## Cliente HTTP
Importamos o cliente HTTP fazendo as seguintes modificações em `.src/app/app.module.ts`:
```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
// Outros imports
import { HttpClientModule } from '@angular/common/http';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { NavComponent } from './nav/nav.component';
import { AboutComponent } from './about/about.component';
import { ContactComponent } from './contact/contact.component';
import { HomeComponent } from './home/home.component';

@NgModule({
  declarations: [
    AppComponent,
    NavComponent,
    AboutComponent,
    ContactComponent,
    HomeComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule,    // <-- Import manual aqui
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
Em `./src/app/data.service.ts`:
```javascript
import { Injectable } from '@angular/core';
// Importando Cliente HTTP
import { HttpClient } from '@angular/common/http';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  // Injetando Cliente HTTP
  constructor(private http: HttpClient) { }

  getUsers() {
    return this.http.get('https://api/users');
  }
}
```
Em `./src/app/home/home.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';
import { DataService } from '../data.service';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  users: Object;

  constructor(private data: DataService) { }

  ngOnInit() {
    this.data.getUsers().subscribe(data => {
        this.users = data
        console.log(this.users);
      }
    );
  }

}
```
Em `./src/app/home/home.component.html`:
```html
<h1>Home</h1>

<ul *ngIf="users">
  <li *ngFor="let user of users.data">
    <img [src]="user.avatar">
    <p>{{ user.first_name }} {{ user.last_name }}</p>
  </li>
</ul>
```
## Formulários
Primeiramente importamos o **módulo de formulários reativos** do **Angular Forms** da seguinte forma:

Em `./src/app/app.module.ts`:
```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
// Outros imports
import { HttpClientModule } from '@angular/common/http';
import { ReactiveFormsModule } from '@angular/forms';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { NavComponent } from './nav/nav.component';
import { AboutComponent } from './about/about.component';
import { ContactComponent } from './contact/contact.component';
import { HomeComponent } from './home/home.component';

@NgModule({
  declarations: [
    AppComponent,
    NavComponent,
    AboutComponent,
    ContactComponent,
    HomeComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule,       // Importando Cliente HTTP
    ReactiveFormsModule     // Importando Módulo de Formulários Reativos
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
Depois implementamos o formulário propriamente dito:

Em `./src/app/contact/contact.component.ts`:
```javascript
import { Component, OnInit } from '@angular/core';
// Importando módulos do Angular Forms
import { FormBuilder, FormGroup, Validators } from '@angular/forms';

@Component({
  selector: 'app-contact',
  templateUrl: './contact.component.html',
  styleUrls: ['./contact.component.scss']
})
export class ContactComponent implements OnInit {

  // Instanciando Formulário
  messageForm: FormGroup;
  // Booleanos de confirmação
  submitted = false;
  success = false;

  constructor(private formBuilder: FormBuilder) { }

  ngOnInit() {
    // Construindo formulário e suas validações
    this.messageForm = this.formBuilder.group({
      name: ['', Validators.required],
      message: ['', Validators.required]
    });
  }

  onSubmit() {
    this.submitted = true;

    if (this.messageForm.invalid) {
        return;
    }

    this.success = true;
  }
}
```
Em `./src/app/contact/contact.component.html`:
```html
<h1>Contact us</h1>

<form [formGroup]="messageForm" (ngSubmit)="onSubmit()">

    <h5 *ngIf="success">Your form is valid!</h5>

    <label>
      Name:
      <input type="text" formControlName="name">
      <!-- Se o formulário for submetido e houverem erros quanto ao nome -->
      <div *ngIf="submitted && messageForm.controls.name.errors" class="error">
        <!-- Se houver o erro na validação required do nome -->
        <div *ngIf="messageForm.controls.name.errors.required">
            Your name is required
        </div>
      </div>
    </label>

    <label>
      Message:
      <textarea formControlName="message"></textarea>
      <!-- Se o formulário for submetido e houverem erros quanto à messagem -->
      <div *ngIf="submitted && messageForm.controls.message.errors" class="error">
        <!-- Se houver o erro na validação required do nome -->
        <div *ngIf="messageForm.controls.message.errors.required">
            A message is required
        </div>
      </div>
    </label>

    <input type="submit" value="Send message" class="cta">

  </form>

  <div *ngIf="submitted" class="results">
    <strong>Name:</strong>
    <span>{{ messageForm.controls.name.value }}</span>

    <strong>Message:</strong>
    <span>{{ messageForm.controls.message.value }}</span>
  </div>
```
## Subindo o Projeto
```bash
ng build --prod
```
Será criado o diretório `./dist`, basta hospedá-lo como quiser.
