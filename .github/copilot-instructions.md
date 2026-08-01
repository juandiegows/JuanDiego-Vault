# Instrucciones del repo — JuanDiego-Vault

Vault de Obsidian. Notas en `books/` (resúmenes de libros) y `Courses/` (apuntes de
cursos).

## Carpeta `books/`

Regla obligatoria al crear o editar cualquier nota dentro de `books/` (capítulo, Index
o Resumen de un libro): ver **`books/AGENTS.md`** para el detalle completo. Resumen:

1. Antes de escribir, lee `Index`/`Resumen` de los demás libros ya existentes en
   `books/` para conocer sus conceptos.
2. Si el contenido que estás escribiendo explica algo que otro libro ya cubre en un
   capítulo específico, enlázalo con `[[wikilink]]` a ESE capítulo (no al libro
   genérico) en la sección `## 🔗 Notas Relacionadas`.
3. A nivel de capítulo: link simple, sin explicación. A nivel de Index/Resumen: link +
   una frase de por qué se conecta.
4. Si la conexión es real, agrégala también en sentido inverso (el otro capítulo debe
   enlazar de vuelta).
5. Al terminar de agregar los capítulos que faltaban de un libro, revisa si notas de
   otros libros ya existentes deberían actualizarse para enlazar hacia los capítulos
   nuevos.
6. Nunca fuerces conexiones débiles. Nunca borres wikilinks existentes, solo añade.
7. Sintaxis cross-carpeta cuando el nombre de archivo se repite entre libros:
   `[[Carpeta/Nota|Texto a mostrar]]`.

Formato de las notas (frontmatter, callouts, estructura de 3 capas por libro): sigue
el patrón ya usado en cualquier carpeta existente de `books/[Libro]/`.
