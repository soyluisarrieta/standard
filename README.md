# Pasos desde 0

### 1. Crear proyecto dentro del directorio:

```bash
npm init -y
```

### 2. Instalar Standard JS como dependencia de desarrollo

```bash
npm install standard -D
```

### 3. En el archivo package.json, debajo de las devDependencies de la siguiente manera:

```javascript
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

## Crear scripts para reportes y correcciones

En el package.json agregamos los scripts:

```javascript
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
