# 00 — Resumen del Producto (Versión Facultad)

## Objetivo
Construir un sistema multiagente simple que responda preguntas de negocio en lenguaje natural usando datos internos, RAG y una consulta externa por MCP.

## Alcance académico
Este proyecto prioriza claridad y cumplimiento de requisitos de cursada por sobre complejidad productiva.

Requisitos cubiertos:
- Orquestador + subagentes con tareas concretas.
- Uso de state compartido.
- Tools para RAG y MCP.
- Consulta externa por MCP (lectura) y escritura por MCP.
- Guardrails mínimos de entrada y salida.
- Evaluación automática con LLM as a Judge.
- Gestión de sesiones.
- Protocolo A2A simulado.
- Observabilidad básica.

## Caso de uso principal
Pregunta tipo: "¿Cómo evolucionaron las ventas y qué se espera para el próximo mes?"

Flujo esperado:
1. Guardrail de entrada valida dominio.
2. Orquestador delega a Recuperador para traer datos (MCP + RAG).
3. Orquestador delega a Respuesta para resumir hallazgos y persistir resultado por MCP.
4. Guardrail de salida enmascara PII.

## Estrategia de demo sin datos reales
Para la defensa se define un modo demo explícito, sin dependencia de datos productivos.

Modalidades:
- Datos simulados deterministas (recomendado v1): series de ventas y segmentos generados con semilla fija.
- Datos públicos curados (opcional): CSV estático versionado en repo para repetir resultados.
- Modo híbrido: público para contexto y simulado para escenarios de borde.

Criterio de selección sugerido:
- Priorizar simulados para robustez y repetibilidad.
- Usar públicos solo cuando aporten narrativa de negocio fácil de explicar.

## No objetivos
- No se busca arquitectura cloud compleja.
- No se busca alta concurrencia ni optimización extrema.
