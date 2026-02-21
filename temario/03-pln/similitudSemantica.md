# Similitud semántica

## ¿Por qué?

Identificar sinónimos y términos relacionados manualmente es inviable en corpus grandes. El análisis de similitud semántica permite agrupar términos por significado, no solo por forma.

## ¿Qué?

**Similitud semántica = medir qué tan "ceranos" están dos términos en significado.**

Embeddings vectoriales: representación numérica del significado de las palabras.

## ¿Para qué?

- Encontrar sinónimos y variantes terminológicas
- Agrupar términos por campos semánticos
- Identificar términos polisémicos en diferentes contextos
- Recuperación de información por significado, no por palabra clave

## ¿Cómo?

**spaCy embeddings**

Demo: palabra → vector → palabras más similares por distancia coseno

**Ejercicio:** Corpus de artículos académicos → encontrar términos semánticamente relacionados y agruparlos por campos temáticos

**Operaciones clave:**

- Similitud entre dos palabras: `palabra1.similarity(palabra2)`
- Encontrar palabras más similares: `[w for w in vocab if palabra.similarity(w) > 0.7]`
- Visualización de clusters semánticos
