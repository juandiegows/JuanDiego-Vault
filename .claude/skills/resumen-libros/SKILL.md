---
name: resumen-libros
description: >
  Crea y mantiene resúmenes de libros en el vault de Obsidian del usuario, siguiendo
  su formato personal ya establecido en la carpeta `books/`. Actívala cuando el usuario
  pida "resumir un libro", "resumen de capítulo", "crea el index de este libro",
  "haz el resumen completo de X", "agrega un capítulo a [libro]", o pegue/adjunte
  contenido de un libro o capítulo pidiendo que se convierta en notas. También úsala
  si el usuario pide actualizar, revisar o conectar un resumen existente con otros
  libros del vault. Siempre genera archivos Markdown con la estructura, callouts de
  Obsidian y wikilinks que el usuario ya usa en sus libros existentes (Hábitos
  Atómicos, Padre Rico Padre Pobre, El Inversor Inteligente, El Hombre Más Rico de
  Babilonia).
---

# Skill: Resumen de Libros (formato del vault)

## Objetivo

Generar notas de libros en Obsidian idénticas en estilo, estructura y profundidad a
las que el usuario ya tiene en `books/`. No es un resumen genérico: es un sistema de
notas interconectadas con 3 capas por libro.

---

## Estructura de carpeta por libro

```
books/[Título del Libro]/
├── Cap 00 - Introducción — [Subtítulo].md
├── Cap 01 - [Título del capítulo].md
├── Cap 02 - ...md
├── Index - [Título del Libro].md   (o Index.md si el libro no tiene homónimos)
└── Resumen - [Título del Libro].md
```

Numeración de capítulo siempre a 2 dígitos (`Cap 00`, `Cap 01`... `Cap 23`). El guion
` - ` separa número de título; un em dash ` — ` puede separar título de subtítulo.

Antes de crear archivos nuevos, revisa si la carpeta del libro ya existe (`Glob` sobre
`books/[Libro]*`) y sigue su convención de nombres exacta (algunos usan
`Index - [Libro].md`, otros solo `Index.md`).

---

## Las 3 capas de contenido

### 1. Nota de capítulo (`Cap NN - Título.md`)

Resume **un capítulo**, con el mayor detalle de conceptos, historias y frameworks del
autor. Frontmatter:

```yaml
---
tags:
  - [tema-general, ej: finanzas, hábitos]
  - [AutorSinEspacios]
  - [conceptos clave del capítulo, 3-6 tags]
---
```

Cuerpo:

```markdown
# Cap NN — Título del Capítulo

> *"Cita textual más memorable del capítulo."*
> — Autor (si aplica)

---

## [emoji] Sección Temática 1

Prosa explicando el concepto. Usa **negritas** en los términos clave.

### Subtítulo si el concepto tiene partes

- Listas para enumerar ideas
- Tablas para comparar categorías (pobre/medio/rico, antes/después, etc.)
- Bloques ` ``` ` para diagramas de flujo tipo `A → B → C → (repite)` o fórmulas

> [!WARNING]/[!IMPORTANT]/[!TIP]/[!NOTE] Callout de Obsidian para la idea que el
> lector debe recordar aunque olvide el resto.

---

## [emoji] Sección Temática 2
...

---

## 🔗 Notas Relacionadas

- [[Index - Título del Libro]]
- [[Cap NN-1 - Título anterior]]
- [[Cap NN+1 - Título siguiente]]
```

Reglas:
- Cada H2 lleva un emoji distinto y temático (no decorativo random — que represente
  el contenido: 🆔 identidad, 🚬 ejemplo de fumadores, 🗳️ hábitos como votos).
- Tablas siempre con formato `|---|---|---|` de 2-4 columnas, nunca más de 5.
- Los diagramas de causa-efecto van en bloques de código plano, no en prosa.
- El cierre siempre enlaza al Index y a capítulos adyacentes (nunca lo omitas).

### 2. Index del libro (`Index - Título.md` o `Index.md`)

Es la portada/mapa del libro. Frontmatter igual que capítulos pero con tags más
generales del libro completo. Cuerpo:

```markdown
# [emoji] Título del Libro — Autor

> *"Frase que resume la tesis del libro."*
> — Autor

---

## 📚 Sobre el Libro

| Dato | Detalle |
|---|---|
| **Autor** | ... |
| **Título original** | ... |
| **Año** | ... |
| **Tema central** | ... |
| **Concepto clave** | ... |

---

## 🗂️ Índice de Capítulos

### [Nombre de la parte/sección si el libro las tiene]
- [[Cap 00 - ...]]
- [[Cap 01 - ...]]
...

---

## 🔑 [Framework o modelo central del libro, si existe]

Tabla o esquema del modelo que estructura todo el libro (ej: las 4 leyes del cambio
de conducta, los 3 patrones financieros).

---

## 💡 Ideas Más Importantes

1. ...
2. ...
(lista numerada de 5 ideas, ordenadas por relevancia, no por orden de aparición)

---

## 🔗 Notas Relacionadas

- [[Otro libro del vault]] — por qué se conectan
```

### 3. Resumen completo (`Resumen - Título.md`)

Es la sintesis ejecutiva del libro completo, pensada para repasar sin releer nada.
Más denso que el Index, con conexiones cross-libro y plan de acción. Frontmatter:

```yaml
---
tags: [temas, autor, resumen-completo, ...]
date: YYYY-MM-DD   # fecha de creación del resumen, no del libro
status: revisado    # o "borrador" si aún no se ha releído
---
```

Cuerpo (orden fijo):

1. `# [emoji] Título — Resumen Completo`
2. `**Autor:** ... | **Año:** ...`
3. Callout `> [!IMPORTANT]` con la frase más importante del libro
4. `## [emoji] La Tesis Central` — 2-3 párrafos de la idea nuclear
5. Sección(es) con el/los framework(s) principales — tablas, diagramas ASCII,
   fórmulas en bloques de código
6. Callouts en secuencia (`[!WARNING]`, `[!TIP]`, etc.) para listas de
   obstáculos/errores/reglas, uno por callout, no todos en un bloque
7. `## Conexiones con el Vault` — wikilinks a otros libros/notas del vault con
   explicación concreta de **por qué** se conectan (nunca un link sin justificación)
8. `## Plan de Acción` — 3-5 callouts `[!SUCCESS]` con acciones concretas y ejecutables
   esta semana, no genéricas ("lee más" no vale; "abre una cuenta separada para
   inversión" sí vale)
9. Opcional: `## Para Ir Más Profundo` — lecturas relacionadas con links reales

---

## Callouts de Obsidian — cuándo usar cada uno

| Callout | Úsalo para |
|---|---|
| `[!IMPORTANT]` | La idea central que no se puede perder |
| `[!WARNING]` | Errores comunes, trampas, patrones destructivos |
| `[!TIP]` | Atajos prácticos, trucos de aplicación |
| `[!SUCCESS]` | Acciones concretas / plan de acción |
| `[!NOTE]` | Datos curiosos o contexto adicional |
| `[!ABSTRACT]` | Principios o leyes numeradas (síntesis de una regla) |
| `[!ADVICE]` | Consejos directos del autor |
| `[!DANGER]` | Riesgos serios si se ignora el consejo |
| `[!CHECK]` | Preguntas de autoevaluación |

---

## Modo portable (.md plano, sin Obsidian)

Úsalo si el usuario dice que no tiene Obsidian instalado, pide "formato .md normal",
"para GitHub", o está trabajando fuera de este vault (otro equipo, otro repo). Mismo
contenido y estructura de 3 capas, pero:

- **Sin `[[wikilinks]]`** → usa markdown estándar: `[Cap 01 - Título](./Cap%2001%20-%20Título.md)`
- **Sin callouts `> [!TIPO]`** → usa blockquote normal `>` o **negrita** para destacar
- **Frontmatter YAML opcional** — solo si el usuario lo pide explícitamente (muchos
  visores .md genéricos no lo ocultan como Obsidian)
- Todo lo demás igual: tablas, bloques de código para diagramas/fórmulas, emojis en
  encabezados, cierre con enlaces a Index y capítulos adyacentes

Si no está claro qué modo usar, pregunta: "¿Obsidian (wikilinks/callouts) o .md plano
portable?" antes de generar el archivo.

---

## Proceso al recibir una solicitud

1. **Identifica qué capa piden**: ¿un capítulo suelto, el Index, el Resumen completo,
   o el libro entero (las 3 capas)?
2. **Busca la carpeta existente** del libro en `books/` antes de crear nada — si ya
   existe, respeta sus nombres de archivo, tags y capítulos previos para mantener
   consistencia (lee al menos un capítulo existente y el Index si están disponibles).
3. **Extrae el contenido real** del libro/capítulo que el usuario dé (texto pegado,
   archivo adjunto, o lo que ya sepas del libro) — no inventes citas ni datos que no
   estén en la fuente. Si no tienes el texto del libro y el usuario solo da el título,
   pregunta si quiere que generes el resumen desde tu conocimiento general del libro
   (dejando claro que no es un resumen capítulo-por-capítulo verificado) o que pegue
   el contenido fuente.
4. **Genera el archivo** con la estructura de la capa correspondiente.
5. **Conecta con el vault**: revisa `books/` (y notas relacionadas si las hay) para
   proponer conexiones reales con otros libros ya resumidos — no fuerces conexiones
   débiles.
6. **Guarda** el archivo en `books/[Título del Libro]/` con el nombre correcto. Si
   creas varios capítulos, actualiza también el Index con los nuevos wikilinks.
