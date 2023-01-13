# Como construir uma API Rest com Node e Express.js

Aqui você encontra o que precisa saber para construir a sua API Rest do zero usando Node e Express.

## Sumário
[1 - Criando o ambiente de desenvolvimento](#1---criando-o-ambiente-de-desenvolvimento)


### <strong>1 - Criando o ambiente de desenvolvimento</strong>

  - <strong>1.1 - Crie e navegue até o diretório do projeto.</strong>

  ```sh
    mkdir nome_do_projeto && cd nome_do_projeto
  ```
 <br />

  - <strong>1.2 - Inicie o gerenciador de pacotes do node dentro do diretório.</strong>

  ```sh
    npm init -y
  ```
 <br />

  - <strong>1.3 - Instale as dependências necessárias para desenvolver a API.</strong>
  ```sh
    npm i express@4.17 
    // framework usado para construir APIs Rest no ambiente Node.js.

    npm i nodemon@2.0 -D
    // dependência de desenvolvimento (dev dependency) que reinicia o servidor a cada alteração feita no código.
  ```

  ```json
  // package.json

    "scripts": {
      "dev": "nodemon src/server.js"
    }

  ```
  <br />

  - <strong>1.4 - Criar os arquivos app.js e server.js</strong>
  
  ```sh
    cd src
    touch app.js server.js 
  ```

  <br />

  - <strong>1.5 - Importar o express no arquivo app.js</strong>
  ```js
    const express = require('express');

    const app = express();

    module.exports = app;
  ```

  <br />

  - <strong>1.6 - Importar o app dentro do arquivo server.js</strong>
  ```js
    const app = require('./app');

    app.listen('3000', () => console.log('Hello, world!'));
  ```
  
  <br />

  - <strong>1.7 - Inicialização do servidor</strong>

  ```sh
    npm start
    // para inicializar o servidor (server.js)

    npm run dev
    // para inicializar o Nodemon
  ```

---


 
 
