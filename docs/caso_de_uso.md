# Caso de uso: Validación y análisis básico de número

## Actor principal
Estudiante de arquitectura de computadoras que ejecuta el programa desde terminal.

## Flujo principal
1. El actor ejecuta el binario `numcheck64`.
2. El sistema solicita ingresar un número entero no negativo.
3. El actor captura una cadena y presiona Enter.
4. El sistema valida que la entrada sea numérica.
5. El sistema convierte la cadena a entero.
6. El sistema informa:
   - Entrada válida.
   - Si el número es par o impar.
   - Si está dentro de 0 a 9999.
7. El sistema termina con código de salida 0.

## Escenarios alternos
### Alterno A: Entrada con caracteres no numéricos
1. En el paso 3, el actor ingresa `12a5`.
2. El sistema detecta carácter inválido.
3. El sistema muestra mensaje de error de formato.
4. El sistema termina con código distinto de 0.

### Alterno B: Entrada vacía o solo Enter
1. En el paso 3, el actor solo presiona Enter.
2. El sistema detecta longitud cero efectiva.
3. El sistema muestra mensaje de entrada vacía.
4. El sistema termina con código distinto de 0.

## Precondiciones
- Binario compilado para ARM64 Linux.
- Permisos de ejecución habilitados.
- Terminal disponible para entrada/salida estándar.

## Postcondiciones
- Se emite un resultado claro de validez y clasificación.
- El programa finaliza sin dejar procesos huérfanos.
- Se conserva trazabilidad por medio de salida de consola.

## Criterios de aceptación
- Si la entrada es numérica válida, siempre se reporta paridad correcta.
- Si la entrada contiene símbolos o letras, siempre se rechaza.
- Si la entrada es vacía, se reporta explícitamente.
- Para valores 0 a 9999, se reporta “en rango”; fuera de ese intervalo, “fuera de rango”.
