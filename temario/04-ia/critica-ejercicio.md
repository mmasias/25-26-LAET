# Ejercicio de Evaluación Crítica y Ética

## Objetivo

Analizar críticamente todas las tecnologías estudiadas y sus implicaciones éticas.

## Nivel: Medio

## Enfoque

Reflexión crítica, debate, identificación de problemas


## Parte 1: Casos de fracaso de las tecnologías (25 min)

**Objetivo:** Documentar situaciones donde cada tecnología falló espectacularmente.

```markdown
Formato de análisis:

Tecnología: [NOMBRE]
Caso de fracaso: [DESCRIPCIÓN]
Qué falló: [ANÁLISIS]
Qué debería haber hecho el humano: [REFLEXIÓN]


Análisis de casos:

1. Regex
   Caso: Expresión regular que "funciona" pero elimina contenido válido

   Ejemplo: Extraer emails pero eliminar también texto que contiene "@"
   como parte de una palabra o username.

   Qué falló: ___
   Cómo evitar: ___

2. PLN (spaCy)
   Caso: POS tagging incorrecto para términos del lenguaje digital

   Ejemplo: "post" clasificado como sustantivo cuando funciona como verbo

   Qué falló: ___
   Cómo validar: ___

3. Traducción automática (DeepL/Google)
   Caso: Traducción literal que pierde significado

   Ejemplo: "Engagement" traducido literalmente en español cuando se usa
   como anglicismo técnico

   Qué falló: ___
   Cómo solucionar: ___

4. IA generativa
   Caso: Alucinación en definición de término

   Ejemplo: LLM inventa origen etimológico de "tuitear"

   Qué falló: ___
   Cómo detectar: ___

5. Prompting
   Caso: Prompt que genera ejercicios inapropiados para el nivel

   Ejemplo: Ejercicio "B1" que usa vocabulario C1

   Qué falló: ___
   Cómo corregir: ___
```


## Parte 2: Análisis de sesgos (25 min)

**Objetivo:** Identificar sesgos presentes en las herramientas estudiadas.

```markdown
Para cada tecnología, analizar sesgos detectados:

1. Corpus de entrenamiento
   Pregunta: ¿Quiénes están representados en los datos?

   Análisis:
   - El corpus de lenguaje digital: ¿qué variedades de español?
   - ¿Sesgo geográfico? (España vs Latinoamérica)
   - ¿Sesgo de edad? (jóvenes vs mayores)
   - ¿Sesgo de plataforma? (Twitter/X vs Instagram vs TikTok)

   Consecuencias: ___

2. spaCy (modelo de PLN)
   Pregunta: ¿Cómo afecta el entrenamiento del modelo?

   Análisis:
   - ¿Reconoce igual de bien variedades de español diferentes?
   - ¿Maneja bien neologismos del lenguaje digital?
   - ¿POS tagging falla más en lenguaje informal?

   Consecuencias: ___

3. LLMs (ChatGPT, Claude, Gemini)
   Pregunta: ¿Qué sesgos reproduce?

   Análisis:
   - ¿Presume cierta edad/género al hablar de "influencer"?
   - ¿Valora más el español peninsular que el latinoamericano?
   - ¿Considera el lenguaje digital como "incorrecto"?

   Ejemplo de prompt para detectar sesgo:
   "Describe brevemente a un usuario típico de TikTok"

   Respuesta: ___
   ¿Qué suposiciones hace? ___

4. Prompting humano
   Pregunta: ¿Sesgos del diseñador de prompts?

   Análisis:
   - ¿Qué variedades de español se usan en ejemplos?
   - ¿Qué registros se valoran como "correctos"?
   - ¿Se privilegia cierto tipo de contenido?

   Reflexión: ___
```


## Parte 3: Implicaciones éticas (25 min)

**Objetivo:** Analizar consecuencias éticas del uso profesional de estas tecnologías.

```markdown
Temas éticos a analizar:

1. Propiedad intelectual
   Pregunta: ¿Quién es el autor de contenido generado con IA?

   Caso: Un profesor usa IA para generar ejercicios didácticos.
   ¿Debe declarar que fueron generados? ¿Debe citar al LLM usado?

   Discusión:
   - Posición A: La IA es una herramienta más, como un corrector ortográfico
   - Posición B: El contenido debe declararse como generado por IA
   - Posición C: Depende del nivel de intervención humana

   ¿Tu opinión? ___

2. Transparencia con estudiantes
   Pregunta: ¿Deben saber los estudiantes que su profesor usa IA?

   Casos:
   a) Profesor usa IA para preparar ejercicios que luego presenta como propios
   b) Profesor usa IA para corregir exámenes
   c) Profesor usa IA para generar feedback personalizado

   ¿Cuándo es éticamente necesario declarar? ___

3. Reemplazo vs asistencia
   Pregunta: ¿Qué tareas humanas pueden reemplazarse?

   Análisis por tecnología:
   - Regex: automatización de tareas repetitivas → ¿Aceptar? ___
   - PLN: análisis gramatical automático → ¿Aceptar? ___
   - TA: traducción asistida → ¿Aceptar? ___
   - IA: generación de materiales → ¿Aceptar? ___

   ¿Dónde está la frontera entre herramienta y reemplazo? ___

4. Responsabilidad profesional
   Pregunta: ¿Quién es responsable de errores?

   Caso: Un profesor usa IA para generar un ejercicio. El ejercicio
   contiene un error gramatical que los estudiantes aprenden como correcto.

   ¿Responsabilidad del profesor? ¿Del LLM? ¿De ambos?

   Reflexión: ___

5. Brecha digital
   Pregunta: ¿El uso de estas tecnologías aumenta o reduce la brecha?

   Análisis:
   - ¿Requiere acceso a tecnología costosa?
   - ¿Requiere conocimientos técnicos especializados?
   - ¿Es accesible para profesionales con recursos limitados?

   Reflexión: ___
```


## Parte 4: Debate - Declaración de uso de IA (15 min)

**Objetivo:** Posicionarse sobre la declaración de uso de IA en trabajos académicos.

```markdown
Escenario: Universidad está decidiendo política sobre IA

Contexto:
- Estudiantes pueden acceder a ChatGPT, Claude, Gemini
- Profesores pueden usar IA para preparar materiales
- No hay política clara todavía

Pregunta: ¿Deben declarar estudiantes el uso de IA en trabajos?

Posicionamientos:

A. Declaración obligatoria siempre
   Argumentos a favor:
   ___

   Argumentos en contra:
   ___

B. Declaración opcional
   Argumentos a favor:
   ___

   Argumentos en contra:
   ___

C. Sin declaración (libertad total)
   Argumentos a favor:
   ___

   Argumentos en contra:
   ___

D. Prohibición total de IA
   Argumentos a favor:
   ___

   Argumentos en contra:
   ___

Tu posición: ___
Justificación: ___
```


## Parte 5: Cuestionario de autoevaluación crítica (10 min)

**Objetivo:** Evaluar propio uso de las tecnologías estudiadas.

```markdown
Para cada tecnología, reflexionar:

1. Regex
   ¿La usaste solo cuando fue necesario o intentaste aplicar a todo?
   ___
   ¿Verificaste manualmente los resultados?
   ___
   ¿Comprendes qué hace exactamente cada patrón que escribiste?
   ___

2. PLN (spaCy)
   ¿Validaste los resultados del análisis gramatical?
   ___
   ¿Confías ciegamente en las etiquetas POS que asigna?
   ___
   ¿Sabes cuándo NO usar spaCy y hacer análisis manual?
   ___

3. Traducción automática
   ¿Hiciste post-edición de las traducciones automáticas?
   ___
   ¿Sabes qué tipo de textos son adecuados para TA y cuáles no?
   ___
   ¿Verificaste terminología especializada?
   ___

4. IA generativa
   ¿Verificaste la exactitud de información generada?
   ___
   ¿Detectaste alguna alucinación en los resultados?
   ___
   ¿Probaste múltiples prompts antes de aceptar un resultado?
   ___

5. Prompting
   ¿Iteraste tus prompts basándote en resultados?
   ___
   ¿Evalúas críticamente la calidad de outputs generados?
   ___
   ¿Sabes cuándo la IA no es la herramienta adecuada?
   ___

Reflexión general:
¿Qué área necesitas mejorar en uso crítico de tecnología?
___
```


## Parte 6: Síntesis final - Qué se llevan (10 min)

**Objetivo:** Integrar aprendizajes del curso.

```markdown
Tecnologías estudiadas:
- Regex: extracción de patrones
- PLN: análisis lingüístico automático
- TA: traducción asistida
- IA generativa: creación de contenido

Para cada una, indicar:

1. Lo que SÍ puede hacer (fortalezas):
   Regex: ___
   PLN: ___
   TA: ___
   IA: ___

2. Lo que NO puede hacer (limitaciones):
   Regex: ___
   PLN: ___
   TA: ___
   IA: ___

3. Cuándo NO usarla:
   Regex: ___
   PLN: ___
   TA: ___
   IA: ___

4. Rol del profesional de la lengua:
   ¿Cuál es tu valor añadido sobre la tecnología?
   ___

   ¿Qué hace un humano que ninguna de estas tecnologías puede hacer?
   ___

   ¿Cómo integrar estas herramientas en práctica profesional responsable?
   ___
```


## Entregable

**Documento con:**

1. **Casos de fracaso** (Parte 1): análisis de 5 tecnologías
2. **Análisis de sesgos** (Parte 2): sesgos identificados por tecnología
3. **Implicaciones éticas** (Parte 3): análisis de 5 temas éticos
4. **Debate IA académica** (Parte 4): posición justificada
5. **Autoevaluación** (Parte 5): reflexión sobre uso propio
6. **Síntesis** (Parte 6): fortalezas, limitaciones, rol profesional


## Hacia la herramienta final

Este ejercicio construye:
- **Consciencia crítica** sobre limitaciones y peligros de las tecnologías
- **Marco ético** para uso profesional responsable
- **Capacidad de evaluar** cuándo usar o no cada herramienta
- **Mentalidad de validación humana** como último filtro

**Conexión con todo el curso:**
- Regex básico → PLN → IA generativa: progresión de herramientas
- Evaluación crítica: integración de todo lo aprendido con enfoque ético

**Producto final del curso:**
- Profesional consciente de fortalezas y limitaciones de tecnología lingüística
- Capaz de usar herramientas de forma crítica y responsable
- Con criterio para decidir qué herramienta usar (o ninguna)
- Comprometido con validación humana y responsabilidad profesional

**Herramienta completa integrada:**
Script/flujo de trabajo que combina:
1. Regex para limpieza de corpus
2. PLN para análisis lingüístico
3. IA para generación de contenido
4. Validación humana crítica en cada paso

Fin del curso.
