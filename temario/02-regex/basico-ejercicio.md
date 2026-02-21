# Ejercicio Regex básico

## Objetivo

Aplicar regex básico para limpiar un corpus de tweets/posts sobre lenguaje contemporáneo y extraer los primeros candidatos a términos.

## Nivel: Simple

## Corpus de trabajo

50 tweets/posts sobre lenguaje digital (proporcionado en clase).

## Parte 1: Limpieza de corpus (30 min)

El corpus contiene elementos que no aportan información lingüística:

```text
🚀 ¡El término "influencer" está viralizando! #LenguajeDigital https://t.co/abc123

@usuario1 De acuerdo: el concepto de "cancelar" cambió en 2024.

Thread sobre neologismos: "woke" pasó del inglés al español... https://www.ejemplo.com/articulo

Ghosting no es solo de citas. También en profesional cuando alguien desaparece.

¿Alguien más usa "flexear"? Antes era solo fitness, ahora está en todo... #Neologismos
```

**Tarea:** Usar regexr.com para limpiar el corpus aplicando:

1. `https?://[^\s]+` → Eliminar URLs
2. `@[\w]+` → Eliminar menciones
3. `#[\w]+` → Eliminar hashtags

**Resultado esperado:**
```text
El término influencer está viralizando.

De acuerdo: el concepto de cancelar cambió en 2024.

Thread sobre neologismos: woke pasó del inglés al español.

Ghosting no es solo de citas. También en profesional cuando alguien desaparece.

¿Alguien más usa flexear? Antes era solo fitness, ahora está en todo...
```

## Parte 2: Extracción de patrones básicos (30 min)

**Tarea:** Encontrar en el corpus limpio:

1. **Todas las fechas** en formato dd/mm/aaaa
   - Regex: `\d{2}/\d{2}/\d{4}`

2. **Todas las palabras entre comillas**
   - Regex: `"([^"]+)"`

3. **Todos los anglicismos terminados en -ing** (bonus)
   - Regex: `\b[a-zA-Z]+ing\b`

**Entrega:** Documento con:
- Corpus original
- Regexes utilizados (explicados brevemente)
- Corpus limpio
- Lista de elementos extraídos

## Hacia la herramienta final

Este ejercicio sienta las bases para:
- Corpus limpio para análisis posteriores
- Primeros candidatos a términos (palabras entre comillas, anglicismos)
- Uso de regexr.com como entorno de experimentación
