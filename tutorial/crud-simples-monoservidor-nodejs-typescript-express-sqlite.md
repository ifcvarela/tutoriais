# CRUD Simples Monoservidor com Node.js (Typescript, Express) e SQLite

O propósito deste tutorial é criar um servidor simples utilizando Node.js com Express e Typescript, utilizando um banco de dados SQLite. O foco é ser o mais prático possível, sem muitas explicações teóricas; porém todos os conceitos podem ser encontrados na documentação oficial de cada tecnologia e nos documentos de referência.

Neste projeto será criado um servidor único que servirá tanto os arquivos [estáticos (HTML, CSS, JS, imagens, etc)](../referencias/glossario.md#arquivos-estaticos) enquanto uma [API RESTful](../referencias/glossario.md#restful-api) para realizar operações de [CRUD (Create, Read, Update, Delete)](../referencias/glossario.md#crud) em um banco de dados [SQLite](../referencias/glossario.md#sqlite), não sendo necessário a implementação de [CORS (Cross-Origin Resource Sharing)](../referencias/glossario.md#cors), pois o servidor e o cliente estarão no mesmo domínio.

> ⚠️ **Aviso Importante**:
>
> 1. Este não é um exemplo de aplicação pronta para produção, pois não possui validação de dados, tratamento de erros, autenticação, autorização, etc. Este é um exemplo didático para fins de aprendizado.

## Pré-requisitos

Certifique-se de ter os seguintes pré-requisitos instalados em seu computador:

- [Node.js e NPM](https://nodejs.org)
- [Visual Studio Code](https://code.visualstudio.com)

> 💡 **Dica**
>
> 1. É possível a utilização do [codespace do GitHub](codespace.md) para executar este projeto substituindo a necessidade de instalar o Node.js e o Visual Studio Code em seu computador. Os codespaces são ambientes de desenvolvimento em nuvem. Para entender o necessário para utilizar o codespace leia o [tutorial codespace](codespace.md).
> 2. Para maiores informações de como usar o codespace leia o [tutorial codespace](codespace.md)

Certifique-se de ter os seguintes conhecimentos básicos:

- Conhecimento básico de Javascript
- Conhecimento básico de Typescript
- Conhecimento básico de HTML e CSS
- Conhecimento básico de SQL

## Boilerplate: Inicializando o Ambiente

Neste tópico será abordado a inicialização do ambiente de desenvolvimento, criando a estrutura de pastas e arquivos necessários para o projeto. Chamamos isso de "boilerplate" ou "esqueleto" do projeto.

### Arquivos/Pastas e Inicialização do Projeto

```bash
npm init -y
npm install express sqlite3 sqlite
npm install --save-dev typescript nodemon ts-node @types/express
npx tsc --init

mkdir public
touch public/index.html
touch public/main.css
touch public/main.js

mkdir src
touch src/index.ts
touch src/database.ts

git init
touch .gitignore
```

> 🧠 **Entendendo os Comandos Utilizados**
>
> 1. [`npm init -y`](../referencias/comandos.md#npm-init-y) - Inicializa um projeto Node.js com as configurações padrão. em outras palavras, cria o arquivo `package.json` com as informações padrão.
> 2. [`npm install express sqlite3 sqlite`](../referencias/comandos.md#npm-install) - Instala as dependências do projeto.
> 3. [`npm install --save-dev typescript nodemon ts-node @types/express`](../referencias/comandos.md#npm-install-d) - Instala as dependências de desenvolvimento do projeto.
> 4. [`npx tsc --init`](../referencias/comandos.md#tsc-init) - Inicializa o arquivo de configuração do Typescript. Em outras palavras, cria o arquivo `tsconfig.json`.
> 5. [`mkdir public`](../referencias/comandos.md#mkdir) - Cria a pasta `public`.
> 6. [`touch public/index.html`](../referencias/comandos.md#touch) - Cria o arquivo `index.html` na pasta `public`.
> 7. [`touch public/main.css`](../referencias/comandos.md#touch) - Cria o arquivo `main.css` na pasta `public`.
> 8. [`touch public/main.js`](../referencias/comandos.md#touch) - Cria o arquivo `main.js` na pasta `public`.
> 9. [`mkdir src`](../referencias/comandos.md#mkdir) - Cria a pasta `src`.
> 10. [`touch src/index.ts`](../referencias/comandos.md#touch) - Cria o arquivo `index.ts` na pasta `src`.
> 11. [`touch src/database.ts`](../referencias/comandos.md#touch) - Cria o arquivo `database.ts` na pasta `src`.
> 12. [`git init`](../referencias/comandos.md#git-init) - Inicializa um repositório Git.
> 13. [`touch .gitignore`](../referencias/comandos.md#touch) - Cria o arquivo `.gitignore`.

> ⚠️ **Atenção**:
>
> 1. O comando `touch` não é nativo do Windows, o equivalente em sistemas Windows atuais é `ni <nome-do-arquivo>` e em sistemas mais antigos é `echo. > <nome-do-arquivo>`.

### Configuração dos scripts de execução no package.json

Scripts de execução são comandos que podem ser executados através do terminal, para isso, basta digitar `npm run <script>`, onde `<script>` é o nome do script que deseja executar.

Os scripts de execução são importantes para automatizar tarefas e padronizar a execução de comandos.

Adicione os seguintes scripts no arquivo `package.json`:

```json
{
  …
  "scripts": {
    "start": "node dist/index.js",
    "dev": "nodemon src/index.ts",
    "build": "tsc -p ."
  },
  …
}
```

> ⚠️ **Atenção**: 
> 
> 1. `…` indica que partes do código foram omitidas para simplificar a leitura.
> 2. O arquivo `package.json` por padrão já possui um script chamado `test`, que é utilizado para executar testes automatizados, porém, como este tutorial não aborda testes automatizados, o script `test` não foi mencionado e caso seja necessário, pode ser removido ou alterado.

> 🧠 **Entendendo os Scripts**
>
> 1. `npm start` - Inicia o servidor em ambiente de produção. Neste caso, executa o comando `node dist/index.js`.
> 2. `npm run dev` - Inicia o servidor em ambiente de desenvolvimento, utilizando o `nodemon` para reiniciar o servidor sempre que houver alterações no código. Neste caso, executa o comando `nodemon src/index.ts`.
> 3. `npm build` - Compila o código Typescript para Javascript. neste caso executa o comando `tsc -p .` que compila o código Typescript baseado nas configurações do arquivo `tsconfig.json`.

### Configuração do tsconfig.json

Procure a linha `"outDir": "./",` e altere para `"outDir": "./dist",` para que os arquivos compilados sejam salvos na pasta `dist`.

Não se esqueça de descomentar a linha, removendo o `//` do início da linha.

### Configuração do .gitignore

O arquivo `.gitignore` é utilizado para informar ao Git quais arquivos e pastas devem ser ignorados ao realizar o controle de versão. Isso significa que os arquivos e pastas listados no arquivo `.gitignore` não serão enviados para o repositório remoto.

Caso você não saiba o que é e como funciona o Git, leia no [documento de referência](../referencias/glossario.md#git) sobre.

```plaintext
node_modules/
dist/

database.sqlite
```

## Desenvolvimento do Projeto

Neste tópico será desenvolvido o projeto, criando o servidor Express, a conexão com o banco de dados SQLite, as rotas para o CRUD de usuários e os arquivos estáticos (HTML, CSS, JS).

### Configuração do src/database.ts

Este arquivo será responsável por criar a conexão com o banco de dados SQLite e criar a tabela de usuários caso ela não exista ou o banco de dados não exista.

```typescript
import { open, Database } from 'sqlite';
import sqlite3 from 'sqlite3';

let instance: Database | null = null;

export async function connect() {
  if (instance) return instance;

  const db = await open({
     filename: './src/database.sqlite',
     driver: sqlite3.Database
   });
  
  await db.exec(`
    CREATE TABLE IF NOT EXISTS users (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      name TEXT,
      email TEXT
    )
  `);

  instance = db;
  return db;
}
```

### Configuração do src/index.ts

Este arquivo será responsável por criar o servidor Express e definir as rotas para o [CRUD](../referencias/glossario.md#crud)
 de usuários, em outras cria uma [API REST](../referencias/glossario.md#restful-api) capaz de criar, ler, atualizar e deletar usuários, este servidor também servirá os arquivos estáticos da pasta `public` (como arquivos HTML, CSS, JS, imagens, etc).

```typescript
import express from 'express'
import { connect } from './database'

const port = 3000
const app = express()

app.use(express.json())
app.use(express.static(__dirname + '/../public'))

app.get('/users', async (req, res) => {
  const db = await connect()
  const users = await db.all('SELECT * FROM users')
  res.json(users)
})

app.post('/users', async (req, res) => {
  const db = await connect()
  const { name, email } = req.body
  const result = await db.run('INSERT INTO users (name, email) VALUES (?, ?)', [name, email])
  const user = await db.get('SELECT * FROM users WHERE id = ?', [result.lastID])
  res.json(user)
})

app.put('/users/:id', async (req, res) => {
  const db = await connect()
  const { name, email } = req.body
  const { id } = req.params
  await db.run('UPDATE users SET name = ?, email = ? WHERE id = ?', [name, email, id])
  const user = await db.get('SELECT * FROM users WHERE id = ?', [id])
  res.json(user)
})

app.delete('/users/:id', async (req, res) => {
  const db = await connect()
  const { id } = req.params
  await db.run('DELETE FROM users WHERE id = ?', [id])
  res.json({ message: 'User deleted' })
})

app.listen(port, () => {
  console.log(`Server running on port ${port}`)
})
```

⚡⚡⚡⚡DESCREVER O CÓDIGO AQUI: NÃO ESQUECER

> ⚠️ **Atenção**:
>
> 1. è muito importante notar que este código não é seguro para ser utilizado em produção, pois não há validação de dados, tratamento de erros, autenticação, autorização, etc. Este código é apenas um exemplo didático para fins de aprendizado.

### Configuração do public/index.html

O arquivo `index.html` será responsável por exibir um formulário para cadastrar usuários, alterar usuários e excluir usuários, além de exibir a lista de usuários cadastrados.

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cadastro de Usuários</title>
  <link rel="stylesheet" href="main.css">
  <script src="main.js" defer></script>
</head>
<body>
  <h1>Cadastro de Usuários</h1>
  <main>
    <form>
      <div class="input-container">
        <label for="name">Nome</label>
        <input type="text" name="name">
      </div>
      <div class="input-container">
        <label for="email">E-mail</label>
        <input type="email" name="email">
      </div>
      <div class="actions-container">
        <button data-action="delete">Excluir</button>
        <button data-action="update">Alterar</button>
        <button data-action="create">Cadastrar</button>
      </div>
    </form>
  </main>
</body>
</html>
```

### Configuração do public/main.css

O arquivo `main.css` será responsável por estilizar os formulários. Este não é um tutorial de [CSS](../referencias/glossario.md#css), por isso, o foco é apenas estilizar os formulários de forma simples e funcional.

```css
* {
  box-sizing: border-box;
}

:root {
  font-family: Arial, sans-serif;
}

body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 0;
  padding: 1rem;
  min-height: 100vh;
  background-color: #f0f0f0;
}

main {
  display: flex;
  gap: .5rem;
  flex-wrap: wrap;
  justify-content: center;
}

form {
  background-color: #fff;
  display: inline-block;
  padding: 1.5rem;
  margin: 0;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: 350px;
  flex: none;
}

form[data-id] {
  & button[data-action=create] {
    display: none;
  }
}

form:not([data-id]) {
  & button[data-action=update],
  & button[data-action=delete] {
    display: none;
  }
}

form .input-container {
  margin-bottom: 1rem;
}

form label {
  display: block;
  font-weight: bold;
  margin-bottom: .25rem;
}

form input {
  width: 100%;
  padding: .6rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}

form .actions-container {
  display: flex;
  justify-content: flex-end;
  gap: .5rem;
}

form button {
  padding: 10px 20px;
  border: 0;
  border-radius: 5px;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
}

form button[data-action=cancel] {
  background-color: transparent;
  color: #dc3545;
  margin-right: auto;
  padding-inline: .5rem;
}

form button[data-action=update] {
  background-color: #007bff;
}

form button[data-action=delete] {
  background-color: #dc3545;
}

form button[data-action=create] {
  background-color: #28a745;
}
```

### Configuração do public/main.js

O arquivo `main.js` será responsável por enviar requisições para o servidor, seja para cadastrar, alterar ou excluir usuários, além de exibir a lista de usuários cadastrados. Note que este arquivo faz requisições para as rotas definidas no arquivo `src/index.ts` que é quem de fatos executa as operações no banco de dados.

```javascript
const mainForm = document.querySelector('form')

void async function () {
  const response = await fetch('/users')
  const users = await response.json()
  users.forEach(user => {
    const newForm = mainForm.cloneNode(true)
    newForm.name.value = user.name
    newForm.email.value = user.email
    newForm.dataset.id = user.id
    newForm.id.readOnly = true
    mainForm.before(newForm)
  })
  console.log(users)
}()

document.addEventListener('submit', async (event) => {
  event.preventDefault()
  const action = event.submitter.dataset.action ?? null
  const currentForm = event.target
  
  if (action === 'delete') {
    const id = currentForm.dataset.id
    const method = 'DELETE'
    const url = `/users/${id}`
    const response = await fetch(url, { method })
    if (!response.ok)
      return console.error('Error:', response.statusText)
    currentForm.remove()
    return
  }
  
  if (action === 'update') {
    const id = currentForm.dataset.id
    const method = 'PUT'
    const url = `/users/${id}`
    const headers = { 'Content-Type': 'application/json' }
    const name = currentForm.name.value
    const email = currentForm.email.value
    const body = JSON.stringify({ name, email })
    const response = await fetch(url, { method, headers, body, })
    if (!response.ok)
      return console.error('Error:', response.statusText)
    const responseData = await response.json()
    currentForm.name.value = responseData.name
    currentForm.email.value = responseData.email
    return
  }
  
  if (action === 'create') {
    const method = 'POST'
    const url = '/users'
    const headers = { 'Content-Type': 'application/json' }
    const name = currentForm.name.value
    const email = currentForm.email.value
    const body = JSON.stringify({ name, email })
    const response = await fetch(url, { method, headers, body })
    if (!response.ok)
      return console.error('Error:', response.statusText)
    const responseData = await response.json()
    const newForm = mainForm.cloneNode(true)
    newForm.name.value = responseData.name
    newForm.email.value = responseData.email
    newForm.dataset.id = responseData.id
    newForm.id.readOnly = true
    mainForm.reset()
    mainForm.before(newForm)
    return
  }
})
```

⚡⚡⚡⚡DESCREVER O CÓDIGO AQUI: NÃO ESQUECER

> ⚠️ **Atenção**:
>
> 1. É muito importante notar que este código não é seguro para ser utilizado em produção, pois não há validação de dados, tratamento de erros, autenticação, autorização, etc. Este código é apenas um exemplo didático para fins de aprendizado.
> 2. Este código também não apresenta feedback ao usuário, como mensagens de sucesso, somente uma mensagem de erro genérica utilizando alertas do navegador.

## Execução e Teste do Projeto

Neste tópico será abordado como executar e testar o projeto.

### Executando o Projeto

Para executar o projeto, basta executar o comando `npm run dev` no terminal. Este comando irá iniciar o servidor Express utilizando o `nodemon`, que irá reiniciar o servidor sempre que houver alterações no código.

```bash
npm run dev
```

> ⚠️ **Atenção**:
>
> 1. O comando `npm run dev` é um script definido no arquivo `package.json` e é responsável por iniciar o servidor Express utilizando o `nodemon`.

### Testando o Projeto

Para testar o projeto, basta abrir o navegador e acessar a URL `http://localhost:3000`. Nesta página, você verá um formulário para cadastrar usuários, alterar usuários e excluir usuários, além de exibir a lista de usuários cadastrados.

> 💡 **Dica**
>
> 1. Para testar [APIs REST](../referencias/glossario.md#restful-api) antes do desenvolvimento de um cliente ([Front-end](../referencias/glossario.md#frontend)), é possível com ferramentas como o [Postman](https://www.postman.com), [Insomnia](https://insomnia.rest) ou [Thunder Client](https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client) (extensão do Visual Studio Code).
> 2. Também é possivel utilizar o [curl](https://curl.se) para testar as requisições direto em seu terminal, porém, é mais complexo e menos visual.
> 3. Este projeto não tem a necessidade de utilização de nenhum dessas ferramentas, pois os [arquivos estáticos (HTML, CSS, JS)](../referencias/glossario.md#static-files) já possuem capacidade para testar as operações de [CRUD](../referencias/glossario.md#crud).

## Salvando o Projeto no Repositório (Git e GitHub)

...
