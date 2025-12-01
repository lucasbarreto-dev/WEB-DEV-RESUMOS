# INTRODUÇÃO AO TS

## <strong> SUMÁRIO </strong>
<!-- - ### [1 - TIPAGEM](#1---tipagem) -->
<!-- - ### [2 - TIPOS E SUBTIPOS](#2---tipos-e-subtipos) --->
- ### [1 - CRIANDO O AMBIENTE DE DESENVOLVIMENTO](#1---criando-o-ambiente-de-desenvolvimento)
    - ### [1.1 - INSTALANDO O TS](#11---instalando-o-ts)
        - ### [1.1.1 - INSTALANDO O TS GLOBALMENTE](#111---para-instalar-globalmente-na-máquina)
        - ### [1.1.2 - INSTALANDO NO DIRETÓRIO DO PROJETO (RECOMENDADO)](#112---para-instalar-localmente-no-diretório-do-projeto-recomendado)
    - ### [1.2 - INICIANDO UM PROJETO](#12---iniciando-um-projeto)
        - ### [1.2.1 - CRIANDO UM DIRETÓRIO](#121---criando-um-diretório)
        - ### [1.2.2 - INICIANDO O NPM](#122---iniciando-o-gerenciador-de-módulos-do-nodejs)
        - ### [1.2.3 - INSTALANDO O TS NO PROJETO](#123---instale-o-typescript-como-dependência-de-desenvolvimento)
 - ### [2 - HELLO, WORLD!](#2---hello-world)
    - ### [2.1 - Crie o script com extensão .ts](#21---crie-o-script-com-extensão-ts)
    - ### [2.2 - Crie uma função para imprimir 'Hello, world!'](#22---crie-uma-função-para-imprimir-hello-world)
    - ### [2.3 - Compilação](#23---compilação) 
    - ### [2.4 - Executando o arquivo em JS](#24---executando-o-arquivo-em-js)
    
<br /> 
<hr>

<!-- ## <strong>1 - TIPAGEM</strong>
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

<hr> -->

## <strong>1 - CRIANDO O AMBIENTE DE DESENVOLVIMENTO</strong>
- ### <strong>1.1 - Instalando o TS</strong>
    - #### <strong>1.1.1 - Para instalar globalmente na máquina</strong>

        ```sh
            npm install -g typescript@4.4
        ```

    - #### <strong>1.1.2 - Para instalar localmente no diretório do projeto (RECOMENDADO)</strong>
        ```sh
            npm i -D typescript@4.4
        ```
     <br />

- ### <strong>1.2 - Iniciando um projeto</strong>
    - #### <strong>1.2.1 - Crie um diretório para o projeto
    ```sh
        mkdir nomeDoProjeto && cd nomeDoProjeto
    ```

    - #### <strong>1.2.2 - Iniciando o gerenciador de módulos do Node.js</strong>
    
    ```sh
        npm init -y
    ```

    - #### <strong>1.2.3 - Instale o Typescript como dependência de desenvolvimento</strong>
    
    ```sh
        npm i -D typescript@4.4
    ```
    <br />

<hr>

## <strong>2 - Hello, world!</strong> 
- ### <strong>2.1 - Crie o script com extensão .ts</strong>

    ```sh
        touch Hello.ts 
    ```

- ### <strong>2.2 - Crie uma função para imprimir 'Hello, world!'</strong>
    
    ```ts
        // Hello.js

        function hello(): void {
            console.log('Hello, world!');
        };

        hello();
    ```
    -  <p> A função apenas imprime no console sem retornar qualquer valor. <br />Por isso, é tipada com 'void'.</p>
    <br />

- ### <strong>2.3 - Compilação</strong>

    ```sh
        npx tsc hello.ts
    ```

    - Ao rodar esse comando, o compilador gera uma versão do código em JS em um novo arquivo e é ele que deverá ser executado pelo Node.js. 

<br />

- ### <strong>2.4 - Executando o arquivo em JS</strong>
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