---
tags:
  - redes
  - internet
  - HTTP
  - TCP-IP
  - platzi
---

# 02 — Redes Informáticas e Internet

---

## 🌐 Cómo Funciona Internet

Cuando introduces `platzi.com` en tu navegador:

```
1. DNS Lookup     → Resuelve el dominio a una IP (ej: 192.168.1.100)
2. TCP Handshake  → Establece conexión (SYN → SYN-ACK → ACK)
3. HTTP Request   → El cliente pide el recurso (GET /index.html)
4. HTTP Response  → El servidor responde con el contenido
5. Renderizado    → El navegador procesa HTML/CSS/JS
```

---

## 📡 Modelos de Red

### Modelo TCP/IP (4 capas)
| Capa | Descripción | Protocolos |
|---|---|---|
| **Aplicación** | Lo que usa el usuario | HTTP, HTTPS, FTP, DNS, SMTP |
| **Transporte** | Confiabilidad de la comunicación | TCP, UDP |
| **Internet** | Direccionamiento y ruteo | IP, ICMP |
| **Acceso a red** | Hardware físico | Ethernet, WiFi |

---

## 🔒 HTTP vs HTTPS

| | HTTP | HTTPS |
|---|---|---|
| Puerto | 80 | 443 |
| Cifrado | ❌ No | ✅ TLS/SSL |
| Seguro | ❌ No | ✅ Sí |
| SEO | ⚠️ Penalizado | ✅ Favorecido |

---

## 📊 Códigos de Estado HTTP

| Rango | Significado | Ejemplos |
|---|---|---|
| 2xx | **Éxito** | 200 OK, 201 Created, 204 No Content |
| 3xx | **Redirección** | 301 Moved, 304 Not Modified |
| 4xx | **Error del cliente** | 400 Bad Request, 401 Unauthorized, 404 Not Found |
| 5xx | **Error del servidor** | 500 Internal Error, 503 Service Unavailable |

---

## 🔗 Siguiente
- [[03 - Fundamentos de Criptografía]]
