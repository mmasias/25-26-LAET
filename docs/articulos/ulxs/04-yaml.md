# YAML

> JSON con ansiedad de indentación

**2001 · Clark Evans, Ingy döt Net, Oren Ben-Kiki · Lenguaje de serialización de datos**

## ¿Por qué?

JSON no admite comentarios y su sintaxis de llaves y corchetes resulta incómoda cuando el humano es quien edita directamente el archivo. Los archivos de configuración de herramientas como Ansible, Kubernetes o GitHub Actions los escriben personas, no máquinas. Se necesitaba un formato que priorizase la escritura y lectura humanas sobre la compacidad.

## ¿Qué?

YAML Ain't Markup Language (acrónimo recursivo). Superconjunto de JSON diseñado para máxima legibilidad humana. La estructura se codifica mediante indentación, no mediante llaves ni corchetes. Todo JSON válido es YAML válido.

## ¿Para qué?

Archivos de configuración (Docker Compose, GitHub Actions, Ansible, Kubernetes). Preferido cuando el humano edita directamente. El precio: un tab invisible convierte un archivo válido en inválido sin ningún cambio visible en pantalla.

## ¿Cómo?

> [LivePreview](https://yaml-online-parser.appspot.com/)

### Sintaxis

| Construcción | Significado |
|---|---|
| indentación con espacios _(nunca tabs)_ | estructura jerárquica |
| `clave: valor` | sin comillas salvo ambigüedad |
| `- item` | elemento de lista |
| `\|` y `>` | bloque de texto literal y plegado |
| `# comentario` | a diferencia de JSON, admite comentarios |

### Ejemplo

```yaml
# Corpus lingüístico
nombre: Corpus del Español Moderno
version: "2.4"
fecha_creacion: 2023-01-15

dimensiones:
  tokens: 1_200_000_000
  documentos: 4500
  idiomas:
    - español peninsular
    - español latinoamericano
    - español canario

anotaciones:
  morfologia: true
  sintaxis: true
  semantica: false

descripcion: |
  Corpus balanceado que cubre
  registros formales e informales
  de 1980 a 2023.
```
