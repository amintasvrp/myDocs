---
title: "LESS: Folha de Estilo Pré-Processadora de CSS"
date: 2018-06-17T23:56:30-03:00
author: "Amintas Victor"
type: "post"
---

## Instalando LESS

Primeiramente devemos instalar o Node.JS e o NPM (Node.JS Package Manager):

```bash
sudo apt update
sudo apt install nodejs
sudo apt install npm
```

Depois, instalamos o LESS em si:

```bash
sudo npm install -g less
```

## Compilando LESS em CSS

Nós escrevemos código em LESS e depois usamos o compilador de LESS para gerar arquivos CSS. Nós compilamos código LESS da seginte forma:

```bash
lessc diretorio/arquivo.less diretorio/arquivo.css
```

Podemos instalar um plug-in, chamado LESS-Watcher, em nosso projeto para que os arquivos LESS seja automaticamente compilados em arquivos CSS. Estando na raiz do projeto, instalamos esse plug-in da seguinte forma:

```bash
sudo npm install less-watcher
```

Para usar o LESS-Watcher basta utilizar o seguinte comando:

```bash
less-watcher -p "" -d diretorios_arquivos_less/
```

## Variáveis

```css

@variavel: blue;

header{
     color: @variavel;
}

footer {
     color: @variavel;
}

button {
     background-color: @variavel;
}

```

## Mixins

```css

.fancy-border(@size: 1px, @color: black) {
     border: @size dashed @color;
}

.fancier-border {
     .fancy-border(10px, blue);
     background-color: yellow;
     border-radius: 5px;
}

```

## Condicionais em Mixins

```css

.p-style(@size) when (@size <= 20) {
     font-size: @size;
     color: red
}

.p-style(@size) when (@size > 20) {
     font-size: @size;
     color: blue
}

p{
     .p-style(30px);
}

```

## Escopo

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

## Operadores

```css

@base-size: 20px;
@base-color: red;

p{
     font-size: @base-size;
     color: @base-color;
}

button {
     font-size: @base-size * 2;
     background-color: @base-color + 200;
}

```

## Importando Arquivos Less

```css

@import "diretorio/nome_do_arquivo"

```
