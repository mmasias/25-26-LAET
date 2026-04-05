# ABC Notation

> Música como texto ASCII: partitura sin pentagrama

**1991 · Chris Walshaw · Lenguaje de descripción musical**

## ¿Por qué?

La música tradicional de tradición oral (folk irlandés, escocés, inglés) se transmitía de músico a músico. Los formatos de notación musical existentes (MIDI, Sibelius, Finale) eran binarios o propietarios: imposibles de escribir en un email, de versionar en un repositorio, de indexar con grep. Walshaw necesitaba algo que cualquier músico pudiese escribir en texto plano, compartir por email y leer sin software especializado.

## ¿Qué?

Sistema de notación musical en texto plano. Cada nota es un carácter; la cabecera declara tonalidad, compás y tempo. Renderizable en partitura o MIDI por múltiples herramientas. El corpus *The Session* contiene más de 40.000 melodías en ABC, y ese dataset se ha usado para entrenar modelos generativos de música folk.

## ¿Para qué?

Archivo y transmisión de música tradicional, análisis computacional de melodías, codificación de corpus musicales, generación algorítmica de música. La notación textual hace que la música sea tan procesable como el lenguaje natural.

## ¿Cómo?

> [LivePreview](https://www.abcjs.net/abcjs-editor.html)

### Sintaxis

| Construcción | Significado |
|---|---|
| `X:1` `T:título` | cabecera: índice y título |
| `M:3/4` `L:1/8` | compás y duración por defecto |
| `K:Dmaj` | armadura (_Key_) |
| `A B c d` | notas (mayúsc = octava baja, minúsc = alta) |
| `z` / `\|` | silencio / barra de compás |

### Ejemplo

```abc
X:1
T:Romance del prisionero
C:Anónimo (tradición oral castellana, s. XV)
M:4/4
L:1/8
Q:1/4=96
K:Dmin
|: D2 F2 A2 F2 | E2 D2 D4 |
   F2 G2 A2 G2 | F6 z2   |
   A2 A2 G2 F2 | E2 F2 G4 |
   F2 E2 D2 C2 | D8      :|
```

```abc
X:2
T:Highway to Hell
C:AC/DC - Young, Young & Johnson (1979)
M:4/4
L:1/8
Q:1/4=116
K:Amaj
% Intro - riff de acordes
|: "A5"[A,EA]4 z2 [A,EA]2 | "D/F#"[^FAd]4 "G5"[GBd]4 :|
% Estrofa - "Livin' easy, livin' free"
"D/F#"e4 z2 e2 | "G5"d4 B4 | "D/F#"e3 d B3 A | "A5"A8 |
"D/F#"e4 z2 e2 | "G5"d4 d4 | "D/F#"B3 A "G5"G4 | "A5"A8 |
% Estribillo - "I'm on the highway to hell"
"A"e2 e2 e2 d2 | "D/A"d4 A4 | "G5"B4 "D/F#"^f4 | "A"e8 |
"A"e2 e2 e2 d2 | "D/A"d4 A4 | "G5"B2 A2 "D/F#"^f4 | "A"A8 |
```
