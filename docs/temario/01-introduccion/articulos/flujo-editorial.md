# El flujo en acción: un ejemplo completo

> Una editorial necesita crear ejercicios de vocabulario a partir de un corpus de artículos periodísticos sobre lenguaje contemporáneo.

Lo que sigue muestra el mismo corpus atravesando cada estado del flujo. No es una descripción del proceso - es el proceso con datos reales.

## Estado 1: Corpus original

Tres fragmentos extraídos de publicaciones digitales. Tal como llegan.

```
CULTURA | LENGUAJE | 14/03/2024
Por: Redacción | redaccion@diario.es | https://diario.es/cultura/neologismos-2024

El fenómeno "phubbing" -ignorar a quien tienes delante por mirar el teléfono- ha pasado
de anglicismo minoritario a candidato en el diccionario de la RAE. Lingüistas consultados
por este diario señalan que la velocidad de adopción es "sin precedentes en la historia
reciente del español". #Neologismos #LenguajeDigital https://t.co/xyz789

[CONTINÚA EN PÁGINA 12] [Publicado: 14-03-2024 08:32] [Actualizado: 14-03-2024 11:15]
```

```
SOCIEDAD | 21/11/2023
Autor: María Fernández (m.fernandez@revista.com)

La palabra "sostenibilidad" lidera por tercer año consecutivo el ranking de términos más
usados en informes corporativos, según el Observatorio de Neologismos. Su frecuencia ha
aumentado un 340% desde 2019. Expertos advierten del riesgo de "vaciamiento semántico":
un término tan repetido que pierde precisión.

Fuente: Observatorio de Neologismos | www.obs-neologismos.es/informe2023 | Acceso: 22/11/2023
```

```
TECNOLOGÍA Y SOCIEDAD - Especial anual
https://www.lectordigital.com/especial/lenguaje-ia-2024 | Publicado: 02/01/2024

El término "alucinación" ha adquirido un nuevo significado técnico en el contexto de los
sistemas de inteligencia artificial: la generación de información falsa presentada con
apariencia de veracidad. Investigadores del campo advierten que su adopción en el lenguaje
común puede generar "confusión conceptual" entre usuarios no especializados.

© LectorDigital 2024 | Todos los derechos reservados | contacto@lectordigital.com
```

## Estado 2: Corpus limpio

Después de aplicar expresiones regulares que eliminan URLs, correos electrónicos, hashtags, fechas, metadatos de sección y contenido entre corchetes.

Patrones aplicados:
- `https?://[^\s]+` → URLs
- `\S+@\S+` → correos
- `#[\w]+` → hashtags
- `\[[^\]]+\]` → contenido entre corchetes
- `\d{1,2}[/\-]\d{1,2}[/\-]\d{2,4}` → fechas
- `^[A-ZÁÉÍÓÚ ]+[|-].*$` → cabeceras de sección
- `^(Por|Autor|Fuente|©).*$` → líneas de autoría y créditos

Resultado:

```
El fenómeno "phubbing" -ignorar a quien tienes delante por mirar el teléfono- ha pasado
de anglicismo minoritario a candidato en el diccionario de la RAE. Lingüistas consultados
por este diario señalan que la velocidad de adopción es "sin precedentes en la historia
reciente del español".

La palabra "sostenibilidad" lidera por tercer año consecutivo el ranking de términos más
usados en informes corporativos, según el Observatorio de Neologismos. Su frecuencia ha
aumentado un 340% desde 2019. Expertos advierten del riesgo de "vaciamiento semántico":
un término tan repetido que pierde precisión.

El término "alucinación" ha adquirido un nuevo significado técnico en el contexto de los
sistemas de inteligencia artificial: la generación de información falsa presentada con
apariencia de veracidad. Investigadores del campo advierten que su adopción en el lenguaje
común puede generar "confusión conceptual" entre usuarios no especializados.
```

El texto es ahora procesable. Sin ruido. Sin metadatos mezclados con contenido.

## Estado 3: Términos extraídos

Después de pasar el corpus limpio por un modelo de PLN (spaCy). El modelo identifica entidades nombradas, categorías gramaticales y lemas relevantes.

| Término | Lema | Categoría | Entidad |
|---|---|---|---|
| phubbing | phubbing | sustantivo (préstamo) | - |
| anglicismo | anglicismo | sustantivo | - |
| RAE | RAE | sustantivo propio | ORG |
| lingüista | lingüista | sustantivo | - |
| sostenibilidad | sostenibilidad | sustantivo | - |
| vaciamiento semántico | vaciamiento semántico | sintagma nominal | - |
| Observatorio de Neologismos | Observatorio de Neologismos | sustantivo propio | ORG |
| neologismo | neologismo | sustantivo | - |
| alucinación | alucinación | sustantivo | - |
| inteligencia artificial | inteligencia artificial | sintagma nominal | - |
| confusión conceptual | confusión conceptual | sintagma nominal | - |

Ocho términos candidatos y dos organizaciones. El modelo no reconoce *phubbing* como palabra española - lo marca como préstamo sin lema canónico. Eso es información, no un error.

## Estado 4: Ejercicios generados

Prompt enviado al modelo de IA generativa:

> A partir de esta lista de términos lingüísticos, genera tres ejercicios de vocabulario para estudiantes universitarios de traducción. Cada ejercicio debe incluir: definición del término, ejemplo de uso en contexto, y una pregunta de reflexión.

Output generado:

> **Ejercicio 1 - phubbing**
> 
> *Definición:* Comportamiento social que consiste en ignorar a las personas presentes en favor del uso del teléfono móvil. El término es un anglicismo formado a partir de *phone* (teléfono) y *snubbing* (desairar).
> 
> *Ejemplo:* "Durante la reunión de equipo, el phubbing generalizado impidió cualquier debate productivo."
> 
> *Reflexión:* ¿En qué contextos comunicativos resulta más disruptivo este comportamiento? ¿Existen equivalentes en otras lenguas o el anglicismo se impone sin adaptación?
> 
> **Ejercicio 2 - vaciamiento semántico**
> 
> *Definición:* Proceso por el cual una palabra pierde progresivamente su contenido significativo debido al uso excesivo o indiscriminado. También denominado *desgaste léxico* o *erosión semántica*.
> 
> *Ejemplo:* "El vaciamiento semántico de 'innovación' en el discurso empresarial ha convertido el término en un marcador de registro más que en un descriptor preciso."
> 
> *Reflexión:* Identificad otros términos que hayan experimentado vaciamiento semántico en el discurso público reciente. ¿Qué consecuencias tiene para la comunicación especializada?
> 
> **Ejercicio 3 - alucinación (en IA)**
> 
> *Definición:* En el campo de la inteligencia artificial, fenómeno por el cual un modelo de lenguaje genera información factualmente incorrecta con apariencia de certeza. El término es una extensión metafórica del uso médico original, que designa percepciones sin estímulo externo real.
> 
> *Ejemplo:* "La traducción automática produjo una alucinación al insertar una cita bibliográfica inexistente en el texto de llegada."
> 
> *Reflexión:* ¿Qué implicaciones tiene la adopción de este término técnico en el lenguaje común? ¿Facilita o dificulta la comprensión del fenómeno para usuarios no especializados?

## Estado 5: Ejercicios validados

La revisión humana detecta dos problemas:

- **Problema 1 - Ejercicio 1, definición de *phubbing*:** La etimología es correcta, pero la definición omite que el término no está en el diccionario de la RAE -precisamente lo que señalaba el artículo de origen. El modelo generó una definición descontextualizada, ignorando el matiz de "candidato". Corrección: añadir que el término está en proceso de normalización y que su estatus lexicográfico es aún provisional.
- **Problema 2 - Ejercicio 2, sinónimos de *vaciamiento semántico*:** El modelo propone "erosión semántica" como sinónimo establecido. No lo es - es una construcción descriptiva ocasional, no un término codificado en la lingüística hispánica. Corrección: eliminarlo o marcarlo explícitamente como término no canónico.

Versión validada: los tres ejercicios con las correcciones aplicadas, listos para distribución.

## Conclusiones

El flujo completo - desde tres artículos periodísticos con metadatos mezclados hasta ejercicios revisables por un profesional - ilustra lo que estas sesiones permiten construir. Cada herramienta hace una cosa; la combinación hace otra de orden distinto.
