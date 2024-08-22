# Glossário

## CRUD - Create, Read, Update, Delete <a id=crud />

CRUD é um acrônimo para Create, Read, Update, Delete, ele é utilizado para descrever as operações básicas de um sistema, as operações são:

- **Create**: Criar um novo recurso.
- **Read**: Ler um recurso existente.
- **Update**: Atualizar um recurso existente.
- **Delete**: Deletar um recurso existente.

Apesar de não ter referência com banco de dados, ou qualquer outra tecnologia, o CRUD é comumente utilizado para descrever operações em um banco de dados, por exemplo, criar um novo registro, ler um registro existente, atualizar um registro existente, deletar um registro existente.

## Path (_Caminho ou Diretório ou Endedereço ou Rota, etc._) <a id=file-path />

Path é o caminho do diretório que deseja acessar, pode ser um caminho absoluto ou relativo, chamamos de caminho absoluto o caminho que inicia na raiz do sistema de arquivos e o caminho relativo o caminho que inicia no diretório atual.

considere a seguinte estrutura de diretórios:

```plaintext
/pai
├─ filho
│   └─ neto
|      └─ bisneto
└─ filha
```

### Path: Caminho Absoluto

O caminho absoluto inicia na raiz do sistema de arquivos, no caso do Windows seria `C:\`, no Linux seria `/` e no MacOS seria `/`, neste exemplo o caminho absoluto para o diretório:

| Diretório | Caminho Absoluto           |
| ---------:| -------------------------- |
| pai       | /pai                       |
| filha     | /pai/filha                 |
| filho     | /pai/filho                 |
| neto      | /pai/filho/neto            |
| bisneto   | /pai/filho/neto/bisneto    |


### Path: Caminho Relativo

O caminho relativo inicia no diretório atual, neste exemplo vamos considerar que o diretório atual é o diretório `filho`, o caminho relativo para o diretório:

| Diretório | Caminho Relativo           |
| ---------:| -------------------------- |
| pai       | ..                         |
| filha     | ../filha                   |
| neto      | neto                       |
| bisneto   | neto/bisneto               |

### Path: .. (ponto ponto)

O `..` é utilizado para acessar o diretório anterior ao diretório atual, por exemplo, se você está no diretório `bisneto` e deseja acessar o diretório `filho`, o caminho `../..` irá acessar o diretório `filho`.

> ⚠️ **Atenção**
>
> 1. neste exemplo, a pasta `/pai` esta representando uma unidade de disco, no Windows seia algo como `C:\`, no Linux e MacOS seria `/`.
> 2. O Windows utiliza a barra invertida `\` para separar os diretórios, já o Linux e o MacOS utilizam a barra `/`.
 
Path é o caminho do diretório que deseja acessar, pode ser um caminho absoluto ou relativo, chamamos de caminho absoluto o caminho que inicia na raiz do sistema de arquivos e o caminho relativo o caminho que inicia no diretório atual.

considere a seguinte estrutura de diretórios:

```plaintext
/pai
├─ filho
│   └─ neto
|      └─ bisneto
└─ filha
```

## Cliente e Servidor <a id=client-server />

O cliente e o servidor são dois sistemas que se comunicam entre si, o cliente é o sistema que envia a requisição e o servidor é o sistema que recebe a requisição e envia uma resposta.

> ⚠️ **Atenção**
>
> 1. Cliente é um software que envia requisições para um servidor, por exemplo, um browser (Google Chrome, Mozilla Firefox, etc), um aplicativo (WhatsApp, Facebook, etc), um script (Python, Javascript, etc), etc.
> 2. É de senso comum que servidores são máquinas físicas enormes em algum lugar remoto, no entanto, um servidor pode ser uma máquina física, uma máquina virtual, um container, um serviço, etc. isso significa que um servidor pode ser um computador, um celular, um tablet, um relógio, um carro, um eletrodoméstico, etc. o que o torna um servidor é o fato dele receber e responder requisições de um cliente em uma rede respeitando um protocolo de comunicação.

> 💭 **Abstação**
>
> Considere que o cliente é um usuário que envia uma carta para um servidor, o servidor é o carteiro que recebe a carta e envia uma resposta.

### Cliente (_Client_) <a id=client />

Cliente é um sistema que envia requisições para um servidor, ele é composto por um software que envia a requisição, por exemplo, um browser (Google Chrome, Mozilla Firefox, etc), um aplicativo (WhatsApp, Facebook, etc), um script (Python, Javascript, etc), etc.

### Servidor (_Server_) <a id=server />

Servidor é um sistema que recebe requisições de um cliente e envia uma resposta, ele é composto por um software que recebe a requisição, processa a requisição e envia uma resposta, por exemplo, um servidor web (Apache, Nginx, etc), um servidor de banco de dados (MySQL, PostgreSQL, etc), um servidor de arquivos (FTP, SFTP, etc), etc.

## JSON - Javascript Object Notation <a id=json />

O JSON (Javascript Object Notation) é um formato de texto utilizado para representar objetos, ele é composto por pares de chave e valor, os valores podem ser strings, números, objetos, arrays, booleanos ou nulos.

JSON é um arquivo texto plano, que implica:

- Não é um objeto Javascript (ou de qualquer outra linguagem de programação), portanto o JSON precisa ser convertido para objeto antes de ser utilizado.
- Pode ser facilmente enviado e recebido no corpo de [requisições](#http-request) e [respostas](#http-response) do [protocolo HTTP](#http).
- É utilizado para enviar e receber informações estruturadas, por exemplo, enviar informações de um formulário, enviar informações de um usuário, etc.

É importante lembrar que o JSON não é o único formato de texto utilizado para representar objetos, existem outros formatos como o XML, YAML, TOML, etc.

Veja abaixo um exemplo de cada tipo de valor em JSON:

```json
{
  "string": "Hello, World!",
  "number": 42,
  "object": {"key": "value"},
  "array": [1, 2, 3],
  "boolean": true,
  "null": null
}
```

O formato também permite aninhamento de objetos e arrays, por exemplo:

```json
{
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "state": "NY"
  },
  "phones": ["555-1234", "555-5678"]
}
```

## Endereço IP <a id=ip-address />

O endereço IP (Internet Protocol) é um número que identifica um dispositivo em uma rede, ele é composto por 4 números de 0 a 255 separados por pontos, por exemplo, `192.168.0.1`, no protocolo IPv4 o endereço IP é composto por 32 bits, já no protocolo IPv6 o endereço IP é composto por 128 bits.

> 💭 **Abstação**
>
> Considere que o endereço IP é o número de telefone ou endereço do dispositivo, ele é utilizado para identificar o dispositivo na rede.

## Porta (redes de computadores) <a id=port />

A porta é um número que identifica um serviço em um dispositivo, ela é composta por 16 bits, ela é utilizada para identificar o serviço que deseja acessar, por exemplo, o serviço HTTP utiliza a porta 80, o serviço HTTPS utiliza a porta 443.

> 💭 **Abstação**
>
> Considere que o servidor é um predio, o endereço IP é o número do predio e a porta é o número do apartamento, cada apartamento é um serviço diferente.

## URL - Uniform Resource Locator <a id=url />

A URL (Uniform Resource Locator) é um endereço que identifica um recurso na internet, ela é composta por 3 partes, o protocolo, o domínio e o caminho, por exemplo, `https://www.google.com.br/search?q=hello`.

O modelo de uma URL é o seguinte:

```plaintext
protocol://domain/path?query
```

Entendendo a URL:
- `protocol`: é o protocolo utilizado para acessar o recurso, por exemplo, `http`, `https`, `ftp`.
- `domain`: é o domínio do recurso, por exemplo, `www.google.com.br` ou endereço IP.
- `path`: é o [caminho](#path) do recurso, por exemplo, `/search`
- `query`: é a [query string](#query-string) do recurso, por exemplo, `?q=hello`.

### URL: Query String <a id=url-query />

A query string é utilizada para enviar informações adicionais para o servidor, ela é composta por uma chave e um valor separados por `=`, os valores são separados por `&`, por exemplo, `?q=hello&lang=en`.

A query string é formatada da seguinte forma:

```plaintext
?chave_1=valor_1&chave_2=valor_2&chave_N=valor_N
```

Entendendo a query string:
- `?`: é utilizado para iniciar a query string.
- `chave_1=valor_1`, `chave_2=valor_2`, `chave_N=valor_N`: são as chaves e valores da query string, por exemplo, `q=hello`, `lang=en`.
- `&`: é utilizado para separar os valores da query string.

> 💭 **Abstação**
>
> Considere que a URL é o endereço do recurso, o protocolo é a forma de acessar o recurso, o domínio é o endereço do recurso, o caminho é o diretório do recurso e a query string é a informação adicional do recurso, por exemplo qual a linguagem que deseja acessar o recurso.

## Protocolo HTTP <a id=http />

O HTTP (Hypertext Transfer Protocol) é um protocolo de comunicação utilizado para transferir informações na internet, ele é utilizado para acessar páginas web, ele é composto por uma requisição e uma resposta.

Para que o browser consiga acessar uma página web, ele envia uma requisição para o servidor, o servidor processa a requisição e envia uma resposta para o browser, essa requisção e resposta devem seguir um padrão, esse padrão é o protocolo HTTP.

### Requisição HTTP <a id=http-request />

A requisição HTTP é composta por 3 partes, a linha de requisição, os cabeçalhos e o corpo, a linha de requisição é composta pelo método, o caminho e a versão do protocolo, os cabeçalhos são utilizados para enviar informações adicionais, o corpo é utilizado para enviar informações adicionais.

Abaixo temos um exemplo de uma requisição HTTP:

```http
METHOD URL PROTOCOL_VERSION
Header1: value1
Header2: value2
HeaderN: valueN

Body
```

Entendendo a requisição:

- `METHOD`: é o método utilizado para acessar o recurso, os métodos mais comuns são o `GET`, `POST`, `PUT`, `DELETE`, etc.
- `URL`: é o caminho do recurso que deseja acessar, por exemplo, `192.168.0.100/index.html`.
- `PROTOCOL_VERSION`: é a versão do protocolo HTTP, por exemplo, `HTTP/1.1`.
- `Header1: value1`, `Header2: value2`, `HeaderN: valueN`: são os cabeçalhos da requisição, são utilizados para enviar informações adicionais, por exemplo, `Content-Type: application/json`.
- `Body`: é o corpo da requisição, é utilizado para enviar informações adicionais, por exemplo, `{"name": "John Doe"}`.

Então, uma requisição HTTP completa seria algo como:

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{"name":"John Doe"}
```

> 💡 **Dica**
>
> 1. Neste exemplo o corpo da requisição é um JSON, o cabeçalho `Content-Type: application/json` informa que o corpo da requisição é um JSON.

#### Métodos HTTP <a id=http-method />

O método HTTP é utilizado o cliente para informar ao servidor qual ação deseja realizar, os métodos mais comuns são:

| Método | Descrição                                                                 | Exemplo                   |
| ------ | ------------------------------------------------------------------------- | ------------------------- |
| GET    | Recuperar informações do servidor                                         | `GET /api/users`          |
| POST   | Enviar informações para o servidor                                        | `POST /api/users`         |
| PUT    | Atualizar informações no servidor                                         | `PUT /api/users/1`        |
| DELETE | Deletar informações no servidor                                           | `DELETE /api/users/1`     |

Em nossa [API](#api) utilizaremos somente os métodos desta lista, no entanto, existem outros métodos HTTP, como o `PATCH`, `HEAD`, `OPTIONS`, `TRACE`, `CONNECT`, etc.

### Resposta HTTP <a id=http-response />

A resposta HTTP é composta por 3 partes, a linha de status, os cabeçalhos e o corpo, a linha de status é composta pelo código de status e a mensagem de status, os cabeçalhos são utilizados para enviar informações adicionais, o corpo é utilizado para enviar informações adicionais.

Abaixo temos um exemplo de uma resposta HTTP:

```http
PROTOCOL_VERSION STATUS_CODE STATUS_MESSAGE
Header1: value1
Header2: value2
HeaderN: valueN

Body
```

Entendendo a resposta:

- `PROTOCOL_VERSION`: é a versão do protocolo HTTP, por exemplo, `HTTP/1.1`.
- `STATUS_CODE`: é o código de status da resposta, por exemplo, `200`, `404`, `500`.
- `STATUS_MESSAGE`: é a mensagem de status da resposta, por exemplo, `OK`, `Not Found`, `Internal Server Error`.
- `Header1: value1`, `Header2: value2`, `HeaderN: valueN`: são os cabeçalhos da resposta, são utilizados para enviar informações adicionais, por exemplo, `Content-Type: application/json`.
- `Body`: é o corpo da resposta, é utilizado para enviar informações adicionais, por exemplo, `{"name": "John Doe"}`.

Então, uma resposta HTTP completa seria algo como:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"name":"John Doe"}
```

#### Status Code <a id=http-status-code />

O código de status é um número que informa o resultado da requisição, ele é composto por 3 dígitos, o primeiro dígito informa a classe do status, os códigos de status são divididos em 5 classes, na lista abaixo temos as classes e alguns dos códigos de status mais comuns:

##### 1xx: Informacional

Os códigos de status 1xx são utilizados para informar que a requisição foi recebida e está sendo processada.

| Código  | Mensagem            | Descrição                                                                   |
| ------- | ------------------- | --------------------------------------------------------------------------- |
| 100     | Continue            | O servidor recebeu a requisição e o cliente pode continuar com a requisição |
| 101     | Switching Protocols | O servidor está mudando os protocolos e o cliente deve mudar também         |
| 102     | Processing          | O servidor está processando a requisição, mas ainda não terminou            |

##### 2xx: Sucesso

Os códigos de status 2xx são utilizados para informar que a requisição foi bem sucedida.

| Código  | Mensagem   | Descrição                                                      |
| ------- | ---------- | -------------------------------------------------------------- |
| 200     | OK         | A requisição foi bem sucedida                                  |
| 201     | Created    | A requisição foi bem sucedida e um novo recurso foi criado     |
| 202     | Accepted   | A requisição foi aceita, mas ainda não foi processada          |
| 204     | No Content | A requisição foi bem sucedida, mas não há conteúdo para enviar |

##### 3xx: Redirecionamento

Os códigos de status 3xx são utilizados para informar que a requisição foi redirecionada.

| Código  | Mensagem          | Descrição                                      |
| ------- | ----------------- | ---------------------------------------------- |
| 300     | Multiple Choices  | A requisição tem mais de uma resposta possível |
| 301     | Moved Permanently | A requisição foi movida permanentemente        |
| 302     | Found             | A requisição foi movida temporariamente        |
| 304     | Not Modified      | A requisição não foi modificada                |

##### 4xx: Erro do Cliente

Os códigos de status 4xx são utilizados para informar que a requisição é inválida.

| Código  | Mensagem           | Descrição                                          |
| ------- | ------------------ | -------------------------------------------------- |
| 400     | Bad Request        | A requisição é inválida                            |
| 401     | Unauthorized       | O cliente não está autorizado                      |
| 403     | Forbidden          | O cliente não tem permissão para acessar o recurso |
| 404     | Not Found          | O recurso não foi encontrado                       |
| 405     | Method Not Allowed | O método não é permitido                           |
| 409     | Conflict           | O recurso já existe                                |
| 429     | Too Many Requests  | O cliente fez muitas requisições                   |

##### 5xx: Erro do Servidor

Os códigos de status 5xx são utilizados para informar que houve um erro no servidor.

| Código  | Mensagem              |                                           |
| ------- | --------------------- | ----------------------------------------- |
| 500     | Internal Server Error | Erro interno do servidor                  |
| 501     | Not Implemented       | O método não foi implementado             |
| 502     | Bad Gateway           | O servidor recebeu uma resposta inválida  |
| 503     | Service Unavailable   | O servidor não está disponível            |
| 504     | Gateway Timeout       | O servidor demorou muito para responder   |

### Similaridades e Diferenças entre Requisição e Resposta HTTP <a id=http-request-response />

Tanto a [requisição](#http-request) quanto a [resposta](#http-response) do [Protocolo HTTP](#http) possuem uma estrutura similar, no entanto, a requisição é enviada do cliente para o servidor e a resposta é enviada do servidor para o cliente, os cabeçalhos e o corpo possuem a mesma estrutura, a diferença está na linha primeira linha, a linha de requisição no caso da requisição e a linha de status no caso da resposta.
 
> ⚠️ **Atenção**
>
> 1. O protocolo HTTP é um protocolo de texto, ou seja, as requisições e respostas são enviadas em texto puro.
> 2. O protocolo HTTP é um protocolo de comunicação sem estado, ou seja, ele não mantém o estado da comunicação, cada requisição é independente da outra.
> 3. A linha em branco entre os cabeçalhos e o corpo é obrigatória, ela é utilizada para separar os cabeçalhos do corpo.

## API - Application Programming Interface <a id=api />

API (Application Programming Interface) é um conjunto de regras e padrões que permite a comunicação entre sistemas, ela é utilizada para acessar recursos de um sistema, por exemplo, acessar informações de um banco de dados, acessar informações de um serviço, etc.

### API RESTFul <a id=restful-api />

O termo RESTFul é uma abreviação de Representational State Transfer, ele foi criado por Roy Fielding em sua tese de doutorado, ele é utilizado para descrever uma API que segue os princípios da arquitetura REST, isso significa que a API segue o mesmo conjunto de regras e padrões do protocolo HTTP.

Uma API RESTFul é composta por 5 princípios, os princípios são:

1. **Cliente-Servidor**: O cliente e o servidor são separados, eles podem ser desenvolvidos e evoluídos independentemente.
2. **Sem Estado**: O servidor não mantém o estado da comunicação, cada requisição é independente da outra.
3. **Cache**: O servidor deve informar se a resposta pode ser armazenada em cache.
4. **Interface Uniforme**: A interface da API deve ser uniforme, os recursos devem ser acessados da mesma forma.
5. **Sistema em Camadas**: O sistema pode ser composto por várias camadas, por exemplo, um servidor de aplicação, um servidor de banco de dados, etc.

A grande peculiaridade da RESTFul API é que ela utiliza os [métodos HTTP](#http-method) para acessar os recursos e executa operações CRUD (Create, Read, Update, Delete) nos recursos, cinculando as operações CRUD com os métodos HTTP e operações do banco de dados.

| CRUD   | Método HTTP |  Banco de Dados  | Possíveis Códigos de Status de Resposta          |
| ------ | ----------- | ---------------- | ------------------------------------------------ |
| Create | POST        | INSERT           | 200, 400, 401, 403, 404, 500                     |
| Read   | GET         | SELECT           | 200, 201, 400, 401, 403, 404, 409, 422, 500      |
| Update | PUT         | UPDATE           | 200, 201, 204, 400, 401, 403, 404, 409, 422, 500 |
| Update | PATCH       | UPDATE           | 200, 204, 400, 401, 403, 404, 409, 422, 500      |
| Delete | DELETE      | DELETE           | 200, 204, 400, 401, 403, 404, 409, 500           |

> ⚠️ **Atenção**
>
> RESTFul vs REST: O termo RESTFul é utilizado para descrever uma API que segue os princípios da arquitetura REST, no entanto, o termo REST é utilizado para descrever a arquitetura em si, ou seja, a arquitetura REST é composta por um conjunto de princípios e regras, já a API RESTFul é uma API que segue esses princípios e regras.

### Arquivos estáticos <a id=static-files />

Arquivos estáticos são arquivos que não são processados pelo servidor, eles são enviados diretamente para o cliente sem nenhum processamento, por exemplo, arquivos HTML, CSS, Javascript, imagens, etc.

## HTML - HyperText Markup Language <a id=html />

O HTML (HyperText Markup Language) é uma linguagem de marcação utilizada para criar páginas web, ela é composta por tags, as tags são utilizadas para estruturar o conteúdo da página, por exemplo, criar títulos, parágrafos, listas, links, imagens, etc.

A sintaxe do HTML segue o seguinte padrão:

```html
<tag atributo1="valor 1" atributo2="valor 2" atributoN="valor 2">Conteúdo</tag>
```

No exemplo a cima temos a tag `<tag>`, ela é composta por 3 partes, a tag de abertura `<tag>`, a tag de fechamento `</tag>` indicando de onde a tag começa e termina sua marcação e o conteúdo `Conteúdo` que será marcado, as tags podem ter atributos, os atributos são utilizados para adicionar informações adicionais a tag, por exemplo, o atributo `style` é utilizado para adicionar estilos a tag. 

Note que as tags podem ser aninhadas, ou seja, uma tag pode conter outra tag, por exemplo:

```html
<tag>
  <tag>Item 1</tag>
  <tag>Item 2</tag>
  <tag>Item 3</tag>
</tag>
```


> 💭 **Abstação**
> - Imagine que a frase "eu gosto de bolo e suco", e é necessário "marcar" a palavra "bolo" como sendo importante, é possível sublinhar a palavra "bolo" ou colocar em negrito, o HTML é justamente utilizado para "marcar".
> - Ainda utilizando o exemplo anterior, imagine que a palavra "bolo" será marcada com um sublinhado, a palavra "eu" será marcada com italico e a frase do início da frase até "bolo" será marcada com negrito, neste caso a frase com estas marcações ficaria da segunte forma: `<b><i>eu</i> gosto de <u>bolo</u></b> e suco`.
> - Resultado seria: 
>   - <b><i>eu</i> gosto de <u>bolo</u></b> e suco

> ⚠️ **Atenção**
>
> - As tags são `<i>`, `<b>` e `<u>` são consideradas obsoletas, ou seja, elas não devem ser utilizadas, no entanto, elas são utilizadas neste exemplo para facilitar o entendimento.

### Estrutura Básica de um Documento HTML <a id=html-structure />

O HTML é composto por uma estrutura básica, a estrutura é composta por tag `<html>`, tag `<head>` e tag `<body>`, a tag `<html>` é a tag raiz do documento, todas as outras tags devem ser filhas da tag `<html>`, a tag `<head>` é utilizada para adicionar informações adicionais ao documento, por exemplo, adicionar o título da página, adicionar o estilo da página, adicionar o script da página, etc, a tag `<body>` é utilizada para adicionar o conteúdo da página.

A estrutura básica de um documento HTML é a seguinte:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Título da Página</title>
  </head>
  <body>
    Conteúdo da Página
  </body>
</html>
```

Entendendo a estrutura:

- `<!DOCTYPE html>`: é a declaração do tipo de documento, ela informa ao navegador que o documento é um documento HTML.
- `<html>`: é a tag raiz do documento, todas as outras tags devem ser filhas da tag `<html>`.
- `<head>`: é a tag utilizada para adicionar informações adicionais ao documento, por exemplo, adicionar o título da página, adicionar o estilo da página, adicionar o script da página, etc.
- `<title>`: é a tag utilizada para adicionar o título da página, o título é exibido na aba do navegador.
- `<body>`: é a tag utilizada para adicionar o conteúdo da página, por exemplo, adicionar títulos, parágrafos, listas, links, imagens, etc.

### Tags HTML <a id=html-tags />

O HTML é composto por várias tags, as tags são utilizadas para estruturar o conteúdo da página, por exemplo, criar títulos, parágrafos, listas, links, imagens, etc, abaixo temos uma lista com algumas tags HTML, não é viavel listar todas as tags HTML, no entanto, é possível encontrar uma lista completa no site da [Mozilla Developer Network](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element) ou no site da [W3Schools](https://www.w3schools.com/tags).

## CSS - Cascading Style Sheets <a id=css />

O CSS (Cascading Style Sheets) é uma linguagem de estilo utilizada para adicionar estilos a páginas web, ela é composta por regras, as regras são utilizadas para adicionar estilos a elementos HTML, por exemplo, adicionar cor, adicionar tamanho, adicionar fonte, adicionar margem, adicionar padding, etc.

A sintaxe do CSS segue o seguinte padrão:

```css
seletor {
  propriedade1: valor 1;
  propriedade2: valor 2;
  propriedadeN: valor N;
}
```

No exemplo a cima temos o seletor `seletor`, ele é utilizado para selecionar o elemento HTML que deseja adicionar estilo, as propriedades `propriedade1`, `propriedade2`, `propriedadeN` são utilizadas para adicionar estilo ao elemento, os valores `valor 1`, `valor 2`, `valor N` são utilizados para definir o estilo, por exemplo, a cor, o tamanho, a fonte, a margem, o padding, etc.

O seletor tem a função de selecionar elementos HTML (DOM) e aplicar estilos a eles, os seletores podem ser simples, compostos, de atributo, de pseudo-classe, de pseudo-elemento, etc. existem vários tipos de seletores, no entanto, os seletores mais comuns são os seletores de tag, de classe e de id, veja abaixo alguns exemplos de seletores:

considerando o seguinte HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Título da Página</title>
    <style>
      /* Seletor de Tag */
      h1 {
        color: red;
      }

      /* Seletor de Classe */
      .classe {
        color: blue;
      }

      /* Seletor de ID */
      #id {
        color: green;
      }
    </style>
  </head>
  <body>
    <h1>Seletor de Tag</h1>
    <p class="classe">Seletor de Classe</p>
    <p id="id">Seletor de ID</p>
  </body>
</html>
```

Entendendo o codigo:

- `h1`: é o seletor de tag, ele é utilizado para selecionar a tag `<h1>`, neste caso, o texto `Seletor de Tag` será vermelho.
- `.classe`: é o seletor de classe, ele é utilizado para selecionar a tag com a classe `classe`, neste caso, o texto `Seletor de Classe` será azul.
- `#id`: é o seletor de id, ele é utilizado para selecionar a tag com o id `id`, neste caso, o texto `Seletor de ID` será verde.

> ⚠️ **Atenção**
> 
> O exemplo acima é um exemplo simples, onde diretamente em um arquivo HTML é adicionado o CSS, no entanto, o mais comum é adicionar o CSS em um arquivo separado, o arquivo CSS é adicionado ao HTML utilizando a tag `<link>`, por exemplo, `<link rel="stylesheet" href="style.css">`, onde `style.css` é o arquivo CSS a ser importado.

para mais informações sobre CSS, consulte a documentação da [Mozilla Developer Network](https://developer.mozilla.org/pt-BR/docs/Web/CSS) ou da [W3Schools](https://www.w3schools.com/css).

## Javascript <a id=javascript />

O Javascript é uma linguagem de programação utilizada para adicionar interatividade a páginas web, ela é composta por instruções, as instruções são utilizadas para adicionar comportamento a elementos HTML, por exemplo, adicionar um evento de clique, adicionar um evento de mouseover, adicionar um evento de submit, etc.

Com o adivento de frameworks como NodeJs, Deno, Bum entre outros, o Javascript passou a ser utilizado também no lado do servidor, ou seja, o Javascript é uma linguagem de programação que pode ser utilizada tanto no lado do cliente quanto no lado do servidor.

Por ser uma linguagem muito ampla não conseguimos abordar todos os aspectos do Javascript, no entanto, é possível encontrar uma lista completa de recursos no site da [Mozilla Developer Network](https://developer.mozilla.org/pt-BR/docs/Web/Javascript) ou no site da [W3Schools](https://www.w3schools.com/js).

## TypeScript <a id=typescript />

O TypeScript é uma linguagem ou superset do Javascript, o propósito principal do TypeScript é adicionar tipagem ao Javascript, ou seja, adicionar tipos de dados a variáveis, funções, classes, etc. tornando o código mais seguro e mais fácil de manter.

> 💡 **Dica**
> - O TypeScript é uma linguagem de programação muito poderosa, no entanto, é importante lembrar que o TypeScript é convertido para Javascript antes de ser executado, isso significa que o TypeScript é uma linguagem de programação que roda em qualquer lugar onde o Javascript roda.
> - Superset é um termo utilizado para descrever uma linguagem que é uma extensão de outra linguagem, por exemplo, o TypeScript é um superset do Javascript, o Sass é um superset do CSS, etc.

## SQL - Structured Query Language <a id=sql />

O SQL (Structured Query Language) é uma linguagem de consulta utilizada para acessar e manipular bancos de dados relacionais, ela é composta por instruções, as instruções são utilizadas para criar, ler, atualizar e deletar dados de um banco de dados, por exemplo, criar uma tabela, inserir um registro, atualizar um registro, deletar um registro, etc.

O SQL é uma linguagem muito ampla, no entanto, é possível encontrar uma lista completa de instruções no site da [Mozilla Developer Network](https://developer.mozilla.org/pt-BR/docs/Web/SQL) ou no site da [W3Schools](https://www.w3schools.com/sql).

## Git <a id=git />

O Git é um sistema de controle de versão distribuído, ele é utilizado para rastrear as alterações em arquivos e coordenar o trabalho entre várias pessoas, ele é composto por comandos, os comandos são utilizados para adicionar, commitar, pushar, pullar, etc.

O Git é uma ferramenta muito poderosa, no entanto, é possível encontrar uma lista completa de comandos no site da [Git](https://git-scm.com/docs).

## NPM - Node Package Manager <a id=npm />

O NPM (Node Package Manager) é um gerenciador de pacotes para a linguagem de programação Javascript, ele é utilizado para instalar, atualizar, remover e publicar pacotes, ele é composto por comandos, os comandos são utilizados para instalar, atualizar, remover e publicar pacotes.

Os comandos mais comuns do NPM são:

- `npm init`: [leia mais](./comandos#npm-init)
- `npm install <pacote>`: [leia mais](./comandos#npm-install)
- `npm uninstall <pacote>`: [leia mais](./comandos#npm-uninstall)
- `npm run <script>`: [leia mais](./comandos#npm-run)

O NPM é uma ferramenta muito poderosa, no entanto, é possível encontrar uma lista completa de comandos no site da [NPM](https://docs.npmjs.com/cli/v7/commands).