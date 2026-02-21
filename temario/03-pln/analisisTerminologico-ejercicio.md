# Ejercicio de Análisis Terminológico

## Objetivo

Extraer automáticamente términos candidatos, calcular frecuencias, identificar contextos y colocaciones.

## Nivel: Avanzado

## Corpus de trabajo

Corpus tokenizado + términos clasificados por POS (ejercicios anteriores)


## Parte 1: Extracción de n-gramas (25 min)

```python
import spacy
from collections import Counter
import csv

nlp = spacy.load("es_core_news_sm")

with open('corpus_limpio.txt', 'r', encoding='utf-8') as f:
    corpus = f.read()

doc = nlp(corpus)

# Función para extraer n-gramas
def extract_ngrams(doc, n):
    ngrams = []
    tokens = [token for token in doc if not token.is_punct and not token.is_space]

    for i in range(len(tokens) - n + 1):
        ngram = ' '.join([t.text for t in tokens[i:i+n]])
        ngrams.append(ngram)

    return ngrams

# Extraer bigramas y trigramas
bigramas = extract_ngrams(doc, 2)
trigramas = extract_ngrams(doc, 3)

# Frecuencias
freq_bigramas = Counter(bigramas)
freq_trigramas = Counter(trigramas)

print("=== Bigramas más frecuentes ===")
for bigrama, count in freq_bigramas.most_common(20):
    print(f"{bigrama:40}: {count}")

print("\n=== Trigramas más frecuentes ===")
for trigrama, count in freq_trigramas.most_common(20):
    print(f"{trigrama:50}: {count}")
```


## Parte 2: Filtrado de n-gramas por patrón gramatical (25 min)

**Tarea:** Extraer solo secuencias que sigan patrones terminológicos típicos (NOUN+NOUN, ADJ+NOUN).

```python
# Extraer bigramas con patrón específico
bigramas_terminologicos = []

for i in range(len(doc) - 1):
    token1 = doc[i]
    token2 = doc[i + 1]

    # Ignorar puntuación y espacios
    if token1.is_punct or token1.is_space or token2.is_punct or token2.is_space:
        continue

    # Patrones terminológicos comunes
    # Sustantivo + Sustantivo: "red social", "inteligencia artificial"
    if token1.pos_ == "NOUN" and token2.pos_ == "NOUN":
        bigramas_terminologicos.append(f"{token1.text} {token2.text}")

    # Adjetivo + Sustantivo: "digital learning", "Machine Learning"
    elif token1.pos_ == "ADJ" and token2.pos_ == "NOUN":
        bigramas_terminologicos.append(f"{token1.text} {token2.text}")

    # Sustantivo + Adjetivo: "aprendizaje automático"
    elif token1.pos_ == "NOUN" and token2.pos_ == "ADJ":
        bigramas_terminologicos.append(f"{token1.text} {token2.text}")

# Frecuencias de bigramas terminológicos
freq_bigramas_term = Counter(bigramas_terminologicos)

print("\n=== Bigramas terminológicos más frecuentes ===")
for bigrama, count in freq_bigramas_term.most_common(30):
    print(f"{bigrama:45}: {count}")
```


## Parte 3: Extracción de contexto (20 min)

**Tarea:** Para términos frecuentes, extraer ventana de contexto (palabras antes y después).

```python
def extract_context(doc, termino, ventana=3):
    """Extrae contexto de un término en el corpus"""
    contextos = []

    for i, token in enumerate(doc):
        if token.text.lower() == termino.lower():
            # Ventana de contexto
            inicio = max(0, i - ventana)
            fin = min(len(doc), i + ventana + 1)

            contexto = ' '.join([t.text for t in doc[inicio:fin]])
            contextos.append(contexto)

    return contextos

# Analizar contexto de términos frecuentes
terminos_analizar = ["influencer", "post", "tuitear"]

for termino in terminos_analizar:
    contextos = extract_context(doc, termino, ventana=3)
    print(f"\n=== Contextos de '{termino}' ({len(contextos)} apariciones) ===")
    for ctx in contextos[:5]:  # Primeros 5
        print(f"  - {ctx}")
```


## Parte 4: Análisis de colocaciones (15 min)

**Tarea:** Identificar palabras que frecuentemente acompañan a términos candidatos.

```python
def get_collocations(doc, termino, ventana=2, pos_filter=None):
    """Obtiene colocaciones de un término"""
    colocaciones = Counter()

    for i, token in enumerate(doc):
        if token.text.lower() == termino.lower():
            # Buscar palabras en ventana
            inicio = max(0, i - ventana)
            fin = min(len(doc), i + ventana + 1)

            for j in range(inicio, fin):
                if j == i:  # Saltar el término mismo
                    continue

                col_token = doc[j]

                # Filtrar por categoría si se especifica
                if pos_filter and col_token.pos_ not in pos_filter:
                    continue

                # Ignorar stop words y puntuación
                if not col_token.is_stop and not col_token.is_punct:
                    colocaciones[col_token.lemma_] += 1

    return colocaciones

# Colocaciones de términos frecuentes
for termino in terminos_analizar:
    colocs = get_collocations(doc, termino, ventana=2, pos_filter=["NOUN", "ADJ", "VERB"])
    print(f"\n=== Colocaciones de '{termino}' ===")
    for col, count in colocs.most_common(10):
        print(f"  {col:20}: {count}")
```


## Parte 5: Integración de todos los análisis (15 min)

**Tarea:** Crear archivo maestro unificando todos los análisis.

```python
import json

# Compilar todos los términos
terminologia_completa = {
    'monolemas': {
        'sustantivos': dict(freq_sustantivos.most_common(100)),
    },
    'polilemas': {
        'bigramas_terminologicos': dict(freq_bigramas_term.most_common(50)),
        'bigramas_generales': dict(freq_bigramas.most_common(50)),
        'trigramas': dict(freq_trigramas.most_common(30)),
    },
    'colocaciones': {},
    'metadatos': {
        'total_tokens': len(doc),
        'total_oraciones': len(list(doc.sents)),
        'total_sustantivos': sum(freq_sustantivos.values()),
        'total_bigramas': len(bigramas),
    }
}

# Añadir colocaciones de términos principales
for termino in terminos_analizar:
    colocs = get_collocations(doc, termino, ventana=2)
    terminologia_completa['colocaciones'][termino] = dict(colocs.most_common(10))

# Guardar como JSON
with open('terminologia_completa.json', 'w', encoding='utf-8') as f:
    json.dump(terminologia_completa, f, ensure_ascii=False, indent=2)

print("\n=== Resultados guardados ===")
print("Archivo: terminologia_completa.json")
print(f"Total monolemas: {len(terminologia_completa['monolemas']['sustantivos'])}")
print(f"Total polilemas: {len(terminologia_completa['polilemas']['bigramas_terminologicos'])}")
print(f"Términos con colocaciones: {len(terminologia_completa['colocaciones'])}")
```


## Parte 6: BONUS - Detección de neologismos (10 min)

**Tarea:** Identificar potenciales neologismos comparando con diccionario.

```python
# Comparar términos con diccionario de spaCy
neologismos = []

# Para bigramas terminológicos frecuentes
for bigrama, count in freq_bigramas_term.most_common(30):
    palabras = bigrama.split()

    # Verificar si alguna palabra no está en vocabulario
    es_nuevo = False
    for palabra in palabras:
        token_palabra = nlp(palabra)[0]
        if not token_palabra.vector_norm:  # No tiene vector = palabra desconocida
            es_nuevo = True
            break

    if es_nuevo:
        neologismos.append((bigrama, count))

print("\n=== Potenciales neologismos ===")
for neologismo, count in neologismos:
    print(f"{neologismo:45}: {count}")
```


## Hacia la herramienta final

Este ejercicio construye:
- **Glosario terminológico completo** con monolemas y polilemas
- **Análisis de contexto** para cada término frecuente
- **Colocaciones** que definen patrones de uso
- **JSON estructurado** listo para visualización o consulta
- **Base de datos terminológica** del corpus digital

**Conexión con ejercicios anteriores:**
- Regex: primera extracción de candidatos
- Tokenización: estructura del corpus
- POS tagging: filtrado por categoría gramatical
- **Análisis terminológico: síntesis de todo lo anterior**

**Producto final:**
- `terminologia_completa.json`: glosario estructurado del lenguaje digital
- Entradas: término + frecuencia + contexto + colocaciones + categoría gramatical

**Próximo paso:** Usar similitud semántica para agrupar términos por campos de significado.
