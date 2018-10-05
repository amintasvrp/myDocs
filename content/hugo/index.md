---
title: "Hugo: Um Gerador de Sites Estáticos"
date: 2018-08-05
author: "Amintas Victor"
type: "post"
---

Um site estático consiste em um aplicativo da Web simples, no qual o conteúdo exposto é o mesmo para todos os que acessam, como blogs, periódicos, portfólios e portais de notícias. No entanto, no **WordPress** encontramos uma plataforma muito robusta para tal, já no **tumblr** e no **blogger** encontramos o oposto: é por isso que usamos o **Hugo, um gerador de site estático**.

## Pré-requisitos
Breves noções de HTML e Markdown.

## Configurando Hugo
1. Baixe e extraia o Hugo do diretório ```Hugo/bin/```;
2. Vá para o diretório ```Hugo/PATH/```.

## Criando o Site
No terminal, use o comando ```hugo new site site_name```.

## Adicionar Tópico
1. Em [Hugo Themes](https://themes.gohugo.io/), clone o repositório git do tema e ponha-o no diretório ```site_name/themes/```;
2. Em ```config.toml```, inclua a tag:

    >```toml
    >theme = "theme_name"
    >```

3. Configurações adicionais podem ser necessárias dependendo do tema.

## Hospedando Localmente
Na raiz do projeto (site), use o comando no terminal: ```hugo server```.

## Criando Arquivo de Conteúdo
1. Vá para a raiz do projeto;
2. Use o comando no terminal ```hugo new file.md``` para criar um arquivo em ```content/```;
3. Use o comando no terminal ```hugo new directory/file.md``` para criar um arquivo em ```content/directory/```.

A árvore de diretórios em ```content/``` corresponde à navegação nas URLs.

## Carregando Rascunhos
In the terminal, use the command: ```hugo server -D```.

## Tipos de Páginas
1. Single Pages: Páginas responsáveis ​​pelo conteúdo de um arquivo Markdown;
2. List Pages: Páginas responsáveis ​​por indexar arquivos Markdown.

{{< note title="Lembre-se" >}}
Hugo pode indexar os arquivos localizados em ```content/``` e seus subdiretórios. No entanto, não pode indexar mais. Para fazer isso, você deve criar um arquivo ```_index.md``` usando o seguinte comando no terminal: ```hugo new content/sub-subdiretório/ _index.md```.
{{< /note >}}


## Front Matter
Corresponde ao conjunto de metadados localizado na parte superior do arquivo de remarcação usado para melhorar a organização do site. Eles têm a seguinte estrutura:

1. YAML:

    >```yaml
    >---
    >config: value
    >---
    >```

2. TOML:

    >```toml
    >config = value
    >```

3. JSON:

    >```json
    >{
    >config: value
    >}
    >```

## Arquétipos
Modelo padrão do Front Matter ao criar um arquivo. Se houver modificações, somente os novos arquivos serão alterados. Podemos criar padrões que não são padrão:

1. Crie um novo arquivo Markdown em ```archetypes/```;
2. Crie um diretório em ```content/``` com o mesmo nome do arquétipo escolhido;
3. Crie arquivos nesse diretório, que seguirá o padrão escolhido.

## Shortcodes
Em vez de escrever código HTML, Hugo permite que você use atalhos pré-definidos. Aqui está a sintaxe:

1. Sem Markdown:

    >```markdown
    >{{ < name params > }}
    >```
2. Com Markdown:

    >```markdown
    >{{ % name params % }}
    >```

Podemos parafrasear códigos para sintaxe:

  >```markdown
  >{{ < filename > }}
  >```

Nós podemos passar parâmetros:

1. Referenciador:

    >```markdown
    >{{ < shortcode color = 'blue'> }}
    >```

2. Referenciado (shortcode):

    >```markdown
    >{{ .Get color }}
    >```

Podemos definir escopos:

1. Referenciador:

    >```markdown
    >{{ < shortcode > }}
    >...
    >{{ < shortcode > }}
    >```

2. Referenciado (shortcode):

    >```markdown
    >{{ .Inner }}
    >```

Podemos inserir o comando markdown no escopo do referenciador:

  >```markdown
  >{{ % shortcode % }}
  > ...
  >{{ % shortcode % }}
  >```

## Taxonomia
Podemos gerar links automaticamente para agrupamento de acordo com tags e categorias (list pages).

1. Tags:

    >```markdown
    >---
    >....
    >tags: ["t1", ..., "tn"]
    >...
    >---
    >```
2. Categories:

    >```markdown
    >---
    >...
    >categories: ["c1", ..., "cn"]
    >...
    >---
    >```


Podemos até gerar taxonomias personalizadas:

1. No config.toml, nós configuramos:

    >```toml
    >[taxonomies]
    >...
    >mood = "types"
    >```

2. E nós usamos a nova taxonomia dessa forma:

    >```markdown
    >---
    >...
    >types: ["type1", ..., "typen"]
    >...
    >---
    >```

## Modelos (Templates)

Eles são definidos em ```layouts/_default/```. Neste diretório, somos apresentados aos arquivos responsáveis ​​pelas listas e páginas únicas. Mais informações sobre templates, [clique aqui] (https://gohugo.io/templates/).

## Pagina Inicial

Definido por tema como padrão. Mas nós podemos definir o nosso em ```layouts/index.html```.

## Seção

Um diretório de conteúdo pode ser indexado a partir de um modelo em si. Para fazer isso, simplesmente crie um novo arquivo HTML em ```layouts/diretório/```.

## Base e Blocos

Podemos tornar o projeto mais modular e poderoso usando a seguinte lógica: temos uma base que é preenchida com blocos. Nós usamos a seguinte sintaxe:

1. Na Base:

    >```markdown
    >...
    >{{block "name". }}
    >{{end}}
    >...
    >```

2. Nos Blocos:

    >```markdown
    >...
    >{{define "name"}}
    >{{end}}
    >...
    > ```

Mais informações sobre templates, [clique aqui] (https://gohugo.io/templates/).

## Variáveis

Nos modelos HTML, podemos usar o que foi definido no cabeçalho da marcação como variáveis. Nós usamos a seguinte sintaxe:

1. Built-ins:

    >```markdown
    >{{.var}}
    >```

2. Personalizadas:

    >```markdown
    >{{ .Params.var }}
    >```

Também podemos definir e acessar variáveis ​​criadas no próprio modelo:

1. Definindo:

    >```markdown
    >{{ $ myVar: = value }}
    >```

2. Acessando:

    >```
    >{{ $ myVar }}
    >```

Mais informações sobre variáveis, [clique aqui] (https://gohugo.io/variables/).

## Funções

Podemos usar funções em HTML por meio da sintaxe:

  >```markdown
  >{{ function params }}
  >```

Algumas funções: ```truncate```, ```add```, ```sub```, ```singularize```.

Podemos executar iterações da seguinte maneira:

  >```markdown
  >{{ range .array }}
  >...
  >{{ end }}
  >```

Mais informações sobre funções, [clique aqui] (https://gohugo.io/functions/).

## Conditionals

Algumas operações que podemos usar são: ```and```, ```eq```, ```lt```, ```le```, ```gt```, ```ge```, ```not```. A sintaxe é a seguinte:

  >```markdown
  >{{ if params operation }}
  >...
  >{{ else if ... }}
  >...
  >{{ else }}
  >...
  >{{ end }}
  >```

{{< note title="Lembre-se" >}}
Os parênteses podem ser usados ​​para precedência. Além disso, podemos usar condicionais em HTML.
{{< /note >}}

## Banco de Dados

Usamos o diretório ```data/``` para depositar arquivos que servem como banco de dados. Esses arquivos podem ser YAML, TOML ou JSON. Neles, nós iteramos sobre seus dados da seguinte forma:

  >```markdown
  >{{ range .Site.Data.File }}
  >```

## Parciais

Podemos modularizar o layout da seguinte forma:

1. Criamos o diretório ```layouts/partials/```;
2. Crie o arquivo parcial;
3. Injete templates em ```layouts/_default/```.

Em ```partials/header.html```:

  >```markdown
  ><h1> {{ .Title }} </ h1>
  >...
  >```

Em ```_default/single.html```:

  >```markdown
  >{{ partial "header". }}
  >...
  >```

Também podemos manipular variáveis ​​personalizáveis:

Em ```partials/header.html```:

  >```markdown
  ><h1> {{ .myTitle }} </h1>
  ><p> {{ .myDate }} </ p>
  >```

Em ```_default/single.html```:

  >```markdown
  >{{ partial "header" (dict "myTitle" "TITLE" "myDate" "DD / MM / YYYY") }}
  >```

## Construindo o Site

Para gerar o site, basta acessar a raiz do projeto e usar o seguinte comando no terminal: ```hugo```.
Um diretório ```public/``` será gerado, agora basta hospedá-lo em um servidor web.
