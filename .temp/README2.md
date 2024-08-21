# UNIDADE 1 - Conceitos Básicos de Desenvolvimento Web

# JavaScript

O JavaScript é uma linguagem de programação de alto nível, dinâmica e orientada a objetos, amplamente utilizada no desenvolvimento de aplicações web. Ela é executada no lado do cliente, ou seja, no navegador do usuário, e permite a criação de páginas web interativas e dinâmicas. O JavaScript é uma das linguagens de programação mais populares e é amplamente utilizada em projetos de todos os tamanhos e complexidades.

## Constantes e Variáveis

As constantes e variáveis são utilizadas para armazenar valores em um programa JavaScript. As constantes são declaradas com a palavra-chave `const` e não podem ser alteradas após a sua inicialização, enquanto as variáveis são declaradas com a palavra-chave `let` e podem ser alteradas ao longo do programa. Por exemplo:

```javascript
const PI = 3.14159
let radius = 10
let area = PI * radius * radius
```

## Desestruturação

A desestruturação é uma técnica do JavaScript que permite extrair valores de objetos e arrays e atribuí-los a variáveis individuais. Ela é útil para acessar propriedades de objetos e elementos de arrays de forma mais concisa e legível. Por exemplo:

```javascript
const person = { name: 'John Doe', age: 30 }
const { name, age } = person
console.log(name, age) // John Doe 30
```

## Callbacks

Os callbacks são funções que são passadas como argumentos para outras funções e executadas após a conclusão de uma operação. Eles são amplamente utilizados em Javascript para lidar com operações assíncronas, como requisições HTTP, leitura de arquivos, e eventos de usuário. Os callbacks permitem que o código seja executado de forma não sequencial, o que é útil para operações que levam tempo para serem concluídas.

```javascript
function fazAlgo(callback) {
  callback({ id: 1, name: 'John Doe' })
}

fazAlgo((data) => {
  console.log(data)
})
```

## Arrow Functions

As arrow functions são uma forma mais concisa de escrever funções em Javascript. Elas são definidas com a sintaxe `() => {}` e não possuem a palavra-chave `function`. As arrow functions são úteis para escrever funções simples e expressivas de forma mais clara e legível. muito utilizadas em callbacks e funções de ordem superior.

```javascript
const sum = (a, b) => a + b
const square = (x) => x * x
```

## Promises e Async/Await

As Promises e o Async/Await são recursos do Javascript que permitem lidar com operações assíncronas de forma mais eficiente e legível. As Promises são objetos que representam o resultado de uma operação assíncrona, e permitem encadear operações assíncronas de forma mais clara e concisa. O Async/Await é uma sintaxe que simplifica o uso de Promises, permitindo que o código assíncrono seja escrito de forma síncrona.

## Cliente e Servidor

O conceito de cliente e servidor é fundamental para a comunicação entre computadores em uma rede. O cliente é o dispositivo que solicita um serviço, enquanto o servidor é o dispositivo que fornece o serviço solicitado. A comunicação entre cliente e servidor é feita através de um protocolo de comunicação, o protocolo que utilizaremos neste curso é o HTTP, poreḿ existem muitos outros protocolos como o FTP, SMTP, SSH, WebSocket, SNMP entre outros.

É senso comum imaginar que servidores são grandes computadores em data centers, enquanto clientes são dispositivos como computadores, smartphones, tablets, e outros dispositivos conectados à internet. No entanto, o conceito de cliente e servidor é mais abstrato e pode ser aplicado a qualquer sistema de comunicação entre dispositivos, como um navegador web e um servidor web, um aplicativo móvel e um servidor de banco de dados, ou um dispositivo IoT e um servidor de nuvem.

Imagine que o cliente seja um navegador web, como o Google Chrome, Mozilla Firefox, Microsoft Edge, Brave, Safari, entre outros, e o servidor seja um programa que fornece páginas web, como o Apache, Nginx, IIS, Express, Django, Spring, entre outros. Quando você digita um endereço na barra de endereços do navegador, O navegador envia uma requisição HTTP para o servidor solicitando uma página web, e o servidor processa a requisição e envia responde a página de volta para o navegador, que a exibe na tela.

Como abstração imagine que a pessoa sentada a mesa de um restaurante é o cliente, e o garçom é o protocolo de comunicação, eo cozinheiro é o servidor, o cliente solicita um prato ao garçom que por sua vez entrega ao cozinheiro, o cozinheiro prepara o prato e entrega ao garçom que entrega ao cliente.

Neste exemplo o cliente é o navegador, o garçom é o protocolo HTTP, o cozinheiro é o servidor web, o prato é a página web, o restaurante é o servidor, e a pessoa na mesa é o cliente.

> - [MDN Web Docs - Visão geral do cliente-servidor](https://developer.mozilla.org/pt-BR/docs/Learn/Server-side/First_steps/Client-Server_overview)

## Protocolo HTTP

O HTTP (Hypertext Transfer Protocol) é um protocolo de comunicação utilizado para transferir informações na World Wide Web. Ele define a estrutura das mensagens de requisição e resposta entre o cliente e o servidor. As mensagens são compostas por um cabeçalho e um corpo, onde o cabeçalho contém informações sobre a requisição ou resposta, e o corpo contém os dados a serem transferidos.

Sempre que o cliente solicita um recurso ao servidor, ele envia uma mensagem de requisição seguindo as diretrizes do protocolo HTTP. O servidor processa a requisição e envia uma mensagem de resposta de volta para o cliente, esta resposta também segue as diretrizes do protocolo HTTP.

Nos proximos tópicos vamos abordar os conceitos de requisição e resposta HTTP e as diretrizes do protocolo HTTP para comunicação entre cliente e servidor.

> - [MDN Web Docs - HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP)

### Requisição HTTP

Uma requisição HTTP é uma mensagem enviada pelo cliente para o servidor solicitando um recurso ou a execução de uma operação. Ela é composta por um método, uma URL, um cabeçalho, e um corpo. Os métodos HTTP mais comuns são `GET`, `POST`, `PUT`, `DELETE`, que são utilizados para obter dados, enviar dados, atualizar dados, e deletar dados, respectivamente.

Isso significa que quando o cliente acessa uma página web, o navegador envia um "arquivo" de requisição para o servidor solicitando o recurso/página este arquivo precisa seguir o padrão estipulado pelo protocolo HTTP, caso contrário o servidor não irá entender a requisição, assim como o cliente não irá entender a resposta caso esta não siga o padrão estipulado pelo protocolo.

O arquivo de requisição que o cliente envia para o servidor segue o padrão estipulado pelo protocolo HTTP, e é composto por:

```http
MÉTODO URL PROTOCOLO/VERSÃO
Cabeçalho1: valor1
Cabeçalho2: valor2
CabeçalhoN: valorN

Corpo da requisição
```

1. `MÉTODO`  
  - O método HTTP utilizado na requisição, como `GET`, `POST`, `PUT`, `DELETE` entre outros.
    - GET: Recupera dados de um recurso.
    - POST: Envia dados para serem processados por um recurso.
    - PUT: Atualiza dados de um recurso.
    - PATCH: Atualiza parcialmente um recurso.
    - DELETE: Deleta um recurso.
    - OPTIONS: Retorna os métodos HTTP suportados por um recurso.
    - HEAD: Retorna apenas os cabeçalhos de uma resposta.
    - Veja mais em [MDN Web Docs - Métodos HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Methods)

2. `URL`  
  - A URL do recurso solicitado, conforme será visto no item [URL - Uniform Resource Locator](#ancora-url).

3. `PROTOCOLO/VERSÃO`
  - O protocolo e a versão do HTTP utilizados na requisição, exemplo: `HTTP/1.1`.

4. `Cabeçalho1: valor1`
    `Cabeçalho2: valor2`
    `CabeçalhoN: valorN`
  - Considere cabeçaçhos como informações adicionais que são enviadas junto com a requisição, por exemplo o tipo de conteúdo que está sendo enviado, o tipo de conteúdo que o cliente aceita, o tipo de conteúdo que o cliente espera receber, entre outros.
  - No exemplo `Content-Type: application/json`, o cabeçalho `Content-Type` indica que o conteúdo enviado no corpo da requisição é do tipo `application/json`.

5. `Corpo da requisição`
  - O corpo da requisição é utilizado para enviar dados ao servidor, como formulários, arquivos, e outros tipos de dados.


> **Importante:** O corpo da requisição é opcional e não é utilizado em todos os tipos de requisições; porém a linha em branco entre o cabeçalho e o corpo é obrigatória.


Veja um exemplo de requisição HTTP `GET`:

```http
GET https://www.google.com/ HTTP/1.1
Host: www.google.com
User-Agent: Mozilla/5.0
```

Veja um exemplo de requisição HTTP `POST`:

```http
POST https://api.example.com/users HTTP/1.1
Content-Type: application/json

{
  "name": "John Doe",
  "email": "
}
```

> Note que o cabeçalho `Content-Type` é utilizado para indicar para o servidor o tipo de conteúdo que está sendo enviado no corpo da requisição.

### Resposta HTTP

Uma resposta HTTP é uma mensagem enviada pelo servidor para o cliente em resposta a uma requisição. Ela é composta por um código de status, um cabeçalho, e um corpo. O código de status indica se a requisição foi bem-sucedida, redirecionada, ou se ocorreu um erro. Os códigos de status mais comuns são `200 OK`, `301 Moved Permanently`, `404 Not Found`, `500 Internal Server Error`, entre outros.

O arquivo de resposta que o servidor envia para o cliente segue o padrão estipulado pelo protocolo HTTP, e é composto por:

```http
PROTOCOLO/VERSÃO CÓDIGO DE STATUS DESCRIÇÃO
Cabeçalho1: valor1
Cabeçalho2: valor2
CabeçalhoN: valorN

Corpo da resposta
```

1. `PROTOCOLO/VERSÃO`  
  - O protocolo e a versão do HTTP utilizados na resposta, como `HTTP/1.1`.

2. `CÓDIGO DE STATUS`
  - O codigo de status é um número de 3 dígitos que indica o resultado da requisição, os códigos de status são divididos em cinco classes, cada classe representa um tipo de resultado, por exemplo, os códigos de status `2xx` indicam sucesso, os códigos de status `3xx` indicam redirecionamento, os códigos de status `4xx` indicam erro do cliente, e os códigos de status `5xx` indicam erro do servidor.
  - [MDN Web Docs - Códigos de status HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)

3. `DESCRIÇÃO`
  - A descrição do código de status, como `OK`, `Moved Permanently`, `Not Found`.
  - [MDN Web Docs - Códigos de status HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)

4. `Cabeçalho1: valor1`
  - Do mesmo modo que na requisição, os cabeçalhos são informações adicionais que são enviadas junto com a resposta, por exemplo o tipo de conteúdo que está sendo enviado, o tipo de conteúdo que o cliente aceita, o tipo de conteúdo que o cliente espera receber, entre outros.

5. `Corpo da resposta`
  - Assim como na requisição, o corpo da resposta é utilizado para enviar dados ao cliente, como páginas web, arquivos, e outros tipos de dados.

Veja um exemplo de resposta HTTP `200 OK`:
  
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "John Doe",
  "email": "
}
```

Veja um exemplo de resposta HTTP `404 Not Found`:

```http
HTTP/1.1 404 Not Found
Content-Type: text/plain

Página não encontrada
```

> **Importante:** O corpo da resposta é opcional e não é utilizado em todos os tipos de respostas; porém a linha em branco entre o cabeçalho e o corpo é obrigatória, assim como na requisição.

<a id="ancora-url"></a>

### URL - Uniform Resource Locator / URI - Uniform Resource Identifier

Parte essencial da requisição HTTP a URL/URI é o endereço do recurso que está sendo solicitado, a URL é composta por vários componentes, como o protocolo, o domínio, a porta, o caminho e a query string. A URL é utilizada para identificar e localizar recursos na web, como páginas web, imagens, arquivos, e outros tipos de conteúdo.

> Chamamos de rotas no Express, que são os caminhos que o servidor irá responder, por exemplo `/users`, `/products`, `/search`.

A estrutura de uma URL é a seguinte:

```
protocolo://domínio:porta/caminho?query
```

1. `protocolo`
  - O protocolo utilizado para acessar o recurso, como `http`, `https`, `ftp` etc.

2. `domínio`
  - O domínio do servidor que hospeda o recurso, Exemplo `www.google.com`, `api.example.com`, `localhost`, endereco-ip etc.

3. `porta`
  - A porta do servidor que está escutando as requisições, como `80`, `443`, `3000` etc.
  - Caso a porta não seja especificada, o navegador utiliza a porta padrão do protocolo, como `80` para `http` e `443` para `https`.
  - Para mais: [MDN Web Docs - Glossário Porta](https://developer.mozilla.org/pt-BR/docs/Glossary/Port)

4. `caminho`
  - O caminho do recurso no servidor, como `/search`, `/users`, `/products` etc.

5. `query`
  - A query string contém parâmetros adicionais que são enviados para o servidor, o padrão é `chave=valor`, separados por `&`, por exemplo `?q=nodejs&lang=pt-br`.
  - [Wikipedia - Query string](https://en.wikipedia.org/wiki/Query_string)


## JSON - Javascript Object Notation

O JSON (Javascript Object Notation) é um formato de dados leve e independente de linguagem que é fácil de ler e escrever. Ele é amplamente utilizado para troca de dados entre sistemas e aplicações web devido à sua simplicidade e legibilidade. O JSON é baseado em pares de chave-valor e suporta tipos de dados como strings, números, booleanos, arrays e objetos.

Nas requisições e respostas HTTP, o JSON é frequentemente utilizado para enviar e receber dados entre o cliente e o servidor. Por exemplo, ao enviar dados de um formulário para o servidor, os dados são enviados em formato JSON no corpo da requisição, e o servidor processa os dados e envia uma resposta em formato JSON no corpo da resposta.

O JSON é uma forma de representar dados de forma estruturada, por exemplo, um objeto Javascript pode ser representado em JSON da seguinte forma:

```json
{
  "name": "John Doe",
  "age": 30,
  "email": "doe@mail.com"
}
```

O JSON é amplamente utilizado em APIs RESTful para enviar e receber dados entre o cliente e o servidor. Ele é suportado nativamente pelo Javascript e por muitas outras linguagens de programação.

> - [JSON.org - Introdução ao JSON](https://www.json.org/json-pt.html)
> - [MDN Web Docs - JSON](https://developer.mozilla.org/pt-BR/docs/Web/Javascript/Reference/Global_Objects/JSON)

## Node.js

O Node.js é uma plataforma de desenvolvimento de aplicações em Javascript que permite a execução de código Javascript no lado do servidor. Ele utiliza o motor V8 do Google Chrome para executar o código Javascript de forma eficiente e escalável. Com o Node.js, é possível criar servidores web, APIs, aplicações de linha de comando, e muito mais.

O Node.js é amplamente utilizado no desenvolvimento de aplicações web devido à sua facilidade de uso, desempenho e escalabilidade. Ele fornece um conjunto de módulos e bibliotecas que facilitam a criação de aplicações robustas e eficientes.

> - [MDN Web Docs - Node.js](https://developer.mozilla.org/pt-BR/docs/Glossario/Node.js)

### Módulos no Node.js (export/import)

Os módulos no Node.js são arquivos Javascript que exportam funções, classes, objetos ou valores para serem utilizados em outros arquivos. Para exportar um valor de um módulo, utiliza-se a palavra-chave `export`, e para importar um valor de um módulo, utiliza-se a palavra-chave `import`. Por exemplo:

```javascript
// arquivo: utils.js
export function sum(a, b) {
  return a + b
}
``` 

```javascript
// arquivo: index.js
import { sum } from './utils.js'

console.log(sum(2, 3)) // 5
```

Exportar e importar módulos no Node.js permite a reutilização de código e a organização de funcionalidades em arquivos separados.

Existe também a possibilidade de exportar um valor padrão de um módulo, que pode ser importado sem a necessidade de utilizar chaves `{}`. Por exemplo:

```javascript
// arquivo: utils.js
export default function sum(a, b) {
  return a + b
}
```

```javascript
// arquivo: index.js
import sum from './utils.js'

console.log(sum(2, 3)) // 5
```

> É importante ressaltar que um módulo pode exportar apenas um valor padrão, enquanto pode exportar vários valores nomeados. O mesmo arquivo pode exportar valores nomeados e um valor padrão ao mesmo tempo.

## Express - Servidor Web

O Express é um framework web para Node.js que simplifica o desenvolvimento de aplicações web. Ele fornece uma série de recursos e funcionalidades para criar servidores web de forma rápida e eficiente. Com o Express, é possível definir rotas, tratar requisições, gerenciar sessões, e muito mais.

### Middleware

Os middlewares no Express são funções que recebem os objetos de requisição (no exemplo nomeado como `req`), resposta (no exemplo nomeado como `res`), e a próxima função middleware (no exemplo nomeado como `next`) no ciclo de requisição-resposta. Eles são utilizados para executar tarefas como autenticação, autorização, validação de dados, e tratamento de erros. Por exemplo:

```javascript
app.use((req, res, next) => {
  console.log('Middleware executado')
  next()
})
```

Este exemplo de middleware imprime uma mensagem no console toda vez que uma requisição é feita ao servidor, independente da rota, pois foi utilizado o método `use` para definir o middleware. É possível definir middlewares para rotas específicas, utilizando o método `get`, `post`, `put`, `delete`, entre outros.
  
```javascript
app.get('/users', (req, res, next) => {
  console.log('Middleware executado para a rota /users')
  next()
})
```

A chamada da função `next()` é utilizada para passar o controle para o próximo middleware na cadeia de middlewares, isso permite que por exemplo, um middleware de autenticação seja executado antes de um middleware de tratamento de requisição.

Os middlewares são executados na ordem em que são definidos, e podem ser utilizados para processar requisições antes de serem tratadas pelas rotas.

## API

Uma API (Application Programming Interface) é um conjunto de regras e padrões que define como os componentes de software interagem entre si. As APIs são utilizadas para permitir a comunicação entre diferentes sistemas, serviços, e aplicações. As APIs podem ser do tipo RESTful, GraphQL, SOAP, entre outros.

Neste curso, vamos abordar as APIs RESTful, que são amplamente utilizadas na web para criar serviços web que seguem os princípios da arquitetura REST (Representational State Transfer). As APIs RESTful utilizam métodos HTTP como `GET`, `POST`, `PUT`, `DELETE` para manipular recursos e representar o estado do sistema como recursos acessíveis por URLs.

### RESTful

Uma API RESTful é uma API baseada nos princípios da arquitetura REST (Representational State Transfer). Ela utiliza métodos HTTP como `GET`, `POST`, `PUT`, `DELETE` para manipular recursos e representa o estado do sistema como recursos acessíveis por URLs. As APIs RESTful são amplamente utilizadas na web devido à sua simplicidade e flexibilidade.

Os recursos em uma API RESTful são representados por URLs, e as operações sobre esses recursos são realizadas através dos métodos HTTP. Por exemplo, para obter uma lista de usuários, utiliza-se o método `GET` na rota `/users`, para adicionar um novo usuário, utiliza-se o método `POST` na rota `/users`, e assim por diante.

> **Importante:** rotas são os caminhos que o servidor irá responder, por exemplo `/users`, `/products`, `/search`.

A relação entre os métodos HTTP e as operações sobre os recursos em uma API RESTful é a seguinte:

| Método HTTP | Operação | Banco de Dados | Descrição                                     |
| ----------- |:--------:|:--------------:| --------------------------------------------- |
| POST        | Create   | INSERT         | Cria um novo recurso.                         |
| GET         | Read     | SELECT         | Recupera um recurso ou uma lista de recursos. |
| PUT         | Update   | UPDATE         | Atualiza um recurso existente.                |
| Patch       | Update   | UPDATE         | Atualiza parcialmente um recurso existente.   |
| DELETE      | Delete   | DELETE         | Deleta um recurso existente.                  |

> Note que as primeiras letras de cada operação formam a sigla CRUD, que é utilizada para descrever as operações básicas de um sistema de gerenciamento de banco de dados.

> - [MDN Web Docs - RESTful](https://developer.mozilla.org/pt-BR/docs/Glossario/REST)

## TypeScript

O TypeScript é um superset de Javascript que adiciona tipagem estática, interfaces, classes, e outros recursos ao Javascript. Ele é transpilado para Javascript puro, permitindo a utilização de recursos modernos do Javascript em navegadores e ambientes Node.js. O TypeScript é amplamente utilizado em projetos de grande escala devido à sua capacidade de detectar erros em tempo de compilação.

> - Superset é um conjunto de recursos adicionais que estendem a linguagem base, no caso o Javascript.
> - Transpilar é o processo de compilar um código de uma linguagem para outra, no caso o TypeScript para Javascript.
> - Tipagem estática é a definição dos tipos de dados das variáveis, parâmetros, e retornos de funções em tempo de compilação.
> - Interfaces são contratos que definem a estrutura de um objeto, como os métodos e propriedades que ele deve possuir.
> - Classes são estruturas que permitem a definição de objetos com métodos e propriedades.

> - [TypeScript para o novo desenvolvedor](https://www.typescriptlang.org/pt/docs/handbook/typescript-from-scratch.html)
> - [TypeScript - Documentação](https://www.typescriptlang.org/docs/)

## Ts-node

O `ts-node` é um interpretador TypeScript que permite executar código TypeScript diretamente no Node.js, ele faz com que não seja necessário compilar o código TypeScript para Javascript antes de executá-lo, em realidade ele compila o código em tempo de execução na memória do computador. Ele é útil para desenvolvimento e testes, pois ele não gera arquivos `.js` em disco.

> - [ts-node - GitHub](https://github.com/TypeStrong/ts-node)

## Nodemom

O `nodemon` é uma ferramenta que monitora as alterações em arquivos de um projeto Node.js e reinicia automaticamente o servidor quando detecta uma alteração. Ele é útil para desenvolvimento, pois permite visualizar as alterações no código em tempo real sem a necessidade de reiniciar o servidor manualmente. O `nodemon` é amplamente utilizado em projetos Node.js para aumentar a produtividade dos desenvolvedores.

> - [nodemon](https://nodemon.io/)

## Banco de Dados

Um banco de dados é um sistema de armazenamento de dados que permite a organização, consulta e manipulação de informações de forma eficiente. Existem vários tipos de bancos de dados, como bancos de dados relacionais (SQL) e bancos de dados não relacionais (NoSQL). Cada tipo de banco de dados possui suas próprias características e utilizações específicas.

> - [Wiki - Banco de Dados](https://pt.wikipedia.org/wiki/Banco_de_dados)

### SQLite

O SQLite é um banco de dados relacional embutido que não requer um servidor separado para funcionar. Ele é amplamente utilizado em aplicações móveis, aplicações desktop, e aplicações web devido à sua simplicidade, eficiência e facilidade de uso. O SQLite armazena os dados em um arquivo de banco de dados local, o que o torna uma escolha popular para aplicações que não requerem um servidor de banco de dados dedicado.

Sua simplicidade implica em não possuir muitos recursos que outros bancos de dados possuem, como por exemplo, triggers, stored procedures, e funções definidas pelo usuário além de não possuir suporte a tipos de dados como `DATE`, `TIME`, `DATETIME`, `BOOLEAN`, `ENUM`, `JSON`, `XML` entre outros. Isso o torna uma escolha popular para aplicações pequenas e médias que não requerem recursos avançados de um banco de dados relacional e nem acesso simultâneo de muitos usuários.

> - [SQLite](https://www.sqlite.org/index.html)

<a id="ancora-git"></a>

## GIT

O Git é um sistema de controle de versão distribuído que permite o rastreamento de alterações em arquivos e diretórios ao longo do tempo. Ele é amplamente utilizado no desenvolvimento de software para colaboração, gerenciamento de código-fonte, e controle de versão de projetos. O Git fornece uma série de comandos e funcionalidades para criar, clonar, modificar, e compartilhar repositórios de código.

### GITHUB

O GitHub é uma plataforma de hospedagem de código-fonte baseada em Git que permite o compartilhamento, colaboração e publicação de projetos de software. Ele fornece recursos como controle de versão, rastreamento de problemas, integração contínua, e hospedagem de páginas web. O GitHub é amplamente utilizado por desenvolvedores, equipes e empresas para gerenciar projetos de software e colaborar em código-fonte.

--------------------------------------------------------------------------------

# UNIDADE 2 - Criando um Servidor Web com Node.js e Express

Nesta unidade, vamos criar um servidor web simples utilizando o Node.js e o Express. O servidor irá fornecer uma API RESTful para manipulação de usuários em um banco de dados SQLite. Vamos abordar os seguintes tópicos:

- Configuração do ambiente de desenvolvimento
- Criação do arquivo de conexão com o banco de dados
- Criação do arquivo do servidor Express
- Teste do servidor com requisições HTTP

Para este tutorial, você precisará instalar os seguintes softwares:

- [Visual Studio Code](https://code.visualstudio.com/)
- [NodeJs](https://nodejs.org/)
- [Git](https://git-scm.com/)

## Configuração do ambiente de desenvolvimento

Para criar um servidor web com Node.js e Express, é necessário configurar o ambiente de desenvolvimento com as dependências necessárias e a estrutura de arquivos do projeto. Vamos instalar as dependências do projeto, inicializar o projeto com o Node.js e o TypeScript, e configurar a estrutura de arquivos e os scripts de execução.

Os comandos a seguir devem ser executados no terminal do Visual Studio Code ou em um terminal de sua preferência. Abra o terminal no Visual Studio Code clicando em `Terminal > New Terminal`, estes comandos devem ser executados na raiz do projeto e eles respectivamente irão inicializar o projeto, instalar as dependências, criar o arquivo deconfiguração do TypeScript, e inicializar o repositório Git.

```bash	
npm init -y
npm install express cors sqlite sqlite3
npm install --save-dev nodemon ts-node typescript  @types/express @types/cors
npx tsc --init
git init
```

### Entendendo os comandos

1. `npm init -y`  
  - Inicializa um novo projeto Node.js com as configurações padrão.
  - O parâmetro `-y` indica que as configurações padrão devem ser utilizadas.
  - Caso o parâmetro `-y` não seja utilizado, o npm irá solicitar a entrada de informações adicionais para configurar o projeto.

2. `npm install express cors sqlite sqlite3`  
  - Instala as dependências do projeto: `express`, `cors`, `sqlite`, e `sqlite3`.

3. `npm install --save-dev nodemon ts-node typescript  @types/express @types/cors`
  - Instala as dependências de desenvolvimento: `nodemon`, `ts-node`, `typescript`, `@types/express`, e `@types/cors`.
  - Dependências de desenvolvimento são utilizadas apenas durante o desenvolvimento do projeto e não são necessárias em ambientes de produção.

4. `npx tsc --init`
  - Inicializa o arquivo de configuração do TypeScript (`tsconfig.json`).
  - tsc é o compilador TypeScript, e o comando `--init` cria um arquivo de configuração com as configurações padrão.
  - Para executar o `tsc` foi utilizado o `npx`, que permite executar comandos de pacotes instalados localmente sem a necessidade de instalar globalmente.
  - O arquivo `tsconfig.json` contém as configurações do compilador TypeScript, como o diretório de saída dos arquivos compilados, o nível de compatibilidade com o Javascript, e outras opções.

5. `git init`
  - Inicializa um repositório Git local para o projeto.
  - O Git é um sistema de controle de versão distribuído que permite rastrear alterações em arquivos e diretórios ao longo do tempo.
  - [O que é Git?](#ancora-git)

### Estrutura de arquivos

Chamamos de estrutura de arquivos a organização dos diretórios e arquivos de um projeto. Para este projeto, vamos criar uma estrutura de arquivos simples com os diretórios `src` e `public`, e os arquivos `index.ts`, `database.ts`, `index.html`, `main.css`, e `main.js`.

A estrutura de arquivos do projeto será a seguinte:

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

Existem muitas maneiras para a criação de diretórios e arquivos, dependendo do sistema operacional que eteja utilizando. Abaixo estão exemplos de como criar esses diretórios e arquivos no Windows (powershell) e no Linux (bash).

Mas é importante ressaltar que você pode criar esses diretórios e arquivos manualmente, sem a necessidade de usar comandos no terminal.

#### Windows (powershell)

Atualmente o Windows possui dois terminais, o `cmd` e o `powershell`, o `powershell` é mais poderoso e atual que o `cmd`, por isso utilizaremos o `powershell` para criar os diretórios e arquivos neste exemplo.

Para isso se estiver em uma maquina Windows, o terminal do Visual Studio Code é o `powershell`, caso esteja utilizando o `cmd` você pode mudar para o `powershell` clicando no botão `Select Default Shell` no canto superior direito do terminal, e executando os seguintes comandos:

```powershell	
mkdir src
mkdir public
New-Item .gitignore
New-Item src\index.ts
New-Item src\database.ts
New-Item public\index.html
New-Item public\main.css
New-Item public\main.js
```

#### Linux (bash)

O bash é o terminal padrão dos sistemas operacionais Linux e MacOS, porém assim como no windows o Linux possui outros terminais, como o `zsh`, o `fish`, e o `ksh`, no entanto o `bash` é o mais comum e é o que será utilizado neste exemplo.

Se estiver em uma maquina Linux, você pode executar os seguintes comandos no terminal do Visual Studio Code ou em um terminal de sua preferência:

```bash
mkdir src
mkdir public
touch .gitignore
touch src/index.ts
touch src/database.ts
touch public/index.html
touch public/main.css
touch public/main.js
```

### Configurando o TypeScript

No passo anterior, foi criado o arquivo de configuração do TypeScript (`tsconfig.json`) com as configurações padrão. Vamos alterar algumas configurações do TypeScript para informar ao compilador TypeScript onde salvar os arquivos compilados e como compilar o código TypeScript para Javascript.

Abra o arquivo `tsconfig.json` e altere a entrada `outDir: "./"` para `"outDir": "./dist"` no arquivo `tsconfig.json`. _note que é necessário remover o comentário `//` da linha, se não a configuração não será aplicada_, isto fara com que os arquivos compilados sejam salvos no diretório `dist` em vez do diretório raiz do projeto.

### Configurando scripts de execução

Scripts de execução são comandos que podem ser executados a partir do terminal para realizar tarefas específicas, como iniciar o servidor, compilar o código, ou executar testes.

Por padrão desenvolvedores utilizam o `npm run dev` para iniciar o servidor em modo de desenvolvimento, `npm run build` para compilar o código TypeScript para Javascript, e `npm start` para iniciar o servidor em modo de produção.

Considerando que cada projeto tem suas particularidades, você deve configurar os scripts de execução de acordo com as necessidades do seu projeto e ainda assim outros desenvolvedores poderão executar os scripts de execução sem a necessidade de conhecer os detalhes da configuração, pois os scripts de execução são padronizados: `npm run dev`, `npm run build`, `npm start` etc.

Para configurar os scripts de execução, abra o arquivo `package.json` e adicione as seguintes entradas no objeto `scripts`:

```json
"scripts": {
    "dev": "nodemon src/index.ts",
    "build": "tsc",
    "start": "node dist/index.js"
},
```

### Configurando o git

O arquivo `.gitignore` é utilizado para especificar quais arquivos e diretórios devem ser ignorados pelo git. Isso é útil para evitar que arquivos temporários, arquivos de configuração, e arquivos gerados automaticamente sejam incluídos no repositório git.

Adicione as seguintes entradas no arquivo `.gitignore`:

```gitignore
node_modules/
dist/

database.sqlite
```

> - [O que é Git?](#ancora-git)
> - [Documentação do Git - .gitignore](https://git-scm.com/docs/gitignore)

## Criando o Arquivo de conexão Banco de Dados

Neste momento começaremos de fato a criar o servidor web com Node.js e Express. Vamos criar o arquivo de conexão com o banco de dados SQLite, que será responsável por abrir uma conexão com o banco de dados e criar a tabela de usuários. O arquivo de conexão com o banco de dados será utilizado pelo servidor Express para realizar operações de CRUD (Create, Read, Update, Delete) sobre os usuários.

Adicione o seguinte código no arquivo `src/database.ts`:

```typescript
// 1. Importação de módulos
import { open, Database } from 'sqlite'
import sqlite3 from 'sqlite3'

// 2. Variavel global para armazenar a instância do banco de dados
let instance: Database | null = null

// 3. Definição da função para obter a instância do banco de dados
export async function getDatabase() {
  // 4. Verificação de instância existente
  if (instance)
    return instance

  // 5. Criação da instância do banco de dados
  const db = await open({
    filename: './database.sqlite',
    driver: sqlite3.Database
  })

  // 6. Criação da tabela de usuários
  await db.exec(`
    CREATE TABLE IF NOT EXISTS users (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      name TEXT,
      email TEXT
    )
  `)

  // 7. Armazenamento da instância do banco de dados
  instance = db

  // 8. Retorno da instância do banco de dados
  return db
}
```

### Entendendo o código

1. Importação de módulos
  - O módulo `sqlite` fornece uma API para interagir com o banco de dados SQLite.
    - `open` é uma função que abre uma conexão com o banco de dados.
    - `Database` é uma interface que representa um banco de dados SQLite.
  - O módulo `sqlite3` é o driver SQLite para o Node.js.
2. Variável global para armazenar a instância do banco de dados
  - A variável `instance` é utilizada para armazenar a instância do banco de dados e evitar a criação de múltiplas instâncias.
  - A variável é inicializada com o valor `null`, indicando que a instância ainda não foi criada.
3. Definição da função para obter a instância do banco de dados
  - A função `getDatabase` é exportada para ser utilizada em outros arquivos.
  - A função é assíncrona para permitir a utilização de `await` para aguardar a abertura da conexão com o banco de dados.
  - A função retorna a instância do banco de dados.
4. Verificação de instância existente
  - Este `if` verifica se a instância do banco de dados já foi armazenada na variável `instance`.
  - Se a instância já existe, a função retorna a instância existente, e evita a execução do restante da função evitando a criação de uma nova instância.
5. Criação da instância do banco de dados
  - A função `open` é utilizada para abrir uma conexão com o banco de dados SQLite.
  - Esta função recebe um objeto de configuração com o nome do arquivo do banco de dados e o driver SQLite.
    - `filename` é o nome do arquivo do banco de dados.
    - `driver` é o driver SQLite para o Node.js.
  - Esta função retorna uma promessa que é resolvida com a instância do banco de dados.
  - Após aguaardar a resolução da promessa, a instância do banco de dados é armazenada na variável `db`.
6. Criação da tabela de usuários
  - A função `exec` é utilizada para executar uma instrução SQL no banco de dados e retorna uma promessa.
  - O SQL utilizado cria uma tabela de usuários com os campos `id`, `name`, e `email`.
  - A instrução SQL é executada apenas se a tabela de usuários não existir, evitando a criação de uma tabela duplicada.
7. Armazenamento da instância do banco de dados
  - Após a criação da instância do banco de dados e da tabela de usuários, a instância é armazenada na variável `instance`.
  - Isso permite que a instância seja reutilizada em chamadas subsequentes à função `getDatabase`.
  - A verificação de instância existente no início da função evita a criação de múltiplas instâncias do banco de dados.
8. Retorno da instância do banco de dados

```typescript
import { open, Database } from 'sqlite'
import sqlite3 from 'sqlite3'
```

## Criando o Arquivo do Servidor Express (HTTP)

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

### Entendendo o código




## Testando o Servidor

Para testar o servidor, execute o comando `npm run dev` no terminal. O servidor será iniciado e estará pronto para receber requisições.

O browser não é capaz de enviar requisições do tipo `POST`, `PUT` e `DELETE` diretamente. Para testar essas rotas, você pode utilizar ferramentas como o [Postman](https://www.postman.com/) ou o [Insomnia](https://insomnia.rest/) e até mesmo o plugin para VSCode [Thunder Client](https://www.thunderclient.io/), porém, para testar a rota `GET` você pode acessar a URL `http://localhost:3000/users` diretamente no navegador, pois por padrão o navegador envia requisições do tipo `GET`.

Apesar do Postman e Insomnia serem ferramentas mais conhecidas, para este tutorial, vamos utilizar a extensão [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) do Visual Studio Code.

Para instalar a extensão, acesse o link acima e clique em `Install`. Após a instalação, crie um arquivo chamado `requests.http` na raiz do projeto e adicione o seguinte conteúdo:

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

Para executar as requisições, clique no botão `Send Request` que aparece ao lado de cada requisição.

--------------------------------------------------------------------------------

# UNIDADE 3 - Adicionando autenticação e autorização

## Autenticação

A autenticação é o processo de verificar a identidade de um usuário, geralmente por meio de credenciais como nome de usuário e senha. Ela é usada para garantir que apenas usuários autorizados tenham acesso a determinados recursos ou funcionalidades de um sistema.

## Autorização

A autorização é o processo de determinar se um usuário tem permissão para acessar um recurso ou executar uma operação específica. Ela é usada para controlar o acesso a recursos protegidos e garantir a segurança e a privacidade dos dados.

### JWT (JSON Web Token)

O JWT (JSON Web Token) é um padrão aberto (RFC 7519) que define um método compacto e seguro para transmitir informações entre partes como um objeto JSON. Ele é comumente usado para autenticação e autorização em aplicações web e APIs RESTful.

### Bcrypt

O Bcrypt é uma função de hash de senha que utiliza um algoritmo de criptografia de senha baseado no Blowfish. Ele é amplamente utilizado para armazenar senhas de forma segura em bancos de dados, protegendo-as contra ataques de força bruta e vazamentos de dados.
