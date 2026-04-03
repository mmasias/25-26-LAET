# XML

> Datos con significado explícito

**1998 · W3C (basado en SGML, 1986) · Lenguaje de marcado extensible**

## ¿Por qué?

HTML describe cómo se ve el contenido; no dice nada sobre qué es. Un número entre etiquetas `<td>` puede ser un precio, una fecha o un código postal: el formato no lo distingue. SGML (1986) propuso separar estructura de presentación, pero era demasiado complejo para la web. XML es la simplificación de SGML diseñada para ser a la vez legible por humanos, parseable por máquinas y extensible: cada comunidad define sus propias etiquetas según su dominio.

## ¿Qué?

eXtensible Markup Language. Metalenguaje para definir lenguajes de marcado con vocabulario propio. A diferencia de HTML, las etiquetas no están predefinidas: el autor las define según la semántica de su dominio. Es la base de TEI, SVG, XHTML, RSS, DOCX y cientos de formatos más.

## ¿Para qué?

Corpus lingüísticos anotados (TEI), documentos con estructura semántica explícita, intercambio de datos entre sistemas heterogéneos. En lingüística de corpus, TEI/XML es el estándar de facto para ediciones digitales de textos históricos y literarios.

## ¿Cómo?

> [LivePreview](https://www.xmlvalidation.com/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `<elemento>contenido</elemento>` | elemento con etiqueta de apertura y cierre |
| `<elemento atributo="valor"/>` | elemento vacío con atributo |
| `<?xml version="1.0" encoding="UTF-8"?>` | declaración obligatoria al inicio |
| `<!-- comentario -->` | comentario |
| `<![CDATA[texto literal]]>` | bloque de texto sin parsear |

### Ejemplo

```xml
<?xml version="1.0" encoding="UTF-8"?>
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
    <fileDesc>
      <titleStmt>
        <title>Corpus de neologismos digitales</title>
      </titleStmt>
    </fileDesc>
  </teiHeader>
  <text lang="es">
    <body>
      <p n="1">
        El término <term type="neologismo" origen="inglés">ghosting</term>
        designa la ruptura abrupta de comunicación sin explicación.
      </p>
      <p n="2">
        <term type="neologismo" origen="español">postureo</term>
        aparece documentado desde 2012 en corpus digitales.
      </p>
    </body>
  </text>
</TEI>
```
