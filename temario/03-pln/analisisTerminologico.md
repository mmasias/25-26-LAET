# Análisis terminológico

## ¿Por qué?

La terminología especializada cambia constantemente. Identificar y extraer términos técnicos de forma manual en corpus grandes es inviable. Se necesita automatización para mantener glosarios actualizados.

## ¿Qué?

**Extracción de términos, frecuencias, contextos y colocaciones.**

Análisis de cómo los términos se usan realmente en corpus especializados.

## ¿Para qué?

- Construcción de glosarios especializados
- Identificación de neologismos
- Análisis de variación terminológica
- Extracción de candidatos para traducción técnica

## ¿Cómo?

**spaCy + análisis de n-gramas**

Corpus → términos candidatos → frecuencias → contextos → colocaciones

**Ejercicio:** Corpus de artículos científicos → extracción de términos técnicos + análisis de frecuencias por campo

**Validación humana:** filtrar ruido y confirmar términos relevantes
