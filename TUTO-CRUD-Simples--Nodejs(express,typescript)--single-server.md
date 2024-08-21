# Inicializando o ambiente

Este tutorial tem como objetivo criar um servidor simples utilizando Node.js com Express e Typescript, utilizando um banco de dados SQLite. O foco é ser o mais pratico possível, sem muitas explicações teóricas; porém todos os conceitos podem ser encontrados na documentação oficial de cada tecnologia e nos documento de referência.

## Arquivos/Pastas e Inicialização do Projeto

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

touch .gitignore
```

> 🧠 **Entendendo os Comandos Utilizados**
> 1. [`npm init -y`](references/comandos.md#npm-init) - Inicializa um projeto Node.js com as configurações padrão. em outras palavras, cria o arquivo `package.json` com as informações padrão.
> 2. [`npm install express sqlite3 sqlite`](references/comandos.md#npm-install) - Instala as dependências do projeto.
> 3. [`npm install --save-dev typescript nodemon ts-node @types/express`](references/comandos.md#npm-install) - Instala as dependências de desenvolvimento do projeto.
> 4. [`npx tsc --init`](references/comandos.md#tsc-init) - Inicializa o arquivo de configuração do Typescript. Em outras palavras, cria o arquivo `tsconfig.json`.
> 5. [`mkdir public`](references/comandos.md#mkdir) - Cria a pasta `public`.
> 6. [`touch public/index.html`](references/comandos.md#touch) - Cria o arquivo `index.html` na pasta `public`.
> 7. [`touch public/main.css`](references/comandos.md#touch) - Cria o arquivo `main.css` na pasta `public`.
> 8. [`touch public/main.js`](references/comandos.md#touch) - Cria o arquivo `main.js` na pasta `public`.
> 9. [`mkdir src`](references/comandos.md#mkdir) - Cria a pasta `src`.
> 10. [`touch src/index.ts`](references/comandos.md#touch) - Cria o arquivo `index.ts` na pasta `src`.
> 11. [`touch src/database.ts`](references/comandos.md#touch) - Cria o arquivo `database.ts` na pasta `src`.
> 12. [`touch .gitignore`](references/comandos.md#touch) - Cria o arquivo `.gitignore`.

> ⚠️ **Notas**:
> 1. O comando `touch` não é nativo do Windows, o equivalente em sistemas Windows atuais é `ni <nome-do-arquivo>` e em sistemas mais antigos é `echo. > <nome-do-arquivo>`.

## Configuração dos scripts de execução no package.json

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

> ⚠️ **Notas**: 
> 1. `…` indica que partes do código foram omitidas para simplificar a leitura.
> 2. O arquivo `package.json` por padrão já possui um script chamado `test`, que é utilizado para executar testes automatizados, porém, como este tutorial não aborda testes automatizados, o script `test` não foi mencionado e caso seja necessário, pode ser removido ou alterado.

> 🧠 **Entendendo os Scripts**
> - `npm start` - Inicia o servidor em ambiente de produção. Neste caso, executa o comando `node dist/index.js`.
> - `npm run dev` - Inicia o servidor em ambiente de desenvolvimento, utilizando o `nodemon` para reiniciar o servidor sempre que houver alterações no código. Neste caso, executa o comando `nodemon src/index.ts`.
> - `npm build` - Compila o código Typescript para Javascript. neste caso executa o comando `tsc -p .` que compila o código Typescript baseado nas configurações do arquivo `tsconfig.json`.

## Configuração do tsconfig.json

Procure a linha `"outDir": "./",` e altere para `"outDir": "./dist",` para que os arquivos compilados sejam salvos na pasta `dist`.

Não se esqueça de descomentar a linha, removendo o `//` do início da linha.

## Configuração do .gitignore

O arquivo `.gitignore` é utilizado para informar ao Git quais arquivos e pastas devem ser ignorados ao realizar o controle de versão. Isso significa que os arquivos e pastas listados no arquivo `.gitignore` não serão enviados para o repositório remoto.

Caso você não saiba o que é e como funciona o Git, leia no [documento de referência](references/glossario.md#git) sobre.

```bash
node_modules/
dist/
database.sqlite
```

## Configuração do src/database.ts

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

## Configuração do src/index.ts

Este arquivo será responsável por criar o servidor Express e definir as rotas para o [CRUD](references/glossario.md#crud)
 de usuários, em outras cria uma [API REST](references/glossario.md#restful-api) capaz de criar, ler, atualizar e deletar usuários, este servidor também servirá os arquivos estáticos da pasta `public` (como arquivos HTML, CSS, JS, imagens, etc).

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

## Configuração do public/index.html

⭐⭐⭐⭐⭐⭐⭐⭐terminar isso

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

## Configuração do public/main.css

```css
* {
  box-sizing: border-box;
}

:root {
  font-family: Arial, sans-serif;
}

body {
  display: flex;
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
  display: inline-block;
  background-color: #fff;
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

## Configuração do public/main.js

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