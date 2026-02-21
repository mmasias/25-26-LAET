# Ejercicio Regex avanzado

## Objetivo

Migrar los regexes de Sheets a Python/Colab, extraer TODAS las coincidencias (no solo la primera), y automatizar el guardado de resultados.

## Nivel: Medio-Avanzado

## Corpus de trabajo

El mismo corpus de 200 tweets/posts, pero ahora trabajando con el archivo de texto original.


## Parte 1: Setup en Google Colab (10 min)

```python
import re
import csv
from collections import Counter

# Cargar corpus
with open('corpus_lenguaje_digital.txt', 'r', encoding='utf-8') as f:
    corpus = f.read()

print(f"Corpus cargado: {len(corpus)} caracteres")
```


## Parte 2: Migración de regexes a Python (30 min)

**Tarea:** Reescribir los regexes del ejercicio anterior usando Python:

```python
# Anglicismos terminados en -ing, -er, -or
anglicismos = re.findall(r"\b[a-zA-Z]+(ing|er|or)\b", corpus)

# Palabras entre comillas
citados = re.findall(r'"([^"]+)"', corpus)

# Palabras en mayúsculas
mayusculas = re.findall(r"\b[A-ZÁÉÍÓÚÑ]{2,}\b", corpus)

# Palabras compuestas con guión
compuestos = re.findall(r"\b[a-záéíóúñ]+-[a-záéóúñ]+\b", corpus)
```


## Parte 3: Conteo y guardado automatizado (20 min)

**Tarea:** Crear un script que:

1. Cuenta frecuencias de cada tipo de término
2. Guarda resultados en un CSV

```python
# Crear CSV con todos los términos
with open('terminos_extraidos.csv', 'w', newline='', encoding='utf-8') as f:
    writer = csv.writer(f)
    writer.writerow(['Tipo', 'Término', 'Frecuencia'])

    # Anglicismos
    freq_anglicismos = Counter(anglicismos)
    for termino, count in freq_anglicismos.items():
        writer.writerow(['Anglicismo', termino, count])

    # Citados
    freq_citados = Counter(citados)
    for termino, count in freq_citados.items():
        writer.writerow(['Citado', termino, count])

    # Mayúsculas
    freq_mayusculas = Counter(mayusculas)
    for termino, count in freq_mayusculas.items():
        writer.writerow(['Mayúscula', termino, count])

print("Resultados guardados en: terminos_extraidos.csv")
```


## Parte 4: Extracción de TODAS las coincidencias (20 min)

**Limitación de Sheets versus ventaja de Python:**

```python
# Sheets: REGEXEXTRACT solo devuelve la primera coincidencia
# Python: findall() devuelve TODAS

# Demo: Extraer TODAS las coincidencias de patrones
texto = "influencer, tuitear, postear, viralizar, tuiteó, posteo"

# Sheets: encontraría solo "influencer"
sheets_result = re.search(r"\b[a-zA-Z]+(ar|er|ir)\b", texto)

# Python: encuentra TODOS
python_result = re.findall(r"\b[a-zA-Z]+(ar|er|ir)\b", texto)

print(f"Sheets (solo primera): {sheets_result.group() if sheets_result else None}")
print(f"Python (todas): {python_result}")
# Output: ['influencer', 'tuitear', 'postear', 'viralizar', 'tuiteó', 'posteo']
```


## Parte 5: BONUS - Contexto de uso (20 min)

**Tarea avanzada:** Extraer contexto de uso para los términos más frecuentes.

```python
# Buscar contexto (ventana de 3 palabras antes y después)
termino_buscar = "influencer"
ventana = 3

# Encontrar todas las posiciones del término
# Extraer contexto para cada aparición
# Guardar en un diccionario
```


## Hacia la herramienta final

Este ejercicio construye:
- **Script reproducible** para análisis de corpus
- **Archivo CSV** con todos los términos y frecuencias
- **Base de datos** para análisis PLN de próxima sesión
- **Herramienta automatizada** que puede ejecutarse en cualquier corpus

**Conexión con ejercicios anteriores:**
- Regex básico: limpieza del corpus
- Regex aplicado: primera extracción manual
- Regex avanzado: automatización completa con Python

**Próximo paso:** Este CSV será input para análisis de tokenización y POS tagging.
