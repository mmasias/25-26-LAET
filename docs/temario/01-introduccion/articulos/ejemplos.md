# Algunos casos

## CVs

Una empresa de recursos humanos necesita procesar cientos de currículos en formato PDF o Word para extraer datos clave (nombre, experiencia, habilidades, formación) y alimentar una base de datos de manera automatizada.

### Roles y herramientas

|Rol|Herramienta|Tarea específica|Ejemplo de código/texto|
|-|-|-|-|
|**Operarios**|Regex|Extraer información estructurada de textos no estructurados, como fechas, nombres o habilidades.|Buscar patrones como `"[A-Z][a-z]+ [A-Z][a-z]+"` para nombres, o `"[0-9]{4}-[0-9]{4}"` para rangos de años.|
|**Arquitectos**|PLN (spaCy)|Validar la coherencia de los datos extraídos: verificar que los nombres sigan un formato válido o que las fechas sean lógicas.|Usar spaCy para etiquetar entidades (PERSON, DATE) y comprobar que el texto sigue los patrones esperados.|
|**Decoradores**|LLM (ej: GPT-4)|Generar un resumen profesional y claro del currículo para el equipo de selección.|*"Juan Pérez tiene 5 años de experiencia en desarrollo de software, especializado en Python y machine learning. Destaca su participación en proyectos de IA para el sector financiero."*|

### Resultado final

Un informe estructurado y listo para ser utilizado en el proceso de selección.

## Opiniones de clientes en redes sociales

Una empresa desea analizar las opiniones de los clientes en plataformas como Twitter o Instagram para identificar tendencias, quejas comunes o aspectos mejor valorados, con el fin de tomar decisiones estratégicas.

### Roles y herramientas

|Rol|Herramienta|Tarea específica|Ejemplo de código/texto|
|-|-|-|-|
|**Operarios**|Regex|Filtrar tweets o comentarios que contengan palabras clave relevantes, como "error", "mal servicio" o "excelente".|Buscar patrones como `"error|mal servicio|excelente"` para agrupar opiniones por categorías.|
|**Arquitectos**|PLN (spaCy/NLTK)|Analizar el sentimiento de cada mensaje (positivo, negativo, neutral) y extraer entidades como productos o marcas mencionadas.|Usar spaCy para tokenizar y etiquetar el texto, y un modelo de análisis de sentimiento preentrenado (ej: VADER).|
|**Decoradores**|LLM (ej: Llama)|Generar un informe ejecutivo con las tendencias principales y recomendaciones para la empresa.|*"El 60% de los comentarios negativos mencionan 'entrega lenta', lo que sugiere que el servicio logístico es un área crítica para mejorar."*|

### Resultado final

Un informe o dashboard que la empresa pueda utilizar para tomar decisiones basadas en datos.

## Traducción y adaptación de un manual técnico

> *Antes de ver este ejemplo, comentar: [U6](https://github.com/mmasias/u6-VII-traslation-project) & [LSL1](https://www.linkedin.com/posts/mmasias_preparando-una-charla-record%C3%A9-que-a-finales-activity-7419710885117472770-OQcJ/)*

Una empresa necesita traducir un manual técnico del inglés al español, pero también adaptarlo culturalmente para que sea comprensible y relevante en el mercado objetivo (ej: cambiar ejemplos, unidades de medida o referencias culturales).

### Roles y herramientas

|Rol|Herramienta|Tarea específica|Ejemplo de código/texto|
|-|-|-|-|
|**Operarios**|Regex|Extraer términos técnicos y referencias a unidades de medida (ej: "mph", "°F") para garantizar su traducción correcta.|Buscar patrones como `"[0-9]+\s?(mph|°F|km/h|°C)"` para identificar unidades en el texto.|
|**Arquitectos**|PLN (spaCy)|Validar que la traducción sea gramaticalmente correcta y que los términos técnicos sean precisos y coherentes.|Usar spaCy para comparar la estructura de las frases en ambos idiomas y detectar inconsistencias.|
|**Decoradores**|LLM (ej: GPT-4)|Adaptar el manual para que sea más claro y relevante para el público objetivo, cambiando ejemplos o unidades de medida.|En lugar de *"The speed limit is 60 mph"*, generar *"La velocidad máxima permitida es 96 km/h"* para el mercado español.|

### Resultado final

Un manual traducido y adaptado, listo para su uso en el mercado objetivo.

## 1998

En 1998, [un proyecto para un periódico local](https://web.archive.org/web/19990219082608/http://www.eltiempo.com.pe/piuranos/index.html) permitía a los ciudadanos de esa ciudad dispersos por el mundo buscarse entre sí. No usaba base de datos sino que los registros se almacenaban en un fichero de texto plano separado por punto y coma. El programa decodificaba caracteres especiales, normalizaba mayúsculas, buscaba coincidencias parciales y fragmentaba cadenas - [cuatro operaciones que la lingüística computacional reconoce como propias](https://github.com/mmasias/DirectorioPiuranos/blob/main/ANALISIS.md#resumen-las-cuatro-operaciones). Sin saberlo, se estaba haciendo lingüística computacional. 

La conexión entre lengua y tecnología no es reciente: lo reciente son las herramientas accesibles.