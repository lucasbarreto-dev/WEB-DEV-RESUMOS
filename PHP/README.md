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
<br />

# 4 - Construir a imagem

```
docker build -t my-php-app .
```

   -  <p>Explicação:</p>

        ```
        | parte          | significado       |
        | -------------- | ----------------- |
        | `docker build` | constrói imagem   |
        | `-t`           | define nome       |
        | `my-php-app`   | nome da imagem    |
        | `.`            | contexto de build |
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

# 6 - Rodar o container
<p>Agora execute:</p>

```
docker run --rm my-php-app
```

<p>Saída:</p>

```
Hello World from Docker!
```

# 7 - Estrutura final do projeto

<p>Seu projeto agora é auto-contido:</p>

```
my_php_project/
 ├── Dockerfile
 └── index.php
 ```

<p>Qualquer pessoa pode rodar:</p>

```
docker build -t my-php-app .
docker run --rm my-php-app
```
