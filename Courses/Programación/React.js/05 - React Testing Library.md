---
tags:
  - programación
  - react
  - testing
  - RTL
  - platzi
---

# 05 — React Testing Library

---

## 🎯 Filosofía de RTL

> "Escribe tests que se asemejen a cómo el usuario usa tu software."

RTL testea el **comportamiento**, no la implementación. No importa cómo está construido el componente — importa lo que el usuario ve y puede hacer.

---

## 📦 Instalación

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom @testing-library/user-event
```

---

## 🧪 Estructura de un Test

```jsx
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Contador from './Contador';

describe('Componente Contador', () => {
  test('muestra el valor inicial en 0', () => {
    render(<Contador />);
    expect(screen.getByText('Contador: 0')).toBeInTheDocument();
  });

  test('incrementa al hacer click en el botón', async () => {
    const user = userEvent.setup();
    render(<Contador />);

    await user.click(screen.getByRole('button', { name: '+1' }));

    expect(screen.getByText('Contador: 1')).toBeInTheDocument();
  });
});
```

---

## 🔍 Queries — Cómo Encontrar Elementos

**Prioridad recomendada (de mejor a peor):**

| Query | Cuándo usarla |
|---|---|
| `getByRole` | Botones, inputs, links, headings (**preferida**) |
| `getByLabelText` | Inputs con label asociado |
| `getByPlaceholderText` | Inputs con placeholder |
| `getByText` | Elementos con texto visible |
| `getByTestId` | Último recurso (agrega data-testid) |

---

## 🔗 Siguiente
- [[06 - E-commerce Profesional (Prueba Técnica)]]
