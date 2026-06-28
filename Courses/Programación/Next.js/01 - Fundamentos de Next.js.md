---
tags:
  - nextjs
  - react
  - platzi
  - SSR
  - routing
---

# 01 — Fundamentos de Next.js

---

## 📦 Crear un Proyecto

```bash
npx create-next-app@latest mi-app
cd mi-app
npm run dev  # localhost:3000
```

---

## 🗂️ Estructura con App Router (Next.js 13+)

```
app/
├── layout.tsx        ← Layout raíz (siempre)
├── page.tsx          ← Ruta "/"
├── about/
│   └── page.tsx      ← Ruta "/about"
├── blog/
│   ├── page.tsx      ← Ruta "/blog"
│   └── [slug]/
│       └── page.tsx  ← Ruta "/blog/:slug" (dinámica)
└── api/
    └── users/
        └── route.ts  ← API endpoint "/api/users"
```

---

## 🖥️ Server vs Client Components

```tsx
// Por defecto: Server Component (renderiza en el servidor)
// Sin "use client" → Server Component
async function ProductPage({ params }: { params: { id: string } }) {
  const product = await fetch(`/api/products/${params.id}`).then(r => r.json());
  return <h1>{product.name}</h1>;
}

// "use client" → Client Component (interactividad)
'use client';
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(c => c + 1)}>{count}</button>;
}
```

---

## 🌐 Estrategias de Renderizado

```tsx
// SSG — Static Site Generation (build time)
// Por defecto para rutas sin datos dinámicos

// SSR — Server-Side Rendering (cada request)
export const dynamic = 'force-dynamic';

// ISR — Incremental Static Regeneration
export const revalidate = 60; // revalida cada 60 segundos

// Fetch con caché controlada
const data = await fetch('/api/data', {
  next: { revalidate: 3600 } // 1 hora
});
```

---

## 🔗 Siguiente
- [[02 - App Router y Server Components]]
