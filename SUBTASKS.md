# SubTasks

A continuación dejamos la constancia de las subtasks redactadas para este proyecto.

---

## HDU_1: Registrar usuarios

### Tareas de Calidad (QA)

- **Diseño de casos de prueba:** Definir flujos para la validación de contraseñas (longitud mínima, caracteres permitidos) y duplicidad de nombres de usuario.
- **Validación de API:** Automatizar pruebas para las respuestas `201 Created` y `400 Bad Request` (campos vacíos) y `409 Conflict` (usuario duplicado).
- **Pruebas de UI:** Verificar que los mensajes de error sean visibles y que el botón de registro permanezca inactivo mientras haya campos obligatorios vacíos.
- **Verificación de seguridad:** Comprobar directamente en base de datos que la contraseña no se almacene en texto plano (hashing)

### Tareas de Desarrollo (Dev)