# 03 — Agente Orquestador

## Rol
Coordinar el flujo completo en pasos simples y deterministas.

## Responsabilidades
1. Validar si guardrail de entrada aprobó.
2. Definir plan de ejecución según intención.
3. Delegar a subagentes en orden.
4. Manejar errores simples.
5. Cerrar sesión con respuesta final.

## Planes tipo
- Consulta descriptiva:
  - recuperador -> respuesta

- Consulta comparativa externa:
  - recuperador -> externo_simulado -> respuesta

## Pseudocódigo
```python
def ejecutar(estado):
    if not estado.guardrail_entrada_ok:
        return estado

    estado.plan = construir_plan(estado.consulta_usuario)

    for paso in estado.plan:
        estado.agente_actual = paso
        estado = llamar_agente(paso, estado)
        if estado.error:
            estado.trazas.append({"evento": "error", "agente": paso})
            break

    estado.agente_actual = "fin"
    return estado
```

## Criterio de simplicidad
Sin replanificación compleja: se usa estrategia lineal con salida temprana en error.
