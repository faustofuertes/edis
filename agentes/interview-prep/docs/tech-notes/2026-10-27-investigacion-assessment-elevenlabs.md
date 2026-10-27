# Investigación: assessment técnico inicial de ElevenLabs (CoderPad, Python)

Para: diseño del agente generador de ejercicios de Eddis (Laburen.com)
Fecha de la investigación: 27/10/2026
Autoría: borrador generado con Claude para revisar. Quien lo use tiene que revisar las fuentes y las conclusiones antes de compartirlo.

## Cómo leer este informe

Cada afirmación lleva una etiqueta:

- **[OFICIAL]**: página de ElevenLabs, CoderPad, CodeSignal o Anthropic.
- **[CANDIDATO]**: relato en primera persona de un candidato, con fecha si existe.
- **[GUÍA]**: guía de terceros (Exponent/Aced, JobsByCulture, faangapply, PracHub, Nora). Agregan reportes, a veces sin decir cuál. Sirven como señal, no como dato confirmado. Varias se citan entre sí, así que coincidir no significa que haya fuentes independientes.
- **[INFERENCIA]**: conclusión mía a partir de lo anterior.

**Límites de la búsqueda.** No pude leer Reddit, Blind (salvo títulos), Glassdoor (bloqueo 403 / verificación anti-bot), LeetCode Discuss ni 1point3acres. Varias búsquedas devolvieron un texto de negativa en vez de resultados. Lo traté como un fallo de la herramienta y seguí por otras vías. Los reportes de Glassdoor que aparecen abajo los conozco por fragmentos de buscadores y por guías que los citan, no porque haya leído la página. No encontré ningún hilo de Reddit específico sobre el assessment de ElevenLabs. Tampoco encontré videos de YouTube con contenido concreto.

---

## 1. Qué problemas toma ElevenLabs en el assessment

### Evidencia

| Fuente | Fecha | Qué dice |
|---|---|---|
| [CANDIDATO] Exponent/Aced, Software Engineer Full Stack (backend-leaning), por referido | publicado mayo 2025 | "a 90-minute CoderPad" y "The OA was just two LeetCode-medium-ish problems". Dificultad global: "Moderate". |
| [CANDIDATO] Glassdoor (fragmento de buscador) | mayo 2024 | Primera etapa: "take home leet code question style exercise with 4 questions which was not too difficult". |
| [CANDIDATO] Glassdoor (fragmento de buscador, citado por Nora) | sin fecha confirmada, ~2025-2026 | Proceso con "automated checkers initially" y "additional automated coding check first". Arranca con un screen offline de problemas LeetCode-style. |
| [GUÍA] Nora (lista de preguntas reportadas) | 2026 | Ejemplo reportado: "merging sorted lists while dropping duplicates". También cita "sophisticated, idiomatic Python beyond just passing test cases". |
| [GUÍA] Exponent/Aced, guía SWE | actualizada ~sep 2026 | "roughly 90 minutes for two to three medium-difficulty questions", que "don't need to relate to ElevenLabs's own products". Tipo de ejemplo: "A graph or tree traversal question". Se pueden testear y corregir las soluciones antes de enviar. |
| [GUÍA] JobsByCulture | 21/05/2026 | 3 problemas: 2 Medium y 1 Medium-Hard, LeetCode-style, autocorregidos. Temas: strings, arrays, estructuras de datos, con escenarios de "procesamiento de datos reales". Dificultad 2.5/5. |
| [GUÍA] faangapply | verificado jul 2026 | 2-3 problemas (2 Medium + 1 Medium-Hard). Temas: strings, arrays/hash maps, sliding window, recorrido de árbol/grafo, procesamiento de streams de datos. Los tests se pueden ejecutar antes de enviar. |
| [GUÍA] PracHub | 07/09/2026 | Advierte que el formato de 90 min no figura en la página oficial. Cita un relato (Exponent, India remoto, 2026) de un OA de 3 partes con mapas, colas y BFS, seguido de un problema de permisos. No pude leer ese relato directamente. |
| [GUÍA] Exponent/Aced, banco de preguntas ElevenLabs | 2025-2026 | Preguntas etiquetadas por candidatos, **sin decir la etapa**: "Reverse a linked list", "Longest substring without repeating characters", detectar archivos duplicados en un file system, permisos jerárquicos con herencia/override. |
| [GUÍA] TechPrep | 2026 | 2 problemas "LeetCode-medium style" en 60-90 min. |

### Síntesis

- **Cantidad.** Lo más reportado y reciente son **2 a 3 problemas en 90 minutos** (confianza media-alta). Un reporte de 2024 habla de 4 preguntas. El formato cambió o varía según el rol.
- **Dificultad.** **Medium de LeetCode**, con un posible Medium-Hard. Ningún reporte menciona Hard puro. Coincide con el mail ("no expert-level Python"). Confianza media-alta.
- **Temas con alguna evidencia.** Hash maps y conteo, strings y parsing, arrays/two pointers/sliding window, listas enlazadas o merge de listas ordenadas, BFS/DFS en árboles y grafos, colas. Los problemas "prácticos" (permisos jerárquicos, archivos duplicados, flujo de doblaje) aparecen sobre todo en la **ronda de código práctico en vivo, no en el assessment**. Confianza media.
- **DP, heaps y grafos con pesos.** No encontré ningún reporte que los mencione para este assessment. [INFERENCIA] Igual pueden aparecer como Medium-Hard. Conviene darles prioridad media, no alta.
- **Problemas con temática de audio en el assessment.** No hay evidencia. La guía de Exponent dice que los problemas no tienen por qué estar ligados al producto.
- **Enunciados reales completos.** No encontré ninguno y no los busqué.

---

## 2. Cómo funciona CoderPad en modo assessment / take-home

### Qué producto de CoderPad usa probablemente

CoderPad tiene dos productos que sirven para un take-home:

1. **CoderPad Screen**: tests asincrónicos con preguntas autocorregidas por "validators".
2. **CoderPad Interview, take-home project**: un pad con temporizador y tests opcionales.

[INFERENCIA, confianza media] Lo más probable es que ElevenLabs use **Screen**:

- El mail habla de "binary scoring", un tiempo máximo fijo y un link que vence.
- El permiso de usar Google/Stack Overflow calca el texto de la guía oficial de Screen: "you can make use of all available resources like StackOverflow or Google — however you may not have someone else actively solve the question for you".

Para confirmarlo, el alumno puede abrir el tutorial del link. La interfaz de Screen está basada en VS Code/Monaco.

### Datos oficiales de CoderPad Screen

Fuente: guía del candidato, actualizada 27/03/2026.

- Al abrir el link hay un **tutorial de práctica** que se puede repetir. Muestra **cuántas preguntas hay** y el **tiempo máximo**.
- En las preguntas de programación hay código inicial ("starter code"). Hay que resolver "in the most efficient way in order to get all the points". **La eficiencia cuenta**: los validators pueden incluir casos grandes. [INFERENCIA]
- **Los validators que puntúan no son los mismos tests que ve el candidato.** Dice textualmente: "your attempt might 'pass' even though your solution does not work properly". Pasar los tests visibles no garantiza el puntaje.
- Si se acaba el tiempo, el código se envía automáticamente y **puede sumar puntos igual**.
- **El candidato no ve su puntaje.** Solo el reclutador decide si se lo comparte.
- Atajos de teclado del editor Monaco (el de VS Code). En Screen, CoderPad describe resaltado de errores y autocompletado (página de marketing).
- Algunas empresas permiten **pedir otro intento** desde el mail de resultados. Es opcional y depende de la empresa.
- Sobre IA: CoderPad ofrece una ventana "AI Assist", pero solo si la empresa la habilita (página para candidatos, 16/10/2026). En este caso el mail de ElevenLabs la prohíbe.
- Anti-trampa, según la integración con Greenhouse: preguntas aleatorizadas y opción de bloquear el pegado. Screen guarda un **playback** del código. [INFERENCIA] Pegar bloques grandes de código puede quedar registrado o estar bloqueado.

### Datos oficiales de take-home en CoderPad Interview (por si es este producto)

- El pad tiene un temporizador visible, y por defecto es de 2 h.
- El código se envía con "Submit Take Home" o automáticamente cuando vence el tiempo.
- Los tests pueden ser **visibles u ocultos**. El candidato corre los visibles con "Run selected test cases" y ve pass/fail, el resultado esperado y el obtenido. Los ocultos corren igual y los ve el entrevistador.
- La firma de la función se define con tipos simples (Integer, String, Integer Array, String Array).
- Se registra cada tecla (playback).
- Hay un botón Run, salida de consola y un REPL (IPython en Python). El autocompletado se puede activar.

### Entorno Python

- **Screen** (página "what compiler does my test run on", sep 2025): **Python 3.11.5** con NumPy 1.20.2, pandas 1.2.4 y SciPy 1.6.3, 768 MB de memoria y un tiempo límite de ejecución de pocos segundos por corrida. El valor exacto para Python no se pudo leer con certeza.
- **Interview** (página de Python 3): CPython 3.10 con IntelliSense, unittest/pytest, y en una sección heredada requests, numpy, pandas, etc.
- [INFERENCIA] Para problemas LeetCode-style alcanza con la stdlib. **No conviene apoyarse en `sortedcontainers`**, porque no figura como disponible.

### Qué significa "binary scoring" en la práctica

[INFERENCIA, confianza media]

- Cada problema, o cada caso de test oculto, suma solo si la salida es exactamente la correcta y dentro del tiempo límite.
- No hay puntaje parcial por el razonamiento ni por un código "casi bien".

Implicancias para entrenar:

- Leer bien el formato de entrada/salida.
- Cubrir los casos borde.
- Evitar soluciones O(n²) cuando n puede ser grande.
- No dejar prints de debug si la salida se compara por stdout.

---

## 3. Qué significa "no hace falta Python experto"

No hay fuente oficial que lo detalle. Esto es lo que aparece:

- [GUÍA] Nora y [CANDIDATO] Glassdoor piden "Python idiomático/sofisticado más allá de pasar tests". Parece referirse más a las rondas en vivo que al assessment automático.
- [GUÍA] Exponent (sobre Anthropic, aplica igual) recomienda dominar la stdlib: map, filter, sort, etc.

[INFERENCIA] Probablemente significa: no hace falta metaprogramación, decoradores, async, typing avanzado ni dominar CPython por dentro. Sí hace falta escribir rápido y bien con lo básico. Lista recomendada:

| Área | Qué dominar |
|---|---|
| Tipos base | slicing, comprensiones (list/dict/set), `enumerate`, `zip`, `sorted(key=..., reverse=...)`, `min/max(key=...)`, desempaquetado, `str.split/join/strip`, `ord/chr`, `int(x, base)`, `float('inf')` |
| `collections` | `Counter` (incluye `most_common`), `defaultdict`, `deque` (cola O(1), BFS, ventana deslizante) |
| `heapq` | `heappush/heappop`, `nsmallest/nlargest`, max-heap con negativos, tuplas como prioridad |
| `bisect` | `bisect_left/right`, `insort` (búsqueda binaria en listas ordenadas) |
| `itertools` | `accumulate` (sumas prefijas), `groupby`, `combinations/permutations/product`, `chain` |
| `functools` | `lru_cache`/`cache` para DP top-down, `cmp_to_key` |
| `math` | `gcd`, `ceil/floor`, `isqrt` |
| Otros | `sys.setrecursionlimit` o DFS iterativo con pila. Leer stdin con `sys.stdin` si la pregunta usa I/O por consola (en Screen es común que el starter code lea la entrada). `dataclasses` o clases simples para modelar. |
| Complejidad | saber que `list.pop(0)` e `in list` son O(n), y que `in set/dict` es O(1) en promedio |

---

## 4. Qué pasa después del assessment en ElevenLabs

**[OFICIAL]** La página de careers dice que los pasos "vary by role, but most processes include a pre-screen, virtual interviews (sometimes with a skills assessment like a take-home or case study), a hiring manager conversation, and a final round with a founder or Bar Raiser".

Según el blog oficial (2025), antes de hablar con un reclutador humano los candidatos interactúan con agentes de voz de IA ("AI Becky" y "AI Oscar"), que responden dudas del proceso.

**[CANDIDATO + GUÍAS]** Secuencia típica para SWE, reportada en 2025-2026:

1. **Llamada con reclutador**, de unos 30 min, sobre motivación y proyectos propios. En algunos casos va antes del assessment y en otros después.
2. **Assessment CoderPad**, asincrónico.
3. **Loop final virtual** (el reclutador envía un PDF con los temas):
   - **Behavioral de ownership**, sobre proyectos llevados a producción por uno mismo.
   - **Código práctico en vivo**, de unos 60 min, sobre un escenario de cliente: workflow de doblaje con planilla, ediciones, aprobaciones y propagación de estados, o permisos jerárquicos. Varios lo reportan como la ronda más difícil.
   - **Product decomposition**: diseño de producto desde la UI hasta el modelo de datos, sin código.
4. A veces, charla final con founder o liderazgo.

Duración total reportada: de 2 a 5 semanas.

Variantes:

- **Frontend**: debug en React, por ejemplo transcripción desincronizada con el audio.
- **Forward Deployed Engineer**: reportan CodeSignal en lugar de CoderPad (faangapply).

---

## 5. OpenAI y Anthropic (breve)

**Anthropic**

- [OFICIAL] Política de IA para candidatos: los take-homes y las entrevistas en vivo se hacen **sin IA** salvo que se indique lo contrario. Para preparar la entrevista sí se puede usar IA.
- [GUÍA] Exponent (actualizada ~sep 2026): el screen técnico dura 60-90 min. Se hace **en CodeSignal, autoguiado y con cámara**, o en vivo en un entorno Python tipo Colab. En los dos formatos el desafío es **por niveles que escalan**: se arranca simple y se van sumando requisitos sobre el propio código. Recomienda entregar algo que funcione en cada nivel.
- [OFICIAL CodeSignal] El "Industry Coding Framework" es **una sola tarea de proyecto con 4 niveles progresivos**, en 90 minutos como máximo, y no se espera terminarla entera. Cada nivel agrega métodos manteniendo los contratos anteriores: primero condicionales/bucles, después estructuras de datos, después errores y casos borde, después refactor y extensión.
- [INFERENCIA] Que Anthropic use exactamente este framework es lo que dicen las guías, pero no tiene confirmación oficial de Anthropic.
- Ejercicio típico para practicar: implementar una clase tipo "banco", "base de datos en memoria" o "file system" que crece nivel por nivel.

**OpenAI**

- La guía oficial (openai.com/interview-guide) bloqueó el acceso automático y no la pude leer.
- [GUÍA] Exponent (~sep 2026):
  - A veces hay un OA tipo HackerRank (2 preguntas, 90-120 min), sobre todo para new grad.
  - Después, un screen técnico de 2 rondas de 60 min (código y diseño de sistemas).
  - El código es **práctico y con mucha implementación**: servicios con stubs, recrear el comportamiento de un sistema real. Menos LeetCode puro, aunque los algoritmos clásicos siguen apareciendo en el OA.
  - Las preguntas rotan.

---

## Tabla final: qué debería practicar un alumno para este assessment

| Tema | Dificultad | Prioridad | Evidencia |
|---|---|---|---|
| Hash maps y conteo de frecuencias (`Counter`, `defaultdict`) | Easy-Medium | Alta | Guías JobsByCulture y faangapply (2026). Inferencia: base de casi todo Medium |
| Strings: parsing, manipulación, sliding window (p. ej. substring sin repetir) | Medium | Alta | Guías 2026 y banco de preguntas de Exponent (etapa no especificada) |
| Arrays: two pointers, sumas prefijas, ordenamiento con `key` | Medium | Alta | Guías 2026 |
| Listas ordenadas / listas enlazadas (merge, dedup, reverse) | Easy-Medium | Media-alta | Nora ("merging sorted lists while dropping duplicates") y Exponent ("reverse a linked list") |
| BFS/DFS en árboles y grafos, colas (`deque`), visited set | Medium | Alta | Exponent (guía, ~sep 2026), PracHub (OA con mapas/colas/BFS), faangapply |
| Simulación / procesamiento de "streams" o registros (aplicar operaciones y llevar estado) | Medium | Media-alta | Guías 2026 ("data stream processing", "real-world data processing"). Inferencia |
| Problema Medium-Hard: heaps (`heapq`), búsqueda binaria (`bisect`), intervalos | Medium-Hard | Media | Guías reportan 1 Medium-Hard. Sin tema confirmado (inferencia) |
| Programación dinámica básica (1D/2D, `lru_cache`) | Medium | Media-baja | Sin evidencia específica. Cobertura por si acaso |
| Estructuras jerárquicas con herencia (permisos, file system) | Medium | Media (más para la ronda en vivo) | Glassdoor 2024 y Exponent: aparece en la entrevista técnica, no en el OA |
| Eficiencia: evitar O(n²), elegir estructuras O(1) | transversal | Alta | Oficial CoderPad: "most efficient way… to get all the points" y validators ocultos |
| Casos borde y formato exacto de entrada/salida | transversal | Alta | Oficial CoderPad: los validators difieren de los tests visibles. Mail: scoring binario |
| Simulacro: 2-3 Medium en 90 min, en editor simple, sin IA, con stdlib | transversal | Alta | Candidato 2025 + guías 2026 + mail |
| Gestión del tiempo: entregar algo funcionando en cada problema | transversal | Alta | Oficial CoderPad: el código se envía al vencer el tiempo y puede sumar |

[INFERENCIA] Ideas para el agente de ejercicios:

- Generar sets de 2-3 problemas (2 Medium + 1 Medium-Hard) con firma de función y tipos simples.
- Incluir tests visibles pocos y simples, y una batería **oculta** con casos borde y casos grandes (para medir eficiencia).
- Corregir con pass/fail binario por problema.
- Fijar un límite de 90 min.

---

## Fuentes

**Oficiales**

- ElevenLabs Careers (FAQ del proceso): https://elevenlabs.io/careers
- ElevenLabs blog, "Agents and the candidate experience" (2025): https://elevenlabs.io/blog/agents-and-candidate-experience
- CoderPad, Screen preparation guide (act. 27/03/2026): https://coderpad.io/resources/docs/for-candidates/screen-preparation-guide/
- CoderPad, For candidates (act. 16/10/2026): https://coderpad.io/resources/docs/for-candidates/
- CoderPad, Interview preparation guide (act. 16/10/2026): https://coderpad.io/resources/docs/for-candidates/interview-preparation-guide/
- CoderPad, Test cases (take-home, act. 02/02/2023): https://coderpad.io/resources/docs/interview/question-bank/test-cases/
- CoderPad, Take-home projects quick start (act. 26/08/2024): https://coderpad.io/resources/docs/interview/quick-start-guides/interviewers/take-home-projects/
- CoderPad Screen, compiladores y versiones (act. 17/09/2025): https://coderpad.io/resources/docs/screen/more-screen-resources/supported-languages-frameworks-technologies/what-compiler-does-my-test-run-on/
- CoderPad, Python 3: https://coderpad.io/languages/python-3/
- CoderPad Screen en Greenhouse: https://www.greenhouse.com/integrations/coderpad-screen
- Anthropic, Guidance on candidates' AI usage: https://www.anthropic.com/candidate-ai-guidance
- CodeSignal, Industry Coding Framework (datasheet): https://discover.codesignal.com/rs/659-AFH-023/images/CodeSignal-Industry-Coding-Framework-Datasheet.pdf
- OpenAI interview guide (no se pudo leer, bloqueo 403): https://openai.com/interview-guide/

**Relatos de candidatos**

- Exponent/Aced, ElevenLabs SWE Full Stack (mayo 2025): https://www.tryexponent.com/experiences/eleven-labs-software-engineer-interview-8e1b37
- Exponent/Aced, ElevenLabs SWE (2026, sin detalle): https://www.tryexponent.com/experiences/eleven-labs-software-engineer-interview-605512
- Exponent/Aced, listado de experiencias ElevenLabs: https://www.aced.io/experiences?company=eleven-labs
- Glassdoor, ElevenLabs (mayo 2024, 4 preguntas + permisos jerárquicos; leído solo por fragmento de buscador): https://www.glassdoor.fr/Entretien/ElevenLabs-Entretien-E9081894-RVW89085040.htm
- Glassdoor, ElevenLabs (screen offline LeetCode-style, luego reclutador y entrevista en vivo; fragmento): https://static.glassdoor.co.nz/Interview/ElevenLabs-Interview-E9081894-RVW103823639.htm
- Glassdoor, índice general: https://www.glassdoor.com/Interview/ElevenLabs-Interview-Questions-E9081894.htm

**Guías de terceros**

- Exponent/Aced, guía SWE ElevenLabs (~sep 2026): https://www.tryexponent.com/guides/elevenlabs-software-engineer-interview
- Exponent/Aced, preguntas ElevenLabs: https://www.tryexponent.com/guides/elevenlabs-software-engineer-interview/questions
- JobsByCulture (21/05/2026): https://jobsbyculture.com/blog/elevenlabs-interview-prep-2026
- faangapply (verificado jul 2026): https://faangapply.io/companies/elevenlabs/interview
- PracHub (07/09/2026): https://prachub.com/resources/elevenlabs-software-engineer-interview-guide-2026-coderpad-audio-streaming-and-product-engineering
- Nora (2026): https://interview.norahq.com/interview-guides/elevenlabs-software-engineer-interview-guide-2026
- TechPrep (2026): https://www.techprep.app/blog/elevenlabs-interview-process
- Exponent/Aced, guía SWE Anthropic (~sep 2026): https://www.tryexponent.com/guides/anthropic-software-engineer-interview
- Exponent/Aced, guía SWE OpenAI (~sep 2026): https://www.tryexponent.com/guides/openai-software-engineer-interview
