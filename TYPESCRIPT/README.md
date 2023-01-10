# INTRODUÇÃO AO TS

## <strong> SUMÁRIO </strong>
- ### [1 - TIPAGEM](#1---tipagem)
- ### [2 - TIPOS E SUBTIPOS](#2---tipos-e-subtipos)
- ### [3 - CRIANDO O AMBIENTE DE DESENVOLVIMENTO](#3---criando-o-ambiente-de-desenvolvimento)
    - ### [3.1 - INSTALANDO O TS](#31---instalando-o-ts)
        - ### [3.1.1 - INSTALANDO O TS GLOBALMENTE](#311---para-instalar-globalmente-na-máquina)
        - ### [3.1.2 - INSTALANDO NO DIRETÓRIO DO PROJETO (RECOMENDADO)](#312---para-instalar-localmente-no-diretório-do-projeto-recomendado)
    - ### [3.2 - INICIANDO UM PROJETO](#32---iniciando-um-projeto)
        - ### [3.2.1 - CRIANDO UM DIRETÓRIO](#321---criando-um-diretório)
        - ### [3.2.2 - INICIANDO O NPM](#322---iniciando-o-gerenciador-de-módulos-do-nodejs)
        - ### [3.2.3 - INSTALANDO O TS NO PROJETO](#323---instale-o-typescript-como-dependência-de-desenvolvimento)
 - ### [4 - HELLO, WORLD!](#4---hello-world)
    - ### [4.1 - Crie o script com extensão .ts](#41---crie-o-script-com-extensão-ts)
    - ### [4.2 - Crie uma função para imprimir 'Hello, world!'](#42---crie-uma-função-para-imprimir-hello-world)
    - ### [4.3 - Compilação](#43---compilação) 
    - ### [4.4 - Executando o arquivo em JS](#44---executando-o-arquivo-em-js)
    
<br /> 
<hr>

## <strong>1 - TIPAGEM</strong>
- ### Tipagem Estática (TS)
- ### Tipagem Dinâmica (JS)
- ### Tipagem Fraca (JS)
- ### Tipagem Forte (TS)
<br />

<hr>

## <strong>2 - TIPOS E SUBTIPOS</strong>

```js
    const any = {
        primitivos: {
            boolean: 'tipo booleano',
            number: 'tipo numérico',
            string: 'caractere de texto',
            void: 'indica a ausência de valor',
            null: 'nulo', 
            undefined: 'indefinido'
            enum: 'estrutura de dados de tamanho constante que agrupa valores constantes',
        },
        objeto: {
            class,
            interface,
            array,
            literals
        },
        parâmetro: {
            // passados para funções
        }
    };
```
- <p> Null e undefined são subtipos de todos os outros tipos. </p>
- <p>Em casos genéricos, se não houver especificação do tipo na declaraçào da variável, haverá inferência de tipo.</p>

<br /> 

<hr>

## <strong>3 - CRIANDO O AMBIENTE DE DESENVOLVIMENTO</strong>
- ### <strong>3.1 - Instalando o TS</strong>
    - #### <strong>3.1.1 - Para instalar globalmente na máquina</strong>

        ```sh
            npm install -g typescript@4.4
        ```

    - #### <strong>3.1.2 - Para instalar localmente no diretório do projeto (RECOMENDADO)</strong>
        ```sh
            npm i -D typescript@4.4
        ```
     <br />

- ### <strong>3.2 - Iniciando um projeto</strong>
    - #### <strong>3.2.1 - Crie um diretório para o projeto
    ```sh
        mkdir nomeDoProjeto && cd nomeDoProjeto
    ```

    - #### <strong>3.2.2 - Iniciando o gerenciador de módulos do Node.js</strong>
    
    ```sh
        npm init -y
    ```

    - #### <strong>3.2.3 - Instale o Typescript como dependência de desenvolvimento</strong>
    
    ```sh
        npm i -D typescript@4.4
    ```
    <br />

<hr>

## <strong>4 - Hello, world!</strong> 
- ### <strong>4.1 - Crie o script com extensão .ts</strong>

    ```sh
        touch Hello.ts 
    ```

- ### <strong>4.2 - Crie uma função para imprimir 'Hello, world!'</strong>
    
    ```ts
        // Hello.js

        function hello(): void {
            console.log('Hello, world!');
        };

        hello();
    ```
    -  <p> A função apenas imprime no console sem retornar qualquer valor. <br />Por isso, é tipada com 'void'.</p>
    <br />

- ### <strong>4.3 - Compilação</strong>

    ```sh
        npx tsc hello.ts
    ```

    - Ao rodar esse comando, o compilador gera uma versão do código em JS em um novo arquivo e é ele que deverá ser executado pelo Node.js. 

<br />

- ### <strong>4.4 - Executando o arquivo em JS</strong>
    ```sh
        node hello.js
    ```
    <br />

    O retorno no console será:
    
    ```sh
        Hello, world!
    ```

<br />   
<hr>