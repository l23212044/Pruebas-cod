# Estructura del repositorio

## Árbol de carpetas
```text
.
├── README.md
├── docs/
│   ├── propuesta.md
│   ├── caso_de_uso.md
│   ├── estructura_repositorio.md
│   ├── plan_de_pruebas.md
│   └── reflexion_ia.md
├── src/
│   └── main.s
├── scripts/
│   └── run_tests.sh
└── Makefile
```

## Descripción de archivos clave
- `src/main.s`: Núcleo del proyecto en ARM64 Assembly con al menos una macro funcional (`PRINT`).
- `scripts/run_tests.sh`: Automatización opcional de casos de prueba de consola.
- `Makefile`: Objetivos mínimos `build`, `run`, `test`, `clean`.
- `docs/*.md`: Evidencias de diseño, alcance, pruebas y reflexión académica.

## Convenciones de nombres
- Archivos en minúsculas y con guion bajo cuando aplique (`caso_de_uso.md`).
- Rutinas Assembly con nombres descriptivos en snake_case (`read_input`, `check_props`).
- Etiquetas de mensajes en Assembly prefijadas por dominio (`msg_error_formato`).
- Commits con prefijo sugerido por evidencia: `docs:`, `asm:`, `test:`.

## Versionado simple
- Estrategia de una rama principal para aula (`main`).
- Etiquetas de avance sugeridas:
  - `v0.1-docs` (documentación base completa).
  - `v0.2-core` (núcleo Assembly funcional).
  - `v1.0-entrega` (pruebas aprobadas y entrega final).
- Cada versión debe incluir mensaje de commit claro y trazable a la rúbrica.
