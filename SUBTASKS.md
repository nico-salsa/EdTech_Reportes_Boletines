# SubTasks

A continuación dejamos la constancia de las subtasks redactadas para este proyecto.

---

## HDU_1: Registrar usuarios

> **Estimación:** 3 Story Points
>
> **Justificación:** Esfuerzo moderado. Aunque es un flujo estándar, requiere asegurar que la validación de duplicados sea infalible y que la comunicación con el backend sea correcta.

### Tareas de Desarrollo (Dev)

- [ ] **Endpoint de registro:** Implementar el endpoint `POST /auth/register` que reciba `username` y `password`.
- [ ] **Validación de campos:** Aplicar validación server-side para campos vacíos u obligatorios faltantes, retornando `400 Bad Request` con detalle de los campos inválidos.
- [ ] **Verificación de duplicados:** Consultar la base de datos antes de insertar y retornar `409 Conflict` si el nombre de usuario ya existe.
- [ ] **Hash de contraseña:** Almacenar la contraseña usando un algoritmo de hashing seguro (bcrypt u equivalente). Nunca persistir texto plano.
- [ ] **Respuesta exitosa:** Retornar `201 Created` con la estructura de usuario creado (sin exponer la contraseña).

### Tareas de Calidad (QA)

- [ ] **Diseño de casos de prueba:** Definir flujos para la validación de contraseñas (longitud mínima, caracteres permitidos) y unicidad de nombres de usuario.
- [ ] **Validación de API:** Automatizar pruebas para las respuestas `201 Created` y `400 Bad Request` (campos vacíos) y `409 Conflict` (usuario duplicado).
- [ ] **Pruebas de UI:** Verificar que los mensajes de error sean visibles y que el botón de registro permanezca inactivo mientras haya campos obligatorios vacíos.
- [ ] **Verificación de seguridad:** Comprobar directamente en base de datos que la contraseña no se almacene en texto plano (hashing verificado).