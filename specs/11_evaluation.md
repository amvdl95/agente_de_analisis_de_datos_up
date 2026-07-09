# 11 — Evaluación Automática

## Objetivo
Evaluar calidad semántica de respuestas con LLM as a Judge.

## Casos mínimos (obligatorios)
1. Faithfulness
- Verifica si la respuesta se apoya en datos recuperados (RAG + MCP).

2. Helpfulness
- Verifica si la respuesta realmente resuelve la pregunta del usuario.

## Métricas
- puntaje_faithfulness (0 a 1)
- puntaje_helpfulness (0 a 1)

## Golden Cases
Archivo: evaluacion/casos_dorados.json
- incluir al menos 6 escenarios:
  - 2 consultas descriptivas
  - 2 consultas comparativas (con/sin A2A)
  - 1 fuera de dominio
  - 1 intento de inyección

## Criterio de aprobación sugerido
- promedio_faithfulness >= 0.80
- promedio_helpfulness >= 0.80
