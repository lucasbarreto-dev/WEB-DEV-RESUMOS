# INTRODUÇÃO AO TS

# <strong> SUMÁRIO </strong>
- ## [1 - INICIANDO UM PROJETO](#1---iniciando-um-projeto-1)
    <!-- - ## [1.1 - ](#11---iniciando-um-projeto) -->
    - #### [1.1 - Criando um diretório](#11---crie-um-diretório-para-o-projeto)
    - #### [1.2 - Iniciando o gerenciador de módulos do Node.js](#12---iniciando-o-gerenciador-de-módulos-do-nodejs)
    - #### [1.3 - Instale o TS como dependência de desenvolvimento](#13---instale-o-typescript-como-dependência-de-desenvolvimento)
    - #### [1.4 - Crie os diretórios <code>src</code> e <code>dist</code>](#14---crie-os-diretórios-src-e-dist)

 - ## [2 - HELLO, WORLD!](#2---hello-world-1)
    - #### [2.1 - Crie o script com extensão .ts](#21---crie-o-script-com-extensão-ts-1)
    - #### [2.2 - Crie uma função para imprimir 'Hello, world!'](#22---crie-uma-função-para-imprimir-hello-world-1)
    - #### [2.3 - Compilação](#23---compilação-1) 
    - #### [2.4 - Executando o arquivo em JS](#24---executando-o-arquivo-em-js-1)

- ## [3 - AVANÇANDO NO SETUP DO AMBIENTE](#3---avançando-no-setup-do-ambiente-1)
    - #### [3.1 - O arquivo tsconfig.json](#31---o-arquivo-tsconfigjson-1)
    - #### [3.2 - Como usar o ts-node](#32---como-usar-o-ts-node-1)

    
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

## <strong>1 - INICIANDO UM PROJETO</strong>

<!-- - ### <strong>1.1 - Criando o ambiente de desenvolvimento</strong> -->

- ### <strong>1.1 - Crie um diretório para o projeto
```sh
    mkdir nomeDoProjeto && cd nomeDoProjeto
```

- ### <strong>1.2 - Iniciando o gerenciador de módulos do Node.js</strong>

```sh
    npm init -y
```

- ### <strong>1.3 - Instale o Typescript como dependência de desenvolvimento</strong>
    - É importante assegurar a compatibilidade entre as versões
        - do <strong>Typescript</strong> 
        - do <strong>Node</strong> 
        - da biblioteca <strong>@types/node</strong> 

```sh

    # Instalar a versão mais recente do TypeScript (devDependency) 
    npm i -D typescript
    
    # Instalar @types/node alinhado (por exemplo latest ou versão compatível com sua versão do Node) 
    npm i -D @types/node 
    
    # Instala a versão LTS mais recente do Node.js e define essa versão como ativa no terminal
    nvm install --lts
```

- ### <strong>1.4 - Crie os diretórios <code>src</code> e <code>dist</code></strong>

    - Na raíz do projeto, rode o comando:
    ```sh
    mkdir src dist
    ```


    - No diretório <code>src</code> devem ficar os arquivos de código <code>.ts</code>.
    - No diretório <code>dist</code>, o compilador <code>tsc</code> criará automaticamente os arquivos <code>.js</code> após configurar o <code>tsconfig</code>. 


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

    Ou seja, escrevemos o código em <code>typescript</code> e o comando <code>npx tsc nomeDoArquivo.ts</code> gera um arquivo <code>.js</code> para este ser executado. 
<br /> 


## <strong>3 - AVANÇANDO NO SETUP DO AMBIENTE</strong> 
- ### <strong>3.1 - O arquivo tsconfig.json</strong>
    Rodando o comando:
    
    ```sh
        npx tsc --init
    ```

    Cria-se o arquivo:

    ```json
    {
    // Visit https://aka.ms/tsconfig to read more about this file
        "compilerOptions": {
            // File Layout
            // "rootDir": "./src",
            // "outDir": "./dist",

            // Environment Settings
            // See also https://aka.ms/tsconfig/module
            "module": "nodenext",
            "target": "esnext",
            "types": [],
            // For nodejs:
            // "lib": ["esnext"],
            // "types": ["node"],
            // and npm install -D @types/node

            // Other Outputs
            "sourceMap": true,
            "declaration": true,
            "declarationMap": true,

            // Stricter Typechecking Options
            "noUncheckedIndexedAccess": true,
            "exactOptionalPropertyTypes": true,

            // Style Options
            // "noImplicitReturns": true,
            // "noImplicitOverride": true,
            // "noUnusedLocals": true,
            // "noUnusedParameters": true,
            // "noFallthroughCasesInSwitch": true,
            // "noPropertyAccessFromIndexSignature": true,

            // Recommended Options
            "strict": true,
            "jsx": "react-jsx",
            "verbatimModuleSyntax": true,
            "isolatedModules": true,
            "noUncheckedSideEffectImports": true,
            "moduleDetection": "force",
            "skipLibCheck": true,
        }
    }
    ```

    Caso esteja usando o compilador <code>tsc</code>, é necessário descomentarmos as linhas:

    ```json

        // "rootDir": "./src",
        // "outDir": "./dist",
    ```

    E setarmos os valores <code>rootDir</code> para o diretório onde estão os arquivos <code>.ts</code> e <code>outDir</code> para o diretório onde os arquivos <code>.js</code> serão gerados.

    Caso queira usar o <code>ts-node</code>, descomente somente a linha referente ao "rootDir". O <code>ts-node</code> ignora completamente a configuração outDir porque, por design, ele não escreve nenhum arquivo no sistema de arquivos.

- ### <strong>3.2 - Como usar o <code>ts-node</code></strong>
    ```sh
        npm i -D ts-node
    ```   

    Após instalá-lo localmente no projeto como dependência de desenvolvimento, podemos usá-lo para executar o programa em apenas uma etapa, com uma linha de código.
    
    O <code>ts-node</code> transpila o código TypeScript inteiramente na memória RAM e passa o JavaScript resultante diretamente para o motor do <code>Node.js</code> executar, descartando o JS temporário logo em seguida.

    Ou seja, se rodarmos o comando:
    ```sh
        npx ts-node hello.ts
    ```
    <br />

    O retorno no console será:
    
    ```sh
        Hello, world!
    ```


<hr>