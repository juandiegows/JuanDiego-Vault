---
tags:
  - javascript
  - platzi
  - fundamentos
  - programación
---

# 01 — Fundamentos de JavaScript

> Fuente: [platzi.com/cursos/javascript](https://platzi.com/cursos/javascript)

---

## 🔤 Variables

```js
// var — scope de función (legacy, evitar)
var nombre = 'Juan';

// let — scope de bloque (reasignable)
let edad = 25;
edad = 26; // ✅

// const — scope de bloque (no reasignable)
const PI = 3.14159;
// PI = 3; // ❌ TypeError
```

---

## 📦 Tipos de Datos

```js
// Primitivos
typeof 42           // "number"
typeof "hola"       // "string"
typeof true         // "boolean"
typeof undefined    // "undefined"
typeof null         // "object" (bug histórico)
typeof Symbol()     // "symbol"
typeof 9007n        // "bigint"

// Objeto
typeof {}           // "object"
typeof []           // "object"
typeof function(){} // "function"
```

---

## 🔄 Funciones

```js
// Declaración (hoisting)
function saludar(nombre) {
  return `Hola, ${nombre}!`;
}

// Expresión
const saludar = function(nombre) {
  return `Hola, ${nombre}!`;
};

// Arrow function (moderno)
const saludar = (nombre) => `Hola, ${nombre}!`;

// Con valor por defecto
const saludar = (nombre = 'Mundo') => `Hola, ${nombre}!`;
```

---

## 🔢 Arrays y Métodos Clave

```js
const nums = [1, 2, 3, 4, 5];

// map — transforma cada elemento
nums.map(n => n * 2);       // [2, 4, 6, 8, 10]

// filter — filtra por condición
nums.filter(n => n > 2);    // [3, 4, 5]

// reduce — acumula un valor
nums.reduce((acc, n) => acc + n, 0); // 15

// find — primer elemento que cumple
nums.find(n => n > 3);      // 4

// some / every
nums.some(n => n > 4);      // true
nums.every(n => n > 0);     // true
```

---

## 🔮 Promesas y Async/Await

```js
// Promesa
fetch('/api/users')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));

// Async/Await (más legible)
async function getUsers() {
  try {
    const response = await fetch('/api/users');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}
```

---

## 🧩 Destructuring y Spread

```js
// Object destructuring
const { nombre, edad } = persona;
const { nombre: n, edad: e = 18 } = persona; // alias y default

// Array destructuring
const [primero, segundo, ...resto] = [1, 2, 3, 4, 5];

// Spread
const nuevoArray = [...arr1, ...arr2];
const nuevoObj = { ...obj1, extra: 'valor' };
```

---

## 🔗 Siguiente
- [[02 - Fundamentos de Matemáticas]]
