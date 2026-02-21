# Regex básico

## ¿Por qué?

Corpus lingüísticos digitales vienen sucios. Formatos inconsistentes, códigos extraños, metadatos mezclados con contenido. Limpieza manual es imposible en corpus de más de 1000 elementos.

## ¿Qué?

<div align=center>

|Regex = Expresión regular = Lenguaje de patrones|
|-|
Búsqueda de patrones en lugar de palabras exactas.

</div>

## ¿Para qué?

| Caso de uso | Regex |
|-------------|-------|
| Extraer fechas dd/mm/aaaa | `\d{2}/\d{2}/\d{4}` |
| Limpiar menciones de redes sociales | `@[\w]+` |
| Encontrar verbos en gerundio | `\w+(ando\|iendo)` |
| Extraer números de teléfono | `\d{3}-\d{3}-\d{4}` |
| Normalizar formatos (fechas) | Buscar `(\d{2})/(\d{2})/(\d{4})` → Reemplazar `$3-$2-$1` |

## ¿Cómo?

<div align=center>

|![](/images/modelosUML/regex-taxonomy.svg)|
|-|

</div>

### Construcción

Las expresiones regulares se construyen con dos tipos de elementos:

**Literales:** caracteres que se buscan tal cual (`hola`, `@`, `#`, ` `, `.`)

**Metacaracteres:** símbolos especiales con significado particular

- `.` - cualquier carácter individual
- `\d` - cualquier dígito (0-9)
- `\w` - cualquier carácter de palabra (letra, número, guión bajo)
- `\s` - cualquier espacio en blanco

**Clases de caracteres:** conjuntos de caracteres

- `[abc]` - cualquiera de a, b o c
- `[^abc]` - cualquiera que NO sea a, b o c
- `[a-z]` - cualquier letra minúscula
- `[0-9]` - cualquier dígito

**Cuantificadores:** indican cuántas veces se repite lo anterior

- `*` - cero o más veces
- `+` - una o más veces
- `?` - cero o una vez
- `{3}` - exactamente 3 veces
- `{2,4}` - entre 2 y 4 veces

**Anclajes:** posicionan la búsqueda

- `^` - inicio de línea
- `$` - fin de línea
- `\b` - límite de palabra

**Grupos de captura:** extraen partes del patrón

- `()` - grupo capturado
- `(?:)` - grupo no capturado

### Ejemplo

- `casa` - busca literalmente "casa"
- `c.s.` - busca "casa", "cosa", "cesa", etc.
- `c[ao]sa` - busca "casa" o "cosa"
- `\d{3}` - busca exactamente 3 dígitos
- `https?://` - busca "http://" o "https://"

### Ejercicio

**Herramienta:** [regexr.com](https://regexr.com/)

Visual, feedback inmediato, sin instalación, explicación de cada parte al pasar el mouse.

[Regex básico - Ejercicio](basico-ejercicio.md)

## Y ahora, ¿qué?

- [regexr.com](https://regexr.com/)
- [RegexOne](https://regexone.com/) - Tutorial interactivo
- [Regex101](https://regex101.com/) - Alternativa con más opciones
