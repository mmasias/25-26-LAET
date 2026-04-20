# Acerca de

## ¿Por qué?

Hay dos fracasos frecuentes cuando se introduce Python a quienes no tienen experiencia previa en programación:

| Por exceso | Por fotocopia |
|-|-|
| Se empieza explicando variables, tipos, bucles, funciones. Quien estudia se pierde en la mecánica y pierde el hilo de para qué sirve. Se acaba odiando Python sin haber aprendido a aplicar la lingüística. | Se da código que funciona y se pide que se ejecute. Se aprende a hacer clic, no a razonar. Cuando algo falla, no hay forma de saber qué ocurrió porque nunca se entendió qué se estaba ejecutando. |

El objetivo es evitar los dos.

## ¿Qué?

Python no es aquí un lenguaje que se aprende: es una herramienta que extiende lo que ya se sabe hacer.

Los mismos patrones regex que funcionan en regexr.com y en Google Sheets funcionan aquí. Lo que cambia es la potencia de la herramienta que los ejecuta:

<div align=center>

| | Google Sheets | Python |
|---|:-:|:-:|
| ¿Cuántas coincidencias devuelve? | Solo la primera | Todas |
| ¿Cómo procesa el texto? | Celda a celda | El corpus entero de una vez |
| ¿Puede leer un fichero externo? | No | Sí |
| ¿Puede guardar los resultados? | Manualmente | Automáticamente |

</div>

Nótese que la columna *Python* no describe una habilidad de programación: describe el comportamiento de una herramienta. Saber usarla no requiere saber construirla.

## ¿Para qué?

Al recorrer la progresión de este bloque, se dispondrá de un script que, dado un corpus de texto, extrae todos los candidatos a término con su frecuencia de aparición. Ese listado es el punto de entrada natural al análisis terminológico con herramientas de PLN.

Conviene distinguir tres capacidades que se irán adquiriendo, por orden:

<div align=center>

| Capacidad | En qué consiste |
|---|---|
| Leer código | Entender qué hace una celda antes de ejecutarla |
| Modificar código | Cambiar el patrón o el corpus sin alterar la lógica |
| Construir desde plantilla | Adaptar una estructura dada a un problema nuevo |

</div>

No se espera poder escribir un script desde cero. Se espera poder usar uno con criterio.

## ¿Cómo?

La progresión tiene cinco fases. Cada una añade un grado de autonomía respecto a la anterior:

<div align=center>

| Fase | Descripción |
|---|---|
| **0 - Colab como herramienta** | El entorno no es un Word especial. Hay celdas de texto y celdas de código. La tarea de esta fase es reconocer el entorno y ejecutar una celda antes de ver una sola línea de Python. |
| **1 - Leer y ejecutar** | El código está escrito y comentado en lenguaje natural. Se ejecuta, se lee el output y se responden preguntas: ¿qué devuelve esto?, ¿por qué hay 7 resultados y no 1? El objetivo es construir un modelo mental de qué hace cada pieza. |
| **2 - Modificar una línea** | El código está íntegro pero hay una variable o un patrón que hay que cambiar. La lección es que el código tiene partes que cambian (el patrón lingüístico) y partes que no (la maquinaria de Python). |
| **3 - Completar huecos** | Hay celdas con huecos marcados explícitamente. Se escribe una línea, no una función entera. Es la transición de "ejecuto" a "construyo". |
| **4 - Plantilla + corpus propio** | Con una estructura completa ya dada, se adapta el patrón a un corpus propio. El código Python queda en segundo plano: lo que se diseña es la lógica lingüística. |

</div>
