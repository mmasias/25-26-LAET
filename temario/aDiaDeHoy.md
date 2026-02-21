# A día de hoy deberíamos saber

> *Entiéndase "deberíamos saber" como una combinación de "nos debería sonar", "no nos debería sorprender", "deberíamos conocer", "deberíamos saber manejar", en función del tema abordado. En cualquier caso, lo mínimo es "no nos debería sorprender" y deberíamos poder tener una mínima conversación o lectura sobre estos temas.*

## Regex

- Expresión regular = lenguaje de patrones para buscar/extraer texto
- Metacaracteres básicos (`.` `\d` `\w` `\s` `[]` `*` `+` `?` `{}`)
- Herramientas: regexr.com (visual), hojas de cálculo (aplicado), Python (automatización)
- Cuándo NO usar regex: para análisis gramatical, HTML completo, JSON

## PLN (Procesamiento de Lenguaje Natural)

- Tokenización ≠ dividir por espacios (spaCy maneja puntuación, contracciones)
- Lematización ≠ lowercasing (lema es forma base de diccionario)
- POS tagging: clasificación gramatical automática (sustantivo, verbo, adjetivo)
- NER: reconocimiento de entidades (personas, lugares, organizaciones)
- spaCy: modelo estadístico, puede fallar, validación humana necesaria

## IA generativa

- LLMs predicen siguiente token, no "razonan" realmente
- Temperature: 0 = determinista, 1 = creativo
- Alucinaciones: inventan información plausible pero falsa
- Ventana de contexto: memoria limitada de la conversación
- Sesgos: reproducen prejuicios del corpus de entrenamiento
- Prompting: calidad de output depende 90% de calidad de prompt

## Traducción automática

- DeepL/Google: traducción automática, útil para primer borrador
- Post-edición: humano corrige máquina, workflow profesional estándar
- Errores típicos: calques, amigos falsos, pérdida de registro, omisiones
- IA generativa vs TA: LLM mejor para contexto cultural, TA más consistente

## Ética profesional

- Tecnología no es neutra: tiene sesgos y limitaciones
- Propiedad intelectual: contenido generado por IA ¿es de quién?
- Transparencia: ¿declarar uso de IA en trabajos académicos?
- Responsabilidad: humano es último filtro de validación
- Brecha digital: herramientas requieren acceso y conocimientos técnicos