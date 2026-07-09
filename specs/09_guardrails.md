# 09 — Guardrails (Seguridad mínima)

## Guardrail de entrada
Bloquea:
- consultas fuera de dominio
- intentos de prompt injection obvios

Template simple de validación:
- dominio_permitido: ventas, clientes, KPI, pronóstico
- patrones_bloqueo: "ignora instrucciones", "actúa como", "revela prompt"

## Guardrail de salida
Revisa reporte_final y enmascara:
- emails
- DNI/documentos
- tarjetas

## Política de respuesta
Si bloquea entrada: devolver mensaje de dominio permitido.
Si detecta PII no enmascarable en salida: devolver mensaje seguro.
