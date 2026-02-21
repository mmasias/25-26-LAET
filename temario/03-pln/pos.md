# POS tagging y análisis gramatical

## ¿Por qué?

Analizar categorías gramaticales en corpus extensos manualmente es imposible. Se requiere identificación automática de sustantivos, verbos, adjetivos para estudios lingüísticos, creación de materiales didácticos y análisis de estilo.

## ¿Qué?

**POS tagging = etiquetar cada palabra con su categoría gramatical**

**Parser sintáctico = identificar estructura de oraciones**

## ¿Para qué?

- Análisis contrastivo de corpus (uso de adjetivos en registro formal vs informal)
- Generación de ejercicios gramaticales específicos
- Análisis de complejidad sintáctica
- Filtrado de términos por categoría (solo sustantivos para glosarios)

## ¿Para qué?

- Frecuencias de categorías gramaticales
- Extracción de patrones sintácticos
- Identificación de estructuras complejas

## ¿Cómo?

**spaCy** - Etiquetado gramatical automático

Demo: texto → etiquetas POS → análisis

**Ellos interpretan las categorías** (lingüistas validando los resultados automáticos)

**Ejercicio:** Analizar corpus de ensayos estudiantiles → identificar patrones de error gramatical

**Visualización:** árboles sintácticos con displaCy

**Categorías principales:**

- NOUN: Sustantivo
- VERB: Verbo
- ADJ: Adjetivo
- ADV: Adverbio
- PROPN: Nombre propio
- DET: Determinante
- ADP: Preposición
- PRON: Pronombre
