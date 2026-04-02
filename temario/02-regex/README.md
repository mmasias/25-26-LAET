# Expresiones regulares

## ¿Por qué?

En 1956 se publicaron dos trabajos que partían de la misma pregunta: ¿qué es un lenguaje, formalmente? ¿Qué estructuras lo definen? ¿Qué puede y qué no puede reconocer una máquina?

<div align=center>

|Stephen Kleene, *matemático*|Noam Chomsky, *lingüista*|
|-|-|
Definía una notación para describir conjuntos de cadenas de símbolos mediante reglas de composición.|Clasificaba los lenguajes en cuatro niveles según la complejidad de sus reglas.
Le llamó ***expresiones regulares***.|Al nivel más bajo, el más simple, le llamó ***lenguajes regulares***.
|[*Representation of Events in Nerve Nets and Finite Automata*](https://www.rand.org/content/dam/rand/pubs/research_memoranda/2008/RM704.pdf)|[*Three Models for the Description of Language*](https://chomsky.info/wp-content/uploads/195609-.pdf)|

</div>

Dos disciplinas, dos vocabularios, un único objeto matemático. No es una coincidencia: ambos investigaban el mismo problema desde ángulos distintos y llegaron al mismo sitio.

## ¿Qué?

Una expresión regular es una cadena de caracteres que describe un conjunto de cadenas posibles. Combina dos tipos de elementos:

- **Literales:** caracteres que se buscan tal cual (`casa`, `@`, `.`)
- **Metacaracteres:** símbolos con significado especial — cualquier carácter, repetición, alternativa, posición

Su potencia está en la composición: con pocos elementos se describen conjuntos arbitrariamente complejos. No se busca una cadena concreta, sino una clase entera de cadenas posibles.

## ¿Para qué?

<div align=center>

| Original (teoría) | Práctica general | Práctica lingüística |
|---|---|---|
| Caracterizar lenguajes formales | Validar formatos de entrada | Verificar convenciones de corpus |
| Definir qué cadenas son válidas | Extraer datos estructurados | Extraer fechas, siglas, referencias |
| Describir lenguajes regulares | Buscar y reemplazar en masa | Normalizar variantes ortográficas |
| | Limpiar datos en bruto | Eliminar metadatos, etiquetas, URLs |
| | Detectar patrones repetitivos | Identificar anglicismos por sufijo |

</div>

## ¿Cómo?

<div align=center>

|![](/images/modelosUML/regex-taxonomy-simple.svg)
|-
| [Ver taxonomía completa](/images/modelosUML/regex-taxonomy.svg) |

</div>

### Literales

Caracteres que se buscan tal cual. `corpus` encuentra exactamente esa cadena. La búsqueda distingue mayúsculas de minúsculas salvo indicación contraria.

### Metacaracteres

Símbolos con significado especial que representan categorías de caracteres:

| Metacarácter | Representa |
|---|---|
| `.` | cualquier carácter individual (excepto salto de línea) |
| `\d` | cualquier dígito (`0-9`) |
| `\w` | cualquier carácter de palabra (letra, dígito, guión bajo) |
| `\s` | cualquier espacio en blanco (espacio, tabulación, salto de línea) |
| `\D` `\W` `\S` | la negación de los anteriores |

### Clases de caracteres

Conjuntos definidos entre corchetes. Solo se busca uno de los caracteres listados:

| Construcción | Representa |
|---|---|
| `[aeiou]` | cualquiera de esas vocales |
| `[^aeiou]` | cualquier carácter que NO sea esas vocales |
| `[a-z]` | cualquier letra minúscula |
| `[a-záéíóúüñ]` | cualquier letra minúscula del español |

### Cuantificadores

Indican cuántas veces se repite el elemento anterior:

| Cuantificador | Significado |
|---|---|
| `*` | cero o más veces |
| `+` | una o más veces |
| `?` | cero o una vez (hace el elemento opcional) |
| `{3}` | exactamente 3 veces |
| `{2,4}` | entre 2 y 4 veces |
| `{2,}` | 2 o más veces |

### Anclas

Posicionan la búsqueda sin consumir caracteres:

| Ancla | Posición |
|---|---|
| `^` | inicio de línea |
| `$` | fin de línea |
| `\b` | límite de palabra (frontera entre `\w` y `\W`) |

### Grupos

Los paréntesis agrupan y capturan:

| Construcción | Uso |
|---|---|
| `(patrón)` | grupo capturador: extrae la coincidencia para reutilizarla |
| `(?:patrón)` | grupo no capturador: agrupa sin extraer |
| `(a\|b)` | alternativa: `a` o `b` |

### Ejemplos

Texto de trabajo:

```text
La conferencia del 12/03/2024 abordó el fenómeno "ghosting" en contextos laborales.
@linguista publicó: "el término 'postureo' ya aparece en corpus del CREA."
Ver más en https://corpus.rae.es — #neologismos #lenguajeDigital
```

**Limpiar** — eliminar ruido no textual:

| Qué eliminar | Regex |
|---|---|
| URLs | `https?://[^\s]+` |
| Menciones | `@\w+` |
| Hashtags | `#\w+` |

Resultado: `La conferencia del 12/03/2024 abordó el fenómeno "ghosting" en contextos laborales. publicó: "el término 'postureo' ya aparece en corpus del CREA."`

**Extraer patrones** — encontrar estructuras específicas:

| Qué extraer | Regex | Encuentra |
|---|---|---|
| Fechas dd/mm/aaaa | `\d{2}/\d{2}/\d{4}` | `12/03/2024` |
| Palabras entre comillas | `"([^"]+)"` | `ghosting`, `postureo` |
| Palabras terminadas en `-ing` | `\b[a-zA-Z]+ing\b` | `ghosting` |
| Verbos en infinitivo | `\b\w+(ar\|er\|ir)\b` | `publicar`, `aparecer` |

**Normalizar** — estandarizar formatos:

Buscar `(\d{2})/(\d{2})/(\d{4})` → reemplazar por `$3-$2-$1` transforma `12/03/2024` en `2024-03-12`. Los grupos capturados permiten reordenar partes del texto sin reescribirlas.

### Trayectoria: de la teoría a la herramienta

| Año | Hito |
|---|---|
| 1956 | Kleene define las expresiones regulares en teoría de autómatas |
| 1968 | Ken Thompson las implementa en el editor QED, luego en `grep` |
| 1970s-80s | Se estandarizan en Unix: `grep`, `sed`, `awk` |
| 1987 | Perl las populariza con sintaxis más expresiva |
| 1990s-2000s | Se integran en editores de texto, IDEs y bases de datos |
| Hoy | Disponibles en cualquier hoja de cálculo y en el navegador |

Una notación diseñada para describir lenguajes formales recorrió setenta años y tres disciplinas —matemáticas, informática, lingüística computacional— antes de llegar al navegador.

---

- [Regex básico](basico.md) — Práctica visual con regexr.com
- [Regex aplicado](aplicado.md) — Corpus reales con hojas de cálculo
- [Regex avanzado](avanzado.md) — Automatización y límites
