---
tags:
  - programación
  - react
  - platzi
  - componentes
  - hooks
---

# 01 — Fundamentos de React.js

---

## 🧩 ¿Qué es React?

React es una **biblioteca de JavaScript** para construir interfaces de usuario. Desarrollada por Meta (Facebook).

**Características clave:**
- Basado en **componentes** reutilizables
- **Virtual DOM** para actualizaciones eficientes
- **Unidireccionalidad de datos** (padre → hijo)
- Ecosistema enorme de librerías

---

## 📦 Crear un Proyecto

```bash
# Con Vite (recomendado)
npm create vite@latest mi-app -- --template react
cd mi-app
npm install
npm run dev

# Con Create React App (legacy)
npx create-react-app mi-app
```

---

## 🧱 Anatomía de un Componente

```jsx
// Componente funcional (moderno)
function Saludo({ nombre }) {
  return (
    <div>
      <h1>Hola, {nombre}!</h1>
    </div>
  );
}

// Uso
<Saludo nombre="Juan Diego" />
```

---

## 🪝 Hooks Fundamentales

### useState — Estado local

```jsx
import { useState } from 'react';

function Contador() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>+1</button>
    </div>
  );
}
```

### useEffect — Efectos secundarios

```jsx
import { useState, useEffect } from 'react';

function DatosAPI() {
  const [datos, setDatos] = useState([]);

  useEffect(() => {
    // Se ejecuta después del render
    fetch('/api/datos')
      .then(r => r.json())
      .then(data => setDatos(data));
  }, []); // [] = solo al montar

  return <ul>{datos.map(d => <li key={d.id}>{d.name}</li>)}</ul>;
}
```

---

## 📋 Props vs State

| | Props | State |
|---|---|---|
| ¿Quién lo controla? | El padre | El propio componente |
| ¿Se puede modificar? | No (solo lectura) | Sí (con setter) |
| ¿Cuándo cambia? | Cuando el padre re-renderiza | Cuando se llama al setter |
| Uso típico | Pasar datos hacia abajo | Datos que cambian con interacción |

---

## 🔗 Siguiente
- [[02 - React Router — Navegación]]
