# Ejercicio Regex aplicado

## Objetivo

Aplicar regex en Google Sheets a un corpus más grande (200 documentos) y construir una tabla de candidatos a términos con frecuencias.

## Nivel: Medio

## Corpus de trabajo

Google Sheet con 200 tweets/posts sobre lenguaje digital.


## Parte 1: Configuración del Sheet (10 min)

**Estructura:**
- Columna A: ID del documento (1-200)
- Columna B: Texto limpio (resultado del ejercicio anterior)


## Parte 2: Extracción de candidatos a términos (50 min)

**Tareas (elegir al menos 3):**

1. **Anglicismos terminados en -ing, -er, -or**
   - Celda C2: `=REGEXEXTRACT(B2; "\b[a-zA-Z]+(ing|er|or)\b")`
   - Aplicar a toda la columna con ARRAYFORMULA

2. **Palabras entre comillas** (términos citados como tales)
   - Celda D2: `=REGEXEXTRACT(B2; "\"([^\"]+)\"")`

3. **Palabras en mayúsculas** (siglas, acrónimos)
   - Celda E2: `=REGEXEXTRACT(B2; "\b[A-ZÁÉÍÓÚÑ]{2;}\b")`

4. **Palabras compuestas con guión**
   - Celda F2: `=REGEXEXTRACT(B2; "\b[a-záéíóúñ]+-[a-záéóúñ]+\b")`

**Formato de entrega:**

| ID | Texto | Anglicismos | Citas | Mayúsculas | Compuestos |
|----|-------|------------|-------|-----------|------------|
| 1 | ... | influencing | "cancelar" | COVID | post-pandemia |
| 2 | ... | | | | |


## Parte 3: Análisis de frecuencias (20 min)

**Tarea:** Contar frecuencias de términos extraídos.

1. Crear pestañas por cada tipo de término (anglicismos, citas, etc.)
2. Usar `COUNTIF` o tablas dinámicas para obtener frecuencias
3. Ordenar por frecuencia descendente


## Hacia la herramienta final

Este ejercicio construye:
- **Tabla de candidatos** con frecuencias
- **Filtrado por tipos** (puedes elegir solo sustantivos después)
- **Base para análisis** PLN (próxima sesión)

**Conexión con ejercicio anterior:** El corpus limpio de Regex básico es el input para este ejercicio.
