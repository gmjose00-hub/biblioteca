# Claude — instrucciones de este proyecto

- Lee expresamente `AGENTS.md` de esta carpeta: contiene las reglas y el contexto compartidos con Codex, incluidas las referencias a documentos especializados.
- Lee `../CLAUDE.md` si existe para las preferencias generales de Claude. En un clon aislado, sigue las reglas locales y este archivo.
- Empieza por `docs/ESTADO.md` y actualiza ese mismo archivo al terminar. Las reglas comunes se editan en `AGENTS.md`, sin copiarlas aquí.
- Al iniciar una tarea, indica brevemente si conviene ajustar el modelo o el esfuerzo; si el actual es adecuado, continúa. Si recomiendas cambiarlo, espera a que el propietario lo cambie o confirme continuar; no afirmes poder cambiar opciones que no controlas.
- Las preferencias privadas pueden ir en `CLAUDE.local.md`, excluido de Git; el contexto necesario para Codex debe quedar en documentos compartidos, sin secretos.

## Cierre de sesión
- Al terminar o cuando José pase a otra sesión: deja `docs/ESTADO.md` al día (máx. 20 líneas), comprueba que no queda trabajo propio sin commitear y avisa en una línea de que la sesión ya se puede archivar.
- No borres ni archives la sesión por tu cuenta: el archivado automático por inactividad (2 días) lo hace la aplicación, y borrar una sesión es irreversible. Solo si José lo pide en ese momento.
