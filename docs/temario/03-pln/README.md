# Procesamiento del Lenguaje Natural

## ¿Por qué?

Las expresiones regulares operan sobre la **forma** del texto: detectan si una cadena termina en *-ing*, si empieza por mayúscula, si encaja en el patrón de una fecha. Son una herramienta quirúrgica y precisa, pero tienen un límite estructural: no saben qué es lo que han encontrado.

| Lo que regex puede responder | Lo que regex no puede responder |
|-|-|
| ¿Esta cadena termina en *-ing*? | ¿Es un sustantivo, un verbo o un modificador? |
| ¿Esta palabra empieza por mayúscula? | ¿Es un nombre propio, una sigla o el inicio de frase? |
| ¿Este fragmento tiene la forma de una fecha? | ¿A qué evento se refiere esa fecha? |
| ¿Esta secuencia coincide con el patrón de una URL? | ¿Es la fuente oficial o un enlace de spam? |

El **Procesamiento del Lenguaje Natural (PLN)** opera en el nivel siguiente: no sobre caracteres, sino sobre unidades lingüísticas con atributos: categoría gramatical, tipo de entidad, posición en la estructura de la oración, proximidad semántica con otros términos.

## ¿Qué?

El bloque trabaja tres capacidades fundamentales de los sistemas PLN modernos:

| Capacidad | Qué hace | Herramienta |
|-|-|-|
| **Reconocimiento de Entidades (NER)** | Identifica y clasifica unidades que representan objetos del mundo real: personas, organizaciones, lugares, fechas | spaCy |
| **Extracción terminológica y similitud semántica** | Detecta candidatos a término técnico mediante patrones morfosintácticos; calcula la cercanía de significado entre palabras mediante vectores | spaCy |
| **Evaluación de traducción automática** | Mide la coincidencia entre una traducción automática y una referencia humana; sistematiza la corrección de errores mediante post-edición | Python |

Los tres niveles responden a una progresión de abstracción creciente: de la **estructura** (qué función cumple cada token) al **concepto** (qué significan y cómo se relacionan) y a la **producción** (cómo evaluar y corregir lo que el sistema genera).

## ¿Para qué?

Para el profesional de la lengua, estas técnicas habilitan tareas que ya forman parte del trabajo en traducción, localización y gestión de contenido:

| Tarea | Técnica PLN implicada |
|-|-|
| Extraer automáticamente los actores de un corpus de noticias | NER |
| Detectar datos sensibles antes de publicar un documento | NER |
| Construir un glosario de candidatos a términos técnicos en un corpus especializado | Extracción terminológica |
| Encontrar el equivalente más natural de un término sin conocerlo de antemano | Similitud semántica |
| Decidir si el output de un motor de traducción es rentable de post-editar | Evaluación BLEU + PE |
| Identificar y categorizar errores léxicos, gramaticales o de registro en una traducción automática | Post-edición profesional |

## ¿Cómo?

Las tres sesiones utilizan **spaCy** sobre **Google Colab**, sin instalación local. Cada sesión sigue la misma estructura: introducción conceptual, demostración guiada, sección de auditoría crítica y reto con datos propios del alumno.

| Sesión | Tema | Contenido |
|-|-|-|
| [Sesión 1](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/03-pln/sesion1.ipynb) | NER y escala | La mirada de la máquina: cómo un modelo identifica entidades sin reglas explícitas. Límites del modelo y auditoría de errores. |
| [Sesión 2](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/03-pln/sesion2.ipynb) | Terminología y vectores | De la forma al concepto: extracción de términos complejos por patrones morfosintácticos y similitud semántica mediante representación vectorial. |
| [Sesión 3](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/03-pln/sesion3.ipynb) | Traducción automática | El principio detrás de BLEU: cómo los algoritmos puntúan traducciones y por qué esa puntuación puede engañar. Post-edición con etiquetado de errores. |

### Alcance del bloque

Este bloque no cubre tokenización ni POS tagging como temas independientes. Ambos conceptos aparecen de forma instrumental dentro de las sesiones (el POS tagger de spaCy se usa en la sesión 2 para detectar patrones morfosintácticos), pero no son el objeto de estudio. La decisión es de compresión curricular: el objetivo es que el alumno opere con las herramientas y desarrolle criterio profesional sobre sus resultados, no que domine la taxonomía completa del análisis morfosintáctico.
