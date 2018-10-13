---
title: "Linux I: Conhecendo e Usando o Terminal"
date: 2018-06-17T23:59:56-03:00
author: "Amintas Victor"
type: "post"
---

Para aqueles que agora estão sendo introduzidos ao Linux, o manuseio do terminal pode, ao mesmo tempo, fascinar e dar um frio na barriga. A fim de aprender o básico sobre como lidar com essa ferramenta muito importante no uso de qualquer distribuição Linux, e claro, de perdermos qualquer preconceito sobre o prompt de comando, veremos neste artigo os **principais comandos no terminal Linux**

## Arquivos e Diretórios

Para encontrar o diretório atual, use o comando:

```bash
pwd
```
Se quisermos listar os arquivos e diretórios no diretório atual, use o comando:
```bash
ls
```
Da mesma forma, podemos listar os arquivos e diretórios no diretório atual em detalhes através do comando:
```bash
ls -l
```
De maneira similar, podemos incluir na listagem detalhada os arquivos ocultos:
```bash
ls -la
```
Podemos listar os arquivos e diretórios em um diretório específico com o comando:
```bash
ls diretório
```
Podemos imprimir uma mensagem no terminal através do comando:
```bash
echo "message"
```
Podemos criar e sobrescrever um arquivo usando o comando:
```bash
echo "message" > arquivo.extensão
```
Se quisermos ler um arquivo no diretório, mostrando seu conteúdo no terminal, podemos usar o comando:
```bash
cat arquivo.extensão
```
Para limpar a tela, usamos o comando:
```bash
clear
```
Para obter a documentação de um comando em particular, usamos o seguinte comando:
```bash
man command
```
{{< note title="Lembre-se" >}}
Para navegar pela documentação, usamos ```cima``` e ```baixo``` .
Para sair, ```q``` .
{{< /note >}}

Para obter o nome de usuário, usamos o comando:
```bash
whoami
```

## Redirecionamento e Curingas

Para entrar em um diretório, usamos o comando abaixo, onde o PATH do diretório é relativo ao diretório atual.
```bash
cd path
```
Também podemos usar o comando abaixo, onde o PATH do diretório é relativo ao diretório base.
```bash
cd ~/path
```
Usamos o mesmo comando abaixo, onde o PATH do diretório é relativo ao diretório raiz.
```bash
cd home/user/path
```
Adicionamos uma linha a um arquivo com o comando:
```bash
echo "message" >> arquivo.extensão
```
Retorne ao diretório atual usando o comando:
```bash
cd ..
```
Da mesma forma, podemos ir ao diretório de usuários usando o comando:
```bash
cd
```
Algumas referências aos diretórios:

1. Diretório atual: ```.```.
2. Diretório anterior, ou superior: ```..```.
3. Diretório raiz: ```/```.
4. Diretório do usuário: ```/ home```.

Para criar um diretório, usamos o comando:
```bash
mkdir diretório_name
```
Para remover um arquivo, usamos o comando:
```bash
rm arquivo.extensão
```
Para remover um diretório sem subdiretórios, usamos o comando:
```bash
rmdir diretório
```
Para remover um diretório e seus subdiretórios recursivamente, usamos o comando:
```bash
rm -r diretório
```

Aqui estão alguns caracteres curinga no bash:

1. Usamos ```?``` Para representar qualquer caractere.
2. Usamos ```*``` para representar qualquer substring.

## Manipulação e Compactação

Para fazer uma cópia de um arquivo, usamos o seguinte comando:
```bash
cp original.extensão copy.extensão
```

Renomeie um arquivo usando o seguinte comando:
```bash
mv old_name.extensão new_name.extensão
```

Nós movemos os arquivos usando o comando:
```bash
mv arquivo.extensão diretório/
```

Nós também podemos renomear o arquivo movendo-o usando o comando:
```bash
mv old_name.extensão diretório/new_name.extensão
```

Podemos listar os arquivos do diretório corrente e dos subdiretórios recursivamente com o comando:
```bash
ls *
```

Nós fazemos uma cópia de um diretório com o comando:
```bash
cp -r original_diretório copy_diretório
```

Nós podemos compactar um arquivo como zip com o comando:
```bash
zip arquivo_comprimido.zip arquivo.extensão
```

Da mesma forma, podemos "zipar" um diretório recursivamente com o comando:
```bash
zip -r compressed_arquivo.zip diretório/
```

Podemos listar o interior de um arquivo zip com o comando:
```bash
unzip -l arquivo.zip
```

Descompacte um arquivo zip com o comando:
```bash
unzip.zip
```

Nós podemos tornar o processo silencioso com o comando:
```bash
unzip -q arquivo.zip
```

{{< note title="Lembre-se" >}}
Nós podemos combinar flags, então o comando ```zip -r -q arquivo_compactado.zip diretório/``` pode ser escrito como ```zip -rq arquivo_compactado.zip diretório/``` .
{{< /note >}}


## Manipulando .tar

Podemos comprimir usando tar com o seguinte comando:
```bash
tar -cz diretório > arquivo.tar.gz
```

{{< note title="Lembre-se" >}}
Por padrão, esse é um processo recursivo e silencioso.
{{< /note >}}

Podemos descompactar usando tar do seguinte comando:
```bash
tar -xz < arquivo.tar.gz
```

Este mesmo comando pode ser escrito como
```bash
tar -x < arquivo.tar.gz
```

Se não quisermos trabalhar com redirecionamentos de entrada de dados (```<```) e saída de dados (```>```), podemos usar os seguintes comandos:

1. ```tar -czf arquivo.tar.gz diretório/ ```, para comprimir usando tar.
2. ```tar -xzf arquivo.tar.gz``` ou ```tar -xf arquivo.tar.gz```, para descompactar usando tar.
3. ```tar -vczf arquivo.tar.gz diretório/```, para compactar com detalhes usando tar.
4. ```tar -vxzf arquivo.tar.gz``` ou ```tar -vxf arquivo.tar.gz```, para descompactar manualmente usando o tar.

{{< warning title="Atenção" >}}
Na realidade, o tar apenas empacota dados e usa compactadores como o gzip (.gz). Existem outros compactadores externos como o bzip2 (.bz2). Para usá-lo em comandos, simplesmente substitua ```-z``` com ```-j``` e a extensão ```tar.gz``` com ```.tar.bz2```.
{{< /warning >}}

## Metadados e Lendo Arquivos

Podemos alterar a data e hora da última modificação de um arquivo com o comando:
```bash
touch arquivo.extensão
```

Podemos verificar a data e hora atual do sistema com o comando:
```bash
date
```

Podemos exibir dados atuais de data e hora com o comando:
```bash
date "+formato"
```

Use o seguinte comando para ver quais dados podem ser exibidos no terminal:
```bash
date --help
```

Podemos acessar ajuda rápida com os seguintes comandos:
```bash
help command
# ou
--help command
```

Podemos ler as primeiras 10 linhas de um arquivo através do comando:
```bash
head arquivo.extensão
```

Podemos ler as primeiras x linhas de um arquivo através do comando:
```bash
head -n x arquivo.extensão
```

Podemos ler as últimas 10 linhas de um arquivo através do comando:
```bash
tail arquivo.extensão
```

Podemos ler as últimas x linhas de um arquivo através do comando:
```bash
tail -n x arquivo.extensão
```

Nós podemos ler um arquivo inteiro usando o leitor ```less``` via o comando:
```bash
less arquivo.extensão
```

{{< note title="Lembre-se" >}}
Para navegar pelo leitor ```less```, basta usar as setas para cima e para baixo.
{{< /note >}}

## Usando o VI

Para abrir um arquivo com o VI, usamos o comando:
```bash
vi arquivo.extensão
```

Passamos do **modo de navegação e comandos**, que é aberto por padrão, para o **modo de inserção** com ```i``` ou ```a``` e vice-versa com ```esc```.

Para fazer letras maiúsculas fazemos```Shift + letter```, em vez de ```Caps lock```.

Os comandos de edição mais utilizados no **modo de navegação e comandos** estão listados abaixo:

1. ```w```, para salvar.
2. ```q```, para sair. Podemos sair sem salvar com o comando ```q!```.
3. ```x```, para remover o caractere atual. Nós podemos remover n caracteres com o comando ```nx```.
4. ```i```, para inserir no caractere atual.
5. ```a```, para entrar no próximo caractere.
6. ```dd```, para remover a linha atual. Nós podemos remover n linhas com o comando ```ndd```.
7. ```A```, para entrar no final da linha.

Os comandos de navegação mais utilizados no **modo de navegação e comandos** estão listados abaixo:

1. ```G```, para ir para a última linha. Podemos ir para a enésima linha com o comando ```nG```.
2. ```gg```, para ir ao começo do arquivo.
3. ```$```, para ir até o final da linha atual.
4. ```O```, para ir ao começo da linha atual.
5. ```/word```, para procurar uma palavra no texto.
6. ```n```, para ir para a próxima ocorrência.
7. ```N```, para ir para a ocorrência anterior.
8. ```yy```, para copiar a linha atual. Podemos copiar 2 linhas com o comando ```y``` e n linhas com ```nyy```.
9. ```p``` para colar e ```np``` para colar n vezes.

{{< note title="Lembre-se" >}}
Podemos combinar comandos. Por exemplo, para salvar e sair, usamos o comando ```wq```.
{{< /note >}}
