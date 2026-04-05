# Mapa

> Corpus: `Ibuprofeno Fernández compró Ibuprofeno en la farmacia. ibuprofeno genérico, IBUPROFENO 600. Paracetamol 500mg - lote 2024/03/12. Contacto: ifernandez@farmacia.es | tel: 612 345 678. Cita: 12/03/2024 a las 09:30h. El el paciente debe tomar la la dosis indicada cada cada día.`

<div align=center>

|UML|BNF| | | |
|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-simple.svg)|![](/docs/images/regex/regex.png)|![](/docs/images/regex/token.png)|![](/docs/images/regex/unidad.png)|![](/docs/images/regex/metacaracter.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-simple.puml)</sub>|Regex|Token|Unidad|Metacaracter

| Patrón | Encuentra |
|:-:|:-:|
| `\w+` | `Ibuprofeno`, `Fernández`, `compró`, `600`, `farmacia`… |

</div>

## Literales

<div align=center>

|UML|BNF| | | |
|:-:|:-:|-|-|-|
|![](/docs/images/modelosUML/regex-taxonomy-literales.svg)|![](/docs/images/regex/literal.png)|![](/docs/images/regex/alfanumerico.png)|![](/docs/images/regex/metacaracterEscapado.png)|![](/docs/images/regex/espacioEscapado.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-literales.puml)</sub>|Literal|Alfanumérico|Metacaracter escapado|Espacios escapados

| Patrón | Encuentra |
|:-:|:-:|
| `Ibuprofeno` | `Ibuprofeno` (exacto, sensible a mayúsculas) |
| `500mg` | `500mg` |
| `\.` | el `.` literal tras `farmacia` |
| `\t` | tabulaciones entre campos |

</div>

## Clases de caracteres

<div align=center>

|UML|BNF| | | | |
|:-:|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-clases.svg)|![](/docs/images/regex/clase.png)|![](/docs/images/regex/predefinida.png)|![](/docs/images/regex/negada.png)|![](/docs/images/regex/personalizada.png)|![](/docs/images/regex/rango.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-clases.puml)</sub>|Clase|Predefinida|Negada|Personalizada|Rango

| Patrón | Encuentra |
|:-:|:-:|
| `.` | cualquier carácter, incluyendo `@`, `/`, `-` |
| `\d` | `6`, `0`, `0`, `5`, `0`, `0`… (dígito a dígito) |
| `\D` | `I`, `b`, `u`, `p`, ` `, `F`… (todo lo que no es dígito) |
| `[A-Z]\w+` | `Ibuprofeno`, `Fernández`, `Paracetamol`, `Cita` |
| `[a-záéíóúüñ]+` | palabras en minúscula con caracteres del español |

</div>

## Cuantificadores

<div align=center>

|UML|BNF| | | |
|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-cuantificadores.svg)|![](/docs/images/regex/cuantificador.png)|![](/docs/images/regex/baseCuantificador.png)|![](/docs/images/regex/modificadorCuantificador.png)|![](/docs/images/regex/numero.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-cuantificadores.puml)</sub>|Cuantificador|Base|Modificador|Número

| Patrón | Encuentra |
|:-:|:-:|
| `\d+` | `600`, `500`, `2024`, `12`, `612`, `345`, `678`… |
| `\d{3}` | `612`, `345`, `678` |
| `\d{2,4}` | `600`, `500`, `2024`, `12`, `09`, `30` |
| `\d+?` | un dígito cada vez (lazy) |

</div>

## Anclas

<div align=center>

|UML|BNF| | |
|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-anclas.svg)|![](/docs/images/regex/ancla.png)|![](/docs/images/regex/posicion.png)|![](/docs/images/regex/limite.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-anclas.puml)</sub>|Ancla|Posición|Límite

| Patrón | Encuentra |
|:-:|:-:|
| `^Ibuprofeno` | `Ibuprofeno` solo si está al inicio de línea |
| `farmacia\.$` | `farmacia.` solo si cierra la línea |
| `\bIbuprofeno\b` | `Ibuprofeno` como palabra completa, no `Ibuprofenoide` |

</div>

## Grupos y alternancia

<div align=center>

|UML|BNF| | | | |
|:-:|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-grupos.svg)|![](/docs/images/regex/grupo.png)|![](/docs/images/regex/captura.png)|![](/docs/images/regex/noCaptura.png)|![](/docs/images/regex/alternancia.png)|![](/docs/images/regex/referencia.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-grupos.puml)</sub>|Grupo|Captura|No captura|Alternancia|Referencia

| Patrón | Encuentra |
|:-:|:-:|
| `(\d{2})/(\d{2})/(\d{4})` | `12/03/2024`; grupos: `12`, `03`, `2024` |
| `(?:\d{2})/(\d{4})` | agrupa sin capturar el día; captura solo el año |
| `Ibuprofeno\|Paracetamol` | `Ibuprofeno` o `Paracetamol` |
| `(\w+)\s+\1` | `el el`, `la la`, `cada cada` (palabras duplicadas) |

</div>

## Lookaround

<div align=center>

|UML|BNF| | |
|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-lookaround.svg)|![](/docs/images/regex/lookaround.png)|![](/docs/images/regex/lookahead.png)|![](/docs/images/regex/lookbehind.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-lookaround.puml)</sub>|Lookaround|Lookahead|Lookbehind

| Patrón | Encuentra |
|:-:|:-:|
| `\d+(?=mg)` | `500` (el número antes de `mg`, sin capturar `mg`) |
| `\d+(?!mg)` | `600`, `2024`, `612`… (números que NO van seguidos de `mg`) |
| `(?<=lote )\d{4}` | `2024` (el año después de `lote `, sin capturar `lote `) |

</div>

## Flags

<div align=center>

|UML|BNF|
|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-flags.svg)|![](/docs/images/regex/flag.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-flags.puml)</sub>|Flag

| Patrón | Encuentra |
|:-:|:-:|
| `/ibuprofeno/i` | `Ibuprofeno`, `ibuprofeno`, `IBUPROFENO` |
| `/^paracetamol/im` | `Paracetamol` al inicio de cualquier línea |

</div>

## Gramática formal (BNF)

> Verlo en vivo en el [Railroad Diagram Generator](https://www.bottlecaps.de/rr/ui)

```bnf
regex               ::= token+

token               ::= unidad cuantificador?

unidad              ::= literal | metacaracter

literal             ::= alfanumerico | metacaracter_escapado | espacio_escapado
alfanumerico        ::= [a-zA-Z0-9]
metacaracter_escapado ::= '\.' | '\*' | '\+' | '\?' | '\(' | '\)'
espacio_escapado    ::= '\t' | '\n' | '\r'

metacaracter        ::= clase | ancla | grupo | lookaround | flag

clase               ::= comodin | predefinida | negada | personalizada
comodin             ::= '.'
predefinida         ::= '\d' | '\w' | '\s'
negada              ::= '\D' | '\W' | '\S'
personalizada       ::= '[' '^'? rango+ ']'
rango               ::= alfanumerico '-' alfanumerico | alfanumerico

cuantificador       ::= base_cuant modificador_cuant?
base_cuant          ::= '*' | '+' | '?' | '{' numero ( ',' numero? )? '}'
modificador_cuant   ::= '?' | '+'
/* '?' → lazy,  '+' → posesivo,  ausente → greedy */

ancla               ::= posicion | limite
posicion            ::= '^' | '$' | '\A' | '\Z'
limite              ::= '\b' | '\B'

grupo               ::= captura | no_captura | alternancia | referencia
captura             ::= '(' regex ')'
no_captura          ::= '(?:' regex ')'
alternancia         ::= regex '|' regex
referencia          ::= '\' numero

lookaround          ::= lookahead | lookbehind
lookahead           ::= '(?=' regex ')' | '(?!' regex ')'
lookbehind          ::= '(?<=' regex ')' | '(?<!' regex ')'

flag                ::= 'i' | 'g' | 'm' | 's'

numero              ::= [0-9]+
```
