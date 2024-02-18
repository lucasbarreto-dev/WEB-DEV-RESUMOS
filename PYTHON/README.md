# Como iniciar um projeto em Python

## Sumário
- [1 - Setup](#1---setup)
    - [1.1 - No terminal, crie e navegue até o diretório do projeto.](#11---no-terminal-crie-e-navegue-até-o-diretório-do-projeto)
    - [1.2 - Crie o ambiente virtual (.venv).](#12---crie-o-ambiente-virtual-venv)
    - [1.3 - Ative o ambiente virtual.](#13---ative-o-ambiente-virtual)
    - [1.4 - Rodando um arquivo com o terminal interativo.](#14---rodando-um-arquivo-com-o-terminal-interativo)
    - [1.5 - Desativando o venv.](#15---desativando-o-venv)
- [2 - Criando um script simples](#2---criando-um-script-simples)


<br />

<hr>

### <strong>1 - Setup</strong>

  - #### <strong>1.1 - No terminal, crie e navegue até o diretório do projeto.</strong>

  ```sh
    mkdir my_project && cd my_project
  ```
 <br />

  - #### <strong>1.2 - Crie o ambiente virtual (.venv).</strong>

  ```sh
    python3 -m venv <myenv>
  ```
  <p>O comando acima cria um diretório na pasta do projeto chamada 'myenv'.</p>
 <br />

  - #### <strong>1.3 - Ative o ambiente virtual.</strong>

  ```sh
    source myenv/bin/activate
  ```
 <br />

  - #### <strong>1.4 - Rodando um arquivo com o terminal interativo.</strong>

  ```sh
    python3 -i <nome_do_arquivo>.py
  ```
 <br />

 - #### <strong>1.5 - Desativando o venv.</strong>

  ```sh
    deactivate
  ```
 <br />

### <strong>2 - Criando um script simples</strong>
```py
    #hello.py

    def greet():
        print('Hello, world!')
    
    greet()
```

