# SUMÁRIO
- [1.FERRAMENTAS](#ferramentas)
  - [Mocha](#mocha);
  - [Chai](#chai);
  - [Sinon](#sinon);
- [2.INSTALAÇÃO](#instalação)

<hr><br />

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

  ```js
    req --- middlewares ---> res
  ```

  <br />

  - <strong>Contratos de API's</strong>
    - As regras de entrada e saída de dados da API.

  <br />

    <p>
      <strong>Ex.: endpoint GET /users/:id</strong>
    </p>
