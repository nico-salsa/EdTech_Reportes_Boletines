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

## HDU_3: Crear nuevo curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de escenarios de prueba**: Definir flujos para nombres de cursos con caracteres especiales, longitudes máximas y espacios en blanco al inicio/final
- **Validación de API**: Automatizar pruebas para los métodos POST (crear) y PUT (editar), verificando respuestas 201 Created (éxito), 409 Conflict (duplicado) y 400 Bad Request (título vacío)
- **Pruebas de UI**: Verificar que tras la creación exitosa, el usuario sea redirigido a la vista del nuevo curso o que este aparezca inmediatamente en el listado de la página principal

#### No funcionales
- **Consistencia en Modificación**: Validar que al editar el título de un curso, todos los estudiantes y grupos previamente asignados mantengan su vínculo correctamente

## HDU_4: Consultar curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Definir escenarios para cursos con muchos estudiantes, cursos vacíos y estudiantes sin notas (promedio 0).
- **Validación de API**: Automatizar pruebas para el endpoint GET /courses/{id} verificando la estructura del JSON y códigos 200 OK o 404 Not Found
- **Pruebas de UI**: Verificar que la tabla de estudiantes muestre correctamente las columnas de nombre completo, grupo, instancias evaluatorias y promedios, asegurando que el diseño sea legible.

#### No funcionales
- **Rendimiento**: Validar el tiempo de carga de la pantalla de detalle cuando el curso tiene un volumen alto de estudiantes (ej: +50 registros)
- **Consistencia de Datos**: Realizar pruebas E2E para confirmar que el promedio visualizado en la pantalla coincida exactamente con el cálculo interno de la base de datos.

## HDU_5: Agregar estudiantes a la lista de estudiantes de un curso

### Tareas de Calidad (QA)

#### Funcionales
- **Diseño de casos de prueba**: Definir escenarios de "Primer Registro" (ID nuevo) y "Registro con ID existente" (el estudiante ya se encuentra en el sistema)
- **Validación de API**: Automatizar pruebas para el endpoint de inscripción, verificando que un POST con ID nuevo devuelva 201 Created y uno con ID existente devuelva el objeto ya persistido
- **Pruebas de UI**: Verificar que la tabla de estudiantes muestre correctamente la lista de estudiantes con nombre completo asegurando que el diseño sea legible.

#### No funcionales
- **Integridad**: Validar que si la inscripción al curso falla (ej: por error de red) el estudiante no quede registrado a medias en el sistema global.
