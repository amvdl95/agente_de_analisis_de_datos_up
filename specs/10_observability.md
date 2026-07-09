# 10 — Observabilidad Básica

## Objetivo
Tener trazabilidad suficiente para explicar qué hizo cada agente.

## Mínimo requerido
1. Log por paso de agente
- id_sesion
- agente
- evento
- timestamp

2. Log de tools
- nombre_tool
- éxito o error
- latencia_ms

3. Métricas simples
- tiempo_total_flujo
- cantidad_errores
- cantidad_bloqueos_guardrail

## Implementación sugerida
- logging estructurado en JSON
- guardar logs a archivo local en desarrollo
