# Turtle (RDF)

> Triples sujeto–predicado–objeto a escala web

**2008 · Dave Beckett, Tim Berners-Lee · Serialización de grafos semánticos**

## ¿Por qué?

Las bases de datos relacionales almacenan hechos en tablas con esquemas fijos. Pero el conocimiento del mundo no tiene esquema fijo: una palabra puede tener dos sentidos, o veinte, o ninguno; un autor puede pertenecer a tres instituciones. Berners-Lee propuso representar el conocimiento como un grafo de afirmaciones atómicas (triples), donde cualquier hecho nuevo es simplemente un triple más, sin alterar ningún esquema.

## ¿Qué?

Terse RDF Triple Language. Serialización compacta del modelo RDF (Resource Description Framework). Representa conocimiento como grafos de triples (sujeto, predicado, objeto), base de la Web Semántica y los grafos de conocimiento.

## ¿Para qué?

Ontologías lingüísticas (WordNet, FrameNet como Linked Data), bases de conocimiento (Wikidata), integración de recursos léxicos heterogéneos. Permite mezclar datos de fuentes distintas sin transformación, porque todo recurso se identifica con una URI global.

## ¿Cómo?

### Sintaxis

| Construcción | Significado |
|---|---|
| `@prefix ex: <http://...>` | declaración de prefijo |
| `sujeto predicado objeto .` | triple (termina en punto) |
| `sujeto pred1 obj1 ; pred2 obj2` | mismo sujeto, varios predicados |
| `sujeto pred (obj1 obj2 obj3)` | lista RDF |
| `a` | abreviatura de `rdf:type` |

### Ejemplo

```turtle
@prefix rdf:     <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix lemon:   <http://lemon-model.net/lemon#> .
@prefix lexinfo: <http://www.lexinfo.net/ontology/2.0/lexinfo#> .
@prefix ex:      <http://ejemplo.org/lexico/> .

ex:correr a lemon:LexicalEntry ;
  lemon:canonicalForm ex:correr_forma ;
  lexinfo:partOfSpeech lexinfo:verb ;
  lemon:sense ex:correr_sentido1 ,
              ex:correr_sentido2 .

ex:correr_forma lemon:writtenRep "correr"@es .

ex:correr_sentido1
  lemon:definition "Moverse rápidamente a pie"@es ;
  lexinfo:senseRelation ex:huir_sentido1 .
```
