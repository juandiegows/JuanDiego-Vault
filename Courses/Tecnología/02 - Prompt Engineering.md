---
tags:
  - tecnología
  - IA
  - prompt-engineering
  - platzi
  - LLM
---

# 02 — Prompt Engineering

---

## 🤖 ¿Qué es Prompt Engineering?

Es el arte y la ciencia de **diseñar instrucciones efectivas** para los modelos de lenguaje (LLMs) con el fin de obtener los mejores resultados posibles.

---

## 🏗️ Estructura de un Buen Prompt

```
[ROL] + [CONTEXTO] + [TAREA] + [FORMATO] + [RESTRICCIONES]
```

**Ejemplo básico:**
```
❌ Malo: "Explícame React"

✅ Bueno: "Eres un instructor senior de frontend. 
Explícame el concepto de useEffect en React para alguien 
que ya sabe JavaScript pero es nuevo en React.
Usa un ejemplo práctico con código y explica cuándo usarlo 
y cuándo NO usarlo. Responde en español."
```

---

## 🎯 Técnicas Clave

### Zero-shot Prompting
Sin ejemplos previos. Solo la instrucción.
```
"Clasifica este texto como positivo, negativo o neutral: [texto]"
```

### Few-shot Prompting
Incluir ejemplos para guiar el modelo.
```
"Clasifica el sentimiento:
Ejemplo 1: 'Me encanta este producto' → Positivo
Ejemplo 2: 'Muy decepcionado con la entrega' → Negativo
Ahora clasifica: 'Es lo que esperaba'"
```

### Chain of Thought (CoT)
Pedir razonamiento paso a paso.
```
"Resuelve este problema matemático. 
Piensa paso a paso antes de dar la respuesta final."
```

### Role Prompting
Asignar un rol específico al modelo.
```
"Actúa como un revisor de código con 10 años de experiencia 
en React. Revisa este componente e identifica posibles 
problemas de rendimiento y mejores prácticas."
```

---

## 🔧 Parámetros de los LLMs

| Parámetro | Descripción | Rango |
|---|---|---|
| **Temperature** | Creatividad vs determinismo | 0 (determinista) – 2 (muy creativo) |
| **Max tokens** | Longitud máxima de respuesta | Depende del modelo |
| **Top P** | Diversidad del vocabulario | 0–1 |
| **System prompt** | Instrucciones base del modelo | Texto |

---

## 💡 Mejores Prácticas

1. **Sé específico** — Cuanto más detallado, mejor resultado
2. **Usa ejemplos** — Few-shot supera a zero-shot en tareas complejas
3. **Divide problemas grandes** — En múltiples prompts más simples
4. **Itera** — El primer prompt rara vez es el mejor
5. **Define el formato de salida** — "Responde en JSON", "Usa bullet points"
6. **Controla el rol** — "Actúa como..." cambia radicalmente el tono

---

## 🔗 Volver al Índice
- [[Index]]
- [[../Index|Todos los Cursos]]
