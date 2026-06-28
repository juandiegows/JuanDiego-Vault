---
tags:
  - nextjs
  - react
  - platzi
  - server-components
  - app-router
---

# 02 — App Router y Server Components

---

## 🏗️ Layout Compartidos

```tsx
// app/layout.tsx — aplica a todas las páginas
export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="es">
      <body>
        <Navbar />
        <main>{children}</main>
        <Footer />
      </body>
    </html>
  );
}

// app/dashboard/layout.tsx — layout anidado
export default function DashboardLayout({ children }) {
  return (
    <div>
      <Sidebar />
      <div>{children}</div>
    </div>
  );
}
```

---

## 🔌 API Routes

```ts
// app/api/users/route.ts
import { NextRequest, NextResponse } from 'next/server';

export async function GET(request: NextRequest) {
  const users = await db.getUsers();
  return NextResponse.json(users);
}

export async function POST(request: NextRequest) {
  const body = await request.json();
  const user = await db.createUser(body);
  return NextResponse.json(user, { status: 201 });
}
```

---

## ⚡ Optimizaciones de Next.js

```tsx
// Imagen optimizada automáticamente
import Image from 'next/image';

<Image
  src="/hero.jpg"
  alt="Hero"
  width={1200}
  height={600}
  priority    // carga prioritaria (above the fold)
/>

// Link con prefetch automático
import Link from 'next/link';
<Link href="/about">Acerca de</Link>

// Metadata (SEO)
export const metadata = {
  title: 'Mi App',
  description: 'Descripción de mi app',
  openGraph: { title: 'Mi App' }
};
```

---

## 🔗 Volver al Índice
- [[Index]]
- [[../../Index|Todos los Cursos]]
