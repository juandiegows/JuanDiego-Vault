---
tags:
  - javascript
  - matemáticas
  - platzi
  - programación
---

# 02 — Fundamentos de Matemáticas para Programación

> Fuente: [platzi.com/cursos/fundamentos-matematicas](https://platzi.com/cursos/fundamentos-matematicas)

---

## 🔢 Números y Operaciones en JS

```js
// Operaciones básicas
10 + 3   // 13
10 - 3   // 7
10 * 3   // 30
10 / 3   // 3.333...
10 % 3   // 1 (módulo / residuo)
10 ** 3  // 1000 (potencia)

// Math object
Math.round(3.7)  // 4
Math.floor(3.9)  // 3 (hacia abajo)
Math.ceil(3.1)   // 4 (hacia arriba)
Math.abs(-5)     // 5 (valor absoluto)
Math.sqrt(25)    // 5 (raíz cuadrada)
Math.pow(2, 10)  // 1024
Math.max(1,5,3)  // 5
Math.min(1,5,3)  // 1
Math.random()    // 0 a 0.999...
```

---

## 📊 Álgebra Básica en Código

```js
// Ecuación lineal: y = mx + b
const pendiente = 2;
const intercepto = 3;
const x = 5;
const y = pendiente * x + intercepto; // 13

// Porcentajes
const precio = 100;
const descuento = 0.15; // 15%
const precioFinal = precio * (1 - descuento); // 85

// Interés compuesto
const capital = 10000;
const tasa = 0.07; // 7% anual
const años = 10;
const resultado = capital * Math.pow(1 + tasa, años); // 19671.51
```

---

## 🔄 Recursividad

```js
// Factorial: n! = n * (n-1) * ... * 1
function factorial(n) {
  if (n === 0 || n === 1) return 1; // caso base
  return n * factorial(n - 1);      // caso recursivo
}
factorial(5); // 120

// Fibonacci
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
fibonacci(8); // 21
```

---

## 🔗 Volver al Índice
- [[Index]]
- [[../../Index|Todos los Cursos]]
