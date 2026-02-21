# Ejercicio de Prompting Avanzado

## Objetivo

Aplicar técnicas complejas de prompting para tareas lingüísticas avanzadas.

## Nivel: Avanzado

## Corpus de trabajo

Glosario completo + campos semánticos (ejercicios PLN anteriores)


## Parte 1: Chain-of-thought (CoT) (25 min)

**Objetivo:** Guiar al LLM para que muestre su razonamiento paso a paso.

**Tarea:** Diseñar prompt CoT para análisis etimológico complejo.

```markdown
Tarea: Analizar si un término es anglicismo, calco o neologismo.

Prompt Chain-of-Thought:

"Analiza el origen del término '[TÉRMINO]' siguiendo estos pasos:

Paso 1: Identificar la lengua de origen del término base
Paso 2: Determinar si existe morfología española añadida
Paso 3: Comparar con el término en inglés (si aplica)
Paso 4: Clasificar como:
   - Anglicismo directo (término inglés usado tal cual)
   - Calco (traducción literal de expresión inglesa)
   - Neologismo español (creación nueva con morfología española)
   - Adaptación (término extranjero con grafía o pronunciación adaptada)
Paso 5: Justificar la clasificación

Comienza tu análisis:"


Practicar con:
1. "tuitear"
   Análisis del LLM: ___
   Clasificación final: ___
   ¿Es correcta? ___

2. "influencer"
   Análisis del LLM: ___
   Clasificación final: ___
   ¿Es correcta? ___

3. "retuitear"
   Análisis del LLM: ___
   Clasificación final: ___
   ¿Es correcta? ___
```


## Parte 2: Few-shot con categorías (25 min)

**Objetivo:** Usar ejemplos etiquetados para clasificación consistente.

**Tarea:** Crear sistema few-shot para clasificar términos por categoría.

```markdown
Prompt few-shot:

"Clasifica cada término del lenguaje digital en una de estas categorías:
   - A: Anglicismo directo
   - C: Calco semántico
   - N: Neologismo español
   - T: Técnico/especializado
   - G: General (no específico de digital)

Ejemplos:

Término: 'influencer' → Categoría: A
Justificación: Término inglés usado sin modificación

Término: 'red social' → Categoría: C
Justificación: Calco de 'social network', expresión preexistente

Término: 'tuitear' → Categoría: N
Justificación: Neologismo formado con morfología española (-ar)

Término: 'algoritmo' → Categoría: T
Justificación: Término técnico preexistente, usado en contexto digital

Término: 'hablar' → Categoría: G
Justificación: Verbo general, no específico del lenguaje digital


Ahora clasifica:

Término: 'postear'
Categoría: ___
Justificación: ___

Término: 'viral'
Categoría: ___
Justificación: ___

Término: 'hashtag'
Categoría: ___
Justificación: ___

Término: 'compartir'
Categoría: ___
Justificación: ___

Término: 'community manager'
Categoría: ___
Justificación: ___"
```


## Parte 3: Self-consistency (20 min)

**Objetivo:** Pedir múltiples soluciones y seleccionar la más consistente.

**Tarea:** Aplicar self-consistency para análisis de ambigüedad.

```markdown
Tarea: Identificar si un término tiene usos múltiples (polisemia).

Prompt:

"Analiza el término '[TÉRMINO]' determinando si tiene:
   - Un único significado en contexto digital
   - Múltiples significados relacionados
   - Múltiples significados no relacionados (polisemia)

Para cada significado, proporciona:
1. Definición
2. Contexto típico de uso
3. Ejemplo"


Probar con términos ambiguos:

Término: "post"

Análisis 1 (primera ejecución): ___

Análisis 2 (segunda ejecución): ___

Análisis 3 (tercera ejecución): ___

Comparación:
- ¿Son consistentes los análisis? ___
- ¿Identificaron los mismos significados? ___
- Si difieren, ¿cuál es más completo? ___


Término: "story"

Análisis 1: ___

Análisis 2: ___

Análisis 3: ___

¿Consistencia? ___
```


## Parte 4: Prompt estructurado con JSON (20 min)

**Objetivo:** Obtener salida estructurada para procesamiento automático.

**Tarea:** Diseñar prompt que devuelva JSON válido.

```markdown
Prompt:

"Para cada término del lenguaje digital, genera un objeto JSON
con esta estructura exacta:

{
  \"termino\": \"string\",
  \"categoria_gramatical\": \"sustantivo|verbo|adjetivo|otro\",
  \"origen\": \"anglicismo|calco|neologismo|español\",
  \"definicion\": \"string (máx 100 caracteres)\",
  \"ejemplo\": \"string (oración completa)\",
  \"traduccion_ingles\": \"string\",
  \"frecuencia\": \"alta|media|baja\"
}

Genera JSON para estos 5 términos:
1. influencer
2. tuitear
3. viralizar
4. linkear
5. trend

Devuelve SOLO el JSON, sin texto adicional."


Resultado:
___

Validación:
- ¿Es JSON válido? ___ (pegar en https://jsonlint.com)
- ¿Tiene todos los campos? ___
- ¿Tipos de datos correctos? ___

Si falla, ¿qué parte del prompt hay que modificar?
___
```


## Parte 5: Descomposición de tareas (15 min)

**Objetivo:** Dividir tarea compleja en subtareas manejables.

**Tarea:** Crear pipeline de prompts para análisis completo de término.

```markdown
Tarea global: Análisis completo de un término del lenguaje digital.

Descomposición:

PROMPT 1: Extracción de información básica
"Analiza el término '[TÉRMINO]' y proporciona:
   - Categoría gramatical
   - Posibles variaciones morfológicas
   - Frecuencia de uso (alta/media/baja)
   - Primer año de uso documentado (si es conocido)"

Resultado: ___


PROMPT 2: Análisis etimológico
"Analiza el origen etimológico del término '[TÉRMINO]':
   - Lengua de origen
   - Si es préstamo, calco o adaptación
   - Etimología del término base"
(Solo si PROMPT 1 indica que es préstamo)

Resultado: ___


PROMPT 3: Análisis semántico
"Analiza el significado del término '[TÉRMINO]':
   - Definición precisa
   - Matices de significado
   - Sinónimos dentro del lenguaje digital
   - Antónimos o términos relacionados"

Resultado: ___


PROMPT 4: Síntesis
"Basándote en los análisis anteriores, genera una ficha completa
del término '[TÉRMINO]' en formato Markdown con secciones:
   ## Definición
   ## Etimología
   ## Análisis gramatical
   ## Significado y matices
   ## Ejemplos de uso
   ## Traducciones"

Resultado final: ___
```


## Parte 6: BONUS - Prompt que se corrige (10 min)

**Tarea:** Diseñar prompt que revise su propia salida.

```markdown
Prompt:

"Paso 1: Genera una definición del término 'postear' en el contexto
de redes sociales.

Paso 2: Revisa tu definición y verifica:
   - ¿Es precisa?
   - ¿Distingue entre 'postear' y 'publicar' si hay diferencia?
   - ¿El ejemplo es auténtico?

Paso 3: Si encuentras problemas, genera una versión mejorada."


Salida del LLM:
___
```


## Entregable

**Documento con:**

1. **Prompt CoT** (Parte 1): prompt diseñado + análisis de 3 términos
2. **Sistema few-shot** (Parte 2): prompt completo con clasificaciones
3. **Self-consistency** (Parte 3): 3 análisis para 2 términos + comparación
4. **Prompt JSON** (Parte 4): prompt + resultado + validación
5. **Pipeline descompuesto** (Parte 5): 4 prompts + resultado final
6. **Prompt autocorrectivo** (Parte 6, bonus): prompt + resultado


## Hacia la herramienta final

Este ejercicio construye:
- **Sistema de prompts estructurados** para análisis terminológico completo
- **Plantillas reproducibles** para clasificación, extracción, análisis
- **Pipeline automatizado** que podría implementarse con API
- **Salida estructurada** (JSON) para integración con herramientas anteriores

**Conexión con ejercicios anteriores:**
- Prompting básico: estructuras simples
- Prompting avanzado: técnicas para tareas complejas
- Glosario completo: input para análisis avanzado
- JSON estructurado: compatible con procesamiento Python (ejercicios PLN)

**Producto:**
- Biblioteca de prompts avanzados para análisis lingüístico automatizado

**Próximo paso:** Aplicar técnicas de prompting a tareas específicas de traducción y creación de contenido.
