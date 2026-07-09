# 02 — Estado Compartido

## Objetivo
Definir un state simple, explícito y suficiente para el flujo multiagente.

## Esquema propuesto
```python
from dataclasses import dataclass, field
from typing import Any

@dataclass
class EstadoSesion:
    id_sesion: str
    consulta_usuario: str
    historial_chat: list[dict[str, str]] = field(default_factory=list)

    # control de flujo
    agente_actual: str = "orquestador"
    plan: list[str] = field(default_factory=list)

    # datos de trabajo
    datos_recuperados: dict[str, Any] | None = None
    contexto_rag: list[str] = field(default_factory=list)
    benchmark_externo: dict[str, Any] | None = None

    # resumen/analisis simple
    metricas: dict[str, Any] | None = None

    # salida
    reporte_final: str = ""

    # seguridad
    guardrail_entrada_ok: bool = True
    guardrail_salida_ok: bool = True

    # observabilidad básica
    trazas: list[dict[str, Any]] = field(default_factory=list)
    error: str | None = None
```

## Reglas
- Cada agente lee y actualiza solo sus campos de responsabilidad.
- Si error no nulo, el orquestador decide continuar degradado o cortar.
- El estado se persiste por id_sesion para habilitar continuidad.
