# Procesamiento de Lenguaje Natural

## ¿Por qué?

Hasta los años 50, el análisis lingüístico era manual: lingüistas leían textos, clasificaban palabras, extraían términos palabra por palabra. Con corpus de millones de palabras, este enfoque era inviable.

Simultáneamente, los primeros sistemas de traducción automática (Georgetown-IBM, 1954) intentaban traducir usando reglas manuales. Noam Chomsky argumentó que el lenguaje humano era demasiado complejo para reglas fijas, que necesitábamos entender la estructura profunda.

La pregunta fundamental: ¿Cómo pueden las máquinas analizar lenguaje sin entenderlo realmente? ¿Es posible automatizar tareas lingüísticas usando estadística en lugar de reglas?

## ¿Qué?

La solución que apareció: **Procesamiento de Lenguaje Natural (PLN)**

Análisis automático de texto usando modelos estadísticos entrenados en corpus masivos, no reglas lingüísticas explícitas.

Historia progresiva:

- **1950s:** Primeros sistemas de traducción automática (Georgetown-IBM). Enfoque basado en diccionarios y reglas. Limitado y costoso.

- **1950s-60s:** Noam Chomsky desarrolla gramática generativa. Argumenta que sistemas simbólicos con reglas deberían dominar el procesamiento de lenguaje. La IA simbólica domina las décadas siguientes.

- **1980s-90s:** Giro estadístico. Aparecen corpus masivos y métodos estadísticos. Los modelos empezaron a extraer patrones de datos reales, no de teoría lingüística. Aprender de datos, no de reglas.

- **1990s-2000s:** Aprendizaje automático aplicado a PLN. Naive Bayes, SVM, modelos ocultos de Markov para tareas como etiquetado gramatical y reconocimiento de entidades.

- **2010s:** Word embeddings (Word2Vec, GloVe). Las palabras se representan como vectores numéricos que capturan significado. "Rey" - "hombre" + "mujer" ≈ "reina".

- **2017:** Architecture "Transformer" revoluciona el campo. Atención permite modelos procesar contexto completo, no solo palabras locales.

- **2018-2023:** BERT, GPT y otros modelos pre-entrenados dominan PLN. Transfer learning: un modelo gigante entrenado una vez, luego fine-tuned para tareas específicas.

Lo fascinante: métodos que empezaron para traducción automática hoy permiten extraer terminología, analizar sentimientos, detectar entidades. La estadística superó las reglas lingüísticas.

## ¿Para qué?

- **Original:** Traducción automática, análisis de sentimiento, clasificación de textos
- **Hoy (lingüística):** Extracción terminológica, análisis de frecuencias, POS tagging, NER, similitud semántica, preprocesamiento para otros análisis

Para lingüistas: automatizar tareas repetitivas, trabajar con corpus masivos, extraer patrones que serían invisibles al análisis manual.

## ¿Cómo?

spaCy y otros modelos estadísticos analizan texto mediante:

- **Tokenización:** división en unidades significativas (no solo por espacios)
- **Lematización:** reducción a forma base de diccionario (cantando → cantar)
- **POS tagging:** clasificación gramatical automática (sustantivo, verbo, adjetivo)
- **NER:** reconocimiento de entidades (personas, lugares, organizaciones)
- **Embeddings:** representaciones vectoriales que capturan significado

**El ecumenismo estadístico-lingüístico:**

| Tarea informática | Tarea lingüística |
|---|---|
| Clasificación de spam | Detección de registro formal/informal |
| Extracción de información | Identificación de candidatos a términos |
| Análisis de sentimiento | Análisis de posicionamiento ideológico |
| Reconocimiento de entidades | Extracción de antropónimos/topónimos |
| Similitud de documentos | Agrupación por campos semánticos |

[Tokenización + normalización](tokenizacion.md) - División en palabras/oraciones, lematización

[POS tagging](pos.md) - Clasificación gramatical, spaCy demo

[Análisis terminológico](analisisTerminologico.md) - Extracción, frecuencias, contextos

[Similitud semántica](similitudSemantica.md) - Agrupación de términos por significado

[Traducción automática](traduccionAutomatica.md) - Evaluación crítica, post-edición
