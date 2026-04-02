# INTRODUÇÃO AO PYTHON COM DOCKER

## Objetivo

Este README documenta o processo básico para iniciar um projeto em Python, utilizando tanto o ambiente virtual local (`.venv`) quanto a containerização com Docker.  
A proposta é construir uma base sólida para rodar scripts simples, instalar dependências e preparar um ambiente reprodutível de desenvolvimento.

## Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- Python 3
- pip
- Docker
- Terminal / Shell (Linux, macOS ou WSL no Windows)

<br />

# <strong>SUMÁRIO</strong>

- ## [1 - INICIANDO UM PROJETO](#1---iniciando-um-projeto)
    - #### [1.1 - Criar a pasta do projeto](#11---criar-a-pasta-do-projeto)
    - #### [1.2 - Criar o ambiente virtual (`.venv`)](#12---criar-o-ambiente-virtual-venv)
    - #### [1.3 - Ativar o ambiente virtual](#13---ativar-o-ambiente-virtual)
    - #### [1.4 - Instalar dependências](#14---instalar-dependências)
    - #### [1.5 - Desativar o ambiente virtual](#15---desativar-o-ambiente-virtual)

- ## [2 - HELLO, WORLD!](#2---hello-world)
    - #### [2.1 - Criar um script simples](#21---criar-um-script-simples)
    - #### [2.2 - Executar o script localmente](#22---executar-o-script-localmente)
    - #### [2.3 - Rodar o script em modo interativo](#23---rodar-o-script-em-modo-interativo)

- ## [3 - MODULARIZANDO O CÓDIGO E ESTRUTURA DE PROJETO](#3---modularizando-o-código-e-estrutura-de-projeto)
    - #### [3.1 - Função Simples e Exportação Inicial](#31---função-simples-e-exportação-inicial)
    - #### [3.2 - Organizando Dados em um Módulo Dedicado](#32---organizando-dados-em-um-módulo-dedicado)
    - #### [3.3 - Consumindo Módulos: Importação e Iteração (`loop.py`)](#33---consumindo-módulos-importação-e-iteração-looppy)

- ## [4 - PYTHON COM DOCKER](#4---python-com-docker)
    - #### [4.1 - Criar o Dockerfile](#41---criar-o-dockerfile)
    - #### [4.2 - Entendendo o Dockerfile](#42---entendendo-o-dockerfile)
    - #### [4.3 - Criar o `.dockerignore`](#43---criar-o-dockerignore)

- ## [5 - EXECUTANDO O PROJETO COM DOCKER](#5---executando-o-projeto-com-docker)
    - #### [5.1 - Construir a imagem](#51---construir-a-imagem)
    - #### [5.2 - Rodar o container](#52---rodar-o-container)
    - #### [5.3 - Desenvolvimento interativo (modo live)](#53---desenvolvimento-interativo-modo-live)

- ## [6 - ESTRUTURA FINAL DO PROJETO](#6---estrutura-final-do-projeto)
<br />
<hr>
<br />

## <strong>1 - INICIANDO UM PROJETO</strong>

- ### <strong>1.1 - Criar a pasta do projeto</strong>

    O primeiro passo é criar o diretório onde o projeto ficará armazenado e navegar até ele:

    ```sh
    mkdir my_python_project && cd my_python_project
    ```

    Estrutura inicial:

    ```sh
    my_python_project/
    ```

- ### <strong>1.2 - Criar o ambiente virtual (`.venv`)</strong>

    O ambiente virtual permite isolar as dependências do projeto, evitando conflitos com outros projetos Python instalados na máquina.

    ```sh
    python3 -m venv .venv
    ```

    Estrutura agora:

    ```sh
    my_python_project/
    └── .venv/
    ```

- ### <strong>1.3 - Ativar o ambiente virtual</strong>

    Para ativar o ambiente virtual no terminal:

    ```sh
    source .venv/bin/activate
    ```

    Após ativar, o terminal normalmente exibirá algo semelhante a:

    ```sh
    (.venv) user@machine my_python_project %
    ```

- ### <strong>1.4 - Instalar dependências</strong>

    Para instalar bibliotecas externas no projeto:

    ```sh
    python3 -m pip install nome_do_pacote
    ```

    ou

    ```sh
    pip install nome_do_pacote
    ```

    Exemplo:

    ```sh
    python3 -m pip install numpy
    ```

    **Diferença entre os comandos:**

    - `python3 -m pip install` garante que você está usando o `pip` da versão correta do Python.
    - `pip install` usa o `pip` padrão configurado no sistema.

    Se houver múltiplas versões do Python instaladas, prefira:

    ```sh
    python3 -m pip install nome_do_pacote
    ```

- ### <strong>1.5 - Desativar o ambiente virtual</strong>

    Quando quiser sair do ambiente virtual:

    ```sh
    deactivate
    ```

<br />

## <strong>2 - HELLO, WORLD!</strong>

- ### <strong>2.1 - Criar um script simples</strong>

    Crie o arquivo:

    ```sh
    touch hello.py
    ```

    Conteúdo:

    ```py
    # hello.py

    def greet():
        print("Hello, world!")

    greet()
    ```

    Estrutura agora:

    ```sh
    my_python_project/
    ├── .venv/
    └── hello.py
    ```

- ### <strong>2.2 - Executar o script localmente</strong>

    Para rodar o script com o Python instalado localmente:

    ```sh
    python3 hello.py
    ```

    Saída esperada:

    ```sh
    Hello, world!
    ```

- ### <strong>2.3 - Rodar o script em modo interativo</strong>

    Se quiser abrir o interpretador Python com o script já carregado:

    ```sh
    python3 -i hello.py
    ```

<br />§

## <strong>3 - MODULARIZANDO O CÓDIGO E ESTRUTURA DE PROJETO</strong>

- ### <strong>3.1 - Função Simples e Exportação Inicial</strong>

    Agora vamos dar um passo além do script único.  
    Em Python, também é uma boa prática separar responsabilidades em arquivos diferentes, transformando partes do código em módulos reutilizáveis.

    Vamos criar um arquivo responsável apenas por saudar uma pessoa:

    ```sh
    touch greet.py
    ```

    Conteúdo:

    ```py
    # greet.py

    def greet(name: str) -> str:
        return f"- Hi, {name}!"
    ```

    Nesse caso:

    - `name: str` indica que a função recebe uma string
    - `-> str` indica que a função retorna uma string

    Podemos testar rapidamente criando um uso simples temporário:

    ```py
    # greet.py

    def greet(name: str) -> str:
        return f"- Hi, {name}!"

    print(greet("Barbie"))
    print(greet("Ken"))
    ```

    Rodando o comando:

    ```sh
    python3 greet.py
    ```

    O retorno no console será:

    ```sh
    - Hi, Barbie!
    - Hi, Ken!
    ```

- ### <strong>3.2 - Organizando Dados em um Módulo Dedicado</strong>

    Agora vamos separar também os dados do programa em outro módulo.

    Crie um diretório para armazenar esses dados:

    ```sh
    mkdir data
    ```

    Dentro dele, crie o arquivo:

    ```sh
    touch data/data.py
    ```

    Conteúdo:

    ```py
    # data/data.py

    people = [
        "Ada Lovelace",
        "Alan Turing",
        "Grace Hopper",
        "Linus Torvalds",
        "Margaret Hamilton",
        "Ken Thompson",
        "Dennis Ritchie",
        "Barbara Liskov",
        "Tim Berners-Lee",
        "James Gosling",
    ]
    ```

    Agora temos uma lista separada em um módulo próprio, o que facilita manutenção e reaproveitamento.

- ### <strong>3.3 - Consumindo Módulos: Importação e Iteração (`loop.py`)</strong>

    Agora vamos criar um arquivo principal para consumir os módulos criados anteriormente:

    ```sh
    touch loop.py
    ```

    Conteúdo:

    ```py
    # loop.py

    from greet import greet
    from data.data import people

    def loop(people: list[str]) -> None:
        for person in people:
            print(greet(person))

    loop(people)
    ```

    Explicação:

    - `from greet import greet`: importa a função `greet()` do arquivo `greet.py`
    - `from data.data import people`: importa a lista `people` do arquivo `data/data.py`
    - `list[str]`: indica que a função recebe uma lista de strings
    - `-> None`: indica que a função não retorna valor, apenas executa ações

    > **Importante:**  
    > Agora que `greet.py` virou um módulo reutilizável, remova os `print()` temporários dele.  
    > Ele deve conter **somente a função**:

    ```py
    # greet.py

    def greet(name: str) -> str:
        return f"- Hi, {name}!"
    ```

    Rodando o comando na raiz do projeto:

    ```sh
    python3 loop.py
    ```

    O retorno no console será algo como:

    ```sh
    - Hi, Ada Lovelace!
    - Hi, Alan Turing!
    - Hi, Grace Hopper!
    - Hi, Linus Torvalds!
    - Hi, Margaret Hamilton!
    - Hi, Ken Thompson!
    - Hi, Dennis Ritchie!
    - Hi, Barbara Liskov!
    - Hi, Tim Berners-Lee!
    - Hi, James Gosling!
    ```

    Estrutura do projeto até aqui:

    ```sh
    my_python_project/
    ├── .venv/
    ├── data/
    │   └── data.py
    ├── greet.py
    ├── hello.py
    └── loop.py
    ```

<br />

## <strong>3 - PYTHON COM DOCKER</strong>

- ### <strong>3.1 - Criar o Dockerfile</strong>

    Agora vamos criar uma imagem Docker para rodar o projeto sem depender do Python instalado diretamente na máquina.

    ```sh
    touch Dockerfile
    ```

    Conteúdo:

    ```Dockerfile
    # my_python_project/Dockerfile

    FROM python:3.12-slim

    WORKDIR /app

    COPY . /app

    CMD ["python", "hello.py"]
    ```

- ### <strong>3.2 - Entendendo o Dockerfile</strong>

    Vamos analisar cada instrução:

    #### `FROM python:3.12-slim`

    Define a imagem base:

    ```Dockerfile
    python:3.12-slim
    ```

    Isso significa:

    ```sh
    Linux + Python 3.12 (versão enxuta)
    ```

    A versão `slim` é mais leve e adequada para ambientes simples ou de produção.

    #### `WORKDIR /app`

    Define o diretório de trabalho dentro do container.

    Equivalente a:

    ```sh
    cd /app
    ```

    #### `COPY . /app`

    Copia os arquivos do projeto para dentro do container.

    ```sh
    host project
      │
      ▼
    container /app
    ```

    O container terá algo como:

    ```sh
    /app
    ├── hello.py
    └── Dockerfile
    ```

    #### `CMD ["python", "hello.py"]`

    Define o comando executado quando o container iniciar.

    Equivalente a:

    ```sh
    python hello.py
    ```

- ### <strong>3.3 - Criar o `.dockerignore`</strong>

    É uma boa prática evitar copiar arquivos desnecessários para dentro da imagem, como o ambiente virtual local.

    Crie o arquivo:

    ```sh
    touch .dockerignore
    ```

    Conteúdo sugerido:

    ```dockerignore
    .venv
    __pycache__
    *.pyc
    ```

<br />

## <strong>4 - EXECUTANDO O PROJETO COM DOCKER</strong>

- ### <strong>4.1 - Construir a imagem</strong>

    Para construir a imagem Docker do projeto:

    ```sh
    docker build -t my_python_project .
    ```

    Explicação:

    ```sh
    | parte                | significado                                                           |
    |----------------------|-----------------------------------------------------------------------|
    | docker build         | Comando para criar uma imagem a partir de um Dockerfile              |
    | -t my_python_project | Tag: nomeia a imagem para podermos referenciá-la depois              |
    | .                    | Contexto: indica que os arquivos e o Dockerfile estão na pasta atual |
    ```

- ### <strong>4.2 - Rodar o container</strong>

    Para executar o projeto com Docker:

    ```sh
    docker run --rm my_python_project
    ```

    Saída esperada:

    ```sh
    Hello, world!
    ```

    Explicação:

    - `docker run`: executa um container
    - `--rm`: remove o container automaticamente ao finalizar
    - `my_python_project`: nome da imagem criada

- ### <strong>4.3 - Desenvolvimento interativo (modo live)</strong>

    Se quiser entrar no container para rodar comandos e testar alterações em tempo real:

    ```sh
    docker run -it --rm -v "$(pwd)":/app my_python_project bash
    ```

    O que este comando faz?

    - `-it`: abre um terminal interativo dentro do container
    - `--rm`: remove o container automaticamente ao finalizar
    - `-v "$(pwd)":/app`: sincroniza a pasta atual da máquina com a pasta `/app` do container
    - `bash`: em vez de apenas executar o script, abre um terminal Linux dentro do container

    Uma vez dentro do container, você verá algo como:

    ```sh
    root@container_id:/app#
    ```

    Agora execute manualmente:

    ```sh
    python hello.py
    ```

    Saída:

    ```sh
    Hello, world!
    ```

<br />

## <strong>5 - ESTRUTURA FINAL DO PROJETO</strong>

Ao final, o projeto estará organizado assim:

```sh
my_python_project/
├── .dockerignore
├── .venv/
├── Dockerfile
└── hello.py
```

Esse projeto agora pode ser executado de duas formas:

### Rodando localmente

```sh
python3 hello.py
```

### Rodando com Docker

```sh
docker build -t my_python_project .
docker run --rm my_python_project
```

### Entrando no container em modo interativo

```sh
docker run -it --rm -v "$(pwd)":/app my_python_project bash
```

<br />
<hr>