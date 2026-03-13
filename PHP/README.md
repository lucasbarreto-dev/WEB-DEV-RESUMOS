# 📌 Índice

1. [Criar a pasta do projeto](#1---criar-a-pasta-do-projeto)
2. [Criar o código PHP](#2---criar-o-código-php)
3. [Criar o Dockerfile](#3---criar-o-dockerfile)
    - 3.1 [FROM](#31---from-php83-cli)
    - 3.2 [WORKDIR](#32---workdir-app)
    - 3.3 [COPY](#33---copy--app)
    - 3.4 [CMD](#34---cmd-php-indexphp)
4. [Construir a imagem](#4---construir-a-imagem)
5. [Verificar a imagem](#5---verificar-a-imagem)
6. [Desenvolvimento Interativo (Modo Live)](#6---desenvolvimento-interativo-modo-live)
7. [Estrutura definitiva](#7---estrutura-definitiva-para-iniciar-o-projeto)

---

# 1 - Criar a pasta do projeto
```
mkdir my_php_project
cd my_php_project
```

<p>Estrutura inicial:</p>
    
```
my_php_project/
```
<br />

# 2 - Criar o código PHP
<p>Crie o arquivo:</p>

```
touch index.php
```

<p>Conteúdo:</p>

```
// my_php_project/index.php

<?php
echo "Hello World from Docker!" . PHP_EOL;
```

<p>Estrutura agora:</p>

```
my_php_project/
├── index.php
```
<br />

# 3 - Criar o Dockerfile

<p>Agora vamos criar a imagem do projeto.</p>

```
touch Dockerfile
```

<p>Conteúdo:</p>

```
// my_php_project/Dockerfile

FROM php:8.3-cli

WORKDIR /app

COPY . /app

CMD ["php", "index.php"]
```

<p>Vamos entender cada linha.</p>

- ### 3.1 - FROM php:8.3-cli
    <p>Define a imagem base:</p>

    ```
    php:8.3-cli
    ```

    <p>significa:</p>

    ```
    Linux + PHP CLI
    ```

- ### 3.2 - WORKDIR /app

    <p>Define o diretório de trabalho dentro do container.</p>

    <p>Equivalente a:</p>

    ```
    cd /app
    ```

- ### 3.3 - COPY . /app
    <p>Copia os arquivos do projeto para o container.</p>

    ```
    host project
      │
      ▼
    container /app
    ```

    <p>Então o container terá:</p>
    
    ```
    /app
    ├── index.php
    ```

- ### 3.4 - CMD ["php", "index.php"]

    <p>Define o comando executado quando o container inicia.</p>

    <p>Equivalente a rodar:</p>

    ```
    php index.php
    ```

<p>Dica: Adicione um arquivo <code>.dockerignore</code> para evitar copiar arquivos desnecessários para dentro da imagem.</p>    
<br />

# 4 - Construir a imagem

```
docker build -t my-php-app .
```

   -  <p>Explicação:</p>

        <!-- ```
        | parte          | significado       |
        | -------------- | ----------------- |
        | `docker build` | constrói imagem   |
        | `-t`           | define nome       |
        | `my-php-app`   | nome da imagem    |
        | `.`            | contexto de build |
        ``` -->
        ```
        | parte         | significado                                                           |
        |---------------|-----------------------------------------------------------------------|
        | docker build  | Comando para criar uma imagem a partir de um Dockerfile.              |
        | -t my-php-app | Tag: Nomeia a imagem para que possamos referenciá-la depois.          |
        | .             | Contexto: Indica que os arquivos e o Dockerfile estão na pasta atual. |
        ```

<br />

# 5 - Verificar a imagem

```
docker images
```

<p>Você verá algo como:</p>

```
REPOSITORY   TAG       IMAGE ID
my-php-app   latest    8f3b2a4d
```

<br />

# 6 - Desenvolvimento Interativo (Modo "Live")
<p>Se quiser entrar no container para rodar comandos e ver alterações no código em tempo real, execute:</p>

<!-- ```
docker run -it --rm my_php_project bash
``` -->

````
docker run -it --rm -v "$(pwd)":/app my_php_project bash
````

<p>O que este comando faz?

<code>-it</code>: Abre um terminal interativo dentro do container.

<code>-v "$(pwd)":/app</code>: Sincroniza sua pasta atual do computador com a pasta /app do container. Se você mudar o código no VS Code, ele muda lá dentro na hora!

<code>bash</code>: Em vez de rodar o script e fechar, ele te dá acesso ao terminal do Linux.</p>

<code>--rm</code>: Remove o container automaticamente após a execução. Isso evita que seu computador fique cheio de containers parados "lixo".</p>

<p>Uma vez dentro do container, você verá o prompt:</p>

````
root@container_id:/app#
````

Agora execute o script manualmente:

````
php index.php
````

<p>Saída:</p>

```
Hello World from Docker!
```

<br />

# 7 - Estrutura definitiva para iniciar o projeto

<p>Seu projeto agora é auto-contido:</p>

```
my_php_project/
 ├── Dockerfile
 └── index.php
 ```

<p>Qualquer pessoa pode rodar:</p>

```
docker build -t my-php-app .
docker run -it --rm my_php_project bash
```
