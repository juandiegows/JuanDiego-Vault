---
tags:
  - tecnología
  - ingeniería
  - computación
  - platzi
---

# 01 — Fundamentos de la Ingeniería Informática

---

## 🖥️ ¿Cómo Funciona una Computadora?

```
Entrada → Procesamiento → Salida → Almacenamiento
 (Input)      (CPU)        (Output)  (Storage)
```

**Componentes clave:**
- **CPU** — Unidad Central de Procesamiento (el "cerebro")
- **RAM** — Memoria de acceso rápido y temporal
- **Almacenamiento** — SSD/HDD para datos permanentes
- **GPU** — Procesamiento gráfico (y ahora, IA)
- **Motherboard** — Conecta todos los componentes

---

## 🔢 Sistemas Numéricos

| Sistema | Base | Dígitos | Uso |
|---|---|---|---|
| Decimal | 10 | 0–9 | Uso cotidiano |
| Binario | 2 | 0, 1 | Computadoras (bits) |
| Hexadecimal | 16 | 0–9, A–F | Memoria, colores (#FF5733) |

```
Decimal 255 = Binario 11111111 = Hexadecimal FF

// Conversiones en JS
(255).toString(2)   // "11111111" (decimal → binario)
(255).toString(16)  // "ff" (decimal → hex)
parseInt("ff", 16)  // 255 (hex → decimal)
parseInt("11111111", 2) // 255 (binario → decimal)
```

---

## 💾 Unidades de Almacenamiento

| Unidad | Equivalencia |
|---|---|
| 1 Bit | 0 o 1 |
| 1 Byte | 8 bits |
| 1 KB (Kilobyte) | 1.024 bytes |
| 1 MB (Megabyte) | 1.024 KB |
| 1 GB (Gigabyte) | 1.024 MB |
| 1 TB (Terabyte) | 1.024 GB |

---

## 🌐 Cómo Funciona Internet (Resumen)

Ver detalles en: [[../Programación/DevOps y Redes/02 - Redes Informáticas e Internet]]

```
Tu dispositivo
    ↓
Router / Modem (IP local → IP pública)
    ↓
ISP (Proveedor de Internet)
    ↓
Internet (Red de redes)
    ↓
DNS (nombre de dominio → IP)
    ↓
Servidor web
    ↓
Respuesta viaja de vuelta
```

---

## 🔗 Siguiente
- [[02 - Prompt Engineering]]
