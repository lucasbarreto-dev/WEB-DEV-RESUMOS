# 📌 Índice

1. [Criar a pasta do projeto](#1---criar-a-pasta-do-projeto)
2. [Criar o ambiente virtual](#2---criar-o-ambiente-virtual)
    - 2.1 [Criar o `.venv`](#21---criar-o-venv)
    - 2.2 [Ativar o ambiente virtual](#22---ativar-o-ambiente-virtual)
    - 2.3 [Instalar dependências](#23---instalar-dependências)
    - 2.4 [Desativar o ambiente virtual](#24---desativar-o-ambiente-virtual)
3. [Criar um script simples](#3---criar-um-script-simples)
4. [Rodar o script localmente](#4---rodar-o-script-localmente)
5. [Criar o Dockerfile](#5---criar-o-dockerfile)
    - 5.1 [FROM](#51---from-python312-slim)
    - 5.2 [WORKDIR](#52---workdir-app)
    - 5.3 [COPY](#53---copy--app)
    - 5.4 [CMD](#54---cmd-python-hellopy)
6. [Construir a imagem](#6---construir-a-imagem)
7. [Rodar o container](#7---rodar-o-container)
8. [Desenvolvimento Interativo (Modo Live)](#8---desenvolvimento-interativo-modo-live)
9. [Estrutura definitiva](#9---estrutura-definitiva-para-iniciar-o-projeto)

---

# 1 - Criar a pasta do projeto

```sh
mkdir my_python_project
cd my_python_project
```

<p>Estrutura inicial:</p>

```sh
my_python_project/
```

<br />

# 2 - Criar o ambiente virtual

## 2.1 - Criar o `.venv`

```sh
python3 -m venv .venv
```

<p>Esse comando cria um ambiente virtual dentro da pasta do projeto.</p>

<p>Estrutura agora:</p>

```sh
my_python_project/
└── .venv/
```

<br />

## 2.2 - Ativar o ambiente virtual

```sh
source .venv/bin/activate
```

<p>Após ativar, o terminal normalmente exibirá algo assim:</p>

```sh
(.venv) user@machine my_python_project %
```

<br />

## 2.3 - Instalar dependências

```sh
python3 -m pip install <nome_do_pacote>
```

ou

```sh
pip install <nome_do_pacote>
```

<p>Exemplo:</p>

```sh
python3 -m pip install numpy
```

<p><strong>Diferença entre os dois:</strong></p>

- <code>python3 -m pip install</code> garante que você está usando o <code>pip</code> da versão correta do Python.
- <code>pip install</code> usa o <code>pip</code> padrão configurado no sistema.

<p>Se houver múltiplas versões do Python instaladas, prefira:</p>

```sh
python3 -m pip install <nome_do_pacote>
```

<br />

## 2.4 - Desativar o ambiente virtual

```sh
deactivate
```

<br />

# 3 - Criar um script simples

<p>Crie o arquivo:</p>

```sh
touch hello.py
```

<p>Conteúdo:</p>

```py
# my_python_project/hello.py

def greet():
    print("Hello, world!")

greet()
```

<p>Estrutura agora:</p>

```sh
my_python_project/
├── .venv/
└── hello.py
```

<br />

# 4 - Rodar o script localmente

```sh
python3 hello.py
```

<p>Saída esperada:</p>

```sh
Hello, world!
```

<p>Se quiser abrir o terminal interativo com o script carregado:</p>

```sh
python3 -i hello.py
```

<br />

# 5 - Criar o Dockerfile

<p>Agora vamos criar uma imagem Docker para rodar o projeto sem depender do Python instalado na máquina.</p>

```sh
touch Dockerfile
```

<p>Conteúdo:</p>

```Dockerfile
# my_python_project/Dockerfile

FROM python:3.12-slim

WORKDIR /app

COPY . /app

CMD ["python", "hello.py"]
```

<p>Vamos entender cada linha.</p>

---

## 5.1 - FROM python:3.12-slim

<p>Define a imagem base:</p>

```Dockerfile
python:3.12-slim
```

<p>significa:</p>

```sh
Linux + Python 3.12 (versão enxuta)
```

<p>A versão <code>slim</code> é mais leve e ideal para projetos simples e ambientes de produção.</p>

---

## 5.2 - WORKDIR /app

<p>Define o diretório de trabalho dentro do container.</p>

<p>Equivalente a:</p>

```sh
cd /app
```

---

## 5.3 - COPY . /app

<p>Copia os arquivos do projeto para dentro do container.</p>

```sh
host project
  │
  ▼
container /app
```

<p>Então o container terá algo como:</p>

```sh
/app
├── hello.py
└── Dockerfile
```

---

## 5.4 - CMD ["python", "hello.py"]

<p>Define o comando executado quando o container iniciar.</p>

<p>Equivalente a rodar:</p>

```sh
python hello.py
```

<p>Dica: Adicione um arquivo <code>.dockerignore</code> para evitar copiar arquivos desnecessários para dentro da imagem, como o <code>.venv</code>.</p>

<p>Exemplo de <code>.dockerignore</code>:</p>

```dockerignore
.venv
__pycache__
*.pyc
```

<br />

# 6 - Construir a imagem

```sh
docker build -t my_python_project .
```

<p>Explicação:</p>

```sh
| parte                    | significado                                                           |
|--------------------------|-----------------------------------------------------------------------|
| docker build             | Comando para criar uma imagem a partir de um Dockerfile              |
| -t my_python_project     | Tag: nomeia a imagem para podermos referenciá-la depois              |
| .                        | Contexto: indica que os arquivos e o Dockerfile estão na pasta atual |
```

<br />

# 7 - Rodar o container

```sh
docker run --rm my_python_project
```

<p>Saída esperada:</p>

```sh
Hello, world!
```

<p>Explicação:</p>

- <code>docker run</code>: executa um container
- <code>--rm</code>: remove o container automaticamente ao finalizar
- <code>my_python_project</code>: nome da imagem criada

<br />

# 8 - Desenvolvimento Interativo (Modo Live)

<p>Se quiser entrar no container para rodar comandos e testar alterações em tempo real, execute:</p>

```sh
docker run -it --rm -v "$(pwd)":/app my_python_project bash
```

<p>O que este comando faz?</p>

- <code>-it</code>: abre um terminal interativo dentro do container
- <code>--rm</code>: remove o container ao finalizar
- <code>-v "$(pwd)":/app</code>: sincroniza sua pasta atual com a pasta <code>/app</code> do container
- <code>bash</code>: em vez de executar apenas o script, abre o terminal Linux do container

<p>Uma vez dentro do container, você verá algo como:</p>

```sh
root@container_id:/app#
```

<p>Agora execute manualmente:</p>

```sh
python hello.py
```

<p>Saída:</p>

```sh
Hello, world!
```

<br />

# 9 - Estrutura definitiva para iniciar o projeto

<p>Seu projeto agora está preparado para rodar tanto localmente quanto com Docker:</p>

```sh
my_python_project/
├── .dockerignore
├── .venv/
├── Dockerfile
└── hello.py
```

<p>Qualquer pessoa pode rodar:</p>

```sh
docker build -t my_python_project .
docker run --rm my_python_project
```

<p>Ou, se quiser entrar no container:</p>

```sh
docker run -it --rm -v "$(pwd)":/app my_python_project bash
```