# Regex@GoogleSheets

Google Sheets expone tres funciones que aplican expresiones regulares sobre el contenido de las celdas. Las tres toman como primer argumento el texto a analizar y como segundo el patrón regex.

> En configuración regional en español, el separador de argumentos es `;` en lugar de `,`.

## `REGEXMATCH`

```
=REGEXMATCH(texto; patrón)
```

Devuelve `VERDADERO` si el patrón tiene al menos una coincidencia en el texto, `FALSO` si no.

| Fórmula | Resultado |
|---|---|
| `=REGEXMATCH("ghosting"; "\w+ing")` | VERDADERO |
| `=REGEXMATCH("scrollear"; "\w+ing")` | FALSO |
| `=REGEXMATCH("03-04-2024"; "\d{2}-\d{2}-\d{4}")` | VERDADERO |

Uso habitual: clasificar filas, filtrar, colorear condicionalmente.

## `REGEXEXTRACT`

```
=REGEXEXTRACT(texto; patrón)
```

Devuelve la primera coincidencia del patrón en el texto. Si el patrón contiene un grupo capturador `(...)`, devuelve el contenido del grupo, no la coincidencia completa.

| Fórmula | Resultado |
|---|---|
| `=REGEXEXTRACT("fecha: 12/03/2024"; "\d{2}/\d{2}/\d{4}")` | `12/03/2024` |
| `=REGEXEXTRACT("El «ghosting» ya está en el DRAE"; "«([^»]+)»")` | `ghosting` |
| `=REGEXEXTRACT(A1; """([^""]+)""")` | primera palabra entre comillas en A1 |

La tercera fórmula ilustra cómo incluir comillas dobles literales dentro de una cadena de Sheets: se duplican (`""`).

Si no hay coincidencia, la función devuelve un error. Conviene envolver con `IFERROR` cuando el patrón puede no aparecer en todas las filas:

```
=IFERROR(REGEXEXTRACT(A1; patrón); "")
```

## `REGEXREPLACE`

```
=REGEXREPLACE(texto; patrón; reemplazo)
```

Reemplaza todas las coincidencias del patrón por la cadena de reemplazo. Las referencias a grupos capturados se escriben `\1`, `\2`, etc.

| Fórmula | Resultado |
|---|---|
| `=REGEXREPLACE("ghosting scrollear"; "\w+ing"; "[-]")` | `[-] scrollear` |
| `=REGEXREPLACE("12/03/2024"; "(\d{2})/(\d{2})/(\d{4})"; "\3-\2-\1")` | `2024-03-12` |
| `=REGEXREPLACE(A1; "@\w+"; "")` | texto de A1 sin menciones |

A diferencia de `REGEXEXTRACT`, reemplaza todas las coincidencias, no solo la primera.

## Notas sobre el motor

Las tres funciones usan el motor **RE2** de Google. Las diferencias más relevantes respecto a PCRE (el motor de regexr.com):

| Característica | RE2 | PCRE |
|---|---|---|
| Referencias retrospectivas (`\1` en el patrón) | No admite | Sí |
| Lookahead / lookbehind | No admite | Sí |
| Grupos capturadores en reemplazo | Sí (`\1`, `\2`…) | Sí (`$1`, `$2`…) |

Si un patrón funciona en regexr.com pero falla en Sheets, la causa más probable es alguna de estas diferencias.

> [*Hoja de referencia*](https://docs.google.com/spreadsheets/d/1fSovq5M3GRsjEQ5X8wA-ApmveHBwpkhFvCzxzvGZ2bo/edit?usp=sharing)
