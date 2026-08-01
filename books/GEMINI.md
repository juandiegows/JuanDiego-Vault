# books/ — instrucciones para Gemini

Al trabajar dentro de `books/`, sigue la regla obligatoria de interconexión entre
notas de libros definida en **`books/AGENTS.md`** (fuente canónica). Este archivo
duplica el resumen para que Gemini CLI lo cargue sin depender de imports entre
archivos.

Regla (ver `AGENTS.md` para el detalle completo):

1. Antes de escribir, lee `Index`/`Resumen` de los demás libros en `books/` para saber
   qué conceptos cubren.
2. Cuando un capítulo/Index/Resumen explique algo que otro libro ya cubre en un
   capítulo concreto, enlázalo con `[[wikilink]]` a ESE capítulo, no al libro genérico.
3. Capítulo → link simple en `## 🔗 Notas Relacionadas`. Index/Resumen → link con una
   frase de por qué se conecta.
4. Haz el link recíproco cuando la conexión sea real (A→B implica revisar B→A).
5. Al completar los capítulos faltantes de un libro, revisa si notas de otros libros ya
   existentes deberían enlazar hacia los capítulos nuevos.
6. Nunca fuerces conexiones débiles. Nunca borres links existentes, solo añade.
7. Sintaxis cross-carpeta cuando el nombre se repite entre libros:
   `[[Carpeta/Nota|Texto a mostrar]]`.
