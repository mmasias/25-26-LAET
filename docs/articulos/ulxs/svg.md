# SVG

> Geometría como texto, escala sin límite

**1999 · W3C · Lenguaje de marcado vectorial**

## ¿Por qué?

Los formatos gráficos dominantes en la web (GIF, JPEG, PNG) son mapas de bits: se pixelan al ampliar, no son accesibles para lectores de pantalla y no se pueden modificar con un editor de texto. El W3C necesitaba un formato vectorial que fuese ciudadano de primera clase de la web: parte del DOM, estilizable con CSS, manipulable con JavaScript y legible por humanos.

## ¿Qué?

Scalable Vector Graphics. Dialecto XML para describir gráficos vectoriales 2D. Cada elemento visual es un nodo en el árbol DOM, manipulable con CSS y JavaScript. Los gráficos escalan sin pérdida a cualquier resolución. Es el único formato gráfico que es simultáneamente imagen, documento y programa.

## ¿Para qué?

Iconografía, infografía, diagramas lingüísticos publicables (árboles de constituyentes, mapas dialectales), animaciones web. Al vivir en el DOM, un lector de pantalla puede leer el contenido de un gráfico SVG.

## ¿Cómo?

> [LivePreview](https://www.svgviewer.dev/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `<svg width="" height="" viewBox="">` | contenedor raíz |
| `<rect>` `<circle>` `<path>` | formas primitivas |
| `<text x="" y="">` | texto posicionado |
| `<g>` | grupo (equivale a capa) |
| `d="M x,y L x2,y2 Z"` | trayectoria vectorial |

### Ejemplo

```svg
<svg width="400" height="200" viewBox="0 0 400 200"
     xmlns="http://www.w3.org/2000/svg">

  <!-- Árbol sintagmático mínimo -->
  <g font-family="monospace" font-size="14">

    <!-- Nodo raíz S -->
    <circle cx="200" cy="30" r="18" fill="#1e3a5f"/>
    <text x="200" y="35" text-anchor="middle" fill="white">S</text>

    <!-- Rama izquierda SN -->
    <line x1="190" y1="48" x2="120" y2="92" stroke="#666"/>
    <circle cx="120" cy="110" r="18" fill="#2d5a2d"/>
    <text x="120" y="115" text-anchor="middle" fill="white">SN</text>

    <!-- Rama derecha SV -->
    <line x1="210" y1="48" x2="280" y2="92" stroke="#666"/>
    <circle cx="280" cy="110" r="18" fill="#5a2d2d"/>
    <text x="280" y="115" text-anchor="middle" fill="white">SV</text>

    <!-- Hojas -->
    <text x="120" y="160" text-anchor="middle" fill="#555">el gato</text>
    <text x="280" y="160" text-anchor="middle" fill="#555">duerme</text>
  </g>
</svg>
```

---

*Ver también: [XML](xml.md) — SVG es un dialecto de XML · [HTML](html.md) — SVG vive en el DOM*
