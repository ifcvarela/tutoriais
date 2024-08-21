# CRUD (Create, Read, Update e Delete) com Typescript, Node.js/Express e SQLite

Este documento tem como objetivo guiar o desenvolvimento de um projeto de CRUD (Create, Read, Update e Delete) utilizando TypeScript, Node.js/Express e SQLite.

## Pré-requisitos

### Softwares necessários

1. Visual Studio Code (VSCode) [site oficial](https://code.visualstudio.com/)
2. Node.js e NPM [site oficial](https://nodejs.org/) 

### Conhecimentos necessários

1. Conhecimento básico de JavaScript
- sintaxe básica do javascript e variáveis [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Grammar_and_types)
- funções [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Functions)
- objetos [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_objects)
- arrays [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array)
- Atribuição via desestruturação [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- assíncrono/promessas/async/await [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Using_promises)
- arrow functions [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- import/export [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/import)
2. Conhecimento básico de TypeScript
- tipos [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/basic-types.html)
3. Conhecimento básico de Node.js
4. HTTP e RESTful APIs
- protocolo HTTP [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP)
  - métodos HTTP [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods)
  - códigos de status HTTP [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)
- APIs RESTful [restfulapi.net](https://restfulapi.net/)
4. Conhecimento básico de SQL/SQLite
- comandos de criação de tabelas [SQLite Docs](https://www.sqlite.org/lang_createtable.html)
- comandos de inserção de dados [SQLite Docs](https://www.sqlite.org/lang_insert.html)
- comandos de seleção de dados [SQLite Docs](https://www.sqlite.org/lang_select.html)
- comandos de atualização de dados [SQLite Docs](https://www.sqlite.org/lang_update.html)

## Criando ambiente de desenvolvimento

Nesta sessão será apresentado o passo a passo para a criação do ambiente de desenvolvimento, com a instalação das dependências necessárias para o projeto e a criação dos arquivos de configuração bem como os scripts de execução e arquivos iniciais do projeto.

Chamamos de ambiente de desenvolvimento o conjunto de ferramentas e configurações necessárias para o desenvolvimento de um projeto, neste caso, o ambiente de desenvolvimento será criado para um projeto Node.js com TypeScript, Express e SQLite.

### Abra o VSCode e crie uma nova pasta para o projeto

1. Crie uma nova pasta em um local de sua preferência (_utilizando o explorador de arquivos do sistema operacional ou o próprio VSCode_)
2. Clique em `File` > `Open Folder...`
3. Navegue até a pasta criada
4. Clique em `Select Folder`

### Abra o terminal do VSCode

1. Clique em `view > Terminal` ou o atalho `Ctrl + '` 
  - _note que o caminho `terminal` > `new terminal` ou o atalho `Ctrl + Shift + '` também pode ser utilizado, porém deta forma sempre cria um novo terminal, enquanto a primeira forma abre o terminal já existente ou cria um se necessário._

### Inicie um novo projeto Node.js
 
1. Execute o seguinte comando no terminal:

```bash
npm init -y
```

### Instale as dependências do projeto: Express, SQLite
  
1. Execute o seguinte comando no terminal:

```bash
npm install express sqlite sqlite3
```	

### Instale as dependências de desenvolvimento do projeto: TypeScript, ts-node, nodemon

1. Execute o seguinte comando no terminal:

```bash
npm install typescript ts-node nodemon @types/node @types/express
```

### Crie o arquivo de configuração do TypeScript
  
1. Execute o seguinte comando no terminal:

```bash
npx tsc --init
```

### Configure o TypeScript para compilar o código para a pasta `dist`
  
1. Abra o arquivo `tsconfig.json`
2. Altere a propriedade `outDir` para `./dist`  
  - _note que é necessário remover o comentário `//` da linha_
3. Salve e feche o arquivo

### Crie os scripts de execução do projeto

1. Abra o arquivo `package.json`
2. Adicione os scripts abaixo:
  ```json
  "scripts": {
    "start": "node dist/index.js",
    "dev": "nodemon src/index.ts",
    "build": "tsc"
  }
  ```
3. Salve e feche o arquivo

### Crie as pastas necessárias para o projeto
  
O objetivo neste momento é criar as pastas `src` e `public` na raiz do projeto, e os arquivos `index.ts` e `database.ts` dentro da pasta `src`.

1. Crie uma pasta chamada `src`
2. Crie uma pasta chamada `public`
3. Crie um arquivo chamado `index.ts` dentro da pasta `src`
4. Crie um arquivo chamado `database.ts` dentro da pasta `src`
5. Crie um arquivo chamado `index.html` dentro da pasta `public`
6. Crie um arquivo chamado `main.css` dentro da pasta `public`
7. Crie um arquivo chamado `main.js` dentro da pasta `public`

A estrutura de pastas e arquivos criada deve estar organizada da seguinte forma:

```plaintext
PASTA-DO-SEU-PROJETO
├── public
│   ├── index.html
│   ├── main.css
│   └── main.js
├── src
│   ├── database.ts
│   └── index.ts
```

Existem várias formas de criar pastas e arquivos, abaixo estão listadas algumas formas de criar as pastas e arquivos necessários para o projeto, escolha a forma que preferir.

#### _OPÇÃO 1 [escolha do autor]_ - Utilizando o Terminal

O terminal do VScode é uma ferramenta poderosa que permite a execução de comandos diretamente no sistema operacional, porém os terminais do Windows e do Linux possuem comandos diferentes para a criação de pastas e arquivos, escolha o comando correspondente ao seu sistema operacional:

##### Windows (powershell)

1. Execute os seguintes comandos no terminal:

```bash
mkdir src
mkdir public
echo > src/index.ts
echo > src/database.ts
echo > public/index.html
echo > public/main.css
echo > public/main.js
```

##### Linux (bash)

1. Execute os seguintes comandos no terminal:

```bash
mkdir src
mkdir public
touch src/index.ts
touch src/database.ts
touch public/index.html
touch public/main.css
```

#### _OPÇÃO 2_ - Utilizando o explorador de arquivos do VSCode

Abra o menu lateral do VSCode, você pode fazer isso pelo caminho `View > Explorer` ou pressionando `Ctrl + Shift + E`, em seguida clique com o botão direito do mouse na pasta raiz do projeto e selecione a opção `New Folder`, repita o processo para criar as pastas `src` e `public`, em seguida clique com o botão direito do mouse na pasta `src` e selecione a opção `New File`, repita o processo para criar os arquivos `index.ts` e `database.ts`.

> também existe a possibilidade de criar pastas utilizando os icones localizados na parte superior do menu lateral do VSCode, clique no icone ![new-file](/README/new-file.png) para criar um novo arquivo ou no icone ![new-folder](/README/new-folder.png) para criar uma nova pasta.

#### _OPÇÃO 3_ - Utilizando o explorador de arquivos do sistema operacional

Se preferir, você pode criar as pastas e arquivos manualmente, utilizando o explorador de arquivos do sistema operacional.

Neste documento não será abordado como criar pastas e arquivos manualmente, pois a forma de fazer isso varia de acordo com o sistema operacional utilizado, porém, você pode consultar a documentação do sistema operacional utilizado para obter mais informações sobre como criar pastas e arquivos.

### REVISÃO: Criando ambiente de desenvolvimento

Ao terminar esta sessão, você terá um ambiente de desenvolvimento configurado para um projeto Node.js com TypeScript, Express e SQLite, com os scripts de execução `start`, `dev` e `build` configurados e prontos para serem utilizados.

Sua estrutura de pastas e arquivos deve estar organizada da seguinte forma neste momento:

```plaintext
PASTA-DO-SEU-PROJETO
├── node_modules
├── public
├── src
│   ├── database.ts
│   └── index.ts
├── package-lock.json
├── package.json
└── tsconfig.json
```

> #### Dica: Mantenha o projeto versionado com GIT
>
> 1. inicie o projeto como sendo um repositório git, para isso certifique que você tenha o git instalado em sua máquina e execute o comando `git init` no terminal do VSCode.
> 2. Crie um arquivo `.gitignore` na raiz do projeto e adicione a pasta `node_modules`, `dist` e o arquivo `database.sqlite` para serem ignorados pelo git, _o arquivo `.gitignore` deve conter as seguintes linhas:_
>  ```plaintext
>  node_modules/
>  dist/
>  database.sqlite
>  ```
> 3. Faça o primeiro commit do projeto, utilizando o comando `git add --all` e `git commit -m "primeiro commit"`.
> 4. Nas próximas sessões deste documento, explicaremos como criar um repositorio remoto no GitHub e como enviar o código para o repositório remoto.
>
> _Para mais informações sobre o git, consulte a documentação oficial em [git-scm.com](https://git-scm.com/)._

## Criando o arquivo de conexão com o banco de dados

Nesta sessão será apresentado o passo a passo para a criação do arquivo de conexão com o banco de dados SQLite, com a criação de uma tabela de exemplo e a inserção de dados na tabela.

no arquivo `database.ts` adicione o seguinte código:

```typescript	
// 1. Importa as bibliotecas necessárias
import sqlite from 'sqlite'
import sqlite3 from 'sqlite3'

// 2. Declara uma variável para armazenar a instância do banco de dados
let instance: sqlite.Database | null = null

// 3. Exporta uma função para conectar ao banco de dados
export async function connect() {
  // 4. Verifica se a instância do banco de dados já foi criada
  if (instance) return instance

  // 5. Abre uma conexão com o banco de dados SQLite
  const db = await sqlite.open({
    filename: './database.sqlite',
    driver: sqlite3.Database
  })

  // 6. Executa um comando SQL para criar a tabela `users`
  await db.exec(`
    CREATE TABLE IF NOT EXISTS users (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      name TEXT NOT NULL,
      email TEXT NOT NULL
    )
  `)

  // 7. Atribui a instância do banco de dados à variável `instance`
  instance = db

  // 8. Retorna a instância do banco de dados
  return db
}
```

### Entendendo o código

1. Importa as bibliotecas necessárias
  - `sqlite` é a biblioteca que será utilizada para conectar ao banco de dados SQLite
  - `sqlite3` é uma biblioteca escreita em TypeScript que fornece uma interface para o banco de dados SQLite adicionando suporte para promessas, tipagem, migrações e muito mais, [sqlite3](https://www.npmjs.com/package/sqlite3)
  - para entender como a sintaxe `import` funciona, consulte a documentação oficial em [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/import)
2. Declara uma variável para armazenar a instância do banco de dados
  - `instance` é uma variável que armazenará a instância do banco de dados, a fim de evitar que a conexão seja aberta mais de uma vez, neste momento a variável é inicializada com o valor `null`, indicando que a instância do banco de dados ainda não foi criada, a verificação se já foi criada será feita posteriormente no passo 4
3. Exporta uma função para conectar ao banco de dados
  - `connect` é uma função assíncrona que será exportada e utilizada para conectar ao banco de dados em outros arquivos
  - para entender como a sintaxe `export` funciona, consulte a documentação oficial em [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/export)
  - para entender como a sintaxe `async` funciona, consulte a documentação oficial em [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/async_function)
4. Verifica se a instância do banco de dados já foi criada
  - `if (instance) return instance` verifica se a instância do banco de dados já foi criada e, se sim, retorna a instância existente
  - neste caso não foi feito a comparação com `null` pois `null` é considerado um valor falso em JavaScript, então a verificação `if (instance)` é suficiente para verificar se a a variável `instance` já contém uma instancia do objeto de conexão com o banco de dados
  - se a instância do banco de dados já foi criada, a função `connect` retorna a instância existente, evitando a execução do restante do código e retornando a instância do banco de dados já criada 
5. Abre uma conexão com o banco de dados SQLite
  - `sqlite.open` abre uma conexão com o banco de dados SQLite, criando um arquivo chamado `database.sqlite` na raiz do projeto
  - o parametro passado para a função é um objeto com as propriedades `filename` e `driver`, onde `filename` é o caminho do arquivo do banco de dados a ser criado e `driver` é o driver do banco de dados a ser utilizado
  - o caminho do arquivo do banco de dados é relativo à pasta raiz do projeto, neste caso o arquivo será criado na raiz do projeto com o nome `database.sqlite`
  - o driver do banco de dados é o `sqlite3.Database`, que é o driver do SQLite que será utilizado para conectar ao banco de dados
  - para saber mais sobre objetos no JavaScript, consulte a documentação oficial em [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Working_with_Objects)
6. Executa um comando SQL para criar a tabela `users`
  - `db.exec` executa um comando SQL para criar a tabela `users` no banco de dados, com as colunas `id`, `name` e `email`
  - o comando SQL é uma string que contém o comando `CREATE TABLE IF NOT EXISTS users (...)`, que cria a tabela `users` se ela não existir, se a tabela já existir o comando é ignorado pelo SQLite
7. Atribui a instância do banco de dados à variável `instance`
  - `instance = db` atribui a instância do banco de dados à variável `instance`, para que caso a função `connect` seja chamada novamente, no passo 4 a instância do banco de dados já existente seja retornada
8. Retorna a instância do banco de dados
  - `return db` retorna a instância do banco de dados, que será utilizada para executar comandos SQL no banco de dados
  - para entender como a sintaxe `return` funciona, consulte a documentação oficial em [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/return)

Ao terminar esta sessão, você terá um arquivo de conexão com o banco de dados SQLite criado, com a função `connect` exportada e pronta para ser utilizada em outros arquivos do projeto.

Porém o arquivo `database.ts` não será executado automaticamente, para isso é necessário importar e executar a função `connect` no arquivo `index.ts`, que será feito na próxima sessão.

## Criando o arquivo de execução do servidor

Nesta sessão será apresentado o passo a passo para a criação do arquivo de execução do servidor, com a importação e execução da função de conexão com o banco de dados, a criação de rotas.

Para saber mais sobre o que são rotas, consulte a documentação oficial do Express em [expressjs.com roteamento básico](https://expressjs.com/pt-br/starter/basic-routing.html), para informações mais detalhadas sobre rotas, consulte a documentação oficial do Express em [expressjs.com](https://expressjs.com/pt-br/guide/routing.html).

> #### Dica: Entendendo o que é um servidor HTTP
>
> Um servidor HTTP é um software que aceita requisições HTTP de clientes, geralmente navegadores, e envia respostas HTTP com conteúdo, como páginas HTML, imagens, arquivos CSS e JavaScript.
>
> O Express é um servidor HTTP que aceita requisições HTTP de clientes e envia respostas HTTP com conteúdo, como páginas HTML, imagens, arquivos CSS e JavaScript.
> 
> É importante conhecer o protocolo HTTP para entender como o Express e outros servidores HTTP funcionam, para saber mais sobre o protocolo HTTP, consulte a documentação oficial em [developer.mozilla.org](https://developer.mozilla.org/pt-BR/docs/Web/HTTP).

  > #### Dica: Entendendo o que são métodos HTTP
  >
  > Os métodos HTTP são verbos que indicam a ação a ser realizada em um recurso, como um arquivo, uma página HTML ou um usuário.
  >
  > Os métodos HTTP mais comuns são:
  > - `GET` para obter um recurso
  > - `POST` para criar um recurso
  > - `PUT` para atualizar um recurso
  > - `DELETE` para deletar um recurso
  >
  > O Express fornece métodos para criar rotas que respondem a esses métodos HTTP, como `app.get`, `app.post`, `app.put` e `app.delete`.

> #### Dica: O que é uma API RESTful
> 
> Uma API RESTful é uma API que segue os princípios da arquitetura REST, que é um estilo de arquitetura de software que define um conjunto de restrições para a criação de serviços web.
> 
> O Express é uma biblioteca que facilita a criação de APIs RESTful, pois fornece métodos para criar rotas, aceitar requisições HTTP e enviar respostas HTTP.
>
> Para saber mais sobre APIs RESTful, consulte a documentação oficial em [restfulapi.net](https://restfulapi.net/).

no arquivo `index.ts` adicione o seguinte código:

```typescript
// 1. Importa as bibliotecas necessárias
import express from 'express'
import { connect } from './database'

// 2. Declara uma variável para armazenar a instância do Express
const app = express()

// 3. Configura o servidor para aceitar requisições JSON
app.use(express.json())

// 4. Cria uma rota para listar todos os usuários
app.get('/users', async (req, res) => {
  // 5 Conecta ao banco de dados
  const db = await connect()

  // 6 Executa um comando SQL para listar todos os usuários
  const users = await db.all('SELECT * FROM users')

  // 7 Retorna a lista de usuários em formato JSON
  res.json(users)
})

// 8. Cria uma rota para criar um novo usuário
app.post('/users', async (req, res) => {
  // 5 Conecta ao banco de dados
  const db = await connect()

  // 9 Obtém os dados do novo usuário a partir do corpo da requisição
  const { name, email } = req.body

  // 10 Executa um comando SQL para inserir um novo usuário
  const { lastID } = await db.run('INSERT INTO users (name, email) VALUES (?, ?)', [name, email])

  // 11 Retorna o novo usuário em formato JSON
  res.json({ id: lastID, name, email })
})

// 6. Cria uma rota para atualizar um usuário existente
app.put('/users/:id', async (req, res) => {
  // 5 Conecta ao banco de dados
  const db = await connect()

  // 9 Obtém os dados do usuário a partir do corpo da requisição
  const { name, email } = req.body
  
  // 12 Obtém o ID do usuário a partir dos parâmetros da requisição
  const { id } = req.params
  
  // 6.4 Executa um comando SQL para atualizar um usuário
  await db.run('UPDATE users SET name = ?, email = ? WHERE id = ?', [name, email, id])

  // 6.3 Retorna uma mensagem de sucesso
  res.json({ message: 'Usuário atualizado com sucesso' })
})

// 7. Cria uma rota para deletar um usuário existente
app.delete('/users/:id', async (req, res) => {
  // 5 Conecta ao banco de dados
  const db = await connect()

  // 12 Executa um comando SQL para deletar um usuário
  const { id } = req.params
  await db.run('DELETE FROM users WHERE id = ?', [id])

  // 13 Retorna uma mensagem de sucesso
  res.json({ message: 'Usuário deletado com sucesso' })
})

// 14. Inicia o servidor na porta 3000
app.listen(3000, () => {
  console.log('Servidor iniciado em http://localhost:3000')
})
```

### Entendendo o código

1. Importa as bibliotecas necessárias
  - `express` é a biblioteca que será utilizada para criar o servidor HTTP, saiba mais sobre o Express em [expressjs.com](https://expressjs.com/pt-br/)
  - `connect` é a função exportada do arquivo `database.ts` que será utilizada para retorna a instância do objeto de conexão com o banco de dados
2. Declara uma variável para armazenar a instância do Express
  - `app` é uma variável que armazenará a instância do servidor Express, que será utilizada para criar rotas e iniciar o servidor
3. Configura o servidor para aceitar requisições JSON
  - `app.use(express.json())` configura o servidor para aceitar requisições no formato JSON, para que seja possível enviar e receber dados no formato JSON
  - para saber mais sobre o método `use` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#app.use)
  - para saber mais sobre o método `json` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#express.json)
  - para saber mais sobre o formato JSON, consulte a documentação oficial em [json.org](https://www.json.org/json-pt.html)
4. Cria uma rota para listar todos os usuários
  - `app.get('/users', async (req, res) => { ... })` cria uma rota para listar todos os usuários, que será acessada através do método `GET` no caminho `/users`
  - para saber mais sobre o método `get` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#app.get)
5. Conecta ao banco de dados
  - `const db = await connect()` conecta ao banco de dados utilizando a função `connect` exportada do arquivo `database.ts`
6. Executa um comando SQL para listar todos os usuários
  - `const users = await db.all('SELECT * FROM users')` executa um comando SQL para listar todos os usuários na tabela `users`
  - para saber mais sobre o método `all` do SQLite, consulte a documentação oficial em [sqlite.org](https://www.sqlite.org/lang_select.html)
  - o retorno do método `all` é uma um array, neste caso o array contém lista de usuários, pois o comando SQL `SELECT * FROM users` retorna todos os usuários da tabela `users`
7. Retorna a lista de usuários em formato JSON
  - `res.json(users)` retorna a lista de usuários em formato JSON, que será enviada como resposta para o cliente
  - para saber mais sobre o método `json` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#res.json)
8. Cria uma rota para criar um novo usuário
  - `app.post('/users', async (req, res) => { ... })` cria uma rota para criar um novo usuário, que será acessada através do método `POST` no caminho `/users`
  - para saber mais sobre o método `post` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#app.post)
9. Obtém os dados do novo usuário a partir do corpo da requisição
  - `const { name, email } = req.body` obtém os dados do novo usuário a partir do corpo da requisição, que são enviados pelo cliente no formato JSON
  - note que para obtenção dos dados do novo usuário foi utilizado a sintaxe de desestruturação do JavaScript, para saber mais sobre desestruturação, consulte a documentação oficial em [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
  - para saber mais sobre o objeto `req.body` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.ht  ml#req.body)
10. Executa um comando SQL para inserir um novo usuário
  - `const { lastID } = await db.run('INSERT INTO users (name, email) VALUES (?, ?)', [name, email])` executa um comando SQL para inserir um novo usuário na tabela `users`
  - para saber mais sobre o método `run` do SQLite, consulte a documentação oficial em [sqlite.org](https://www.sqlite.org/lang_insert.html)
11. Retorna o novo usuário em formato JSON
  - `res.json({ id: lastID, name, email })` retorna o novo usuário em formato JSON, que será enviado como resposta para o cliente
  - note que o objeto retornado contém as propriedades `id`, `name` e `email`, que são os dados do novo usuário obtidos anteriormente
12. Obtém o ID do usuário a partir dos parâmetros da requisição
  - `const { id } = req.params` obtém o ID do usuário a partir dos parâmetros da requisição, que são enviados pelo cliente no caminho da rota
  - para saber mais sobre o objeto `req.params` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#req.params)
13. Retorna uma mensagem de sucesso
  - `res.json({ message: 'Usuário atualizado com sucesso' })` retorna uma mensagem de sucesso em formato JSON, que será enviada como resposta para o cliente
14. Inicia o servidor na porta 3000
  - `app.listen(3000, () => { ... })` inicia o servidor Express na porta 3000, que será acessível através do endereço `http://localhost:3000`
  - para saber mais sobre o método `listen` do Express, consulte a documentação oficial em [expressjs.com](https://expressjs.com/pt-br/4x/api.html#app.listen)

Ao terminar esta sessão, você terá um arquivo de execução do servidor Express criado, com as rotas para listar, criar, atualizar e deletar usuários, prontas para serem acessadas através do endereço `http://localhost:3000`.
