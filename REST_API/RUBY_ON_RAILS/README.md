# SETUP

## Sumário
- [1 - Iniciando o ambiente Ruby](#1---iniciando-o-ambiente-ruby)


<br />

<hr>

### <strong>0 - Generators</strong>
  <p>No Ruby on Rails, generators são ferramentas de linha de comando que ajudam você a criar rapidamente arquivos e códigos padrão para tarefas comuns em uma aplicação Rails.</p>
  

### <strong>1 - Iniciando o projeto Rails</strong>

  ```sh
    rails new Toy_App
  ```

  ```sh
    cd Toy_App
  ```

  ```sh
    bundle install --without production
  ```


 <br />

 ### <strong>2 - Sincronizando com o repositório remoto</strong>

  ```sh
    git init
  ```

  ```sh
    git add -A
  ```

  ```sh
    git commit -m 'Initialize repository'
  ```

  ```sh
    git remote add origin <endereço SSH>
  ```

  ```sh
    git branch -M main
  ```
  ```sh
    git push -u origin main
  ```

 <br />
