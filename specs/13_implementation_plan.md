# 13 — Plan de Implementación (Simple y Realista)

## Objetivo general
Entregar un proyecto claro, corto y defendible en facultad, cumpliendo mínimos y contenidos medios sin sobreingeniería.

## Fase 1 — Base (día 1)
- Crear estado compartido (nucleo/estado.py).
- Crear guardrails mínimos (nucleo/guardrails.py).
- Definir sesión simple en memoria o sqlite (nucleo/sesion.py).

## Fase 2 — Herramientas (día 2)
- Implementar herramienta_rag.py.
- Implementar herramienta_mcp.py (leer + escribir).

## Fase 2.5 — Datos de demo (día 2)
- Definir modo de datos: simulado (default) y publico_local (fallback).
- Crear generador con seed fija para escenarios de negocio.
- Versionar snapshots CSV públicos mínimos para demo.
- Documentar 3 escenarios reproducibles de punta a punta.

## Fase 3 — Agentes (día 3)
- orquestador.py
- recuperador.py
- respuesta.py
- externo_simulado.py (A2A, opcional)

## Fase 4 — Flujo completo (día 4)
- Conectar todo en main.py.
- Probar flujo descriptivo y flujo comparativo con A2A.
- Validar fallback automático entre fuentes de datos demo.

## Fase 5 — Evaluación y cierre (día 5)
- Armar evaluacion/casos_dorados.json.
- Implementar evaluacion/juez_llm.py (faithfulness + helpfulness).
- Agregar observabilidad básica y tests mínimos.

## Estructura recomendada (reducida)
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
  - test_mcp.py
  - test_a2a.py

## Qué eliminar para mantener simple
- pipelines de observabilidad avanzada
- ML en la primera entrega
- agente de visualización separado (opcional)
- despliegue cloud y componentes enterprise no necesarios para la entrega
