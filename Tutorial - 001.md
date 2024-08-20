# Inicializando o ambiente

## Arquivos/Pastas e Inicialização do Projeto

```bash
npm init -y
npm install express sqlite3 sqlite
npm install --save-dev typescript nodemon ts-node @types/express
npx tsc --init
mkdir public
mkdir src
touch .gitignore
touch public/index.html
touch src/index.ts
touch src/database.ts
```

## Configuração do package.json

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

> **Nota**: `…` indica que partes do código foram omitidas para simplificar a leitura.

## Configuração do tsconfig.json

Procure a linha `"outDir": "./",` e altere para `"outDir": "./dist",` para que os arquivos compilados sejam salvos na pasta `dist`.

Não se esqueça de descomentar a linha, removendo o `//` do início da linha.

## Configuração do .gitignore

```bash
node_modules/
dist/
database.sqlite
```

## Configuração do src/database.ts

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

```typescript
import express from 'express'
import cors from 'cors'
import { connect } from './database'

const port = 3333
const app = express()

app.use(cors())
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
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cadastro de Usuário</title>
  <style>
    * {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    form {
      display: inline-flex;
      flex-direction: column;
      gap: 10px;
      width: 300px;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    form>div.input-container {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }

    form>div.actions {
      display: flex;
      gap: 10px;
      justify-content: flex-end;
    }

    form>div.actions>button {
      padding: 5px 10px;
      border: none;
      border-radius: 5px;
      background-color: #007bff;
      color: #fff;
      cursor: pointer;
    }

    form>div.actions>button.excluir {
      background-color: #dc3545;
    }

    form>div.actions>button.atualizar {
      background-color: #28a745;
    }
  </style>
</head>

<body>
  <form data-id="1">
    <div class="input-container">
      <label for="nome">Nome:</label>
      <input type="text" name="nome" id="nome" required>
    </div>
    <div class="input-container">
      <label for="email">E-mail:</label>
      <input type="email" name="email" id="email" required>
    </div>
    <div class="actions">
      <button type="submit" class="excluir">Deletar</button>
      <button type="submit" class="atualizar">Atualizar</button>
    </div>
  </form>

  <form class="add">
    <div class="input-container">
      <label for="nome">Nome:</label>
      <input type="text" name="nome" id="nome" required>
    </div>
    <div class="input-container">
      <label for="email">E-mail:</label>
      <input type="email" name="email" id="email" required>
    </div>
    <div class="actions">
      <button type="submit">Cadastrar</button>
    </div>
  </form>
  <script>
    const forms = document.querySelectorAll('form')
    forms.forEach(form => {
      form.addEventListener('submit', async (event) => {
        event.preventDefault()

        const newForm = document.createElement('form')

        newForm.innerHTML = form.innerHTML
        document.body.insertBefore(newForm, form)

        return

        const id = form.dataset.id
        const nome = form.nome.value
        const email = form.email.value
        const body = { nome, email }
        const url = id ? `/usuarios/${id}` : '/usuarios'
        const method = id ? 'PUT' : 'POST'
        const headers = { 'Content-Type': 'application/json' }
        const response = await fetch(url, { method, headers, body });
        const data = await response.json()

        if (id && response.ok) {
          alert('Usuário atualizado com sucesso!')
          return
        }

        if (response.ok) {
          alert('Usuário cadastrado com sucesso!')
          // append before created user form
          const newForm = document.createElement('form')
          newForm.dataset.id = data.id
          newForm.innerHTML = form.innerHTML
          form.before(newForm)
          return
        }
      });
    });

  </script>
</body>

</html>
```