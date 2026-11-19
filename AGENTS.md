# biblioteca

Finalidad (confirmada por José el 19/11/2026): catálogo personal de los libros que tiene en casa. Usuario final: José. El stack, los dispositivos de uso y los comandos siguen sin decidir; todavía no hay código. No confundir este proyecto con Biblioteca Técnica (24.Pistachos). Consulta docs/ESTADO.md y pregunta antes de implementar.

## Relevo compartido — vigente desde el 20/10/2026
- Estas reglas locales sirven para Claude y Codex. Lee también `../AGENTS.md` si está disponible; las particularidades de este proyecto se conservan aquí. Si el clon está aislado, este protocolo sigue siendo aplicable.
- Un solo asistente edita el proyecto cada vez. Antes de tocar archivos, consulta la rama y los cambios pendientes de Git; conserva el trabajo previo y no incluyas archivos ajenos en un commit.
- Empieza por `docs/ESTADO.md` y consulta después las fuentes de continuidad que enlaza. Es el único resumen operativo del relevo; los diarios anteriores conservan su historia y su detalle, sin mantener un segundo resumen contradictorio.
- Al cerrar o cambiar de asistente, actualiza `docs/ESTADO.md` (máximo 20 líneas): fecha/asistente, objetivo, decisiones aprobadas, cambios, comprobaciones ejecutadas y pendientes, rama/cambios sin commit, bloqueos y siguiente paso. Distingue hechos, propuestas y datos pendientes de verificar.
- Las decisiones duraderas y su motivo permanecen en los documentos de decisiones o arquitectura propios del proyecto. No copies conversaciones completas ni secretos al estado.
- Habla en español de España, con palabras llanas, fechas dd/mm/aaaa y unidades métricas. No inventes requisitos ni avances.
- Busca antes de leer; consulta solo lo necesario. Datos, registros, binarios y archivos de dependencias se leen únicamente si la tarea lo requiere.
- Primero entiende la zona afectada; en cambios grandes, presenta un plan y espera confirmación salvo autorización previa. Comprueba los cambios y explica cualquier fallo o limitación.
- Conserva las reglas locales de seguridad, datos, pruebas, Git y publicación. Un relevo documental no exige instalar, compilar, abrir programas, cambiar versiones, crear commits, subir a GitHub ni publicar; esas acciones mantienen sus autorizaciones y condiciones específicas para el trabajo de desarrollo.
- Los cambios en instrucciones no se propagan a otras carpetas salvo petición expresa. Lo específico de Claude se queda en `CLAUDE.md`; no presupongas que el otro asistente comparte conversación, configuración o memoria privada.
- Usa `rtk` cuando esté disponible; si falta, informa y usa el comando nativo. No lo instales sin petición.
