---
title: "HTML 5: Construindo um Website"
date: 2018-06-17T23:58:30-03:00
author: "Amintas Victor"
type: "post"
---

## Tags Básicas

### Meta Tags

```html

<html>
     <head>
           <meta charset="UTF-8">
           <meta name="description" content="Descrição do website">
           <meta name="keywords" content="palavras,chave">
           <meta name="author" content="Autor do website">
           <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Janela de visualização-->
          <title>Título do Website</title>
     </head>
    <body>
        Corpo do Website
    </body>
</html>


<head>

</head>


```

### Cabeçalhos

```html

<h1>Cabeçalho 1</h1>

<h2>Cabeçalho 2</h2>

<h3>Cabeçalho 3</h3>

<h4>Cabeçalho 4</h4>

<h5>Cabeçalho 5</h5>

<h6>Cabeçalho 6</h6>

```

### Linha Horizontal

```html

<hr/>

```

### Parágrafo

```html

<p>
  Parágrafo 1
</p>

```

### Formatadores de Texto

```html

<p>
  <big>Texto Grande</big>

  <small>Texto Pequeno</small>

  <b>Texto em Negrito</b>
  <strong>Texto em Negrito</strong>

  <i>Texto em Itálico</i>
</p>

<p>
  Escrita Normal <sup>Escrita Superior</sup>
</p>

```

## Comentários

```html

<!--
Isto é um comentário
Que encobre mais de uma linha
-->

```

## Cores e Estilos

```html

<body style="background-color:cordefundo">
     <h2 style="color:cordafonte">
          Cor de fundo e da fonte determinam um Estilo
     </h2>

     <p style="color: cordafonte; background-color:cordefundo">
          Podemos ter um estilo dentro de outro
     </p>
</body>

```

## Formatando a Página

```html

<body>
     <header>
          Cabeçalho
          <nav>
               Área de Navegação
          </nav>
     </header>
     <main>
          Parte principal (conteúdo)
          <article>
               Artigo
               <section>
                    Seção
                    <aside>
                         Exposto
                    </aside>
               </section>
          </article>
     </main>
     <footer>
          Rodapé
     </footer>
</body>

```

## Links

```html


<a href="https://www.site.com"> Página externa </a>

<a href="pagina.html"> Página no mesmo website </a>

<a href="ebook.pdf"> Arquivo interno </a>


```

## Imagens

```html

<!--
Podemos alterar configurações da imagem como comprimento e largura
-->

<img src="http://www.site.com/foto/"
     alt="Título da Imagem"
     width="200">

```

## Vídeos

```html

<!--
Vídeos externos
-->

<iframe width="560"
        height="315"
        src="https://www.site.com/video/"
        frameborder="0"
        gesture="media"
        allow="encrypted-media"
        allowfullscreen>
</iframe>

<!--
Vídeos internos
-->

<video src="meuvideo.mp4"
       autoplay
       controls
       width="300"
       poster="thumbnail.jpg">
</video>

```

## Listas

```html

<!-- Lista não numerada -->

<ul>
     <li>Ítem</li>
</ul>

<!-- Lista numerada -->

<ol>
     <li>1. Ítem</li>
</ol>

<ol type="A">
     <li>A. Ítem</li>
</ol>

<ol type="a">
     <li>a. Ítem</li>
</ol>

<ol type="I">
     <li>I. Ítem</li>
</ol>

<ol type="i">
     <li>i. Ítem</li>
</ol>

<!-- Lista descritiva -->

<dl>
     <dt>Ítem</dt>
     <dd>Descrição</dd>
</dl>


```

## Tabela

```html


<table>
     <caption>Minha Tabela</caption>
     <thead>
          <tr>
               <th>Cabeçalho 1</th>
               <th>Cabeçalho 2</th>
               <th>Cabeçalho 3</th>
          </tr>
     </thead>
     <tbody>
          <tr>
               <td>Linha 1 Coluna 1</td>
               <td>Linha 1 Coluna 2</td>
               <td>Linha 1 Coluna 3</td>
          </tr>
          <tr>
               <td>Linha 2 Coluna 1</td>
               <td>Linha 2 Coluna 2</td>
               <td colspan="2">Linha 2 Coluna 3</td>
               <td>Linha 2 Coluna 6</td>
          </tr>
     </tbody>
</table>


```

## Divs e Spans

```html

<!-- Containers um abaixo do outro -->
<div>Div1</div>
<div>Div2</div>

<!-- Containers na mesma linha -->
<span>Span1</span>
<span>Span2</span>

```

## Entradas e Formulários

```html
<form>

    <input type="text" value="Insira aqui a entrada"/>

    <input type="password" />

    <input type="number" />

    <input type="checkbox" />

    <input type="color" />

    <input type="date" />

    <input type="email" />

    <input type="file" />

    <!-- Botões multualmente excludentes -->
    <input type="radio" />

    <input type="submit" />

    <input type="time" />

    <input type="url" />

    <textarea rows="10" cols="200">
      Insira aqui um parágrafo
    </textarea>

</form>

```

## Iframe

```html


<iframe src="http://www.site.com/"
         frameborder="0"
         width="1000"
         height="800">
     Aviso: Nem todo website suporta iframe
</iframe>

```

##
