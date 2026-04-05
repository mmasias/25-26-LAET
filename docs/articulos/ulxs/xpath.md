# XPath

> Navegación por documentos XML como si fueran sistemas de ficheros

**1999 · W3C · Lenguaje de consulta sobre XML**

## ¿Por qué?

XML organiza los datos en árboles jerárquicos. Para extraer un dato concreto de ese árbol, necesitas una forma de describir su posición: "el tercer párrafo del segundo capítulo", "todos los elementos con atributo `lang='es'`". XPath es esa notación: una forma de apuntar a nodos en un árbol XML de la misma manera que una ruta de ficheros apunta a un archivo en un directorio.

## ¿Qué?

XML Path Language. Lenguaje de consulta para seleccionar nodos en documentos XML y HTML. Usa una sintaxis de ruta similar a los sistemas de ficheros. Es la base de XSLT (transformación de XML) y XQuery (consultas complejas sobre XML).

## ¿Para qué?

Corpus lingüísticos en formato TEI (Text Encoding Initiative), extracción de datos de XML, transformación de documentos estructurados. La mayoría de corpus históricos y literarios digitalizados usan TEI/XML como formato de almacenamiento.

## ¿Cómo?

> [LivePreview](https://www.freeformatter.com/xpath-tester.html)

### Sintaxis

| Construcción | Significado |
|---|---|
| `/raiz/hijo` | ruta absoluta desde la raíz |
| `//elemento` | cualquier elemento en cualquier nivel |
| `@atributo` | acceso a atributo |
| `[condición]` | predicado de filtro |
| `text()` | contenido textual del nodo |

### Ejemplo

```xml
<!-- Corpus TEI simplificado -->
<TEI>
  <text lang="es">
    <body>
      <p n="1">El lingüista <term>tokeniza</term> el corpus.</p>
      <p n="2">La <term>lematización</term> reduce variantes.</p>
    </body>
  </text>
</TEI>
```

```xpath
//term                        (todos los términos)
//p[@n='1']/text()            (texto del primer párrafo)
//p[contains(., 'corpus')]    (párrafos que contienen 'corpus')
/TEI/text/@lang               (valor del atributo lang)
```

---

*Ver también: [XML](xml.md) - XPath navega documentos XML · [jq](jq.md) - equivalente para JSON*
