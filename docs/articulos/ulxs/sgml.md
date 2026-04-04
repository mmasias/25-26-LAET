# SGML

> El tatarabuelo de la web

**1986 · Charles Goldfarb, Edward Mosher, Raymond Lorie (IBM) · Metalenguaje de marcado**

## ¿Por qué?

En los años 70, IBM necesitaba gestionar documentación técnica compleja que debía publicarse en múltiples formatos (papel, pantalla, microficha) sin duplicar el contenido. La solución fue separar la estructura semántica del documento de su presentación: el mismo texto, marcado una sola vez, podía renderizarse de formas distintas según el destino. GML (1969) fue el primer prototipo interno; SGML (1986) fue su estandarización como norma ISO.

## ¿Qué?

Standard Generalized Markup Language. Metalenguaje ISO (8879:1986) para definir lenguajes de marcado con vocabulario propio. No es un lenguaje de marcado en sí: es un sistema para crear lenguajes de marcado. HTML es una aplicación de SGML. XML es una simplificación de SGML diseñada para la web.

## ¿Para qué?

Publicación técnica, documentación aeronáutica y militar, edición electrónica de gran escala. Su legado directo son HTML, XML y todos los lenguajes derivados. Sin SGML no existiría la web tal como la conocemos.

## ¿Cómo?

> No tiene live preview: es un metalenguaje, no se "ejecuta". Sus descendientes sí: [HTML](html.md) · [XML](xml.md)

### Sintaxis

| Construcción | Significado |
|---|---|
| `<!DOCTYPE nombre SYSTEM "fichero.dtd">` | declaración del tipo de documento |
| `<elemento>contenido</elemento>` | elemento marcado (igual que HTML/XML) |
| `<!-- comentario -->` | comentario |
| DTD (Document Type Definition) | define qué elementos y atributos son válidos |
| etiquetas minimizadas (`<P>` sin cierre) | permitidas en SGML, prohibidas en XML |

### Ejemplo

```sgml
<!DOCTYPE articulo SYSTEM "articulo.dtd">
<articulo>
  <titulo>Análisis morfológico del español</titulo>
  <autor>
    <nombre>Ana García</nombre>
    <institucion>CSIC</institucion>
  </autor>
  <resumen>
    Este trabajo presenta un análisis de los morfemas
    derivativos más productivos del español contemporáneo.
  </resumen>
  <termino tipo="tecnico">morfema</termino>
  <termino tipo="tecnico">derivación</termino>
</articulo>
```

---

*Ver también: [HTML](html.md) · [XML](xml.md) — sus dos descendientes directos*
