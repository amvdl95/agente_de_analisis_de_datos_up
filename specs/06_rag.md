# 06 — RAG Simplificado

## Objetivo
Recuperar contexto documental para mejorar la respuesta.

## Implementación mínima
1. Cargar documentos locales en texto plano.
2. Partir en fragmentos pequeños.
3. Embedding + búsqueda por similitud.
4. Devolver top_k fragmentos.

## API de tool
buscar_contexto_rag(consulta: str, top_k: int = 3) -> list[str]

## Datos sugeridos
- diccionario de datos
- definiciones de KPI
- reglas de negocio del caso

## Criterio de simplicidad
Sin reranking avanzado ni múltiples stores.
