# Regex avanzado: límites y Python

## ¿Por qué?

Saber cuándo no usar una herramienta es tan importante como saber usarla. Regex tiene límites: no entiende sintaxis, no maneja semántica, falla en casos complejos.

## ¿Qué?

**Límites de regex. Cuándo usar PLN en vez de regex.**

Regex busca patrones de caracteres, no entiende estructuras lingüísticas.

## ¿Para qué?

Evitar frustraciones intentando resolver problemas con la herramienta equivocada. Reconocer cuándo regex no es suficiente y se requieren técnicas de PLN o IA.

## ¿Cómo?

### Casos donde regex no funciona

- "Encontrar todas las frases en voz pasiva" → Se necesita parser sintáctico
- "Extraer nombres de personas" → Se necesita NER
- "Identificar sentimiento" → Se necesita análisis semántico
- "Extraer todas las coincidencias, no solo la primera" → Se necesita Python

### Python regex vs Google Sheets

| Función | Sheets | Python |
|---------|--------|--------|
| Extraer primera coincidencia | REGEXEXTRACT | `re.search()` |
| Extraer todas las coincidencias | No existe | `re.findall()` |
| Reemplazar | REGEXREPLACE | `re.sub()` |
| Verificar si coincide | REGEXMATCH | `re.match()` / `re.fullmatch()` |

### Sintaxis básica de Python regex

```python
import re

texto = "Los posts sobre influencers generan engagement"

# re.search() - primera coincidencia
resultado = re.search(r'\b\w+ing\b', texto)
# Devuelve un objeto match, acceder con .group()

# re.findall() - todas las coincidencias
resultados = re.findall(r'\b\w+ing\b', texto)
# Devuelve lista: ['posts', 'influencers', 'engagement']

# re.sub() - reemplazar
nuevo_texto = re.sub(r'\b\w+ing\b', '[ANGICISMO]', texto)
# Devuelve texto con reemplazos

# re.match() - coincide solo al inicio
if re.match(r'^Los', texto):
    # True si el texto empieza con "Los"
```

### Ejercicio

[Regex avanzado - Ejercicio](avanzado-ejercicio.md)

## Y ahora, ¿qué?

### Hacia PLN

Para análisis profundo se necesita procesamiento de lenguaje natural.
