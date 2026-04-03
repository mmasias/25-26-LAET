# CSV

> Datos tabulares en texto plano

**1972 · IBM · Formato de intercambio de datos tabulares**

## ¿Por qué?

Las hojas de cálculo y las bases de datos almacenan datos en formatos propietarios y binarios: imposibles de leer sin el software correspondiente, difíciles de versionar. CSV resuelve el problema más simple posible: intercambiar una tabla entre dos programas distintos sin depender de ninguno de los dos.

## ¿Qué?

Comma-Separated Values. Formato de texto plano para representar datos tabulares: cada línea es una fila, cada campo está separado por comas (o punto y coma, según la configuración regional). La primera fila suele ser la cabecera con los nombres de las columnas.

## ¿Para qué?

Intercambio de corpus lingüísticos anotados, exportación de bases de datos terminológicas, hojas de cálculo, resultados de análisis. Cualquier herramienta de PLN puede leer y escribir CSV. Es el formato de entrada y salida más universal en lingüística de corpus.

## ¿Cómo?

> [LivePreview](https://csvlint.io/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `valor1,valor2,valor3` | fila de datos separada por comas |
| primera fila | cabecera con nombres de columna (convención, no obligatorio) |
| `"valor con, coma"` | comillas dobles para valores que contienen el separador |
| `"valor con ""comillas"""` | comillas dobles escapadas duplicándolas |
| _(sin comentarios)_ | limitación del formato |

### Ejemplo

```csv
token,lema,pos,frecuencia
corriendo,correr,VERB,1243
rápidamente,rápidamente,ADV,567
el,el,DET,98432
lingüista,lingüista,NOUN,89
```
