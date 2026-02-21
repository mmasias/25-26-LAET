# Ejercicio de IA para Traducción/Localización

## Objetivo

Usar LLMs para traducción y localización de contenido sobre lenguaje digital.

## Nivel: Medio

## Corpus de trabajo

Muestra de textos del corpus + definiciones del glosario


## Parte 1: Prompt especializado para traducción (20 min)

**Objetivo:** Diseñar prompt optimizado para traducción de terminología digital.

```markdown
Tarea: Traducir definiciones de términos del lenguaje digital al inglés.

Prompt base:
"Traduce al inglés el siguiente texto sobre lenguaje digital:
[TEXTO]"


Problema: Puede generar traducciones literales o perder matices.

Prompt mejorado:

"Actúa como traductor especializado en tecnología y redes sociales.
Traduce al inglés el siguiente texto, teniendo en cuenta:

1. Usa terminología estándar en inglés (no inventes términos)
2. Para anglicismos, mantén el original en inglés si ese es el uso estándar
3. Adapta referencias culturales españolas/latinoamericanas al contexto angloparlante
4. Mantén el registro formal pero accesible

Texto a traducir:
[TEXTO]"


Ejercicio: Traducir 3 definiciones

1. "Influencer: Persona con gran número de seguidores en redes sociales
    cuya opinión influye en las decisiones de compra o comportamiento de su audiencia."

   Traducción: ___
   ¿Mantiene terminología correcta? ___

2. "Postear: Publicar contenido en una red social o plataforma digital.
    Proviene del inglés 'post' y se ha adaptado morfológicamente al español."

   Traducción: ___
   ¿Maneja bien el origen etimológico? ___

3. "Tuitear: Enviar un mensaje a través de la plataforma Twitter/X.
    Ejemplo: 'Voy a tuitear esto ahora mismo'."

   Traducción: ___
   ¿Adapta la referencia a la plataforma? ___
```


## Parte 2: Localización cultural (25 min)

**Objetivo:** Adaptar contenido para diferentes variedades del inglés.

```markdown
Tarea: Localizar texto para diferentes audiencias angloparlantes.

Texto base:
"En España, muchos 'influencers' colaboran con marcas para promocionar
productos en Instagram, usando hashtags como #ad para transparentar la publicidad."


Prompt para inglés británico:

"Localiza este texto para una audiencia del Reino Unido.
Usa ortografía y vocabulario británicos (ej: colour, not color).
Adapta las referencias culturales si es necesario.

Texto: [TEXTO]"

Resultado: ___


Prompt para inglés americano:

"Localiza este texto para una audiencia de Estados Unidos.
Usa ortografía y vocabulario americanos.
Adapta las referencias culturales si es necesario.

Texto: [TEXTO]"

Resultado: ___


Comparación:
Diferencias identificadas:
- Ortografía: ___
- Vocabulario: ___
- Referencias culturales: ___
- ¿Hay diferencias en cómo se traducen los términos de redes sociales? ___
```


## Parte 3: Comparación LLM vs TA tradicional (20 min)

**Objetivo:** Comparar calidad de LLM versus DeepL/Google Translate.

```markdown
Texto a traducir:
"El community manager es responsable de gestionar la presencia online
de la marca, incluyendo linkear contenido, responder comentarios y
viralizar publicaciones para alcanzar mayor engagement."


Traducción DeepL/Google:
___


Traducción LLM (con prompt especializado):
___


Análisis comparativo:

Criterio: 'community manager'
- DeepL/Google: ___
- LLM: ___
- ¿Cuál maneja mejor que ya es un término establecido? ___

Criterio: 'linkear'
- DeepL/Google: ___
- LLM: ___
- ¿Cuál reconoce mejor que es un neologismo del español? ___

Criterio: 'viralizar'
- DeepL/Google: ___
- LLM: ___
- ¿Cuál propone traducción más natural? ___

Criterio: 'engagement'
- DeepL/Google: ___
- LLM: ___
- ¿Alguno reconoce que es anglicismo usado en español? ___

Conclusión: ¿Qué herramienta es mejor para este tipo de texto?
___
```


## Parte 4: Post-edición asistida por LLM (20 min)

**Objetivo:** Usar LLM para mejorar traducciones automáticas.

```markdown
Workflow:
1. Obtener traducción inicial (DeepL/Google)
2. Pedir al LLM que revise y mejore
3. Evaluar resultado final


Texto: "La hashtag es una palabra clave precedida del símbolo # que
permite agrupar contenidos por tema en redes sociales."

Paso 1 - TA inicial (DeepL/Google):
___

Problemas detectados: ___


Paso 2 - Prompt de revisión al LLM:

"Esta es una traducción automática del español al inglés.
Revísala y corrige:
1. Errores gramaticales
2. Terminología incorrecta
3. Falta de naturalidad

Traducción automática: [TA_INICIAL]

Si encuentra errores, explica el problema y proporciona la versión corregida."

Resultado del LLM: ___


Paso 3 - Evaluación:
¿Mejoró la traducción? ___
¿Qué corrigió? ___
¿Introdujo nuevos errores? ___
```


## Parte 5: Preservación de formato (15 min)

**Objetivo:** Traducir manteniendo estructura o formato específico.

```markdown
Tarea: Traducir tabla de glosario manteniendo formato.

Prompt:

"Traduce las siguientes entradas de glosario al inglés.
MANTÉN el formato exacto de líneas y pipes (|).
No agregues ni elimines columnas.

| Término | Categoría | Definición |
|---------|-----------|------------|
| influencer | Sustantivo | Persona con seguidores que influye en su audiencia |
| postear | Verbo | Publicar contenido en redes sociales |
| viral | Adjetivo | Que se difunde rápidamente por internet |"

Resultado:
___

¿Se mantuvo el formato? ___
¿Las definiciones quedaron naturales en inglés? ___
```


## Parte 6: BONUS - Explicación de decisiones de traducción (10 min)

**Tarea:** Pedir al LLM que justifique sus decisiones de traducción.

```markdown
Prompt:

"Traduce al inglés: 'La influencer posteo una foto y se viralizó'
 Después de traducir, explica tus decisiones para:
 1. 'influencer'
 2. 'posteo'
 3. 'viralizó'

 ¿Usaste el término en inglés o lo tradujiste? ¿Por qué?"

Resultado:
___

Análisis de la explicación:
___
```


## Entregable

**Documento con:**

1. **Prompt especializado** (Parte 1): prompt + 3 traducciones + evaluación
2. **Localización** (Parte 2): texto localizado para UK vs US + diferencias
3. **Comparación LLM vs TA** (Parte 3): análisis término por término
4. **Post-edición asistida** (Parte 4): workflow de 3 pasos con ejemplo
5. **Preservación de formato** (Parte 5): prompt + resultado
6. **Justificación de decisiones** (Parte 6, bonus): prompt + explicación


## Hacia la herramienta final

Este ejercicio construye:
- **Sistema de prompts** para traducción especializada de terminología digital
- **Workflow de localización** para diferentes variedades del inglés
- **Método de post-edición asistida** por LLM
- **Consciencia de diferencias** entre TA tradicional y LLM

**Conexión con ejercicios anteriores:**
- Traducción automática: comparación con DeepL/Google
- Prompting avanzado: aplicación de técnicas a traducción
- Glosario bilingüe: mejora y expansión con LLM

**Producto:**
- Glosario bilingüe mejorado con traducciones LLM validadas
- Sistema de prompts para traducción futura

**Próximo paso:** Creación de contenido didáctico usando IA.
