## Iniciando com React, Typescript e Vite

### 1 - Crie o projeto usando vite

```sh
    npm create vite@latest my-project
    cd my-project
    npm install
```

### 2 - Instale o Tailwindcss

```sh 
    npm install -D tailwindcss postcss autoprefixer
    npx tailwindcss init -p
```

<p>Ao rodar os comandos acima, o seu arquivo <code>postcss.config.js</code> deve estar assim:</p>

```js
// postcss.config.js

 export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}

```

### 3 - Configure os paths do seu template

```js
    // tailwind.config.js

    /** @type {import('tailwindcss').Config} */
    export default {
    content: [
        "./index.html",
        "./src/**/*.{js,ts,jsx,tsx}",
    ],
    theme: {
        extend: {},
    },
    plugins: [],
    }
```

### 4 - Add the Tailwind directives to your CSS

```js
    // ./src/index.css

    @tailwind base;
    @tailwind components;
    @tailwind utilities;
```

### 5 - Build

```sh
    npm run dev
```

## Referência/Docs

- Tailwind components: https://www.creative-tim.com/twcomponents/cheatsheet)