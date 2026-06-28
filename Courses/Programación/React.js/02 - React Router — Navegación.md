---
tags:
  - programación
  - react
  - react-router
  - platzi
  - SPA
---

# 02 — React Router: Navegación en SPAs

---

## 📦 Instalación

```bash
npm install react-router-dom
```

---

## 🗺️ Configuración Básica

```jsx
// main.jsx
import { BrowserRouter } from 'react-router-dom';

ReactDOM.createRoot(document.getElementById('root')).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);

// App.jsx
import { Routes, Route } from 'react-router-dom';

function App() {
  return (
    <Routes>
      <Route path="/"        element={<Home />} />
      <Route path="/about"   element={<About />} />
      <Route path="/product/:id" element={<Product />} />
      <Route path="*"        element={<NotFound />} />
    </Routes>
  );
}
```

---

## 🔗 Links y Navegación

```jsx
import { Link, NavLink, useNavigate } from 'react-router-dom';

// Link — navegación declarativa
<Link to="/about">Acerca de</Link>

// NavLink — agrega clase "active" automáticamente
<NavLink to="/home" style={({ isActive }) => ({
  color: isActive ? 'red' : 'black'
})}>Home</NavLink>

// useNavigate — navegación programática
const navigate = useNavigate();
navigate('/dashboard');      // navegar
navigate(-1);                // volver atrás
```

---

## 🔧 Parámetros de URL

```jsx
import { useParams, useSearchParams } from 'react-router-dom';

// Parámetros de ruta: /product/:id
function Product() {
  const { id } = useParams();
  return <h1>Producto #{id}</h1>;
}

// Query params: /search?q=react&page=2
function Search() {
  const [searchParams] = useSearchParams();
  const query = searchParams.get('q');
  return <h1>Buscando: {query}</h1>;
}
```

---

## 🔗 Siguiente
- [[03 - Redux y State Management]]
