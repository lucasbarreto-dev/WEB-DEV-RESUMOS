# SUMÁRIO
- [1. FERRAMENTAS](#ferramentas)

  - [MOCHA](#mocha);

  - [CHAI](#chai);

  - [SINON](#sinon);

- [2. INSTALAÇÃO](#instalação)

- [3. TESTES DE INTEGRAÇÃO](#3-testes-de-integração)

- [4. IMPLEMENTAÇÃO DE TESTES](#4-implementação-de-testes)

  - [4.1 - NA CAMADA MODEL](#41---na-camada-model)

  - [4.2 - NA CAMADA SERVICE](#42---na-camada-service)

  - [4.3 - NA CAMADA CONTROLLER](#43---na-camada-controller)

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
    Usado para criar os [Stubs](#stub---objeto-que-podemos-utilizar-para-simular-interações-com-dependências-externas-ao-que-estamos-testando), nossos dublês de teste.

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

  - ### <strong> 4.1 - Na camada Model</strong>

  ```js
  // /tests/integration/models/elements.model.test.js

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
  // ../../../tests/integration/models/mocks/mock

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
  <p><strong>Exemplo de mock da camada Model.</strong></p>

  <br />

  - ### <strong>4.2 - Na camada Service</strong>

  <p>A partir da camada service, é necessário usar o <strong>sinon</strong> para mocar a camada anterior da camada em teste.</p>

  <br />
  
  #### <strong>Stub</strong> -> Objeto que podemos utilizar para simular interações com dependências externas ao que estamos testando.

  <p>Criamos os dublês de teste com a funçao <code>sinon.stub()</code>, que recebe 2 parâmetros:</p>

  ```js
  sinon.stub(a, b)

  // a = Módulo que será simulado.
  // b = Qual função do módulo vai ser simulada.

  // no teste, usamos:
  sinon.stub(a, b).resolves( <retorno esperado da função b> );
  ```  

  ```js

  // /tests/integration/services/elements.services.test.js

    const { expect } = require('chai');
    const sinon = require('sinon');

    const MODEL = require('../../../src/models/elements.model');
    const SERVICE = require('../../../src/services/elements.service');

    const MOCK = require('../models/mocks/elements.model.mock');

    describe('Testa a camada services para a rota /elements', function () {
      afterEach(function () { sinon.restore() });

      it('Verifica se o endpoint "/elements" retorna todos os elementos cadastrados.', async function () {

        // aqui ocorre o mock da camada model
        sinon.stub(MODEL, 'getAll').resolves(MOCK);
        
        const result = await SERVICE.getAll();
        
        expect(result).to.be.deep.equal({ status: 200, data: MOCK });
      }
    }
  ```

<br />

  - ### <strong>4.3 - Na camada Controller</strong>

  <p>Recordando o uso do sinon para criar os "dublês de teste":</p>

  ```js
  sinon.stub(a, b)

  // a = Módulo que será simulado.
  // b = Qual função do módulo vai ser simulada.

  // no teste, usamos:
  sinon.stub(a, b).resolves( <retorno esperado da função b> );
  ```

  ```js
  // /tests/integration/controllers/elements.controller.test.js

      const chai = require('chai');
      const sinon = require('sinon');
      const sinonChai = require('sinon-chai');

      const { expect } = chai;
      chai.use(sinonChai);

      const SERVICE = require('../../../src/services/elements.service');
      const CONTROLLER = require('../../../src/controllers/elements.controllers');
      const MOCK = require('../models/mocks/elements.model.mock');

      describe('Testa a camada controllers para a rota "/elements"', function () {
        afterEach(function () { sinon.restore() });

        it('Testa a função getAll da camada controller.', async function () {
          const req = {};
          const res = {};

          res.status = sinon.stub().returns(res);
          res.json = sinon.stub().returns();
          
          // aqui ocorre o mock da camada service
          sinon.stub(SERVICE, 'getAll').resolves({
            status: 200,
            data: MOCK.elements
          });
          
          await CONTROLLER.getAll(req, res);
          
          expect(res.status).to.have.been.calledWith(200);
          expect(res.json).to.have.been.calledWith(MOCK.elements);
        });
  ```

<br />
<hr>
<br />
