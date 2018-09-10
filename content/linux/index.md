---
title: "Linux I: Conhecendo e Usando o Terminal"
date: 2018-08-09T21:19:00-03:00
author: "Amintas Victor"
type: "post"
---

Para aqueles que agora estão sendo introduzidos ao Linux, o manuseio do terminal pode, ao mesmo tempo, fascinar e dar um frio na barriga. A fim de aprender o básico sobre como lidar com essa ferramenta muito importante no uso de qualquer distribuição Linux, e claro, de perdermos qualquer preconceito sobre o prompt de comando, veremos neste artigo os **principais comandos no terminal Linux**

## Trabalhando com arquivos e diretórios

1. Para encontrar o diretório atual, use o comando ```pwd```.
2. Se quisermos listar os arquivos e diretórios no diretório atual, use o comando ```ls```.
  1. Da mesma forma, podemos listar os arquivos e diretórios no diretório atual em detalhes através do comando ```ls -l```.
  2. De maneira similar, podemos incluir na listagem detalhada os arquivos ocultos: ```ls -la```.
  3. Podemos listar os arquivos e diretórios em um diretório específico com o comando ```ls directory```.
3. Podemos imprimir uma mensagem no terminal através do comando ```echo" message "```.
4. Podemos criar e sobrescrever um arquivo usando o comando ```echo "message" > file.extension```.
5. Se quisermos ler um arquivo no diretório, mostrando seu conteúdo no terminal, podemos usar o comando ```cat file.extension```.
6. Para limpar a tela, usamos o comando ```clear```.
7. Para obter a documentação de um comando em particular, usamos o seguinte comando: ```man command```. Para navegar pela documentação, usamos as setas para cima e para baixo e ```q``` para sair.
8. Para obter o nome de usuário, usamos o comando ```whoami```.

## Mais sobre os caracteres de redirecionamento e curingas no bash

1. Para entrar em um diretório, usamos o comando ```cd path```, onde o PATH do diretório é relativo ao diretório atual.
  1. Também podemos usar o comando ```cd ~/path```, onde o PATH do diretório é relativo ao diretório base.
  2. Usamos o mesmo comando ```cd home/user/path```, onde o PATH do diretório é relativo ao diretório raiz.
2. Adicionamos uma linha a um arquivo com o comando ```echo "message" >> file.extension```.
3. Retorne ao diretório atual usando o comando ```cd ..```. Da mesma forma, podemos ir ao diretório de usuários usando o comando ```cd```.
4. Algumas referências aos diretórios:
  1. Diretório atual: ```.```.
  2. Diretório anterior, ou superior: ```..```.
  3. Diretório raiz: ```/```.
  4. Diretório do usuário: ```/ home```.
5. Para criar um diretório, usamos o comando: ```mkdir directory_name```.
6. Para remover um arquivo, usamos o comando ```rm file.extension```.
7. Para remover um diretório sem subdiretórios, usamos o comando ```rmdir directory```.
8. Para remover um diretório e seus subdiretórios recursivamente, usamos o comando ```rm -r directory```.
9. Aqui estão alguns caracteres curinga no bash:
  1. Usamos ```?``` Para representar qualquer personagem.
  2. Usamos ```*``` para representar qualquer substring.

## Manipulando, compactando e descompactando arquivos

1. Para fazer uma cópia de um arquivo, usamos o seguinte comando: ```cp original.extension copy.extension```.
2. Renomeie um arquivo usando o seguinte comando: ```mv old_name.extension new_name.extension```.
3. Nós movemos os arquivos usando o comando ```mv file.extension directory /```. Nós também podemos renomear o arquivo movendo-o usando o comando ```mv old_name.extension directory/new_name.extension```.
4. Podemos listar os arquivos do diretório corrente e dos subdiretórios recursivamente com o comando ```ls *```.
5. Nós fazemos uma cópia de um diretório com o comando ```cp -r original_directory copy_directory```.
6. Nós podemos compactar um arquivo como zip com o comando ```zip arquivo_comprimido.zip arquivo.extensão```. Da mesma forma, podemos "zipar" um diretório recursivamente com o comando ```zip -r compressed_file.zip directory /```.
7. Podemos listar o interior de um arquivo zip com o comando ```unzip -l file.zip```.
8. Descompacte um arquivo zip com o comando ```unzip.zip```. Nós podemos tornar o processo silencioso com o comando ```unzip -q file.zip```.

Nota: Nós podemos combinar flags, então o comando ```zip -r -q arquivo_compactado.zip diretório /``` pode ser escrito como ```zip -rq compressed_file.zip directory /```.

## Compactando e descompactando o tar

1. Podemos comprimir usando tar do seguinte comando: ```tar -cz directory > file.tar.gz```. Por padrão, esse é um processo recursivo e silencioso.
2. Podemos descompactar usando tar do seguinte comando: ```tar -xz < file.tar.gz```. Este mesmo comando pode ser escrito como ```tar -x < file.tar.gz```.
3. Se não quisermos trabalhar com redirecionamentos de entrada de dados (```<```) e saída de dados (```>```), podemos usar os seguintes comandos:
  1. ```tar -czf file.tar.gz directory/ ```, para comprimir usando tar.
  2. ```tar -xzf file.tar.gz``` ou ```tar -xf file.tar.gz```, para descompactar usando tar.
  3. ```tar -vczf file.tar.gz directory/```, para compactar com detalhes usando tar.
  4. ```tar -vxzf file.tar.gz``` ou ```tar -vxf file.tar.gz```, para descompactar manualmente usando o tar.

Nota: Na realidade, o tar apenas empacota dados e usa compactadores como o gzip (.gz). Existem outros compactadores externos como o bzip2 (.bz2). Para usá-lo em comandos, simplesmente substitua ```-z``` com ```-j``` e a extensão ```tar.gz``` com ```.tar.bz2```.

## Mais sobre compressão e descompactação e comandos de terminal

1. Podemos alterar a data e hora da última modificação de um arquivo com o comando ```touch file.extension```.
2. Podemos verificar a data e hora atual do sistema com o comando ```date```.
3. Podemos exibir dados atuais de data e hora com o comando ```date "+formato"```. Use o comando ```date --help``` para ver quais dados podem ser exibidos no terminal.
4. Podemos acessar ajuda rápida com o comando ```help command``` ou ``` --help command```.
5. Podemos ler as primeiras 10 linhas de um arquivo através do comando ```head file.extension```. Podemos ler as primeiras x linhas de um arquivo através do comando ```head -n x file.extension```.
6. Podemos ler as últimas 10 linhas de um arquivo através do comando ```tail file.extension```. Podemos ler as últimas x linhas de um arquivo através do comando ```tail -n x file.extension```.
7. Nós podemos ler um arquivo inteiro usando o leitor ```less``` via o comando ```less arquivo.extensão```. Para navegar pelo leitor, basta usar as setas para cima e para baixo.

## Editando arquivos com o VI: inclusão, alteração, exclusão, repetição

1. Para abrir um arquivo com o VI, usamos o comando ```file.extension```.
2. Passamos do **modo de navegação e comandos**, que é aberto por padrão, para o **modo de inserção** com ```i``` ou ```a``` e vice-versa com ```esc```.
3. Para fazer letras maiúsculas fazemos```Shift + letter```, em vez de ```Caps lock```.
4. Os comandos de edição mais utilizados no **modo de navegação e comandos** estão listados abaixo:
  1. ```w```, para salvar.
  2. ```q```, para sair. Podemos sair sem salvar com o comando ```q!```.
  3. ```x```, para remover o caractere atual. Nós podemos remover n caracteres com o comando ```nx```.
  4. ```i```, para inserir no caractere atual.
  5. ```a```, para entrar no próximo caractere.
  6. ```dd```, para remover a linha atual. Nós podemos remover n linhas com o comando ```ndd```.
  7. ```A```, para entrar no final da linha.
5. Os comandos de navegação mais utilizados no **modo de navegação e comandos** estão listados abaixo:
  1. ```G```, para ir para a última linha. Podemos ir para a enésima linha com o comando ```nG```.
  2. ```gg```, para ir ao começo do arquivo.
  3. ```$```, para ir até o final da linha atual.
  4. ```O```, para ir ao começo da linha atual.
  5. ```/word```, para procurar uma palavra no texto.
  6. ```n```, para ir para a próxima ocorrência.
  7. ```N```, para ir para a ocorrência anterior.
  8. ```yy```, para copiar a linha atual. Podemos copiar 2 linhas com o comando ```y``` e n linhas com ```nyy```.
  9. ```p``` para colar e ```np``` para colar n vezes.

Nota: podemos combinar comandos. Por exemplo, para salvar e sair, usamos o comando ```wq```.
