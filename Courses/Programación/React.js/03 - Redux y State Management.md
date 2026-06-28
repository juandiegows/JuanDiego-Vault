---
tags:
  - programación
  - react
  - redux
  - platzi
  - estado-global
---

# 03 — Redux y State Management

---

## 🤔 ¿Cuándo Usar Estado Global?

Usa estado global cuando:
- Múltiples componentes **no relacionados** necesitan los mismos datos
- La prop drilling llega a 3+ niveles de profundidad
- Datos que cambian frecuentemente (carrito, usuario autenticado)

---

## 🔄 El Flujo de Redux

```
UI → dispatch(action) → reducer → nuevo estado → UI se actualiza
```

**3 Principios:**
1. **Una sola fuente de verdad** — un solo store
2. **Estado de solo lectura** — solo actions pueden cambiarlo
3. **Cambios con funciones puras** — reducers sin efectos secundarios

---

## 📦 Redux Toolkit (Moderno)

```bash
npm install @reduxjs/toolkit react-redux
```

```jsx
// store/counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: state => { state.value += 1; },
    decrement: state => { state.value -= 1; },
    reset:     state => { state.value = 0; },
  }
});

export const { increment, decrement, reset } = counterSlice.actions;
export default counterSlice.reducer;

// store/index.js
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

export const store = configureStore({
  reducer: { counter: counterReducer }
});

// Uso en componente
import { useSelector, useDispatch } from 'react-redux';
import { increment } from './store/counterSlice';

function Counter() {
  const count = useSelector(state => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <span>{count}</span>
      <button onClick={() => dispatch(increment())}>+</button>
    </div>
  );
}
```

---

## ⚡ Alternativas a Redux

| Herramienta | Cuándo usarla |
|---|---|
| **Context API** | Estado simple, pocas actualizaciones |
| **Zustand** | Más simple que Redux, mismo poder |
| **Jotai / Recoil** | Estado atómico, granular |
| **Redux Toolkit** | Apps grandes y complejas |

---

## 🔗 Siguiente
- [[04 - State Machines en React]]
