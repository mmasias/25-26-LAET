# Práctica autónoma — Regex básico

Material de práctica opcional para consolidar lo trabajado en clase.

## Corpus de trabajo

```text
🚀 ¡El término "influencer" está viralizando! #LenguajeDigital https://t.co/abc123

@usuario1 De acuerdo: el concepto de "cancelar" cambió en 2024.

Thread sobre neologismos: "woke" pasó del inglés al español... https://www.ejemplo.com/articulo

Ghosting no es solo de citas. También en profesional cuando alguien desaparece.

¿Alguien más usa "flexear"? Antes era solo fitness, ahora está en todo... #Neologismos
```

Abre [regexr.com](https://regexr.com/), pega el corpus y experimenta con los patrones siguientes. No hay una única solución correcta: el objetivo es entender qué captura cada regex y por qué.

---

## Ejercicios

**1. Limpiar ruido**

Elimina del corpus los elementos que no aportan información lingüística: URLs, menciones y hashtags.

¿Qué queda después de limpiar? ¿Hay algo que hayas eliminado sin querer?

**2. Extraer candidatos a términos**

Encuentra todas las palabras entre comillas. ¿Son todas neologismos? ¿Hay alguna que no lo sea?

**3. Palabras terminadas en `-ing`**

Encuentra todas las palabras terminadas en `-ing`. ¿El patrón captura solo anglicismos? ¿Qué otros resultados aparecen?

**4. Libre**

Diseña un patrón propio para extraer algo que te parezca interesante del corpus. Documenta qué buscabas, qué encontraste y qué ajustes tuviste que hacer.
