<h1 align="center">
  <a href="https://standardjs.com"><img src="https://cdn.rawgit.com/standard/standard/master/sticker.svg" alt="Standard - JavaScript Style Guide" width="200"></a>
  <br>
  JavaScript Standard Style
  <br>
  <br>
</h1>

<p align="center">
  <a href="https://discord.gg/ZegqCBr"><img src="https://img.shields.io/discord/612704110008991783" alt="discord"></a>
  <a href="https://github.com/standard/standard/actions/workflows/test-external.yml"><img src="https://github.com/standard/standard/actions/workflows/test-external.yml/badge.svg?branch=master" alt="External tests"></a>
  <a href="https://github.com/standard/standard/actions/workflows/test-internal.yml"><img src="https://github.com/standard/standard/actions/workflows/test-internal.yml/badge.svg?branch=master" alt="Internal tests"></a>
  <a href="https://github.com/standard/standard/actions?query=workflow%3A%22Old+test%22"><img src="https://github.com/standard/standard/workflows/Old%20test/badge.svg" alt="status badge old Node test"></a>
  <a href="https://www.npmjs.com/package/standard"><img src="https://img.shields.io/npm/v/standard.svg" alt="npm version"></a>
  <a href="https://www.npmjs.com/package/eslint-config-standard"><img src="https://img.shields.io/npm/dm/eslint-config-standard.svg" alt="npm downloads"></a>
  <a href="https://standardjs.com"><img src="https://img.shields.io/badge/code_style-standard-brightgreen.svg" alt="Standard - JavaScript Style Guide"></a>
</p>


### 1. Instalar Standard JS como dependencia de desarrollo

```bash
npm install standard -D
```

### 2. En el archivo package.json, debajo de las devDependencies de la siguiente manera:

```json
"devDependencies": {
  "standard": "^17.0.0"
},
"eslintConfig": {
  "extends": "./node_modules/standard/eslintrc.json"
}
```

---

#### Probar si funciona: Crear un archivo por ejemplo "prueba-eslint.js" y pegar lo siguiente:

```javascript
// "Extra semicolon." Significa que el punto y coma sobra y que deberías eliminarlo.
console.log('hola mundo');
```

---

# Crear scripts para reportes y correcciones

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

# Auto-corregir al guardar

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
