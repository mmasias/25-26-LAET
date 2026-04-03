# JSON

> El esperanto de las APIs

**2001 · Douglas Crockford · Formato de intercambio de datos**

## ¿Por qué?

A finales de los 90, el formato estándar para intercambio de datos entre sistemas era XML: verboso, lleno de etiquetas redundantes y difícil de leer. Crockford observó que la sintaxis de objetos de JavaScript ya era un formato de datos perfectamente válido, legible y compacto. No lo inventó: lo descubrió, lo documentó y registró `json.org` en 2002.

## ¿Qué?

JavaScript Object Notation. Subconjunto de la sintaxis de objetos de JavaScript que se convirtió en formato estándar de intercambio de datos. Legible por humanos, parseable por máquinas.

## ¿Para qué?

APIs REST, archivos de configuración, almacenamiento de documentos. Ha desplazado casi completamente a XML en servicios web.

## ¿Cómo?

> [LivePreview](https://jsoneditoronline.org/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `{ }` | objeto (pares clave:valor) |
| `[ ]` | array (lista ordenada) |
| `"clave": valor` | las claves SIEMPRE entre comillas dobles |
| `null` / `true` / `false` | literales especiales |
| _(sin comentarios)_ | limitación de diseño deliberada |

### Ejemplo

```json
{
  "lengua": "español",
  "familia": "indoeuropea",
  "rama": "romance",
  "hablantes": {
    "nativos": 490000000,
    "totales": 595000000
  },
  "oficial_en": [
    "España", "México", "Argentina",
    "Colombia", "Perú"
  ],
  "escritura": {
    "sistema": "latino",
    "direccion": "izquierda-derecha",
    "distingue_mayusculas": false
  },
  "viva": true
}
```
