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

- Lingüista computacional
- Especialista en localización
- Terminólogo con automatización
- Gestor de contenido técnico

Existe una brecha visible entre la formación lingüística tradicional y lo que el mercado laboral demanda. Este curso aborda esa brecha de forma práctica.

## ¿Qué?

Las herramientas que integran el perfil tecnológico del profesional de la lengua forman parte de una disciplina consolidada: la **ingeniería lingüística**. Se trata del conjunto de métodos y sistemas que aplican técnicas computacionales al procesamiento, análisis y generación del lenguaje natural.

<div align=center>

![Mapa de la ingeniería lingüística](/images/modelosUML/ingenieria-linguistica.svg)

</div>

Las ramas marcadas en verde son las que cubren estos módulos y estas sesiones. Las restantes existen y tienen relevancia profesional; quedan fuera del alcance aquí, pero el mapa es útil para situar lo que se trabaja dentro de un contexto más amplio.

Tres de esas ramas articulan estos módulos:

<div align=center>

| Tecnología | Nivel de abstracción | Para qué sirve |
| --- | --- | --- |
| **Expresiones regulares** | Carácter y patrón | Limpiar y estructurar texto |
| **Procesamiento de Lenguaje Natural (PLN)** | Palabra y oración | Analizar y extraer información |
| **IA generativa** | Discurso y significado | Generar y transformar contenido |

</div>

La secuencia no es arbitraria: cada capa opera a un nivel de abstracción mayor y construye sobre la anterior.

## ¿Para qué?

- Visibilizar el mercado laboral real en el ámbito lingüístico-tecnológico
- Entender qué resuelve cada tecnología y en qué contexto conviene aplicarla
- Desarrollar criterio propio: ni tecnofilia acrítica ni tecnofobia paralizante

## ¿Cómo?

### El arco del curso

**Regex → PLN → IA generativa** no es una secuencia arbitraria. Cada tecnología resuelve un nivel distinto del problema:

1. **Regex** — opera sobre la forma del texto: caracteres, patrones, estructura superficial.
2. **PLN** — opera sobre el contenido lingüístico: morfología, sintaxis, entidades, significado.
3. **IA generativa** — opera sobre el sentido y la producción: genera, transforma, adapta.

La metáfora del iceberg es útil: regex trabaja en la superficie visible; PLN y la IA trabajan en capas cada vez más profundas.

### A day in the life

> Una editorial necesita crear ejercicios de vocabulario a partir de un corpus de artículos periodísticos.

Un flujo de trabajo profesional podría ser:

1. **Regex** → limpiar metadatos, URLs y ruido del corpus
2. **PLN** → extraer entidades, lemas y categorías gramaticales
3. **IA generativa** → generar ejercicios a partir de los términos extraídos
4. **Validación humana** → corregir, refinar y publicar

Cada paso produce un output que alimenta el siguiente. El profesional de la lengua diseña y supervisa el proceso; las herramientas lo ejecutan.

Un caso real de este tipo de flujo puede consultarse en: https://github.com/mmasias/u6-VII-traslation-project

## ¿Y ahora qué?

Herramientas que se utilizarán a lo largo del curso:

- [regexr.com](https://regexr.com/) — entorno visual para expresiones regulares
- [displaCy](https://explosion.ai/demos/displacy) — visualización de análisis PLN con spaCy
- [Claude](https://claude.ai) / [ChatGPT](https://chatgpt.com) — interfaces de IA generativa
