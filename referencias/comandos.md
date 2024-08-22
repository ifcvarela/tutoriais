# Comandos

## Comandos NPM

### npm init <a id=npm-init />

Cria o arquivo de configuração `package.json` que contém as informações do projeto e as dependências do projeto, ao digitar este comando, o terminal irá fazer algumas perguntas sobre o projeto, como o nome do projeto, a versão, a descrição, o ponto de entrada, o comando de testes, o repositório, as palavras-chave, o autor, a licença e as dependências do projeto.

Para que o comando `npm init` seja executado, sem que seja necessário responder as perguntas, é possível utilizar o comando `npm init -y`, isso criará o arquivo `package.json` com as informações padrão.

> 💡 **Dica**
> 
> 1. Para aceitar o valor padrão sugerido pelo no modo interativo, basta pressionar a tecla `Enter`.

#### npm init -y <a id=npm-init-y />

Conforme mencionado anteriormente em [npm init](#npm-init), este comando cria o arquivo de configuração `package.json` com as informações padrão, sem a necessidade de responder as perguntas.

### npm install `pacote(s)` _(abreviação: npm i `pacote(s)`)_ <a id=npm-install />

O comando `npm install` é utilizado para instalar pacotes no projeto, para isso basta digitar `npm install` seguido do nome do pacote que deseja instalar, o pacote pode ser um pacote do [npm](https://www.npmjs.com/), um pacote local ou um pacote remoto.

Na pratica, o comando `npm install` cria uma pasta chamada `node_modules` no diretório do projeto e instala os pacotes nessa pasta, além disso, o comando `npm install` adiciona as dependências do projeto no arquivo `package.json`, na seção `dependencies`.

É possivel instalar mais de um pacote de uma só vez, para isso basta digitar `npm install` seguido dos nomes dos pacotes separados por espaço.

> ⭐ **Exemplo**
>
> ```bash
> npm install express
> npm install express sqlite sqlite3
> ```

É possível executar uma versão abreviada do `install`, para isso basta digitar `npm i` seguido do nome do pacote que deseja instalar.

> ⭐ **Exemplo**
>
> ```bash
> npm i express
> npm i express sqlite sqlite3
> ```

#### npm install `pacote(s)` --save-dev _(abreviação: npm i -D)_ <a id=npm-install-d />

O comando `npm install` com a flag `--save-dev` é utilizado para instalar pacotes de desenvolvimento no projeto, para isso basta digitar `npm install` seguido do nome do pacote que deseja instalar e da flag `--save-dev`, o pacote pode ser um pacote do [npm](https://www.npmjs.com/), um pacote local ou um pacote remoto.

Na pratica, o comando `npm install` com a flag `--save-dev` cria uma pasta chamada `node_modules` no diretório do projeto e instala os pacotes nessa pasta, além disso, o comando `npm install` com a flag `--save-dev` adiciona as dependências de desenvolvimento do projeto no arquivo `package.json`, na seção `devDependencies`.

É possivel instalar mais de um pacote de uma só vez, para isso basta digitar `npm install` seguido dos nomes dos pacotes separados por espaço.

> ⭐ **Exemplo**
>
> ```bash
> npm install nodemon --save-dev
> npm install ts-node typescript @types/express --save-dev
> ```

É possível executar uma versão abreviada do `install`, para isso basta digitar `npm i` da flag `-D` e seguido do nome do pacote que deseja instalar.

> ⚠️ **Atenção**
>
> 1. O parametro abrevido `-D` é uma abreviação para `--save-dev` e precisa necessariamente ser escrito em maiúsculo.
> 2. Os pacotes de desenvolvimento são pacotes que são necessários apenas durante o desenvolvimento do projeto, como por exemplo, pacotes de testes, pacotes de compilação, pacotes de transpilação, etc.

> ⭐ **Exemplo**
> 
> ```bash
> npm i -D nodemon
> npm i -D ts-node typescript @types/express
> ```


### npm uninstall `pacote(s)` _(npm un `pacote(s)`)_ <a id=npm-uninstall />

O comando `npm uninstall` é utilizado para desinstalar pacotes do projeto, para isso basta digitar `npm uninstall` seguido do nome do pacote que deseja desinstalar, o pacote pode ser um pacote do [npm](https://www.npmjs.com/), um pacote local ou um pacote remoto.

Na pratica, o comando `npm uninstall` remove a pasta do pacote da pasta `node_modules` no diretório do projeto, além disso, o comando `npm uninstall` remove as dependências do projeto no arquivo `package.json`, na seção `dependencies` ou `devDependencies`.


### npm run `script` <a id=npm-run />

O comando `npm run` é utilizado para executar scripts definidos no arquivo `package.json`, para isso basta digitar `npm run` seguido do nome do script que deseja executar.

> ⭐ **Exemplo**
>
> ```json
> {
>   "scripts": {
>     "start": "node index.js",
>     "dev": "nodemon index.js",
>     "build": "tesc -p tsconfig.json"
>   }
> }
> ```
>
> ```bash
> npm start
> npm run dev
> npm run build
> ```

atenção
> ⚠️ **Atenção**
>
> 1. O script `start` é um script padrão do `npm`, que é executado com o comando `npm start`, note que não é necessário utilizar o comando `run` para executar o script `start`. 


## Comandos Typescript

### tsc <a id=tsc />

O comando `tsc` é utilizado para compilar arquivos `.ts` para arquivos `.js`, para isso basta digitar `tsc`, caso queira compilar um arquivo específico, basta digitar `tsc` seguido do nome do arquivo que deseja compilar.

É importante ressaltar que o comando `tsc` irá compilar o arquivo `.ts` para `.js` utilizando as configurações do arquivo `tsconfig.json`.

> ⭐ **Exemplo**
>
> ```bash
> tsc
> tsc index.ts
> ```

Para saber outras possibilidades de uso do comando `tsc`, acesse a [documentação oficial do Typescript](https://www.typescriptlang.org/docs/handbook/compiler-options.html).

#### tsc --init <a id=tsc-init />

O comando `tsc --init` é utilizado para criar o arquivo de configuração `tsconfig.json`, que contém as configurações do compilador do Typescript, ao digitar este comando, o terminal irá criar um arquivo `tsconfig.json` com as configurações padrão.

## Comandos Git

### git init <a id=git-init />

O comando `git init` é utilizado para iniciar um repositório git em um diretório, para isso basta digitar `git init` no diretório que deseja iniciar o repositório.

## Comandos GNU/Linux

### cd [`path`](glossario.md#file-path) - Change Directory <a id=cd />

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

Para mais detalhes sobre o comando acesse a [documentação GNU para o cd](https://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html).


### mkdir [`path`](glossario.md#file-path) <a id=mkdir />

O comando `mkdir` é utilizado para criar diretórios, para isso basta digitar `mkdir` seguido do nome do diretório que deseja criar.

> ⭐ **Exemplo**
>
> ```bash
> mkdir src
> mkdir src/routes
> mkdir src/controllers
> mkdir src/models
> ```

Mais detalhes para o comando acesse a [documentação GNU para o mkdir](https://www.gnu.org/software/coreutils/manual/html_node/mkdir-invocation.html).

### touch [`path`](glossario.md#file-path) <a id=touch />

O comando touch é um comando utilizado em sistemas Unix e Unix-like (Linux, MacOS, FreeBSD etc) para criar arquivos vazios ou atualizar a data de modificação de arquivos existentes. Ele é comumente usado para criar novos arquivos, mas também pode ser usado para alterar a data de modificação de um arquivo existente.

> ⭐ **Exemplo**
>
> ```bash
> touch index.html
> touch style.css
> touch script.js
> ```

Touch não é compatível com o Windows, mas é facilmente substituído pelo comando `echo` ou `ni` (New-Item).

> ⭐ **Exemplo**
>
> 1. Para Windows anterior ao Windows 10
>     ```powershell
>     echo $null >> index.html
>     echo $null >> style.css
>     echo $null >> script.js
>     ```
> 2. Para Windows 10 e superiores
>     ```powershell
>     ni index.html
>     ni style.css
>     ni script.js
>     ```

Mais detalhes para o comando acesse a [documentação GNU para o touch](https://www.gnu.org/software/coreutils/manual/html_node/touch-invocation.html).