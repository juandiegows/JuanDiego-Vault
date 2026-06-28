---
tags:
  - criptografía
  - seguridad
  - platzi
  - cifrado
---

# 03 — Fundamentos de Criptografía

---

## 🔐 ¿Qué es la Criptografía?

La criptografía es la ciencia de proteger información mediante transformaciones matemáticas, haciéndola ilegible para personas no autorizadas.

---

## 🔑 Tipos de Cifrado

### Simétrico
Una **misma clave** para cifrar y descifrar.

```
Mensaje + Clave → Cifrado → Clave → Mensaje original
```

- **Ventaja:** Muy rápido
- **Desventaja:** ¿Cómo compartes la clave de forma segura?
- **Algoritmos:** AES, DES, 3DES

### Asimétrico (Llave pública/privada)
**Dos claves** relacionadas matemáticamente:
- **Pública:** Cualquiera puede cifrar con ella
- **Privada:** Solo tú puedes descifrar

```
Mensaje + Clave Pública → Cifrado → Clave Privada → Mensaje original
```

- **Ventaja:** No necesitas compartir la clave privada
- **Desventaja:** Más lento que simétrico
- **Algoritmos:** RSA, ECC
- **Usado en:** HTTPS, SSH, firmas digitales

---

## 🔏 Hashing

El hash convierte datos de cualquier tamaño en un valor de tamaño fijo. Es **unidireccional** (no se puede revertir).

| Algoritmo | Output | Uso |
|---|---|---|
| MD5 | 128 bits | ⚠️ Solo verificación de integridad (inseguro para contraseñas) |
| SHA-256 | 256 bits | ✅ Integridad, blockchain, contraseñas (con salt) |
| bcrypt | Variable | ✅ Contraseñas (diseñado para ser lento) |
| Argon2 | Variable | ✅ Estándar moderno para contraseñas |

```js
// En Node.js con bcrypt
import bcrypt from 'bcrypt';

const hash = await bcrypt.hash('mi-contraseña', 10); // 10 = salt rounds
const valida = await bcrypt.compare('mi-contraseña', hash); // true
```

---

## 🌐 HTTPS y TLS

TLS (Transport Layer Security) usa una combinación de:
1. **Asimétrico** — Para intercambiar la clave de sesión
2. **Simétrico** — Para cifrar la comunicación real (más rápido)

```
Cliente          Servidor
   |  ClientHello  |
   |←──────────────|
   |  ServerHello + Certificado
   |──────────────→|
   |  Verificar cert con CA
   |  Generar clave de sesión
   |←──────────────|
   |  Comunicación cifrada (AES)
```

---

## 🔗 Volver al Índice
- [[Index]]
- [[../../Index|Todos los Cursos]]
