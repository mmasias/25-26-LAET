# Regex avanzado: Python y Colab

## ¿Por qué?

Regex en regexr.com, Google Docs y Google Sheets es suficiente para explorar patrones y procesar documentos individuales. No es suficiente para trabajar con un corpus real: cientos o miles de fragmentos, análisis de frecuencia, extracción sistemática, resultados exportables. Para eso hace falta un lenguaje de programación.

> *No es una idea nueva. Cuando Ken Thompson implementó regex en los años 60, lo hizo precisamente para procesar texto programáticamente. El entorno natural de regex siempre ha sido un lenguaje: primero `sed` y `awk` en Unix, después Perl, que en 1987 convirtió regex en su característica definitoria y los popularizó entre programadores de todo el mundo. Desde entonces, prácticamente todos los lenguajes de uso general los implementan: Java, R, JavaScript, Ruby, Go.*

Python es uno más de esa lista, con una ventaja relevante para este contexto: su sintaxis es notablemente más legible que la de Perl o awk, y su ecosistema de herramientas lingüísticas (spaCy, NLTK, Gensim) lo ha convertido en el estándar de facto del PLN. El salto de Sheets a Python no es un salto a "programar": es un salto al entorno donde regex tiene toda su potencia y donde las herramientas del bloque siguiente están disponibles.

Ese salto permite cosas que las herramientas anteriores no tienen:

| Capacidad | Por qué importa |
|---|---|
| Leer ficheros externos | El corpus no hace falta pegarlo a mano: se carga desde un archivo |
| Guardar resultados | Las listas de términos y frecuencias se exportan directamente |
| Encadenar operaciones | Limpiar, extraer y contar en una sola ejecución |
| Conectar con PLN | Los resultados de regex son la entrada natural a herramientas de análisis lingüístico |

Las dos sesiones anteriores también dejaron tres tareas sin resolver, no por falta de patrón sino por límites del motor de Sheets:

**Los emojis**: no existe un patrón para "cualquier emoji" en RE2, el motor que usan las herramientas de Google. El problema no era el patrón: era la herramienta.

**Las referencias retrospectivas**: el patrón `\b(\w+) \1\b` detecta palabras duplicadas (*"de de"*, *"crece crece"*…), pero RE2 no admite `\1` por razones de eficiencia computacional.

**La frecuencia**: `REGEXEXTRACT` devuelve la primera coincidencia por celda. Obtener el listado completo de términos ordenado por frecuencia era estructuralmente imposible en una hoja.

Python resuelve los tres. Y son el hilo conductor de los cinco notebooks de esta sesión.

## ¿Qué?

Los mismos patrones. Un motor distinto.

El módulo `re` de Python usa un motor diferente al de Google Sheets. Los patrones aprendidos funcionan sin modificación; lo que cambia es lo que el motor puede hacer con ellos:

<div align=center>

| | Google Sheets (RE2) | Python (`re`) |
|---|:-:|:-:|
| Referencias retrospectivas (`\1`) | No admitido | Admitido |
| Rangos Unicode / emojis | Parcial | Completo |
| Coincidencias por llamada | Primera por celda | Todas, en el corpus completo |
| Análisis de frecuencia | Manual (COUNTIF + SUM) | `Counter` en una línea |

</div>

El corpus deja de ser 25 celdas independientes y pasa a ser un único objeto de texto. Eso no es solo comodidad: cambia qué preguntas se pueden formular.

## ¿Para qué?

Las tres operaciones de la sesión anterior (limpiar, extraer, normalizar) ahora funcionan a escala de corpus:

| Operación | En Sheets | En Python |
|---|---|---|
| Extraer términos | Uno por fila, luego manual | Todos a la vez, con frecuencia |
| Detectar palabras duplicadas | El patrón no funciona en RE2 | `\b(\w+) \1\b` funciona |
| Extraer emojis | Listando cada uno a mano | Rango Unicode sistemático |
| Normalizar fechas | Una fórmula por columna | Una sustitución sobre el corpus entero |
| Rankear por frecuencia | Imposible directamente | `Counter.most_common()` |

Al final del bloque se dispone de un script que, dado cualquier corpus de texto, extrae todos los términos y los ordena por frecuencia de aparición. Ese listado es el punto de entrada natural al análisis terminológico con herramientas de PLN.

## ¿Cómo?

El trabajo se articula en cinco notebooks de Google Colab, uno por fase. Cada notebook es autónomo: incluye el corpus y todo el código necesario. No hace falta instalar nada ni configurar ningún entorno.

Antes de abrir el primero, conviene leer el marco pedagógico que orienta la progresión: [Acerca de](../disclaimer.md). Explica qué se espera en cada fase y qué no se espera en ninguna.

<div align=center>

| Notebook | Fase | Qué se hace |
|---|:-:|---|
| [00 - Entorno](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/02-regex/colab-00-entorno.ipynb) | Orientación | Reconocer el entorno: celdas de texto, celdas de código, output. Ejecutar tres celdas. |
| [01 - Leer](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/02-regex/colab-01-leer.ipynb) | Leer y ejecutar | El código está escrito. Se ejecuta y se responde: ¿qué devuelve esto, y por qué? |
| [02 - Modificar](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/02-regex/colab-02-modificar.ipynb) | Modificar una línea | Tres tareas, cada una con una línea marcada para cambiar. El resto no se toca. |
| [03 - Completar](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/02-regex/colab-03-completar.ipynb) | Completar huecos | Tres tareas con huecos explícitos (`___`). Un hueco por tarea. |
| [04 - Construir](https://colab.research.google.com/github/mmasias/25-26-LAET/blob/main/docs/temario/02-regex/colab-04-construir.ipynb) | Construir desde plantilla | Código completo, tarea lingüística. Patrón libre sobre el corpus o sobre uno propio. |

</div>

La separación entre celdas de texto y celdas de código en Colab resuelve una tensión del enfoque: el código queda limpio, la explicación queda en las celdas de texto. Para saber qué hace un bloque no hace falta leer Python: la celda anterior lo dice en lenguaje natural.
