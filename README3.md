# Unidade 01 - Conhecimento básico necessário

Nesta unidade, vamos revisar os conhecimentos básicos necessários para o desenvolvimento de aplicações web, com NodeJs, Express e SQLite, nesta unidade serão abordaos os seguintes tópicos:

## Conhecimento básico de terminal, Windows (powershell) e/ou Linux (bash)
  - Navegação entre pastas
  - Criar pastas e arquivos

## Conhecimento básico de redes
  - Endereçamento IP
  - Portas

## Protocolo HTTP
  - Requisições
    - Estrutura de uma requisição
    - Métodos
  - Respostas
    - Estrutura de uma resposta
    - Códigos de status

## Conhecimento básico de HTML e CSS
  - Sintaxe do HTML
  - Sintaxe do CSS

## Conhecimento básico de JavaScript
  - Variáveis e Constantes
  - Funções, Arrow Functions
  - Arrays e Objetos
  - Operadores
    - Aritméticos
    - Lógicos
    - Comparação
  - Estruturas de controle
    - `if ... else`, `do ... while`, `switch`, `for`, `while`
  - Promises (async/await)

## Conhecimento básico de SQL 
  - `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`
  - `SELECT` (`ORDER BY`, `LIMIT`), `INSERT`, `UPDATE`, `DELETE`, `WHERE`, `JOIN`, `GROUP BY`

## Conhecimento básico de TypeScript
  - Compilação vs Transpilação
  - Tipos de dados
    - `string`, `number`, `boolean`, `any`, `void`, `null`, `undefined`, `object`, `Array`, `Enum` etc

## Conhecimento básico de Node.js
  - Módulos (import/export)

## REST API
  - Métodos HTTP
    - `GET`, `POST`, `PUT`, `DELETE`
  - Recursos
  - Endpoints
  - Corpo da requisição
  - Cabeçalhos da requisição
  - Corpo da resposta
  - Cabeçalhos da resposta

## Conhecimento básico de NPM e NPX
  - Instalação de pacotes
  - Scripts de execução
  - Pacotes de produção
  - Pacotes de desenvolvimento
  - Comandos
    - npm init -y
    - npm install \<pacote(s)>
    - npm install --save-dev
    - npm run \<script>
    - npx tsc --init

## Conhecimento básico de Git e GitHub
  - Repositório
  - Arquivo .gitignore
  - Commands
    - git init
    - git add --all
    - git commit -m \<messagem>
    - git push
    - git pull
    - git clone

## Terminal

O terminal é uma interface de linha de comando que permite interagir com o sistema operacional, executar comandos e navegar entre pastas e arquivos. Existem diversos terminais disponíveis, como o terminal do Windows (powershell), terminal do Linux (bash), terminal do MacOS (bash), entre outros.

### Navegação entre pastas

Para navegar entre pastas no terminal, utilizamos os comandos `cd` (change directory) para entrar em uma pasta e `cd ..` para sair de uma pasta. Abaixo estão alguns exemplos de comandos para navegar entre pastas:

```bash
# Entrar na pasta "Documents"
cd Documents

# Sair da pasta "Documents"
cd ..

# Entrar na pasta "Projects"
cd Projects
```

### Criar pastas e arquivos

Para criar pastas e arquivos no terminal, utilizamos os comandos `mkdir` (make directory) para criar uma pasta e `touch` para criar um arquivo. Abaixo estão alguns exemplos de comandos para criar pastas e arquivos:

```bash
# Criar a pasta "Documents"
mkdir Documents

# Criar o arquivo "index.html"
touch index.html
```

## Redes

Redes de computadores são sistemas de comunicação que permitem a troca de informações entre dispositivos, como computadores, servidores, smartphones, entre outros. Para que a comunicação entre dispositivos seja possível, é necessário que cada dispositivo tenha um endereço IP único e que as informações sejam enviadas e recebidas através de portas.

### Endereçamento IP

O endereço IP (Internet Protocol) é um identificador único atribuído a cada dispositivo em uma rede de computadores. Existem dois tipos de endereços IP: IPv4 (32 bits) e IPv6 (128 bits). O endereço IP é composto por quatro números separados por pontos, por exemplo: `

### Portas

As portas são canais de comunicação que permitem que diferentes aplicativos e serviços se comuniquem entre si. Cada aplicativo ou serviço é associado a uma porta específica, que é utilizada para enviar e receber informações. As portas são identificadas por números inteiros de 0 a 65535, sendo que as portas de 0 a 1023 são conhecidas como portas bem conhecidas e são reservadas para serviços específicos, como HTTP (80), HTTPS (443), SSH (22), entre outros.

## Protocolo HTTP

O protocolo HTTP (Hypertext Transfer Protocol) é um protocolo de comunicação utilizado para transferir informações na web. O HTTP define a estrutura das mensagens de requisição e resposta, bem como os métodos de requisição e os códigos de status.

### Requisições

As requisições HTTP são mensagens enviadas pelo cliente para o servidor, solicitando a execução de uma ação. As requisições HTTP são compostas por um cabeçalho e, opcionalmente, um corpo. O cabeçalho contém informações sobre a requisição, como o método, o caminho, os cabeçalhos de autenticação, entre outros. O corpo contém os dados enviados na requisição, como os parâmetros de um formulário.

#### Estrutura de uma requisição

Uma requisição HTTP é composta por um método, um caminho, um cabeçalho e, opcionalmente, um corpo. Abaixo está a estrutura de uma requisição HTTP:

```
Método Caminho HTTP/1.1
Cabeçalho: Valor
Cabeçalho: Valor

Corpo da requisição
```

#### Métodos

Os métodos de requisição HTTP definem a ação que deve ser executada pelo servidor. Alguns dos métodos mais comuns são:

- `GET`: solicita a recuperação de um recurso.
- `POST`: envia dados para serem processados por um recurso.
- `PUT`: atualiza um recurso existente.
- `DELETE`: remove um recurso existente.

### Respostas

As respostas HTTP são mensagens enviadas pelo servidor para o cliente, em resposta a uma requisição. As respostas HTTP são compostas por um cabeçalho e, opcionalmente, um corpo. O cabeçalho contém informações sobre a resposta, como o código de status, a descrição do status, os cabeçalhos de autenticação, entre outros. O corpo contém os dados enviados na resposta, como o conteúdo de uma página web.

#### Estrutura de uma resposta

Uma resposta HTTP é composta por um código de status, uma descrição do status, um cabeçalho e, opcionalmente, um corpo. Abaixo está a estrutura de uma resposta HTTP:

```
HTTP/1.1 Código de status Descrição do status
Cabeçalho: Valor
Cabeçalho: Valor

Corpo da resposta
```

#### Códigos de status

Os códigos de status HTTP indicam o resultado da requisição. Alguns dos códigos de status mais comuns são:

- `200 OK`: a requisição foi bem-sucedida.
- `201 Created`: a requisição foi bem-sucedida e um novo recurso foi criado.
- `400 Bad Request`: a requisição não pôde ser processada devido a um erro no cliente.
- `404 Not Found`: o recurso solicitado não foi encontrado no servidor.
- `500 Internal Server Error`: o servidor encontrou um erro ao processar a requisição.

## HTML e CSS

HTML (Hypertext Markup Language) e CSS (Cascading Style Sheets) são as linguagens de marcação e estilização utilizadas para criar páginas web. O HTML define a estrutura e o conteúdo da página, enquanto o CSS define o estilo e a aparência da página.

### Sintaxe do HTML

O HTML é composto por elementos, que são tags delimitadas por `<` e `>`. Cada elemento possui um nome e pode conter atributos e conteúdo. Abaixo está um exemplo de um elemento HTML:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Título da Página</title>
</head>
<body>
  <h1>Olá, mundo!</h1>
  <p>Este é um parágrafo de exemplo.</p>
</body>
</html>
```

### Sintaxe do CSS

O CSS é composto por regras de estilo, que são formadas por um seletor e um bloco de declarações. O seletor define os elementos aos quais as declarações se aplicam, e as declarações definem o estilo dos elementos. Abaixo está um exemplo de uma regra de estilo CSS:

```css
h1 {
  color: blue;
  font-size: 24px;
}
```

## JavaScript

JavaScript é uma linguagem de programação utilizada para criar páginas web interativas. O JavaScript é executado no navegador do cliente e permite adicionar interatividade, animações e dinamismo às páginas web.

### Variáveis e Constantes

As variáveis e constantes são utilizadas para armazenar valores na memória do computador. As variáveis podem ter seu valor alterado ao longo do tempo, enquanto as constantes têm um valor fixo. Abaixo estão exemplos de declaração de variáveis e constantes em JavaScript:

```javascript
let nome = 'João'; // variável
const idade = 30; // constante
```

### Funções, Arrow Functions

As funções são blocos de código que podem ser reutilizados em diferentes partes do programa. As arrow functions são uma forma simplificada de declarar funções em JavaScript. Abaixo estão exemplos de declaração de funções e arrow functions em JavaScript:

```javascript
// Função
function somar(a, b) {
  return a + b;
}

// Função Flexa / Arrow Function
const subtrair = (a, b) => a - b;
```

### Arrays e Objetos

Os arrays e objetos são estruturas de dados utilizadas para armazenar coleções de valores. Os arrays são listas ordenadas de valores, enquanto os objetos são coleções de pares chave-valor. Abaixo estão exemplos de declaração de arrays e objetos em JavaScript:

```javascript
// Array
let frutas = ['maçã', 'banana', 'laranja'];

// Objeto
let pessoa = {
  nome: 'João',
  idade: 30
};
```

### Operadores

Os operadores são símbolos utilizados para realizar operações matemáticas, lógicas e de comparação em JavaScript. Alguns dos operadores mais comuns são:

#### Aritméticos

- `+`: adição
- `-`: subtração
- `*`: multiplicação
- `/`: divisão
- `%`: resto da divisão

#### Lógicos

- `&&`: e lógico
- `||`: ou lógico
- `!`: negação lógica

#### Comparação

- `==`: igual a
- `===`: igual a (comparação estrita)	
- `>`: maior que
- `<`: menor que
- `>=`: maior ou igual a
- `<=`: menor ou igual a
- `!`: operador de negação
- `!=`: diferente de
- `!==`: diferente de (comparação estrita)
- `??`: operador de coalescência nula
- `?.`: operador de encadeamento opcional

### Estruturas de controle

As estruturas de controle são utilizadas para controlar o fluxo de execução do programa. Alguns dos comandos de controle mais comuns em JavaScript são:

- `if ... else`: executa um bloco de código se uma condição for verdadeira, e outro bloco de código se a condição for falsa.
- `do ... while`: executa um bloco de código enquanto uma condição for verdadeira.
- `switch`: executa um bloco de código com base no valor de uma expressão.
- `for`: executa um bloco de código um número específico de vezes.
- `while`: executa um bloco de código enquanto uma condição for verdadeira.
- `break`: interrompe a execução de um loop.
- `continue`: pula a iteração atual de um loop.

### Promises (async/await)

As promises são objetos utilizados para representar operações assíncronas em JavaScript. As promises possuem três estados: pendente, resolvida e rejeitada. O `async` e `await` são palavras-chave utilizadas para trabalhar com promises de forma síncrona. Abaixo está um exemplo de utilização de promises com async/await em JavaScript:

```javascript
async function buscarDados() {
  try {
    let resposta = await fetch('https://api.exemplo.com/dados');
    let dados = await resposta.json();
    console.log(dados);
  } catch (erro) {
    console.error(erro);
  }
}
```

## SQL

SQL (Structured Query Language) é uma linguagem de consulta estruturada utilizada para interagir com bancos de dados relacionais. O SQL permite realizar operações de consulta, inserção, atualização e exclusão de dados em um banco de dados. Abaixo estão alguns dos comandos SQL mais comuns:

- `SELECT`: recupera dados de uma ou mais tabelas.
- `INSERT`: insere novos dados em uma tabela.
- `UPDATE`: atualiza dados existentes em uma tabela.
- `DELETE`: remove dados de uma tabela.

## TypeScript

TypeScript é uma linguagem de programação que estende o JavaScript adicionando tipagem estática e outros recursos avançados. O TypeScript é transpilado para JavaScript antes de ser executado no navegador ou no servidor. Abaixo estão alguns dos conceitos básicos do TypeScript:

### Compilação vs Transpilação

A compilação é o processo de tradução de um código fonte em uma linguagem de programação para um código objeto em outra linguagem. A transpilação é um tipo específico de compilação em que o código fonte é traduzido para uma linguagem de nível semelhante. O TypeScript é transpilado para JavaScript, pois ambos são linguagens de programação de alto nível.

### Tipos de dados

O TypeScript possui diversos tipos de dados, que são utilizados para definir o tipo de uma variável, constante ou parâmetro de função. Alguns dos tipos de dados mais comuns em TypeScript são:

- `string`: representa valores de texto.
- `number`: representa valores numéricos.
- `boolean`: representa valores lógicos (verdadeiro ou falso).
- `any`: representa qualquer tipo de dado.
- `void`: representa a ausência de tipo.
- `null`: representa um valor nulo.
- `undefined`: representa um valor indefinido.
- `object`: representa um objeto.
- `Array`: representa um array.
- `Enum`: representa um conjunto de valores nomeados.

## Node.js

Node.js é uma plataforma de desenvolvimento de aplicações server-side baseada no motor V8 do Google Chrome. O Node.js permite a execução de código JavaScript no servidor, o que possibilita a criação de aplicações web escaláveis e de alto desempenho. Abaixo estão alguns dos conceitos básicos do Node.js:

### Módulos (import/export)

Os módulos são arquivos ou bibliotecas que contêm funções, classes e variáveis que podem ser reutilizadas em diferentes partes do programa. No Node.js, os módulos são importados e exportados utilizando as palavras-chave `import` e `export`. Abaixo está um exemplo de importação e exportação de módulos em Node.js:

```javascript
// Módulo A
export function somar(a, b) {
  return a + b;
}

// Módulo B
import { somar } from './moduloA';
console.log(somar(2, 3)); // 5
```

## REST API

REST (Representational State Transfer) é um estilo arquitetural utilizado para projetar serviços web que são escaláveis, flexíveis e fáceis de manter. As APIs RESTful são baseadas em recursos, que são identificados por URIs (Uniform Resource Identifiers) e manipulados através de métodos HTTP. Abaixo estão alguns dos conceitos básicos de uma API REST:



























# Unidade 2 - Desenvolvimento de Aplicações Web

Nesta unidade, vamos desenvolver uma aplicação web utilizando Node.js, Express e SQLite. A aplicação será um [CRUD](/doc/glossario.md#crud) de usuários, onde será possível listar, adicionar, atualizar e deletar usuários.

## Antes de começar

Instale os seguintes programas:
- [Node.js](https://nodejs.org/)
- [Visual Studio Code](https://code.visualstudio.com/)

Crie uma pasta para o projeto e abra a pasta no [VSCode](/doc/glossario.md#vscode), para isso, abra o [VSCode](/doc/glossario.md#vscode) e clique em `File > Open Folder...` e selecione a pasta que você criou então clique em `Selecionar Pasta`.

## Configuração do ambiente de desenvolvimento

Chamaremos aqui de ambiente de desenvolvimento o conjunto de ferramentas e configurações necessárias para desenvolver a aplicação, bem como a estrutura de arquivos e pastas do projeto e scripts de execução.

### Inicialização do Projeto

```bash	
npm init -y
npm install express sqlite sqlite3
npm install --save-dev nodemon ts-node typescript  @types/express
npx tsc --init
git init
```

> Entenda os comandos executados:
> ---
> - `npm init -y`
>   - cria o arquivo `package.json` com as configurações padrão do projeto.
>   - [veja na lista de comandos: npm init -y](/doc/comandos.md#npm_init_-y)
> - `npm install express sqlite sqlite3`
>   - instala os pacotes **express**, **sqlite** e **sqlite3** no projeto.
>   - [veja na lista de comandos: npm install](/doc/comandos.md#npm_install)
>   - [veja no glossário: Pacotes de produção](/doc/glossario.md#pacotes_de_producao)
> - `npm install --save-dev nodemon ts-node typescript  @types/express`
>   - instala os pacotes **nodemon**, **ts-node**, **typescript** e **@types/express** como dependências de desenvolvimento.
>   - [veja na lista de comandos: npm install --save-dev](/doc/comandos.md#npm_install_dev)
>   - [veja no glossário: Pacotes de desenvolvimento](/doc/glossario.md#pacotes_de_desenvolvimento)
> - `npx tsc --init`
>   - cria o arquivo **tsconfig.json** de configuração do TypeScript com as configurações padrão.
>   - [veja na lista de comandos: npx](/doc/comandos.md#npx)
>   - [veja na lista de comandos: npx tsc --init](/doc/comandos.md#npx_tsc_--init)
> - `git init`
>   - inicializa um repositório git no projeto.
>   - [veja na lista de comandos: git init](/doc/comandos.md#git_init)
>   - [veja no glossário: Git](/doc/glossario.md#git)

### Estrutura de Arquivos e Pastas

Neste passo vamos criar a estrutura de arquivos e pastas do projeto, a criação dos arquivos e pastas pode ser feita utilizando o próprio [VSCode](/doc/glossario.md#vscode) ou utilizando o [explorador de arquivos](/doc/glossario.md#explorador_de_arquivos) do sistema operacional ou ainda utilizando o [terminal](/doc/glossario.md#terminal), escolha a opção que preferir, porém neste guia vamos utilizar o terminal para criar os arquivos e pastas.

A estrutura de arquivos e pastas do projeto será a seguinte:

```
- src/
  - index.ts
  - database.ts
- public/
  - index.html
  - main.css
  - main.js
- .gitignore
```

> Entenda o que cada arquivo e pasta faz:
> ---
> - `src/`
>   - pasta onde ficarão os arquivos de código fonte da aplicação.
> - `src/index.ts`
>   - arquivo principal da aplicação.
> - `src/database.ts`
>   - arquivo de conexão com o banco de dados.
> - `public/`
>   - pasta onde ficarão os arquivos de front-end da aplicação.
> - `public/index.html`
>   - arquivo HTML inicial da aplicação.
> - `public/main.css`
>   - arquivo de estilos CSS principal da aplicação.
> - `public/main.js`
>   - arquivo de scripts JavaScript principal da aplicação.
> - `.gitignore`
>   - arquivo de configuração do git para ignorar arquivos e pastas no repositório.


#### Como criar a estrutura de arquivos e pastas

Como dito anteriormente, a criação dos arquivos e pastas pode ser feita utilizando o [VSCode](/doc/glossario.md#vscode), o [explorador de arquivos](/doc/glossario.md#explorador_de_arquivos) do sistema operacional ou o [terminal](/doc/glossario.md#terminal), escolha a opção que preferir, porém neste guia vamos utilizar o terminal para criar os arquivos e pastas.

Abaixo estão os comandos para criar a estrutura de arquivos e pastas utilizando o terminal, escolha o comando de acordo com o sistema operacional que você está utilizando.

##### Windows (powershell)

```powershell	
mkdir src
mkdir public
New-Item requests.http
New-Item .gitignore
New-Item src\index.ts
New-Item src\database.ts
New-Item public\index.html
New-Item public\main.css
New-Item public\main.js
```

##### Linux (bash)

```bash
mkdir src
mkdir public
touch requests.http
touch .gitignore
touch src/index.ts
touch src/database.ts
touch public/index.html
touch public/main.css
touch public/main.js
```

### Configurando scripts de execução

Scripts de execução são comandos que podem ser executados através do terminal para realizar tarefas específicas, como iniciar o servidor, compilar o código, entre outros comandos. Vamos configurar os scripts de execução do projeto.

Adicione os scripts no arquivo `package.json`:

```json
  ...
  "scripts": {
    "dev": "nodemon src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js"
  },
  ...
```
> - [Para saber mais sobre scripts de execução, veja na lista de comandos: npm run <script>](/doc/comandos.md#npm_run)

### Configuração do compilador TypeScript

No passo anterior, foi criado o arquivo de configuração do TypeScript (`tsconfig.json`) com as configurações padrão. Vamos alterar algumas configurações do TypeScript para informar ao compilador TypeScript onde salvar os arquivos compilados e como compilar o código TypeScript para Javascript.

Abra o arquivo `tsconfig.json` e altere a entrada `outDir: "./"` para `"outDir": "./dist"` no arquivo `tsconfig.json`. _note que é necessário remover o comentário `//` da linha, se não a configuração não será aplicada_, isto fara com que os arquivos compilados sejam salvos no diretório `dist` em vez do diretório raiz do projeto.

### Configuração .gitignore

O arquivo `.gitignore` é um arquivo de configuração do git que informa ao git quais arquivos e pastas devem ser ignorados pelo git, ou seja, quais arquivos e pastas não devem ser versionados no repositório git.

Adicione as seguintes entradas no arquivo `.gitignore`:

```gitignore
node_modules/
dist/

database.sqlite
```

## Desenvolvimento do Projeto

Aqui de fato iniciamos o desenvolvimento da aplicação, vamos criar o código fonte da aplicação, o banco de dados e os arquivos de front-end.

### Arquivo de conexão com o banco de dados

O arquivo de conexão com o banco de dados é responsável por criar a conexão com o banco de dados SQLite e criar a tabela de usuários caso ela não exista. Este arquivo exporta uma função `getDatabase` que retorna a instância do banco de dados, certificando-se de que apenas uma instância do banco de dados seja criada.

Adicione o seguinte código no arquivo `src/database.ts`:

```typescript
import { open, Database } from 'sqlite'
import sqlite3 from 'sqlite3'

let instance: Database | null = null

export async function getDatabase() {
  if (instance)
    return instance

  const db = await open({
    filename: './database.sqlite',
    driver: sqlite3.Database
  })

  await db.exec(`
    CREATE TABLE IF NOT EXISTS users (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      name TEXT,
      email TEXT
    )
  `)

  instance = db

  return db
}
```

GHFDSRGFTHYJKL

### Arquivo principal da aplicação

Adicione o seguinte código no arquivo `src/index.ts`:

```typescript
import express from 'express'
import { getDatabase } from './database'

const port = 3000
const app = express()

app.use(express.json())
app.use(express.static(__dirname + '/../public'))

app.get('/users', async (req, res) => {
  try {
    const db = await getDatabase()
    const users = await db.all('SELECT * FROM users')
    res.json(users)
  } catch (error) {
    res.status(500)
    res.json({ error: error.message })
  }
})

app.post('/users', async (req, res) => {
  try {
    const db = await getDatabase()
    const { name, email } = req.body
    const { lastID } = await db.run('INSERT INTO users (name, email) VALUES (?, ?)', [name, email])
    res.json({ id: lastID, name, email })
  } catch (error) {
    res.status(500)
    res.json({ error: error.message })
  }
})

app.put('/users/:id', async (req, res) => {
  try {
    const db = await getDatabase()
    const { name, email } = req.body
    const { id } = req.params
    await db.run('UPDATE users SET name = ?, email = ? WHERE id = ?', [name, email, id])
    res.json({ id, name, email })
  } catch (error) {
    res.status(500)
    res.json({ error: error.message })
  }
})

app.delete('/users/:id', async (req, res) => {
  try {
    const db = await getDatabase()
    const { id } = req.params
    await db.run('DELETE FROM users WHERE id = ?', id)
    res.json({ id })
  } catch (error) {
    res.status(500)
    res.json({ error: error.message })
  }
})

app.listen(port, () => console.log(`⚡Server running on port ${port}`))
```

### Arquivo de teste de requisições

Adicione o seguinte código no arquivo `requests.http`:

```http
#### Listar usuários

GET http://localhost:3000/users

#### Adicionar usuário

POST http://localhost:3000/users 
Content-Type: application/json

{
  "name": "John Doe",
  "email": "doe@mail.com"
}

#### Atualizar usuário

PUT http://localhost:3000/users/1
Content-Type: application/json

{
  "name": "Jane Doe",
  "email": "doe@mail.com"
}

#### Deletar usuário

DELETE http://localhost:3000/users/1
```