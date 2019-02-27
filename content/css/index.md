---
title: "CSS 3: Estilizando seu Website"
date: 2018-06-17T23:59:00-03:00
author: "Amintas Victor"
type: "post"
---

## Folha de Estilo Interna

```html

<body style="color: blue; font-size:20px">
     <header>
          <h1 style="color: red;"> Título de fonte vermelha</h1>
     </header>

     <main style="border: 1px solid black; width: 80%; max-width:500px">
          <p>Parágrafo com fonte azul; borda fina, reta e preta ao redor, com tamanho responsivo de 80% e máximo de 500px</p>
     </main>
</body>

```

## Cores

```html

<header>
     <h1 style="color: CornflowerBlue;">Configurando cor pelo nome</h1>
     <h1 style="color: #ff0000;">Configurando cor pelo código hexadecimal</h1>
     <h1 style="color: rgb(255, 0, 0);">Configurando cor pelo RGB</h1>
</header>

```

## Margens e Preenchimentos

```html

<!-- Preenchimentos (espaço entre a margem e o elemento em si) -->
<div style="padding: 50px;">
     Preenchimento geral
</div>

<div style="padding-top: 50px; padding-bottom: 25px;padding-left: 50px; padding-right: 25px;">
     Preenchimento de apenas um lado
</div>

<div style="padding: 50px 25px 50px 25px;">
     Preenchimento de todos os lados
</div>

<!-- Margem -->
<div style="margin: 50px;">
     Margem geral
</div>

<div style="margin-top: 50px; margin-bottom: 25px; margin-left: 50px; margin-right: 25px;">
     Margem de apenas um lado
</div>

<div style="margin: 50px 25px 50px 25px;">
     Margem de todos os lados
</div>

```

## Displays e Floats

```html

<!--float: desloca o elemento para um dos lados (left ou right), abrindo espaço para que o elemento seguinte se coloque no outro lado -->
<!-- display: determina se o elemento ocupará a linha toda (block) ou apenas o espaço necessário (inline) -->
<ul style="float:left">
     <li style="display:inline;">Nomes</li>
     <li style="display:inline;">na</li>
     <li style="display:inline;">mesma</li>
     <li style="display:inline;">linha</li>
</ul>

<p>Este parágrafo estará a direita da lista</p>

```

## Posição

```html

<div style="position: static">
  Elemento na posição padrão, seguindo o fluxo da página
</div>

<div style="position: relative; top: 10px; bottom: 10px; width:10px; height:10px">
  Deslocamento relativo a posição padrão
</div>

<div style="position: absolute; top: 10px; bottom: 10px; width:10px; height:10px">
  Deslocamento relativo a origem da página
</div>

<div style="position: fixed; top: 10px; bottom: 10px; width:10px; height:10px">
  Deslocamento relativo a origem da página, flutuando durante a navegação
</div>

```

## Estilização Avançada

```html

<!-- text-shadow e box-shadow: desloc.vertical desloc.horizontal blur cor -->
<!-- opacity: de 0.0 a 1.0 -->
<!-- border-radius (arredondado): pixels ou porcentagem -->

<h1 style="text-shadow: 2px 2px 2px red">
     Texto Estilizado
</h1>

<img style="box-shadow: 2px 2px 2px black;
            opacity:0.4;
            border-radius: 50%;"
     src="imagem.jpeg"
/>

```

## Texto e Fontes

```html

<!-- font-size: pixels ou em (1em = 16px) -->
<!-- font-variant: maiúsculas e minúsculas-->

<p style="color: blue;
          font-size:2em;
          font-family: 'Arial Black', Gadget, sans-serif;
          font-style: italic;
          font-variant: small-caps;
          font-weight: bold;">
     Texto Estilizado
</p>

```

## Tag Style

```html

<style>
     body {
          color:blue;
     }

     h1 {
          color:green;
     }
</style>

<body>
  <h1> ... </h1>
  ...
</body>

```

## Folha de Estilo Externa

Em **site.html**:

```html

<head>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1> ... </h1>
  ...
</body>

```

Em **style.css**:

```css

body {
     color:blue;
}

h1 {
     color:green;
}

```

## Ids e Classes

```html

<main class="fancy-border red-text">
     <h1 id="title-id" > Título Azul </h1>
     <p>
       Parágrafo Vermelho
     </p>     
</main>

```

Em **style.css**:

```css

/* O mais específico (no caso, o id) sempre tem prioridade*/

#title-id {
     color:blue;
}

.fancy-border {
     border: 3px dashed red;
}

.red-text {
     color:red;
}

```

## Manipulando Seletores

```css

#id {
  /* Elemento único */
}

.classe {
  /* Todos os elementos que fazem parte de uma classe */
}

* {
  /* Toda a página*/
}

h2 {
  /* Todas as tags h2 */
}

h2, h1 {
  /* Todas as tags h2 e as tags h1 */
}

ul > li {
  /* Todas as tags li que estão dentro de ul*/
}

p + h2 {
  /* Todas as tags h2 que vem logo após uma tag p */
}

[title] {
  /* Todas as tags que tem a propriedade title */
}

li[title="nome"] {
  /* Todas as tags li que tem a propriedade title com valor "nome" */
}

[title*="cabeçalho"] {
  /* Todas as tags que tem a propriedade title cujo valor tem a
  substring "cabeçalho" */
}

input:checked{
  /* Todas as tags que são input e estão com valor checked */
}

h2:hover {
  /* Todas as tags h2 que estão sob o mouse */
}

ul > li:nth-last-child(2) {
  /* Para cada ul, a penúltima tag li */
}

```

## Flexbox

Consiste em containers de alinhamento responsivo. Para ver um diagrama completo sobre como configurar seu flexbox (em inglês), clique [aqui](http://jonibologna.com/content/images/flexboxsheet.pdf) !

Segue abaixo um exemplo de uso do flexbox:

Em **site.html**:

```html

<div class="flex-container">
     <div class="flex-item"> Caixa 1 </div>
     <div class="flex-item"> Caixa 2 </div>
     <div class="flex-item"> Caixa 3 </div>
     <div style="align-self:center;" class="flex-item"> Caixa 4 </div>
     <div class="flex-item"> Caixa 5 </div>
</div>

```

Em **style.css**:

```css

.flex-container {
     display: flex;
     flex-direction: row;
     justify-content: space-around;
     flex-wrap: wrap;
     align-items: center;
     align-content: space-between;
}

```

## Animações

Seguem abaixo exemplos de animações:

```css

@keyframes mudar-cor {
     from {background-color: red;}
     to {background-color: green;}
}

@keyframes arco-iris {
     0% {background—color: red;}
     15% {background—color: orange; top:10px; left:10px;}
     30% {background—color: yellow; top:20px; left:20px;}
     45% {background—color: green; top:30px; left:30px;}
     60% {background—color: blue; top:40px; left:40px;}
     80% {background—color: lightblue; top:50px; left:50px;}
     100% {background—color: purple; top:60px; left:60;}
}

.box-animation{
     animation-name: muda-cor;
     animation-duration: 2s;
     animation-delay: 2s;
     animation-iteration-count: 2;
}

```

## Importar outros CSSs

```css

@import "style.css";

```

## Suporte de Navegadores

Para saber quais navegadores suportam quais funcionalidades do CSS 3, basta consultar o guia (em inglês) clicando [aqui](https://www.w3schools.com/cssref/css3_browsersupport.asp) !

## Frameworks

Ao invés de escrevermos CSSs do zero para estilizar nosso website, podemos usar frameworks que implementam esses CSSs por nós. Há várias formas de utilizar esses frameworks em nosso projeto: baixar os arquivos, instalar via gerenciador de pacotes... Mas a mais simples e recomendada é utilizar CDNs.

Os CDNs são como APIs que nos retornam os serviços que necessitamos, no caso os arquivos CSS e JS que irão estilizar nosso site. Para tal, basta colar tags no head do arquivo html. Segue abaixo as tags para utiliar o **Bootstrap**, uma das mais comuns entre os iniciantes:

```html

<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k" crossorigin="anonymous"></script>

```

Lembre-se de olhar a documentação para entender quais classes serão usadas e para quê elas servem.
