# Relevamiento inicial — interview-prep (Eddis)

- **Fecha:** 2026-10-27
- **Fuente:** lo que contó el cliente a Fausto (Delta) + dos mails de procesos de entrevista que pasó el cliente.
- **Nota:** los mails se transcriben con el nombre del alumno anonimizado. Los links a los assessments **no** se guardan ni se abren (abrirlos podría activar el test del alumno).

## Pedido del cliente (según el Delta)

- Agente nuevo para Eddis: **generador de ejercicios de práctica** para cursos intensivos de programación en **Python**, estilo **LeetCode**.
- Todo en **inglés**.
- Objetivo: preparar a los alumnos para **entrevistas técnicas en empresas del exterior**. Ejemplos que dio el cliente: ElevenLabs, OpenAI, Anthropic.
- Formato objetivo: "así de específico, LeetCode para CoderPad".
- El cliente pasó mails reales de procesos de entrevista como insumo de diseño.

## Mail 1 — ElevenLabs (primer paso del proceso)

> Hi [alumno],
>
> Thank you for your interest in ElevenLabs. We're excited to begin the hiring process with you. Due to high application volume, we've streamlined our approach. The first step is a Python based technical assessment via CoderPad.
>
> The assessment consists of LeetCode-style coding problems with binary scoring. You're welcome to use Google or Stack Overflow to check things like syntax or documentation, but we ask that you complete the problems yourself without using AI coding tools.
>
> Watch for a separate email with complete details. Don't worry - you won't need expert-level Python knowledge to complete this 90-minute challenge.
>
> Feel free to complete the assessment at your convenience, for context the common completion time would be within 7-10 days, it takes around an hour or so to complete. The link expires after 30 days.
>
> In the meantime, feel free to explore our products and learn more about the role and the company by chatting with one of our conversational AI agents - Becky or Oscar. Interacting with either agent is optional and is meant for informational purposes only.
>
> You can also find out more about us on our careers page, LinkedIn, and blog.
>
> Best wishes,
> Banu

## Mail 2 — empresa no identificada (invitación al assessment)

> Hello [alumno],
>
> Thank you for the time speaking to us. As a next step we'd like to invite you to take a short technical assessment as part of our recruitment process.
>
> You're free to choose the time that best suits you to start your assessment.
>
> When you're ready, please click this link below to access a tutorial and the test itself.
>
> [link al test — omitido]
>
> Good luck!

## Datos duros que salen de los mails

| Dato | Fuente |
|------|--------|
| Lenguaje: Python | Mail 1 |
| Plataforma: CoderPad (assessment asincrónico) | Mail 1 |
| Problemas "LeetCode-style" | Mail 1 |
| Scoring **binario** (pasa o no pasa) | Mail 1 |
| Duración: 90 min (≈1 h de resolución real) | Mail 1 |
| Se permite Google / Stack Overflow; **no** herramientas de IA | Mail 1 |
| "No hace falta Python experto" | Mail 1 |
| Ventana: 7–10 días habitual, link vence a los 30 días | Mail 1 |
| El test trae un tutorial previo | Mail 2 |

## Abierto / a confirmar con el cliente

- Canal: ¿dónde lo usan los alumnos? (WhatsApp, web, plataforma propia de Eddis).
- ¿El agente solo **genera** ejercicios, o también **corrige** las soluciones del alumno / da pistas / simula el examen cronometrado?
- Nivel de entrada de los alumnos y duración del curso.
- ¿Quién lo usa: el alumno directo o el profesor que arma el material?
- ¿Hay más mails / empresas objetivo (OpenAI, Anthropic) con formato distinto a CoderPad?
- Qué hace `eddis-api-worker` y si se relaciona con este agente.
