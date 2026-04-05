# Expresiones regulares

## ¿Por qué?

En 1956 se publicaron dos trabajos que partían de la misma pregunta: ¿qué es un lenguaje, formalmente? ¿Qué estructuras lo definen? ¿Qué puede y qué no puede reconocer una máquina?

|Stephen Kleene, *matemático*|Noam Chomsky, *lingüista*|
|-|-|
Definía una notación para describir conjuntos de cadenas de símbolos mediante reglas de composición.|Clasificaba los lenguajes en cuatro niveles según la complejidad de sus reglas.
Le llamó ***expresiones regulares***.|Al nivel más bajo, el más simple, le llamó ***lenguajes regulares***.
|[*Representation of Events in Nerve Nets and Finite Automata*](https://www.rand.org/content/dam/rand/pubs/research_memoranda/2008/RM704.pdf)|[*Three Models for the Description of Language*](https://chomsky.info/wp-content/uploads/195609-.pdf)|

Dos disciplinas, dos vocabularios, un único objeto matemático. No es una coincidencia: ambos investigaban el mismo problema desde ángulos distintos y llegaron al mismo sitio.

## ¿Qué?

Una expresión regular es una cadena de caracteres que describe un conjunto de cadenas posibles. Combina dos tipos de elementos:

- **Literales:** caracteres que se buscan tal cual (`casa`, `@`, `.`)
- **Metacaracteres:** símbolos con significado especial - cualquier carácter, repetición, alternativa, posición

Estructuralmente, una expresión regular es una secuencia de tokens - unidades mínimas con significado dentro del patrón - donde cada token es un literal o un metacarácter.

Su potencia está en la composición: con pocos elementos se describen conjuntos arbitrariamente complejos. No se busca una cadena concreta, sino una clase entera de cadenas posibles.

## ¿Para qué?


| Original (teoría) | Práctica general | Práctica lingüística |
|---|---|---|
| Caracterizar lenguajes formales | Validar formatos de entrada | Verificar convenciones de corpus |
| Definir qué cadenas son válidas | Extraer datos estructurados | Extraer fechas, siglas, referencias |
| Describir lenguajes regulares | Buscar y reemplazar en masa | Normalizar variantes ortográficas |
| | Limpiar datos en bruto | Eliminar metadatos, etiquetas, URLs |
| | Detectar patrones repetitivos | Identificar anglicismos por sufijo |


## ¿Cómo?


|![](/docs/images/modelosUML/regex-taxonomy-simple.svg)
|-
| [Ver taxonomía completa](mapa.md) |


### Taxonomía

#### Literales

Caracteres que se buscan tal cual. Tres tipos:


| Tipo | Ejemplo | Busca |
|---|---|---|
| Alfanumérico | `corpus` | exactamente esa cadena |
| Espacio escapado | `\t` `\n` `\r` | tabulación, salto de línea, retorno de carro |
| Metacarácter escapado | `\.` `\*` `\(` `\[` … | cualquier metacarácter precedido de `\` pierde su significado especial y se busca como literal |


La búsqueda distingue mayúsculas de minúsculas salvo indicación contraria.

#### Metacaracteres

Símbolos con significado especial que representan categorías de caracteres:


| Metacarácter | Representa |
|---|---|
| `.` | cualquier carácter individual (excepto salto de línea) |
| `\d` | cualquier dígito (`0-9`) |
| `\w` | cualquier carácter de palabra (letra, dígito, guión bajo) |
| `\s` | cualquier espacio en blanco (espacio, tabulación, salto de línea) |
| `\D` `\W` `\S` | la negación de los anteriores |


#### Clases de caracteres

Conjuntos definidos entre corchetes. Solo se busca uno de los caracteres listados:


| Construcción | Representa |
|---|---|
| `[aeiou]` | cualquiera de esas vocales |
| `[^aeiou]` | cualquier carácter que NO sea esas vocales |
| `[a-z]` | cualquier letra minúscula |
| `[a-záéíóúüñ]` | cualquier letra minúscula del español |


#### Cuantificadores

Indican cuántas veces se repite el elemento anterior:


| Cuantificador | Significado |
|---|---|
| `*` | cero o más veces |
| `+` | una o más veces |
| `?` | cero o una vez (hace el elemento opcional) |
| `{3}` | exactamente 3 veces |
| `{2,4}` | entre 2 y 4 veces |
| `{2,}` | 2 o más veces |


#### Anclas

Posicionan la búsqueda sin consumir caracteres:


| Ancla | Posición |
|---|---|
| `^` | inicio de línea |
| `$` | fin de línea |
| `\b` | límite de palabra (frontera entre `\w` y `\W`) |


#### Grupos

Los paréntesis agrupan y capturan:


| Construcción | Uso |
|---|---|
| `(patrón)` | grupo capturador: extrae la coincidencia para reutilizarla |
| `(?:patrón)` | grupo no capturador: agrupa sin extraer |
| `(a\|b)` | alternativa: `a` o `b` |


### Ejemplos


| Patrón | Coincide con | No coincide con |
|---|---|---|
| `Ibuprofeno` | `Ibuprofeno` | `ibuprofeno`, `Ibuprofenos` |
| `I.uprofeno` | `Ibuprofeno` | `uprofeno`, `ibuprofeno` |
| `Fern\w+` | `Fernández`, `Fernanda`, `Fernando` | `Fern`, `fern` |
| `\d\d` | `25`, `43` | `2f`, `ab` |
| `[aeiou]` | `a`, `e`, `i`, `o`, `u` | `b`, `c`, `F` |
| `^Ibuprofeno` | `Ibuprofeno Fernández` | `Hola Ibuprofeno` |


En la práctica, una forma de construir las expresiones regulares es de adentro hacia afuera: primero se identifica el patrón mínimo que describe lo que se busca, luego se añaden repeticiones o restricciones.

#### Un proceso de trabajo

Supongamos el siguiente texto

```text
La conferencia del 12/03/2024 abordó el fenómeno "ghosting" en contextos laborales.
@linguista publicó: "el término 'postureo' ya aparece en corpus del CREA."
Ver más en https://corpus.rae.es - #neologismos #lenguajeDigital
```

**Limpiar** - eliminar ruido no textual:


| Qué eliminar | Regex | Encuentra |
|---|---|---|
| URLs | `https?://[^\s]+` | https://corpus.rae.es
| Menciones | `@\w+` | @linguista
| Hashtags | `#\w+` | #neologismos #lenguajeDigital


Si lo aplicamos eliminando lo que encuentra tendremos:

```
La conferencia del 12/03/2024 abordó el fenómeno "ghosting" en contextos laborales.
 publicó: "el término 'postureo' ya aparece en corpus del CREA."
Ver más en -
```

**Extraer patrones** - encontrar estructuras específicas:


| Qué extraer | Regex | Encuentra |
|---|---|---|
| Fechas dd/mm/aaaa | `\d{2}/\d{2}/\d{4}` | `12/03/2024` |
| Palabras entre comillas | `"([^"]+)"` | `ghosting`, `postureo` |
| Palabras terminadas en `-ing` | `\b[a-zA-Z]+ing\b` | `ghosting` |
| Verbos en infinitivo | `\b\w+(ar\|er\|ir)\b` | `publicar`, `aparecer` |


**Normalizar** - estandarizar formatos:


| Buscar | Encuentra | Reemplazar | Devuelve |
|---|---|---|---|
| `(\d{2})/(\d{2})/(\d{4})` | `12/03/2024` | `$3-$2-$1` | `2024-03-12` |


Los grupos capturados permiten reordenar partes del texto sin reescribirlas.

Para una referencia exhaustiva de toda la taxonomía: [regular-expressions.info](https://www.regular-expressions.info/)

### Trayectoria: de la teoría a la herramienta


| Año | Hito |
|---|---|
| 1956 | Kleene define las expresiones regulares en teoría de autómatas |
| 1968 | Ken Thompson las implementa en el editor QED, luego en `grep` |
| 1970s-80s | Se estandarizan en Unix: `grep`, `sed`, `awk` |
| 1987 | Perl las populariza con sintaxis más expresiva |
| 1990s-2000s | Se integran en editores de texto, IDEs y bases de datos |
| Hoy | Disponibles en múltiples herramientas ofimáticas, de desarrollo y en el navegador |


Una notación diseñada para describir lenguajes formales recorrió setenta años y tres disciplinas -matemáticas, informática, lingüística computacional- antes de llegar al navegador.

### Nota sobre implementaciones

La sintaxis presentada aquí es válida en la mayoría de entornos. Sin embargo, cada motor de expresiones regulares tiene sus particularidades: lo que funciona en uno puede no funcionar en otro.

| Motor | Usado en | Referencia |
|---|---|---|
| PCRE | regexr.com, PHP, R, editores de texto | [pcre.org](https://www.pcre.org/) |
| `re` | Python, spaCy | [docs.python.org/re](https://docs.python.org/3/library/re.html) |
| RE2 | Go, herramientas Google | [github.com/google/re2](https://github.com/google/re2/blob/main/doc/syntax.txt) |

Si un patrón no funciona como se espera, conviene consultar la documentación del motor concreto. La diferencia más habitual: RE2 no admite referencias retrospectivas (`\1`), por razones de eficiencia computacional.
