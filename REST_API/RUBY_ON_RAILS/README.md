# Sumário
- [Generators](#generators)
  - [Generators comuns no Rails](#generators-comuns-no-rails)
    - [Model Generator](#model-generator)
    - [Controller Generator](#controller-generator)
    - [Migration Generator](#migration-generator)
    - [Scaffold Generator](#scaffold-generator)
- [Documentações e tutoriais](#documentações-e-tutoriais)
- [Iniciando um projeto Rails](#iniciando-o-projeto-rails)


<br />

<hr>

## <strong>Generators</strong>
  <p>No Ruby on Rails, generators são ferramentas de linha de comando que ajudam você a criar rapidamente arquivos e códigos padrão para tarefas comuns em uma aplicação Rails.</p>

### <strong>Generators comuns no Rails</strong>
O Rails vem com vários geradores integrados para diferentes componentes de uma aplicação web. Aqui estão alguns dos mais comumente usados:

- #### <strong>Model Generator:</strong>
  Gera um novo arquivo de model, junto com o arquivo de migration correspondente para alterações de schema de banco de dados e arquivos de teste unitário.

  ```sh
  rails generate model ModelName attribute1:type attribute2:type
  ```

  Exemplo: 
  ```sh
  rails generate model User name:string email:string
  ```

  Este comando gera:

  - <code>app/models/user.rb</code> (Model file)
  - <code>db/migrate/XXXXXXXXXX_create_users.rb</code> (Migration file)
  - <code>test/models/user_test.rb</code> (Test file) ou <code>spec/models/user_spec.rb</code> se estiver usando RSpec

- #### <strong>Controller Generator:</strong> 
  Cria um novo controller junto com views, arquivos auxiliares (helpers) e configuração de roteamento.

  ```sh
    rails generate controller ControllerName action1 action2
  ```
  Exemplo:
  ```sh
    rails generate controller Users index show
  ```

  Este comando gera:

  - <code>app/controllers/users_controller.rb</code>(Controller file)
  - <code>app/views/users/index.html.erb</code> and <code>app/views/users/show.html.erb</code> (View templates)
  - <code>test/controllers/users_controller_test.rb</code> ou <code>spec/controllers/users_controller_spec.rb</code> se estiver usando RSpec
  - <code>app/helpers/users_helper.rb</code> (Helper file)

- #### <strong>Migration Generator</strong> 
  Cria um arquivo de migration para modificar o schema do banco de dados.

  ```sh
    rails generate migration MigrationName
  ```

  Exemplo: 
  ```sh
    rails generate migration AddAgeToUsers age:integer
  ```

  Este comando gera:

  - <code>db/migrate/XXXXXXXXXX_add_age_to_users.rb</code>(Controller file)

- #### <strong>Scaffold Generator:</strong> 
  Gera um conjunto completo de arquivos de models, views e controllers, incluindo ações CRUD e visualizações para um recurso.

  ```sh
    rails generate scaffold ModelName attribute1:type attribute2:type
  ```
  Exemplo: 
  ```sh
    rails generate scaffold Post title:string body:text
  ```

  Este comando gera:

  - <code>Models, controllers, views, helpers, migrations, e test files para o Post resource</code>(Controller file)

## Documentações e tutoriais
- Documentação Oficial: [Ruby-Doc](https://ruby-doc.org)
- Documentação colaborativa: [apidock](https://apidock.com/ruby)
- Rubyapi.org: [rubyapi](https://rubyapi.org)
- Ruby em vinte minutos: [ruby-lang](https://www.ruby-lang.org/pt/documentation/quickstart/)

<hr>

## Iniciando um projeto Rails

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

 ## Sincronizando com o repositório remoto

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
