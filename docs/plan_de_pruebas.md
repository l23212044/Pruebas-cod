# Plan de pruebas

## Estrategia de pruebas
Se aplicarán pruebas funcionales de caja negra sobre entrada/salida de consola. Cada caso valida una competencia observable: validación de formato, conversión básica, lógica de paridad y verificación de rango.

## Casos de prueba
| ID | Entrada | Resultado esperado | Criterio de éxito |
|---|---|---|---|
| CP-01 | `24` | Mensaje de válido, par, en rango | Salida contiene las 3 confirmaciones y exit code 0 |
| CP-02 | `17` | Mensaje de válido, impar, en rango | Salida contiene “impar” y exit code 0 |
| CP-03 | `12005` | Mensaje de válido, impar/par según corresponda, fuera de rango | Clasificación de rango correcta |
| CP-04 | `12a5` | Mensaje de error de formato | Se rechaza entrada y exit code != 0 |
| CP-05 | *(vacía)* | Mensaje de entrada vacía | Se detecta vacío y exit code != 0 |
| CP-06 | `0008` | Válido, par, en rango | Manejo correcto de ceros a la izquierda |

## Cobertura mínima
- 100% de funcionalidades declaradas en alcance (4 de 4).
- Al menos 1 caso por escenario alterno del caso de uso.
- Al menos 1 caso límite de formato y 1 de rango.

## Criterios de aprobación
- Se aprueba cuando al menos 5 de 6 casos pasan y obligatoriamente pasan CP-01, CP-04 y CP-05.
- Si falla cualquier caso obligatorio, la entrega queda en estatus “requiere corrección”.
- Resultados deben documentarse con evidencia de comandos y salidas en el historial del repositorio.
