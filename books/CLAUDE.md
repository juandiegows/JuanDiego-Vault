# books/ — instrucciones para Claude

Al trabajar dentro de `books/`, sigue **`books/AGENTS.md`** (regla obligatoria de
interconexión entre notas de libros) además de la skill `resumen-libros` para formato
y estructura. `AGENTS.md` es la fuente canónica — este archivo solo la referencia para
que Claude Code la cargue automáticamente al entrar a esta carpeta.

Resumen de la regla (ver `AGENTS.md` para el detalle completo):

1. Antes de escribir, lee `Index`/`Resumen` de los demás libros en `books/` para saber
   qué conceptos cubren.
2. Cuando un capítulo/Index/Resumen explique algo que otro libro ya cubre en un
   capítulo concreto, enlázalo con `[[wikilink]]` a ESE capítulo, no al libro genérico.
3. Capítulo → link simple en `## 🔗 Notas Relacionadas`. Index/Resumen → link con una
   frase de por qué.
4. Haz el link recíproco cuando la conexión sea real.
5. Al completar los capítulos faltantes de un libro, revisa si notas de otros libros ya
   existentes deberían enlazar hacia los capítulos nuevos.
6. Nunca fuerces conexiones débiles. Nunca borres links existentes.
