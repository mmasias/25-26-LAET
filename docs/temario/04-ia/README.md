# Modelos de lenguaje de gran escala

## ¿Por qué?

La comunicación entre humanos y máquinas ha requerido históricamente que el humano aprenda el lenguaje de la máquina: comandos, sintaxis de programación, interfaces rígidas. Las máquinas no procesaban el lenguaje natural con eficacia, lo que relegaba el acceso a la tecnología a quienes dominaban ese lenguaje técnico.

Los modelos de lenguaje de gran escala invierten esa relación: es el sistema el que aprende a entender y producir lenguaje humano.

## ¿Qué?

Un **modelo de lenguaje de gran escala** (LLM, del inglés *large language model*) es un sistema de inteligencia artificial entrenado sobre cantidades masivas de texto para predecir cuál es el fragmento más probable dado un contexto. La intuición es la del autocompletado, pero a una escala y sofisticación radicalmente distintas.

La arquitectura dominante desde 2017 son los *transformers*, que permiten al modelo ponderar el contexto completo de una secuencia - no solo las palabras inmediatamente anteriores - para generar cada nuevo token.

Todo sistema LLM se articula en torno a tres componentes:

| Componente | Qué es | Ejemplo |
|---|---|---|
| **Datos** | El corpus de texto sobre el que se entrena el modelo; determina qué sabe y qué sesgos incorpora | Páginas web, libros, artículos, código fuente |
| **Algoritmo** | La arquitectura y el proceso de entrenamiento que extrae patrones del corpus | Transformer; aprendizaje sobre predicción de tokens |
| **Interfaz** | El producto a través del que el usuario interactúa con el modelo | ChatGPT, Gemini, Claude, Copilot; también APIs para desarrolladores |

La distinción importa: dos interfaces distintas pueden usar el mismo modelo subyacente, y el mismo modelo produce resultados distintos según los datos con que fue entrenado.

| Concepto | Descripción |
|---|---|
| **Token** | Unidad mínima de procesamiento: puede ser una palabra, una sílaba o un signo de puntuación |
| **Temperatura** | Parámetro que controla cuán predecible o creativa es la respuesta del modelo |
| **Alucinación** | Generación de texto plausible pero factualmente incorrecto, consecuencia estructural del funcionamiento estadístico |

## ¿Para qué?

Los LLMs eliminan la barrera del lenguaje técnico: cualquier persona puede acceder a capacidades avanzadas de análisis, generación y transformación de texto sin conocimientos especializados. Para el profesional de la lengua, esto abre un conjunto de tareas que regex y las herramientas de PLN no pueden abordar:

- Generación de texto con restricciones de registro, audiencia y estilo
- Traducción asistida con información de contexto y equivalencia funcional
- Análisis cualitativo de corpus sin reglas explícitas predefinidas
- Investigación terminológica con síntesis de múltiples fuentes

## ¿Cómo?

El laboratorio de esta sesión trabaja directamente con [Google AI Studio](https://aistudio.google.com), una interfaz que expone parámetros del modelo — temperatura, instrucciones de sistema — que las interfaces de uso general ocultan. Esa visibilidad permite observar el comportamiento del modelo de forma controlada y conectar cada fenómeno observado con su causa técnica.
