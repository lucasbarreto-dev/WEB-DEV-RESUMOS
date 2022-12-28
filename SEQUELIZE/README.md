# ORM

## Sumário
  - [1 - Definição](#1---definição)

  - [2 - Sequelize](#2---Sequelize)

  - [3 - Instalação do Sequelize e das dependências necessárias](#3---instalação-do-sequelize-e-das-dependências-necessárias)
  
    - [3.1 - Instalar o Sequelize](#31---instalar-o-sequelize)

    - [3.2 - Instalar o sequelize-cli](#32---instalar-o-sequelize-cli)

    - [3.3 - Instalar o mysql2](#33---instalar-o-mysql2)

    - [3.4 - Instalar o dotenv](#34---instalar-o-dotenv)

  - [4 - Inicialização do Sequelize](#4---inicialização-do-sequelize)

  - [5 - Conexão com o banco de dados](#5---conexão-com-o-banco-de-dados)

    - [5.1 - Crie o arquivo .env na raíz do projeto.](#51---crie-o-arquivo-env-na-raíz-do-projeto)

    - [5.2 - Usando as variáveis de ambiente para conectar Sequelize com o Banco de Dados](#52---usando-as-variáveis-de-ambiente-para-conectar-sequelize-com-o-banco-de-dados)

      - [5.2.1 - Mude o nome do arquivo config.json para config.js](#521---mude-o-nome-do-arquivo-configjson-para-configjs)
      
      - [5.2.2 - Altere a importação no arquivo index.js.](#522---altere-a-importação-no-arquivo-indexjs)

      - [5.2.3 - Rode um container MySQL pelo Docker.](#523---rode-um-container-mysql-pelo-docker)

      - [5.2.4 - Crie o arquivo .sequelizerc na raíz do projeto.](#524---crie-o-arquivo-sequelizerc-na-raíz-do-projeto)

  - [6 - Criando o banco de dados](#6---criando-o-banco-de-dados)
  
---

## 1 - Definição
<p><strong>Object-Relational Mapping</strong>: (Mapeamento objeto-relacional)</p>

<p>
  Técnica que permite fazer um mapeamento estrutural entre as entidades do banco de dados e os objetos que as representam no código Javascript.
</p>

  <br />

  ```js
  // App -> Mapeamento objeto-relacional -> Banco de dados
  ```

  <br />

---

## 2 - Sequelize
  - <strong>Biblioteca de ORM com métodos assíncronos.</strong>
  - <strong>Terceirização da camada Model:</strong>
    - Cria o banco de dados <strong>(Migrations)</strong>;
    - Adiciona os dados ao banco <strong>(Seeders)</strong>;
    - Efetua as Queries;

---

## 3 - Instalação do Sequelize e das dependências necessárias
  - ### <strong>3.1 - Instalar o Sequelize</strong>

    ```sh
      npm i sequelize@6.3
    ```
    <br />

  - ### <strong>3.2 - Instalar o sequelize-cli</strong>

    ```sh
      npm install -D sequelize-cli@6.2
    ```

    - <p>O <strong>sequelize-cli</strong> é uma dependência de desenvolvimento que serve para gerar e executar as operações.<br />Ao rodar os comandos </p>

      ```sh
        npx sequelize help
      ```
      <p><strong>ou</strong></p>

      ```sh
        npx sequelize-cli help 
      ```

      obtém-se resultados similares.

      <br />

  - ### <strong>3.3 - Instalar o mysql2</strong>

    ```sh
      npm i mysql2@2.3
    ```
      - <p>Precisamos usar o <strong>mysql2</strong> para combinar o MySQL com o Sequelize.</p>

      <br />
  
  - ### <strong>3.4 - Instalar o dotenv</strong>

    ```sh
      npm i dotenv@10.0
    ```
    <br />

---

## 4 - Inicialização do Sequelize

<p>No terminal, verifique que esteja na <strong>raíz</strong> do projeto e execute:</p>

```sh
  cd src
  npx sequelize init
```

<p>O comando acima cria 4 diretórios na pasta src:</p>

- <strong>config</strong> (Aqui devem constar orientações para a CLI)
- <strong>models</strong> (Modelos da aplicação)
- <strong>migrations</strong> (Comandos que criam o banco de dados com todas as tabelas)
- <strong>seeders</strong> (Dados para popular as tabelas do banco)

---

## 5 - Conexão com o banco de dados

- ### <strong>5.1 - Crie o arquivo .env na raíz do projeto.</strong>


  ```sh
    touch .env
  ```

  <strong>Agora declare as variáveis de ambiente</strong>

  ```env
    // .env

    MYSQL_USER=<seu nome>
    MYSQL_PASSWORD=<sua senha>
    MYSQL_DATABASE=<nome do banco de dados>
    MYSQL_HOST=localhost
  ```

  - <strong>Curiosidade</strong>

    <p>Se preferir fazer direto pela linha de comando, execute no seguinte formato:</p>

    ```sh
      echo -e 'MYSQL_USER=<seu nome>\nMYSQL_PASSWORD=<sua senha>\nMYSQL_DATABASE=<nome do banco de dados>\nMYSQL_HOST=localhost' >> .env
    ```
    <p>A flag <strong>-e</strong> torna possível a interpretação da marcação <strong>\n</strong>, que indica quebra de linha em shellscript.</p>

  <br />
  
- ### <strong>5.2 - Usando as variáveis de ambiente para conectar Sequelize com o Banco de Dados</strong>
  - #### <strong>5.2.1</strong> - Mude o nome do arquivo <strong>config.json</strong> para <strong>config.js</strong>
    ```sh
      mv config/config.json config/config.js
    ```

    ```js
      //config.js

        require('dotenv').config();
      
        const config = {
          username: process.env.MYSQL_USER,
          password: process.env.MYSQL_PASSWORD,
          database: process.env.MYSQL_DATABASE,
          host: process.env.MYSQL_HOST,
          dialect: 'mysql',
        };
      
        module.exports = {
          development: config, 
          test: config, 
          production: config, 
        };
    ```

    - <p>
        <strong>dialect</strong> = Nome do banco de dados a ser utilizado.
      </p>

    <br />

  - #### <strong>5.2.2</strong> - Altere a importação no arquivo <strong>index.js</strong>.

    ```js
      const config = require(__dirname + '/../config/config.js')[env];
    ```


    <br />

  - #### <strong>5.2.3</strong> - Rode um container MySQL pelo Docker.
  <br />

  - #### <strong>5.2.4</strong> - Crie o arquivo <strong>.sequelizerc</strong> na raíz do projeto.

    ```sh
      touch .sequelizerc
    ```

    A função desse arquivo é exportar os itens criados na inicialização na [seção 4](#4---inicialização-do-sequelize):

      ```js
      // .sequelizerc

        const path = require('path');

        module.exports = {
          'config': path.resolve('src', 'config', 'config.js'),
          'models-path': path.resolve('src', 'models'),
          'seeders-path': path.resolve('src', 'seeders'),
          'migrations-path': path.resolve('src', 'migrations')
        };
      ```

    <strong>Nota: É possível você executar este passo antes de executar o passo na [seção 4](#4---inicialização-do-sequelize) ( <code>npx sequelize init</code> ).

    <br />
---    

## 6 - Criando o banco de dados

```sh
  npx sequelize db:create
```

---