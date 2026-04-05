# Mapa

<div align=center>

|UML|BNF| | | |
|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-simple.svg)|![](/docs/images/regex/regex.png)|![](/docs/images/regex/token.png)|![](/docs/images/regex/unidad.png)|![](/docs/images/regex/metacaracter.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-simple.puml)</sub>|Regex|Token|Unidad|Metacaracter

</div>

## Literales

<div align=center>

|UML|BNF| | | |
|:-:|:-:|-|-|-|
|![](/docs/images/modelosUML/regex-taxonomy-literales.svg)|![](/docs/images/regex/literal.png)|![](/docs/images/regex/alfanumerico.png)|![](/docs/images/regex/metacaracterEscapado.png)|![](/docs/images/regex/espacioEscapado.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-literales.puml)</sub>|Literal|Alfanumérico|Metacaracter escapado|Espacios escapados

</div>

## Clases de caracteres

<div align=center>

|UML|BNF| | | | |
|:-:|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-clases.svg)|![](/docs/images/regex/clase.png)|![](/docs/images/regex/predefinida.png)|![](/docs/images/regex/negada.png)|![](/docs/images/regex/personalizada.png)|![](/docs/images/regex/rango.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-clases.puml)</sub>|Clase|Predefinida|Negada|Personalizada|Rango

</div>

## Cuantificadores

<div align=center>

|UML|BNF| | | |
|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-cuantificadores.svg)|![](/docs/images/regex/cuantificador.png)|![](/docs/images/regex/baseCuantificador.png)|![](/docs/images/regex/modificadorCuantificador.png)|![](/docs/images/regex/numero.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-cuantificadores.puml)</sub>|Cuantificador|Base|Modificador|Número

</div>

## Anclas

<div align=center>

|UML|BNF| | |
|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-anclas.svg)|![](/docs/images/regex/ancla.png)|![](/docs/images/regex/posicion.png)|![](/docs/images/regex/limite.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-anclas.puml)</sub>|Ancla|Posición|Límite

</div>

## Grupos y alternancia

<div align=center>

|UML|BNF| | | | |
|:-:|:-:|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-grupos.svg)|![](/docs/images/regex/grupo.png)|![](/docs/images/regex/captura.png)|![](/docs/images/regex/noCaptura.png)|![](/docs/images/regex/alternancia.png)|![](/docs/images/regex/referencia.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-grupos.puml)</sub>|Grupo|Captura|No captura|Alternancia|Referencia

</div>

## Lookaround

<div align=center>

|UML|BNF| | |
|:-:|:-:|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-lookaround.svg)|![](/docs/images/regex/lookaround.png)|![](/docs/images/regex/lookahead.png)|![](/docs/images/regex/lookbehind.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-lookaround.puml)</sub>|Lookaround|Lookahead|Lookbehind

</div>

## Flags

<div align=center>

|UML|BNF|
|:-:|:-:|
|![](/docs/images/modelosUML/regex-taxonomy-flags.svg)|![](/docs/images/regex/flag.png)|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-flags.puml)</sub>|Flag

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
