---
title: "SASS: CSS com Superpoderes"
date: 2018-06-17T23:51:30-03:00
author: "Amintas Victor"
type: "post"
---

## Instalando SASS

Primeiramente devemos instalar o Ruby, linguagem de programação que implementa SASS, e o gem, gerenciador de pacotes do Ruby. Fazemos ambas as instalações com o seguinte comando:

```bash

sudo apt install ruby

```

Em seguida, basta utilizar o gem para instalar o SASS com o seguinte comando:

```bash

sudo apt install ruby-sass

```

## SASS X SCSS

O framework SASS comporta duas sintaxes para implementação: SASS, que utiliza identações para definir escopos, e SCSS que utiliza chaves e ponto-e-vírgula para definir escopos. Além da sintaxe ambos possuem uma clara diferença: arquivos SCSS são considerados arquivos CSS válidos, não necessitando de conversão; já arquivos SASS precisam ser convertidos para gerar arquivos CSS válidos.

## Pré-Processamento

Nós escrevemos o código em SCSS e utilizamos o SASS-Watcher para automatizar a compilação de arquivos SCSS em arquivos CSS. Para tal, basta utilizar o comando abaixo:

```bash

sass --watch diretorios_arquivos_scss/

```

## Variáveis

```css

$variavel-cor: blue;

header{
     color: $variavel-cor;
}

footer {
     color: $variavel-cor;
}

button {
     background-color: $variavel-cor;
}

```

## Escopos

```css

main {
     background-color: blue;
     p {
          color: red;
     }
     article {
          background-color: yellow;
          p{
               color: green;
          }
     }
}

```

## Importando e Lidando com Parciais

Nós podemos criar arquivos SCSS parciais, que irão compor um arquivo SCSS principal, usando a seguinte sintaxe em seu nome: ```_arquivo.scss```. Arquivos parciais não precisam ser compilados, e de fato não o são !

Podemos importar esse arquivos parciais através da seguinte sintaxe:

```css

@import "diretorio/_arquivo";

```

## Mixins

```css

@mixin fancy-border($size: 1px, $color: black) {
     border: $size dashed $color;
     border-radius: 5px;
}

header {
     @include fancy-border(10px, blue);
     background-color: yellow;
}

```

## Herança

```css

.message {
     font-size: 20px;
     border: 1px solid black;
}

.warning {
     @extend .message;
     color: yellow;
}

.error {
     @extend .message;
     color: red;
}

```

## Operadores

```css

$base-size: 20px;
$base-color: red;

p{
     font-size: $base-size / 2;
     color: $base-color - 10;
}

button {
     font-size: $base-size * 2;
     background-color: $base-color + 200;
}

```

## Condicionais

```css

@mixin text-style($size) {
    font-size: $size;

    @if $size > 20px {
         color: blue;
    } @elseif $size = 20px {
         color: red;
    } @else {
         color:green;
    }

}

header {
    @include text-style(21px);
}

```
