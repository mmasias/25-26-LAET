# Expresiones regulares

## ¿Por qué?

En los años 50, Stephen Kleene, matemático y lógico, estudiaba sistemas formales de representación de lenguajes. Se enfrentaba a un problema teórico fundamental: ¿Qué es un lenguaje? ¿Cómo se pueden describir patrones en símbolos? ¿Existe una forma matemática de caracterizar qué cadenas son válidas en un lenguaje y cuáles no?

No buscaba "limpiar corpus" ni "extraer datos". Buscaba una notación formal para describir conjuntos de cadenas, una herramienta matemática para caracterizar lenguajes.

## ¿Qué?

La solución que apareció: **expresiones regulares**

Una notación formal para describir patrones en cadenas de texto. Diseñada originalmente para problemas teóricos de lenguajes formales, se convirtió en una herramienta omnipresente: cualquier búsqueda en un editor de texto, cualquier validación de formulario, cualquier filtro de datos usa regex.

Historia progresiva:

- **1950s:** Stephen Kleene define "expresiones regulares" en teoría de autómatas y lenguajes formales. Pregunta fundamental: ¿Qué lenguajes puede reconocer una máquina de estados finita?

- **1960s:** Ken Thompson implementa regex en el editor QED, luego en ed. Primera vez que la abstracción matemática se convierte en herramienta práctica de Unix.

- **1970s-80s:** regex se estandariza en herramientas Unix (grep, sed, awk). Se vuelve herramienta estándar de administradores de sistemas y programadores.

- **1980s-90s:** Perl populariza regex con sintaxis más expresiva. Henry Spencer escribe librerías que se convierten en estándar de facto.

- **1990s-2000s:** regex se integra en editores de texto, IDEs, bases de datos. Se vuelve herramienta transversal a cualquier profesional que trabaje con texto.

- **Hoy:** regex es parte del flujo de trabajo diario de lingüistas, traductores, terminólogos que trabajan con corpus digitales.

Lo fascinante: una notación matemática de los años 50, diseñada para problemas teóricos, hoy permite limpiar un corpus de tweets en segundos. La teoría encontró una aplicación práctica imprevista.

## ¿Para qué?

- **Original (teoría):** Caracterizar lenguajes formales, definir qué cadenas son válidas en un lenguaje
- **Hoy (práctica):** Búsqueda y reemplazo complejo en textos, validación de datos, extracción de información, limpieza de corpus

Para lingüistas: extraer fechas, normalizar formatos, eliminar metadatos, identificar patrones sintácticos, filtrar tipos de palabras.

## ¿Cómo?

Notación formal que permite describir patrones mediante dos tipos de elementos:

- **Literales:** caracteres que se buscan tal cual
- **Metacaracteres:** símbolos especiales que representan categorías (dígitos, espacios, cualquier carácter, repeticiones)

| Problema informático | Problema lingüístico |
|---------------------|-------------------|
| `\(.*\)` - extraer contenido entre paréntesis | `\b[a-zA-Z]+ing\b` - encontrar anglicismos |
| `^function\s+\w+` - detectar declaraciones de función | `"\w+"(?=\s*quiere)` - palabras en contexto de deseo |
| `<a href="[^"]+">` - extraer enlaces HTML | `\b[A-ZÁÉÍÓÚÑ]{3,}\b` - sustantivos en mayúscula |
| `\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}` - validar IPv4 | `\b\w+(ar\|er\|ir)\b` - verbos en infinitivo |

[Regex básico](basico.md) - Práctica visual con regexr.com

[Regex aplicado](aplicado.md) - Corpus reales con hojas de cálculo

[Regex avanzado](avanzado.md) - Automatización y límites
