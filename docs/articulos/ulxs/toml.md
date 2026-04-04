# TOML

> Configuración obvia para humanos, inequívoca para máquinas

**2013 · Tom Preston-Werner (cofundador de GitHub) · Lenguaje de configuración**

## ¿Por qué?

YAML tiene una especificación de 80 páginas y comportamientos sorprendentes: `yes`, `no`, `on`, `off` se parsean como booleanos; los números octales tienen sintaxis diferente según la versión; las fechas son strings con convención implícita. Preston-Werner quería un formato donde cada construcción tuviese exactamente una interpretación posible y los tipos fuesen explícitos y nativos.

## ¿Qué?

Tom's Obvious, Minimal Language. Diseñado como alternativa a YAML con semántica inequívoca. Mapea directamente a tipos de datos primitivos, incluyendo `datetime` nativo (que ni JSON ni YAML tienen).

## ¿Para qué?

Archivos de configuración de proyectos: `Cargo.toml` en Rust, `pyproject.toml` en Python, `config.toml` en Hugo. Preferido cuando la corrección es más importante que la flexibilidad.

## ¿Cómo?

### Sintaxis

| Construcción | Significado |
|---|---|
| `clave = valor` | asignación simple |
| `[seccion]` | tabla (equivale a objeto) |
| `[[array_de_tablas]]` | tabla repetible |
| `# comentario` | hasta fin de línea |
| tipos: `string`, `int`, `float`, `bool`, `datetime`, `array` | tipado explícito y nativo |

### Ejemplo

```toml
# Proyecto de corpus lingüístico

[proyecto]
nombre = "CorpusEsp"
version = "1.0.0"
fecha = 2024-03-15
descripcion = """
  Corpus anotado morfológicamente
  del español contemporáneo.
"""

[dimensiones]
tokens = 1_200_000_000
documentos = 4_500
balance = 0.87

[etiquetador]
modelo = "spaCy"
precision = 0.962
idiomas = ["es", "es-419", "es-MX"]

[[autores]]
nombre = "Ana García"
institucion = "CSIC"
orcid = "0000-0001-2345-6789"
```

---

*Ver también: [YAML](yaml.md) · [JSON](json.md) — alternativas de configuración*
