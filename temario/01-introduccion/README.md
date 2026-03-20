# Contexto y fundamentos

## ¿Por qué?

El perfil del graduado en lenguas ha cambiado drásticamente. Empresas e instituciones demandan profesionales que no solo dominen idiomas, sino que sepan trabajar con herramientas tecnológicas:

<div align=center>

|Corpus lingüísticos|Traducción asistida|Análisis de datos|IA generativa|
|-|-|-|-|
|<sub>Colecciones de textos reales usadas para analizar el lenguaje en contexto|<sub>Herramientas que combinan memoria de traducción, terminología y automatización|<sub>Extracción de patrones y métricas a partir de grandes volúmenes de texto|<sub>Sistemas capaces de generar, transformar y adaptar contenido lingüístico|

</div>

La tecnología no es neutra. Quien no comprende estas herramientas se convierte en usuario pasivo, con opciones profesionales limitadas. Quien las domina puede diseñar procesos eficientes, ofrecer servicios de mayor valor y adaptarse a un mercado en constante cambio.

### El profesional de la lengua hoy

Un recorrido por las ofertas de empleo actuales en traducción, localización y gestión de contenido revela una constante: junto a la competencia lingüística, se exigen capacidades técnicas. Términos como *corpus*, *NLP*, *herramientas CAT*, *automatización* o *IA generativa* aparecen con creciente frecuencia en perfiles como:

|Perfil|Qué hace|
|-|-|
|***Lingüista computacional***|Diseña y entrena sistemas que procesan lenguaje: clasificadores, extractores, modelos de traducción|
|***Especialista en localización***|Adapta productos digitales a mercados locales: interfaz, contenido, culturalización|
|***Terminólogo con automatización***|Construye y mantiene bases terminológicas; extrae términos de corpus con herramientas NLP|
|***Gestor de contenido técnico***|Produce y estructura documentación técnica, a menudo con asistencia de IA generativa|

Existe una brecha visible entre la formación lingüística tradicional y lo que el mercado laboral demanda. Estas sesiones abordan esa brecha de forma práctica.

## ¿Qué?

Las herramientas que integran el perfil tecnológico del profesional de la lengua forman parte de una disciplina consolidada: la **ingeniería lingüística**. Se trata del conjunto de métodos y sistemas que aplican técnicas computacionales al procesamiento, análisis y generación del lenguaje natural.

<div align=center>

![Mapa de la ingeniería lingüística](/images/modelosUML/ingenieria-linguistica.svg)

</div>

Las ramas marcadas en verde son las que cubren estos módulos y estas sesiones. Las restantes existen y tienen relevancia profesional; quedan fuera del alcance aquí, pero el mapa es útil para situar lo que se trabaja dentro de un contexto más amplio.

Tres de esas ramas articulan el contenido:

<div align=center>

|Tecnología|Qué es|
|-|-|
|**Expresiones regulares**|Lenguaje formal para describir y localizar patrones en texto|
|**Procesamiento de Lenguaje Natural (PLN)**|Conjunto de técnicas para que los sistemas analicen y comprendan lenguaje humano|
|**IA generativa**|Sistemas capaces de producir texto nuevo a partir de grandes modelos de lenguaje|

</div>

Conocer estas herramientas no es un fin en sí mismo — es lo que habilitan lo que importa.

## ¿Para qué?

Estas herramientas habilitan tareas que forman parte del trabajo profesional real en el ámbito lingüístico:

- Limpiar y preparar corpus para análisis o traducción
- Extraer terminología, entidades y patrones de grandes volúmenes de texto
- Automatizar partes del flujo de traducción y post-edición
- Generar contenido lingüístico: ejercicios, resúmenes, adaptaciones de registro
- Evaluar críticamente herramientas y sus limitaciones, en lugar de usarlas como cajas negras

## ¿Cómo?

### El arco del contenido

El contenido se organiza en tres bloques: expresiones regulares, procesamiento de lenguaje natural e IA generativa. La secuencia no es arbitraria: cada tecnología opera a un nivel de abstracción distinto y mayor.

<div align=center>

|Tecnología|Nivel de abstracción|Opera sobre|Qué tocaremos|
|-|-|-|-|
|**Expresiones regulares**|Carácter y patrón|Forma superficial del texto|Detectar fechas, limpiar URLs, extraer menciones — en regexr.com, Google Sheets y Python|
|**Procesamiento de Lenguaje Natural (PLN)**|Palabra y oración|Contenido lingüístico: morfología, sintaxis, entidades|Tokenizar, etiquetar categorías gramaticales, reconocer entidades — con spaCy en Google Colab|
|**IA generativa**|Discurso y significado|Sentido, contexto y producción|Generar ejercicios, reescribir en otro registro, traducir con contexto cultural — con Claude, ChatGPT y Gemini|

</div>

Cada capa construye sobre la anterior. La tabla describe niveles; el siguiente caso muestra cómo esos niveles se encadenan en un flujo de trabajo real.

### A day in the life

> Una editorial necesita crear ejercicios de vocabulario a partir de un corpus de artículos periodísticos.

Un flujo de trabajo profesional podría ser:

<table>
<tr><td valign=top>

1. **Regex** → limpiar metadatos, URLs y ruido del corpus
1. **PLN** → extraer entidades, lemas y categorías gramaticales
1. **IA generativa** → generar ejercicios a partir de los términos extraídos
1. **Validación humana** → corregir, refinar y publicar
</td><td>

![](/images/modelosUML/day-in-the-life-teorico.svg)
</td></tr>
</table>

Cada paso produce un output que alimenta el siguiente. El profesional de la lengua diseña y supervisa el proceso; las herramientas lo ejecutan.

> Este flujo es la versión ordenada. Pero, [*is this the real life?*](articulos/day-in-the-life-real.md)

## ¿Y ahora qué?

Herramientas que se utilizarán a lo largo de estas sesiones:

|Expresiones regulares|PLN|Traducción|IA generativa|
|:-:|:-:|:-:|:-:|
[regexr.com](https://regexr.com/)<br><sub>entorno visual e interactivo para construir y probar patrones|[Google Colab](https://colab.research.google.com)<br><sub>entorno Python en el navegador, sin instalación|[DeepL](https://www.deepl.com)<br><sub>traducción automática neural, referencia en el sector profesional|[Claude](https://claude.ai)<br><sub>LLM de Anthropic; fuerte en análisis de documentos y contexto largo
[Google Sheets](https://sheets.google.com)<br><sub>hojas de cálculo con funciones regex nativas|[spaCy](https://spacy.io)<br><sub>biblioteca de PLN; se ejecuta en Colab|[Google Translate](https://translate.google.com)<br><sub>traducción automática de referencia generalista|[ChatGPT](https://chatgpt.com)<br><sub>LLM de OpenAI; fuerte en razonamiento y tareas complejas
[Google Docs](https://docs.google.com)<br><sub>buscar y reemplazar con expresiones regulares|[displaCy](https://explosion.ai/demos/displacy)<br><sub>visualización interactiva de análisis PLN||[Le Chat](https://chat.mistral.ai)<br><sub>LLM de Mistral; modelo europeo de referencia

### Referencia

- [Caso real: u6-VII-traslation-project](https://github.com/mmasias/u6-VII-traslation-project) — flujo lingüístico-tecnológico aplicado
