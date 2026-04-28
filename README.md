# Actividad integradora: Microproyecto en ARM64 Assembly para GitHub Classroom

## Contexto
En cursos de arquitectura de computadoras y sistemas embebidos, es clave que el estudiantado conecte teoría (registros, llamadas al sistema, flujo de control) con una implementación funcional y medible. Esta actividad propone un microproyecto de bajo costo computacional, viable en laboratorio o en equipos personales con Linux ARM64 o emulación.

## Objetivo general
Diseñar, documentar e implementar un microproyecto con núcleo obligatorio en ARM64 Assembly que resuelva una necesidad simple de procesamiento de datos de consola, con evidencia técnica en repositorio y pruebas verificables.

## Competencias
- Diseña una solución técnica de alcance acotado con criterios de aceptación claros.
- Implementa rutinas básicas en ARM64 Assembly usando al menos una macro funcional.
- Integra documentación técnica mínima para mantenimiento y evaluación por competencias.
- Ejecuta pruebas funcionales con criterios objetivos de aprobación.

## Instrucciones rápidas
1. Crea tu repositorio de GitHub Classroom y clona en local.
2. Lee `docs/propuesta.md` y valida alcance (3 a 5 funcionalidades pequeñas).
3. Implementa el núcleo en ARM64 Assembly (máximo sugerido de ~150 líneas funcionales).
4. Incluye al menos una macro (ejemplo: macro para impresión de cadenas por syscall).
5. Si lo requieres, agrega una capa opcional mínima (Bash o C++/Rust/Go/C#/Java/JavaScript) sin frameworks pesados.
6. Ejecuta plan de pruebas de `docs/plan_de_pruebas.md` y registra resultados.
7. Entrega con commit final y evidencias en el repositorio.

## Criterios de entrega
- Repositorio con los 6 documentos solicitados completos y coherentes.
- Implementación ARM64 Assembly funcional con al menos 1 macro.
- Alcance acotado: 3 a 5 funcionalidades pequeñas de consola.
- Sin Python, sin Docker/Kubernetes, sin servicios cloud adicionales, sin APIs pagadas.
- Pruebas ejecutadas con evidencia de cumplimiento de criterios de éxito.

## Rúbrica
| Criterio | Excelente (100-90) | Satisfactorio (89-80) | Básico (79-70) | Insuficiente (<70) |
|---|---|---|---|---|
| Diseño técnico | Problema, alcance, riesgos y supuestos totalmente alineados | Hay alineación general con detalles menores faltantes | Diseño parcial o ambiguo | Diseño incoherente o incompleto |
| Implementación ARM64 | Funciona, usa macro y cumple restricciones técnicas | Funciona con fallas menores de estilo/documentación | Funciona parcialmente | No funcional o fuera de restricciones |
| Pruebas | Casos completos, medibles y reproducibles | Casos suficientes con evidencia parcial | Casos limitados o poco medibles | Sin pruebas verificables |
| Documentación | Clara, profesional y accionable | Clara con omisiones menores | Incompleta o poco clara | Deficiente o ausente |
| Integridad académica | Reflexión crítica y validación manual sólida | Reflexión aceptable con validación mínima | Reflexión superficial | Sin declaración de integridad |
