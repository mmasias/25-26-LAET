# Síntesis pedagógica del curso

## Visión general

**Curso:** Lingüística aplicada a la educación y a la tecnología

**Duración:** ~15-20 sesiones de 2 horas

**Estudiantes:** Falsos principiantes en tecnología
- Perfil: Lingüística (traducción, enseñanza de lenguas)
- Brecha digital: Máximo ofimática
- Actitud inicial: "La tech es otro mundo"

## Estructura del curso

### Bloque 0: Contexto y fundamentos (1 sesión)

**Contenido:** Presentación del profesional de la lengua en la era de la informática, estado del arte, demo en vivo de regex + PLN + IA

### Bloque 1: Regex (3 sesiones)

| Sesión | Herramienta | Contenido |
|--------|-------------|----------|
| Básico | regexr.com | Limpieza de corpus |
| Aplicado | Google Sheets | Extracción de candidatos a términos |
| Avanzado | Python/Colab | Extracción de todas las coincidencias, límites |

### Bloque 2: PLN (5 sesiones)

| Sesión | Contenido |
|--------|----------|
| Tokenización + normalización | spaCy: división en palabras/oraciones, lematización |
| POS tagging + NER | Clasificación gramatical, reconocimiento de entidades |
| Análisis terminológico | Frecuencias, contextos, colocaciones |
| Similitud semántica | Agrupación de términos por significado |
| Traducción automática | Evaluación crítica, post-edición |

### Bloque 3: IA generativa (6 sesiones)

| Sesión | Contenido |
|--------|----------|
| Fundamentos | LLMs: cómo funcionan, límites |
| Prompting básico | Estructura de prompts efectivos |
| Prompting avanzado | Técnicas complejas: few-shot, chain-of-thought |
| Traducción/localización | Uso de LLMs en traducción |
| Creación de contenido didáctico | Generación de materiales con IA |
| Evaluación crítica + ética | Límites, sesgos, responsabilidad profesional |

## Progresión de herramientas

### Regex
regexr.com → Google Sheets → Python/Colab
(visual) (corpus real) (automatización)

### PLN
spaCy demo → Colab notebooks → Scripts automatizados
(web) (aprendizaje) (producción)

### IA generativa
ChatGPT web → Prompting estructurado → API + Python
(básico) (efectivo) (automatizado)

## Secuenciación de sesiones

Patrón típico de sesión (120 min):

- Introducción del problema real
- ¿Por qué? ¿Qué? ¿Para qué? ¿Cómo?
- Demostración en vivo
- Práctica autónoma
- Cierre + conexión siguiente sesión

## Entregas y evaluación

**Construcción progresiva:** Cada entrega se conecta con las anteriores

| Entrega | Artefacto |
|---------|-----------|
| 001-003 | Documentos/Scripts de regex |
| 004-008 | Notebooks de PLN |
| 009-014 | Prompts y contenido generado |

**Criterio:** Explicación a terceros (podrías explicarle esto a un compañero que no vino)

## Errores frecuentes por bloque

### Regex
- Confundir `.` con punto literal
- No usar cuantificadores correctamente
- Copy-paste sin comprender

### PLN
- Confundir token con palabra
- Confundir lema con lowercasing
- Olvidar procesar con nlp() antes de usar

### IA generativa
- Antropomorfizar el LLM ("entiende que...")
- Confianza ciega en las salidas
- Prompts demasiado vagos

## Recursos por bloque

### Regex
- [regexr.com](https://regexr.com/)
- [RegexOne](https://regexone.com/)
- [Google Sheets funciones regex](https://support.google.com/docs/answer/9325625)

### PLN
- [spaCy](https://spacy.io/)
- [Modelos spaCy español](https://spacy.io/models/es)
- [Curso spaCy](https://course.spacy.io/)
- [displaCy demo](https://explosion.ai/demos/displacy)

### IA generativa
- [ChatGPT](https://chat.openai.com)
- [Claude](https://claude.ai)
- [Gemini](https://gemini.google.com)
- [Cursos prompting](https://www.deeplearning.ai/short-courses/)
