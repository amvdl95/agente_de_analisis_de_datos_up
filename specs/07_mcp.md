# 07 — MCP (Lectura y Escritura)

## Objetivo
Usar MCP para integrar un servicio externo en forma simple.

## Tools
1. mcp_leer(recurso, filtros)
- Usada por AgenteRecuperador.

2. mcp_escribir(destino, contenido)
- Usada por AgenteRespuesta.

## Contrato mínimo
- Input: JSON con recurso/destino y payload.
- Output: JSON con success, data o error.

Parámetros sugeridos para demo:
- mode: "simulado" | "publico"
- scenario: nombre de escenario (ej: "ventas_mensuales")
- seed: entero opcional para reproducibilidad en simulado

## Reglas
- Si falla lectura, registrar error y continuar degradado cuando sea posible.
- Si falla escritura, no perder respuesta al usuario.
- En modo demo, priorizar simulado; si no hay datos, usar público local como fallback.
