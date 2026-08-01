---
name: apuntes-cursos
description: >
  Crea y mantiene apuntes de cursos (Platzi, Udemy, etc.) en el vault de Obsidian del
  usuario, siguiendo su formato personal ya establecido en la carpeta `Courses/`.
  Actívala cuando el usuario pida "apuntes de este curso", "resume esta clase/módulo",
  "crea el index de este curso", "agrega una clase a [curso]", o pegue/adjunte
  transcripción o contenido de una clase/video pidiendo que se convierta en notas.
  También úsala si el usuario pide crear una categoría nueva de cursos o conectar un
  curso con los libros/otros cursos del vault. Distinta de `resumen-libros`: los
  cursos usan notas de módulo más cortas y prácticas (sin cita de apertura, cierre
  con solo "Siguiente"), organizadas por categoría → curso → módulos.
---

# Skill: Apuntes de Cursos (formato del vault)

## Objetivo

Generar notas de cursos en Obsidian idénticas en estilo y estructura a las que el
usuario ya tiene en `Courses/`. Más cortas y accionables que los resúmenes de libros:
cada módulo es una clase o video, no un capítulo largo.

---

## Jerarquía de carpetas

```
Courses/
├── Index.md                                    (catálogo general, categorías)
├── [Categoría]/                                (ej: Finanzas, Programación, Inglés)
│   ├── Index.md                                (lista de cursos de la categoría)
│   └── [Nombre del Curso]/
│       ├── 01 - Título del módulo.md
│       ├── 02 - Título del módulo.md
│       └── Index.md                            (portada del curso)
```

Nota: en "Finanzas/Aprende a Invertir en Bolsa" los módulos se llaman `Video NN - ...`
en vez de solo `NN - ...` porque el curso está organizado por video. Sigue la
convención que ya usa el curso existente; si es curso nuevo, usa `NN - Título.md`
por defecto salvo que el usuario indique que el curso está dividido en videos.

Antes de crear nada, `Glob` sobre `Courses/[Categoría]*` para ver si la categoría y
el curso ya existen y respetar nombres/tags previos.

---

## 1. Nota de módulo/clase (`NN - Título.md`)

Frontmatter:

```yaml
---
tags:
  - [categoría, ej: ciberseguridad, finanzas]
  - [plataforma si aplica: platzi, udemy]
  - [2-4 tags de conceptos específicos del módulo]
---
```

Cuerpo:

```markdown
# NN — Título del Módulo

---

## [emoji] Sección Temática 1

Prosa breve y directa — sin cita de apertura (a diferencia de los capítulos de
libros). Va directo al concepto.

- Listas para pasos o comandos
- Tablas para comparar opciones, comandos o criterios

### Subtítulo si aplica (ej: "Comandos principales")

| Comando/Término | Descripción | Ejemplo |
|---|---|---|
| ... | ... | ... |

---

## [emoji] Sección Temática 2
...

---

## 🔑 Regla de Oro / Idea Clave (opcional, si el módulo tiene una síntesis clara)

> Frase que resume el punto práctico del módulo.

---

## 🔗 Siguiente
- [[NN+1 - Título del siguiente módulo]]
```

Reglas:
- **No lleva cita de apertura** ni "Notas Relacionadas" con Index — solo enlaza al
  **siguiente** módulo (el último módulo del curso no lleva esta sección, o enlaza
  de vuelta al Index del curso).
- Prioriza tablas de comandos/sintaxis/criterios sobre prosa larga — los cursos
  técnicos y prácticos se resumen en referencias rápidas, no en ensayos.
- Tono práctico: qué es, cómo se usa, ejemplo. No profundizar en teoría más allá de
  lo necesario para aplicar.

---

## 2. Index del curso (`[Curso]/Index.md`)

```yaml
---
tags:
  - [categoría]
  - [plataforma]
  - [tema del curso]
---
```

```markdown
# [emoji] Nombre del Curso

> Fuente: [Plataforma — Nombre del curso](url si se conoce, si no omite la línea)
> Estado: ✅ Cerrado / 🔄 En progreso

---

## 📚 Archivos del Curso

- [[01 - Título del módulo]]
- [[02 - Título del módulo]]
...

---

## 💡 Idea Central

1-2 frases con el concepto que atraviesa todo el curso.

> "Frase memorable del curso, si existe."

---

## 🔑 Conceptos Clave

| Concepto | Descripción |
|---|---|
| ... | ... |
```

`Estado` usa siempre ✅ Cerrado o 🔄 En progreso — pregunta al usuario si no es obvio
por el contexto (ej. si solo pegó 2 de 10 módulos, es 🔄).

---

## 3. Index de categoría (`[Categoría]/Index.md`)

Cuando la categoría tiene más de un curso:

```markdown
# [emoji] Cursos de [Categoría]

---

## 📚 Cursos

- [[[Curso 1]/Index|Nombre del Curso 1]]
- [[[Curso 2]/Index|Nombre del Curso 2]]

---

## 🔗 Notas Relacionadas

- [[../../books/[Libro relacionado]/Index|Libro relacionado]]  — solo si hay conexión temática real
- [[../Index|Todos los Cursos]]
```

Usa el formato de wikilink con alias `[[ruta|Texto a mostrar]]` cuando el link cruza
carpetas, igual que en `Courses/Finanzas/Index.md`.

---

## 4. Index general (`Courses/Index.md`)

Solo se edita cuando se agrega una **categoría nueva** (no un curso o módulo dentro
de una categoría existente). Actualiza dos partes:

1. La sección `## 📂 Categorías` — agrega bloque `### [emoji] [[Categoría/Index|Categoría]]` con descripción de 1 línea y link "Ver cursos →".
2. La tabla `## 📊 Resumen de Cursos` — agrega fila con categoría, número de cursos y estado.

---

## Callouts

Los apuntes de curso usan callouts con más moderación que los libros — principalmente
para comandos peligrosos o advertencias de seguridad (relevante en Ciberseguridad):

| Callout | Úsalo para |
|---|---|
| `[!WARNING]` | Riesgos legales/técnicos (ej: usar dorks solo en objetivos autorizados) |
| `[!TIP]` | Atajos o buenas prácticas |
| `[!NOTE]` | Contexto adicional no esencial |

No fuerces callouts si el módulo es puramente una tabla de referencia (ej. lista de
comandos) — ahí la tabla sola es suficiente.

---

## Modo portable (.md plano, sin Obsidian)

Úsalo si el usuario dice que no tiene Obsidian instalado, pide "formato .md normal",
"para GitHub", o trabaja fuera de este vault (otro equipo, otro repo). Misma jerarquía
categoría → curso → módulos, pero:

- **Sin `[[wikilinks]]`** → usa markdown estándar: `[02 - Título](./02%20-%20Título.md)`
- **Sin callouts `> [!TIPO]`** → blockquote normal `>` o **negrita**
- **Sin alias de wikilink** (`[[ruta|Texto]]`) en los Index de categoría → usa
  `[Texto](./ruta.md)` normal
- Frontmatter YAML opcional, solo si el usuario lo pide explícitamente

Si no está claro qué modo usar, pregunta antes de generar el archivo.

---

## Proceso al recibir una solicitud

1. **Identifica la categoría y el curso** — si no existen, pregunta el nombre de la
   categoría (o infiere de una lista existente en `Courses/Index.md`) antes de crear
   carpetas nuevas.
2. **Busca el curso/categoría existente** con `Glob`/`Grep` y respeta numeración,
   nombres de archivo (`NN -` vs `Video NN -`) y tags ya usados.
3. **Extrae el contenido real** de la clase/video que el usuario dé (transcripción,
   texto pegado, o resumen que dicte) — no inventes comandos, cifras o datos técnicos
   que no estén en la fuente. Si el módulo es de seguridad/hacking, mantén el marco
   ético del curso existente (pentesting autorizado, sin instrucciones de daño real).
4. **Genera el archivo de módulo** siguiendo la plantilla de la sección 1.
5. **Actualiza el Index del curso** agregando el wikilink del nuevo módulo en
   "📚 Archivos del Curso" y, si corresponde, el "🔗 Siguiente" del módulo anterior.
6. **Si es curso o categoría nueva**, crea también su Index siguiendo las secciones
   2-4 y enlázalo desde el nivel superior correspondiente.
