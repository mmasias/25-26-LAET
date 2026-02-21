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
| Aplicado | Hojas de cálculo | Extracción de candidatos a términos |
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

- **Error:** Confundir `.` con punto literal
  - **Solución:** Usar `\.` para punto literal, `.` para cualquier carácter
- **Error:** No usar cuantificadores correctamente
  - **Solución:** `*` (0 o más), `+` (1 o más), `?` (0 o 1), `{n}` (exactamente n)
- **Error:** Copy-paste sin comprender
  - **Solución:** Desglosar cada parte del regex en regexr.com antes de usar

### PLN

- **Error:** Confundir token con palabra
  - **Solución:** Token es unidad lingüística (puede incluir puntuación adjunta)
- **Error:** Confundir lema con lowercasing
  - **Solución:** Lema es forma base de diccionario (cantar → cantar), no solo minúsculas
- **Error:** Olvidar procesar con nlp() antes de usar
  - **Solución:** Siempre `doc = nlp(texto)` antes de acceder a propiedades

### IA generativa

- **Error:** Antropomorfizar el LLM ("entiende que...")
  - **Solución:** Recordar que predice tokens, no "entiende"
- **Error:** Confianza ciega en las salidas
  - **Solución:** Verificar factualmente, especialmente fechas, nombres, datos
- **Error:** Prompts demasiado vagos
  - **Solución:** Incluir rol, contexto, tarea, formato, restricciones

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
- [WebLicht](https://weblicht.hu-berlin.de/) - Herramienta web para análisis lingüístico

### IA generativa
- [ChatGPT](https://chat.openai.com)
- [Claude](https://claude.ai)
- [Gemini](https://gemini.google.com)
- [Cursos prompting](https://www.deeplearning.ai/short-courses/)
- [MT-Bench](https://github.com/lm-sys/FastChat/tree/main/mt-bench) - Benchmark de modelos
- [HELM](https://crfm.stanford.edu/helm/latest/) - Evaluación holística de modelos
