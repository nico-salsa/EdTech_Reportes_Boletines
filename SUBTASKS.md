# SubTasks

A continuación dejamos la constancia de las subtasks redactadas para este proyecto.

---

## HDU_1: Registrar usuarios

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba:** Definir flujos para la validación de contraseñas (longitud mínima, caracteres permitidos) y duplicidad de nombres de usuario.
- **Validación de API:** Automatizar pruebas para las respuestas `201 Created` y `400 Bad Request` (campos vacíos) y `409 Conflict` (usuario duplicado).
- **Pruebas de UI:** Verificar que los mensajes de error sean visibles y que el botón de registro permanezca inactivo mientras haya campos obligatorios vacíos.

#### No funcionales
- **Verificación de seguridad:** Comprobar directamente en base de datos que la contraseña no se almacene en texto plano (hashing)

### Tareas de Desarrollo (Dev)

## HDU_2: Iniciar sesión

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos de "happy path" (credenciales correctas) y flujos negativos (usuario inexistente, contraseña errónea).
- **Validación de API**: Automatizar pruebas para verificar códigos de respuesta: 200 OK (éxito con entrega de Token), 401 Unauthorized (credenciales inválidas) y 400 Bad Request (campos vacíos).
- **Pruebas de UI**: Verificar el redireccionamiento exitoso a la página principal y el resaltado visual de campos obligatorios cuando están vacíos.

#### No funcionales
- **Seguridad (Autenticación)**: Validar que tras un inicio de sesión exitoso, el sistema genere y almacene un token de sesión seguro y no exponga la contraseña en la URL o en logs
- **Usabilidad de Errores**: Comprobar que el mensaje de error para credenciales inválidas sea genérico (ej: "Usuario o contraseña incorrectos") para no dar pistas sobre qué dato falló específicamente.

### Tareas de Desarrollo (Dev)