# Regex aplicado

## ¿Por qué?

||||
|-|-|-|
Las expresiones regulares no son exclusivas de los entornos de programación. Están integradas —sin anunciarse demasiado— en herramientas que muchos profesionales de la lengua ya utilizan a diario.|En Google Docs, el diálogo de buscar y reemplazar incluye una opción llamada *Usar expresiones regulares*.<br><br>En Google Sheets, existen tres funciones dedicadas: `REGEXMATCH`, `REGEXEXTRACT` y `REGEXREPLACE`.<br><br>Ambas herramientas llevan años con esta capacidad. La mayoría de sus usuarios no lo saben.|Esto no es un detalle menor: significa que el conocimiento adquirido en la sesión anterior no requiere aprender una herramienta nueva sino que se aplica donde ya se trabaja. La barrera no es tecnológica —es de visibilidad.

## ¿Qué?

Aplicar regex en el contexto profesional consiste en combinar tres operaciones sobre texto:

<div align=center>

| Operación | Qué hace | Ejemplo |
|:-:|:-:|:-:|
| **Limpiar** | Eliminar ruido: metadatos, URLs, etiquetas, caracteres extraños | Corpus de Twitter → texto limpio |
| **Extraer** | Localizar y aislar patrones de interés | Fechas, correos, términos entre comillas |
| **Normalizar** | Estandarizar variantes de un mismo patrón | `12/03/2024` → `2024-03-12` |

</div>

Las tres operaciones se apoyan en la misma sintaxis. Lo que cambia es la herramienta que las ejecuta y el propósito que las motiva.

Las herramientas de trabajo para esta sesión son las mismas que se usan en un entorno profesional habitual:

<div align=center>

| Herramienta | Cómo se accede al regex | Cuándo usarla |
|:-:|:-:|:-:|
| [regexr.com](https://regexr.com/) | Directamente | Probar y depurar patrones |
| [Google Docs](https://docs.google.com) | Buscar y reemplazar → *Usar expresiones regulares* | Editar documentos de texto |
| [Google Sheets](https://sheets.google.com) | Funciones `REGEXMATCH`, `REGEXEXTRACT`, `REGEXREPLACE` | Procesar datos en tabla |

</div>

## ¿Para qué?

El mismo patrón ejecutado en distintas herramientas produce resultados de distinta naturaleza. Esa portabilidad tiene valor profesional directo:

| Tarea | Herramienta | Operación |
|---|---|---|
| Limpiar un corpus de artículos antes de analizarlo | Google Docs | Reemplazar URLs, hashtags y menciones por nada |
| Localizar términos candidatos en un glosario | Google Docs | Buscar palabras en mayúsculas o entre comillas |
| Clasificar entradas de una lista terminológica | Google Sheets | `REGEXMATCH` para filtrar por patrón |
| Extraer fechas de un corpus de contratos | Google Sheets | `REGEXEXTRACT` con patrón de fecha |
| Estandarizar formatos de una base de datos | Google Sheets | `REGEXREPLACE` para reordenar campos |
| Identificar anglicismos por sufijo | Cualquiera | Patrón `\b\w+ing\b` sobre el corpus |

## ¿Cómo?

