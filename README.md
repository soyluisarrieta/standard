<h1 align="center">
  <a href="https://standardjs.com"><img src="https://cdn.rawgit.com/standard/standard/master/sticker.svg" alt="Standard - JavaScript Style Guide" width="200"></a>
  <br>
  JavaScript Standard Style
  <br>
  <br>
</h1>

<p align="center">
  <a href="https://discord.gg/ZegqCBr"><img src="https://img.shields.io/discord/612704110008991783" alt="discord"></a>
  <a href="https://github.com/standard/standard/actions/workflows/test-internal.yml"><img src="https://github.com/standard/standard/actions/workflows/test-internal.yml/badge.svg?branch=master" alt="Internal tests"></a>
  <a href="https://github.com/standard/standard/actions?query=workflow%3A%22Old+test%22"><img src="https://github.com/standard/standard/workflows/Old%20test/badge.svg" alt="status badge old Node test"></a>
  <a href="https://www.npmjs.com/package/standard"><img src="https://img.shields.io/npm/v/standard.svg" alt="npm version"></a>
  <a href="https://www.npmjs.com/package/eslint-config-standard"><img src="https://img.shields.io/npm/dm/eslint-config-standard.svg" alt="npm downloads"></a>
  <a href="https://standardjs.com"><img src="https://img.shields.io/badge/code_style-standard-brightgreen.svg" alt="Standard - JavaScript Style Guide"></a>
</p>


1. Instalar Standard JS como dependencia de desarrollo
    ```bash
    npm install standard -D
    ```

2. En el archivo package.json, debajo de las devDependencies de la siguiente manera:
    ```json
    "devDependencies": {
      "standard": "^17.1.0"
    },
    "eslintConfig": {
      "extends": "./node_modules/standard/eslintrc.json"
    }
    ```

Probar si funciona: Crear un archivo por ejemplo "prueba-eslint.js" y pegar lo siguiente:

```javascript
// "Extra semicolon." Significa que el punto y coma sobra y que deberías eliminarlo.
console.log('hola mundo');
```

## Configurar standardjs en los proyectos de vite

Ve al archivo `.eslintrc.cjs` y solo cambia los extends:

```js
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    './node_modules/standard/eslintrc.json'
  ],
  ignorePatterns: ['dist', '.eslintrc.cjs'],
  parserOptions: { ecmaVersion: 'latest', sourceType: 'module' },
  settings: { react: { version: '18.2' } },
  plugins: ['react-refresh'],
  rules: {
    'react-refresh/only-export-components': [
      'warn',
      { allowConstantExport: true },
      // ⬇ Reglas que suelo desactivar
      'import/no-absolute-path': 'off',
    ],
  },
}
```

## Crear scripts para reportes y correcciones

En el package.json agregamos los scripts:

```json
"scripts": {
    "lint": "standard",
    "lint:fix": "standard  --fix"
  }
```

### Para ejecutarlos:

- Mostrar reportes

  ```bash
  npm run lint
  ```

- Corregir todo

  ```bash
  npm run lint:fix
  ```

## Auto-corregir al guardar

1. Crear carpeta `.vscode/`
2. Dentro de la carpeta crear el archivo `settings.json`
3. En el archivo ingresar el siguiente código:

    ```json
    {
      "editor.codeActionsOnSave": {
        "source.fixAll": true
      }
    }
    ```

Con esto, al presionar `Ctrl+S` se autocorregirá el código dependiendo de las reglas de [StandardJS]([https://](https://standardjs.com/))

## Para Typescript en Vite

1. Ejecutar comando de eslint para instalar standard-with-typescript
    ```bash
    npx eslit --init
    ```
2. Responder cada pregunta, ejemplo:
  ```bash
    ✔ How would you like to use ESLint? · style     
    ✔ What type of modules does your project use? · esm
    ✔ Which framework does your project use? · react
    ✔ Does your project use TypeScript? · No / Yes
    ✔ Where does your code run? · browser
    ✔ How would you like to define a style for your project? · guide
    ✔ Which style guide do you want to follow? · standard-with-typescript
    ✔ What format do you want your config file to be in? · JavaScript
    Checking peerDependencies of eslint-config-standard-with-typescript@latest
    The config that you've selected requires the following dependencies:
    
    eslint-plugin-react@latest eslint-config-standard-with-typescript@latest @typescript-eslint/eslint-plugin@^6.4.0 eslint@^8.0.1 eslint-plugin-import@^2.25.2 eslint-plugin-n@^15.0.0 || ^16.0.0  eslint-plugin-promise@^6.0.0 typescript@* 
    ✔ Would you like to install them now? · No / Yes
    ✔ Which package manager do you want to use? · npm
    Installing eslint-plugin-react@latest, eslint-config-standard-with-typescript@latest, @typescript-eslint/eslint-plugin@^6.4.0, eslint@^8.0.1, eslint-plugin-import@^2.25.2, eslint-plugin-n@^15.0.0 || ^16.0.0 , eslint-plugin-promise@^6.0.0, typescript@*
```

3. Identificar el proyecto con la ruta del tsconfig.json en el parserOptions de .eslintrc.cjs
  ```js
  // ...
  "parserOptions": {
        //...
        "project": "./tsconfig.json"
  },
  ```
  Gracias a esto, eslint detecta y muestra los problemas en todo el proyecto.
  
4. Crear .eslintignore para evitar que eslint muestre errores que no son errores:
  ```
  .eslintrc.cjs
  vite.config.ts
  
  postcss.config.js
  tailwind.config.js
  
  node_modules
  src/vite-env.d.ts
  ```


## Contribuciones

Te invito a compartir alguna sugerencia en una [solicitud de extracción](https://github.com/soyluisarrieta/standardjs/pulls).
