# Mapa

<div align=center>

|![](/images/modelosUML/regex-taxonomy-simple.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-simple.puml)</sub>

</div>

## Literales

<div align=center>

|![](/images/modelosUML/regex-taxonomy-literales.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-literales.puml)</sub>

</div>

## Clases de caracteres

<div align=center>

|![](/images/modelosUML/regex-taxonomy-clases.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-clases.puml)</sub>

</div>

## Cuantificadores

<div align=center>

|![](/images/modelosUML/regex-taxonomy-cuantificadores.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-cuantificadores.puml)</sub>

</div>

## Anclas

<div align=center>

|![](/images/modelosUML/regex-taxonomy-anclas.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-anclas.puml)</sub>

</div>

## Grupos y alternancia

<div align=center>

|![](/images/modelosUML/regex-taxonomy-grupos.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-grupos.puml)</sub>

</div>

## Lookaround

<div align=center>

|![](/images/modelosUML/regex-taxonomy-lookaround.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-lookaround.puml)</sub>

</div>

## Flags

<div align=center>

|![](/images/modelosUML/regex-taxonomy-flags.svg)
|-:|
|<sub>[Código fuente](/modelosUML/regex-taxonomy-flags.puml)</sub>

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
