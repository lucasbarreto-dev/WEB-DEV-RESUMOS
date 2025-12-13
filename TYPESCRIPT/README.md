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

- ## [4 - MODULARIZANDO O CÓDIGO E ESTRUTURA DE PROJETO](#4---modularizando-o-código-e-estrutura-de-projeto-1)
    - #### [4.1 - Função Simples e Exportação Inicial](#41---função-simples-e-exportação-inicial-1)
    - #### [4.2 - Organizando Dados em um Módulo Dedicado](#42---organizando-dados-em-um-módulo-dedicado-1)
    - #### [4.3 - Consumindo Módulos: Importação e Iteração (loop.ts)](#43---consumindo-módulos-importação-e-iteração-loopts-1)

    
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
    O primeiro passo é criar a pasta onde o código residirá e entrar nela pelo terminal:
    ```sh
        mkdir nomeDoProjeto && cd nomeDoProjeto
    ```

- ### <strong>1.2 - Iniciando o gerenciador de módulos do Node.js</strong>
    Iniciamos o projeto Node.js para criar o arquivo <code>package.json</code>, que gerenciará nossas dependências:

    ```sh
        npm init -y
    ```

- ### <strong>1.3 - Instale o Typescript como dependência de desenvolvimento</strong>
    - Para garantir a segurança do tipo e a execução correta, instalamos o TypeScript e as definições de tipos para o ambiente Node.js:

        - Atenção: Mantenha a compatibilidade entre as versões do <strong>TypeScript</strong>, do <strong>Node</strong> e da biblioteca <strong>@types/node</strong>.
    ```sh

        # Instala o TypeScript como dependência de desenvolvimento
        npm i -D typescript
        
        # Instala as definições de tipo para o Node.js
        npm i -D @types/node 
        
        # Garante o uso da versão LTS (Long Term Support) do Node.js
        nvm install --lts
    ```

- ### <strong>1.4 - Crie os diretórios <code>src</code> e <code>dist</code></strong>

    Organizaremos o projeto separando o código original do código gerado para produção. Por isso, na raíz do projeto, rode o comando:

    ```sh
    mkdir src dist
    ```

    <code>src</code>: Diretório dos arquivos fonte (<code>.ts</code>).

    <code>dist</code>: Onde o compilador (<code>tsc</code>) salvará os arquivos compilados (<code>.js</code>).

<br />

<!-- <hr> -->

## <strong>2 - Hello, world!</strong> 
- ### <strong>2.1 - Crie o script dentro da pasta <code>src</code></strong>
    Sempre trabalharemos com os arquivos fonte dentro de <code>src</code>:
    ```sh
        touch src/hello.ts 
    ```

- ### <strong>2.2 - Escreva a função com tipagem <code>void</code></strong>
    
    ```ts
        // src/hello.ts

        function hello(): void {
            console.log('Hello, world!');
        };

        hello();
    ```
    A função apenas imprime no console sem retornar valor, por isso utilizamos o tipo <code>void</code>.

- ### <strong>2.3 - Realize a Compilação (TS para JS)</strong>

    ```sh
        npx tsc src/hello.ts
    ```
    O compilador <code>tsc</code> lerá o arquivo TypeScript e gerará uma versão compatível em JavaScript (<code>src/hello.js</code>).

- ### <strong>2.4 - Execute o arquivo gerado com Node.js</strong>
    Lembre-se: o Node executa o arquivo <strong>.js</strong> resultante:
    ```sh
        node src/hello.js
    ```

    O retorno no console será:
    
    ```sh
        Hello, world!
    ```
    Ou seja, escrevemos o código em <code>typescript</code> e o comando <code>npx tsc nomeDoArquivo.ts</code> gera um arquivo <code>.js</code> para este ser executado. 

    <br /> 


## <strong>3 - CONFIGURAÇÃO DO COMPILADOR E TS-NODE</strong> 

- ### <strong>3.1 - Inicialize e configure o <code>tsconfig.json</code></strong>
    Gere o arquivo de configuração padrão do TypeScript:
    
    ```sh
        npx tsc --init
    ```

    Abra o arquivo <code>tsconfig.json</code> e realize as seguintes alterações conforme sua necessidade:

    - **Para compilação via <code>tsc</code> (Geração de arquivos na <code>dist</code>):**
        Descomente e configure estas linhas para organizar a saída:
        ```json
            "rootDir": "./src",
            "outDir": "./dist",
        ```

    - **Compatibilidade de Módulos (Interop):**
        Procure pela chave abaixo e altere para <code>false</code> para facilitar a integração entre ESM e CommonJS:
        ```json
            "verbatimModuleSyntax": false
        ```

    <details>
    <summary>📌 <strong>Entenda a opção <code>verbatimModuleSyntax</code> (Clique para expandir)</strong></summary>
    <br />
    <table border="1" style="border-collapse: collapse; width: 100%;">
        <thead>
            <tr style="background-color: #f2f2f2;">
                <th style="padding: 8px;">Opção</th>
                <th style="padding: 8px;">Comportamento Principal</th>
                <th style="padding: 8px;">Implicações</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td style="padding: 8px;"><strong><code>false</code></strong> (Sugerido)</td>
                <td>O TS aplica transformações e interop automaticamente.</td>
                <td>Permite usar sintaxe ESM e compilar para CommonJS sem erros de sistema de módulos.</td>
            </tr>
            <tr>
                <td style="padding: 8px;"><strong><code>true</code></strong></td>
                <td>Desliga o Interop. Exige coerência exata (verbatim).</td>
                <td>Evita a "magia" do TS, mas exige que você saiba exatamente se o arquivo final é ESM ou CJS.</td>
            </tr>
        </tbody>
    </table>
    </details>

- ### <strong>3.2 - Execução rápida com <code>ts-node</code></strong>
    
    Instale a ferramenta para rodar scripts sem precisar gerar arquivos <code>.js</code> físicos:
    ```sh
        npm i -D ts-node
    ```   

    O <code>ts-node</code> transpila o código na memória RAM e o executa instantaneamente. Para testar o script que criamos anteriormente:
    
    ```sh
        npx ts-node src/hello.ts
    ```

    - **Observação:** O <code>ts-node</code> ignora a configuração <code>outDir</code>, pois ele não escreve arquivos no disco.

<br />
<!-- <hr> -->

## <strong>4 - MODULARIZANDO O CÓDIGO E ESTRUTURA DE PROJETO</strong> 
<!-- - ### <strong>3.1 - Sistemas de módulos</strong> -->

- ### <strong>4.1 - Função Simples e Exportação Inicial</strong>

    Podemos escrever uma função para saudar uma pessoa, que recebe um nome (string) como parâmetro e retorna uma string do tipo <code>'- Hi, pessoa!'</code>. Por isso, o retorno não será mais <code>void</code>, e sim, <code>string</code>.

    ```ts
        // src/greet.ts

        export function greet(name: string): string {
            return '- Hi, ' + name + '!';
        }

        console.log(greet('Barbie'));
        console.log(greet('Ken'));

    ```

    Rodando o comando:

    ```sh
        npx ts-node src/greet.ts
    ```

    O retorno no console será:
        
    ```sh
        - Hi, Barbie!
        - Hi, Ken!
    ```

    Observe que não foram criados arquivos <code>.js</code> em nenhum local.<br>
    Com o <code>ts-node</code> usamos apenas uma linha de código para rodar o script.

- ### <strong>4.2 - Organizando Dados em um Módulo Dedicado</strong>


    Agora, vamos dar um passo à frente elevando um pouco mais a complexidade do código.

    Criamos o diretório <code>data</code> dentro de <code>src</code>

    ```sh
        mkdir src/data
    ```

    Dentro do novo diretório, criamos um arquivo para armazenar os dados.

    ```sh
        cd src/data && touch data.ts
    ```

    ```ts
        // src/data/data.ts

        export default [
            'Ada Lovelace',
            'Alan Kay',
            'Ken Thompson',
            'Dennis Ritchie',
        ];
    ```

- ### <strong>4.3 - Consumindo Módulos: Importação e Iteração (loop.ts)</strong>


    Vamos criar uma função para efetuar um loop.
        
    ```sh
        cd .. && touch loop.ts
    ```

    Neste loop, vamos saudar cada uma das personalidades no array chamando a função <code>greet()</code> no módulo <code>src/greet</code>.

    ```ts
        // src/loop.ts

        import people from './data/data';
        import { greet } from './greet';

        const loop = (people: Array<string>): void => {
            people.forEach((p) => console.log(greet(p)));
        }

        loop(people);    
    ```

    Não esqueça de eliminar os <code>console.log()</code> do arquivo <code>greet.ts</code>.
    O arquivo deve conter somente a função com a exportação:

    ```ts
    // src/greet.ts

    export function greet(name: string): string {
        return '- Hi, ' + name + '!';
    }

    // console.log(greet('Barbie'));
    // console.log(greet('Ken'));

    ```

    Rodando o comando:

    ```sh
        npx ts-node src/loop.ts
    ```


    O retorno no console será:

    ```sh
    - Hi, Ada Lovelace!
    - Hi, Alan Kay!
    - Hi, Ken Thompson!
    - Hi, Dennis Ritchie!
    ```

<hr>
