# IA generativa

## ¿Por qué?

Hasta 2017, los modelos de lenguaje se basaban en n-gramas: secuencias fijas de palabras (bigramas, trigramas) que predecían la siguiente palabra basándose en estadísticas simples. "El gato está en el..." → probablemente "techo", "suelo", "cama".

Pero este enfoque tenía límites: no capturaba contexto largo, no entendía relaciones complejas entre palabras distantes, no generaba texto coherente más allá de frases cortas.

La pregunta fundamental: ¿Es posible construir un modelo que realmente entienda lenguaje? ¿O al menos que genere texto indistinguible de humano? ¿Cómo capturar significado y contexto en todas las escalas, no solo localmente?

## ¿Qué?

La solución que apareció: **LLMs (Large Language Models)**

Modelos neuronales gigantescos entrenados en billones de textos de internet que generan texto prediciendo el siguiente token, no "razonando" realmente pero produciendo outputs que parecen razonamiento.

Historia progresiva:

- **1990s-2000s:** Modelos n-grama dominan. Estadística simple: "the" suele ir seguido de sustantivo. Funciona para corrección ortográfica, predicción básica.

- **2013:** Word embeddings (Word2Vec) revoluciona. Palabras se representan como vectores numéricos. "Rey" - "hombre" + "mujer" ≈ "reina". Significado emerge de contexto de uso.

- **2017:** "Attention is All You Need" (Vaswani et al.) introduce arquitectura Transformer. Atención permite al modelo mirar todas las posiciones del texto simultáneamente, no secuencialmente. Revolución silenciosa al principio.

- **2018:** GPT-1, BERT aparecen. Pre-entrenamiento masivo + fine-tuning. Transfer learning llega a NLP. Un modelo gigante entrenado una vez, luego adaptado a tareas específicas.

- **2019-2020:** GPT-2, GPT-3 escalan. 1.5 mil millones, luego 175 mil millones de parámetros. Emergence: capacidades que no se entrenaron explícitamente aparecen "mágicamente" al escalar.

- **2022:** ChatGPT lanzado. Explosión pública. Por primera vez, IA generativa accesible a cualquiera con navegador. Adopción masiva, controversias, entusiasmo.

- **2023-2024:** GPT-4, Claude, Gemini, Llama. Modelos multimodales (texto + imagen), contexto más largo, mejor razonamiento. IA generativa se vuelve herramienta estándar en muchas profesiones.

Lo fascinante: arquitectura diseñada en 2017 para traducción automática hoy permite generar poesía, código, ejercicios didácticos, traducciones con estilo. La atención mecánica se convirtió en algo que parece comprensión.

## ¿Para qué?

- **Original:** Traducción automática, resumen de textos, generación de código
- **Hoy (lingüística):** Creación de contenido didáctico, asistencia en traducción, extracción de información, generación de ejercicios, brainstorming, refinamiento de textos

Para lingüistas: multiplicar productividad sin sacrificar calidad, generar materiales differentiated por nivel, explorar ideas, asistir en tareas repetitivas manteniendo supervisión humana.

## ¿Cómo?

LLMs generan texto mediante predicción probabilista del siguiente token, controlada por prompts que especifican tarea, contexto, formato y restricciones.

**El ecumenismo ingeniería-lingüística:**

| Tarea ingeniería | Tarea lingüística |
|---|---|
| Generación de código | Creación de ejercicios gramaticales |
| Resumen técnico | Síntesis de textos adaptados por nivel |
| Corrección de bugs | Corrección de errores gramaticales |
| Documentación de APIs | Generación de glosarios explicativos |
| Refactorización | Parafraseo de textos con diferentes registros |

[Fundamentos](fundamentos.md) - LLMs: cómo funcionan, límites, alucinaciones, sesgos

[Prompting básico](basico.md) - Estructura de prompts efectivos, patrones

[Prompting avanzado](avanzado.md) - Técnicas complejas: few-shot, chain-of-thought

[Traducción/localización](traduccion.md) - Uso de LLMs en traducción, post-edición

[Creación de contenido](creacionContenido.md) - Generación de materiales didácticos

[Evaluación crítica](critica.md) - Límites, sesgos, implicaciones éticas
