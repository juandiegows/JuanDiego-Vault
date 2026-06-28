---
tags:
  - programación
  - react
  - e-commerce
  - prueba-técnica
  - platzi
---

# 06 — E-commerce Profesional: Prueba Técnica

---

## 🎯 Objetivo

Construir un e-commerce completo con React.js que incluya:
- Listado de productos desde una API
- Carrito de compras funcional
- Navegación entre páginas
- Filtros por categoría y búsqueda

---

## 🏗️ Arquitectura del Proyecto

```
src/
├── components/
│   ├── Layout/
│   ├── ProductCard/
│   ├── ShoppingCart/
│   └── Navbar/
├── pages/
│   ├── Home/
│   ├── ProductDetail/
│   └── Checkout/
├── context/
│   └── ShoppingCartContext.jsx
├── hooks/
│   └── useProducts.js
└── api/
    └── products.js
```

---

## 🛒 Context del Carrito de Compras

```jsx
// context/ShoppingCartContext.jsx
import { createContext, useContext, useState } from 'react';

const ShoppingCartContext = createContext();

export function ShoppingCartProvider({ children }) {
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    const exists = cart.find(item => item.id === product.id);
    if (exists) {
      setCart(cart.map(item =>
        item.id === product.id
          ? { ...item, quantity: item.quantity + 1 }
          : item
      ));
    } else {
      setCart([...cart, { ...product, quantity: 1 }]);
    }
  };

  const removeFromCart = (id) =>
    setCart(cart.filter(item => item.id !== id));

  const total = cart.reduce((sum, item) => sum + item.price * item.quantity, 0);

  return (
    <ShoppingCartContext.Provider value={{ cart, addToCart, removeFromCart, total }}>
      {children}
    </ShoppingCartContext.Provider>
  );
}

export const useShoppingCart = () => useContext(ShoppingCartContext);
```

---

## 🔗 Volver al Índice
- [[Index]]
- [[../../Index|Todos los Cursos]]
