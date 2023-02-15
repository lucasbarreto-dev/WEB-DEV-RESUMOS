# SUMÁRIO
- [1. FERRAMENTAS](#ferramentas)

  - [Mocha](#mocha);

  - [Chai](#chai);

  - [Sinon](#sinon);

- [2. INSTALAÇÃO](#instalação)

- [3. TESTES DE INTEGRAÇÃO](#3-testes-de-integração)

- [4. IMPLEMENTAÇÃO DE TESTES](#4-implementação-de-testes)

  - [4.1 - NA CAMADA MODEL](#1---na-camada-model)

<br /> 
<hr>
<br />

## <strong>1. FERRAMENTAS</strong>
  - ### <strong>Mocha;</strong>
    <p>Através do Mocha você consegue usar <strong>describe</strong> e <strong>it</strong> </p>

  ```js
      describe('', function () {

        it('', function () {}); 

      });
  ```

 
  <br />

  - ### <strong>Chai;</strong>
  <p>Do Chai extraímos o expect e os getters</p>

  ```js
      // describe('', function () {

        // it('', function () {
          const FOUR = 4;
          expect(2 + 2).to.be.equal(FOUR);
        // }); 

      // });
  ```

  <br />


  - ### <strong>Sinon;</strong>
    <p>Stubs (dublês de teste)</p> 

<br /> 
<hr>
<br />

## <strong>2. INSTALAÇÃO</strong>

  ```sh
    npm i -D mocha chai
  ```
<br />
<hr>
<br />

## <strong>3. TESTES DE INTEGRAÇÃO</strong>
  - <strong>Verificam se a comunicação entre os componentes está ocorrendo da forma esperada.</strong>

  ![Fluxo de informação na API](https://github.com/lucasbarreto92/WEB-DEV-RESUMOS/blob/main/TESTES/INTEGRATION/public/Captura%20de%20Tela%202023-02-15%20%C3%A0s%2017.32.07.png)

  <br />

  - <strong>Contratos de API's</strong>
    - As regras de entrada e saída de dados da API.

  <br />


![Ex.: endpoint GET /users/:id](https://github.com/lucasbarreto92/WEB-DEV-RESUMOS/blob/main/TESTES/INTEGRATION/public/Captura%20de%20Tela%202023-02-15%20%C3%A0s%2017.21.58.png)

<br />
<hr>
<br />

## <strong>4. IMPLEMENTAÇÃO DE TESTES</strong>

  - <strong>3 A's</strong>
    - Arrange
    - Act
    - Assert

  <br />

  - ### <strong> 1 - Na camada Model</strong>

  ```js
  // test.js

    const { expect } = require('chai');
    const sinon = require('sinon');

    const connection = require('../../../src/db/connection');
    const MODEL = require('../../../src/models/model');

    const mock = require('../../../tests/integration/mocks/mock');

    describe('Testa a camada model para a rota /elements', function () {
      afterEach( function () { sinon.restore() });

      it('Verifica se é retornada a listagem completa de elementos.', async function () {
        sinon.stub(connection, 'execute').resolves([mock]);
        const response = await MODEL.getAllElements();

        expect(response).to.be.equal(mock);
      });
    });
  ```

  <strong>O mock da camanda model é feito com um array de objetos, tal qual o retorno da função</strong> <code>connection.execute()</code> 
  
  ```js
  // ../../../tests/integration/mocks/mock

    const elements = [
      {
        id: 1, 
        name: 'elemento01'
      },
      {
        id: 2,
        name: 'elemento02'
      },
      {
        id: 3,
        name: 'elemento03'
      }
    ];

    module.exports = { elements };
  ``` 

  <br />

  <!-- - ### <strong>2 - Na camada Service</strong>

  ```js
    const { expect } = require('chai');
    const sinon = require('sinon');

    const MODEL = require('../../../src/models/elements.model');
    const SERVICE = require('../../../src/services/elements.service');

    const MOCK = require('../models/mocks/elements.model.mock');

    describe('Testa a camada services para a rota /elements', function () {
      afterEach(function () { sinon.restore() });

      it('Verifica se o endpoint "/elements" retorna todos os produtos cadastrados.', async function () {
        sinon.stub(elements_MODEL, 'getAllElements').resolves(MOCK);
        
        const result = await elements_SERVICE.getAllelementsService();
        
        expect(result).to.be.deep.equal({ status: 200, data: MOCK });

  ``` -->

