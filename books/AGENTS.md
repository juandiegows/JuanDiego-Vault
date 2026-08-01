# Instrucciones para IAs — carpeta `books/`

Este archivo aplica a cualquier IA que edite o genere notas dentro de `books/`
(Claude Code, GitHub Copilot, Gemini CLI, u otra). Es la fuente canónica de la regla;
`CLAUDE.md` y `GEMINI.md` en esta misma carpeta duplican su contenido para que cada
herramienta lo lea sin depender de imports.

Formato base de las notas: ver skill `resumen-libros` (si la IA la tiene disponible) o,
si no, seguir la estructura ya existente en cualquier carpeta de `books/[Libro]/`
(frontmatter, callouts `[!TIPO]`, wikilinks `[[...]]`, cierre con `## 🔗 Notas
Relacionadas`).

---

## Regla obligatoria: interconexión entre libros

**Nunca generes o edites una nota de `books/` como si fuera aislada.** Cada libro en
este vault vive en conversación con los demás — mismos temas (finanzas, hábitos,
comportamiento) desde ángulos distintos. La regla existe para no tener que repetir
después un barrido masivo de cross-linking sobre todo `books/` (ya se hizo una vez
manualmente; el objetivo es que no vuelva a hacer falta).

### Cuándo aplica

Cada vez que:
- Se crea un capítulo nuevo (`Cap NN - ...md`).
- Se crea o edita un `Index` o `Resumen` de un libro.
- Se termina de resumir un libro completo o se le agregan los capítulos que faltaban.

### Proceso

1. **Antes de escribir contenido nuevo**, lee el `Index` y/o `Resumen` de los demás
   libros ya existentes en `books/` (Glob `books/*/Index*.md` y `books/*/Resumen*.md`)
   para tener el mapa de conceptos de cada uno. No hace falta leer todos los capítulos,
   pero sí saber qué cubre cada libro.
2. **Mientras escribes el capítulo/Index/Resumen**, si el contenido explica un concepto
   que otro libro ya cubre en un capítulo específico, identifica ESE capítulo exacto
   (no solo "el libro" en general).
3. **Agrega el wikilink** en la sección `## 🔗 Notas Relacionadas`:
   - A nivel de **capítulo**: solo el link, en lista simple, sin explicación inline
     (mismo estilo que los links a capítulos adyacentes).
   - A nivel de **Index/Resumen**: cada link lleva una frase corta explicando el
     **por qué** de la conexión (no un link suelto sin contexto).
4. **Haz el link recíproco cuando la conexión sea genuina**: si agregas
   `Libro A Cap X → Libro B Cap Y`, abre `Libro B Cap Y` y agrega el link de vuelta si
   todavía no existe. Una conexión real casi siempre es de ida y vuelta.
5. **Revisa hacia atrás**: si acabas de terminar los capítulos que faltaban de un libro
   (ej. estabas en 17/20 y ahora está completo), revisa si capítulos de OTROS libros ya
   existentes deberían actualizarse para enlazar hacia los capítulos nuevos que acabas
   de crear. No dejes esa conexión pendiente para "después".
6. **Nunca fuerces una conexión débil.** Cero conexión es mejor que una conexión
   trivial o forzada solo para "cumplir cuota". Calidad sobre cobertura.
7. **Nunca borres links existentes** al editar una nota — solo añade.
8. **Sintaxis cross-carpeta**: cuando el nombre de archivo se repite entre libros (ej.
   varios `Index.md`), usa `[[Carpeta/Nota|Texto a mostrar]]` para que el link resuelva
   al archivo correcto y se lea con un título claro. Ejemplo:
   `[[Hábitos Atómicos/Index|Hábitos Atómicos]]`.

### Libros actualmente en el vault (julio 2026)

- `El Inversor Inteligente` (Benjamin Graham) — incluye subcarpeta `Docs/` con notas de
  concepto (Diversificación, Margen de Seguridad, etc.) también sujetas a esta regla.
- `El hombre más ricos de babilonia` (George Clason)
- `Hábitos Atómicos` (James Clear)
- `Padre Rico Padre Pobre` (Robert Kiyosaki)
- `La Psicología del Dinero` (Morgan Housel)

Actualiza esta lista cuando se agregue un libro nuevo a `books/`.

### Verificación antes de terminar

- Todo `[[wikilink]]` nuevo debe apuntar a un archivo real que existe en `books/`
  (verifica con Glob si no estás seguro del nombre exacto).
- No repitas el mismo link dos veces en la misma sección.
