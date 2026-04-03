# Markdown

> Prosa con intención tipográfica

**2004 · John Gruber · Lenguaje de marcado ligero**

## ¿Por qué?

El HTML es ilegible sin renderizar. Al mismo tiempo, los emails en texto plano de los años 90 ya usaban convenciones tipográficas informales: asteriscos para énfasis, guiones para listas, mayúsculas para gritar, pero nadie las había codificado. Gruber estudió esas convenciones y las formalizó con un requisito de diseño explícito: el texto sin renderizar debe ser legible por sí mismo.

## ¿Qué?

Sistema de marcado en texto plano que se convierte en HTML. La sintaxis imita esas convenciones editoriales preexistentes: lo que ya hacía la gente de forma intuitiva, convertido en estándar.

## ¿Para qué?

Documentación, blogs, wikis, README. Base de la mayoría de plataformas de escritura técnica modernas.

## ¿Cómo?

### Sintaxis

| Construcción | Significado |
|---|---|
| `# Encabezado` | jerarquía mediante almohadillas |
| `**negrita** / *cursiva*` | énfasis por duplicación / simple |
| `[texto](url)` | hipervínculo en línea |
| ` ```código``` ` | bloque de código con backticks |
| `> cita` | blockquote con símbolo de respuesta postal |

### Ejemplo

````markdown
# Fonología del español

El español tiene **5 vocales** y aproximadamente *20 consonantes*.

## Rasgos distintivos

- [±sonoro]: distingue /p/ de /b/
- [±nasal]: separa /m/ de /b/

> "La lengua es el ropaje del pensamiento" — Samuel Johnson

```
/pato/ ≠ /bato/   →  par mínimo
```
````
