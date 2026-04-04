# Gherkin

> Requisitos que se ejecutan como tests

**2008 · Aslak Hellesøy (Cucumber) · DSL para especificación ejecutable**

## ¿Por qué?

Los documentos de requisitos en lenguaje natural y los tests automatizados son dos artefactos separados que se dessincronizan inevitablemente: el requisito dice una cosa, el test comprueba otra. BDD (Behavior-Driven Development) propone un único artefacto que sea legible por el cliente y ejecutable por la máquina. Gherkin es la sintaxis que lo hace posible.

## ¿Qué?

Lenguaje de dominio específico para describir comportamiento software en lenguaje natural estructurado. Los escenarios son a la vez documentación de negocio y tests automatizados. Disponible en más de 70 idiomas naturales: las palabras clave se traducen, la estructura es idéntica.

## ¿Para qué?

Especificación de requisitos funcionales, tests de aceptación, comunicación entre equipos técnicos y no técnicos. El escenario escrito por el cliente es el mismo archivo que ejecuta el framework de tests.

## ¿Cómo?

### Sintaxis

| Construcción | Significado |
|---|---|
| `Feature: nombre` | agrupa escenarios relacionados |
| `Scenario: descripción` | caso de prueba |
| `Given` / `When` / `Then` | precondición / acción / resultado esperado |
| `And` / `But` | continuación del paso anterior |
| `\| col1 \| col2 \|` | tabla de datos inline |

### Ejemplo

```gherkin
# language: es
Característica: Análisis morfológico
  Como lingüista computacional
  Quiero analizar la morfología de palabras
  Para identificar sus componentes morfémicos

  Escenario: Segmentación de palabra prefijada
    Dado que tengo la palabra "desleal"
    Cuando aplico el analizador morfológico
    Entonces obtengo los morfemas ["des-", "leal"]
    Y el morfema "des-" tiene valor "negación"
    Y el morfema "leal" es la raíz léxica

  Esquema del escenario: Palabras con sufijo -ción
    Dado que tengo la palabra "<entrada>"
    Cuando analizo el sufijo
    Entonces el resultado es "<morfema>"

    Ejemplos:
      | entrada    | morfema |
      | canción    | -ción   |
      | nación     | -ción   |
      | producción | -ción   |
```
