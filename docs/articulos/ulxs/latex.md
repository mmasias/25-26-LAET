# LaTeX

> Separa contenido de presentación desde 1984

**1984 · Leslie Lamport (sobre TeX de Knuth, 1978) · Sistema de composición tipográfica**

## ¿Por qué?

En 1976, Knuth recibió las galeradas de la segunda edición de *The Art of Computer Programming* y quedó horrorizado por la calidad tipográfica: la transición a la fotocomposición digital había destruido la belleza de la edición anterior. Decidió escribir él mismo un sistema de composición. El resultado fue TeX (1978). Lamport construyó LaTeX sobre TeX para añadir la separación entre estructura semántica y presentación: el autor marca *qué es* cada cosa; LaTeX decide *cómo se ve*.

## ¿Qué?

Sistema de preparación de documentos basado en comandos. El autor marca la estructura semántica (`\section`, `\emph`, `\cite`); LaTeX decide la presentación tipográfica. Estándar de facto en publicación científica y lingüística.

## ¿Para qué?

Artículos científicos, tesis, documentación con notación matemática o fonética compleja (IPA), libros técnicos. El sistema de kerning y justificación de TeX sigue siendo superior al de la mayoría de procesadores de texto modernos.

## ¿Cómo?

> [LivePreview](https://www.overleaf.com/)

### Sintaxis

| Construcción | Significado |
|---|---|
| `\comando{argumento}` | patrón universal |
| `\begin{entorno}...\end{entorno}` | bloques delimitados |
| `$fórmula$` | modo matemático en línea |
| `% comentario` | hasta fin de línea |
| `\\` | salto de línea explícito |

### Ejemplo

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{tipa}  % fonética IPA

\begin{document}

\section{Rasgos distintivos}

Según \cite{chomsky1968}, el rasgo
\textsc{[±sonoro]} distingue pares como:

\begin{itemize}
  \item \textipa{/p/} vs. \textipa{/b/}
  \item \textipa{/t/} vs. \textipa{/d/}
\end{itemize}

La regla de asimilación es:
\[ C \rightarrow [+son] / \underline{\hspace{1em}} [+son] \]

\end{document}
```

---

*Ver también: [Markdown](markdown.md) — alternativa ligera · [SGML](sgml.md) — antecesor*
