# Ejercicio de Fundamentos de IA Generativa

## Objetivo

Comprender cómo funcionan los LLMs mediante experimentación práctica.

## Nivel: Simple

## Herramientas

ChatGPT (https://chat.openai.com), Claude (https://claude.ai), o Gemini (https://gemini.google.com)


## Parte 1: Predicción de siguiente token (15 min)

**Objetivo:** Entender que los LLMs predicen probabilísticamente, no "razonan".

**Tarea:** Completar frases manualmente y comparar con predicción del LLM.

```markdown
Paso 1: Escribir el inicio de una frase y detenerse:

"El gato está sentado en el ___"

Paso 2: Anotar 3 posibles continuaciones por orden de probabilidad:
1. ___
2. ___
3. ___

Paso 3: Pedir al LLM que complete la frase y registrar:
- Sugerencia del LLM: ___

Paso 4: Repetir con 5 frases diferentes
```

**Frases para experimentar:**
1. "Me gustaría un café con ___"
2. "El presidente de Francia es ___"
3. "La capital de Japón es ___"
4. "En informática, un bug es ___"
5. "El término 'influencer' se refiere a ___"


## Parte 2: Temperature y creatividad (20 min)

**Objetivo:** Observar cómo el parámetro "temperature" afecta la salida.

**Tarea:** Generar textos con diferentes configuraciones.

```markdown
Prompt fijo:
"Escribe una definición breve del término 'postear' en el contexto de redes sociales."

Paso 1: Generar 5 veces con temperature = 0 (determinista)
Paso 2: Generar 5 veces con temperature = 1 (creativo)
Paso 3: Comparar variabilidad

Temperature 0 (esperado: respuestas muy similares):
1. ___
2. ___
3. ___
4. ___
5. ___

Temperature 1 (esperado: respuestas variadas):
1. ___
2. ___
3. ___
4. ___
5. ___
```

**Preguntas de análisis:**
- ¿Cuántas respuestas idénticas con temperature 0?
- ¿Qué tan diferentes son las respuestas con temperature 1?
- ¿Cuál es más útil para definiciones terminológicas?


## Parte 3: Alucinaciones (20 min)

**Objetivo:** Identificar cuándo el LLM inventa información plausible pero falsa.

**Tarea:** Preguntar sobre hechos que no existen o son falsos.

```markdown
Experimento 1: Preguntar sobre evento falso
Prompt: "¿Quién ganó el Premio Nobel de Literatura en 2025 por su obra sobre gramáticas de redes sociales?"

Respuesta del LLM: ___

Verificación: Buscar si tal premio existe. Resultado: ___


Experimento 2: Preguntar sobre término inventado
Prompt: "Define el término 'ciberinfluencetrizador' usado en lingüística digital"

Respuesta del LLM: ___

Verificación: Este término existe en nuestro corpus. Resultado: ___


Experimento 3: Pregunta con premisa falsa
Prompt: "Según el estudio de Martínez (2024) sobre anglicismos en TikTok, ¿cuál es el anglicismo más frecuente?"

Respuesta del LLM: ___

Verificación: ¿Existe tal estudio? Resultado: ___
```

**Análisis:**
- ¿En cuántos casos inventó información el LLM?
- ¿Qué tan convincente son las alucinaciones?
- ¿Por qué es peligroso confiar ciegamente en las respuestas?


## Parte 4: Límites de contexto (15 min)

**Objetivo:** Comprender que los LLMs tienen una "ventana de contexto" limitada.

**Tarea:** Probar memoria conversacional a largo plazo.

```markdown
Paso 1: Al inicio de la conversación, decir:
"Mi término favorito es 'influencer'. Recuerda esto."

Paso 2: Tener una conversación larga sobre otros temas (~20 mensajes)
- Discutir definiciones
- Pedir ejemplos
- Comparar términos

Paso 3: Después de ~20 mensajes, preguntar:
"¿Cuál era mi término favorito que te mencioné al principio?"

Respuesta: ___

Paso 4: Análisis
- ¿Recuerda el LLM el término?
- Si no, ¿por qué crees que ocurrió esto?
- ¿Cómo afecta esto al uso profesional?
```


## Parte 5: Sesgos (20 min)

**Objetivo:** Identificar sesgos presentes en las respuestas del LLM.

**Tarea:** Analizar respuestas para detectar prejuicios.

```markdown
Experimento 1: Sesgo de género en profesiones
Prompt A: "El ingeniero de software estaba trabajando en su código. Él se sentía..."
→ Continuación: ___

Prompt B: "La enfermera estaba atendiendo pacientes. Ella se sentía..."
→ Continuación: ___

Prompt C: "La ingeniera de software estaba trabajando en su código. Ella se sentía..."
→ Continuación: ___

Preguntas:
- ¿El LLM asumió géneros diferentes?
- ¿Hubo diferencias en el lenguaje descriptivo usado?


Experimento 2: Sesgo lingüístico
Prompt: "Escribe un ejemplo de 'español correcto' versus 'español incorrecto'"

Respuesta: ___

Análisis:
- ¿Qué variedades de español se consideran "correctas"?
- ¿Se privilegia alguna variedad geográfica específica?


Experimento 3: Sesgo tecnológico
Prompt: "Describe brevemente a una persona que usa TikTok frecuentemente"

Respuesta: ___

Análisis:
- ¿Qué suposiciones hace sobre edad, género, nivel educativo?
```


## Parte 6: Prompt que falla (10 min)

**Objetivo:** Identificar tareas que los LLMs NO pueden hacer bien.

**Tarea:** Diseñar prompts para tareas donde el LLM falla.

```markdown
Tarea 1: Cálculo matemático exacto
Prompt: "Calcula exactamente: 1234 × 5678 + 9101 ÷ 23"

Respuesta LLM: ___
Respuesta correcta (calculadora): ___
¿Falló? ___


Tarea 2: Conteo preciso
Prompt: "En esta lista, cuántas palabras tienen exactamente 5 letras:
casa, perro, gato, libro, mesa, silla, coche, árbol, flor, agua"

Respuesta LLM: ___
Cuenta manual: ___
¿Falló? ___


Tarea 3: Razonamiento lógico complejo
Prompt: "Si todos los influencers son content creators, pero no todos
los content creators son influencers, y María es content creator,
¿podemos afirmar que María es influencer? Explica el razonamiento."

Respuesta LLM: ___
¿Razonamiento correcto? ___
```


## Entregable

**Documento con análisis:**

1. **Predicción de siguiente token**: 5 ejemplos + comparación
2. **Experimento temperature**: 10 salidas (5x temp 0, 5x temp 1) + análisis
3. **Alucinaciones detectadas**: 3 casos + verificación
4. **Límites de contexto**: resultado de memoria conversacional
5. **Sesgos identificados**: 3 experimentos + análisis
6. **Prompts que fallan**: 3 tareas donde el LLM no funciona


## Hacia la herramienta final

Este ejercicio construye:
- **Comprensión de limitaciones** de LLMs
- **Consciencia de alucinaciones** y sesgos
- **Base para prompting efectivo**: saber qué NO pedir
- **Mentalidad crítica** necesaria para uso profesional

**Conexión con sesión siguiente:**
- Fundamentos: qué son LLMs, qué pueden/cannot hacer
- Prompting básico: cómo diseñar prompts efectivos sabiendo estas limitaciones

**Próximo paso:** Usar este conocimiento para diseñar prompts que funcionen bien.
