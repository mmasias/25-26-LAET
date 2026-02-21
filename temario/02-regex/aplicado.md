# Regex aplicado

## ¿Por qué?

Casos reales son más complejos que ejemplos didácticos. Corpus grandes no caben en regexr.com. Necesitan procesar archivos reales, extraer información estructurada y reutilizar regexes.

## ¿Qué?

**Patrones avanzados para casos lingüísticos específicos**

Aplicación de regex a corpus reales con herramientas que manejan volúmenes mayores.

## ¿Para qué?

- Extracción terminológica de documentos técnicos
- Normalización de corpus multilingües
- Preprocesamiento para análisis posterior

## ¿Cómo?

**Google Sheets + funciones regex**

- `REGEXEXTRACT(texto, regex)` - Extrae la primera coincidencia
- `REGEXREPLACE(texto, regex, reemplazo)` - Reemplaza coincidencias
- `REGEXMATCH(texto, regex)` - Devuelve TRUE/FALSE si coincide
- `ARRAYFORMULA()` - Aplica a todo un rango

**Caso 1:** Corpus de tweets → extraer anglicismos (buscando `\-ing`, `\-er`, `\-or`)

**Caso 2:** Corpus literario → identificar diálogos vs narración

**Caso 3:** Corpus médico → extraer dosis medicamentos (`## mg`, `## ml`)

**Transición a Python:** Mismo regex en regexr.com vs en Notebook Colab
