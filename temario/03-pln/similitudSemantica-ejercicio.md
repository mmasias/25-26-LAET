# Ejercicio de Similitud Semántica

## Objetivo

Agrupar términos por campos semánticos y encontrar relaciones de significado.

## Nivel: Medio-Avanzado

## Corpus de trabajo

Glosario terminológico completo (terminologia_completa.json)


## Parte 1: Setup y modelo con vectores (10 min)

```python
import spacy
import json
from collections import defaultdict

# Usar modelo con vectores (md o lg)
# Nota: es_core_news_sm NO tiene vectores, necesitaron descargar modelo más grande
# Para este ejercicio, usamos vectores disponibles si existen, o método alternativo

try:
    nlp = spacy.load("es_core_news_md")
    print("Modelo md cargado (con vectores)")
except OSError:
    print("Modelo md no disponible. Usando modelo sm sin vectores.")
    print("Descargue modelo md: python -m spacy download es_core_news_md")
    nlp = spacy.load("es_core_news_sm")

# Cargar terminología
with open('terminologia_completa.json', 'r', encoding='utf-8') as f:
    terminologia = json.load(f)

sustantivos = list(terminologia['monolemas']['sustantivos'].keys())[:50]
print(f"Sustantivos cargados: {len(sustantivos)}")
```


## Parte 2: Cálculo de similitud entre pares (20 min)

**Tarea:** Calcular similitud semántica entre pares de términos.

```python
def calcular_similitud(termino1, termino2, nlp):
    """Calcula similitud semántica entre dos términos"""
    doc1 = nlp(termino1)
    doc2 = nlp(termino2)

    # Verificar que tienen vectores
    if doc1.has_vector and doc2.has_vector:
        return doc1.similarity(doc2)
    else:
        return None

# Calcular similitud entre pares de términos frecuentes
terminos_principales = ["influencer", "post", "tuitear", "viral", "plataforma"]

print("=== Similitud semántica entre términos ===")
for i, t1 in enumerate(terminos_principales):
    for t2 in terminos_principales[i+1:]:
        sim = calcular_similitud(t1, t2, nlp)
        if sim is not None:
            print(f"{t1:15} - {t2:15}: {sim:.3f}")
```


## Parte 3: Agrupación por campos semánticos (25 min)

**Tarea:** Encontrar términos similares y agruparlos por campos de significado.

```python
def encontrar_similares(termino, candidatos, nlp, top_n=5, umbral=0.5):
    """Encuentra términos similares a uno dado"""
    if not nlp(termino).has_vector:
        return []

    similitudes = []
    for cand in candidatos:
        if cand.lower() == termino.lower():
            continue

        doc_cand = nlp(cand)
        if not doc_cand.has_vector:
            continue

        sim = nlp(termino).similarity(doc_cand)
        if sim >= umbral:
            similitudes.append((cand, sim))

    # Ordenar por similitud
    similitudes.sort(key=lambda x: x[1], reverse=True)
    return similitudes[:top_n]

# Encontrar similares para términos principales
print("\n=== Términos similares por campo semántico ===")
camposSemanticos = {}

for termino in terminos_principales:
    similares = encontrar_similares(termino, sustantivos, nlp, top_n=5, umbral=0.4)
    camposSemanticos[termino] = similares

    print(f"\n[{termino.upper()}]")
    for similar, score in similares:
        print(f"  {similar:25} (sim: {score:.3f})")
```


## Parte 4: Método alternativo sin vectores (20 min)

**Tarea:** Si no hay modelo con vectores, usar contexto compartido como proxy de similitud.

```python
# Método alternativo: similitud por contexto compartido
# Dos términos son semánticamente similares si comparten colocaciones

def similitud_por_contexto(termino1, termino2, colocaciones):
    """Calcula similitud basada en colocaciones compartidas"""
    col1 = set(colocaciones.get(termino1, {}).keys())
    col2 = set(colocaciones.get(termino2, {}).keys())

    if not col1 or not col2:
        return 0.0

    # Coeficiente Jaccard
    interseccion = len(col1 & col2)
    union = len(col1 | col2)

    return interseccion / union if union > 0 else 0.0

# Calcular similitud por contexto
colocaciones = terminologia['colocaciones']

print("\n=== Similitud por contexto compartido (Jaccard) ===")
for i, t1 in enumerate(terminos_principales):
    for t2 in terminos_principales[i+1:]:
        sim = similitud_por_contexto(t1, t2, colocaciones)
        print(f"{t1:15} - {t2:15}: {sim:.3f}")
```


## Parte 5: Creación de campos semánticos (15 min)

**Tarea:** Agrupar términos en campos semánticos basándose en similitud.

```python
# Agrupar términos en campos semánticos
campos = defaultdict(list)

for termino in sustantivos:
    # Encontrar campo más cercano
    mejor_campo = None
    mejor_sim = 0.0

    for campo_rep in terminos_principales:
        sim = similitud_por_contexto(termino, campo_rep, colocaciones)
        if sim > mejor_sim and sim > 0.1:  # Umbral mínimo
            mejor_sim = sim
            mejor_campo = campo_rep

    if mejor_campo:
        campos[mejor_campo].append((termino, mejor_sim))

# Mostrar campos semánticos
print("\n=== Campos semánticos identificados ===")
for campo, terminos_campos in campos.items():
    print(f"\nCAMPO: {campo.upper()}")
    terminos_ordenados = sorted(terminos_campos, key=lambda x: x[1], reverse=True)
    for termino, sim in terminos_ordenados[:10]:
        print(f"  {termino:25} (sim: {sim:.3f})")
```


## Parte 6: Exportar campos semánticos (10 min)

**Tarea:** Guardar agrupación para uso posterior.

```python
# Crear estructura de campos semánticos
estructura_campos = {
    'campos': {},
    'metadatos': {
        'metodo': 'similitud_por_contexto',
        'umbral_minimo': 0.1,
        'terminos_totales': len(sustantivos),
        'campos_identificados': len(campos)
    }
}

for campo, terminos_campos in campos.items():
    estructura_campos['campos'][campo] = [
        {'termino': t, 'similitud': s}
        for t, s in sorted(terminos_campos, key=lambda x: x[1], reverse=True)
    ]

# Guardar
with open('campos_semanticos.json', 'w', encoding='utf-8') as f:
    json.dump(estructura_campos, f, ensure_ascii=False, indent=2)

print("\n=== Campos semánticos guardados ===")
print("Archivo: campos_semanticos.json")
print(f"Campos identificados: {len(campos)}")
for campo in campos.keys():
    print(f"  - {campo}: {len(campos[campo])} términos")
```


## Hacia la herramienta final

Este ejercicio construye:
- **Campos semánticos** que agrupan términos por significado
- **Estructura temática** del lenguaje digital
- **Base para organización** del glosario final por temas
- **Método reproducible** para clasificar nuevos términos

**Conexión con ejercicios anteriores:**
- Análisis terminológico: términos + frecuencias + colocaciones
- Similitud semántica: agrupación de términos por campos de significado

**Producto final:**
- `campos_semanticos.json`: términos organizados por campos temáticos

**Aplicación:**
- Glosario organizado por temas (no solo alfabético)
- Detección de polysemy (mismos términos en campos diferentes)
- Identificación de sinónimos dentro de cada campo

**Próximo paso:** Traducción automática - comparar calidad de TA en términos del glosario.
