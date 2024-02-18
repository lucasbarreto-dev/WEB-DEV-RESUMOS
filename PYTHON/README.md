# Como iniciar um projeto em Python

## Sumário
- [1 - Setup](#1---setup)
    - [1.1 - No terminal, crie e navegue até o diretório do projeto.](#11---no-terminal-crie-e-navegue-até-o-diretório-do-projeto)
    - [1.2 - Crie o ambiente virtual (.venv).](#12---crie-o-ambiente-virtual-venv)
    - [1.3 - Ative o ambiente virtual.](#13---ative-o-ambiente-virtual)
    - [1.4 - Rodando um arquivo com o terminal interativo.](#14---rodando-um-arquivo-com-o-terminal-interativo)
    - [1.5 - Desativando o venv.](#15---desativando-o-venv)
    - [1.6 - Instalando as dependências do projeto.](#16---instalando-as-dependências-do-projeto)

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
    python3 -m venv <.venv>
  ```
  <p>O comando acima cria um diretório na pasta do projeto chamada '.venv'.</p>
 <br />

  - #### <strong>1.3 - Ative o ambiente virtual.</strong>

  ```sh
    source .venv/bin/activate
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


  - #### <strong>1.6 - Instalando as dependências do projeto.</strong>
  
  ```sh
    python3 -m pip install <nome_do_pacote>
  ```
  ou

  ```sh
    pip install <nome_do_pacote>
  ```
 <br />

  <p>
  O comando <code>python3 -m pip install</code> em Python é utilizado para instalar pacotes externos utilizando o gerenciador de pacotes pip associado à versão específica do Python indicada (neste caso, Python 3.x). Aqui está uma explicação detalhada de cada parte do comando:

  <strong>python3</strong>: Este é o interpretador Python que você está utilizando. Ao digitar python3, você está especificando explicitamente que deseja executar o comando usando a versão 3.x do Python. Dependendo da sua configuração do sistema, você pode simplesmente usar python para se referir à versão padrão do Python.

  <strong>-m pip</strong>: Isso diz ao Python para executar o módulo pip, que é o gerenciador de pacotes do Python. O uso de -m é uma forma de chamar um módulo como um script executável, sem depender do sistema de arquivos.

  <strong>install</strong>: Este é o comando que você está passando para o pip, indicando que você deseja instalar um pacote.

  Portanto, quando você executa python3 -m pip install, você está instruindo o Python a usar o pip da versão 3.x para instalar pacotes externos. Após install, você normalmente especificaria o nome do pacote que deseja instalar, como por exemplo, para instalar o pacote NumPy:
  </p>

  ```sh
    #ex.:
    python3 -m pip install numpy
  ```

 <br />

<p>
Ambos os comandos, <code>python3 -m pip install</code> e <code>pip install</code>, são usados para instalar pacotes externos em Python. No entanto, há uma diferença sutil entre os dois.

<code>python3 -m pip install</code> invoca o módulo pip do Python 3 diretamente. Isso garante que você está usando o pip associado explicitamente à versão do Python 3 que você está utilizando.
É útil quando você tem várias versões do Python instaladas no seu sistema e deseja garantir que está instalando o pacote para uma versão específica do Python.
Este método é mais explícito e pode ajudar a evitar conflitos entre diferentes versões do Python.</p>

<br />

<p>
<code>pip install</code> depende do pip padrão configurado em seu sistema. Dependendo das configurações de instalação, o pip padrão pode estar vinculado a uma versão específica do Python (por exemplo, Python 2.x ou Python 3.x).
Se apenas pip install for utilizado, pode não ser garantido que você está instalando o pacote para a versão correta do Python.
Em sistemas onde há apenas uma versão do Python instalada e o pip padrão está configurado corretamente, este comando funciona sem problemas.
Em resumo, "python3 -m pip install" é mais explícito e garante que você está utilizando o pip associado a uma versão específica do Python, enquanto "pip install" depende do pip padrão configurado em seu sistema, que pode ou não estar vinculado à versão do Python desejada.
</p>


### <strong>2 - Criando um script simples</strong>
```py
    #hello.py

    def greet():
        print('Hello, world!')
    
    greet()
```

