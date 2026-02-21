# Tokenización y normalización

## ¿Por qué?

Las computadoras no leen como humanos. Necesitan texto estructurado: palabra por palabra, oración por oración. Sin esta estructuración, cualquier análisis automatizado es imposible.

## ¿Qué?

**Tokenización = segmentar texto en unidades (palabras, oraciones)**

**Normalización = convertir a forma estándar (minúsculas, sin acentos, lematización)**

## ¿Para qué?

Paso previo obligatorio para cualquier análisis automatizado. Análisis de frecuencias. Comparación de corpus. Preparación para análisis posteriores (POS tagging, NER, similitud semántica).

## ¿Cómo?

**spaCy** - Biblioteca de Python para NLP

Demo: texto → tokens → lemas

**Ejercicio:** Comparar frecuencia léxica en dos corpus (formal vs coloquial) usando lematización para agrupar variantes.

Notebook pre-configurado: cambiar texto, ver output.

**Operaciones clave:**

- Tokenizar por palabras: `[token.text for token in doc]`
- Tokenizar por oraciones: `[sent.text for sent in doc.sents]`
- Lematizar: `[token.lemma_ for token in doc]`
- Normalizar minúsculas: `[token.text.lower() for token in doc]`
- Filtrar stopwords: `[token.text for token in doc if not token.is_stop]`
