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

**Hojas de cálculo + funciones regex**

Google Sheets, Excel 365, LibreOffice Calc incluyen funciones regex:

- `REGEXEXTRACT(texto, regex)` - Extrae la primera coincidencia
- `REGEXREPLACE(texto, regex, reemplazo)` - Reemplaza coincidencias
- `REGEXMATCH(texto, regex)` - Devuelve TRUE/FALSE si coincide
- `ARRAYFORMULA()` - Aplica a todo un rango

Google Docs también permite búsqueda con regex en Editar → Buscar y reemplazar → Match using regular expressions.

**Caso 1:** Corpus digital → extraer anglicismos (buscando `\-ing`, `\-er`, `\-or`)

**Caso 2:** Corpus de traducciones → identificar citas y referencias bibliográficas

**Caso 3:** Corpus jurídico → extraer números de ley/artículo (`Art\. \d+`, `Ley \d+/\d{4}`)

**Transición a Python:** Mismo regex en regexr.com vs en Notebook Colab
