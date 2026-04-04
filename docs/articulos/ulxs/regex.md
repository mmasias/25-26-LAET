# Expresiones Regulares

> Álgebra de patrones sobre cadenas

**1956 · Stephen Kleene · Lenguaje formal / teoría de autómatas**

## ¿Por qué?

Kleene las definió en 1956 como notación matemática para describir lenguajes regulares, el nivel más bajo de la jerarquía de Chomsky. Décadas después, Ken Thompson las implementó en el editor `ed` (1968), desde donde se propagaron a `grep`, `sed` y todos los lenguajes de programación modernos. El problema que resuelven es siempre el mismo: describir un conjunto infinito de cadenas mediante una expresión finita.

## ¿Qué?

Notación algebraica para describir lenguajes regulares (Tipo 3 en la jerarquía de Chomsky). Implementada en prácticamente todos los lenguajes de programación para búsqueda y manipulación de texto.

## ¿Para qué?

Validación de entrada, extracción de datos, transformación de texto, análisis léxico en compiladores. Limitación fundamental: no pueden parsear HTML ni XML de forma general, porque esos lenguajes son libres de contexto (Tipo 2) y requieren memoria en forma de pila, que escapa al poder de los autómatas finitos.

## ¿Cómo?

> [LivePreview](https://regexr.com/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `. * + ?` | metacaracteres de cuantificación |
| `[ ]` | clase de caracteres / `[^ ]` clase negada |
| `( )` | grupo capturador / agrupación |
| `^ $` | anclas inicio / fin de línea |
| `\d \w \s` | clases abreviadas (dígito, palabra, espacio) |

### Ejemplo

```js
// Detectar diptongos en español
/[aeiou][iuIU]|[iuIU][aeiou]/g

// Tokenizador básico: palabras o puntuación
/[\wáéíóúüñÁÉÍÓÚÜÑ]+|[^\s\wáéíóúüñ]/g

// Prefijos negativos del español
/\b(in|im|des|a|an)[a-záéíóú]+/g

// Número de sílabas aproximado (conteo de vocales)
const silabas = palabra.match(/[aeiouáéíóúü]/gi)?.length ?? 0;
```

---

*Ver también: [BNF/EBNF](bnf.md) — ambos describen lenguajes formales*
