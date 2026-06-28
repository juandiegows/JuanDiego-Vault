---
tags:
  - videojuegos
  - game-maker
  - GML
  - platzi
  - desarrollo
---

# 02 — Game Maker Studio 2: Introducción a Creación de Videojuegos

---

## 🎮 ¿Qué es Game Maker Studio 2?

Game Maker Studio 2 (GMS2) es un motor de videojuegos 2D desarrollado por YoYo Games. Usa GML (Game Maker Language) o drag-and-drop visual.

**Usado en:** Undertale, Hotline Miami, Hyper Light Drifter, Spelunky original.

---

## 🏗️ Arquitectura de GMS2

```
Proyecto GMS2
├── Sprites    → Imágenes y animaciones
├── Objects    → Entidades con comportamiento (código)
├── Rooms      → Niveles / escenas del juego
├── Sounds     → Efectos de sonido y música
├── Fonts      → Tipografías
└── Scripts    → Funciones reutilizables
```

---

## 💻 GML Básico

```gml
// Create Event (se ejecuta al crear el objeto)
speed = 0;
hsp = 0; // velocidad horizontal
vsp = 0; // velocidad vertical
grv = 0.5; // gravedad

// Step Event (se ejecuta cada frame)
// Input
hsp = (keyboard_check(vk_right) - keyboard_check(vk_left)) * 4;

// Gravedad
vsp += grv;
if vsp > 10 vsp = 10; // velocidad máxima de caída

// Colisiones
if place_meeting(x, y+vsp, obj_wall) {
    while !place_meeting(x, y+sign(vsp), obj_wall) {
        y += sign(vsp);
    }
    vsp = 0;
}

// Mover
x += hsp;
y += vsp;
```

---

## 🔑 Conceptos Clave

| Concepto | Descripción |
|---|---|
| **Room** | El nivel/escena donde ocurre el juego |
| **Object** | Entidad con sprites y eventos (Player, Enemy, etc.) |
| **Instance** | Una copia específica de un Object en el Room |
| **Sprite** | La imagen visual del Object |
| **Event** | Cuándo se ejecuta el código (Create, Step, Draw, Collision...) |
| **Variable** | Dato guardado en el objeto |

---

## 🔗 Volver al Índice
- [[Index]]
- [[../Index|Todos los Cursos]]
