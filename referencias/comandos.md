# Comandos

...

## cd [`path`](glossario.md#file-path) - Change Directory <a id=cd />

O comando `cd` é utilizado para mudar o diretório atual, para isso basta digitar `cd` seguido do [caminho](glossario.md#file-path) do diretório que deseja acessar, o caminho pode ser absoluto ou relativo.

> ⭐ **Exemplo**
>
> 1. ` Linux e MacOS`
>
>    ```bash
>    cd /pai/filho/neto
>    cd bisneto
>    cd ../..
>    cd ..
>    ``` 
>
> 2. `Windows (powershell)`
>
>    ```powershell
>    cd C:\pai\filho\neto
>    cd bisneto
>    cd ..\..
>    cd ..
>    ```

> 💡 **Dica**
>
> 1. Por padrão, os terminais sempre mostram o diretório atual, para saber em qual diretório você está, basta olhar para o terminal.


## npm init <a id=npm-init />

Cria o arquivo de configuração `package.json` que contém as informações do projeto e as dependências do projeto, ao digitar este comando, o terminal irá fazer algumas perguntas sobre o projeto, como o nome do projeto, a versão, a descrição, o ponto de entrada, o comando de testes, o repositório, as palavras-chave, o autor, a licença e as dependências do projeto.

Para que o comando `npm init` seja executado, sem que seja necessário responder as perguntas, é possível utilizar o comando `npm init -y`, isso criará o arquivo `package.json` com as informações padrão.

> 💡 **Dica**
> 
> 1. Para aceitar o valor padrão sugerido pelo no modo interativo, basta pressionar a tecla `Enter`.

### npm init -y <a id=npm-init-y />

Conforme mencionado anteriormente em [npm init](#npm-init), este comando cria o arquivo de configuração `package.json` com as informações padrão, sem a necessidade de responder as perguntas.

## npm install _(npm i)_ <a id=npm-install />

...

### npm install --save-dev _(npm i -D)_ <a id=npm-install-d />

...

## npm uninstall <a id=npm-uninstall />

...


## npm run <a id=npm-run />

...

## tsc <a id=tsc />

...

### tsc --init <a id=tsc-init />

...

## mkdir [`path`](glossario.md#file-path) <a id=mkdir />

...

## touch <a id=touch />

...

## git init <a id=git-init />

...