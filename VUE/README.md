# Getting Started


### <strong>1 - Configurando o ambiente</strong>

```sh
    npm install -g @vue/cli
```

```sh
    vue create <nome-do-projeto>
```

### <strong>2 - Instalar dependências</strong>

```sh
    cd <nome-do-projeto>
```

```sh
    npm install vue-notion@3.0.0-beta.1
```

### <strong>3 - Criar componente (src/components)</strong>

```html
    // /src/components/HelloWorld.vue

    <template>
        <h1>Hello world!</h1>
    </template>

    <script>
        export default {
            name: 'HelloWorld',
        };
    </script>
```

### <strong>4 - Importar componente ao App (/src))</strong>

```html
    // /src/App.vue

    <template>
        <div id="app">
            <HelloWorld />
        </div>
    </template>

    <script>
        import HelloWorld from './components/HelloWorld.vue';

        export default {
            name: 'App',
            components: {
                HelloWorld,
            },
        };
    </script>
```

### <strong>5 - Rodando o projeto</strong>

```sh
    npm run serve
```

