# BNF / EBNF

> El lenguaje para describir lenguajes

**1960 · John Backus & Peter Naur · Metalenguaje (gramática formal)**

## ¿Por qué?

En 1958, Backus necesitaba especificar la sintaxis de ALGOL 58 de forma precisa y no ambigua. El lenguaje natural es insuficiente para ese propósito: dos personas pueden interpretar la misma frase de modo distinto. BNF fue la primera notación formal para describir gramáticas libres de contexto, el mismo nivel que Chomsky había formalizado matemáticamente ese mismo año de forma independiente.

## ¿Qué?

Backus-Naur Form. Notación para gramáticas libres de contexto (Tipo 2 de Chomsky). Describe la sintaxis de lenguajes mediante reglas de producción. EBNF añade cuantificadores opcionales y repetición, eliminando la necesidad de recursión para expresar patrones simples.

## ¿Para qué?

Especificación formal de lenguajes de programación, protocolos y formatos. Documentación de parsers. Análisis de ambigüedad gramatical. En lingüística computacional, es la notación base para escribir gramáticas formales del lenguaje natural.

## ¿Cómo?

> [LivePreview — Railroad Diagram Generator](https://bottlecaps.de/rr/ui)

### Sintaxis

| Construcción | Significado |
|---|---|
| `<símbolo> ::= definición` | regla de producción |
| `A \| B` | alternativa |
| `{ A }` | cero o más (EBNF) |
| `[ A ]` | opcional (EBNF) |
| `"terminal"` | token literal |

### Ejemplo

```bnf
/* Gramática BNF para oraciones simples en español */

<oracion>  ::= <sn> <sv>
<sn>       ::= <det> <n> | <det> <n> <sadj>
<sv>       ::= <v> | <v> <sn> | <v> <sadj>
<sadj>     ::= <adj> | <adv> <adj>

<det>      ::= "el" | "la" | "los" | "las" | "un" | "una"
<n>        ::= "gato" | "perro" | "lingüista" | "corpus"
<v>        ::= "duerme" | "analiza" | "construye"
<adj>      ::= "rápido" | "complejo" | "preciso"
<adv>      ::= "muy" | "bastante" | "poco"

/* EBNF equivalente */
oración = sn , sv ;
sn      = det , n , [ sadj ] ;
sv      = v , [ sn | sadj ] ;
```
