# Práctica autónoma - Regex básico

Material de práctica opcional para consolidar lo trabajado en clase.

## Corpus de trabajo

```text
🚀 ¡El término "influencer" está viralizando! #LenguajeDigital https://t.co/abc123

@usuario1 De acuerdo: el concepto de "cancelar" cambió en 2024.

Thread sobre neologismos: "woke" pasó del inglés al español... https://www.ejemplo.com/articulo

Ghosting no es solo de citas. También en profesional cuando alguien desaparece.

¿Alguien más usa "flexear"? Antes era solo fitness, ahora está en todo... #Neologismos
```

Herramienta de trabajo: [regexr.com](https://regexr.com/). No hay una única solución correcta para cada ejercicio: lo relevante es documentar qué captura el patrón y por qué.

---

## Ejercicios

**1. Limpiar ruido**

El corpus contiene elementos que no aportan información lingüística: URLs, menciones y hashtags. ¿Qué queda una vez eliminados? ¿Se ha perdido algo de valor?

**2. Extraer candidatos a términos**

Las palabras entre comillas son candidatos a términos o neologismos. ¿Lo son todas? ¿Hay excepciones?

**3. Palabras terminadas en `-ing`**

Un patrón para palabras terminadas en `-ing` debería capturar anglicismos. ¿Es eso lo que ocurre? ¿Qué otros resultados aparecen?

**4. Libre**

Diseñar un patrón para extraer algo de interés propio en el corpus. Documentar qué se buscaba, qué capturó el patrón y qué ajustes fueron necesarios.
