---
title: "Hugo: A Static Site Generator"
date: 2018-08-05
author: "Amintas Victor"
type: "post"
---

A static websites consists of a simple web application where the content exposed is the same for all those who access, such as blogs, journals, portfolios, news portals. However, in WordPress we find a platform too robust for such, already on tumblr. and in the blogger we find the opposite: **that's why we use Hugo, a static site generator**.

<!--more-->

# Prerequisites
Brief notion of HTML and Markdown.

# Setting up Hugo
1. Download and extract Hugo from the ```Hugo/bin/``` directory;
2. Place the ```Hugo/PATH/``` directory.

# Create Site
In the terminal, use the command ```hugo new site site_name```.

# Add Topic
1. In [Hugo Themes](https://themes.gohugo.io/), clone the git theme and put it in the directory ```site_name/themes/```;
2. In ```config.toml```, include the tag:

    >```toml
    >theme = "theme_name"
    >```


3. Additional settings may be required depending on the theme.

# Hosting Locally
In the project root (site), use the command in the terminal: ```hugo server```.

# Create a content file
1. Go to the root of the project
2. Use the command in the terminal ```hugo new file.md``` to create a file in ```content/```;
3. Use the command in the terminal ```hugo new directory/file.md``` to create a file in ```content/directory/```;

The directory tree in ```content/``` matches url navigation.

# Upload draft files (drafts)
In the terminal, use the command: ```hugo server -D```.

# Types of pages
1. Single Pages: Pages responsible for the content of a markdown file;
2. List Pages: Pages responsible for indexing markdown files.

Note: Hugo can index the files located in ```content/``` and its subdirectories. However, it can not index any further. To do this, you must create a ```_index.md``` using the following command in the terminal: ```hugo new content/sub-subdirectory/_index.md```.

# Front Matter
Corresponds to the set of metadata located at the top of the markdown file used for better site organization. They have the following structure:

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

# Archetypes (archetypes)
Front matter default template  when creating a file. If there are modifications, only the new files will be changed. We can create patterns that are not default:

1. Create a new markdown file in archetypes;
2. Create a directory in ```content/``` with the same name as the chosen archetype;
3. Create files in this directory, which will follow the chosen pattern.

# Shortcodes
Instead of writing HTML code, Hugo allows you to use pre-defined shortcuts. Here's the syntax:

1. Without markdown:

    >```markdown
    >{{ < name params > }}
    >```
2. With markdown:

    >```markdown
    >{{ % name params % }}
    >```

# Taxonomy
We can generate links automatically for grouping according to tags and categories (list pages).

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


We can even generate custom taxonomies:

1. In config.toml, we configure:

    >```toml
    >[taxonomies]
    >...
    >mood = "types"
    >```

2. We use the new taxonomy:

    >```markdown
    >---
    >...
    >types: ["type1", ..., "typen"]
    >...
    >---
    >```

# Templates

They are defined in ```layouts/_default/```. In this directory, we are presented to the files responsible for the lists and single pages. More information about templates, [click here](https://gohugo.io/templates/).

# Home Page

Defined by theme as default. But we can define ours in ```layouts/index.html```.

# Section

A directory of content can be indexed from a template itself. To do this, simply create a new HTML file in ```layouts/directory_name/```.

# Base and Blocks

We can make the project more modular and powerful by using the following logic: we have a base that is filled with blocks. We use the following syntax:

1. On the basis:

    >```markdown
    >...
    >{{block "name". }}
    >{{end}}
    >...
    >```

2. In the blocks:

    >```markdown
    >...
    >{{define "name"}}
    >{{end}}
    >...
    > ```

More information about templates, [click here](https://gohugo.io/templates/).

# Variables

In HTML templates we can use what was defined in the markdown header as variables. We use the following syntax:

1. Built-ins:

    >```markdown
    >{{.var}}
    >```

2. Created by us:

    >```markdown
    >{{ .Params.var }}
    >```

We can also define and access variables created in the template itself:

1. Defining:

    >```markdown
    >{{ $ myVar: = value }}
    >```

2. Accessing:

    >```
    >{{ $ myVar }}
    >```

More information about variables, [click here](https://gohugo.io/variables/).

# Functions

We can use functions in HTML through syntax:

  >```markdown
  >{{ function params }}
  >```

Some functions: ```truncate```, ```add```, ```sub```, ```singularize```.

We can perform iterations as follows:

  >```markdown
  >{{ range .array }}
  >...
  >{{ end }}
  >```

More information about functions, [click here](https://gohugo.io/functions/).

# Conditionals

Some operations we can use are: ```and```, ```eq```, ```lt```, ```le```, ```gt```, ```ge```, ```not```. The syntax is as follows:

  >```markdown
  >{{ if params operation }}
  >...
  >{{ else if ... }}
  >...
  >{{ else }}
  >...
  >{{ end }}
  >```

Note: Parentheses can be used for precedence. Also, we can use conditionals in HTML.

# Data

We use the ```data/``` directory to deposit files that serve as a database. These files can be YAML, TOML or JSON. In them, we iterate about their data as follows:

  >```markdown
  >{{ range .Site.Data.File }}
  >```

# Partials

We can modularize the layout as follows:

1. We created the directory ```layouts/partials/```;
2. Create the partial file;
3. Inject templates into ```layouts/_default/```.

At ```partials/header.html```:

  >```markdown
  ><h1> {{ .Title }} </ h1>
  >...
  >```

In ```_default/single.html```:

  >```markdown
  >{{ partial "header". }}
  >...
  >```

We can also handle customizable variables:

At ```partials/header.html```:

  >```markdown
  ><h1> {{ .myTitle }} </h1>
  ><p> {{ .myDate }} </ p>
  >```

In ```_default/single.html```:

  >```markdown
  >{{ partial "header" (dict "myTitle" "TITLE" "myDate" "DD / MM / YYYY") }}
  >```

# Shortcodes

We can paraphrase codes for syntax:

  >```markdown
  >{{ < filename > }}
  >```

We can pass parameters:

1. Referrer:

    >```markdown
    >{{ < shortcode color = 'blue'> }}
    >```

2. Referenced (shortcode):

    >```markdown
    >{{ .Get color }}
    >```

We can define scopes:

1. Referrer:

    >```markdown
    >{{ < shortcode > }}
    >...
    >{{ < shortcode > }}
    >```

2. Referenced (shortcode):

    >```markdown
    >{{ .Inner }}
    >```

We can enter markdown command in referrer scope:

  >```markdown
  >{{ % shortcode % }}
  > ...
  >{{ % shortcode % }}
  > ```

# Building the Site

To generate the site just go to the root of the project and use the following command in the terminal: ```hugo```.
A ```public/``` directory will be generated, now just host it on a web server.
