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

<hr>

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

    Caso esteja usando o compilador <code>tsc</code>, é necessário descomentar as linhas:

    ```json
        "rootDir": "./src",
        "outDir": "./dist",
    ```

    É importante ter em mente a necessidade de setarmos os valores <code>rootDir</code> para o diretório onde estão os arquivos <code>.ts</code> e <code>outDir</code> para o diretório onde os arquivos <code>.js</code> serão gerados.

    Caso queira usar o <code>ts-node</code>, descomente somente a linha referente ao "rootDir". O <code>ts-node</code> ignora completamente a configuração outDir porque, por design, ele não escreve nenhum arquivo no sistema de arquivos.

    Também é importante lembrar de executar a configuração abaixo:

    ```json
        "verbatimModuleSyntax": false
    ```

    Ao desligar <code>verbatimModuleSyntax</code> permitimos que o TypeScript transforme a sintaxe <code>export</code> em código <strong>CommonJS</strong> compatível (por exemplo exports.x = ...), em vez de exigir que o arquivo já seja tratado como <strong>ESM</strong>. Se estiver como <code>true</code> o TS exige coerência verbatim entre a sintaxe do arquivo (ESM) e o formato do módulo (CommonJS); ao desativar, ele faz a interop/transformação automaticamente.

    <table>
        <thead>
            <tr>
                <th>Opção</th>
                <th>Comportamento Principal (Transformação/Interop)</th>
                <th>Exigência / Implicações</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><strong><code>false</code></strong> (Padrão)</td>
                <td>O TypeScript aplica transformações e interop de módulos automaticamente.</td>
                <td>
                    <ul>
                        <li>Permite usar sintaxe ESM e compilar para CommonJS.</li>
                        <li>Tenta compatibilizar imports entre ESM ↔️ CJS automaticamente.</li>
                        <li>Pode gerar interop implícito (ex.: __importDefault).</li>
                        <li>Pode causar bugs sutis com default imports de libs CJS.</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td><strong><code>true</code></strong></td>
                <td>Desliga o Interop e as transformações. Exige coerência Verbatim (exata).</td>
                <td>
                    <ul>
                        <li>Exige: Que a sintaxe no código-fonte seja verbatim (exata) para o formato do módulo final.</li>
                        <li>Prevenção: Evita a "magia" do TS e previne bugs de *default imports* comuns no ecossistema Node.js.</li>
                        <li>Necessidade: Exige o uso da sintaxe correta (ex: `import * as X from 'Y'` ou `import { X } from 'Y'`) para compatibilidade.</li>
                    </ul>
                </td>
            </tr>
        </tbody>
    </table>

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
