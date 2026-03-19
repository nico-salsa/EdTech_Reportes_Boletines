# SubTasks

A continuación dejamos la constancia de las subtasks redactadas para este proyecto.


| Historia de Usuario | Tareas de Calidad (QA Tasking) | Est. (SP) | Justificación del Esfuerzo |
|---------------------|--------------------------------|-----------|----------------------------|
| HDU_1 Registrar usuarios | 1. Diseño de casos de prueba: Definir flujos para contraseñas (longitud, caracteres) y nombres de usuario. | 3 | Esfuerzo moderado. Aunque es un flujo estándar, requiere asegurar que la validación de duplicados sea infalible y que la comunicación con el Backend sea correcta. |
| | 2. Validación de API: Automatizar pruebas para respuestas 201 Created y 400 Bad Request (duplicados/vacíos). | | |
| | 3. Pruebas de UI: Verificar que los mensajes de error sean visibles y el botón de registro se bloquee si hay campos nulos. | | |
| | 4. Verificación de Persistencia: Comprobar en base de datos que la contraseña no se guarde en texto plano (Hasing). | | |