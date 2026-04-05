# HTML

> El esqueleto de la web

**1991 · Tim Berners-Lee · Lenguaje de marcado de hipertexto**

## ¿Por qué?

En 1989, Berners-Lee trabajaba en el CERN y necesitaba un sistema para compartir documentos entre investigadores con ordenadores distintos. La solución fue combinar tres ideas: un formato de documento (HTML), un protocolo de transferencia (HTTP) y un esquema de direccionamiento (URL). HTML no describe cómo se ve el contenido sino qué es: un encabezado, un párrafo, un enlace, una lista. La presentación es responsabilidad de CSS.

## ¿Qué?

HyperText Markup Language. Lenguaje de marcado para estructurar contenido en la web. Las etiquetas describen la semántica del contenido (`<h1>` es un título principal, `<p>` es un párrafo, `<a>` es un enlace). El navegador interpreta esa estructura y la renderiza. Es el único lenguaje que todos los navegadores del mundo entienden de forma nativa.

## ¿Para qué?

Toda página web. Documentación técnica publicada online. Corpus web (Common Crawl, CC-100). Las herramientas de scraping y extracción de texto de la web trabajan sobre HTML. Entender HTML es prerequisito para limpiar texto extraído de la web.

## ¿Cómo?

> [LivePreview](https://codepen.io/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `<etiqueta>contenido</etiqueta>` | elemento con apertura y cierre |
| `<etiqueta atributo="valor"/>` | elemento vacío (img, br, input) |
| `<h1>` – `<h6>` | jerarquía de encabezados |
| `<p>` `<ul>` `<li>` `<a>` | párrafo, lista, ítem, enlace |
| `<!-- comentario -->` | comentario (no visible en el navegador) |

### Ejemplo

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Corpus de neologismos</title>
</head>
<body>
  <h1>Neologismos digitales en español</h1>

  <p>El término <strong>ghosting</strong> designa la ruptura abrupta
  de comunicación sin explicación previa.</p>

  <h2>Características</h2>
  <ul>
    <li>Origen: inglés (<em>ghost</em>, fantasma)</li>
    <li>Documentado desde: 2014</li>
    <li>Registro: coloquial, digital</li>
  </ul>

  <p>Ver también:
    <a href="https://corpus.rae.es">Corpus RAE</a>
  </p>
</body>
</html>
```

---

*Ver también: [SGML](sgml.md) - antecesor · [XML](xml.md) - hermano más estricto · [SVG](svg.md) - vive en el DOM · [Markdown](markdown.md) - alternativa ligera*
