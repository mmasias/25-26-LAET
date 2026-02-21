# Ejercicio de Prompting Básico

## Objetivo

Aprender a estructurar prompts efectivos para tareas lingüísticas.

## Nivel: Medio

## Corpus de trabajo

Glosario bilingüe del ejercicio de traducción automática


## Parte 1: Anatomía de un buen prompt (15 min)

**Objetivo:** Identificar componentes de prompts efectivos.

**Tarea:** Comparar dos prompts para la misma tarea.

```markdown
Prompt A (malo):
"Define influencer"


Prompt B (bueno):
"Actúa como lingüista especializado en lenguaje digital.
Define el término 'influencer' en el contexto de redes sociales.
Incluye:
1. Definición breve (1 frase)
2. Etimología o origen
3. Ejemplo de uso
4. Traducción al inglés
Mantén un tono académico pero accesible."


Ejercicio: Analizar las diferencias
1. ¿Qué información falta en el Prompt A?
2. ¿Qué componentes adicionales tiene el Prompt B?
3. ¿Cuál generará mejor resultado? ¿Por qué?

Componentes identificados:
- Rol: ___
- Contexto: ___
- Tarea: ___
- Formato: ___
- Restricciones: ___
```


## Parte 2: Iteración de prompts (25 min)

**Objetivo:** Mejorar un prompt mediante iteraciones sucesivas.

**Tarea:** Diseñar prompt para generar definiciones de términos del glosario.

```markdown
Iteración 1:
Prompt: "Define el término postear"

Resultado: ___
Problemas: ___


Iteración 2:
Prompt: "Define el término postear en el contexto de redes sociales"

Resultado: ___
Problemas: ___


Iteración 3:
Prompt: "Define el término 'postear' específicamente en el contexto
de redes sociales como Twitter o Instagram. Incluye un ejemplo de uso."

Resultado: ___
Problemas: ___


Iteración 4:
Prompt: "Actúa como diccionario de lengua española. Define el verbo
'postear' usado en el contexto de redes sociales. Proporciona:
1. Definición en 1 frase
2. Si es préstamo del inglés
3. Un ejemplo de uso real
4. Una traducción natural al inglés"

Resultado: ___
Evaluación: ___
```


## Parte 3: Prompt para análisis gramatical (20 min)

**Objetivo:** Usar LLM para análisis gramatical de términos.

**Tarea:** Crear prompt que analice categoría gramatical de términos.

```markdown
Prompt objetivo:
Analizar categoría gramatical, variación morfológica y uso sintáctico.

Diseño:

Escribe un prompt que pida al LLM:
- Categoría gramatical (sustantivo, verbo, adjetivo, etc.)
- Variaciones morfológicas (plural, conjugaciones)
- Posición típica en la oración
- Ejemplos de uso

Prompt diseñado:
___

Resultado con término "tuitear":
___

Evaluación:
- ¿Identificó correctamente que es un verbo?
- ¿Dio conjugaciones correctas?
- ¿Los ejemplos son auténticos?
```


## Parte 4: Prompt para extracción de contexto (20 min)

**Objetivo:** Extraer contexto de uso de términos del glosario.

**Tarea:** Diseñar prompt que genere oraciones de ejemplo naturales.

```markdown
Prompt objetivo:
Generar oraciones de ejemplo auténticas usando términos del lenguaje digital.

Diseño:
___

Prueba con 3 términos:
1. "viral"
   Resultado: ___
   ¿Suena natural? ___

2. "trending topic"
   Resultado: ___
   ¿Suena natural? ___

3. "community manager"
   Resultado: ___
   ¿Suena natural? ___

Problemas detectados:
- Oraciones muy formales: ___
- Vocabulario inadecuado: ___
- Contexto incorrecto: ___

Mejoras al prompt:
___
```


## Parte 5: Prompt con ejemplos (few-shot) (20 min)

**Objetivo:** Usar ejemplos para guiar la salida del LLM.

**Tarea:** Crear prompt few-shot para definiciones consistentes.

```markdown
Prompt few-shot:

"Define cada término del lenguaje digital siguiendo este formato:

Término: influencer
Definición: Persona con gran número de seguidores en redes sociales
cuya opinión influye en las decisiones de su audiencia.
Origen: Préstamo del inglés, de "influence" (influencia) + "-er" (agente)

Término: postear
Definición: Publicar contenido en una red social o plataforma digital.
Origen: Verbo derivado del sustantivo inglés "post" (publicación)

Término: [NUEVO TÉRMINO]
Definición:
Origen:"

Términos a definir:
1. tuitear
2. viralizar
3. linkear

Resultados:
1. tuitear
   ___

2. viralizar
   ___

3. linkear
   ___

¿El formato se mantiene consistente? ___
```


## Parte 6: BONUS - Comparación de modelos (10 min)

**Tarea:** Probar el mismo prompt en diferentes modelos.

```markdown
Prompt estándar:
"Define brevemente el término 'influencer' en el contexto de redes
sociales. Incluye origen etimológico y un ejemplo."

Modelos a probar:
- ChatGPT (GPT-4 o GPT-4o): ___
- Claude (Sonnet u Opus): ___
- Gemini: ___

Comparación:
- Longitud: ___
- Profundidad etimológica: ___
- Calidad del ejemplo: ___
- ¿Cuál dio mejor resultado? ___
```


## Entregable

**Documento con:**

1. **Análisis comparativo** (Parte 1): diferencias entre prompt malo y bueno
2. **Iteraciones** (Parte 2): 4 versiones de prompt con resultados
3. **Prompt para análisis gramatical** (Parte 3): prompt diseñado + resultado
4. **Prompt para contexto** (Parte 4): prompt + 3 resultados + mejoras
5. **Prompt few-shot** (Parte 5): plantilla + resultados para 3 términos
6. **Comparación de modelos** (Parte 6, bonus): respuestas de 3 modelos


## Hacia la herramienta final

Este ejercicio construye:
- **Repertorio de prompts efectivos** para tareas lingüísticas
- **Plantillas reutilizables** para análisis de términos
- **Habilidad de iteración** basada en evaluación de resultados
- **Base para prompting avanzado**: técnicas de few-shot, chain-of-thought

**Conexión con ejercicios anteriores:**
- Glosario bilingüe: input para generar definiciones y análisis
- Fundamentos IA: conocimiento de límites para diseñar prompts mejores

**Producto:**
- Biblioteca de prompts probados para definiciones, análisis gramatical, contexto

**Próximo paso:** Prompting avanzado - técnicas complejas para tareas más difíciles.
