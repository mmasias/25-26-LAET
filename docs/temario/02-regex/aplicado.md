# Regex aplicado

## ¿Por qué?

||||
|-|-|-|
Las expresiones regulares no son exclusivas de los entornos de programación. Están integradas en herramientas que muchos profesionales de la lengua ya utilizan a diario.|En Google Docs, el diálogo de buscar y reemplazar incluye una opción llamada *Usar expresiones regulares*.<br><br>En Google Sheets, existen tres funciones dedicadas: `REGEXMATCH`, `REGEXEXTRACT` y `REGEXREPLACE`.<br><br>La capacidad existe desde hace años; pasa desapercibida porque no ocupa un lugar prominente en ninguna de las dos interfaces.|El conocimiento de la sesión anterior se aplica directamente en herramientas ya en uso. No es necesario aprender un entorno nuevo.

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

### El corpus de trabajo

El material de trabajo son 25 fragmentos sobre neologismos del español digital: [corpus-neologismos.md](corpus-neologismos.md). Contiene ruido típico de origen digital: URLs, menciones, hashtags, emojis, fechas en formatos inconsistentes y palabras duplicadas.

### Paso 1 - Limpiar en Google Docs

Abrir Google Docs, pegar el corpus y activar **Editar → Buscar y reemplazar → Usar expresiones regulares**. Aplicar los reemplazos necesarios para eliminar el ruido digital del corpus.

El resultado esperado para los dos primeros fragmentos sería:

|Original|Limpio|
|-|-|
🚀 El término "influencer" lleva tres años en los corpus académicos y sigue sin traducción estable. #NeoLogismos #LenguaDigital https://t.co/abc123 - 12/03/2024|El término "influencer" lleva tres años en los corpus académicos y sigue sin traducción estable. - 12/03/2024
@linguista_pro De acuerdo: "ghosting" ya aparece en el DRAE con marca coloquial. Fuente: https://dle.rae.es/ghosting - 03-04-2024|De acuerdo: "ghosting" ya aparece en el DRAE con marca coloquial. Fuente: - 03-04-2024

<details>
<summary>Pista</summary>

Hay que eliminar, por ejemplo, emojis, menciones, hashtags, URLs y palabras duplicadas. Aplicando estos reemplazos en orden (campo *Reemplazar por* vacío salvo indicación expresa):

<div align=center>

| Qué eliminar | Patrón | Reemplazar por |
|---|---|---|
| Emojis | `[🚀🧵]` | *(vacío)* |
| Menciones | `@\w+` | *(vacío)* |
| Hashtags | `#\w+` | *(vacío)* |
| URLs | `https?://\S+` | *(vacío)* |
| Palabras duplicadas | `\b(\w+) \1\b` | `\1` |
| Espacios múltiples | `\s{2,}` | *(un espacio)* |

</div>

</details>

### Paso 2 - Extraer y normalizar en Google Sheets

Copiar los 25 fragmentos limpios en Google Sheets, uno por celda en la columna A. Añadir las columnas siguientes con las fórmulas indicadas y arrastrarlas hacia abajo para cubrir todas las filas.

| Columna | Qué produce | Fórmula |
|---|---|---|
| B - Término | Primera palabra entre comillas del fragmento | `=REGEXEXTRACT(A1; """([^""]+)""")` |
| C - ¿Anglicismo en -ing? | VERDADERO si el término termina en *-ing* | `=REGEXMATCH(B1; "\w+ing")` |
| D - Fecha extraída | Fecha en formato numérico (si existe) | `=REGEXEXTRACT(A1; "\d{1,2}[/\-]\d{1,2}[/\-]\d{4}")` |
| E - Fecha normalizada | Fecha reordenada a formato ISO `aaaa-mm-dd` | `=REGEXREPLACE(D1; "(\d{1,2})[/\-](\d{1,2})[/\-](\d{4})"; "\3-\2-\1")` |

Las filas 4, 7, 17, 19 y 25 contienen fechas en formato textual (*"5 de abril de 2024"*, *"1 de abril de 2024"*…): la columna D quedará vacía en esas filas. El patrón que haría falta para capturarlas es parte del ejercicio.

> **Resultado esperado** - solo para verificación:

<div align=center>

| # | Término | ¿-ing? | Fecha extraída | Fecha normalizada |
|:-:|:-:|:-:|:-:|:-:|
| 1 | influencer | FALSO | 12/03/2024 | 2024-03-12 |
| 2 | ghosting | VERDADERO | 03-04-2024 | 2024-04-03 |
| 3 | woke | FALSO | | |
| 4 | phishing | VERDADERO | | |
| 5 | scrollear | FALSO | 12/3/2024 | 2024-3-12 |
| 6 | deepfake | FALSO | 7-4-2024 | 2024-4-7 |
| 7 | streaming | VERDADERO | | |
| 8 | mansplaining | VERDADERO | 04/04/2024 | 2024-04-04 |
| 9 | Selfie | FALSO | 15/03/2024 | 2024-03-15 |
| 10 | meme | FALSO | 18-03-2024 | 2024-03-18 |
| 11 | burnout | FALSO | 20/03/2024 | 2024-03-20 |
| 12 | spoiler | FALSO | 22-03-2024 | 2024-03-22 |
| 13 | hater | FALSO | 25/03/2024 | 2024-03-25 |
| 14 | fake news | FALSO | 26-03-2024 | 2024-03-26 |
| 15 | Trolling | VERDADERO | 28/03/2024 | 2024-03-28 |
| 16 | networking | VERDADERO | 29-03-2024 | 2024-03-29 |
| 17 | spam | FALSO | | |
| 18 | spanglish | FALSO | 2-4-2024 | 2024-4-2 |
| 19 | Coaching | VERDADERO | | |
| 20 | rebranding | VERDADERO | 5/04/2024 | 2024-04-5 |
| 21 | teletrabajo | FALSO | 7/04/2024 | 2024-04-7 |
| 22 | Hashtag | FALSO | 8/04/2024 | 2024-04-8 |
| 23 | Storytelling | VERDADERO | 9-04-2024 | 2024-04-9 |
| 24 | ranking | VERDADERO | 10/04/2024 | 2024-04-10 |
| 25 | crowdfunding | VERDADERO | | |

</div>
