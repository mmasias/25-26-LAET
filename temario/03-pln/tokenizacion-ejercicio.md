# Ejercicio de Tokenización y Normalización

## Objetivo

Tokenizar, normalizar y lematizar el corpus limpio para preparar análisis estadísticos.

## Nivel: Simple

## Corpus de trabajo

Corpus limpio procedente del ejercicio de Regex avanzado (terminos_extraidos.csv + corpus_lenguaje_digital.txt)


## Parte 1: Setup en Google Colab (10 min)

```python
# Instalar spaCy y modelo español
!pip install spacy
!python -m spacy download es_core_news_sm

import spacy
from collections import Counter

# Cargar modelo
nlp = spacy.load("es_core_news_sm")

# Cargar corpus limpio (del ejercicio anterior)
with open('corpus_limpio.txt', 'r', encoding='utf-8') as f:
    corpus = f.read()

print(f"Corpus cargado: {len(corpus)} caracteres")
```


## Parte 2: Tokenización básica (20 min)

**Tarea:** Comparar división por espacios versus tokenización con spaCy.

```python
# Método ingenuo: split por espacios
tokens_naive = corpus.split()

# Método spaCy: tokenización real
doc = nlp(corpus)
tokens_spacy = [token.text for token in doc]

print(f"Tokens naïve: {len(tokens_naive)}")
print(f"Tokens spaCy: {len(tokens_spacy)}")

# ¿Por qué son diferentes?
# Mostrar ejemplos donde difieren
for i, (t1, t2) in enumerate(zip(tokens_naive[:20], tokens_spacy[:20])):
    if t1 != t2:
        print(f"Naïve: '{t1}' vs spaCy: '{t2}'")
```


## Parte 3: Normalización (20 min)

**Tarea:** Aplicar normalización (lowercasing, eliminación de puntuación, eliminación de stop words).

```python
# Lowercasing
tokens_lower = [t.lower() for t in tokens_spacy]

# Sin puntuación
tokens_no_punct = [t.text for t in doc if not t.is_punct]

# Sin stop words
tokens_no_stop = [t.text for t in doc if not t.is_stop]

print(f"Tokens originales: {len(tokens_spacy)}")
print(f"Tokens sin puntuación: {len(tokens_no_punct)}")
print(f"Tokens sin stop words: {len(tokens_no_stop)}")
```


## Parte 4: Lematización (20 min)

**Tarea:** Extraer lemas de todas las palabras.

```python
# Extraer lemas
lemas = [token.lemma_ for token in doc]

# Comparar token vs lema
print("\n=== Token vs Lema ===")
for token in list(doc)[:30]:
    if token.text != token.lemma_:
        print(f"{token.text} → {token.lemma_}")

# Frecuencias de lemas (normalizados)
freq_lemas = Counter([l.lower() for l in lemas if not doc[lemas.index(l)].is_punct])

print("\n=== Lemas más frecuentes ===")
for lema, count in freq_lemas.most_common(20):
    print(f"{lema}: {count}")
```


## Parte 5: Segmentación en oraciones (10 min)

**Tarea:** Dividir el corpus en oraciones para análisis contextual.

```python
# Extraer oraciones
oraciones = list(doc.sents)

print(f"Total de oraciones: {len(oraciones)}")
print(f"Longitud media: {sum(len(s) for s in oraciones) / len(oraciones):.1f} tokens")

# Mostrar oraciones más largas
oraciones_ordenadas = sorted(oraciones, key=len, reverse=True)
print("\n=== Oraciones más largas ===")
for i, s in enumerate(oraciones_ordenadas[:5], 1):
    print(f"{i}. ({len(s)} tokens) {s}")
```


## Parte 6: Guardar resultados (10 min)

**Tarea:** Crear archivos para análisis posterior.

```python
import json

# Guardar tokens normalizados
with open('tokens_normalizados.json', 'w', encoding='utf-8') as f:
    json.dump({
        'tokens': tokens_no_stop,
        'lemas': lemas,
        'oraciones': [s.text for s in oraciones]
    }, f, ensure_ascii=False, indent=2)

print("Resultados guardados en tokens_normalizados.json")
```


## Hacia la herramienta final

Este ejercicio construye:
- **Corpus tokenizado** listo para análisis estadístico
- **Lemas normalizados** para conteo de frecuencias fiable
- **Oraciones segmentadas** para análisis contextual
- **Base para POS tagging**: mismo objeto `doc` se usará en próxima sesión

**Conexión con ejercicios anteriores:**
- Regex básico/aplicado/avanzado: limpieza y extracción de términos
- Tokenización: preparación del corpus para análisis lingüístico

**Diferencia clave con regex:**
- Regex: extrae patrones específicos
- Tokenización: estructura todo el corpus para análisis general

**Próximo paso:** Este objeto `doc` tokenizado es input para análisis gramatical (POS tagging).
