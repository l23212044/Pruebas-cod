# Propuesta de microproyecto

## Problema
En prácticas iniciales de arquitectura, el estudiantado suele compilar ejemplos aislados sin articular una solución completa. Se requiere una actividad donde se diseñe e implemente un utilitario realista, pequeño y comprobable en ARM64 Assembly.

## Justificación
Este microproyecto fortalece la comprensión de:
- Uso de registros y convenciones de llamada.
- Manejo de syscalls básicas en Linux ARM64.
- Modularidad mínima por rutinas y macros.
- Validación de resultados con criterios objetivos.

Además, su alcance corto permite evaluación por competencias en grupos numerosos y con recursos limitados.

## Alcance y límites
### Alcance
Desarrollar una herramienta de consola llamada `numcheck64` con 4 funcionalidades:
1. Leer una cadena numérica desde entrada estándar.
2. Validar si el texto contiene solo dígitos.
3. Convertir a entero de 64 bits (con validación básica de rango académico).
4. Reportar si el número es par o impar y si está en rango de 0 a 9999.

### Límites
- Núcleo en ARM64 Assembly con al menos una macro funcional.
- Máximo sugerido de ~150 líneas funcionales en Assembly.
- Sin interfaz gráfica, sin base de datos obligatoria, sin red.
- Capa opcional mínima permitida: script Bash para automatizar pruebas.

## Arquitectura (alto nivel)
- **Módulo Assembly principal (`src/main.s`)**
  - Macro `PRINT msg, len` para salida por syscall `write`.
  - Rutina `read_input` para capturar hasta N caracteres.
  - Rutina `is_digits` para validar entrada.
  - Rutina `to_int64` para conversión básica.
  - Rutina `check_props` para paridad y rango.
- **Capa opcional (`scripts/run_tests.sh`)**
  - Ejecuta casos de prueba predefinidos y compara salidas esperadas.

## Riesgos y mitigación
- **Riesgo:** Dificultad con sintaxis ensamblador y linker.
  - **Mitigación:** Proporcionar plantilla mínima y comandos de compilación estándar.
- **Riesgo:** Errores por manejo de salto de línea en entrada.
  - **Mitigación:** Incluir prueba específica para `\n` y limpieza de buffer.
- **Riesgo:** Exceso de alcance.
  - **Mitigación:** Limitar a 4 funcionalidades y no aceptar extras no documentados.

## Supuestos
- El entorno académico dispone de Linux ARM64 nativo o emulación configurada por docente.
- El estudiantado conoce fundamentos de registros generales y saltos condicionales.
- Se cuenta con `as` y `ld` (GNU binutils) o cadena equivalente instalada.
