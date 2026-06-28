---
tags:
  - programación
  - react
  - state-machines
  - xstate
  - platzi
---

# 04 — State Machines en React

> Fuente: [platzi.github.io/react-state-machines](https://platzi.github.io/react-state-machines/)

---

## 🤔 ¿Qué es una Máquina de Estados?

Una máquina de estados finita (FSM) define:
- Un conjunto finito de **estados**
- Las **transiciones** entre ellos
- Los **eventos** que las disparan

**Problema que resuelve:** El estado booleano explosivo.

```jsx
// ❌ Sin máquina de estados — difícil de mantener
const [isLoading, setIsLoading] = useState(false);
const [isError, setIsError] = useState(false);
const [isSuccess, setIsSuccess] = useState(false);
// ¿Qué pasa si isLoading y isError son true al mismo tiempo?

// ✅ Con máquina de estados — imposible tener estados inválidos
type Status = 'idle' | 'loading' | 'success' | 'error';
const [status, setStatus] = useState<Status>('idle');
```

---

## 📊 Diagrama de una Máquina Simple

```
    [idle]
      ↓ FETCH
   [loading]
    ↙     ↘
[error]  [success]
   ↓         ↓
 RETRY     RESET
   ↓         ↓
[loading]  [idle]
```

---

## 🔧 useReducer como Máquina de Estados

```jsx
const initialState = { status: 'idle', data: null, error: null };

function reducer(state, event) {
  switch (state.status) {
    case 'idle':
      if (event.type === 'FETCH') return { ...state, status: 'loading' };
      break;
    case 'loading':
      if (event.type === 'SUCCESS') return { status: 'success', data: event.data, error: null };
      if (event.type === 'ERROR')   return { status: 'error', data: null, error: event.error };
      break;
    case 'error':
      if (event.type === 'RETRY') return { ...state, status: 'loading' };
      break;
    case 'success':
      if (event.type === 'RESET') return initialState;
      break;
  }
  return state; // Estado inválido — no hace nada
}

function FetchComponent() {
  const [state, dispatch] = useReducer(reducer, initialState);

  const fetchData = async () => {
    dispatch({ type: 'FETCH' });
    try {
      const data = await api.getData();
      dispatch({ type: 'SUCCESS', data });
    } catch (error) {
      dispatch({ type: 'ERROR', error: error.message });
    }
  };

  if (state.status === 'loading') return <Spinner />;
  if (state.status === 'error')   return <Error message={state.error} onRetry={() => dispatch({ type: 'RETRY' })} />;
  if (state.status === 'success') return <Data data={state.data} />;
  return <button onClick={fetchData}>Cargar</button>;
}
```

---

## 🔗 Siguiente
- [[05 - React Testing Library]]
