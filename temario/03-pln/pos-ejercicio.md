# Ejercicio de POS Tagging y Análisis Gramatical

## Objetivo

Analizar categorías gramaticales de términos del corpus y filtrar candidatos por tipo.

## Nivel: Medio

## Corpus de trabajo

Corpus tokenizado del ejercicio anterior (objeto `doc` de spaCy)


## Parte 1: Análisis gramatical automático (15 min)

```python
import spacy
import json
from collections import Counter

# Cargar modelo y corpus
nlp = spacy.load("es_core_news_sm")

# Cargar corpus limpio
with open('corpus_limpio.txt', 'r', encoding='utf-8') as f:
    corpus = f.read()

# Procesar con spaCy (ya incluye tokenización + POS tagging)
doc = nlp(corpus)

# Explorar etiquetas POS
print("=== Etiquetas POS en spaCy ===")
for token in list(doc)[:50]:
    print(f"{token.text:15} {token.pos_:10} {token.tag_:15} {spacy.explain(token.tag_)}")
```


## Parte 2: Frecuencia de categorías gramaticales (20 min)

**Tarea:** Calcular distribución de categorías en el corpus.

```python
# Contar frecuencia de categorías gramaticales (POS)
pos_freq = Counter([token.pos_ for token in doc])

print("\n=== Distribución de categorías gramaticales ===")
total = sum(pos_freq.values())
for pos, count in pos_freq.most_common():
    porcentaje = (count / total) * 100
    print(f"{pos:10}: {count:5} ({porcentaje:5.1f}%) - {spacy.explain(pos)}")
```


## Parte 3: Extracción de sustantivos (20 min)

**Tarea:** Extraer todos los sustantivos como candidatos a términos.

```python
# Extraer sustantivos (NOUN)
sustantivos = [token.text for token in doc if token.pos_ == "NOUN"]

# Frecuencia de sustantivos
freq_sustantivos = Counter(sustantivos)

print("\n=== Sustantivos más frecuentes ===")
for sust, count in freq_sustantivos.most_common(30):
    print(f"{sust:25}: {count}")
```


## Parte 4: Extracción de adjetivos (15 min)

**Tarea:** Extraer adjetivos para análisis modificación.

```python
# Extraer adjetivos
adjetivos = [token.text for token in doc if token.pos_ == "ADJ"]

# Frecuencia de adjetivos
freq_adj = Counter(adjetivos)

print("\n=== Adjetivos más frecuentes ===")
for adj, count in freq_adj.most_common(20):
    print(f"{adj:25}: {count}")
```


## Parte 5: Análisis de verbos (10 min)

**Tarea:** Identificar verbos más frecuentes y sus tiempos.

```python
# Extraer verbos
verbos = [(token.text, token.tag_) for token in doc if token.pos_ == "VERB"]

# Agrupar por tiempo verbal
tiempos = Counter([tag for text, tag in verbos])

print("\n=== Distribución de tiempos verbales ===")
for tiempo, count in tiempos.most_common():
    explicacion = spacy.explain(tiempo)
    print(f"{tiempo:10}: {count:4} - {explicacion}")

print("\n=== Verbos más frecuentes ===")
freq_verbos = Counter([text for text, tag in verbos])
for verbo, count in freq_verbos.most_common(15):
    print(f"{verbo:25}: {count}")
```


## Parte 6: Filtrado de términos por categoría (10 min)

**Tarea:** Filtrar términos del CSV anterior por categoría gramatical.

```python
import csv

# Cargar términos extraídos con regex (del ejercicio avanzado)
terminos_extraidos = []
with open('terminos_extraidos.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for row in reader:
        terminos_extraidos.append(row)

# Clasificar cada término según su POS
print("\n=== Clasificación gramatical de términos extraídos ===")
terminos_clasificados = []

for row in terminos_extraidos[:50]:  # Primeros 50
    termino = row['Término']
    # Buscar el término en el corpus procesado
    for token in doc:
        if token.text.lower() == termino.lower():
            terminos_clasificados.append({
                'termino': termino,
                'pos': token.pos_,
                'tag': token.tag_,
                'explicacion': spacy.explain(token.tag_),
                'frecuencia': row['Frecuencia']
            })
            break

# Guardar clasificación
with open('terminos_clasificados_pos.csv', 'w', newline='', encoding='utf-8') as f:
    writer = csv.DictWriter(f, fieldnames=['termino', 'pos', 'tag', 'explicacion', 'frecuencia'])
    writer.writeheader()
    writer.writerows(terminos_clasificados)

print("Clasificación guardada en: terminos_clasificados_pos.csv")

# Resumen por categoría
categorias = Counter([t['pos'] for t in terminos_clasificados])
print("\n=== Distribución de términos por categoría ===")
for cat, count in categorias.most_common():
    print(f"{cat}: {count}")
```


## Parte 7: BONUS - Parse sintáctico (10 min)

**Tarea:** Visualizar estructura sintáctica de oraciones con términos candidatos.

```python
# Extraer oraciones con términos de interés
termino_buscar = "influencer"

for sent in doc.sents:
    if termino_buscar in sent.text.lower():
        print(f"\n=== Oración con '{termino_buscar}' ===")
        print(sent.text)
        print("\nAnálisis sintáctico:")
        for token in sent:
            print(f"{token.text:15} {token.dep_:15} ← {token.head.text}")
        break
```


## Hacia la herramienta final

Este ejercicio construye:
- **Sustantivos filtrados** como candidatos principales a términos
- **Clasificación gramatical** de términos extraídos previamente
- **Base para análisis terminológico**: términos ya clasificados por categoría
- **CSV combinado**: términos_regex + categoría_gramatical + frecuencia

**Conexión con ejercicios anteriores:**
- Regex avanzado: términos extraídos manualmente
- Tokenización: corpus estructurado para análisis
- POS tagging: clasificación gramatical automática de términos

**Diferencia clave:**
- Regex: extrae patrones sin saber qué son
- POS tagging: clasifica qué tipo de palabra es cada término

**Próximo paso:** Con términos clasificados por categoría, análisis de contexto y colocaciones.
