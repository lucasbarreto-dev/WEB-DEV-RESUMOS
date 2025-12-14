# INTRODUÇÃO AO TS

# <strong> SUMÁRIO </strong>
- ## [1 - INICIANDO UM PROJETO](#1---iniciando-um-projeto)
    - #### [1.1 - Crie um diretório para o projeto](#11---crie-um-diretório-para-o-projeto)
    - #### [1.2 - Iniciando o gerenciador de módulos do Node.js](#12---iniciando-o-gerenciador-de-módulos-do-nodejs)
    - #### [1.3 - Instale o Typescript como dependência de desenvolvimento](#13---instale-o-typescript-como-dependência-de-desenvolvimento)
    - #### [1.4 - Crie os diretórios src e dist](#14---crie-os-diretórios-src-e-dist)

 - ## [2 - HELLO, WORLD!](#2---hello-world)
    - #### [2.1 - Crie o script dentro da pasta src](#21---crie-o-script-dentro-da-pasta-src)
    - #### [2.2 - Escreva a função com tipagem void](#22---escreva-a-função-com-tipagem-void)
    - #### [2.3 - Realize a Compilação (TS para JS)](#23---realize-a-compilação-ts-para-js) 
    - #### [2.4 - Execute o arquivo gerado com Node.js](#24---execute-o-arquivo-gerado-com-nodejs)

- ## [3 - CONFIGURAÇÃO DO COMPILADOR E TS-NODE](#3---configuração-do-compilador-e-ts-node)
    - #### [3.1 - Inicialize e configure o tsconfig.json](#31---inicialize-e-configure-o-tsconfigjson)
    - #### [3.2 - Execução rápida com ts-node](#32---execução-rápida-com-ts-node)

- ## [4 - MODULARIZANDO O CÓDIGO E ESTRUTURA DE PROJETO](#4---modularizando-o-código-e-estrutura-de-projeto)
    - #### [4.1 - Função Simples e Exportação Inicial](#41---função-simples-e-exportação-inicial)
    - #### [4.2 - Organizando Dados em um Módulo Dedicado](#42---organizando-dados-em-um-módulo-dedicado)
    - #### [4.3 - Consumindo Módulos: Importação e Iteração (loop.ts)](#43---consumindo-módulos-importação-e-iteração-loopts)

- ## [5 - NODE.JS COM HTTP / EXPRESS + TYPESCRIPT](#5---nodejs-com-http--express--typescript)
    - #### [5.1 - Instalando dependências do Express](#51---instalando-dependências-do-express)
    - #### [5.2 - Estrutura inicial de pastas](#52---estrutura-inicial-de-pastas)
    - #### [5.3 - Criando a aplicação Express (app.ts)](#53---criando-a-aplicação-express-appts)
    - #### [5.4 - Definindo rotas HTTP (routes.ts)](#54---definindo-rotas-http-routests)
    - #### [5.5 - Inicializando o servidor HTTP (server.ts)](#55---inicializando-o-servidor-http-serverts)
    - #### [5.6 - Executando o servidor com ts-node](#56---executando-o-servidor-com-ts-node)
    - #### [5.7 - Observações Importantes](#57---observações-importantes)

- ## [6 - API PROFISSIONAL: ARQUITETURA E PRODUÇÃO](#6---api-profissional-arquitetura-e-produção)
    - #### [6.1 - Separando responsabilidades: Controllers e Services](#61---separando-responsabilidades-controllers-e-services)
    - #### [6.2 - Criando um Service (Lógica de Negócio)](#62---criando-um-service-lógica-de-negócio)
    - #### [6.3 - Criando um Controller tipado](#63---criando-um-controller-tipado)
    - #### [6.4 - Tipagem de Request Body](#64---tipagem-of-request-body)
    - #### [6.5 - Middleware de Erro Global](#65---middleware-de-erro-global)
    - #### [6.6 - Variáveis de Ambiente (.env)](#66---variáveis-de-ambiente-env)
    - #### [6.7 - Scripts de Build e Produção](#67---scripts-de-build-e-produção)
<br /> 
<hr>
<br /> 


## <strong>1 - INICIANDO UM PROJETO</strong>

- ### <strong>1.1 - Crie um diretório para o projeto</strong>
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
    - Para habilitar tipagem estática e compatibilidade com o ambiente Node.js:

        - Atenção: Mantenha a compatibilidade entre as versões do <strong>TypeScript</strong>, do <strong>Node</strong> e da biblioteca <strong>@types/node</strong>.

    ```sh
    # Instala o TypeScript como dependência de desenvolvimento
    npm i -D typescript
    
    # Instala as definições de tipo para o Node.js
    npm i -D @types/node 
    
    # Garante o uso da versão LTS (Long Term Support) do Node.js
    nvm install --lts
    ```

- ### <strong>1.4 - Crie os diretórios src e dist</strong>

    Organizaremos o projeto separando o código original do código gerado para produção. Por isso, na raíz do projeto, rode o comando:

    ```sh
    mkdir src dist
    ```

    <code>src</code>: Diretório dos arquivos fonte (<code>.ts</code>).

    <code>dist</code>: Onde o compilador (<code>tsc</code>) salvará os arquivos compilados (<code>.js</code>).

<br />

## <strong>2 - HELLO, WORLD!</strong> 
- ### <strong>2.1 - Crie o script dentro da pasta src</strong>
    Sempre trabalharemos com os arquivos fonte dentro de <code>src</code>:
    ```sh
    touch src/hello.ts 
    ```

- ### <strong>2.2 - Escreva a função com tipagem void</strong>
    
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

- ### <strong>3.1 - Inicialize e configure o tsconfig.json</strong>
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
                <td>O TypeScript pode aplicar interop automaticamente dependendo do <code>compilerOptions.module</code>.</td>
                <td>Facilita a convivência em projetos CommonJS ou híbridos, automatizando a tradução entre ESM e CJS.</td>
            </tr>
            <tr>
                <td style="padding: 8px;"><strong><code>true</code></strong></td>
                <td>Desliga o Interop e exige coerência exata (verbatim).</td>
                <td>Ideal para projetos puramente ESM (<code>"type": "module"</code>), garantindo que o código escrito seja exatamente o executado.</td>
            </tr>
        </tbody>
    </table>    
    </details>

- ### <strong>3.2 - Execução rápida com ts-node</strong>
    
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

## <strong>4 - MODULARIZANDO O CÓDIGO E ESTRUTURA DE PROJETO</strong> 

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

- ### <strong>4.2 - Organizando Dados em um Módulo Dedicado</strong>

    Agora, vamos dar um passo à frente elevando um pouco mais a complexidade do código.
    Criamos o diretório <code>data</code> dentro de <code>src</code>:

    ```sh
    mkdir src/data
    ```

    Dentro do novo diretório, criamos um arquivo para armazenar os dados:

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

    Vamos criar uma função para efetuar um loop (certifique-se de estar na pasta <code>src</code>):
        
    ```sh
    cd .. && touch loop.ts
    ```

    Neste loop, vamos saudar cada uma das personalidades no array chamando a função <code>greet()</code> no módulo <code>src/greet</code>.

    ```ts
    // src/loop.ts

    import people from './data/data';
    import { greet } from './greet';

    // Array<string> é equivalente a string[]
    function loop(people: Array<string>): void {
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
    ```

    Rodando o comando na raíz do projeto:

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

<br />

## <strong>5 - NODE.JS COM HTTP / EXPRESS + TYPESCRIPT</strong>

Nesta seção, vamos evoluir do uso de scripts simples para a criação de uma API HTTP básica, utilizando <strong>Express.js</strong> com TypeScript, seguindo boas práticas de organização de código.

- ### <strong>5.1 - Instalando dependências do Express</strong>
    Instale o framework e suas respectivas definições de tipos para o ambiente de desenvolvimento:

    ```sh
    npm i express
    npm i -D @types/express
    ```

- ### <strong>5.2 - Estrutura inicial de pastas</strong>
    Organizaremos o projeto para separar as responsabilidades de configuração, rotas e inicialização:

    ```sh
    src/
     ├── app.ts        # Configuração da aplicação (middleware/rotas)
     ├── server.ts     # Ponto de entrada (bootstrap do servidor)
     └── routes.ts     # Definição dos endpoints
    ```
    Crie os arquivos necessários:
    ```sh
    touch src/app.ts src/server.ts src/routes.ts
    ```



- ### <strong>5.3 - Criando a aplicação Express (app.ts)</strong>
    O arquivo <code>app.ts</code> configura a instância da aplicação:

    ```ts
    // src/app.ts
    import express, { Application } from 'express';
    import routes from './routes';

    const app: Application = express();

    app.use(express.json()); // Permite o parse de corpos em JSON
    app.use(routes);

    export default app;
    ```

- ### <strong>5.4 - Definindo rotas HTTP (routes.ts)</strong>
    Utilizaremos o <code>Router</code> do Express para desacoplar as rotas da lógica principal:

    ```ts
    // src/routes.ts
    import { Router, Request, Response } from 'express';

    const router = Router();

    router.get('/health', (req: Request, res: Response) => {
        return res.status(200).json({ status: 'ok' });
    });

    export default router;
    ```
    Observe o uso das interfaces <code>Request</code> e <code>Response</code> para garantir a tipagem dos objetos do Express.

- ### <strong>5.5 - Inicializando o servidor HTTP (server.ts)</strong>
    Separar o <code>app</code> do <code>server</code> facilita a execução de testes automatizados posteriormente:

    ```ts
    // src/server.ts
    import app from './app';

    const PORT = 3000;

    app.listen(PORT, () => {
        console.log(`🚀 Server running on http://localhost:${PORT}`);
    });
    ```

- ### <strong>5.6 - Executando o servidor com ts-node</strong>
    Rode o servidor em ambiente de desenvolvimento e teste o endpoint:

    ```sh
    npx ts-node src/server.ts
    ```

    Acesse via navegador ou terminal (curl):
    ```sh
    curl http://localhost:3000/health
    # Resposta: { "status": "ok" }
    ```

- ### <strong>5.7 - Observações Importantes</strong>
    * **Produção:** Sempre utilize o <code>tsc</code> para gerar arquivos JS na pasta <code>dist</code> antes do deploy.
    * **Runtime:** O Node.js executará o código transpilado; o TypeScript é uma ferramenta de auxílio em tempo de desenvolvimento.
    * **Escalabilidade:** A separação <code>app/server/routes</code> é o primeiro passo para padrões mais avançados como Clean Architecture ou Hexagonal.

<br />

## <strong>6 - API PROFISSIONAL: ARQUITETURA E PRODUÇÃO</strong>

Nesta seção, evoluiremos nossa API para um formato profissional, introduzindo a separação de responsabilidades (Pattern Service/Controller), tratamento centralizado de erros e fluxo de build.

- ### <strong>6.1 - Separando responsabilidades: Controllers e Services</strong>
    Para manter o código escalável, dividimos as tarefas:
    * **Controllers**: Lidam com o protocolo HTTP (recebem <code>req</code> e enviam <code>res</code>).
    * **Services**: Contêm a lógica de negócio (puramente TypeScript, sem conhecer o Express).

    Estrutura de diretórios:
    ```sh
    mkdir src/controllers src/services src/middlewares
    touch src/controllers/health.controller.ts src/services/health.service.ts src/middlewares/error.middleware.ts
    ```

- ### <strong>6.2 - Criando um Service (Lógica de Negócio)</strong>
    O Service executa as regras e retorna dados puros. Isso facilita testes unitários:

    ```ts
    // src/services/health.service.ts
    export function checkHealth() {
        return {
            status: 'ok',
            timestamp: new Date().toISOString(),
        };
    }
    ```

- ### <strong>6.3 - Criando um Controller tipado</strong>
    O Controller recebe a requisição, chama o Service e define o status HTTP:

    ```ts
    // src/controllers/health.controller.ts
    import { Request, Response } from 'express';
    import { checkHealth } from '../services/health.service';

    export function healthController(req: Request, res: Response) {
        const result = checkHealth();
        return res.status(200).json(result);
    }
    ```

- ### <strong>6.4 - Tipagem de Request Body</strong>
    Em endpoints de escrita (POST/PUT), utilizamos Generics para tipar o corpo da requisição, garantindo autocomplete e segurança:

    ```ts
    // Exemplo: Request<Params, ResBody, ReqBody, Query>
    interface CreateUserBody {
        name: string;
        email: string;
    }

    export function createUserController(
        req: Request<{}, {}, CreateUserBody>, 
        res: Response
    ) {
        const { name, email } = req.body; // Totalmente tipado!
        return res.status(201).json({ name, email });
    }
    ```

- ### <strong>6.5 - Middleware de Erro Global</strong>
    Um único local para capturar falhas em toda a aplicação. **Importante:** deve ser o último <code>app.use()</code> no arquivo <code>app.ts</code>.

    ```ts
    // src/middlewares/error.middleware.ts
    import { Request, Response, NextFunction } from 'express';

    export function errorMiddleware(err: Error, req: Request, res: Response, next: NextFunction) {
        console.error(err.stack);
        return res.status(500).json({ message: 'Internal server error' });
    }
    ```

- ### <strong>6.6 - Variáveis de Ambiente (.env)</strong>
    Instale o <code>dotenv</code> para gerenciar configurações sensíveis:
    ```sh
    npm i dotenv
    ```
    Carregue-o no topo do seu <code>src/server.ts</code>:
    ```ts
    import 'dotenv/config';
    import app from './app';

    const PORT = process.env.PORT || 3000;
    app.listen(PORT, () => console.log(`🚀 Server on port ${PORT}`));
    ```

- ### <strong>6.7 - Scripts de Build e Produção</strong>
    Configure seu <code>package.json</code> para automatizar o fluxo:

    ```json
    "scripts": {
      "dev": "ts-node src/server.ts",
      "build": "tsc",
      "start": "node dist/server.js"
    }
    ```
    * **Desenvolvimento**: <code>npm run dev</code>
    * **Compilação**: <code>npm run build</code> (Gera a pasta <code>dist</code>)
    * **Produção**: <code>npm start</code>

<br />
<hr>

<hr>