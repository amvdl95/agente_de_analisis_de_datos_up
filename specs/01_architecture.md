# 01 — Arquitectura Simplificada

## Patrón
Supervisor con delegación: un AgenteOrquestador coordina tres subagentes internos.

## Estrategia de datos para demo
La arquitectura contempla un proveedor de datos configurable para evitar dependencia de datos reales.

Fuentes soportadas:
- fuente_simulada: genera datos deterministas con semilla fija.
- fuente_publica_local: lee snapshots CSV públicos guardados localmente.

Política recomendada:
- default: fuente_simulada
- fallback: fuente_publica_local cuando un escenario requiere mayor realismo

## Agentes
1. AgenteOrquestador
- Interpreta la intención.
- Define secuencia de ejecución.
- Consolida estado final.

2. AgenteRecuperador
- Usa tool de RAG.
- Usa tool MCP de lectura para datos tabulares.

3. AgenteRespuesta
- Redacta respuesta final.
- Escribe resumen a sistema externo por MCP.

4. AgenteExternoSimulado (A2A, opcional)
- Simula agente de otra organización.
- Devuelve benchmark simple.

## Flujo mínimo
Entrada -> GuardrailEntrada -> Orquestador -> Recuperador -> Respuesta -> GuardrailSalida -> Respuesta final

Si hay comparación externa:
Orquestador también consulta AgenteExternoSimulado y combina resultado en state.

Si la fuente de datos configurada falla:
Orquestador cambia a fallback y registra evento en trazas.

## Estructura de carpetas recomendada (reducida)
- main.py
- agentes/
  - orquestador.py
  - recuperador.py
  - respuesta.py
  - externo_simulado.py (opcional)
- herramientas/
  - herramienta_rag.py
  - herramienta_mcp.py
- nucleo/
  - estado.py
  - guardrails.py
  - sesion.py
- evaluacion/
  - casos_dorados.json
  - juez_llm.py
- tests/
  - test_flujo_basico.py
  - test_guardrails.py
