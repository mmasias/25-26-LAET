# Regex avanzado: límites y Python

## ¿Por qué?

Saber cuándo no usar una herramienta es tan importante como saber usarla. Regex tiene límites: no entiende sintaxis, no maneja semántica, falla en casos complejos.

## ¿Qué?

**Límites de regex. Cuándo usar PLN en vez de regex.**

Regex busca patrones de caracteres, no entiende estructuras lingüísticas.

## ¿Para qué?

Evitar frustraciones intentando resolver problemas con la herramienta equivocada. Reconocer cuándo regex no es suficiente y se requieren técnicas de PLN o IA.

## ¿Cómo?

**Casos donde regex no funciona:**

- "Encontrar todas las frases en voz pasiva" → Se necesita parser sintáctico
- "Extraer nombres de personas" → Se necesita NER
- "Identificar sentimiento" → Se necesita análisis semántico
- "Extraer todas las coincidencias, no solo la primera" → Se necesita Python

**Python regex vs Google Sheets:**

| Función | Sheets | Python |
|---------|--------|--------|
| Extraer primera coincidencia | REGEXEXTRACT | `re.search()` |
| Extraer todas las coincidencias | No existe | `re.findall()` |
| Reemplazar | REGEXREPLACE | `re.sub()` |
| Verificar si coincide | REGEXMATCH | `re.match()` / `re.fullmatch()` |

**Ejercicio diagnóstico:** 10 tareas lingüísticas, decidir qué necesitan (regex / PLN / IA gen)

**Introducción a lo que viene:** Para análisis profundo se necesita PLN.
