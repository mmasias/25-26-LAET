# Ejercicio de Traducción Automática y Post-edición

## Objetivo

Evaluar y corregir traducciones automáticas de términos del glosario digital.

## Nivel: Medio

## Corpus de trabajo

Muestra de 20 términos del glosario con sus definiciones


## Parte 1: Selección de muestra (10 min)

```python
import json
import random

# Cargar glosario completo
with open('terminologia_completa.json', 'r', encoding='utf-8') as f:
    glosario = json.load(f)

# Seleccionar 20 términos representativos
todos_terminos = list(glosario['monolemas']['sustantivos'].keys())
terminos_muestra = random.sample(todos_terminos, min(20, len(todos_terminos)))

print("=== Términos seleccionados para análisis ===")
for i, term in enumerate(terminos_muestra, 1):
    freq = glosario['monolemas']['sustantivos'][term]
    print(f"{i:2}. {term:25} (frec: {freq})")
```


## Parte 2: Traducción con herramientas automáticas (20 min)

**Tarea:** Traducir términos y definiciones usando DeepL y Google Translate.

```python
# Crear archivo con términos para traducir
with open('terminos_traducir.txt', 'w', encoding='utf-8') as f:
    for termino in terminos_muestra:
        # Buscar contexto del término en el corpus
        f.write(f"Término: {termino}\n")
        f.write(f"Contexto típico: [buscar en corpus]\n")
        f.write(f"Definición propuesta: [escribir manualmente]\n")
        f.write("\n")

print("Archivo creado: terminos_traducir.txt")
print("\nINSTRUCCIONES:")
print("1. Copiar términos al traductor automático (DeepL o Google Translate)")
print("2. Traducir del español al inglés")
print("3. Copiar resultados al archivo 'traduccion_TA.csv'")
```


## Parte 3: Análisis comparativo (25 min)

**Tarea:** Comparar traducciones de diferentes herramientas y detectar patrones de error.

```python
import csv

# Template para análisis comparativo
# Crear CSV para registrar resultados

with open('analisis_traduccion.csv', 'w', newline='', encoding='utf-8') as f:
    writer = csv.writer(f)
    writer.writerow([
        'Termino_ES',
        'Traduccion_DeepL',
        'Traduccion_Google',
        'Traduccion_Humana',
        'Error_DeepL',
        'Error_Google',
        'Tipo_Error',
        'Correccion'
    ])

    print("=== Plantilla de análisis creada ===")
    print("Archivo: analisis_traduccion.csv")
    print("\nTipos de error a buscar:")
    print("- CALQUE: traducción literal de expresión fija")
    print("- FALSE_FRIEND: amigo falso no detectado")
    print("- NEOLOGISM: neologismo no traducido (dejar en original)")
    print("- WRONG_REGISTER: registro inadecuado")
    print("- OMISSION: información perdida")
    print("- CULTURAL: adaptación cultural necesaria")
```


## Parte 4: Detección automática de errores (20 min)

**Tarea:** Script para identificar potenciales errores de traducción.

```python
import spacy

nlp_es = spacy.load("es_core_news_sm")

# Indicadores automáticos de problemas de traducción

def detectar_potenciales_problemas(traduccion_es, traduccion_en):
    """Detecta potenciales problemas en traducción"""
    problemas = []

    # 1. Anglicismo sin traducir (palabra en inglés en texto español)
    doc_es = nlp_es(traduccion_es)
    for token in doc_es:
        # Detección simple de palabras en inglés
        if token.text.isalpha() and len(token.text) > 3:
            # Verificar si contiene patrones típicos del inglés
            if any(token.text.endswith(suf) for suf in ['ing', 'ion', 'ment', 'ness']):
                if not any(token.text.lower() == w for w in ['traducción', 'publicación', 'documento']):
                    problemas.append(f"Posible anglicismo sin traducir: {token.text}")

    # 2. Longitud muy diferente (puede indicar omisión)
    len_es = len(traduccion_es.split())
    len_en = len(traduccion_en.split())
    if abs(len_es - len_en) / max(len_es, len_en) > 0.5:
        problemas.append(f"Diferencia de longitud: ES={len_es}, EN={len_en}")

    return problemas

# Ejemplo de uso
print("\n=== Detección automática de problemas ===")
print("Función definida. Usar con cada par de traducciones.")
```


## Parte 5: Ejercicio de post-edición (25 min)

**Tarea:** Post-editar traducciones automáticas para alcanzar calidad humana.

```python
# Ejercicio práctico de post-edición
ejemplos_postedicion = [
    {
        'original': 'influencer',
        'contexto': 'Los influencers promocionan productos en redes sociales',
        'TA': 'influencer',
        'pregunta': '¿Es aceptable "influencer" en inglés o hay traducción?',
        'opciones': ['influencer', 'influenciador', 'líder de opinión', 'celebridad digital']
    },
    {
        'original': 'postear',
        'contexto': 'Voy a postear esto en mi muro',
        'TA': 'to post',
        'pregunta': '¿Verbo adecuado o need calque?',
        'opciones': ['to post', 'to publish', 'to upload', 'to share']
    },
    {
        'original': 'viralizar',
        'contexto': 'El video se viralizó en horas',
        'TA': 'to viralize',
        'pregunta': '¿Existente en inglés o neologismo?',
        'opciones': ['to go viral', 'to viralize', 'to become viral', 'to trend']
    }
]

print("=== Ejemplos para post-edición ===")
for i, ej in enumerate(ejemplos_postedicion, 1):
    print(f"\nEjemplo {i}: {ej['original']}")
    print(f"Contexto: {ej['contexto']}")
    print(f"TA propuesta: {ej['TA']}")
    print(f"Pregunta: {ej['pregunta']}")
    print(f"Opciones:")
    for j, op in enumerate(ej['opciones'], 1):
        print(f"  {j}. {op}")
```


## Parte 6: Creación de glosario bilingüe (10 min)

**Tarea:** Compilar glosario final con traducciones validadas.

```python
# Estructura del glosario bilingüe
glosario_bilingue = {
    'metadatos': {
        'fecha': '2025-01-XX',
        'idioma_origen': 'es',
        'idioma_destino': 'en',
        'metodo_traduccion': 'TA + post-edición',
        'terminos_totales': len(terminos_muestra)
    },
    'entradas': []
}

# Template para cada entrada
print("\n=== Estructura del glosario bilingüe ===")
print("Cada entrada contiene:")
print("{")
print('  "termino_es": "influencer",')
print('  "traduccion_TA": "influencer",')
print('  "traduccion_final": "influencer",')
print('  "contexto": "Los influencers promocionan...",')
print('  "justificacion": "Anglicismo aceptado, documento Oxford English Dictionary",')
print('  "categoria": "sustantivo",')
print('  "frecuencia": 47')
print("}")

# Guardar template
with open('glosario_bilingue_template.json', 'w', encoding='utf-8') as f:
    json.dump(glosario_bilingue, f, ensure_ascii=False, indent=2)

print("\nTemplate guardado en: glosario_bilingue_template.json")
```


## Parte 7: BONUS - Evaluación de calidad (10 min)

**Tarea:** Calcular métricas de calidad de traducción automática.

```python
# Métricas de evaluación
metricas = {
    'terminos_analizados': len(terminos_muestra),
    'aceptados_sin_cambios': 0,  # Llenar manualmente
    'correcciones_menores': 0,    # Cambios de 1-2 palabras
    'correcciones_mayores': 0,    # Cambios significativos
    'retraducciones_completas': 0 # TA inútil
}

print("=== Métricas de calidad TA ===")
print("Registrar después de post-edición:")
for key, value in metricas.items():
    print(f"  {key}: {value}")

# Calcular porcentaje de aceptación
# aceptacion = metricas['aceptados_sin_cambios'] / metricas['terminos_analizados']
# print(f"\nTasa de aceptación: {aceptacion*100:.1f}%")
```


## Hacia la herramienta final

Este ejercicio construye:
- **Glosario bilingüe** con traducciones validadas humanamente
- **Catálogo de errores típicos** de TA en lenguaje digital
- **Consciencia crítica** de limitaciones de herramientas TA
- **Workflow profesional**: TA → post-edición → validación

**Conexión con ejercicios anteriores:**
- Todos los ejercicios PLN anteriores: glosario monolingüe español
- Traducción automática: añadir dimensión bilingüe

**Producto final:**
- `glosario_bilingue.json`: términos ES + traducciones EN validadas

**Aplicación profesional:**
- Traducción especializada en tecnología/digital
- Localización de contenido sobre redes sociales
- Comprensión de limitaciones de TA en neologismos

**Fin del bloque PLN** - Ahora se tiene glosario completo bilingüe con:
- Extracción automática de términos
- Clasificación gramatical
- Análisis de contexto y colocaciones
- Campos semánticos
- Traducciones validadas

**Próximo paso:** Bloque IA generativa - usar prompts para generar contenido con el glosario.
