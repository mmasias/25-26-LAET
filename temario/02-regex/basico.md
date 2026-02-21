# Regex básico

## ¿Por qué?

Corpus lingüísticos digitales vienen sucios. Formatos inconsistentes, códigos extraños, metadatos mezclados con contenido. Limpieza manual es imposible en corpus de más de 1000 elementos.

## ¿Qué?

**Regex = expresión regular = lenguaje de patrones**

Búsqueda de patrones en lugar de palabras exactas.

| Concepto | Descripción | Ejemplo |
|----------|-------------|---------|
| Literales | Caracteres que se buscan tal cual | `hola`, `@`, `#` |
| Metacaracteres | Caracteres especiales | `\d` (dígito), `\w` (carácter de palabra), `.` (cualquier carácter) |
| Clases de caracteres | Conjuntos de caracteres | `[abc]`, `[^abc]`, `[\d]` |
| Cuantificadores | Cuántas veces se repite algo | `{3}` (exactamente 3), `*` (0 o más), `+` (1 o más) |
| Grupos de captura | Partes que se pueden referenciar | `()` captura para usar en reemplazo |

## ¿Para qué?

| Caso de uso | Regex |
|-------------|-------|
| Extraer fechas dd/mm/aaaa | `\d{2}/\d{2}/\d{4}` |
| Limpiar menciones de redes sociales | `@[\w]+` |
| Encontrar verbos en gerundio | `\w+(ando\|iendo)` |
| Extraer números de teléfono | `\d{3}-\d{3}-\d{4}` |
| Normalizar formatos (fechas) | Buscar `(\d{2})/(\d{2})/(\d{4})` → Reemplazar `$3-$2-$1` |

## ¿Cómo?

**Herramienta:** [regexr.com](https://regexr.com/)

Visual, feedback inmediato, sin instalación, explicación de cada parte al pasar el mouse.

**Ejemplos prácticos incrementales:**

1. Buscar fechas en formato dd/mm/aaaa → `\d{2}/\d{2}/\d{4}`
2. Buscar emails → `[\w.]+@[\w.]+`
3. Buscar verbos en gerundio → `\w+ando`
4. Buscar anglicismos terminados en -ing → `\b[a-zA-Z]+ing\b`
5. Buscar palabras entre comillas → `"([^"]+)"`

**Corpus real:** Subtítulos con códigos de tiempo que hay que limpiar.

**Ejercicio:** Limpiar corpus de tweets (URLs, menciones, hashtags)

**Demostración en vivo:**

```text
🚀 ¡El nuevo término "influencer" está viralizando! #LenguajeDigital https://t.co/abc123

@usuario1 De acuerdo con @usuario2: el concepto de "cancelar" cambió en 2024.

Thread sobre neologismos: "woke" pasó del inglés al español... https://www.ejemplo.com/articulo
```

Aplicando:
- `https?://[^\s]+` → elimina URLs
- `@[\w]+` → elimina menciones
- `#[\w]+` → elimina hashtags

Resultado: texto limpio en segundos en lugar de horas de trabajo manual.

## Y ahora, ¿qué?

- [regexr.com](https://regexr.com/)
- [RegexOne](https://regexone.com/) - Tutorial interactivo
- [Regex101](https://regex101.com/) - Alternativa con más opciones
