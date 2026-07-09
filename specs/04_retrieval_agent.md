# 04 — Agente Recuperador

## Rol
Recuperar información factual para responder la consulta.

## Tools usadas
1. buscar_contexto_rag(consulta)
- Devuelve fragmentos de documentos relevantes.

2. mcp_leer(recurso, filtros)
- Devuelve datos tabulares desde un servicio externo.

## Entradas
- consulta_usuario
- pistas de filtros inferidas por el orquestador

## Salidas en state
- contexto_rag
- datos_recuperados

## Regla operativa
- Siempre intenta RAG primero (definiciones y contexto).
- Luego intenta MCP lectura si la consulta pide números o tablas.

## Error handling mínimo
- Si MCP falla, guardar error legible en estado.error.
- Si RAG no encuentra nada, continuar con lista vacía.
