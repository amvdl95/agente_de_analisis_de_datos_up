# 12 — Testing Simplificado

## Objetivo
Garantizar funcionamiento del flujo principal con pocas pruebas de alto valor.

## Suite mínima
1. test_flujo_basico
- orquestador + recuperador + respuesta

2. test_guardrail_entrada
- bloquea prompt injection

3. test_guardrail_salida
- enmascara PII

4. test_mcp_lectura_escritura
- lee y escribe con mocks

5. test_a2a_simulado
- consulta benchmark externo simulado

6. test_datos_demo_reproducibles
- misma seed produce mismos resultados

7. test_fallback_fuente_datos
- si falla fuente simulada o publica, el orquestador cambia a la otra y completa respuesta degradada

## Criterio
Todo en verde con uv run pytest.
